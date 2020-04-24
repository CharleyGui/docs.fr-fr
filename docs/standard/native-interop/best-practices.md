---
title: Meilleures pratiques pour l’interopérabilité native – .NET
description: Découvrez les meilleures pratiques pour interagir avec des composants natifs en .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391219"
---
# <a name="native-interoperability-best-practices"></a>Meilleures pratiques pour l’interopérabilité native

.NET propose différents moyens de personnaliser du code d’interopérabilité native. Cet article détaille les instructions suivies par les équipes .NET de Microsoft pour l’interopérabilité native.

## <a name="general-guidance"></a>Règle générale

Les instructions de cette section s’appliquent à tous les scénarios d’interopérabilité.

- ✔️ À FAIRE : utilisez les mêmes noms et la même mise en majuscules pour vos méthodes que pour la méthode native que vous souhaitez appeler.
- ✔️ À ENVISAGER : utiliser les mêmes noms et la même mise en majuscules pour les valeurs constantes.
- ✔️ À FAIRE : utilisez les types .NET les plus proches d’une correspondance avec le type natif. Par exemple, en C#, utilisez `uint` lorsque le type natif est `unsigned int`.
- ✔️ À FAIRE : n’utilisez les attributs `[In]` et `[Out]` que si le comportement souhaité diffère du comportement par défaut.
- ✔️ À ENVISAGER : utiliser <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pour regrouper les mémoires tampons du tableau natif.
- ✔️ À ENVISAGER : encapsuler les déclarations P/Invoke dans une classe portant le même nom et utilisant la même mise en majuscules que votre bibliothèque native.
  - Vos attributs `[DllImport]` pourront ainsi utiliser la fonctionnalité `nameof` du langage C# pour transmettre le nom de la bibliothèque native et vérifier qu’il ne comporte pas d’erreur.

## <a name="dllimport-attribute-settings"></a>Paramètres des attributs DllImport

| Paramètre | Par défaut | Recommandation | Détails |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  Conserver la valeur par défaut  | S’il est défini explicitement sur false, les valeurs de retour HRESULT en échec sont converties en exceptions (et la valeur de retour de la définition devient ainsi Null).|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | Dépend de l'API  | Définissez-le sur true si l’API utilise GetLastError et Marshal.GetLastWin32Error pour obtenir la valeur. Si l’API définit une condition indiquant une erreur, récupérez l’erreur avant d’effectuer d’autres appels, de façon à éviter de la remplacer par inadvertance.|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | `CharSet.None`, qui bascule en secours vers le comportement `CharSet.Ansi`  | Utilisez explicitement `CharSet.Unicode` ou `CharSet.Ansi` lorsque des chaînes ou des caractères sont présents dans la définition | Cela permet de spécifier le comportement de marshaling des chaînes et le rôle de `ExactSpelling` quand la valeur est `false`. Notez que `CharSet.Ansi` est en réalité UTF-8 sur Unix. _La plupart du temps_, Windows utilise Unicode et Unix UTF-8. Pour plus d'informations, voir la [documentation sur les charsets](./charset.md). |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | Définissez-le sur true pour augmenter légèrement les performances. En effet, le runtime ne recherche pas de noms de fonctions de remplacement avec un suffixe « A » ou « W » selon la valeur du paramètre `CharSet` (« A » pour `CharSet.Ansi` et « W » pour `CharSet.Unicode`). |

## <a name="string-parameters"></a>Paramètre de chaîne

Lorsque le charset est Unicode ou que l’argument est explicitement marqué comme `[MarshalAs(UnmanagedType.LPWSTR)]` _et_ que la chaîne est passée en valeur (pas `ref` ou `out`), la chaîne est épinglée et utilisée directement par le code natif (et non copiée).

N’oubliez pas de marquer `[DllImport]` comme `Charset.Unicode` sauf si vous souhaitez explicitement un traitement ANSI de vos chaînes.

❌N’utilisez `[Out] string` pas de paramètres. Les paramètres de chaînes passés en valeur avec l’attribut `[Out]` risquent de déstabiliser le runtime s’il s’agit de chaînes centralisées. Pour plus d’informations sur la centralisation des chaînes, voir la documentation de <xref:System.String.Intern%2A?displayProperty=nameWithType>.

❌Évitez `StringBuilder` les paramètres. Le marshaling `StringBuilder` crée *toujours* une copie de la mémoire tampon native. Il peut donc se révéler extrêmement inefficace. Prenons le scénario classique d’appel d’une API Windows qui prend une chaîne :

1. Créer un SB de la capacité souhaitée (alloue la capacité managée)**{1}**
2. Appeler
   1. Alloue une mémoire tampon Native**{2}**
   2. Copie le contenu si `[In]` _(valeur par défaut d’un paramètre `StringBuilder`)_
   3. Copie la mémoire tampon native dans un tableau managé nouvellement alloué si `[Out]` **{3}** _(valeur par défaut de `StringBuilder` également)_
3. `ToString()`alloue un autre groupe géré**{4}**

Il s' *{4}* agit des allocations pour obtenir une chaîne à partir du code natif. Le mieux que l’on puisse faire pour réduire ce nombre est de réutiliser `StringBuilder` dans un autre appel, mais cela ne fait gagner que *1* allocation. Il est largement préférable d’utiliser et de mettre en cache une mémoire tampon de caractères à partir de `ArrayPool` : vous pourrez limiter l’allocation à `ToString()` lors des appels suivants.

L’autre problème de `StringBuilder` est qu’il copie toujours la sauvegarde de la mémoire tampon de retour sur la première valeur Null. Si la chaîne de retour transmise n’est pas terminée ou se termine par un double Null, P/Invoke est au mieux incorrect.

Si vous *utilisez*`StringBuilder`, le dernier piège est que la capacité n’inclut **pas** de valeur Null masquée, qui est toujours prise en compte dans l’interopérabilité. Il est courant de se tromper de ce point de vue, car la plupart des API demandent la taille de la mémoire tampon valeur Null *incluse*. Il en résulte parfois des allocations gaspillées/inutiles. En outre, cet écueil empêche le runtime d’optimiser le marshaling `StringBuilder` afin de réduire les copies.

✔️ À ENVISAGER : utiliser des `char[]` à partir d’un `ArrayPool`.

Pour plus d’informations sur le marshaling des chaînes, consultez [Marshaling par défaut pour les chaînes](../../framework/interop/default-marshaling-for-strings.md) et [Personnaliser le marshaling des chaînes](customize-parameter-marshaling.md#customizing-string-parameters).

> __Spécifique à Windows__ Pour `[Out]` les chaînes que le CLR `CoTaskMemFree` utilisera par défaut pour libérer `SysStringFree` des chaînes ou pour les chaînes `UnmanagedType.BSTR`qui sont marquées comme.
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

❌N’utilisez `[MarshalAs(UnmanagedType.LPStruct)]` pas pour les paramètres de `ref` GUID.

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

Une `string` est blittable si elle n’est pas contenue dans un autre type et qu’elle est passé en argument marqué `[MarshalAs(UnmanagedType.LPWStr)]` ou que `CharSet = CharSet.Unicode` est défini pour `[DllImport]`.

Pour savoir si un type est blittable, essayez de créer un `GCHandle` épinglé. Si le type n’est pas une chaîne ou n’est pas considéré comme blittable, `GCHandle.Alloc` lèvera une `ArgumentException`.

✔️ À FAIRE : rendez vos structures blittables dans la mesure du possible.

Pour plus d’informations, voir :

- [types blittable et non blittable](../../framework/interop/blittable-and-non-blittable-types.md)
- [Marshaling de type](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a>Maintenir actifs les objets gérés

`GC.KeepAlive()` garantit qu'un objet reste accessible jusqu'à ce que la méthode KeepAlive soit atteinte.

[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)permet au marshaleur de conserver un objet actif pendant la durée d’un appel P/Invoke. Il peut être utilisé à la place de `IntPtr` dans les signatures de méthode. `SafeHandle` remplace cette classe et doit être utilisé à la place.

[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)autorise l’épinglage d’un objet managé et l’obtention du pointeur natif vers celui-ci. En voici le modèle de base :

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

[Plages de types de données](/cpp/cpp/data-type-ranges)

## <a name="structs"></a>Structs

Les structs managés sont créés sur la pile et ne sont pas supprimés tant que la méthode n’a pas retourné de valeur. Ils sont donc par définition « épinglés » (ils ne sont pas déplacés par le récupérateur de mémoire). Vous pouvez aussi prendre simplement l’adresse dans des blocs de code unsafe si le code natif n’utilise pas le pointeur après la fin de la méthode actuelle.

Les structs blittables sont beaucoup plus performants, car ils sont directement utilisables par la couche de marshaling. Essayez de rendre les structs blittables (par exemple, évitez `bool`). Pour plus d'informations, voir la section [Types blittables](#blittable-types).

*Si* le struct est blittable, utilisez `sizeof()` au lieu de `Marshal.SizeOf<MyStruct>()` pour obtenir de meilleures performances. Comme nous l’avons mentionné plus haut, vous pouvez valider que le type est blittable en essayant de créer un `GCHandle` épinglé. Si le type n’est pas une chaîne ou n’est pas considéré comme blittable, `GCHandle.Alloc` lèvera une `ArgumentException`.

Les pointeurs vers des structs dans les définitions doivent être passés en `ref` ou utiliser `unsafe` et `*`.

✔️ À FAIRE : faites correspondre le struct managé aussi fidèlement que possible à la forme et aux noms utilisés dans l’en-tête ou dans la documentation officielle de la plateforme.

✔️ À FAIRE : utilisez le `sizeof()` C# au lieu de `Marshal.SizeOf<MyStruct>()` pour les structures blittables afin d’améliorer les performances.

❌Évitez d' `System.Delegate` utiliser `System.MulticastDelegate` des champs ou pour représenter des champs de pointeur de fonction dans des structures.

Étant <xref:System.Delegate?displayProperty=fullName> donné <xref:System.MulticastDelegate?displayProperty=fullName> que et n’ont pas de signature obligatoire, elles ne garantissent pas que le délégué passé correspond à la signature attendue par le code natif. En outre, dans .NET Framework et .NET Core, le marshaling d’un struct `System.Delegate` contenant `System.MulticastDelegate` un ou à partir de sa représentation native vers un objet managé peut déstabiliser le runtime si la valeur du champ dans la représentation native n’est pas un pointeur de fonction qui encapsule un délégué managé. Dans .NET 5 et versions ultérieures, le marshaling d’un `System.Delegate` champ ou `System.MulticastDelegate` d’une représentation native vers un objet managé n’est pas pris en charge. Utilisez un type délégué spécifique au lieu `System.Delegate` de `System.MulticastDelegate`ou.

### <a name="fixed-buffers"></a>Mémoires tampons fixes

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
