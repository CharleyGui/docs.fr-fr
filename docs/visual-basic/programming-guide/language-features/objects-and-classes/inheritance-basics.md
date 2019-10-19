---
title: Éléments fondamentaux de l'héritage (Visual Basic)
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
ms.openlocfilehash: 8a75b75ef9acb4c89f4c7d05f1410d4ca70e680b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582748"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="0ffe8-102">Éléments fondamentaux de l'héritage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ffe8-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="0ffe8-103">L’instruction `Inherits` est utilisée pour déclarer une nouvelle classe, appelée *classe dérivée*, basée sur une classe existante, appelée classe de *base*.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="0ffe8-104">Les classes dérivées héritent des propriétés, des méthodes, des événements, des champs et des constantes définies dans la classe de base, et peuvent étendre celles-ci.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="0ffe8-105">La section suivante décrit certaines des règles d’héritage et les modificateurs que vous pouvez utiliser pour modifier la façon dont les classes héritent ou sont héritées :</span><span class="sxs-lookup"><span data-stu-id="0ffe8-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="0ffe8-106">Par défaut, toutes les classes peuvent être héritées, sauf si elles sont marquées avec le mot clé `NotInheritable`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="0ffe8-107">Les classes peuvent hériter d’autres classes de votre projet ou de classes dans d’autres assemblys référencés par votre projet.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="0ffe8-108">Contrairement aux langages qui autorisent l’héritage multiple, Visual Basic n’autorise que l’héritage unique dans les classes ; autrement dit, les classes dérivées ne peuvent avoir qu’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="0ffe8-109">Même si l’héritage multiple n’est pas autorisé dans les classes, les classes peuvent implémenter plusieurs interfaces, ce qui peut effectivement atteindre les mêmes terminaisons.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="0ffe8-110">Pour empêcher l’exposition d’éléments restreints dans une classe de base, le type d’accès d’une classe dérivée doit être égal ou plus restrictif que sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="0ffe8-111">Par exemple, une classe `Public` ne peut pas hériter d’une classe `Friend` ou `Private`, et une classe `Friend` ne peut pas hériter d’une classe `Private`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="0ffe8-112">Modificateurs d’héritage</span><span class="sxs-lookup"><span data-stu-id="0ffe8-112">Inheritance Modifiers</span></span>

<span data-ttu-id="0ffe8-113">Visual Basic introduit les instructions et les modificateurs de niveau classe suivants pour prendre en charge l’héritage :</span><span class="sxs-lookup"><span data-stu-id="0ffe8-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="0ffe8-114">instruction `Inherits` : spécifie la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="0ffe8-115">modificateur de `NotInheritable` : empêche les programmeurs d’utiliser la classe comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="0ffe8-116">`MustInherit` modifier : spécifie que la classe est destinée à être utilisée comme classe de base uniquement.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="0ffe8-117">Les instances de `MustInherit` classes ne peuvent pas être créées directement ; ils peuvent uniquement être créés en tant qu’instances de classe de base d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="0ffe8-118">(D’autres langages de programmation C++ , C#tels que et, utilisent le terme *classe abstraite* pour décrire une telle classe.)</span><span class="sxs-lookup"><span data-stu-id="0ffe8-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="0ffe8-119">Substitution de propriétés et de méthodes dans les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="0ffe8-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="0ffe8-120">Par défaut, une classe dérivée hérite des propriétés et des méthodes de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="0ffe8-121">Si une propriété ou une méthode héritée doit se comporter différemment dans la classe dérivée, elle peut être *substituée*.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="0ffe8-122">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="0ffe8-123">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="0ffe8-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="0ffe8-124">`Overridable` : permet à une propriété ou à une méthode d’une classe d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="0ffe8-125">`Overrides` : substitue une propriété ou une méthode `Overridable` définie dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="0ffe8-126">`NotOverridable` : empêche une propriété ou une méthode d’être substituée dans une classe qui hérite.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="0ffe8-127">Par défaut, les méthodes de `Public` sont `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="0ffe8-128">`MustOverride` : exige qu’une classe dérivée substitue la propriété ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="0ffe8-129">Lorsque le mot clé `MustOverride` est utilisé, la définition de la méthode se compose uniquement de l’instruction `Sub`, `Function` ou `Property`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="0ffe8-130">Aucune autre instruction n’est autorisée et, en particulier, il n’y a pas d’instruction `End Sub` ou `End Function`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="0ffe8-131">`MustOverride` méthodes doivent être déclarées dans des classes `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="0ffe8-132">Supposons que vous souhaitiez définir des classes pour gérer les salaires.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="0ffe8-133">Vous pouvez définir une classe de `Payroll` générique qui contient une méthode `RunPayroll` qui calcule la paie d’une semaine classique.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="0ffe8-134">Vous pouvez ensuite utiliser `Payroll` comme classe de base pour une classe `BonusPayroll` plus spécialisée, qui pourrait être utilisée lors de la distribution des bonus des employés.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="0ffe8-135">La classe `BonusPayroll` peut hériter de la méthode `PayEmployee` définie dans la classe de base `Payroll` et la substituer.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="0ffe8-136">L’exemple suivant définit une classe de base, `Payroll,` et une classe dérivée, `BonusPayroll`, qui substitue une méthode héritée, `PayEmployee`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="0ffe8-137">Une procédure, `RunPayroll`, crée, puis passe un objet `Payroll` et un objet `BonusPayroll` à une fonction, `Pay`, qui exécute la méthode `PayEmployee` des deux objets.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="0ffe8-138">Le mot clé MyBase</span><span class="sxs-lookup"><span data-stu-id="0ffe8-138">The MyBase Keyword</span></span>

<span data-ttu-id="0ffe8-139">Le mot clé `MyBase` se comporte comme une variable objet qui fait référence à la classe de base de l’instance actuelle d’une classe.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="0ffe8-140">`MyBase` est fréquemment utilisé pour accéder aux membres de la classe de base qui sont substitués ou occultés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="0ffe8-141">En particulier, `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="0ffe8-142">Par exemple, supposons que vous conceviez une classe dérivée qui substitue une méthode héritée de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="0ffe8-143">La méthode substituée peut appeler la méthode dans la classe de base et modifier la valeur de retour comme indiqué dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="0ffe8-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="0ffe8-144">La liste suivante décrit les restrictions relatives à l’utilisation de `MyBase` :</span><span class="sxs-lookup"><span data-stu-id="0ffe8-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="0ffe8-145">`MyBase` fait référence à la classe de base immédiate et à ses membres hérités.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="0ffe8-146">Elle ne peut pas être utilisée pour accéder à `Private` membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="0ffe8-147">`MyBase` est un mot clé, et non un objet réel.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="0ffe8-148">`MyBase` ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans une comparaison `Is`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="0ffe8-149">La méthode qui `MyBase` qualifie n’a pas besoin d’être définie dans la classe de base immédiate ; elle peut être définie à la place dans une classe de base indirectement héritée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="0ffe8-150">Pour qu’une référence qualifiée par `MyBase` soit compilée correctement, une classe de base doit contenir une méthode qui correspond au nom et aux types des paramètres qui s’affichent dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="0ffe8-151">Vous ne pouvez pas utiliser `MyBase` pour appeler des méthodes de classe de base `MustOverride`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="0ffe8-152">`MyBase` ne peut pas être utilisé pour se qualifier lui-même.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="0ffe8-153">Par conséquent, le code suivant n’est pas valide :</span><span class="sxs-lookup"><span data-stu-id="0ffe8-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="0ffe8-154">`MyBase` ne peut pas être utilisé dans les modules.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="0ffe8-155">`MyBase` ne peut pas être utilisé pour accéder aux membres de la classe de base marqués comme `Friend` si la classe de base se trouve dans un assembly différent.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="0ffe8-156">Pour plus d’informations et pour obtenir un autre exemple, consultez [Comment : accéder à une variable masquée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="0ffe8-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="0ffe8-157">Mot clé MyClass</span><span class="sxs-lookup"><span data-stu-id="0ffe8-157">The MyClass Keyword</span></span>

<span data-ttu-id="0ffe8-158">Le mot clé `MyClass` se comporte comme une variable objet qui fait référence à l’instance actuelle d’une classe telle qu’elle a été implémentée à l’origine.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="0ffe8-159">`MyClass` ressemble à `Me`, mais chaque méthode et appel de propriété sur `MyClass` est traité comme si la méthode ou la propriété était [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="0ffe8-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="0ffe8-160">Par conséquent, la méthode ou la propriété n’est pas affectée par la substitution dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="0ffe8-161">`MyClass` est un mot clé, et non un objet réel.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="0ffe8-162">`MyClass` ne peut pas être assigné à une variable, passé à des procédures ou utilisé dans une comparaison `Is`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="0ffe8-163">`MyClass` fait référence à la classe conteneur et à ses membres hérités.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="0ffe8-164">`MyClass` peut être utilisé en tant que qualificateur pour les membres `Shared`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="0ffe8-165">`MyClass` ne peut pas être utilisé à l’intérieur d’une méthode `Shared`, mais peut être utilisé dans une méthode d’instance pour accéder à un membre partagé d’une classe.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="0ffe8-166">`MyClass` ne peut pas être utilisé dans les modules standard.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="0ffe8-167">`MyClass` peut être utilisé pour qualifier une méthode définie dans une classe de base et qui n’a aucune implémentation de la méthode fournie dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="0ffe8-168">Une telle référence a la même signification que `MyBase.`*méthode*.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="0ffe8-169">L’exemple suivant compare `Me` et `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="0ffe8-170">Même si `derivedClass` remplace `testMethod`, le mot clé `MyClass` dans `useMyClass` annule les effets de la substitution, et le compilateur résout l’appel à la version de la classe de base de `testMethod`.</span><span class="sxs-lookup"><span data-stu-id="0ffe8-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0ffe8-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ffe8-171">See also</span></span>

- [<span data-ttu-id="0ffe8-172">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="0ffe8-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="0ffe8-173">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="0ffe8-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
