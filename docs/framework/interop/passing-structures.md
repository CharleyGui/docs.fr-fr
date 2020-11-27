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
ms.openlocfilehash: ece5db8fdf803ce2f450ebeaaad66a379cfbf992
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268909"
---
# <a name="passing-structures"></a><span data-ttu-id="f2b69-104">Passage de structures</span><span class="sxs-lookup"><span data-stu-id="f2b69-104">Passing Structures</span></span>

<span data-ttu-id="f2b69-105">De nombreuses fonctions non managées s’attendent à ce que vous passiez, en tant que paramètre de la fonction, des membres de structures (types définis par l’utilisateur en Visual Basic) ou des membres de classes qui sont définis dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="f2b69-105">Many unmanaged functions expect you to pass, as a parameter to the function, members of structures (user-defined types in Visual Basic) or members of classes that are defined in managed code.</span></span> <span data-ttu-id="f2b69-106">Lors du passage de structures ou de classes à du code non managé à l’aide de l’appel de code non managé, vous devez fournir des informations supplémentaires afin de conserver la disposition et l’alignement d’origine.</span><span class="sxs-lookup"><span data-stu-id="f2b69-106">When passing structures or classes to unmanaged code using platform invoke, you must provide additional information to preserve the original layout and alignment.</span></span> <span data-ttu-id="f2b69-107">Cette rubrique présente l’attribut <xref:System.Runtime.InteropServices.StructLayoutAttribute>, qui vous permet de définir des types mis en forme.</span><span class="sxs-lookup"><span data-stu-id="f2b69-107">This topic introduces the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute, which you use to define formatted types.</span></span> <span data-ttu-id="f2b69-108">Pour les classes et structures managées, vous pouvez sélectionner parmi plusieurs comportements de disposition prévisible fournis par l’énumération **LayoutKind**.</span><span class="sxs-lookup"><span data-stu-id="f2b69-108">For managed structures and classes, you can select from several predictable layout behaviors supplied by the **LayoutKind** enumeration.</span></span>  
  
 <span data-ttu-id="f2b69-109">Les concepts présentés dans cette rubrique sont axés sur une différence importante entre les types structure et classe.</span><span class="sxs-lookup"><span data-stu-id="f2b69-109">Central to the concepts presented in this topic is an important difference between structure and class types.</span></span> <span data-ttu-id="f2b69-110">Les structures sont des types valeur et les classes sont des types référence. Les classes fournissent toujours au moins un niveau d’indirection de mémoire (un pointeur vers une valeur).</span><span class="sxs-lookup"><span data-stu-id="f2b69-110">Structures are value types and classes are reference types — classes always provide at least one level of memory indirection (a pointer to a value).</span></span> <span data-ttu-id="f2b69-111">Cette différence est importante, car les fonctions non managées exigent souvent une indirection, comme indiqué par les signatures de la première colonne du tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f2b69-111">This difference is important because unmanaged functions often demand indirection, as shown by the signatures in the first column of the following table.</span></span> <span data-ttu-id="f2b69-112">Les déclarations de structures et de classes managées dans les colonnes restantes montrent le degré auquel vous pouvez ajuster le niveau d’indirection dans votre déclaration. Les déclarations sont fournies pour Visual Basic et Visual C#.</span><span class="sxs-lookup"><span data-stu-id="f2b69-112">The managed structure and class declarations in the remaining columns show the degree to which you can adjust the level of indirection in your declaration.Declarations are provided for both Visual Basic and Visual C#.</span></span>  
  
|<span data-ttu-id="f2b69-113">Signature non managée</span><span class="sxs-lookup"><span data-stu-id="f2b69-113">Unmanaged signature</span></span>|<span data-ttu-id="f2b69-114">Déclaration managée :</span><span class="sxs-lookup"><span data-stu-id="f2b69-114">Managed declaration:</span></span> <br /><span data-ttu-id="f2b69-115">aucune indirection</span><span class="sxs-lookup"><span data-stu-id="f2b69-115">no indirection</span></span><br />`Structure MyType`<br />`struct MyType;`|<span data-ttu-id="f2b69-116">Déclaration managée :</span><span class="sxs-lookup"><span data-stu-id="f2b69-116">Managed declaration:</span></span> <br /><span data-ttu-id="f2b69-117">un niveau d’indirection</span><span class="sxs-lookup"><span data-stu-id="f2b69-117">one level of indirection</span></span><br />`Class MyType`<br />`class MyType;`|  
|-------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------------------------|  
|`DoWork(MyType x);`<br /><br /> <span data-ttu-id="f2b69-118">N’exige aucun niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-118">Demands zero levels of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="f2b69-119">N’ajoute aucun niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-119">Adds zero levels of indirection.</span></span>|<span data-ttu-id="f2b69-120">Impossible, car il existe déjà un niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-120">Not possible because there is already one level of indirection.</span></span>|  
|`DoWork(MyType* x);`<br /><br /> <span data-ttu-id="f2b69-121">Exige un niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-121">Demands one level of indirection.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="f2b69-122">Ajoute un niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-122">Adds one level of indirection.</span></span>|`DoWork(ByVal x As MyType)` <br /> `DoWork(MyType x)`<br /><br /> <span data-ttu-id="f2b69-123">N’ajoute aucun niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-123">Adds zero levels of indirection.</span></span>|  
|`DoWork(MyType** x);`<br /><br /> <span data-ttu-id="f2b69-124">Exige deux niveaux d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-124">Demands two levels of indirection.</span></span>|<span data-ttu-id="f2b69-125">Impossible, car **ByRef** **ByRef** ou `ref` `ref` ne peut pas être utilisé.</span><span class="sxs-lookup"><span data-stu-id="f2b69-125">Not possible because **ByRef** **ByRef** or `ref` `ref` cannot be used.</span></span>|`DoWork(ByRef x As MyType)` <br /> `DoWork(ref MyType x)`<br /><br /> <span data-ttu-id="f2b69-126">Ajoute un niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-126">Adds one level of indirection.</span></span>|  
  
 <span data-ttu-id="f2b69-127">Le tableau décrit les instructions suivantes pour les déclarations d’appel de code non managé :</span><span class="sxs-lookup"><span data-stu-id="f2b69-127">The table describes the following guidelines for platform invoke declarations:</span></span>  
  
- <span data-ttu-id="f2b69-128">Utilisez une structure passée par valeur quand la fonction non managée n’exige aucune indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-128">Use a structure passed by value when the unmanaged function demands no indirection.</span></span>  
  
- <span data-ttu-id="f2b69-129">Utilisez une structure passée par référence ou une classe passée par valeur quand la fonction non managée exige un niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-129">Use either a structure passed by reference or a class passed by value when the unmanaged function demands one level of indirection.</span></span>  
  
- <span data-ttu-id="f2b69-130">Utilisez une classe passée par référence quand la fonction non managée exige deux niveaux d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-130">Use a class passed by reference when the unmanaged function demands two levels of indirection.</span></span>  
  
## <a name="declaring-and-passing-structures"></a><span data-ttu-id="f2b69-131">Déclaration et passage de structures</span><span class="sxs-lookup"><span data-stu-id="f2b69-131">Declaring and Passing Structures</span></span>  

 <span data-ttu-id="f2b69-132">L’exemple suivant montre comment définir les structures `Point` et `Rect` dans le code managé, et comment passer les types en tant que paramètre à la fonction **PtInRect** dans le fichier User32.dll.</span><span class="sxs-lookup"><span data-stu-id="f2b69-132">The following example shows how to define the `Point` and `Rect` structures in managed code, and pass the types as parameter to the **PtInRect** function in the User32.dll file.</span></span> <span data-ttu-id="f2b69-133">**PtInRect** a la signature non managée suivante :</span><span class="sxs-lookup"><span data-stu-id="f2b69-133">**PtInRect** has the following unmanaged signature:</span></span>  
  
```cpp
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="f2b69-134">Notez que vous devez passer la structure Rect par référence, étant donné que la fonction attend un pointeur vers un type RECT.</span><span class="sxs-lookup"><span data-stu-id="f2b69-134">Notice that you must pass the Rect structure by reference, since the function expects a pointer to a RECT type.</span></span>  
  
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
  
## <a name="declaring-and-passing-classes"></a><span data-ttu-id="f2b69-135">Déclaration et passage de classes</span><span class="sxs-lookup"><span data-stu-id="f2b69-135">Declaring and Passing Classes</span></span>  

 <span data-ttu-id="f2b69-136">Vous pouvez passer les membres d’une classe à une fonction DLL non managée, à condition que la classe ait une disposition de membre fixe.</span><span class="sxs-lookup"><span data-stu-id="f2b69-136">You can pass members of a class to an unmanaged DLL function, as long as the class has a fixed member layout.</span></span> <span data-ttu-id="f2b69-137">L’exemple suivant montre comment passer les membres de la classe `MySystemTime`, qui sont définis dans un ordre séquentiel, à **GetSystemTime** dans le fichier User32.dll.</span><span class="sxs-lookup"><span data-stu-id="f2b69-137">The following example demonstrates how to pass members of the `MySystemTime` class, which are defined in sequential order, to the **GetSystemTime** in the User32.dll file.</span></span> <span data-ttu-id="f2b69-138">**GetSystemTime** a la signature non managée suivante :</span><span class="sxs-lookup"><span data-stu-id="f2b69-138">**GetSystemTime** has the following unmanaged signature:</span></span>  
  
```cpp
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="f2b69-139">Contrairement aux types valeur, les classes ont toujours au moins un niveau d’indirection.</span><span class="sxs-lookup"><span data-stu-id="f2b69-139">Unlike value types, classes always have at least one level of indirection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f2b69-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2b69-140">See also</span></span>

- [<span data-ttu-id="f2b69-141">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="f2b69-141">Calling a DLL Function</span></span>](calling-a-dll-function.md)
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- <xref:System.Runtime.InteropServices.FieldOffsetAttribute>
