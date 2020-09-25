---
title: Classes - Guide de programmation C#
description: En savoir plus sur les types de classe et découvrir comment les créer
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 93fc0296eeb410ba7ca0e781bededbe79820506d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178864"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="ce542-103">Classes (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ce542-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="ce542-104">Types référence</span><span class="sxs-lookup"><span data-stu-id="ce542-104">Reference types</span></span>  

<span data-ttu-id="ce542-105">Un type défini comme [class](../../language-reference/keywords/class.md) est un *type référence*.</span><span class="sxs-lookup"><span data-stu-id="ce542-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="ce542-106">Au moment de l’exécution, quand vous déclarez une variable de type référence, celle-ci contient la valeur [Null](../../language-reference/keywords/null.md) tant que vous n’avez pas explicitement créé une instance de la classe à l’aide de l’opérateur [new](../../language-reference/operators/new-operator.md), ou que vous ne lui avez pas assigné un objet existant d’un type compatible, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ce542-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="ce542-107">Quand l’objet est créé, une quantité de mémoire suffisante est allouée sur le tas managé de l’objet spécifié, et la variable contient uniquement une référence à l’emplacement de cet objet.</span><span class="sxs-lookup"><span data-stu-id="ce542-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="ce542-108">Les types sur le tas managé entraînent une surcharge quand ils sont alloués et récupérés par la fonctionnalité de gestion automatique de la mémoire du CLR (appelée *garbage collection*).</span><span class="sxs-lookup"><span data-stu-id="ce542-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="ce542-109">Toutefois, le garbage collection est également optimisé et, dans la plupart des cas, ne nuit pas aux performances.</span><span class="sxs-lookup"><span data-stu-id="ce542-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="ce542-110">Pour plus d’informations sur le garbage collection, consultez [Gestion automatique de la mémoire et garbage collection](../../../standard/garbage-collection/fundamentals.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/fundamentals.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="ce542-111">Déclaration de classes</span><span class="sxs-lookup"><span data-stu-id="ce542-111">Declaring Classes</span></span>

 <span data-ttu-id="ce542-112">Les classes sont déclarées à l’aide du mot clé [class](../../language-reference/keywords/class.md) suivi d’un identificateur unique, comme l’illustre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ce542-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="ce542-113">Le mot clé `class` est précédé du niveau d’accès.</span><span class="sxs-lookup"><span data-stu-id="ce542-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="ce542-114">Comme [public](../../language-reference/keywords/public.md) est utilisé dans ce cas, n’importe qui peut créer des instances de cette classe.</span><span class="sxs-lookup"><span data-stu-id="ce542-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="ce542-115">Le nom de la classe suit le mot clé `class`.</span><span class="sxs-lookup"><span data-stu-id="ce542-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="ce542-116">Le nom de la classe doit être un [nom d’identificateur](../inside-a-program/identifier-names.md) C# valide.</span><span class="sxs-lookup"><span data-stu-id="ce542-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="ce542-117">Le reste de la définition est le corps de la classe, où le comportement et les données sont définis.</span><span class="sxs-lookup"><span data-stu-id="ce542-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="ce542-118">Les champs, propriétés, méthodes et événements d’une classe sont désignés collectivement par le terme « *membres de classe* ».</span><span class="sxs-lookup"><span data-stu-id="ce542-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="ce542-119">Création d'objets</span><span class="sxs-lookup"><span data-stu-id="ce542-119">Creating objects</span></span>

<span data-ttu-id="ce542-120">Bien qu’ils soient parfois employés indifféremment, une classe et un objet sont deux choses différentes.</span><span class="sxs-lookup"><span data-stu-id="ce542-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="ce542-121">Une classe définit un type d’objet, mais il ne s’agit pas d’un objet en soi.</span><span class="sxs-lookup"><span data-stu-id="ce542-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="ce542-122">Un objet, qui est une entité concrète basée sur une classe, est parfois désigné par le terme « instance de classe ».</span><span class="sxs-lookup"><span data-stu-id="ce542-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="ce542-123">Vous pouvez créer des objets en utilisant le mot clé [new](../../language-reference/operators/new-operator.md) suivi du nom de la classe sur laquelle l’objet est basé, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce542-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="ce542-124">Quand une instance d’une classe est créée, une référence à l’objet est repassée au programmeur.</span><span class="sxs-lookup"><span data-stu-id="ce542-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="ce542-125">Dans l’exemple précédent, `object1` est une référence à un objet basé sur `Customer`.</span><span class="sxs-lookup"><span data-stu-id="ce542-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="ce542-126">Cette référence fait référence au nouvel objet, mais elle ne contient pas ses données.</span><span class="sxs-lookup"><span data-stu-id="ce542-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="ce542-127">En fait, vous pouvez créer une référence d’objet sans créer d’objet :</span><span class="sxs-lookup"><span data-stu-id="ce542-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="ce542-128">Nous vous déconseillons de créer des références d’objet comme celle-ci, sans référence à un objet, car toute tentative d’accès à un objet à l’aide d’une telle référence échoue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="ce542-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="ce542-129">Vous pouvez toutefois créer une telle référence pour faire référence à un objet : soit en créant un objet, soit en l’assignant à un objet existant, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce542-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it to an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="ce542-130">Ce code crée deux références d’objet qui font toutes deux référence au même objet.</span><span class="sxs-lookup"><span data-stu-id="ce542-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="ce542-131">Toute modification apportée à l’objet par le biais de `object3` est donc reflétée dans les utilisations suivantes de `object4`.</span><span class="sxs-lookup"><span data-stu-id="ce542-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="ce542-132">Les objets qui sont basés sur des classes étant désignés par référence, les classes sont appelées des « types référence ».</span><span class="sxs-lookup"><span data-stu-id="ce542-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="ce542-133">Héritage de classe</span><span class="sxs-lookup"><span data-stu-id="ce542-133">Class inheritance</span></span>  

<span data-ttu-id="ce542-134">Les classes prennent entièrement en charge l’*héritage*, caractéristique fondamentale de la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="ce542-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="ce542-135">Quand vous créez une classe, vous pouvez hériter de toute autre interface ou classe qui n’est pas définie comme [sealed](../../language-reference/keywords/sealed.md), et d’autres classes peuvent hériter de votre classe et substituer des méthodes virtuelles de la classe.</span><span class="sxs-lookup"><span data-stu-id="ce542-135">When you create a class, you can inherit from any other interface or class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span>

<span data-ttu-id="ce542-136">L’héritage se fait par le biais d’une *dérivation*, ce qui signifie qu’une classe est déclarée à l’aide d’une *classe de base* dont elle hérite les données et le comportement.</span><span class="sxs-lookup"><span data-stu-id="ce542-136">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="ce542-137">Pour spécifier une classe de base, ajoutez deux-points et le nom de la classe de base après le nom de la classe dérivée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ce542-137">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="ce542-138">Quand une classe déclare une classe de base, elle hérite de tous les membres de la classe de base à l’exception des constructeurs.</span><span class="sxs-lookup"><span data-stu-id="ce542-138">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="ce542-139">Pour plus d’informations, consultez [Héritage](inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-139">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="ce542-140">Contrairement à C++, une classe en C# ne peut hériter directement que d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="ce542-140">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="ce542-141">Toutefois, une classe de base pouvant elle-même hériter d’une autre classe, une classe peut hériter indirectement de plusieurs classes de base.</span><span class="sxs-lookup"><span data-stu-id="ce542-141">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="ce542-142">En outre, une classe peut implémenter directement plusieurs interfaces.</span><span class="sxs-lookup"><span data-stu-id="ce542-142">Furthermore, a class can directly implement more than one interface.</span></span> <span data-ttu-id="ce542-143">Pour plus d'informations, consultez [Interfaces](../interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-143">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="ce542-144">Une classe peut être déclarée [abstract](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-144">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="ce542-145">Une classe abstraite contient des méthodes abstraites qui ont une définition de signature, mais aucune implémentation.</span><span class="sxs-lookup"><span data-stu-id="ce542-145">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="ce542-146">Les classes abstraites ne peuvent pas être instanciées.</span><span class="sxs-lookup"><span data-stu-id="ce542-146">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="ce542-147">Elles peuvent être utilisées uniquement à travers des classes dérivées qui implémentent les méthodes abstraites.</span><span class="sxs-lookup"><span data-stu-id="ce542-147">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="ce542-148">En revanche, une classe [sealed](../../language-reference/keywords/sealed.md) ne permet pas à d’autres classes de dériver d’elle.</span><span class="sxs-lookup"><span data-stu-id="ce542-148">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="ce542-149">Pour plus d’informations, consultez [Classes abstract et sealed, et membres de classe](abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-149">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="ce542-150">Les définitions de classe peuvent être fractionnées entre différents fichiers sources.</span><span class="sxs-lookup"><span data-stu-id="ce542-150">Class definitions can be split between different source files.</span></span> <span data-ttu-id="ce542-151">Pour plus d’informations, consultez la page [Classes et méthodes partielles](partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-151">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce542-152">Exemple</span><span class="sxs-lookup"><span data-stu-id="ce542-152">Example</span></span>

<span data-ttu-id="ce542-153">L’exemple suivant définit une classe publique qui contient une [propriété implémentée automatiquement](auto-implemented-properties.md), une méthode et une méthode spéciale appelée un constructeur.</span><span class="sxs-lookup"><span data-stu-id="ce542-153">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="ce542-154">Pour plus d’informations, consultez les rubriques [Propriétés](properties.md), [Méthodes](methods.md) et [Constructeurs](constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ce542-154">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="ce542-155">Les instances de la classe sont ensuite instanciées à l’aide du mot clé `new`.</span><span class="sxs-lookup"><span data-stu-id="ce542-155">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="ce542-156">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ce542-156">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ce542-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce542-157">See also</span></span>

- [<span data-ttu-id="ce542-158">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ce542-158">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ce542-159">Programmation orientée objet dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce542-159">Object-Oriented Programming</span></span>](../concepts/object-oriented-programming.md)
- [<span data-ttu-id="ce542-160">Polymorphisme</span><span class="sxs-lookup"><span data-stu-id="ce542-160">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="ce542-161">Noms d’identificateurs</span><span class="sxs-lookup"><span data-stu-id="ce542-161">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- <span data-ttu-id="ce542-162">[Members](members.md) (Membres)</span><span class="sxs-lookup"><span data-stu-id="ce542-162">[Members](members.md)</span></span>
- [<span data-ttu-id="ce542-163">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce542-163">Methods</span></span>](methods.md)
- [<span data-ttu-id="ce542-164">Constructeurs</span><span class="sxs-lookup"><span data-stu-id="ce542-164">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="ce542-165">Finaliseurs</span><span class="sxs-lookup"><span data-stu-id="ce542-165">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="ce542-166">Objets</span><span class="sxs-lookup"><span data-stu-id="ce542-166">Objects</span></span>](objects.md)
