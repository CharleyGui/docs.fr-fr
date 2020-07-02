---
title: Passage de structures
description: Découvrez comment passer des structures et des classes à des fonctions non managées. En savoir plus sur l’attribut StructLayoutAttribute, que vous utilisez pour définir les types mis en forme.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform invoke, calling unmanaged functions
ms.assetid: 9b92ac73-32b7-4e1b-862e-6d8d950cf169
ms.openlocfilehash: eae28d6746cd89d98b659b9eb957f158e1319190
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620818"
---
# <a name="passing-structures"></a>Passage de structures
De nombreuses fonctions non managées s’attendent à ce que vous passiez, en tant que paramètre de la fonction, des membres de structures (types définis par l’utilisateur en Visual Basic) ou des membres de classes qui sont définis dans le code managé. Lors du passage de structures ou de classes à du code non managé à l’aide de l’appel de code non managé, vous devez fournir des informations supplémentaires afin de conserver la disposition et l’alignement d’origine. Cette rubrique présente l’attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, qui vous permet de définir des types mis en forme. Pour les classes et structures managées, vous pouvez sélectionner parmi plusieurs comportements de disposition prévisible fournis par l’énumération **LayoutKind**.  
  
 Les concepts présentés dans cette rubrique sont axés sur une différence importante entre les types structure et classe. Les structures sont des types valeur et les classes sont des types référence. Les classes fournissent toujours au moins un niveau d’indirection de mémoire (un pointeur vers une valeur). Cette différence est importante, car les fonctions non managées exigent souvent une indirection, comme indiqué par les signatures de la première colonne du tableau suivant. Les déclarations de structures et de classes managées dans les colonnes restantes montrent le degré auquel vous pouvez ajuster le niveau d’indirection dans votre déclaration. Les déclarations sont fournies pour Visual Basic et Visual C#.  
  
|Signature non managée|Déclaration managée : <br />aucune indirection<br />`Structure MyType`<br />`struct MyType;`|Déclaration managée : <br />un niveau d’indirection<br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> N’exige aucun niveau d’indirection.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> N’ajoute aucun niveau d’indirection.|Impossible, car il existe déjà un niveau d’indirection.|  
|`DoWork(MyType* x);`<br /><br /> Exige un niveau d’indirection.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Ajoute un niveau d’indirection.|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> N’ajoute aucun niveau d’indirection.|  
|`DoWork(MyType** x);`<br /><br /> Exige deux niveaux d’indirection.|Impossible, car **ByRef** **ByRef** ou `ref` `ref` ne peut pas être utilisé.|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> Ajoute un niveau d’indirection.|  
  
 Le tableau décrit les instructions suivantes pour les déclarations d’appel de code non managé :  
  
- Utilisez une structure passée par valeur quand la fonction non managée n’exige aucune indirection.  
  
- Utilisez une structure passée par référence ou une classe passée par valeur quand la fonction non managée exige un niveau d’indirection.  
  
- Utilisez une classe passée par référence quand la fonction non managée exige deux niveaux d’indirection.  
  
## <a name="declaring-and-passing-structures"></a>Déclaration et passage de structures  
 L’exemple suivant montre comment définir les structures `Point` et `Rect` dans le code managé, et comment passer les types en tant que paramètre à la fonction **PtInRect** dans le fichier User32.dll. **PtInRect** a la signature non managée suivante :  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Notez que vous devez passer la structure Rect par référence, étant donné que la fonction attend un pointeur vers un type RECT.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
    Public x As Integer  
    Public y As Integer  
End Structure  
  
Public Structure <StructLayout(LayoutKind.Explicit)> Rect  
    <FieldOffset(0)> Public left As Integer  
    <FieldOffset(4)> Public top As Integer  
    <FieldOffset(8)> Public right As Integer  
    <FieldOffset(12)> Public bottom As Integer  
End Structure  
  
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "user32.dll" (
        ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
    public int x;  
    public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
    [FieldOffset(0)] public int left;  
    [FieldOffset(4)] public int top;  
    [FieldOffset(8)] public int right;  
    [FieldOffset(12)] public int bottom;  
}
  
internal static class NativeMethods
{  
    [DllImport("User32.dll")]  
    internal static extern bool PtInRect(ref Rect r, Point p);  
}  
```  
  
## <a name="declaring-and-passing-classes"></a>Déclaration et passage de classes  
 Vous pouvez passer les membres d’une classe à une fonction DLL non managée, à condition que la classe ait une disposition de membre fixe. L’exemple suivant montre comment passer les membres de la classe `MySystemTime`, qui sont définis dans un ordre séquentiel, à **GetSystemTime** dans le fichier User32.dll. **GetSystemTime** a la signature non managée suivante :  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Contrairement aux types valeur, les classes ont toujours au moins un niveau d’indirection.  
  
```vb  
Imports System.Runtime.InteropServices  
  
<StructLayout(LayoutKind.Sequential)> Public Class MySystemTime  
    Public wYear As Short  
    Public wMonth As Short  
    Public wDayOfWeek As Short
    Public wDay As Short  
    Public wHour As Short  
    Public wMinute As Short  
    Public wSecond As Short  
    Public wMiliseconds As Short  
End Class  
  
Friend Class NativeMethods  
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        sysTime As MySystemTime)  
    Friend Declare Auto Function MessageBox Lib "User32.dll" (
        hWnd As IntPtr, lpText As String, lpCaption As String, uType As UInteger) As Integer  
End Class  
  
Public Class TestPlatformInvoke
    Public Shared Sub Main()  
        Dim sysTime As New MySystemTime()  
        NativeMethods.GetSystemTime(sysTime)  
  
        Dim dt As String  
        dt = "System time is:" & ControlChars.CrLf & _  
              "Year: " & sysTime.wYear & _  
              ControlChars.CrLf & "Month: " & sysTime.wMonth & _  
              ControlChars.CrLf & "DayOfWeek: " & sysTime.wDayOfWeek & _  
              ControlChars.CrLf & "Day: " & sysTime.wDay  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0)
    End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class MySystemTime {  
    public ushort wYear;
    public ushort wMonth;  
    public ushort wDayOfWeek;
    public ushort wDay;
    public ushort wHour;
    public ushort wMinute;
    public ushort wSecond;
    public ushort wMilliseconds;
}  
internal static class NativeMethods
{  
    [DllImport("Kernel32.dll")]  
    internal static extern void GetSystemTime(MySystemTime st);  
  
    [DllImport("user32.dll", CharSet = CharSet.Auto)]  
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);  
}  
  
public class TestPlatformInvoke  
{  
    public static void Main()  
    {  
        MySystemTime sysTime = new MySystemTime();  
        NativeMethods.GetSystemTime(sysTime);  
  
        string dt;  
        dt = "System time is: \n" +  
              "Year: " + sysTime.wYear + "\n" +  
              "Month: " + sysTime.wMonth + "\n" +  
              "DayOfWeek: " + sysTime.wDayOfWeek + "\n" +  
              "Day: " + sysTime.wDay;  
        NativeMethods.MessageBox(IntPtr.Zero, dt, "Platform Invoke Sample", 0);  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Appel à une fonction DLL](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
