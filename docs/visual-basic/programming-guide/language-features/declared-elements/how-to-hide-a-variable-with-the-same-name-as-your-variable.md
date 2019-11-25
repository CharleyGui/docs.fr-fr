---
title: 'Comment : masquer une variable portant le même nom que votre variable'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: 0915adbbabb778b1bdd3b6b30e56725a7e74867c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345370"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a><span data-ttu-id="ad2db-102">Comment : masquer une variable portant le même nom que votre variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad2db-102">How to: Hide a Variable with the Same Name as Your Variable (Visual Basic)</span></span>

<span data-ttu-id="ad2db-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span><span class="sxs-lookup"><span data-stu-id="ad2db-103">You can hide a variable by *shadowing* it, that is, by redefining it with a variable of the same name.</span></span> <span data-ttu-id="ad2db-104">You can shadow the variable you want to hide in two ways:</span><span class="sxs-lookup"><span data-stu-id="ad2db-104">You can shadow the variable you want to hide in two ways:</span></span>

- <span data-ttu-id="ad2db-105">**Shadowing Through Scope.**</span><span class="sxs-lookup"><span data-stu-id="ad2db-105">**Shadowing Through Scope.**</span></span> <span data-ttu-id="ad2db-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span><span class="sxs-lookup"><span data-stu-id="ad2db-106">You can shadow it through scope by redeclaring it inside a subregion of the region containing the variable you want to hide.</span></span>

- <span data-ttu-id="ad2db-107">**Shadowing Through Inheritance.**</span><span class="sxs-lookup"><span data-stu-id="ad2db-107">**Shadowing Through Inheritance.**</span></span> <span data-ttu-id="ad2db-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span><span class="sxs-lookup"><span data-stu-id="ad2db-108">If the variable you want to hide is defined at class level, you can shadow it through inheritance by redeclaring it with the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in a derived class.</span></span>

## <a name="two-ways-to-hide-a-variable"></a><span data-ttu-id="ad2db-109">Two Ways to Hide a Variable</span><span class="sxs-lookup"><span data-stu-id="ad2db-109">Two Ways to Hide a Variable</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a><span data-ttu-id="ad2db-110">To hide a variable by shadowing it through scope</span><span class="sxs-lookup"><span data-stu-id="ad2db-110">To hide a variable by shadowing it through scope</span></span>

1. <span data-ttu-id="ad2db-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-111">Determine the region defining the variable you want to hide, and determine a subregion in which to redefine it with your variable.</span></span>

    |<span data-ttu-id="ad2db-112">Variable's region</span><span class="sxs-lookup"><span data-stu-id="ad2db-112">Variable's region</span></span>|<span data-ttu-id="ad2db-113">Allowable subregion for redefining it</span><span class="sxs-lookup"><span data-stu-id="ad2db-113">Allowable subregion for redefining it</span></span>|
    |-----------------------|-------------------------------------------|
    |<span data-ttu-id="ad2db-114">Module</span><span class="sxs-lookup"><span data-stu-id="ad2db-114">Module</span></span>|<span data-ttu-id="ad2db-115">A class within the module</span><span class="sxs-lookup"><span data-stu-id="ad2db-115">A class within the module</span></span>|
    |<span data-ttu-id="ad2db-116">Class</span><span class="sxs-lookup"><span data-stu-id="ad2db-116">Class</span></span>|<span data-ttu-id="ad2db-117">A subclass within the class</span><span class="sxs-lookup"><span data-stu-id="ad2db-117">A subclass within the class</span></span><br /><br /> <span data-ttu-id="ad2db-118">A procedure within the class</span><span class="sxs-lookup"><span data-stu-id="ad2db-118">A procedure within the class</span></span>|

    <span data-ttu-id="ad2db-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span><span class="sxs-lookup"><span data-stu-id="ad2db-119">You cannot redefine a procedure variable in a block within that procedure, for example in an `If`...`End If` construction or a `For` loop.</span></span>

2. <span data-ttu-id="ad2db-120">Create the subregion if it does not already exist.</span><span class="sxs-lookup"><span data-stu-id="ad2db-120">Create the subregion if it does not already exist.</span></span>

3. <span data-ttu-id="ad2db-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-121">Within the subregion, write a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) declaring the shadowing variable.</span></span>

    <span data-ttu-id="ad2db-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-122">When code inside the subregion refers to the variable name, the compiler resolves the reference to the shadowing variable.</span></span>

    <span data-ttu-id="ad2db-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span><span class="sxs-lookup"><span data-stu-id="ad2db-123">The following example illustrates shadowing through scope, as well as a reference that bypasses the shadowing.</span></span>

    ```vb
    Module shadowByScope
        ' The following statement declares num as a module-level variable.
        Public num As Integer
        Sub show()
            ' The following statement declares num as a local variable.
            Dim num As Integer
            ' The following statement sets the value of the local variable.
            num = 2
            ' The following statement displays the module-level variable.
            MsgBox(CStr(shadowByScope.num))
        End Sub
        Sub useModuleLevelNum()
            ' The following statement sets the value of the module-level variable.
            num = 1
            show()
        End Sub
    End Module
    ```

    <span data-ttu-id="ad2db-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span><span class="sxs-lookup"><span data-stu-id="ad2db-124">The preceding example declares the variable `num` both at module level and at procedure level (in the procedure `show`).</span></span> <span data-ttu-id="ad2db-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span><span class="sxs-lookup"><span data-stu-id="ad2db-125">The local variable `num` shadows the module-level variable `num` within `show`, so the local variable is set to 2.</span></span> <span data-ttu-id="ad2db-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span><span class="sxs-lookup"><span data-stu-id="ad2db-126">However, there is no local variable to shadow `num` in the `useModuleLevelNum` procedure.</span></span> <span data-ttu-id="ad2db-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span><span class="sxs-lookup"><span data-stu-id="ad2db-127">Therefore, `useModuleLevelNum` sets the value of the module-level variable to 1.</span></span>

    <span data-ttu-id="ad2db-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span><span class="sxs-lookup"><span data-stu-id="ad2db-128">The `MsgBox` call inside `show` bypasses the shadowing mechanism by qualifying `num` with the module name.</span></span> <span data-ttu-id="ad2db-129">Therefore, it displays the module-level variable instead of the local variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-129">Therefore, it displays the module-level variable instead of the local variable.</span></span>

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a><span data-ttu-id="ad2db-130">To hide a variable by shadowing it through inheritance</span><span class="sxs-lookup"><span data-stu-id="ad2db-130">To hide a variable by shadowing it through inheritance</span></span>

1. <span data-ttu-id="ad2db-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span><span class="sxs-lookup"><span data-stu-id="ad2db-131">Be sure the variable you want to hide is declared in a class, and at class level (outside any procedure).</span></span> <span data-ttu-id="ad2db-132">Otherwise you cannot shadow it through inheritance.</span><span class="sxs-lookup"><span data-stu-id="ad2db-132">Otherwise you cannot shadow it through inheritance.</span></span>

2. <span data-ttu-id="ad2db-133">Define a class derived from the variable's class if one does not already exist.</span><span class="sxs-lookup"><span data-stu-id="ad2db-133">Define a class derived from the variable's class if one does not already exist.</span></span>

3. <span data-ttu-id="ad2db-134">Inside the derived class, write a `Dim` statement declaring your variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-134">Inside the derived class, write a `Dim` statement declaring your variable.</span></span> <span data-ttu-id="ad2db-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span><span class="sxs-lookup"><span data-stu-id="ad2db-135">Include the [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) keyword in the declaration.</span></span>

    <span data-ttu-id="ad2db-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-136">When code in the derived class refers to the variable name, the compiler resolves the reference to your variable.</span></span>

    <span data-ttu-id="ad2db-137">The following example illustrates shadowing through inheritance.</span><span class="sxs-lookup"><span data-stu-id="ad2db-137">The following example illustrates shadowing through inheritance.</span></span> <span data-ttu-id="ad2db-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span><span class="sxs-lookup"><span data-stu-id="ad2db-138">It makes two references, one that accesses the shadowing variable and one that bypasses the shadowing.</span></span>

    ```vb
    Public Class shadowBaseClass
        Public shadowString As String = "This is the base class string."
    End Class
    Public Class shadowDerivedClass
        Inherits shadowBaseClass
        Public Shadows shadowString As String = "This is the derived class string."
        Public Sub showStrings()
            Dim s As String = "Unqualified shadowString: " & shadowString &
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString
            MsgBox(s)
        End Sub
    End Class
    ```

    <span data-ttu-id="ad2db-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span><span class="sxs-lookup"><span data-stu-id="ad2db-139">The preceding example declares the variable `shadowString` in the base class and shadows it in the derived class.</span></span> <span data-ttu-id="ad2db-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span><span class="sxs-lookup"><span data-stu-id="ad2db-140">The procedure `showStrings` in the derived class displays the shadowing version of the string when the name `shadowString` is not qualified.</span></span> <span data-ttu-id="ad2db-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span><span class="sxs-lookup"><span data-stu-id="ad2db-141">It then displays the shadowed version when `shadowString` is qualified with the `MyBase` keyword.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="ad2db-142">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="ad2db-142">Robust Programming</span></span>

<span data-ttu-id="ad2db-143">Shadowing introduces more than one version of a variable with the same name.</span><span class="sxs-lookup"><span data-stu-id="ad2db-143">Shadowing introduces more than one version of a variable with the same name.</span></span> <span data-ttu-id="ad2db-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span><span class="sxs-lookup"><span data-stu-id="ad2db-144">When a code statement refers to the variable name, the version to which the compiler resolves the reference depends on factors such as the location of the code statement and the presence of a qualifying string.</span></span> <span data-ttu-id="ad2db-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-145">This can increase the risk of referring to an unintended version of a shadowed variable.</span></span> <span data-ttu-id="ad2db-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span><span class="sxs-lookup"><span data-stu-id="ad2db-146">You can lower that risk by fully qualifying all references to a shadowed variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="ad2db-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad2db-147">See also</span></span>

- [<span data-ttu-id="ad2db-148">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="ad2db-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="ad2db-149">Shadowing in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad2db-149">Shadowing in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [<span data-ttu-id="ad2db-150">Différences entre l'occultation et la substitution</span><span class="sxs-lookup"><span data-stu-id="ad2db-150">Differences Between Shadowing and Overriding</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [<span data-ttu-id="ad2db-151">Guide pratique : masquer une variable héritée</span><span class="sxs-lookup"><span data-stu-id="ad2db-151">How to: Hide an Inherited Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [<span data-ttu-id="ad2db-152">Guide pratique : accéder à une variable masquée par une classe dérivée</span><span class="sxs-lookup"><span data-stu-id="ad2db-152">How to: Access a Variable Hidden by a Derived Class</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [<span data-ttu-id="ad2db-153">Overrides</span><span class="sxs-lookup"><span data-stu-id="ad2db-153">Overrides</span></span>](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="ad2db-154">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="ad2db-154">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="ad2db-155">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="ad2db-155">Inheritance Basics</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
