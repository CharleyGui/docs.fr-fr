---
title: Éléments fondamentaux de l’héritage
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400882"
---
# <a name="inheritance-basics-visual-basic"></a><span data-ttu-id="9c619-102">Éléments fondamentaux de l'héritage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c619-102">Inheritance Basics (Visual Basic)</span></span>

<span data-ttu-id="9c619-103">La `Inherits` déclaration est utilisée pour déclarer une nouvelle classe, appelée *classe dérivée,* basée sur une classe existante, connue sous le nom de *classe de base*.</span><span class="sxs-lookup"><span data-stu-id="9c619-103">The `Inherits` statement is used to declare a new class, called a *derived class*, based on an existing class, known as a *base class*.</span></span> <span data-ttu-id="9c619-104">Les classes dérivées héritent et peuvent s’étendre, les propriétés, les méthodes, les événements, les champs et les constantes définis dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-104">Derived classes inherit, and can extend, the properties, methods, events, fields, and constants defined in the base class.</span></span> <span data-ttu-id="9c619-105">La section suivante décrit certaines des règles d’héritage, et les modificateurs que vous pouvez utiliser pour changer la façon dont les classes héritent ou sont héritées :</span><span class="sxs-lookup"><span data-stu-id="9c619-105">The following section describes some of the rules for inheritance, and the modifiers you can use to change the way classes inherit or are inherited:</span></span>

- <span data-ttu-id="9c619-106">Par défaut, toutes les classes sont `NotInheritable` héréditaires à moins d’être marquées par le mot clé.</span><span class="sxs-lookup"><span data-stu-id="9c619-106">By default, all classes are inheritable unless marked with the `NotInheritable` keyword.</span></span> <span data-ttu-id="9c619-107">Les classes peuvent hériter d’autres classes de votre projet ou de cours dans d’autres assemblées que votre projet fait référence.</span><span class="sxs-lookup"><span data-stu-id="9c619-107">Classes can inherit from other classes in your project or from classes in other assemblies that your project references.</span></span>

- <span data-ttu-id="9c619-108">Contrairement aux langues qui permettent un héritage multiple, Visual Basic n’autorise qu’un seul héritage dans les classes; c’est-à-dire que les classes dérivées ne peuvent avoir qu’une seule classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-108">Unlike languages that allow multiple inheritance, Visual Basic allows only single inheritance in classes; that is, derived classes can have only one base class.</span></span> <span data-ttu-id="9c619-109">Bien que l’héritage multiple ne soit pas autorisé dans les classes, les classes peuvent implémenter plusieurs interfaces, qui peuvent accomplir efficacement les mêmes extrémités.</span><span class="sxs-lookup"><span data-stu-id="9c619-109">Although multiple inheritance is not allowed in classes, classes can implement multiple interfaces, which can effectively accomplish the same ends.</span></span>

- <span data-ttu-id="9c619-110">Pour éviter d’exposer des articles restreints dans une classe de base, le type d’accès d’une classe dérivée doit être égal ou plus restrictif que sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-110">To prevent exposing restricted items in a base class, the access type of a derived class must be equal to or more restrictive than its base class.</span></span> <span data-ttu-id="9c619-111">Par exemple, `Public` une classe `Friend` ne `Private` peut pas `Friend` hériter `Private` d’une classe ou d’une classe, et une classe ne peut pas hériter d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9c619-111">For example, a `Public` class cannot inherit a `Friend` or a `Private` class, and a `Friend` class cannot inherit a `Private` class.</span></span>

## <a name="inheritance-modifiers"></a><span data-ttu-id="9c619-112">Modifications d’héritage</span><span class="sxs-lookup"><span data-stu-id="9c619-112">Inheritance Modifiers</span></span>

<span data-ttu-id="9c619-113">Visual Basic présente les énoncés et les modificateurs de niveau de classe suivants pour soutenir l’héritage :</span><span class="sxs-lookup"><span data-stu-id="9c619-113">Visual Basic introduces the following class-level statements and modifiers to support inheritance:</span></span>

- <span data-ttu-id="9c619-114">`Inherits`déclaration — Précise la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-114">`Inherits` statement — Specifies the base class.</span></span>

- <span data-ttu-id="9c619-115">`NotInheritable`modificateur — Empêche les programmeurs d’utiliser la classe comme classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-115">`NotInheritable` modifier — Prevents programmers from using the class as a base class.</span></span>

- <span data-ttu-id="9c619-116">`MustInherit`modificateur — Précise que la classe est destinée à être utilisée comme classe de base seulement.</span><span class="sxs-lookup"><span data-stu-id="9c619-116">`MustInherit` modifier — Specifies that the class is intended for use as a base class only.</span></span> <span data-ttu-id="9c619-117">Les `MustInherit` instances des classes ne peuvent pas être créées directement; ils ne peuvent être créés que comme instances de classe de base d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c619-117">Instances of `MustInherit` classes cannot be created directly; they can only be created as base class instances of a derived class.</span></span> <span data-ttu-id="9c619-118">(D’autres langages de programmation, tels que le C et le CMD, utilisent le terme *classe abstraite* pour décrire une telle classe.)</span><span class="sxs-lookup"><span data-stu-id="9c619-118">(Other programming languages, such as C++ and C#, use the term *abstract class* to describe such a class.)</span></span>

## <a name="overriding-properties-and-methods-in-derived-classes"></a><span data-ttu-id="9c619-119">Propriétés et méthodes prépondérer dans les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="9c619-119">Overriding Properties and Methods in Derived Classes</span></span>

<span data-ttu-id="9c619-120">Par défaut, une classe dérivée des propriétés et des méthodes de sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-120">By default, a derived class inherits properties and methods from its base class.</span></span> <span data-ttu-id="9c619-121">Si une propriété ou une méthode héritée doit se comporter différemment dans la classe dérivée, elle peut être *remplacée.*</span><span class="sxs-lookup"><span data-stu-id="9c619-121">If an inherited property or method has to behave differently in the derived class it can be *overridden*.</span></span> <span data-ttu-id="9c619-122">Autrement dit, vous pouvez définir une nouvelle implémentation de la méthode dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c619-122">That is, you can define a new implementation of the method in the derived class.</span></span> <span data-ttu-id="9c619-123">Les modificateurs suivants sont utilisés pour contrôler la façon dont les propriétés et les méthodes sont substituées :</span><span class="sxs-lookup"><span data-stu-id="9c619-123">The following modifiers are used to control how properties and methods are overridden:</span></span>

- <span data-ttu-id="9c619-124">`Overridable`— Permet de répartir une propriété ou une méthode dans une classe dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c619-124">`Overridable` — Allows a property or method in a class to be overridden in a derived class.</span></span>

- <span data-ttu-id="9c619-125">`Overrides`— Remplace une `Overridable` propriété ou une méthode définie dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-125">`Overrides` — Overrides an `Overridable` property or method defined in the base class.</span></span>

- <span data-ttu-id="9c619-126">`NotOverridable`— Empêche qu’une propriété ou une méthode ne soit remplacée dans une classe d’héritage.</span><span class="sxs-lookup"><span data-stu-id="9c619-126">`NotOverridable` — Prevents a property or method from being overridden in an inheriting class.</span></span> <span data-ttu-id="9c619-127">Par défaut, `Public` `NotOverridable`les méthodes sont .</span><span class="sxs-lookup"><span data-stu-id="9c619-127">By default, `Public` methods are `NotOverridable`.</span></span>

- <span data-ttu-id="9c619-128">`MustOverride`— Exige qu’une classe dérivée l’emporte sur la propriété ou la méthode.</span><span class="sxs-lookup"><span data-stu-id="9c619-128">`MustOverride` — Requires that a derived class override the property or method.</span></span> <span data-ttu-id="9c619-129">Lorsque `MustOverride` le mot clé est utilisé, `Sub`la `Function`définition `Property` de la méthode se compose de seulement le , , ou la déclaration.</span><span class="sxs-lookup"><span data-stu-id="9c619-129">When the `MustOverride` keyword is used, the method definition consists of just the `Sub`, `Function`, or `Property` statement.</span></span> <span data-ttu-id="9c619-130">Aucune autre déclaration n’est autorisée, et en particulier il n’y a pas `End Sub` ou `End Function` déclaration.</span><span class="sxs-lookup"><span data-stu-id="9c619-130">No other statements are allowed, and specifically there is no `End Sub` or `End Function` statement.</span></span> <span data-ttu-id="9c619-131">`MustOverride`méthodes doivent être `MustInherit` déclarées en classe.</span><span class="sxs-lookup"><span data-stu-id="9c619-131">`MustOverride` methods must be declared in `MustInherit` classes.</span></span>

<span data-ttu-id="9c619-132">Supposons que vous voulez définir les classes pour gérer la paie.</span><span class="sxs-lookup"><span data-stu-id="9c619-132">Suppose you want to define classes to handle payroll.</span></span> <span data-ttu-id="9c619-133">Vous pouvez définir `Payroll` une classe `RunPayroll` générique qui contient une méthode qui calcule la paie pour une semaine typique.</span><span class="sxs-lookup"><span data-stu-id="9c619-133">You could define a generic `Payroll` class that contains a `RunPayroll` method that calculates payroll for a typical week.</span></span> <span data-ttu-id="9c619-134">Vous pouvez `Payroll` alors utiliser comme classe `BonusPayroll` de base pour une classe plus spécialisée, qui pourrait être utilisée lors de la distribution des primes des employés.</span><span class="sxs-lookup"><span data-stu-id="9c619-134">You could then use `Payroll` as a base class for a more specialized `BonusPayroll` class, which could be used when distributing employee bonuses.</span></span>

<span data-ttu-id="9c619-135">La `BonusPayroll` classe peut hériter `PayEmployee` et remplacer la `Payroll` méthode définie dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-135">The `BonusPayroll` class can inherit, and override, the `PayEmployee` method defined in the base `Payroll` class.</span></span>

<span data-ttu-id="9c619-136">L’exemple suivant définit une `Payroll,` classe de `BonusPayroll`base, et une classe `PayEmployee`dérivée, qui l’emporte sur une méthode héritée, .</span><span class="sxs-lookup"><span data-stu-id="9c619-136">The following example defines a base class, `Payroll,` and a derived class, `BonusPayroll`, which overrides an inherited method, `PayEmployee`.</span></span> <span data-ttu-id="9c619-137">Une `RunPayroll`procédure, , crée `Payroll` puis passe `BonusPayroll` un objet `Pay`et un objet `PayEmployee` à une fonction, , qui exécute la méthode des deux objets.</span><span class="sxs-lookup"><span data-stu-id="9c619-137">A procedure, `RunPayroll`, creates and then passes a `Payroll` object and a `BonusPayroll` object to a function, `Pay`, that executes the `PayEmployee` method of both objects.</span></span>

[!code-vb[VbVbalrOOP#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#28)]

## <a name="the-mybase-keyword"></a><span data-ttu-id="9c619-138">Le mot-clé MyBase</span><span class="sxs-lookup"><span data-stu-id="9c619-138">The MyBase Keyword</span></span>

<span data-ttu-id="9c619-139">Le `MyBase` mot clé se comporte comme une variable d’objet qui se réfère à la classe de base de l’instance actuelle d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9c619-139">The `MyBase` keyword behaves like an object variable that refers to the base class of the current instance of a class.</span></span> <span data-ttu-id="9c619-140">`MyBase`est fréquemment utilisé pour accéder aux membres de la classe de base qui sont remplacés ou ombragés dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c619-140">`MyBase` is frequently used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="9c619-141">En particulier, `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d’un constructeur de classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c619-141">In particular, `MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>

<span data-ttu-id="9c619-142">Supposons, par exemple, que vous concevez une classe dérivée qui remplace une méthode héritée de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-142">For example, suppose you are designing a derived class that overrides a method inherited from the base class.</span></span> <span data-ttu-id="9c619-143">La méthode précédée peut appeler la méthode dans la classe de base et modifier la valeur de retour comme indiqué dans le fragment de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9c619-143">The overridden method can call the method in the base class and modify the return value as shown in the following code fragment:</span></span>

[!code-vb[VbVbalrOOP#109](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#109)]

<span data-ttu-id="9c619-144">La liste suivante décrit `MyBase`les restrictions à l’utilisation :</span><span class="sxs-lookup"><span data-stu-id="9c619-144">The following list describes restrictions on using `MyBase`:</span></span>

- <span data-ttu-id="9c619-145">`MyBase`se réfère à la classe de base immédiate et à ses membres hérités.</span><span class="sxs-lookup"><span data-stu-id="9c619-145">`MyBase` refers to the immediate base class and its inherited members.</span></span> <span data-ttu-id="9c619-146">Il ne peut `Private` pas être utilisé pour accéder aux membres de la classe.</span><span class="sxs-lookup"><span data-stu-id="9c619-146">It cannot be used to access `Private` members in the class.</span></span>

- <span data-ttu-id="9c619-147">`MyBase`est un mot clé, pas un objet réel.</span><span class="sxs-lookup"><span data-stu-id="9c619-147">`MyBase` is a keyword, not a real object.</span></span> <span data-ttu-id="9c619-148">`MyBase`ne peuvent pas être affectés à une variable, `Is` transmis aux procédures ou utilisés en comparaison.</span><span class="sxs-lookup"><span data-stu-id="9c619-148">`MyBase` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="9c619-149">La méthode `MyBase` qui est admissible n’a pas à être définie dans la classe de base immédiate; il peut plutôt être défini dans une classe de base indirectement héritée.</span><span class="sxs-lookup"><span data-stu-id="9c619-149">The method that `MyBase` qualifies does not have to be defined in the immediate base class; it may instead be defined in an indirectly inherited base class.</span></span> <span data-ttu-id="9c619-150">Afin qu’une référence `MyBase` qualifiée pour compiler correctement, une classe de base doit contenir une méthode correspondant au nom et aux types de paramètres qui apparaissent dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="9c619-150">In order for a reference qualified by `MyBase` to compile correctly, some base class must contain a method matching the name and types of parameters that appear in the call.</span></span>

- <span data-ttu-id="9c619-151">Vous ne `MyBase` pouvez `MustOverride` pas utiliser pour appeler les méthodes de classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c619-151">You cannot use `MyBase` to call `MustOverride` base class methods.</span></span>

- <span data-ttu-id="9c619-152">`MyBase`ne peut pas être utilisé pour se qualifier lui-même.</span><span class="sxs-lookup"><span data-stu-id="9c619-152">`MyBase` cannot be used to qualify itself.</span></span> <span data-ttu-id="9c619-153">Par conséquent, le code suivant n’est pas valide :</span><span class="sxs-lookup"><span data-stu-id="9c619-153">Therefore, the following code is not valid:</span></span>

  `MyBase.MyBase.BtnOK_Click()`

- <span data-ttu-id="9c619-154">`MyBase`ne peut pas être utilisé dans les modules.</span><span class="sxs-lookup"><span data-stu-id="9c619-154">`MyBase` cannot be used in modules.</span></span>

- <span data-ttu-id="9c619-155">`MyBase`ne peut pas être utilisé pour `Friend` accéder aux membres de la classe de base qui sont marqués comme si la classe de base est dans une assemblée différente.</span><span class="sxs-lookup"><span data-stu-id="9c619-155">`MyBase` cannot be used to access base class members that are marked as `Friend` if the base class is in a different assembly.</span></span>

<span data-ttu-id="9c619-156">Pour plus d’informations et un autre exemple, voir [Comment : Accéder à une variable cachée par une classe dérivée](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span><span class="sxs-lookup"><span data-stu-id="9c619-156">For more information and another example, see [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).</span></span>

## <a name="the-myclass-keyword"></a><span data-ttu-id="9c619-157">Le mot-clé MyClass</span><span class="sxs-lookup"><span data-stu-id="9c619-157">The MyClass Keyword</span></span>

<span data-ttu-id="9c619-158">Le `MyClass` mot clé se comporte comme une variable d’objet qui se réfère à l’instance actuelle d’une classe telle qu’elle a été mise en œuvre à l’origine.</span><span class="sxs-lookup"><span data-stu-id="9c619-158">The `MyClass` keyword behaves like an object variable that refers to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="9c619-159">`MyClass`ressemble `Me`, mais chaque méthode `MyClass` et appel de propriété sur est traitée comme si la méthode ou la propriété [n’étaient pasOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span><span class="sxs-lookup"><span data-stu-id="9c619-159">`MyClass` resembles `Me`, but every method and property call on `MyClass` is treated as if the method or property were [NotOverridable](../../../../visual-basic/language-reference/modifiers/notoverridable.md).</span></span> <span data-ttu-id="9c619-160">Par conséquent, la méthode ou la propriété n’est pas affectée par le dépassement dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="9c619-160">Therefore, the method or property is not affected by overriding in a derived class.</span></span>

- <span data-ttu-id="9c619-161">`MyClass`est un mot clé, pas un objet réel.</span><span class="sxs-lookup"><span data-stu-id="9c619-161">`MyClass` is a keyword, not a real object.</span></span> <span data-ttu-id="9c619-162">`MyClass`ne peuvent pas être affectés à une variable, `Is` transmis aux procédures ou utilisés en comparaison.</span><span class="sxs-lookup"><span data-stu-id="9c619-162">`MyClass` cannot be assigned to a variable, passed to procedures, or used in an `Is` comparison.</span></span>

- <span data-ttu-id="9c619-163">`MyClass`se réfère à la classe de confinement et à ses membres hérités.</span><span class="sxs-lookup"><span data-stu-id="9c619-163">`MyClass` refers to the containing class and its inherited members.</span></span>

- <span data-ttu-id="9c619-164">`MyClass`peut être utilisé comme `Shared` un qualificatif pour les membres.</span><span class="sxs-lookup"><span data-stu-id="9c619-164">`MyClass` can be used as a qualifier for `Shared` members.</span></span>

- <span data-ttu-id="9c619-165">`MyClass`ne peut pas `Shared` être utilisé à l’intérieur d’une méthode, mais peut être utilisé à l’intérieur d’une méthode d’instance pour accéder à un membre partagé d’une classe.</span><span class="sxs-lookup"><span data-stu-id="9c619-165">`MyClass` cannot be used inside a `Shared` method, but can be used inside an instance method to access a shared member of a class.</span></span>

- <span data-ttu-id="9c619-166">`MyClass`ne peut pas être utilisé dans des modules standard.</span><span class="sxs-lookup"><span data-stu-id="9c619-166">`MyClass` cannot be used in standard modules.</span></span>

- <span data-ttu-id="9c619-167">`MyClass`peut être utilisé pour qualifier une méthode qui est définie dans une classe de base et qui n’a pas de mise en œuvre de la méthode fournie dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="9c619-167">`MyClass` can be used to qualify a method that is defined in a base class and that has no implementation of the method provided in that class.</span></span> <span data-ttu-id="9c619-168">Une telle référence a `MyBase.`le même sens que *la méthode*.</span><span class="sxs-lookup"><span data-stu-id="9c619-168">Such a reference has the same meaning as `MyBase.`*Method*.</span></span>

<span data-ttu-id="9c619-169">L’exemple suivant `Me` `MyClass`se compare et .</span><span class="sxs-lookup"><span data-stu-id="9c619-169">The following example compares `Me` and `MyClass`.</span></span>

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

<span data-ttu-id="9c619-170">Même `derivedClass` si les `testMethod`remplacements, le `MyClass` mot clé dans `useMyClass` annule les effets de la prépondération, `testMethod`et le compilateur résout l’appel à la version de la classe de base de .</span><span class="sxs-lookup"><span data-stu-id="9c619-170">Even though `derivedClass` overrides `testMethod`, the `MyClass` keyword in `useMyClass` nullifies the effects of overriding, and the compiler resolves the call to the base class version of `testMethod`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c619-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c619-171">See also</span></span>

- [<span data-ttu-id="9c619-172">Inherits (instruction)</span><span class="sxs-lookup"><span data-stu-id="9c619-172">Inherits Statement</span></span>](../../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="9c619-173">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="9c619-173">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
