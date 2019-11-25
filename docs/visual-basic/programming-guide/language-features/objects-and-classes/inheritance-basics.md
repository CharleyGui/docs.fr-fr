---
title: Éléments fondamentaux de l'héritage
ms.date: 07/20/2015
helpviewer_keywords:
- derived classes [Visual Basic], inheritance
- MyClass keyword [Visual Basic], using
- MyBase keyword [Visual Basic], using
- Inherits statement [Visual Basic], inheritance
- overriding, Overridable keyword
- MustInherit keyword [Visual Basic], using
- Overrides keyword [Visual Basic], using
- inheritance
- MustInherit classes [Visual Basic]
- MustOverride keyword [Visual Basic], using
- classes [Visual Basic], derived
- NotInheritable keyword [Visual Basic], using
- base classes [Visual Basic], extending properties and methods [Visual Basic]
- NotOverridable keyword [Visual Basic], using
- base classes [Visual Basic], inheritance
- abstract classes [Visual Basic], inheritance
- overriding, Overrides keyword
ms.assetid: dfc8deba-f5b3-4d1d-a937-7cb826446fc5
ms.openlocfilehash: 89fcf2a14d8938d536aa72628218242811baa1a2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350818"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="87c73-102">Éléments fondamentaux de l'héritage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87c73-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="87c73-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span><span class="sxs-lookup"><span data-stu-id="87c73-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="87c73-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="87c73-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span><span class="sxs-lookup"><span data-stu-id="87c73-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="87c73-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span><span class="sxs-lookup"><span data-stu-id="87c73-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="87c73-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span><span class="sxs-lookup"><span data-stu-id="87c73-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="87c73-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="87c73-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span><span class="sxs-lookup"><span data-stu-id="87c73-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="87c73-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="87c73-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span><span class="sxs-lookup"><span data-stu-id="87c73-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="87c73-112">Inheritance Modifiers</span><span class="sxs-lookup"><span data-stu-id="87c73-112">Inheritance Modifiers</span></span>

<span data-ttu-id="87c73-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span><span class="sxs-lookup"><span data-stu-id="87c73-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="87c73-114">`Inherits` statement — Specifies the base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="87c73-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="87c73-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span><span class="sxs-lookup"><span data-stu-id="87c73-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="87c73-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span><span class="sxs-lookup"><span data-stu-id="87c73-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="87c73-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span><span class="sxs-lookup"><span data-stu-id="87c73-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="87c73-119">Overriding Properties and Methods in Derived Classes</span><span class="sxs-lookup"><span data-stu-id="87c73-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="87c73-120">By default, a derived class inherits properties and methods from its base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="87c73-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span><span class="sxs-lookup"><span data-stu-id="87c73-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="87c73-122">That is, you can define a new implementation of the method in the derived class.</span><span class="sxs-lookup"><span data-stu-id="87c73-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="87c73-123">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="87c73-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="87c73-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span><span class="sxs-lookup"><span data-stu-id="87c73-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="87c73-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="87c73-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span><span class="sxs-lookup"><span data-stu-id="87c73-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="87c73-127">By default, `Public` methods are `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="87c73-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="87c73-128">`MustOverride` — Requires that a derived class override the property or method.</span><span class="sxs-lookup"><span data-stu-id="87c73-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="87c73-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span><span class="sxs-lookup"><span data-stu-id="87c73-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="87c73-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span><span class="sxs-lookup"><span data-stu-id="87c73-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="87c73-131">`MustOverride` methods must be declared in `MustInherit` classes.</span><span class="sxs-lookup"><span data-stu-id="87c73-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="87c73-132">Suppose you want to define classes to handle payroll.</span><span class="sxs-lookup"><span data-stu-id="87c73-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="87c73-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span><span class="sxs-lookup"><span data-stu-id="87c73-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="87c73-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span><span class="sxs-lookup"><span data-stu-id="87c73-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="87c73-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span><span class="sxs-lookup"><span data-stu-id="87c73-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="87c73-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="87c73-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="87c73-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span><span class="sxs-lookup"><span data-stu-id="87c73-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="87c73-138">The MyBase Keyword</span><span class="sxs-lookup"><span data-stu-id="87c73-138">The MyBase Keyword</span></span>

<span data-ttu-id="87c73-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span><span class="sxs-lookup"><span data-stu-id="87c73-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="87c73-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span><span class="sxs-lookup"><span data-stu-id="87c73-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="87c73-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span><span class="sxs-lookup"><span data-stu-id="87c73-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="87c73-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="87c73-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span><span class="sxs-lookup"><span data-stu-id="87c73-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="87c73-144">The following list describes restrictions on using `MyBase`:</span><span class="sxs-lookup"><span data-stu-id="87c73-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="87c73-145">`MyBase` refers to the immediate base class and its inherited members.</span><span class="sxs-lookup"><span data-stu-id="87c73-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="87c73-146">It cannot be used to access `Private` members in the class.</span><span class="sxs-lookup"><span data-stu-id="87c73-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="87c73-147">`MyBase` is a keyword, not a real object.</span><span class="sxs-lookup"><span data-stu-id="87c73-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="87c73-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span><span class="sxs-lookup"><span data-stu-id="87c73-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="87c73-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span><span class="sxs-lookup"><span data-stu-id="87c73-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="87c73-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span><span class="sxs-lookup"><span data-stu-id="87c73-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="87c73-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span><span class="sxs-lookup"><span data-stu-id="87c73-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="87c73-152">`MyBase` cannot be used to qualify itself.</span><span class="sxs-lookup"><span data-stu-id="87c73-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="87c73-153">Therefore, the following code is not valid:</span><span class="sxs-lookup"><span data-stu-id="87c73-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="87c73-154">`MyBase` cannot be used in modules.</span><span class="sxs-lookup"><span data-stu-id="87c73-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="87c73-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span><span class="sxs-lookup"><span data-stu-id="87c73-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="87c73-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="87c73-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="87c73-157">The MyClass Keyword</span><span class="sxs-lookup"><span data-stu-id="87c73-157">The MyClass Keyword</span></span>

<span data-ttu-id="87c73-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span><span class="sxs-lookup"><span data-stu-id="87c73-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="87c73-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="87c73-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="87c73-160">Therefore, the method or property is not affected by overriding in a derived class.</span><span class="sxs-lookup"><span data-stu-id="87c73-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="87c73-161">`MyClass` is a keyword, not a real object.</span><span class="sxs-lookup"><span data-stu-id="87c73-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="87c73-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span><span class="sxs-lookup"><span data-stu-id="87c73-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="87c73-163">`MyClass` refers to the containing class and its inherited members.</span><span class="sxs-lookup"><span data-stu-id="87c73-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="87c73-164">`MyClass` can be used as a qualifier for `Shared` members.</span><span class="sxs-lookup"><span data-stu-id="87c73-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="87c73-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span><span class="sxs-lookup"><span data-stu-id="87c73-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="87c73-166">`MyClass` cannot be used in standard modules.</span><span class="sxs-lookup"><span data-stu-id="87c73-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="87c73-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span><span class="sxs-lookup"><span data-stu-id="87c73-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="87c73-168">Such a reference has the same meaning as `MyBase.`*Method*.</span><span class="sxs-lookup"><span data-stu-id="87c73-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="87c73-169">The following example compares `Me` and `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="87c73-169">The following example compares `Me` and `MyClass`.</span></span>

```vb
Class baseClass
    Public Overridable Sub testMethod()
        MsgBox("Base class string")
    End Sub
    Public Sub useMe()
        ' The following call uses the calling class's method, even if
        ' that method is an override.
        Me.testMethod()
    End Sub
    Public Sub useMyClass()
        ' The following call uses this instance's method and not any
        ' override.
        MyClass.testMethod()
    End Sub
End Class
Class derivedClass : Inherits baseClass
    Public Overrides Sub testMethod()
        MsgBox("Derived class string")
    End Sub
End Class
Class testClasses
    Sub startHere()
        Dim testObj As derivedClass = New derivedClass()
        ' The following call displays "Derived class string".
        testObj.useMe()
        ' The following call displays "Base class string".
        testObj.useMyClass()
    End Sub
End Class
```

<span data-ttu-id="87c73-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="87c73-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="87c73-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87c73-171">See also</span></span>

- [<span data-ttu-id="87c73-172">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="87c73-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="87c73-173">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="87c73-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
