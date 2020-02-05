---
title: Meilleures pratiques pour l’interopérabilité native – .NET
description: Découvrez les meilleures pratiques pour interagir avec des composants natifs en .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 9486256b815856c0c283f5fe231be3d35d6e8f00
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742753"
---
# <a name="native-interoperability-best-practices"></a>Meilleures pratiques pour l’interopérabilité native

.NET propose différents moyens de personnaliser du code d’interopérabilité native. Cet article détaille les instructions suivies par les équipes .NET de Microsoft pour l’interopérabilité native.

## <a name="general-guidance"></a>Règle générale

Les instructions de cette section s’appliquent à tous les scénarios d’interopérabilité.

- ✔️ Utilisez le même nom et la même mise en majuscules pour vos méthodes et paramètres que la méthode Native que vous souhaitez appeler.
- ✔️ envisagez d’utiliser le même nom et la même mise en majuscules pour les valeurs constantes.
- ✔️ Utilisez les types .NET qui se mappent le plus près du type natif. Par exemple, en C#, utilisez `uint` lorsque le type natif est `unsigned int`.
- ✔️ N’utilisez que des attributs `[In]` et `[Out]` lorsque le comportement que vous recherchez diffère du comportement par défaut.
- ✔️ envisagez d’utiliser <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pour regrouper vos mémoires tampons de tableau natives.
- ✔️ Encapsulez vos déclarations P/Invoke dans une classe portant le même nom et en respectant la casse que votre bibliothèque native.
  - Vos attributs `[DllImport]` pourront ainsi utiliser la fonctionnalité `nameof` du langage C# pour transmettre le nom de la bibliothèque native et vérifier qu’il ne comporte pas d’erreur.

## <a name="dllimport-attribute-settings"></a>Paramètres des attributs DllImport

| Paramètre | Default | Recommandation | Détails |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Conserver la valeur par défaut  | S’il est défini explicitement sur false, les valeurs de retour HRESULT en échec sont converties en exceptions (et la valeur de retour de la définition devient ainsi Null).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | Dépend de l'API  | Définissez-le sur true si l’API utilise GetLastError et Marshal.GetLastWin32Error pour obtenir la valeur. Si l’API définit une condition indiquant une erreur, récupérez l’erreur avant d’effectuer d’autres appels, de façon à éviter de la remplacer par inadvertance.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, qui bascule en secours vers le comportement `CharSet.Ansi`  | Utilisez explicitement `CharSet.Unicode` ou `CharSet.Ansi` lorsque des chaînes ou des caractères sont présents dans la définition | Cela permet de spécifier le comportement de marshaling des chaînes et le rôle de `ExactSpelling` quand la valeur est `false`. Notez que `CharSet.Ansi` est en réalité UTF-8 sur Unix. _La plupart du temps_, Windows utilise Unicode et Unix UTF-8. Pour plus d'informations, voir la [documentation sur les charsets](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Définissez-le sur true pour augmenter légèrement les performances. En effet, le runtime ne recherche pas de noms de fonctions de remplacement avec un suffixe « A » ou « W » selon la valeur du paramètre `CharSet` (« A » pour `CharSet.Ansi` et « W » pour `CharSet.Unicode`). |

## <a name="string-parameters"></a>Paramètres de chaînes

Lorsque le jeu de caractères est Unicode ou que l’argument est explicitement marqué comme `[MarshalAs(UnmanagedType.LPWSTR)]` _et_ que la chaîne est passée par valeur (non `ref` ou `out`), la chaîne est épinglée et utilisée directement par le code natif (au lieu d’être copiée).

N’oubliez pas de marquer `[DllImport]` comme `Charset.Unicode` sauf si vous souhaitez explicitement un traitement ANSI de vos chaînes.

❌ n’utilisez pas de paramètres de `[Out] string`. Les paramètres de chaînes passés en valeur avec l’attribut `[Out]` risquent de déstabiliser le runtime s’il s’agit de chaînes centralisées. Pour plus d’informations sur la centralisation des chaînes, voir la documentation de <xref:System.String.Intern%2A?displayProperty=nameWithType>.

❌ éviter les paramètres de `StringBuilder`. Le marshaling `StringBuilder` crée *toujours* une copie de la mémoire tampon native. Il peut donc se révéler extrêmement inefficace. Prenons le scénario classique d’appel d’une API Windows qui prend une chaîne :

1. Crée un SB de la capacité souhaitée (alloue la capacité gérée) **{1}**
2. Appeler
   1. Alloue une mémoire tampon native **{2}**
   2. Copie le contenu si `[In]` _(valeur par défaut pour un paramètre `StringBuilder`)_
   3. Copie la mémoire tampon native dans un tableau managé nouvellement alloué si `[Out]` **{3}** _(également la valeur par défaut pour `StringBuilder`)_ .
3. `ToString()` alloue encore un autre tableau managé **** **

Soit *{4}* allocations pour extraire une chaîne du code natif. Le mieux que l’on puisse faire pour réduire ce nombre est de réutiliser `StringBuilder` dans un autre appel, mais cela ne fait gagner que *1* allocation. Il est largement préférable d’utiliser et de mettre en cache une mémoire tampon de caractères à partir de `ArrayPool` : vous pourrez limiter l’allocation à `ToString()` lors des appels suivants.

L’autre problème de `StringBuilder` est qu’il copie toujours la sauvegarde de la mémoire tampon de retour sur la première valeur Null. Si la chaîne de retour transmise n’est pas terminée ou se termine par un double Null, P/Invoke est au mieux incorrect.

Si vous *utilisez*`StringBuilder`, le dernier piège est que la capacité n’inclut **pas** de valeur Null masquée, qui est toujours prise en compte dans l’interopérabilité. Il est courant de se tromper de ce point de vue, car la plupart des API demandent la taille de la mémoire tampon valeur Null *incluse*. Il en résulte parfois des allocations gaspillées/inutiles. En outre, cet écueil empêche le runtime d’optimiser le marshaling `StringBuilder` afin de réduire les copies.

✔️ envisagez d’utiliser `char[]`s à partir d’un `ArrayPool`.

Pour plus d’informations sur le marshaling des chaînes, consultez [Marshaling par défaut pour les chaînes](../../framework/interop/default-marshaling-for-strings.md) et [Personnaliser le marshaling des chaînes](customize-parameter-marshaling.md#customizing-string-parameters).

> __Spécifique à Windows__ Pour les chaînes de `[Out]`, le CLR utilise `CoTaskMemFree` par défaut pour libérer des chaînes ou `SysStringFree` pour les chaînes marquées comme `UnmanagedType.BSTR`.
> **Pour la plupart des API avec une mémoire tampon de chaîne de sortie :** Le nombre de caractères transmis doit inclure la valeur null. Si la valeur de retour est inférieure au nombre de caractères transmis, c’est le signe que l’appel a réussi et que la valeur correspond au nombre de caractères *sans* la valeur Null de fin. Sinon, le nombre représente la taille requise de la mémoire tampon caractère Null *inclus*.
>
> - Pass in 5, obtenir 4 : la chaîne comporte 4 caractères avec une valeur null de fin.
> - Pass in 5, obtenir 6 : la chaîne comporte 5 caractères, nécessite une mémoire tampon de 6 caractères pour contenir la valeur null.
> [Types de données Windows pour les chaînes](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a>Paramètres et champs booléens

Il est facile de se perdre avec les booléens. Par défaut, un `bool` .NET est marshalé en un `BOOL` Windows, où il s’agit d’une valeur de 4 octets. À l’inverse, les types `_Bool` et `bool` en C et C++ correspondent à un *seul* octet. Il peut alors être difficile de traquer les bogues, car la valeur de retour est à moitié ignorée, ce qui ne modifie que *potentiellement* le résultat. Pour plus d’informations sur le marshaling des valeurs `bool` .NET en types `bool` C ou C++, consultez la documentation [Personnaliser le marshaling des champs booléens](customize-struct-marshaling.md#customizing-boolean-field-marshaling).

## <a name="guids"></a>GUID

Les GUID sont directement utilisables dans les signatures. De nombreuses API Windows acceptent des alias de type `GUID&` comme `REFIID`, qui, s’ils sont passés en référence, peuvent être transmis par `ref` ou avec l’attribut `[MarshalAs(UnmanagedType.LPStruct)]`.

| GUID | GUID en référence |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

❌ n’utilisez pas `[MarshalAs(UnmanagedType.LPStruct)]` pour tous les paramètres du GUID `ref`.

## <a name="blittable-types"></a>Types blittables

Les types blittables sont des types qui ont la même représentation au niveau du bit dans le code managé et dans le code natif. Il n’est donc pas nécessaire de les convertir dans un autre format pour les marshaler vers et à partir du code natif. Ils sont à privilégier en raison de l’amélioration des performances qui en résulte.

**Types blittables :**

- `byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`
- Tableaux unidimensionnels non imbriqués de types blittables (par exemple, `int[]`)
- Structs et classes à disposition fixe qui n’ont que des types valeurs blittables, par exemple les champs :
  - La disposition fixe exige `[StructLayout(LayoutKind.Sequential)]` ou `[StructLayout(LayoutKind.Explicit)]`.
  - Les structs sont `LayoutKind.Sequential` par défaut, les classes `LayoutKind.Auto`.

**Types NON blittables :**

- `bool`

**Types PARFOIS blittables :**

- `char`, `string`

Lorsque des types blittables sont passés en référence, ils sont simplement épinglés par le marshaleur, et non copiés vers une mémoire tampon intermédiaire. (Les classes sont, par nature, passées en référence ; les structs sont passés en référence lorsqu’ils sont utilisés avec `ref` ou `out`.)

Un `char` est blittable dans un tableau unidimensionnel **ou** s’il fait partie d’un type explicitement marqué `[StructLayout]` avec `CharSet = CharSet.Unicode`.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

Une `string` est blittable si elle n’est pas contenue dans un autre type et qu’elle est passé en argument marqué `[MarshalAs(UnmanagedType.LPWStr)]` ou que `[DllImport]` est défini pour `CharSet = CharSet.Unicode`.

Pour savoir si un type est blittable, essayez de créer un `GCHandle` épinglé. Si le type n’est pas une chaîne ou n’est pas considéré comme blittable, `GCHandle.Alloc` lèvera une `ArgumentException`.

✔️ faire en sorte que vos structures soient blittables si possible.

Pour plus d'informations, consultez les pages suivantes :

- [Types blittable et non blittable](../../framework/interop/blittable-and-non-blittable-types.md)
- [Marshaling de types](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Maintenir actifs les objets gérés

`GC.KeepAlive()` garantit qu'un objet reste accessible jusqu'à ce que la méthode KeepAlive soit atteinte.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) permet au marshaleur de maintenir un objet actif pendant la durée de P/Invoke. Il peut être utilisé à la place de `IntPtr` dans les signatures de méthode. `SafeHandle` remplace cette classe et doit être utilisé à la place.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) permet d’épingler un objet géré et d’y associer le pointeur natif. En voici le modèle de base :

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

L’épinglage n’est pas le comportement par défaut de `GCHandle`. L’autre grand modèle sert à faire passer une référence à un objet géré à travers le code natif, puis à nouveau au code managé, en général avec un rappel. En voici le modèle :

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

N’oubliez pas que `GCHandle` doit être explicitement libéré pour éviter les fuites de mémoire.

## <a name="common-windows-data-types"></a>Types de données Windows courants

Voici la liste des types de données courants dans les API Windows et des types C# à utiliser pour les appels dans le code Windows.

Malgré leur nom, les types suivants ont la même taille sur Windows 32 bits et 64 bits.

| Largeur | Windows          | C (Windows)          | C#       | Alternative                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| 32    | `BOOL`           | `int`                | `int`    | `bool`                               |
| 8     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| 8     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| 8     | `CHAR`           | `char`               | `sbyte`  |                                      |
| 8     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| 16    | `SHORT`          | `short`              | `short`  |                                      |
| 16    | `CSHORT`         | `short`              | `short`  |                                      |
| 16    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| 16    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| 16    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| 32    | `INT`            | `int`                | `int`    |                                      |
| 32    | `LONG`           | `long`               | `int`    |                                      |
| 32    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| 32    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| 64    | `QWORD`          | `long long`          | `long`   |                                      |
| 64    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| 64    | `LONGLONG`       | `long long`          | `long`   |                                      |
| 64    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| 64    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| 32    | `HRESULT`        | `long`               | `int`    |                                      |
| 32    | `NTSTATUS`       | `long`               | `int`    |                                      |

Comme il s’agit de pointeurs, les types suivants suivent la largeur de la plateforme. Utilisez pour eux `IntPtr`/`UIntPtr`.

| Types de pointeurs signés (utilisez `IntPtr`) | Types de pointeurs non signés (utilisez `UIntPtr`) |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

Un `PVOID` Windows, qui correspond à un `void*` C, peut être marshalé comme `IntPtr` ou `UIntPtr` ; préférez `void*` dans la mesure du possible.

[Types de données Windows](/windows/desktop/WinProg/windows-data-types)

[plages de types de données](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Structs

Les structs managés sont créés sur la pile et ne sont pas supprimés tant que la méthode n’a pas retourné de valeur. Ils sont donc par définition « épinglés » (ils ne sont pas déplacés par le récupérateur de mémoire). Vous pouvez aussi prendre simplement l’adresse dans des blocs de code unsafe si le code natif n’utilise pas le pointeur après la fin de la méthode actuelle.

Les structs blittables sont beaucoup plus performants, car ils sont directement utilisables par la couche de marshaling. Essayez de rendre les structs blittables (par exemple, évitez `bool`). Pour plus d'informations, voir la section [Types blittables](#blittable-types).

*Si* le struct est blittable, utilisez `sizeof()` au lieu de `Marshal.SizeOf<MyStruct>()` pour obtenir de meilleures performances. Comme nous l’avons mentionné plus haut, vous pouvez valider que le type est blittable en essayant de créer un `GCHandle` épinglé. Si le type n’est pas une chaîne ou n’est pas considéré comme blittable, `GCHandle.Alloc` lèvera une `ArgumentException`.

Les pointeurs vers des structs dans les définitions doivent être passés en `ref` ou utiliser `unsafe` et `*`.

✔️ Faites correspondre le struct managé le plus fidèlement possible à la forme et aux noms utilisés dans la documentation ou l’en-tête officiel de la plateforme.

✔️ Utilisez le `sizeof()` C# au lieu de `Marshal.SizeOf<MyStruct>()` pour les structures blittable afin d’améliorer les performances.

Un tableau comme `INT_PTR Reserved1[2]` doit être marshalé en deux champs `IntPtr`, `Reserved1a` et `Reserved1b`. Lorsque le tableau natif est un type primitif, il est possible d’utiliser le mot clé `fixed` pour que le code soit un peu plus propre. Par exemple, `SYSTEM_PROCESS_INFORMATION` se présente ainsi dans l’en-tête natif :

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

On peut l’écrire ainsi en C# :

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

Toutefois, les mémoires tampons fixes présentent quelques pièges. Les mémoires tampons fixes de types non blittables ne sont pas marshalées correctement ; par conséquent, le tableau sur place doit être étendu à plusieurs champs différents. En outre, dans .NET Framework et .NET Core avant la version 3.0, si un struct contenant un champ de mémoire tampon fixe est imbriqué dans un struct non blittable, le champ de mémoire tampon fixe n’est pas marshalé correctement dans le code natif.
