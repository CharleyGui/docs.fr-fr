---
title: References to Declared Elements
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: a6477a9f0abaf8eb9176f4f6ab2a920af6c8f500
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345301"
---
# <a name="references-to-declared-elements-visual-basic"></a><span data-ttu-id="b9b56-102">Références aux éléments déclarés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9b56-102">References to Declared Elements (Visual Basic)</span></span>
<span data-ttu-id="b9b56-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-103">When your code refers to a declared element, the Visual Basic compiler matches the name in your reference to the appropriate declaration of that name.</span></span> <span data-ttu-id="b9b56-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-104">If more than one element is declared with the same name, you can control which of those elements is to be referenced by *qualifying* its name.</span></span>  
  
 <span data-ttu-id="b9b56-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span><span class="sxs-lookup"><span data-stu-id="b9b56-105">The compiler attempts to match a name reference to a name declaration with the *narrowest scope*.</span></span> <span data-ttu-id="b9b56-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span><span class="sxs-lookup"><span data-stu-id="b9b56-106">This means it starts with the code making the reference and works outward through successive levels of containing elements.</span></span>  
  
 <span data-ttu-id="b9b56-107">The following example shows references to two variables with the same name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-107">The following example shows references to two variables with the same name.</span></span> <span data-ttu-id="b9b56-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span><span class="sxs-lookup"><span data-stu-id="b9b56-108">The example declares two variables, each named `totalCount`, at different levels of scope in module `container`.</span></span> <span data-ttu-id="b9b56-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span><span class="sxs-lookup"><span data-stu-id="b9b56-109">When the procedure `showCount` displays `totalCount` without qualification, the Visual Basic compiler resolves the reference to the declaration with the narrowest scope, namely the local declaration inside `showCount`.</span></span> <span data-ttu-id="b9b56-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span><span class="sxs-lookup"><span data-stu-id="b9b56-110">When it qualifies `totalCount` with the containing module `container`, the compiler resolves the reference to the declaration with the broader scope.</span></span>  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a><span data-ttu-id="b9b56-111">Qualifying an Element Name</span><span class="sxs-lookup"><span data-stu-id="b9b56-111">Qualifying an Element Name</span></span>  
 <span data-ttu-id="b9b56-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span><span class="sxs-lookup"><span data-stu-id="b9b56-112">If you want to override this search process and specify a name declared in a broader scope, you must *qualify* the name with the containing element of the broader scope.</span></span> <span data-ttu-id="b9b56-113">In some cases, you might also have to qualify the containing element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-113">In some cases, you might also have to qualify the containing element.</span></span>  
  
 <span data-ttu-id="b9b56-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span><span class="sxs-lookup"><span data-stu-id="b9b56-114">Qualifying a name means preceding it in your source statement with information that identifies where the target element is defined.</span></span> <span data-ttu-id="b9b56-115">This information is called a *qualification string*.</span><span class="sxs-lookup"><span data-stu-id="b9b56-115">This information is called a *qualification string*.</span></span> <span data-ttu-id="b9b56-116">It can include one or more namespaces and a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="b9b56-116">It can include one or more namespaces and a module, class, or structure.</span></span>  
  
 <span data-ttu-id="b9b56-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-117">The qualification string should unambiguously specify the module, class, or structure containing the target element.</span></span> <span data-ttu-id="b9b56-118">The container might in turn be located in another containing element, usually a namespace.</span><span class="sxs-lookup"><span data-stu-id="b9b56-118">The container might in turn be located in another containing element, usually a namespace.</span></span> <span data-ttu-id="b9b56-119">You might need to include several containing elements in the qualification string.</span><span class="sxs-lookup"><span data-stu-id="b9b56-119">You might need to include several containing elements in the qualification string.</span></span>  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a><span data-ttu-id="b9b56-120">To access a declared element by qualifying its name</span><span class="sxs-lookup"><span data-stu-id="b9b56-120">To access a declared element by qualifying its name</span></span>  
  
1. <span data-ttu-id="b9b56-121">Determine the location in which the element has been defined.</span><span class="sxs-lookup"><span data-stu-id="b9b56-121">Determine the location in which the element has been defined.</span></span> <span data-ttu-id="b9b56-122">This might include a namespace, or even a hierarchy of namespaces.</span><span class="sxs-lookup"><span data-stu-id="b9b56-122">This might include a namespace, or even a hierarchy of namespaces.</span></span> <span data-ttu-id="b9b56-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span><span class="sxs-lookup"><span data-stu-id="b9b56-123">Within the lowest-level namespace, the element must be contained in a module, class, or structure.</span></span>  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. <span data-ttu-id="b9b56-124">Determine a qualification path based on the target element's location.</span><span class="sxs-lookup"><span data-stu-id="b9b56-124">Determine a qualification path based on the target element's location.</span></span> <span data-ttu-id="b9b56-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-125">Start with the highest-level namespace, proceed to the lowest-level namespace, and end with the module, class, or structure containing the target element.</span></span> <span data-ttu-id="b9b56-126">Each element in the path must contain the element that follows it.</span><span class="sxs-lookup"><span data-stu-id="b9b56-126">Each element in the path must contain the element that follows it.</span></span>  
  
     <span data-ttu-id="b9b56-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span><span class="sxs-lookup"><span data-stu-id="b9b56-127">`outerSpace` → `innerSpace` → `holdsTotals` → `totals`</span></span>  
  
3. <span data-ttu-id="b9b56-128">Prepare the qualification string for the target element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-128">Prepare the qualification string for the target element.</span></span> <span data-ttu-id="b9b56-129">Place a period (`.`) after every element in the path.</span><span class="sxs-lookup"><span data-stu-id="b9b56-129">Place a period (`.`) after every element in the path.</span></span> <span data-ttu-id="b9b56-130">Your application must have access to every element in your qualification string.</span><span class="sxs-lookup"><span data-stu-id="b9b56-130">Your application must have access to every element in your qualification string.</span></span>  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. <span data-ttu-id="b9b56-131">Write the expression or assignment statement referring to the target element in the normal way.</span><span class="sxs-lookup"><span data-stu-id="b9b56-131">Write the expression or assignment statement referring to the target element in the normal way.</span></span>  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. <span data-ttu-id="b9b56-132">Precede the target element name with the qualification string.</span><span class="sxs-lookup"><span data-stu-id="b9b56-132">Precede the target element name with the qualification string.</span></span> <span data-ttu-id="b9b56-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-133">The name should immediately follow the period (`.`) that follows the module, class, or structure that contains the element.</span></span>  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. <span data-ttu-id="b9b56-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span><span class="sxs-lookup"><span data-stu-id="b9b56-134">The compiler uses the qualification string to find a clear, unambiguous declaration to which it can match the target element reference.</span></span>  
  
 <span data-ttu-id="b9b56-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-135">You might also have to qualify a name reference if your application has access to more than one programming element that has the same name.</span></span> <span data-ttu-id="b9b56-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="b9b56-136">For example, the <xref:System.Windows.Forms> and <xref:System.Web.UI.WebControls> namespaces both contain a `Label` class (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> and <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>).</span></span> <span data-ttu-id="b9b56-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span><span class="sxs-lookup"><span data-stu-id="b9b56-137">If your application uses both, or if it defines its own `Label` class, you must distinguish the different `Label` objects.</span></span> <span data-ttu-id="b9b56-138">Include the namespace or import alias in the variable declaration.</span><span class="sxs-lookup"><span data-stu-id="b9b56-138">Include the namespace or import alias in the variable declaration.</span></span> <span data-ttu-id="b9b56-139">The following example uses the import alias.</span><span class="sxs-lookup"><span data-stu-id="b9b56-139">The following example uses the import alias.</span></span>  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a><span data-ttu-id="b9b56-140">Members of Other Containing Elements</span><span class="sxs-lookup"><span data-stu-id="b9b56-140">Members of Other Containing Elements</span></span>  
 <span data-ttu-id="b9b56-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span><span class="sxs-lookup"><span data-stu-id="b9b56-141">When you use a nonshared member of another class or structure, you must first qualify the member name with a variable or expression that points to an instance of the class or structure.</span></span> <span data-ttu-id="b9b56-142">In the following example, `demoClass` is an instance of a class named `class1`.</span><span class="sxs-lookup"><span data-stu-id="b9b56-142">In the following example, `demoClass` is an instance of a class named `class1`.</span></span>  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 <span data-ttu-id="b9b56-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b9b56-143">You cannot use the class name itself to qualify a member that is not [Shared](../../../../visual-basic/language-reference/modifiers/shared.md).</span></span> <span data-ttu-id="b9b56-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-144">You must first create an instance in an object variable (in this case `demoClass`) and then reference it by the variable name.</span></span>  
  
 <span data-ttu-id="b9b56-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span><span class="sxs-lookup"><span data-stu-id="b9b56-145">If a class or structure has a `Shared` member, you can qualify that member either with the class or structure name or with a variable or expression that points to an instance.</span></span>  
  
 <span data-ttu-id="b9b56-146">A module does not have any separate instances, and all its members are `Shared` by default.</span><span class="sxs-lookup"><span data-stu-id="b9b56-146">A module does not have any separate instances, and all its members are `Shared` by default.</span></span> <span data-ttu-id="b9b56-147">Therefore, you qualify a module member with the module name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-147">Therefore, you qualify a module member with the module name.</span></span>  
  
 <span data-ttu-id="b9b56-148">The following example shows qualified references to module member procedures.</span><span class="sxs-lookup"><span data-stu-id="b9b56-148">The following example shows qualified references to module member procedures.</span></span> <span data-ttu-id="b9b56-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span><span class="sxs-lookup"><span data-stu-id="b9b56-149">The example declares two `Sub` procedures, both named `perform`, in different modules in a project.</span></span> <span data-ttu-id="b9b56-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span><span class="sxs-lookup"><span data-stu-id="b9b56-150">Each one can be specified without qualification within its own module but must be qualified if referenced from anywhere else.</span></span> <span data-ttu-id="b9b56-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span><span class="sxs-lookup"><span data-stu-id="b9b56-151">Because the final reference in `module3` does not qualify `perform`, the compiler cannot resolve that reference.</span></span>  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a><span data-ttu-id="b9b56-152">References to Projects</span><span class="sxs-lookup"><span data-stu-id="b9b56-152">References to Projects</span></span>  
 <span data-ttu-id="b9b56-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span><span class="sxs-lookup"><span data-stu-id="b9b56-153">To use [Public](../../../../visual-basic/language-reference/modifiers/public.md) elements defined in another project, you must first set a *reference* to that project's assembly or type library.</span></span> <span data-ttu-id="b9b56-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span><span class="sxs-lookup"><span data-stu-id="b9b56-154">To set a reference, click **Add Reference** on the **Project** menu, or use the [-reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) command-line compiler option.</span></span>  
  
 <span data-ttu-id="b9b56-155">For example, you can use the XML object model of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9b56-155">For example, you can use the XML object model of the .NET Framework.</span></span> <span data-ttu-id="b9b56-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="b9b56-156">If you set a reference to the <xref:System.Xml> namespace, you can declare and use any of its classes, such as <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="b9b56-157">The following example uses <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="b9b56-157">The following example uses <xref:System.Xml.XmlDocument>.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a><span data-ttu-id="b9b56-158">Importing Containing Elements</span><span class="sxs-lookup"><span data-stu-id="b9b56-158">Importing Containing Elements</span></span>  
 <span data-ttu-id="b9b56-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span><span class="sxs-lookup"><span data-stu-id="b9b56-159">You can use the [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to *import* the namespaces that contain the modules or classes that you want to use.</span></span> <span data-ttu-id="b9b56-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span><span class="sxs-lookup"><span data-stu-id="b9b56-160">This enables you to refer to the elements defined in an imported namespace without fully qualifying their names.</span></span> <span data-ttu-id="b9b56-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span><span class="sxs-lookup"><span data-stu-id="b9b56-161">The following example rewrites the previous example to import the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 <span data-ttu-id="b9b56-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span><span class="sxs-lookup"><span data-stu-id="b9b56-162">In addition, the `Imports` statement can define an *import alias* for each imported namespace.</span></span> <span data-ttu-id="b9b56-163">This can make the source code shorter and easier to read.</span><span class="sxs-lookup"><span data-stu-id="b9b56-163">This can make the source code shorter and easier to read.</span></span> <span data-ttu-id="b9b56-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span><span class="sxs-lookup"><span data-stu-id="b9b56-164">The following example rewrites the previous example to use `xD` as an alias for the <xref:System.Xml> namespace.</span></span>  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 <span data-ttu-id="b9b56-165">The `Imports` statement does not make elements from other projects available to your application.</span><span class="sxs-lookup"><span data-stu-id="b9b56-165">The `Imports` statement does not make elements from other projects available to your application.</span></span> <span data-ttu-id="b9b56-166">That is, it does not take the place of setting a reference.</span><span class="sxs-lookup"><span data-stu-id="b9b56-166">That is, it does not take the place of setting a reference.</span></span> <span data-ttu-id="b9b56-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span><span class="sxs-lookup"><span data-stu-id="b9b56-167">Importing a namespace just removes the requirement to qualify the names defined in that namespace.</span></span>  
  
 <span data-ttu-id="b9b56-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span><span class="sxs-lookup"><span data-stu-id="b9b56-168">You can also use the `Imports` statement to import modules, classes, structures, and enumerations.</span></span> <span data-ttu-id="b9b56-169">You can then use the members of such imported elements without qualification.</span><span class="sxs-lookup"><span data-stu-id="b9b56-169">You can then use the members of such imported elements without qualification.</span></span> <span data-ttu-id="b9b56-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span><span class="sxs-lookup"><span data-stu-id="b9b56-170">However, you must always qualify nonshared members of classes and structures with a variable or expression that evaluates to an instance of the class or structure.</span></span>  
  
## <a name="naming-guidelines"></a><span data-ttu-id="b9b56-171">Indications concernant l'attribution d'un nom</span><span class="sxs-lookup"><span data-stu-id="b9b56-171">Naming Guidelines</span></span>  
 <span data-ttu-id="b9b56-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span><span class="sxs-lookup"><span data-stu-id="b9b56-172">When you define two or more programming elements that have the same name, a *name ambiguity* can result when the compiler attempts to resolve a reference to that name.</span></span> <span data-ttu-id="b9b56-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span><span class="sxs-lookup"><span data-stu-id="b9b56-173">If more than one definition is in scope, or if no definition is in scope, the reference is irresolvable.</span></span> <span data-ttu-id="b9b56-174">For an example, see "Qualified Reference Example" on this Help page.</span><span class="sxs-lookup"><span data-stu-id="b9b56-174">For an example, see "Qualified Reference Example" on this Help page.</span></span>  
  
 <span data-ttu-id="b9b56-175">You can avoid name ambiguity by giving all your elements unique names.</span><span class="sxs-lookup"><span data-stu-id="b9b56-175">You can avoid name ambiguity by giving all your elements unique names.</span></span> <span data-ttu-id="b9b56-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span><span class="sxs-lookup"><span data-stu-id="b9b56-176">Then you can make reference to any element without having to qualify its name with a namespace, module, or class.</span></span> <span data-ttu-id="b9b56-177">You also reduce the chances of accidentally referring to the wrong element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-177">You also reduce the chances of accidentally referring to the wrong element.</span></span>  
  
## <a name="shadowing"></a><span data-ttu-id="b9b56-178">Copie shadow</span><span class="sxs-lookup"><span data-stu-id="b9b56-178">Shadowing</span></span>  
 <span data-ttu-id="b9b56-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span><span class="sxs-lookup"><span data-stu-id="b9b56-179">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="b9b56-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span><span class="sxs-lookup"><span data-stu-id="b9b56-180">A shadowed element is not available for reference; instead, when your code uses the shadowed element name, the Visual Basic compiler resolves it to the shadowing element.</span></span> <span data-ttu-id="b9b56-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="b9b56-181">For a more detailed explanation with examples, see [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b56-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9b56-182">See also</span></span>

- [<span data-ttu-id="b9b56-183">Noms d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="b9b56-183">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="b9b56-184">Caractéristiques d’éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="b9b56-184">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="b9b56-185">Gestion des propriétés des projets et des solutions</span><span class="sxs-lookup"><span data-stu-id="b9b56-185">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="b9b56-186">Variables</span><span class="sxs-lookup"><span data-stu-id="b9b56-186">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [<span data-ttu-id="b9b56-187">Imports (instruction) (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="b9b56-187">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b9b56-188">New (opérateur)</span><span class="sxs-lookup"><span data-stu-id="b9b56-188">New Operator</span></span>](../../../../visual-basic/language-reference/operators/new-operator.md)
- [<span data-ttu-id="b9b56-189">Public</span><span class="sxs-lookup"><span data-stu-id="b9b56-189">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)
