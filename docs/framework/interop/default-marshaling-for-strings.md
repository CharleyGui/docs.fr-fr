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
# <a name="default-marshaling-for-strings"></a>Marshaling par défaut pour les chaînes

Les classes <xref:System.String?displayProperty=nameWithType> et <xref:System.Text.StringBuilder?displayProperty=nameWithType> ont un comportement de marshaling semblable.

Les chaînes sont marshalées en tant que type `BSTR` de style COM ou comme une chaîne se terminant par un caractère Null (un tableau de caractères se terminant par un caractère Null). Les caractères de la chaîne peuvent être marshalés en tant que caractères Unicode (valeur par défaut sur les systèmes Windows) ou ANSI.

## <a name="strings-used-in-interfaces"></a>Chaînes utilisées dans les interfaces

Le tableau suivant montre les options de marshaling pour le type de données String quand il est marshalé comme un argument de méthode du code non managé. L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler des chaînes d'interfaces COM.

|Type d'énumération|Description du format non managé|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr` (valeur par défaut)|`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.|
|`UnmanagedType.LPStr`|Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.|
|`UnmanagedType.LPWStr`|Pointeur vers un tableau de caractères Unicode terminé par un caractère null.|

Ce tableau s’applique à <xref:System.String>. Pour <xref:System.Text.StringBuilder>, les seules options autorisées sont `UnmanagedType.LPStr` et `UnmanagedType.LPWStr`.

L'exemple suivant montre des chaînes déclarées dans l'interface `IStringWorker`.

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

L'exemple suivant montre l'interface correspondante décrite dans une bibliothèque de types.

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

## <a name="strings-used-in-platform-invoke"></a>Chaînes utilisées dans les appels de code non managé

L'appel de code non managé copie des arguments de chaîne, en convertissant du format .NET Framework (Unicode) au format non managé de la plateforme. Les chaînes sont immuables et ne sont pas copiées depuis la mémoire non managée vers la mémoire managée quand l'appel est retourné.

Le tableau suivant répertorie les options de marshaling pour les chaînes quand celles-ci sont marshalées comme un argument de méthode d'un appel de code non managé. L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les chaînes.

|Type d'énumération|Description du format non managé|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|`BSTR` de style COM avec une longueur prédéfinie et des caractères ANSI.|
|`UnmanagedType.BStr`|`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.|
|`UnmanagedType.LPStr` (valeur par défaut)|Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.|
|`UnmanagedType.LPTStr`|Pointeur vers un tableau de caractères dépendant de la plateforme se terminant par un caractère Null.|
|`UnmanagedType.LPUTF8Str`|Pointeur vers un tableau de caractères encodés UTF-8 terminé par un caractère null.|
|`UnmanagedType.LPWStr`|Pointeur vers un tableau de caractères Unicode terminé par un caractère null.|
|`UnmanagedType.TBStr`|`BSTR` de style COM de longueur fixe avec des caractères dépendant de la plateforme.|
|`VBByRefStr`|Valeur qui permet à Visual Basic .NET de changer une chaîne dans du code non managé et de répercuter les résultats dans du code managé. Cette valeur est prise en charge uniquement pour l'appel de code non managé. Il s’agit de la valeur par défaut dans Visual Basic pour les chaînes `ByVal`.|

Ce tableau s’applique à <xref:System.String>. Pour <xref:System.Text.StringBuilder>, les seules options autorisées sont `LPStr`, `LPTStr` et `LPWStr`.

La définition de type suivante montre une utilisation correcte de `MarshalAsAttribute` pour les appels de code non managé.

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

## <a name="strings-used-in-structures"></a>Chaînes utilisées dans les structures

Les chaînes sont des membres valides de structures. Toutefois, les mémoires tampons <xref:System.Text.StringBuilder> ne sont pas valides dans les structures. Le tableau suivant montre les options de marshaling pour le type de données <xref:System.String> quand le type est marshalé en tant que champ. L'attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute> fournit plusieurs valeurs d'énumération <xref:System.Runtime.InteropServices.UnmanagedType> pour marshaler les chaînes en tant que champ.

|Type d'énumération|Description du format non managé|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|`BSTR` de style COM avec une longueur prédéfinie et des caractères Unicode.|
|`UnmanagedType.LPStr` (valeur par défaut)|Pointeur vers un tableau de caractères ANSI terminé par un caractère Null.|
|`UnmanagedType.LPTStr`|Pointeur vers un tableau de caractères dépendant de la plateforme se terminant par un caractère Null.|
|`UnmanagedType.LPUTF8Str`|Pointeur vers un tableau de caractères encodés UTF-8 terminé par un caractère null.|
|`UnmanagedType.LPWStr`|Pointeur vers un tableau de caractères Unicode terminé par un caractère null.|
|`UnmanagedType.ByValTStr`|Tableau de caractères de longueur fixe. Le type du tableau est déterminé par le jeu de caractères de la structure contenante.|

Le type `ByValTStr` est utilisé pour les tableaux de caractères inline de longueur fixe qui sont situés dans une structure. D'autres types s'appliquent aux références de chaîne contenues au sein de structures qui contiennent des pointeurs vers des chaînes.

L’argument `CharSet` du <xref:System.Runtime.InteropServices.StructLayoutAttribute> qui est appliqué à la structure contenante détermine le format de caractères des chaînes des structures. Les exemples de structures suivants contiennent des références de chaîne et des chaînes inline, ainsi que des caractères ANSI, Unicode et dépendant de la plateforme. La représentation de ces structures dans une bibliothèque de types est illustrée dans l’exemple de code C++ suivant :

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

L’exemple suivant montre comment utiliser le <xref:System.Runtime.InteropServices.MarshalAsAttribute> pour définir une même structure dans des formats différents.

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

## <a name="fixed-length-string-buffers"></a>Mémoires tampons de chaînes de longueur fixe

Dans certains cas, une mémoire tampon de caractères de longueur fixe doit être passée à du code non managé pour pouvoir être manipulée. Le fait de passer une chaîne ne fonctionne pas dans ce cas, car l'appelé ne peut pas modifier le contenu de la mémoire tampon passée. Même si la chaîne est passée par référence, il est impossible d'initialiser la mémoire tampon à une taille donnée.

La solution consiste à passer une mémoire tampon <xref:System.Text.StringBuilder> comme argument plutôt que comme <xref:System.String>. Un `StringBuilder` peut être déréférencé et modifié par l'appelé à condition qu'il ne dépasse pas la capacité de `StringBuilder`. Il peut également être initialisé à une longueur fixe. Par exemple, si vous initialisez une mémoire tampon `StringBuilder` avec une capacité de `N`, le marshaleur fournira une mémoire tampon de (`N`+ 1) caractères. Le +1 tient compte du fait que la chaîne non managée possède un terminateur Null, contrairement à `StringBuilder`.

Par exemple, la [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) fonction API Windows (définie dans *winuser. h*) requiert que l’appelant passe une mémoire tampon de caractères de longueur fixe à laquelle la fonction écrit le texte de la fenêtre. `LpString` pointe vers une mémoire tampon allouée par l'appelant de taille `nMaxCount`. L'appelant est censé allouer la mémoire tampon et définir l'argument `nMaxCount` sur la taille de la mémoire tampon allouée. L’exemple suivant illustre la déclaration de fonction `GetWindowText` définie dans *winuser.h*.

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

Un `StringBuilder` peut être déréférencé et modifié par l'appelé à condition qu'il ne dépasse pas la capacité de `StringBuilder`. L'exemple de code suivant montre comment `StringBuilder` peut être initialisé à une longueur fixe.

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

## <a name="see-also"></a>Voir aussi

- [comportement de marshaling par défaut](default-marshaling-behavior.md)
- [Marshaling de chaînes](marshaling-strings.md)
- [types blittable et non blittable](blittable-and-non-blittable-types.md)
- [Attributs directionnels](/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [copie et épinglage](copying-and-pinning.md)
