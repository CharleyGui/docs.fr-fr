---
title: Savoir quand utiliser les mots clés override et new - Guide de programmation C#
description: Utilisez les mots clés New et override en C# pour spécifier comment interagir les méthodes portant le même nom dans une classe de base et une classe dérivée.
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 732a37c08b4c7bb998a7cc5dcfbd00d4e706b06c
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864538"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="fa928-103">Savoir quand utiliser les mots clés override et new (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="fa928-103">Knowing When to Use Override and New Keywords (C# Programming Guide)</span></span>

<span data-ttu-id="fa928-104">En C#, une méthode dans une classe dérivée peut avoir le même nom qu’une méthode dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="fa928-104">In C#, a method in a derived class can have the same name as a method in the base class.</span></span> <span data-ttu-id="fa928-105">Vous pouvez spécifier le mode d’interaction des méthodes avec les mots clés [new](../../language-reference/keywords/new-modifier.md) et [override](../../language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="fa928-105">You can specify how the methods interact by using the [new](../../language-reference/keywords/new-modifier.md) and [override](../../language-reference/keywords/override.md) keywords.</span></span> <span data-ttu-id="fa928-106">Le modificateur `override`*étend* la méthode `virtual` de la classe de base, tandis que le modificateur `new`*masque* une méthode de classe de base accessible.</span><span class="sxs-lookup"><span data-stu-id="fa928-106">The `override` modifier *extends* the base class `virtual` method, and the `new` modifier *hides* an accessible base class method.</span></span> <span data-ttu-id="fa928-107">La différence est illustrée dans les exemples de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fa928-107">The difference is illustrated in the examples in this topic.</span></span>  
  
 <span data-ttu-id="fa928-108">Dans une application console, déclarez les deux classes suivantes, `BaseClass` et `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-108">In a console application, declare the following two classes, `BaseClass` and `DerivedClass`.</span></span> <span data-ttu-id="fa928-109">`DerivedClass` hérite de `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-109">`DerivedClass` inherits from `BaseClass`.</span></span>  
  
```csharp  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
```  
  
 <span data-ttu-id="fa928-110">Dans la méthode `Main`, déclarez les variables `bc`, `dc` et `bcdc`.</span><span class="sxs-lookup"><span data-stu-id="fa928-110">In the `Main` method, declare variables `bc`, `dc`, and `bcdc`.</span></span>  
  
- <span data-ttu-id="fa928-111">`bc` est de type `BaseClass` et sa valeur est de type `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-111">`bc` is of type `BaseClass`, and its value is of type `BaseClass`.</span></span>  
  
- <span data-ttu-id="fa928-112">`dc` est de type `DerivedClass` et sa valeur est de type `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-112">`dc` is of type `DerivedClass`, and its value is of type `DerivedClass`.</span></span>  
  
- <span data-ttu-id="fa928-113">`bcdc` est de type `BaseClass` et sa valeur est de type `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-113">`bcdc` is of type `BaseClass`, and its value is of type `DerivedClass`.</span></span> <span data-ttu-id="fa928-114">Il s’agit de la variable à surveiller.</span><span class="sxs-lookup"><span data-stu-id="fa928-114">This is the variable to pay attention to.</span></span>  
  
 <span data-ttu-id="fa928-115">Comme `bc` et `bcdc` ont le type `BaseClass`, ils ne peuvent accéder directement qu’à `Method1`, sauf si vous effectuez un cast.</span><span class="sxs-lookup"><span data-stu-id="fa928-115">Because `bc` and `bcdc` have type `BaseClass`, they can only directly access `Method1`, unless you use casting.</span></span> <span data-ttu-id="fa928-116">La variable `dc` peut accéder à `Method1` et `Method2`.</span><span class="sxs-lookup"><span data-stu-id="fa928-116">Variable `dc` can access both `Method1` and `Method2`.</span></span> <span data-ttu-id="fa928-117">Ces relations sont illustrées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="fa928-117">These relationships are shown in the following code.</span></span>  
  
```csharp  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
```  
  
 <span data-ttu-id="fa928-118">Ensuite, ajoutez la méthode `Method2` suivante à `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-118">Next, add the following `Method2` method to `BaseClass`.</span></span> <span data-ttu-id="fa928-119">La signature de cette méthode correspond à celle de la méthode `Method2` dans `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-119">The signature of this method matches the signature of the `Method2` method in `DerivedClass`.</span></span>  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 <span data-ttu-id="fa928-120">Comme `BaseClass` a maintenant une méthode `Method2`, une deuxième instruction d’appel peut être ajoutée pour les variables `BaseClass``bc` et `bcdc`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="fa928-120">Because `BaseClass` now has a `Method2` method, a second calling statement can be added for `BaseClass` variables `bc` and `bcdc`, as shown in the following code.</span></span>  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 <span data-ttu-id="fa928-121">Quand vous générez le projet, vous constatez que l’ajout de la méthode `Method2` dans `BaseClass` génère un avertissement.</span><span class="sxs-lookup"><span data-stu-id="fa928-121">When you build the project, you see that the addition of the `Method2` method in `BaseClass` causes a warning.</span></span> <span data-ttu-id="fa928-122">L’avertissement indique que la méthode `Method2` dans `DerivedClass` masque la méthode `Method2` dans `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-122">The warning says that the `Method2` method in `DerivedClass` hides the `Method2` method in `BaseClass`.</span></span> <span data-ttu-id="fa928-123">Il est recommandé d’utiliser le mot clé `new` dans la définition de `Method2` si vous avez l’intention de provoquer ce résultat.</span><span class="sxs-lookup"><span data-stu-id="fa928-123">You are advised to use the `new` keyword in the `Method2` definition if you intend to cause that result.</span></span> <span data-ttu-id="fa928-124">Sinon, vous pouvez renommer l’une des méthodes `Method2` pour résoudre l’avertissement, mais ce n’est pas toujours pratique.</span><span class="sxs-lookup"><span data-stu-id="fa928-124">Alternatively, you could rename one of the `Method2` methods to resolve the warning, but that is not always practical.</span></span>  
  
 <span data-ttu-id="fa928-125">Avant d’ajouter `new`, exécutez le programme pour afficher la sortie produite par les instructions d’appel supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fa928-125">Before adding `new`, run the program to see the output produced by the additional calling statements.</span></span> <span data-ttu-id="fa928-126">Les résultats suivants s'affichent.</span><span class="sxs-lookup"><span data-stu-id="fa928-126">The following results are displayed.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="fa928-127">Le mot clé `new` conserve les relations qui génèrent cette sortie, mais supprime l’avertissement.</span><span class="sxs-lookup"><span data-stu-id="fa928-127">The `new` keyword preserves the relationships that produce that output, but it suppresses the warning.</span></span> <span data-ttu-id="fa928-128">Les variables de type `BaseClass` continuent d’accéder aux membres de `BaseClass` et la variable de type `DerivedClass` continue d’accéder aux membres dans `DerivedClass` avant de prendre en compte les membres hérités de `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-128">The variables that have type `BaseClass` continue to access the members of `BaseClass`, and the variable that has type `DerivedClass` continues to access members in `DerivedClass` first, and then to consider members inherited from `BaseClass`.</span></span>  
  
 <span data-ttu-id="fa928-129">Pour supprimer l’avertissement, ajoutez le modificateur `new` à la définition de `Method2` dans `DerivedClass`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="fa928-129">To suppress the warning, add the `new` modifier to the definition of `Method2` in `DerivedClass`, as shown in the following code.</span></span> <span data-ttu-id="fa928-130">Le modificateur peut être ajouté avant ou après `public`.</span><span class="sxs-lookup"><span data-stu-id="fa928-130">The modifier can be added before or after `public`.</span></span>  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 <span data-ttu-id="fa928-131">Réexécutez le programme pour vérifier que la sortie n’a pas changé.</span><span class="sxs-lookup"><span data-stu-id="fa928-131">Run the program again to verify that the output has not changed.</span></span> <span data-ttu-id="fa928-132">Vérifiez aussi que l’avertissement ne s’affiche plus.</span><span class="sxs-lookup"><span data-stu-id="fa928-132">Also verify that the warning no longer appears.</span></span> <span data-ttu-id="fa928-133">À l’aide de `new`, vous déclarez que vous êtes conscient que le membre qu’il modifie masque un membre hérité de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="fa928-133">By using `new`, you are asserting that you are aware that the member that it modifies hides a member that is inherited from the base class.</span></span> <span data-ttu-id="fa928-134">Pour plus d’informations sur le masquage de nom par héritage, consultez [new, modificateur](../../language-reference/keywords/new-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="fa928-134">For more information about name hiding through inheritance, see [new Modifier](../../language-reference/keywords/new-modifier.md).</span></span>  
  
 <span data-ttu-id="fa928-135">Pour comparer ce comportement aux effets de l’utilisation de `override`, ajoutez la méthode suivante à `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-135">To contrast this behavior to the effects of using `override`, add the following method to `DerivedClass`.</span></span> <span data-ttu-id="fa928-136">Le modificateur `override` peut être ajouté avant ou après `public`.</span><span class="sxs-lookup"><span data-stu-id="fa928-136">The `override` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 <span data-ttu-id="fa928-137">Ajoutez le modificateur `virtual` à la définition de `Method1` dans `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-137">Add the `virtual` modifier to the definition of `Method1` in `BaseClass`.</span></span> <span data-ttu-id="fa928-138">Le modificateur `virtual` peut être ajouté avant ou après `public`.</span><span class="sxs-lookup"><span data-stu-id="fa928-138">The `virtual` modifier can be added before or after `public`.</span></span>  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 <span data-ttu-id="fa928-139">Réexécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="fa928-139">Run the project again.</span></span> <span data-ttu-id="fa928-140">Notez en particulier les deux dernières lignes de la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="fa928-140">Notice especially the last two lines of the following output.</span></span>  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 <span data-ttu-id="fa928-141">L’utilisation du modificateur `override` permet à `bcdc` d’accéder à la méthode `Method1` définie dans `DerivedClass`.</span><span class="sxs-lookup"><span data-stu-id="fa928-141">The use of the `override` modifier enables `bcdc` to access the `Method1` method that is defined in `DerivedClass`.</span></span> <span data-ttu-id="fa928-142">En règle générale, il s’agit du comportement souhaité dans les hiérarchies d’héritage.</span><span class="sxs-lookup"><span data-stu-id="fa928-142">Typically, that is the desired behavior in inheritance hierarchies.</span></span> <span data-ttu-id="fa928-143">Vous voulez que les objets dont les valeurs sont créées à partir de la classe dérivée utilisent les méthodes définies dans la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="fa928-143">You want objects that have values that are created from the derived class to use the methods that are defined in the derived class.</span></span> <span data-ttu-id="fa928-144">Vous obtenez ce comportement en utilisant `override` pour étendre la méthode de classe de base.</span><span class="sxs-lookup"><span data-stu-id="fa928-144">You achieve that behavior by using `override` to extend the base class method.</span></span>  
  
 <span data-ttu-id="fa928-145">Le code suivant contient l’exemple complet.</span><span class="sxs-lookup"><span data-stu-id="fa928-145">The following code contains the full example.</span></span>  
  
```csharp  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="fa928-146">L’exemple suivant illustre un comportement similaire dans un autre contexte.</span><span class="sxs-lookup"><span data-stu-id="fa928-146">The following example illustrates similar behavior in a different context.</span></span> <span data-ttu-id="fa928-147">L’exemple définit trois classes : une classe de base nommée `Car` et deux de ses classes dérivées, `ConvertibleCar` et `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="fa928-147">The example defines three classes: a base class named `Car` and two classes that are derived from it, `ConvertibleCar` and `Minivan`.</span></span> <span data-ttu-id="fa928-148">La classe de base contient une méthode `DescribeCar`.</span><span class="sxs-lookup"><span data-stu-id="fa928-148">The base class contains a `DescribeCar` method.</span></span> <span data-ttu-id="fa928-149">La méthode affiche une description de base d’une voiture et appelle ensuite `ShowDetails` pour fournir des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="fa928-149">The method displays a basic description of a car, and then calls `ShowDetails` to provide additional information.</span></span> <span data-ttu-id="fa928-150">Chacune des trois classes définit une méthode `ShowDetails`.</span><span class="sxs-lookup"><span data-stu-id="fa928-150">Each of the three classes defines a `ShowDetails` method.</span></span> <span data-ttu-id="fa928-151">Le modificateur `new` est utilisé pour définir `ShowDetails` dans la classe `ConvertibleCar`.</span><span class="sxs-lookup"><span data-stu-id="fa928-151">The `new` modifier is used to define `ShowDetails` in the `ConvertibleCar` class.</span></span> <span data-ttu-id="fa928-152">Le modificateur `override` est utilisé pour définir `ShowDetails` dans la classe `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="fa928-152">The `override` modifier is used to define `ShowDetails` in the `Minivan` class.</span></span>  
  
```csharp  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
```  
  
 <span data-ttu-id="fa928-153">L’exemple vérifie la version de `ShowDetails` qui est appelée.</span><span class="sxs-lookup"><span data-stu-id="fa928-153">The example tests which version of `ShowDetails` is called.</span></span> <span data-ttu-id="fa928-154">La méthode suivante, `TestCars1`, déclare une instance de chaque classe, puis appelle `DescribeCar` sur chaque instance.</span><span class="sxs-lookup"><span data-stu-id="fa928-154">The following method, `TestCars1`, declares an instance of each class, and then calls `DescribeCar` on each instance.</span></span>  
  
```csharp  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
```  
  
 <span data-ttu-id="fa928-155">`TestCars1` génère la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="fa928-155">`TestCars1` produces the following output.</span></span> <span data-ttu-id="fa928-156">Notez en particulier les résultats de `car2`, qui ne correspondent probablement pas à ce que vous attendiez.</span><span class="sxs-lookup"><span data-stu-id="fa928-156">Notice especially the results for `car2`, which probably are not what you expected.</span></span> <span data-ttu-id="fa928-157">Le type de l’objet est `ConvertibleCar`, mais `DescribeCar` n’accède pas à la version de `ShowDetails` qui est défini dans la classe `ConvertibleCar`, car cette méthode est déclarée avec le modificateur `new`, et non `override`.</span><span class="sxs-lookup"><span data-stu-id="fa928-157">The type of the object is `ConvertibleCar`, but `DescribeCar` does not access the version of `ShowDetails` that is defined in the `ConvertibleCar` class because that method is declared with the `new` modifier, not the `override` modifier.</span></span> <span data-ttu-id="fa928-158">Par conséquent, un objet `ConvertibleCar` affiche la même description qu’un objet `Car`.</span><span class="sxs-lookup"><span data-stu-id="fa928-158">As a result, a `ConvertibleCar` object displays the same description as a `Car` object.</span></span> <span data-ttu-id="fa928-159">Comparez les résultats pour `car3`, qui est un objet `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="fa928-159">Contrast the results for `car3`, which is a `Minivan` object.</span></span> <span data-ttu-id="fa928-160">Dans ce cas, la méthode `ShowDetails` déclarée dans la classe `Minivan` substitue la méthode `ShowDetails` déclarée dans la classe `Car` et la description affichée décrit un minivan.</span><span class="sxs-lookup"><span data-stu-id="fa928-160">In this case, the `ShowDetails` method that is declared in the `Minivan` class overrides the `ShowDetails` method that is declared in the `Car` class, and the description that is displayed describes a minivan.</span></span>  
  
```csharp  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="fa928-161">`TestCars2` crée une liste d’objets de type `Car`.</span><span class="sxs-lookup"><span data-stu-id="fa928-161">`TestCars2` creates a list of objects that have type `Car`.</span></span> <span data-ttu-id="fa928-162">Les valeurs des objets sont instanciées à partir des classes `Car`, `ConvertibleCar` et `Minivan`.</span><span class="sxs-lookup"><span data-stu-id="fa928-162">The values of the objects are instantiated from the `Car`, `ConvertibleCar`, and `Minivan` classes.</span></span> <span data-ttu-id="fa928-163">`DescribeCar` est appelé sur chaque élément de la liste.</span><span class="sxs-lookup"><span data-stu-id="fa928-163">`DescribeCar` is called on each element of the list.</span></span> <span data-ttu-id="fa928-164">Le code suivant illustre la définition de `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="fa928-164">The following code shows the definition of `TestCars2`.</span></span>  
  
```csharp  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
```  
  
 <span data-ttu-id="fa928-165">La sortie suivante s’affiche.</span><span class="sxs-lookup"><span data-stu-id="fa928-165">The following output is displayed.</span></span> <span data-ttu-id="fa928-166">Notez qu’elle est identique à la sortie affichée par `TestCars1`.</span><span class="sxs-lookup"><span data-stu-id="fa928-166">Notice that it is the same as the output that is displayed by `TestCars1`.</span></span> <span data-ttu-id="fa928-167">La méthode `ShowDetails` de la classe `ConvertibleCar` n’est pas appelée, que le type de l’objet soit `ConvertibleCar`, comme dans `TestCars1`, ou `Car`, comme dans `TestCars2`.</span><span class="sxs-lookup"><span data-stu-id="fa928-167">The `ShowDetails` method of the `ConvertibleCar` class is not called, regardless of whether the type of the object is `ConvertibleCar`, as in `TestCars1`, or `Car`, as in `TestCars2`.</span></span> <span data-ttu-id="fa928-168">À l’inverse, `car3` appelle la méthode `ShowDetails` à partir de la classe `Minivan` dans les deux cas, que son type soit `Minivan` ou `Car`.</span><span class="sxs-lookup"><span data-stu-id="fa928-168">Conversely, `car3` calls the `ShowDetails` method from the `Minivan` class in both cases, whether it has type `Minivan` or type `Car`.</span></span>  
  
```csharp  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
```  
  
 <span data-ttu-id="fa928-169">Les méthodes `TestCars3` et `TestCars4` terminent l’exemple.</span><span class="sxs-lookup"><span data-stu-id="fa928-169">Methods `TestCars3` and `TestCars4` complete the example.</span></span> <span data-ttu-id="fa928-170">Ces méthodes appellent `ShowDetails` directement, d’abord à partir des objets déclarés avec le type `ConvertibleCar` et `Minivan` (`TestCars3`), puis à partir des objets déclarés avec le type `Car` (`TestCars4`).</span><span class="sxs-lookup"><span data-stu-id="fa928-170">These methods call `ShowDetails` directly, first from objects declared to have type `ConvertibleCar` and `Minivan` (`TestCars3`), then from objects declared to have type `Car` (`TestCars4`).</span></span> <span data-ttu-id="fa928-171">Le code suivant définit ces deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="fa928-171">The following code defines these two methods.</span></span>  
  
```csharp  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
```  
  
 <span data-ttu-id="fa928-172">Les méthodes produisent la sortie suivante, qui correspond aux résultats du premier exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="fa928-172">The methods produce the following output, which corresponds to the results from the first example in this topic.</span></span>  
  
```csharp  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
```  
  
 <span data-ttu-id="fa928-173">Le code suivant illustre le projet complet et sa sortie.</span><span class="sxs-lookup"><span data-stu-id="fa928-173">The following code shows the complete project and its output.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa928-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa928-174">See also</span></span>

- [<span data-ttu-id="fa928-175">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="fa928-175">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fa928-176">Classes et structs</span><span class="sxs-lookup"><span data-stu-id="fa928-176">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="fa928-177">Versioning avec les mots clés override et new</span><span class="sxs-lookup"><span data-stu-id="fa928-177">Versioning with the Override and New Keywords</span></span>](./versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="fa928-178">base</span><span class="sxs-lookup"><span data-stu-id="fa928-178">base</span></span>](../../language-reference/keywords/base.md)
- [<span data-ttu-id="fa928-179">abstraction</span><span class="sxs-lookup"><span data-stu-id="fa928-179">abstract</span></span>](../../language-reference/keywords/abstract.md)
