---
title: Marshaling de types - .NET
description: Découvrez comment .NET marshale vos types en une représentation native.
ms.date: 01/18/2019
ms.openlocfilehash: 91b8f3d6cb53fd7a0adea7ea9669e7459e81445f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706264"
---
# <a name="type-marshaling"></a>Marshaling de types

Le **marshaling** est le processus qui consiste à transformer les types quand ils doivent naviguer entre du code managé et du code natif.

La raison pour laquelle le marshaling est nécessaire est que les types diffèrent entre le code managé et le code non managé. Dans le code managé, par exemple, vous avez `String`un, tandis que dans les chaînes universelles non managées peuvent être Unicode (« larges »), non-Unicode, terminé par null, ASCII, etc. Par défaut, le sous-système P/Invoke tente d’effectuer la bonne chose en fonction du comportement par défaut, décrit dans cet article. Toutefois, dans les cas où vous avez besoin de plus de contrôle, vous pouvez employer l’attribut [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) pour spécifier le type attendu du côté du code non managé. Par exemple, pour que la chaîne soit envoyée sous forme de chaîne ANSI terminée par Null, vous pouvez procéder ainsi :

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

## <a name="default-rules-for-marshaling-common-types"></a>Règles par défaut de marshaling des types courants

En règle générale, le runtime tente de prendre la bonne décision en matière de marshaling, c’est-à-dire celle qui demande le moins de travail de votre part. Les tableaux suivants indiquent comment chaque type est marshalé par défaut lorsqu’il est utilisé dans un paramètre ou un champ. Les types de caractères et d’entiers de longueur fixe C99/C ++11 garantissent que le tableau suivant est correct pour toutes les plateformes. Vous pouvez utiliser n’importe quel type natif ayant les mêmes exigence d’alignement et de taille que ces types.

Le premier tableau décrit les correspondances de différents types pour lesquels le marshaling P/Invoke et le marshaling des champs sont identiques.

| Type .NET | Type natif  |
|-----------|-------------------------|
| `byte`    | `uint8_t`               |
| `sbyte`   | `int8_t`                |
| `short`   | `int16_t`               |
| `ushort`  | `uint16_t`              |
| `int`     | `int32_t`               |
| `uint`    | `uint32_t`              |
| `long`    | `int64_t`               |
| `ulong`   | `uint64_t`              |
| `char`    | `char` ou `char16_t` selon le `CharSet` de P/Invoke ou de la structure. Voir la [documentation charset](charset.md). |
| `string`  | `char*` ou `char16_t*` selon le `CharSet` de P/Invoke ou de la structure. Voir la [documentation charset](charset.md). |
| `System.IntPtr` | `intptr_t`        |
| `System.UIntPtr` | `uintptr_t`      |
| Types pointeur .NET (p. ex., `void*`)  | `void*` |
| Type dérivé de `System.Runtime.InteropServices.SafeHandle` | `void*` |
| Type dérivé de `System.Runtime.InteropServices.CriticalHandle` | `void*`          |
| `bool`    | Type `BOOL` Win32       |
| `decimal` | Struct `DECIMAL` COM |
| Délégué .NET | Pointeur de fonction natif |
| `System.DateTime` | Type `DATE` Win32 |
| `System.Guid` | Type `GUID` Win32 |

Certaines catégories ont des valeurs par défaut différentes pour le marshaling comme paramètre ou comme structure.

| Type .NET | Type natif (paramètre) | Type natif (champ) |
|-----------|-------------------------|---------------------|
| Tableau .NET | Pointeur vers le début d’un tableau de représentations natives des éléments du tableau | Non autorisé sans attribut `[MarshalAs]`|
| Classe avec `LayoutKind` de `Sequential` ou de `Explicit` | Pointeur vers la représentation native de la classe | Représentation native de la classe |

Le tableau suivant présente les règles de marshaling par défaut propres à Windows. Sur les autres plateformes, il n’est pas possible de marshaler ces types.

| Type .NET | Type natif (paramètre) | Type natif (champ) |
|-----------|-------------------------|---------------------|
| `object`  | `VARIANT`               | `IUnknown*`         |
| `System.Array` | Interface COM | Non autorisé sans attribut `[MarshalAs]` |
| `System.ArgIterator` | `va_list` | Non autorisé |
| `System.Collections.IEnumerator` | `IEnumVARIANT*` | Non autorisé |
| `System.Collections.IEnumerable` | `IDispatch*` | Non autorisé |
| `System.DateTimeOffset` |  représentant le nombre de cycles depuis le 1er janvier 1601 à minuit ||  représentant le nombre de cycles depuis le 1er janvier 1601 à minuit |

Certains types ne peuvent être marshalés que comme paramètres, et non comme champs. :

| Type .NET | Type natif (paramètre uniquement) |
|-----------|------------------------------|
| `System.Text.StringBuilder` | `char*` ou `char16_t*` selon le `CharSet` de P/Invoke.  Voir la [documentation charset](charset.md). |
| `System.ArgIterator` | `va_list` (sur Windows x86/x64/arm64 uniquement) |
| `System.Runtime.InteropServices.ArrayWithOffset` | `void*` |
| `System.Runtime.InteropServices.HandleRef` | `void*` |

Si ces valeurs par défaut ne vous conviennent pas tout à fait, vous pouvez personnaliser la façon dont les paramètres sont marshalés. L’article [Marshaling des paramètres](customize-parameter-marshaling.md) explique comment faire, pour différents types de paramètres.

## <a name="default-marshaling-in-com-scenarios"></a>Marshaling par défaut dans les scénarios COM

Quand vous appelez des méthodes sur des objets COM dans .NET, le runtime .NET modifie les règles de marshaling par défaut pour qu’elles correspondent à la sémantique COM courante. Le tableau suivant liste les règles utilisées par les runtimes .NET dans les scénarios COM :

| Type .NET | Type natif (appels de méthodes COM) |
|-----------|--------------------------------|
| `bool`    | `VARIANT_BOOL`                 |
| `StringBuilder` | `LPWSTR`                 |
| `string`  | `BSTR`                         |
| Types délégués | `_Delegate*` dans le .NET Framework. Interdits dans .NET Core. |
| `System.Drawing.Color` | `OLECOLOR`        |
| Tableau .NET | `SAFEARRAY`                   |
| `string[]` | `SAFEARRAY` de `BSTR`s        |

## <a name="marshaling-classes-and-structs"></a>Marshaling de classes et de structures

Un autre aspect du marshaling de types consiste à passer une structure à une méthode non managée. Par exemple, certaines des méthodes non managées nécessitent une structure comme paramètre. Il faut dans ce cas créer une classe ou un struct correspondant dans la partie managée de l’environnement pour l’utiliser comme paramètre. Toutefois, il ne suffit pas de définir la classe : il est également nécessaire d’indiquer au marshaleur comment mapper des champs de la classe au struct non managé. C’est ici qu’intervient l’attribut `StructLayout`.

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

Le code précédent illustre de manière simple les appels dans la fonction `GetSystemTime()`. L’élément digne d’intérêt se trouve sur la ligne 4. L’attribut spécifie que les champs de la classe doivent être mappés séquentiellement à la structure de l’autre côté (non managé). Cela signifie que le nom des champs n’a pas d’importance ; seul leur ordre compte, car il doit correspondre au struct non managé, comme dans l’exemple suivant :

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME;
```

Il est possible que le marshaling par défaut de votre structure ne vous convienne pas. L’article [Personnaliser le marshaling des structures](./customize-struct-marshaling.md) explique comment personnaliser la façon dont les structures sont marshalées.
