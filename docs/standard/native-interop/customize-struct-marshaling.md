---
title: Personnalisation du marshaling de structures - .NET
description: Découvrez comment personnaliser la façon dont .NET marshale vos structures en une représentation native.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7f8d1ad93633d6feef9c3c6f5d19aad52105968c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400371"
---
# <a name="customizing-structure-marshaling"></a>Personnalisation du marshaling de structures

Parfois, les règles de marshaling par défaut pour les structures ne sont pas exactement ce dont vous avez besoin. Les runtimes .NET fournissent quelques points d’extension qui vous permettent de personnaliser la disposition de votre structure et la manière dont les champs sont marshalés.

## <a name="customizing-structure-layout"></a>Personnalisation de la disposition de structures

.NET fournit l’attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> et l’énumération <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> pour vous permettre de personnaliser la façon dont les champs sont placés en mémoire. Les conseils suivants vous aideront à éviter les problèmes courants.

ENVISAGEZ de ✔️ d’utiliser `LayoutKind.Sequential` dans la mesure du possible.

FAITES ✔️ uniquement usage de `LayoutKind.Explicit` dans le marshaling lorsque votre struct natif a également une disposition explicite, par exemple une union.

❌Évitez d' `LayoutKind.Explicit` utiliser lors du marshaling de structures sur des plateformes non-Windows si vous devez cibler des runtimes avant .net Core 3,0. Le Runtime .NET Core avant 3,0 ne prend pas en charge le passage de structures explicites par valeur aux fonctions natives sur les systèmes Intel ou AMD 64 bits non-Windows. Toutefois, le runtime prend en charge le passage de structures par référence sur toutes les plateformes.

## <a name="customizing-boolean-field-marshaling"></a>Personnalisation du marshaling des champs booléens

Le code natif a de nombreuses représentations booléennes différentes. Sur Windows uniquement, il y a trois façons de représenter des valeurs booléennes. Le runtime ne connaissant pas la définition native de votre structure, le mieux est faire une estimation sur la manière de marshaler vos valeurs booléennes. Le runtime .NET fournit un moyen d’indiquer comment marshaler votre champ booléen. Les exemples suivants montrent comment marshaler .NET `bool` pour différents types booléens natifs.

Les valeurs booléennes sont marshalées par défaut en tant que valeur [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) Win32 sur 4 octets native, comme indiqué dans l’exemple suivant :

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

Si vous souhaitez être explicite, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> pour obtenir le même comportement que ci-dessus :

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

À l’aide des valeurs `UnmanagedType.U1` ou `UnmanagedType.I1` ci-dessous, vous pouvez indiquer au runtime de marshaler le champ `b` comme type `bool` natif sur 1 octet.

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

Sur Windows, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> pour indiquer au runtime de marshaler votre valeur booléenne dans une valeur `VARIANT_BOOL` sur 2 octets :

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> `VARIANT_BOOL` est différent de la plupart des types de bools dans `VARIANT_TRUE = -1` et `VARIANT_FALSE = 0`. De plus, toutes les valeurs qui ne sont pas égales à `VARIANT_TRUE` sont considérées comme false.

## <a name="customizing-array-field-marshaling"></a>Personnalisation du marshaling des champs de tableaux

.NET inclut également quelques façons de personnaliser le marshaling de tableaux.

Par défaut, .NET marshale des tableaux en tant que pointeur vers une liste contiguë d’éléments :

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

Si vous interagissez avec des API COM, vous devez marshaler des tableaux en tant qu’objets `SAFEARRAY*`. Vous pouvez utiliser les valeurs <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> pour indiquer au runtime de marshaler un tableau en tant que `SAFEARRAY*` :

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

Si vous devez personnaliser le type d’élément dans le `SAFEARRAY`, vous pouvez utiliser les champs <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> pour personnaliser le type d’élément exacte du `SAFEARRAY`.

Si vous devez marshaler le tableau sur place, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> pour indiquer au marshaleur de le faire. Lorsque vous utilisez ce marshaling, vous devez également fournir une valeur au champ <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pour le nombre d’éléments du tableau afin que le runtime puisse allouer correctement de l’espace pour la structure.

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> .NET ne prend pas en charge le marshaling d’un champ de tableau de longueur variable en tant que membre de tableau flexible C99.

## <a name="customizing-string-field-marshaling"></a>Personnalisation du marshaling des champs de chaînes

.NET fournit également un large éventail de personnalisations pour marshaler les champs de chaînes.

Par défaut, .NET marshale une chaîne en tant que pointeur vers une chaîne se terminant par Null. L’encodage dépend de la valeur du champ <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> dans le <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>. Si aucun attribut n’est spécifié, l’encodage par défaut est un encodage ANSI.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

Si vous devez utiliser différents codages pour les différents champs ou si vous préférez simplement être plus explicite dans votre définition de struct, vous pouvez utiliser les valeurs <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> ou <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> sur un attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

Si vous voulez marshaler vos chaînes à l’aide de l’encodage UTF-8, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> dans votre <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> L’utilisation de <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requiert .NET Framework 4.7 (ou versions ultérieures) ou .NET Core 1.1 (ou versions ultérieures). Elle n’est pas disponible dans .NET Standard 2.0.

Si vous travaillez avec des API COM, vous devrez peut-être marshaler une chaîne comme `BSTR`. À l’aide de la valeur <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, vous pouvez marshaler une chaîne comme `BSTR`.

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

Lorsque vous utilisez une API WinRT, vous devez marshaler une chaîne comme `HSTRING`.  À l’aide de la valeur <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, vous pouvez marshaler une chaîne comme `HSTRING`.

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

Si votre API vous oblige à passer la chaîne sur place dans la structure, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>. Notez que l’encodage d’une chaîne marshalée par `ByValTStr` est déterminé à partir de l’attribut `CharSet`. Ceci requiert en outre le passage d’une longueur de chaîne par le champ <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType>.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshaling"></a>Personnalisation du marshaling de champs décimaux

Si vous travaillez sur Windows, vous pouvez rencontrer des API qui utilisent la structure [ `CY` ou `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) native. Par défaut, le type `decimal` .net est marshalé à la [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure native. Toutefois, vous pouvez utiliser un <xref:System.Runtime.InteropServices.MarshalAsAttribute> avec la valeur <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> pour indiquer au marshaleur de convertir une valeur `decimal` en valeur `CY` native.

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshaling-systemobjects"></a>Marshaling de `System.Object`

Sur Windows, vous pouvez marshaler des champs de type `object` dans du code natif. Vous pouvez marshaler ces champs dans l’un des trois types suivants :

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Par défaut, un champ de type `object` sera marshalé dans un `IUnknown*` qui inclut l’objet dans un wrapper.

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

Si vous voulez marshaler un champ d’objet pour un `IDispatch*`, ajoutez un <xref:System.Runtime.InteropServices.MarshalAsAttribute> avec la valeur <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

Si vous voulez le marshaler comme `VARIANT`, ajoutez un <xref:System.Runtime.InteropServices.MarshalAsAttribute> avec la valeur <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

Le tableau suivant décrit comment les différents types de runtime du champ `obj` correspondent aux différents types stockés dans un `VARIANT` :

| Type .NET | Type VARIANT | | Type .NET | Type VARIANT |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|
