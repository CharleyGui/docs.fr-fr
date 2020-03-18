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
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="16664-103">Personnalisation du marshaling de structures</span><span class="sxs-lookup"><span data-stu-id="16664-103">Customizing structure marshaling</span></span>

<span data-ttu-id="16664-104">Parfois, les règles de marshaling par défaut pour les structures ne sont pas exactement ce dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="16664-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="16664-105">Les runtimes .NET fournissent quelques points d’extension qui vous permettent de personnaliser la disposition de votre structure et la manière dont les champs sont marshalés.</span><span class="sxs-lookup"><span data-stu-id="16664-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="16664-106">Personnalisation de la disposition de structures</span><span class="sxs-lookup"><span data-stu-id="16664-106">Customizing structure layout</span></span>

<span data-ttu-id="16664-107">.NET fournit l’attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> et l’énumération <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> pour vous permettre de personnaliser la façon dont les champs sont placés en mémoire.</span><span class="sxs-lookup"><span data-stu-id="16664-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="16664-108">Les conseils suivants vous aideront à éviter les problèmes courants.</span><span class="sxs-lookup"><span data-stu-id="16664-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="16664-109">ENVISAGEZ de ✔️ d’utiliser `LayoutKind.Sequential` dans la mesure du possible.</span><span class="sxs-lookup"><span data-stu-id="16664-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="16664-110">FAITES ✔️ uniquement usage de `LayoutKind.Explicit` dans le marshaling lorsque votre struct natif a également une disposition explicite, par exemple une union.</span><span class="sxs-lookup"><span data-stu-id="16664-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="16664-111">❌AVOID `LayoutKind.Explicit` en utilisant lorsque les structures de marshaling sur les plates-formes non-Windows si vous avez besoin de cibler les temps d’exécution avant .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="16664-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="16664-112">Le temps d’exécution .NET Core avant 3.0 ne prend pas en charge le passage de structures explicites par valeur à des fonctions natives sur Intel ou AMD 64 bits non-Windows systèmes.</span><span class="sxs-lookup"><span data-stu-id="16664-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="16664-113">Toutefois, le runtime prend en charge le passage de structures par référence sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="16664-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="16664-114">Personnalisation du marshaling des champs booléens</span><span class="sxs-lookup"><span data-stu-id="16664-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="16664-115">Le code natif a de nombreuses représentations booléennes différentes.</span><span class="sxs-lookup"><span data-stu-id="16664-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="16664-116">Sur Windows uniquement, il y a trois façons de représenter des valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="16664-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="16664-117">Le runtime ne connaissant pas la définition native de votre structure, le mieux est faire une estimation sur la manière de marshaler vos valeurs booléennes.</span><span class="sxs-lookup"><span data-stu-id="16664-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="16664-118">Le runtime .NET fournit un moyen d’indiquer comment marshaler votre champ booléen.</span><span class="sxs-lookup"><span data-stu-id="16664-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="16664-119">Les exemples suivants montrent comment marshaler .NET `bool` pour différents types booléens natifs.</span><span class="sxs-lookup"><span data-stu-id="16664-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="16664-120">Boolean valeurs par défaut à marshaling comme un [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) natif 4-byte Win32 valeur comme indiqué dans l’exemple suivant:</span><span class="sxs-lookup"><span data-stu-id="16664-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="16664-121">Si vous souhaitez être explicite, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> pour obtenir le même comportement que ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="16664-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="16664-122">À l’aide des valeurs `UnmanagedType.U1` ou `UnmanagedType.I1` ci-dessous, vous pouvez indiquer au runtime de marshaler le champ `b` comme type `bool` natif sur 1 octet.</span><span class="sxs-lookup"><span data-stu-id="16664-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="16664-123">Sur Windows, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> pour indiquer au runtime de marshaler votre valeur booléenne dans une valeur `VARIANT_BOOL` sur 2 octets :</span><span class="sxs-lookup"><span data-stu-id="16664-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="16664-124">`VARIANT_BOOL` est différent de la plupart des types de bools dans `VARIANT_TRUE = -1` et `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="16664-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="16664-125">De plus, toutes les valeurs qui ne sont pas égales à `VARIANT_TRUE` sont considérées comme false.</span><span class="sxs-lookup"><span data-stu-id="16664-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="16664-126">Personnalisation du marshaling des champs de tableaux</span><span class="sxs-lookup"><span data-stu-id="16664-126">Customizing array field marshaling</span></span>

<span data-ttu-id="16664-127">.NET inclut également quelques façons de personnaliser le marshaling de tableaux.</span><span class="sxs-lookup"><span data-stu-id="16664-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="16664-128">Par défaut, .NET marshale des tableaux en tant que pointeur vers une liste contiguë d’éléments :</span><span class="sxs-lookup"><span data-stu-id="16664-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="16664-129">Si vous interagissez avec des API COM, vous devez marshaler des tableaux en tant qu’objets `SAFEARRAY*`.</span><span class="sxs-lookup"><span data-stu-id="16664-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="16664-130">Vous pouvez utiliser les valeurs <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> pour indiquer au runtime de marshaler un tableau en tant que `SAFEARRAY*` :</span><span class="sxs-lookup"><span data-stu-id="16664-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="16664-131">Si vous devez personnaliser le type d’élément dans le `SAFEARRAY`, vous pouvez utiliser les champs <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> et <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> pour personnaliser le type d’élément exacte du `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="16664-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="16664-132">Si vous devez marshaler le tableau sur place, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> pour indiquer au marshaleur de le faire.</span><span class="sxs-lookup"><span data-stu-id="16664-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="16664-133">Lorsque vous utilisez ce marshaling, vous devez également fournir une valeur au champ <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pour le nombre d’éléments du tableau afin que le runtime puisse allouer correctement de l’espace pour la structure.</span><span class="sxs-lookup"><span data-stu-id="16664-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="16664-134">.NET ne prend pas en charge le marshaling d’un champ de tableau de longueur variable en tant que membre de tableau flexible C99.</span><span class="sxs-lookup"><span data-stu-id="16664-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="16664-135">Personnalisation du marshaling des champs de chaînes</span><span class="sxs-lookup"><span data-stu-id="16664-135">Customizing string field marshaling</span></span>

<span data-ttu-id="16664-136">.NET fournit également un large éventail de personnalisations pour marshaler les champs de chaînes.</span><span class="sxs-lookup"><span data-stu-id="16664-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="16664-137">Par défaut, .NET marshale une chaîne en tant que pointeur vers une chaîne se terminant par Null.</span><span class="sxs-lookup"><span data-stu-id="16664-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="16664-138">L’encodage dépend de la valeur du champ <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> dans le <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16664-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="16664-139">Si aucun attribut n’est spécifié, l’encodage par défaut est un encodage ANSI.</span><span class="sxs-lookup"><span data-stu-id="16664-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="16664-140">Si vous devez utiliser différents codages pour les différents champs ou si vous préférez simplement être plus explicite dans votre définition de struct, vous pouvez utiliser les valeurs <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> ou <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> sur un attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16664-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="16664-141">Si vous voulez marshaler vos chaînes à l’aide de l’encodage UTF-8, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> dans votre <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="16664-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="16664-142">L’utilisation de <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requiert .NET Framework 4.7 (ou versions ultérieures) ou .NET Core 1.1 (ou versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="16664-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="16664-143">Elle n’est pas disponible dans .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="16664-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="16664-144">Si vous travaillez avec des API COM, vous devrez peut-être marshaler une chaîne comme `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="16664-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="16664-145">À l’aide de la valeur <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, vous pouvez marshaler une chaîne comme `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="16664-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="16664-146">Lorsque vous utilisez une API WinRT, vous devez marshaler une chaîne comme `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="16664-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="16664-147">À l’aide de la valeur <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, vous pouvez marshaler une chaîne comme `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="16664-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="16664-148">Si votre API vous oblige à passer la chaîne sur place dans la structure, vous pouvez utiliser la valeur <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16664-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="16664-149">Notez que l’encodage d’une chaîne marshalée par `ByValTStr` est déterminé à partir de l’attribut `CharSet`.</span><span class="sxs-lookup"><span data-stu-id="16664-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="16664-150">Ceci requiert en outre le passage d’une longueur de chaîne par le champ <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16664-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="16664-151">Personnalisation du marshaling de champs décimaux</span><span class="sxs-lookup"><span data-stu-id="16664-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="16664-152">Si vous travaillez sur Windows, vous pourriez rencontrer [ `CY` des `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) API qui utilisent le natif ou la structure.</span><span class="sxs-lookup"><span data-stu-id="16664-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="16664-153">Par défaut, les `decimal` commissaires de [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) type .NET à la structure indigène.</span><span class="sxs-lookup"><span data-stu-id="16664-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="16664-154">Toutefois, vous pouvez utiliser un <xref:System.Runtime.InteropServices.MarshalAsAttribute> avec la valeur <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> pour indiquer au marshaleur de convertir une valeur `decimal` en valeur `CY` native.</span><span class="sxs-lookup"><span data-stu-id="16664-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="16664-155">Marshaling de `System.Object`</span><span class="sxs-lookup"><span data-stu-id="16664-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="16664-156">Sur Windows, vous pouvez marshaler des champs de type `object` dans du code natif.</span><span class="sxs-lookup"><span data-stu-id="16664-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="16664-157">Vous pouvez marshaler ces champs dans l’un des trois types suivants :</span><span class="sxs-lookup"><span data-stu-id="16664-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="16664-158">Par défaut, un champ de type `object` sera marshalé dans un `IUnknown*` qui inclut l’objet dans un wrapper.</span><span class="sxs-lookup"><span data-stu-id="16664-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="16664-159">Si vous voulez marshaler un champ d’objet pour un `IDispatch*`, ajoutez un <xref:System.Runtime.InteropServices.MarshalAsAttribute> avec la valeur <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16664-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="16664-160">Si vous voulez le marshaler comme `VARIANT`, ajoutez un <xref:System.Runtime.InteropServices.MarshalAsAttribute> avec la valeur <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="16664-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="16664-161">Le tableau suivant décrit comment les différents types de runtime du champ `obj` correspondent aux différents types stockés dans un `VARIANT` :</span><span class="sxs-lookup"><span data-stu-id="16664-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="16664-162">Type .NET</span><span class="sxs-lookup"><span data-stu-id="16664-162">.NET Type</span></span> | <span data-ttu-id="16664-163">Type VARIANT</span><span class="sxs-lookup"><span data-stu-id="16664-163">VARIANT Type</span></span> | | <span data-ttu-id="16664-164">Type .NET</span><span class="sxs-lookup"><span data-stu-id="16664-164">.NET Type</span></span> | <span data-ttu-id="16664-165">Type VARIANT</span><span class="sxs-lookup"><span data-stu-id="16664-165">VARIANT Type</span></span> |
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
