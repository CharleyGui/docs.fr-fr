---
title: Marshaling par défaut pour les chaînes
description: Examinez le comportement de marshaling par défaut pour les chaînes d’interfaces, d’appel de code non managé, de structures & de mémoires tampons de chaînes de longueur fixe dans .NET.
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
ms.openlocfilehash: 81df2dcc132c8ce057fa3e0e7d0ad04832f7a48b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555053"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="736c5-103">Marshaling par défaut pour les chaînes</span><span class="sxs-lookup"><span data-stu-id="736c5-103">Default Marshaling for Strings</span></span>

<span data-ttu-id="736c5-104">Les classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> ont un comportement de marshaling semblable.</span><span class="sxs-lookup"><span data-stu-id="736c5-104">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="736c5-105">Les chaînes sont marshalées en tant que type `BSTR` de style COM ou comme une chaîne se terminant par un caractère Null (un tableau de caractères se terminant par un caractère Null).</span><span class="sxs-lookup"><span data-stu-id="736c5-105">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="736c5-106">Les caractères de la chaîne peuvent être marshalés en tant que caractères Unicode (valeur par défaut sur les systèmes Windows) ou ANSI.</span><span class="sxs-lookup"><span data-stu-id="736c5-106">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="736c5-107">Chaînes utilisées dans les interfaces</span><span class="sxs-lookup"><span data-stu-id="736c5-107">Strings Used in Interfaces</span></span>

<span data-ttu-id="736c5-108">Le tableau suivant montre les options de marshaling pour le type de données String quand il est marshalé comme un argument de méthode du code non managé.</span><span class="sxs-lookup"><span data-stu-id="736c5-108">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="736c5-109">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler des chaînes d'interfaces COM.</span><span class="sxs-lookup"><span data-stu-id="736c5-109">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="736c5-110">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="736c5-110">Enumeration type</span></span>|<span data-ttu-id="736c5-111">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="736c5-111">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="736c5-112">`UnmanagedType.BStr` (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="736c5-112">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="736c5-113">`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="736c5-113">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="736c5-114">Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="736c5-114">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="736c5-115">Pointeur vers un tableau de caractères Unicode terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="736c5-115">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="736c5-116">Ce tableau s’applique à <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="736c5-116">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="736c5-117">Pour <xref:System.Text.StringBuilder>, les seules options autorisées sont `UnmanagedType.LPStr` et `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="736c5-117">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="736c5-118">L'exemple suivant montre des chaînes déclarées dans l'interface `IStringWorker`.</span><span class="sxs-lookup"><span data-stu-id="736c5-118">The following example shows strings declared in the `IStringWorker` interface.</span></span>

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

<span data-ttu-id="736c5-119">L'exemple suivant montre l'interface correspondante décrite dans une bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="736c5-119">The following example shows the corresponding interface described in a type library.</span></span>

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="736c5-120">Chaînes utilisées dans les appels de code non managé</span><span class="sxs-lookup"><span data-stu-id="736c5-120">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="736c5-121">L'appel de code non managé copie des arguments de chaîne, en convertissant du format .NET Framework (Unicode) au format non managé de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="736c5-121">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="736c5-122">Les chaînes sont immuables et ne sont pas copiées depuis la mémoire non managée vers la mémoire managée quand l'appel est retourné.</span><span class="sxs-lookup"><span data-stu-id="736c5-122">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="736c5-123">Le tableau suivant répertorie les options de marshaling pour les chaînes quand celles-ci sont marshalées comme un argument de méthode d'un appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="736c5-123">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="736c5-124">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les chaînes.</span><span class="sxs-lookup"><span data-stu-id="736c5-124">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="736c5-125">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="736c5-125">Enumeration type</span></span>|<span data-ttu-id="736c5-126">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="736c5-126">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="736c5-127">`BSTR` de style COM avec une longueur prédéfinie et des caractères ANSI.</span><span class="sxs-lookup"><span data-stu-id="736c5-127">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="736c5-128">`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="736c5-128">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="736c5-129">`UnmanagedType.LPStr` (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="736c5-129">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="736c5-130">Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="736c5-130">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="736c5-131">Pointeur vers un tableau de caractères dépendant de la plateforme se terminant par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="736c5-131">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="736c5-132">Pointeur vers un tableau de caractères encodés UTF-8 terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="736c5-132">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="736c5-133">Pointeur vers un tableau de caractères Unicode terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="736c5-133">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="736c5-134">`BSTR` de style COM de longueur fixe avec des caractères dépendant de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="736c5-134">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="736c5-135">Valeur qui permet à Visual Basic .NET de changer une chaîne dans du code non managé et de répercuter les résultats dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="736c5-135">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="736c5-136">Cette valeur est prise en charge uniquement pour l'appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="736c5-136">This value is supported only for platform invoke.</span></span> <span data-ttu-id="736c5-137">Il s’agit de la valeur par défaut dans Visual Basic pour les chaînes `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="736c5-137">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="736c5-138">Ce tableau s’applique à <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="736c5-138">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="736c5-139">Pour <xref:System.Text.StringBuilder>, les seules options autorisées sont `LPStr`, `LPTStr` et `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="736c5-139">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="736c5-140">La définition de type suivante montre une utilisation correcte de `MarshalAsAttribute` pour les appels de code non managé.</span><span class="sxs-lookup"><span data-stu-id="736c5-140">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="736c5-141">Chaînes utilisées dans les structures</span><span class="sxs-lookup"><span data-stu-id="736c5-141">Strings Used in Structures</span></span>

<span data-ttu-id="736c5-142">Les chaînes sont des membres valides de structures. Toutefois, les mémoires tampons <xref:System.Text.StringBuilder> ne sont pas valides dans les structures.</span><span class="sxs-lookup"><span data-stu-id="736c5-142">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="736c5-143">Le tableau suivant montre les options de marshaling pour le type de données <xref:System.String> quand le type est marshalé en tant que champ.</span><span class="sxs-lookup"><span data-stu-id="736c5-143">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="736c5-144">L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les chaînes en tant que champ.</span><span class="sxs-lookup"><span data-stu-id="736c5-144">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="736c5-145">Type d'énumération</span><span class="sxs-lookup"><span data-stu-id="736c5-145">Enumeration type</span></span>|<span data-ttu-id="736c5-146">Description du format non managé</span><span class="sxs-lookup"><span data-stu-id="736c5-146">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="736c5-147">`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.</span><span class="sxs-lookup"><span data-stu-id="736c5-147">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="736c5-148">`UnmanagedType.LPStr` (valeur par défaut)</span><span class="sxs-lookup"><span data-stu-id="736c5-148">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="736c5-149">Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="736c5-149">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="736c5-150">Pointeur vers un tableau de caractères dépendant de la plateforme se terminant par un caractère Null.</span><span class="sxs-lookup"><span data-stu-id="736c5-150">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="736c5-151">Pointeur vers un tableau de caractères encodés UTF-8 terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="736c5-151">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="736c5-152">Pointeur vers un tableau de caractères Unicode terminé par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="736c5-152">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="736c5-153">Tableau de caractères de longueur fixe. Le type du tableau est déterminé par le jeu de caractères de la structure contenante.</span><span class="sxs-lookup"><span data-stu-id="736c5-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="736c5-154">Le type `ByValTStr` est utilisé pour les tableaux de caractères inline de longueur fixe qui sont situés dans une structure.</span><span class="sxs-lookup"><span data-stu-id="736c5-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="736c5-155">D'autres types s'appliquent aux références de chaîne contenues au sein de structures qui contiennent des pointeurs vers des chaînes.</span><span class="sxs-lookup"><span data-stu-id="736c5-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="736c5-156">L’argument `CharSet` du <xref:System.Runtime.InteropServices.StructLayoutAttribute> qui est appliqué à la structure contenante détermine le format de caractères des chaînes des structures.</span><span class="sxs-lookup"><span data-stu-id="736c5-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="736c5-157">Les exemples de structures suivants contiennent des références de chaîne et des chaînes inline, ainsi que des caractères ANSI, Unicode et dépendant de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="736c5-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="736c5-158">La représentation de ces structures dans une bibliothèque de types est illustrée dans l’exemple de code C++ suivant :</span><span class="sxs-lookup"><span data-stu-id="736c5-158">The representation of these structures in a type library is shown in the following C++ code:</span></span>

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

<span data-ttu-id="736c5-159">L’exemple suivant montre comment utiliser le <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour définir une même structure dans des formats différents.</span><span class="sxs-lookup"><span data-stu-id="736c5-159">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

```vb
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _
Structure StringInfoA
    <MarshalAs(UnmanagedType.LPStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
End Structure

<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _
Structure StringInfoW
    <MarshalAs(UnmanagedType.LPWStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
<MarshalAs(UnmanagedType.BStr)> Public f3 As String
End Structure

<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _
Structure StringInfoT
    <MarshalAs(UnmanagedType.LPTStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
End Structure
```

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="736c5-160">Mémoires tampons de chaînes de longueur fixe</span><span class="sxs-lookup"><span data-stu-id="736c5-160">Fixed-Length String Buffers</span></span>

<span data-ttu-id="736c5-161">Dans certains cas, une mémoire tampon de caractères de longueur fixe doit être passée à du code non managé pour pouvoir être manipulée.</span><span class="sxs-lookup"><span data-stu-id="736c5-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="736c5-162">Le fait de passer une chaîne ne fonctionne pas dans ce cas, car l'appelé ne peut pas modifier le contenu de la mémoire tampon passée.</span><span class="sxs-lookup"><span data-stu-id="736c5-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="736c5-163">Même si la chaîne est passée par référence, il est impossible d'initialiser la mémoire tampon à une taille donnée.</span><span class="sxs-lookup"><span data-stu-id="736c5-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="736c5-164">La solution consiste à passer une mémoire tampon <xref:System.Text.StringBuilder> comme argument plutôt que comme <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="736c5-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="736c5-165">Un `StringBuilder` peut être déréférencé et modifié par l'appelé à condition qu'il ne dépasse pas la capacité de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="736c5-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="736c5-166">Il peut également être initialisé à une longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="736c5-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="736c5-167">Par exemple, si vous initialisez une mémoire tampon `StringBuilder` avec une capacité de `N`, le marshaleur fournira une mémoire tampon de (`N`+ 1) caractères.</span><span class="sxs-lookup"><span data-stu-id="736c5-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="736c5-168">Le +1 tient compte du fait que la chaîne non managée possède un terminateur Null, contrairement à `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="736c5-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="736c5-169">Par exemple, la [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) fonction API Windows (définie dans *winuser. h*) requiert que l’appelant passe une mémoire tampon de caractères de longueur fixe à laquelle la fonction écrit le texte de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="736c5-169">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="736c5-170">`LpString` pointe vers une mémoire tampon allouée par l'appelant de taille `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="736c5-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="736c5-171">L'appelant est censé allouer la mémoire tampon et définir l'argument `nMaxCount` sur la taille de la mémoire tampon allouée.</span><span class="sxs-lookup"><span data-stu-id="736c5-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="736c5-172">L’exemple suivant illustre la déclaration de fonction `GetWindowText` définie dans *winuser.h*.</span><span class="sxs-lookup"><span data-stu-id="736c5-172">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="736c5-173">Un `StringBuilder` peut être déréférencé et modifié par l'appelé à condition qu'il ne dépasse pas la capacité de `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="736c5-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="736c5-174">L'exemple de code suivant montre comment `StringBuilder` peut être initialisé à une longueur fixe.</span><span class="sxs-lookup"><span data-stu-id="736c5-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="736c5-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="736c5-175">See also</span></span>

- [<span data-ttu-id="736c5-176">comportement de marshaling par défaut</span><span class="sxs-lookup"><span data-stu-id="736c5-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="736c5-177">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="736c5-177">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="736c5-178">types blittable et non blittable</span><span class="sxs-lookup"><span data-stu-id="736c5-178">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="736c5-179">[Attributs directionnels](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="736c5-179">[Directional Attributes](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="736c5-180">copie et épinglage</span><span class="sxs-lookup"><span data-stu-id="736c5-180">Copying and Pinning</span></span>](copying-and-pinning.md)
