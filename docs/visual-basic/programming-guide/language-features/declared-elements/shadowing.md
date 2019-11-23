---
title: Copie shadow
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 034b5c0ecf3be6e77048fb7318e931801575f07a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345325"
---
# <a name="shadowing-in-visual-basic"></a><span data-ttu-id="f0cac-102">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0cac-102">Shadowing in Visual Basic</span></span>
<span data-ttu-id="f0cac-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span><span class="sxs-lookup"><span data-stu-id="f0cac-103">When two programming elements share the same name, one of them can hide, or *shadow*, the other one.</span></span> <span data-ttu-id="f0cac-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span><span class="sxs-lookup"><span data-stu-id="f0cac-104">In such a situation, the shadowed element is not available for reference; instead, when your code uses the element name, the Visual Basic compiler resolves it to the shadowing element.</span></span>  
  
## <a name="purpose"></a><span data-ttu-id="f0cac-105">Fonction</span><span class="sxs-lookup"><span data-stu-id="f0cac-105">Purpose</span></span>  
 <span data-ttu-id="f0cac-106">The main purpose of shadowing is to protect the definition of your class members.</span><span class="sxs-lookup"><span data-stu-id="f0cac-106">The main purpose of shadowing is to protect the definition of your class members.</span></span> <span data-ttu-id="f0cac-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span><span class="sxs-lookup"><span data-stu-id="f0cac-107">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="f0cac-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span><span class="sxs-lookup"><span data-stu-id="f0cac-108">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
## <a name="types-of-shadowing"></a><span data-ttu-id="f0cac-109">Types of Shadowing</span><span class="sxs-lookup"><span data-stu-id="f0cac-109">Types of Shadowing</span></span>  
 <span data-ttu-id="f0cac-110">An element can shadow another element in two different ways.</span><span class="sxs-lookup"><span data-stu-id="f0cac-110">An element can shadow another element in two different ways.</span></span> <span data-ttu-id="f0cac-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span><span class="sxs-lookup"><span data-stu-id="f0cac-111">The shadowing element can be declared inside a subregion of the region containing the shadowed element, in which case the shadowing is accomplished *through scope*.</span></span> <span data-ttu-id="f0cac-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span><span class="sxs-lookup"><span data-stu-id="f0cac-112">Or a deriving class can redefine a member of a base class, in which case the shadowing is done *through inheritance*.</span></span>  
  
### <a name="shadowing-through-scope"></a><span data-ttu-id="f0cac-113">Shadowing Through Scope</span><span class="sxs-lookup"><span data-stu-id="f0cac-113">Shadowing Through Scope</span></span>  
 <span data-ttu-id="f0cac-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span><span class="sxs-lookup"><span data-stu-id="f0cac-114">It is possible for programming elements in the same module, class, or structure to have the same name but different scope.</span></span> <span data-ttu-id="f0cac-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span><span class="sxs-lookup"><span data-stu-id="f0cac-115">When two elements are declared in this manner and the code refers to the name they share, the element with the narrower scope shadows the other element (block scope is the narrowest).</span></span>  
  
 <span data-ttu-id="f0cac-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-116">For example, a module can define a `Public` variable named `temp`, and a procedure within the module can declare a local variable also named `temp`.</span></span> <span data-ttu-id="f0cac-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span><span class="sxs-lookup"><span data-stu-id="f0cac-117">References to `temp` from within the procedure access the local variable, while references to `temp` from outside the procedure access the `Public` variable.</span></span> <span data-ttu-id="f0cac-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-118">In this case, the procedure variable `temp` shadows the module variable `temp`.</span></span>  
  
 <span data-ttu-id="f0cac-119">The following illustration shows two variables, both named `temp`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-119">The following illustration shows two variables, both named `temp`.</span></span> <span data-ttu-id="f0cac-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-120">The local variable `temp` shadows the member variable `temp` when accessed from within its own procedure `p`.</span></span> <span data-ttu-id="f0cac-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span><span class="sxs-lookup"><span data-stu-id="f0cac-121">However, the `MyClass` keyword bypasses the shadowing and accesses the member variable.</span></span>  
  
 ![Graphic that shows shadowing through scope.](./media/shadowing/shadow-scope-diagram.gif)
  
 <span data-ttu-id="f0cac-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span><span class="sxs-lookup"><span data-stu-id="f0cac-123">For an example of shadowing through scope, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).</span></span>  
  
### <a name="shadowing-through-inheritance"></a><span data-ttu-id="f0cac-124">Shadowing Through Inheritance</span><span class="sxs-lookup"><span data-stu-id="f0cac-124">Shadowing Through Inheritance</span></span>  
 <span data-ttu-id="f0cac-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span><span class="sxs-lookup"><span data-stu-id="f0cac-125">If a derived class redefines a programming element inherited from a base class, the redefining element shadows the original element.</span></span> <span data-ttu-id="f0cac-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span><span class="sxs-lookup"><span data-stu-id="f0cac-126">You can shadow any type of declared element, or set of overloaded elements, with any other type.</span></span> <span data-ttu-id="f0cac-127">For example, an `Integer` variable can shadow a `Function` procedure.</span><span class="sxs-lookup"><span data-stu-id="f0cac-127">For example, an `Integer` variable can shadow a `Function` procedure.</span></span> <span data-ttu-id="f0cac-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span><span class="sxs-lookup"><span data-stu-id="f0cac-128">If you shadow a procedure with another procedure, you can use a different parameter list and a different return type.</span></span>  
  
 <span data-ttu-id="f0cac-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-129">The following illustration shows a base class `b` and a derived class `d` that inherits from `b`.</span></span> <span data-ttu-id="f0cac-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span><span class="sxs-lookup"><span data-stu-id="f0cac-130">The base class defines a procedure named `proc`, and the derived class shadows it with another procedure of the same name.</span></span> <span data-ttu-id="f0cac-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-131">The first `Call` statement accesses the shadowing `proc` in the derived class.</span></span> <span data-ttu-id="f0cac-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-132">However, the `MyBase` keyword bypasses the shadowing and accesses the shadowed procedure in the base class.</span></span>  
  
 ![Diagramme graphique d'une occultation par héritage](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 <span data-ttu-id="f0cac-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span><span class="sxs-lookup"><span data-stu-id="f0cac-134">For an example of shadowing through inheritance, see [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) and [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).</span></span>  
  
#### <a name="shadowing-and-access-level"></a><span data-ttu-id="f0cac-135">Shadowing and Access Level</span><span class="sxs-lookup"><span data-stu-id="f0cac-135">Shadowing and Access Level</span></span>  
 <span data-ttu-id="f0cac-136">The shadowing element is not always accessible from the code using the derived class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-136">The shadowing element is not always accessible from the code using the derived class.</span></span> <span data-ttu-id="f0cac-137">For example, it might be declared `Private`.</span><span class="sxs-lookup"><span data-stu-id="f0cac-137">For example, it might be declared `Private`.</span></span> <span data-ttu-id="f0cac-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span><span class="sxs-lookup"><span data-stu-id="f0cac-138">In such a case, shadowing is defeated and the compiler resolves any reference to the same element it would have if there had been no shadowing.</span></span> <span data-ttu-id="f0cac-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-139">This element is the accessible element the fewest derivational steps backward from the shadowing class.</span></span> <span data-ttu-id="f0cac-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span><span class="sxs-lookup"><span data-stu-id="f0cac-140">If the shadowed element is a procedure, the resolution is to the closest accessible version with the same name, parameter list, and return type.</span></span>  
  
 <span data-ttu-id="f0cac-141">The following example shows an inheritance hierarchy of three classes.</span><span class="sxs-lookup"><span data-stu-id="f0cac-141">The following example shows an inheritance hierarchy of three classes.</span></span> <span data-ttu-id="f0cac-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-142">Each class defines a `Sub` procedure `display`, and each derived class shadows the `display` procedure in its base class.</span></span>  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f0cac-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span><span class="sxs-lookup"><span data-stu-id="f0cac-143">In the preceding example, the derived class `secondClass` shadows `display` with a `Private` procedure.</span></span> <span data-ttu-id="f0cac-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span><span class="sxs-lookup"><span data-stu-id="f0cac-144">When module `callDisplay` calls `display` in `secondClass`, the calling code is outside `secondClass` and therefore cannot access the private `display` procedure.</span></span> <span data-ttu-id="f0cac-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span><span class="sxs-lookup"><span data-stu-id="f0cac-145">Shadowing is defeated, and the compiler resolves the reference to the base class `display` procedure.</span></span>  
  
 <span data-ttu-id="f0cac-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span><span class="sxs-lookup"><span data-stu-id="f0cac-146">However, the further derived class `thirdClass` declares `display` as `Public`, so the code in `callDisplay` can access it.</span></span>  
  
## <a name="shadowing-and-overriding"></a><span data-ttu-id="f0cac-147">Shadowing and Overriding</span><span class="sxs-lookup"><span data-stu-id="f0cac-147">Shadowing and Overriding</span></span>  
 <span data-ttu-id="f0cac-148">Do not confuse shadowing with overriding.</span><span class="sxs-lookup"><span data-stu-id="f0cac-148">Do not confuse shadowing with overriding.</span></span> <span data-ttu-id="f0cac-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span><span class="sxs-lookup"><span data-stu-id="f0cac-149">Both are used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="f0cac-150">But there are significant differences between the two.</span><span class="sxs-lookup"><span data-stu-id="f0cac-150">But there are significant differences between the two.</span></span> <span data-ttu-id="f0cac-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span><span class="sxs-lookup"><span data-stu-id="f0cac-151">For a comparison, see [Differences Between Shadowing and Overriding](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).</span></span>  
  
## <a name="shadowing-and-overloading"></a><span data-ttu-id="f0cac-152">Shadowing and Overloading</span><span class="sxs-lookup"><span data-stu-id="f0cac-152">Shadowing and Overloading</span></span>  
 <span data-ttu-id="f0cac-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span><span class="sxs-lookup"><span data-stu-id="f0cac-153">If you shadow the same base class element with more than one element in your derived class, the shadowing elements become overloaded versions of that element.</span></span> <span data-ttu-id="f0cac-154">Pour plus d'informations, consultez [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="f0cac-154">For more information, see [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="accessing-a-shadowed-element"></a><span data-ttu-id="f0cac-155">Accessing a Shadowed Element</span><span class="sxs-lookup"><span data-stu-id="f0cac-155">Accessing a Shadowed Element</span></span>  
 <span data-ttu-id="f0cac-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span><span class="sxs-lookup"><span data-stu-id="f0cac-156">When you access an element from a derived class, you normally do so through the current instance of that derived class, by qualifying the element name with the `Me` keyword.</span></span> <span data-ttu-id="f0cac-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span><span class="sxs-lookup"><span data-stu-id="f0cac-157">If your derived class shadows the element in the base class, you can access the base class element by qualifying it with the `MyBase` keyword.</span></span>  
  
 <span data-ttu-id="f0cac-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="f0cac-158">For an example of accessing a shadowed element, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>  
  
### <a name="declaration-of-the-object-variable"></a><span data-ttu-id="f0cac-159">Declaration of the Object Variable</span><span class="sxs-lookup"><span data-stu-id="f0cac-159">Declaration of the Object Variable</span></span>  
 <span data-ttu-id="f0cac-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span><span class="sxs-lookup"><span data-stu-id="f0cac-160">How you create the object variable can also affect whether the derived class accesses a shadowing element or the shadowed element.</span></span> <span data-ttu-id="f0cac-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-161">The following example creates two objects from a derived class, but one object is declared as the base class and the other as the derived class.</span></span>  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()   
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="f0cac-162">In the preceding example, the variable `basObj` is declared as the base class.</span><span class="sxs-lookup"><span data-stu-id="f0cac-162">In the preceding example, the variable `basObj` is declared as the base class.</span></span> <span data-ttu-id="f0cac-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span><span class="sxs-lookup"><span data-stu-id="f0cac-163">Assigning a `dervCls` object to it constitutes a widening conversion and is therefore valid.</span></span> <span data-ttu-id="f0cac-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span><span class="sxs-lookup"><span data-stu-id="f0cac-164">However, the base class cannot access the shadowing version of the variable `z` in the derived class, so the compiler resolves `basObj.z` to the original base class value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0cac-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0cac-165">See also</span></span>

- [<span data-ttu-id="f0cac-166">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="f0cac-166">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="f0cac-167">Scope in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f0cac-167">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [<span data-ttu-id="f0cac-168">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="f0cac-168">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="f0cac-169">Shadows</span><span class="sxs-lookup"><span data-stu-id="f0cac-169">Shadows</span></span>](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="f0cac-170">Overrides</span><span class="sxs-lookup"><span data-stu-id="f0cac-170">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f0cac-171">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="f0cac-171">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="f0cac-172">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="f0cac-172">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
