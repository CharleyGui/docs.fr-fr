---
title: Savoir quand utiliser les mots clés override et new - Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- override keyword [C#]
- new keyword [C#]
- polymorphism [C#], using override and new [C#]
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
ms.openlocfilehash: 493c6c5f5bf47c6b2cd140ac0f6922f91ca4252b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170258"
---
# <a name="knowing-when-to-use-override-and-new-keywords-c-programming-guide"></a>Savoir quand utiliser les mots clés override et new (Guide de programmation C#)

En C#, une méthode dans une classe dérivée peut avoir le même nom qu’une méthode dans la classe de base. Vous pouvez spécifier le mode d’interaction des méthodes avec les mots clés [new](../../language-reference/keywords/new-modifier.md) et [override](../../language-reference/keywords/override.md). Le modificateur `override`*étend* la méthode `virtual` de la classe de base, tandis que le modificateur `new`*masque* une méthode de classe de base accessible. La différence est illustrée dans les exemples de cette rubrique.  
  
 Dans une application console, déclarez les deux classes suivantes, `BaseClass` et `DerivedClass`. `DerivedClass` hérite de `BaseClass`.  
  
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
  
 Dans la méthode `Main`, déclarez les variables `bc`, `dc` et `bcdc`.  
  
- `bc` est de type `BaseClass` et sa valeur est de type `BaseClass`.  
  
- `dc` est de type `DerivedClass` et sa valeur est de type `DerivedClass`.  
  
- `bcdc` est de type `BaseClass` et sa valeur est de type `DerivedClass`. Il s’agit de la variable à surveiller.  
  
 Comme `bc` et `bcdc` ont le type `BaseClass`, ils ne peuvent accéder directement qu’à `Method1`, sauf si vous effectuez un cast. La variable `dc` peut accéder à `Method1` et `Method2`. Ces relations sont illustrées dans le code suivant.  
  
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
  
 Ensuite, ajoutez la méthode `Method2` suivante à `BaseClass`. La signature de cette méthode correspond à celle de la méthode `Method2` dans `DerivedClass`.  
  
```csharp  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
```  
  
 Comme `BaseClass` a maintenant une méthode `Method2`, une deuxième instruction d’appel peut être ajoutée pour les variables `BaseClass``bc` et `bcdc`, comme illustré dans le code suivant.  
  
```csharp  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
```  
  
 Quand vous générez le projet, vous constatez que l’ajout de la méthode `Method2` dans `BaseClass` génère un avertissement. L’avertissement indique que la méthode `Method2` dans `DerivedClass` masque la méthode `Method2` dans `BaseClass`. Il est recommandé d’utiliser le mot clé `new` dans la définition de `Method2` si vous avez l’intention de provoquer ce résultat. Sinon, vous pouvez renommer l’une des méthodes `Method2` pour résoudre l’avertissement, mais ce n’est pas toujours pratique.  
  
 Avant d’ajouter `new`, exécutez le programme pour afficher la sortie produite par les instructions d’appel supplémentaires. Les résultats suivants s'affichent.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
```  
  
 Le mot clé `new` conserve les relations qui génèrent cette sortie, mais supprime l’avertissement. Les variables de type `BaseClass` continuent d’accéder aux membres de `BaseClass` et la variable de type `DerivedClass` continue d’accéder aux membres dans `DerivedClass` avant de prendre en compte les membres hérités de `BaseClass`.  
  
 Pour supprimer l’avertissement, ajoutez le modificateur `new` à la définition de `Method2` dans `DerivedClass`, comme illustré dans le code suivant. Le modificateur peut être ajouté avant ou après `public`.  
  
```csharp  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
```  
  
 Réexécutez le programme pour vérifier que la sortie n’a pas changé. Vérifiez aussi que l’avertissement ne s’affiche plus. À l’aide de `new`, vous déclarez que vous êtes conscient que le membre qu’il modifie masque un membre hérité de la classe de base. Pour plus d’informations sur le masquage de nom par héritage, consultez [new, modificateur](../../language-reference/keywords/new-modifier.md).  
  
 Pour comparer ce comportement aux effets de l’utilisation de `override`, ajoutez la méthode suivante à `DerivedClass`. Le modificateur `override` peut être ajouté avant ou après `public`.  
  
```csharp  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
```  
  
 Ajoutez le modificateur `virtual` à la définition de `Method1` dans `BaseClass`. Le modificateur `virtual` peut être ajouté avant ou après `public`.  
  
```csharp  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
```  
  
 Réexécutez le projet. Notez en particulier les deux dernières lignes de la sortie suivante.  
  
```csharp  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
```  
  
 L’utilisation du modificateur `override` permet à `bcdc` d’accéder à la méthode `Method1` définie dans `DerivedClass`. En règle générale, il s’agit du comportement souhaité dans les hiérarchies d’héritage. Vous voulez que les objets dont les valeurs sont créées à partir de la classe dérivée utilisent les méthodes définies dans la classe dérivée. Vous obtenez ce comportement en utilisant `override` pour étendre la méthode de classe de base.  
  
 Le code suivant contient l’exemple complet.  
  
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
  
 L’exemple suivant illustre un comportement similaire dans un autre contexte. L’exemple définit trois classes : une classe de base nommée `Car` et deux de ses classes dérivées, `ConvertibleCar` et `Minivan`. La classe de base contient une méthode `DescribeCar`. La méthode affiche une description de base d’une voiture et appelle ensuite `ShowDetails` pour fournir des informations supplémentaires. Chacune des trois classes définit une méthode `ShowDetails`. Le modificateur `new` est utilisé pour définir `ShowDetails` dans la classe `ConvertibleCar`. Le modificateur `override` est utilisé pour définir `ShowDetails` dans la classe `Minivan`.  
  
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
  
 L’exemple vérifie la version de `ShowDetails` qui est appelée. La méthode suivante, `TestCars1`, déclare une instance de chaque classe, puis appelle `DescribeCar` sur chaque instance.  
  
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
  
 `TestCars1` génère la sortie suivante. Notez en particulier les résultats de `car2`, qui ne correspondent probablement pas à ce que vous attendiez. Le type de l’objet est `ConvertibleCar`, mais `DescribeCar` n’accède pas à la version de `ShowDetails` qui est défini dans la classe `ConvertibleCar`, car cette méthode est déclarée avec le modificateur `new`, et non `override`. Par conséquent, un objet `ConvertibleCar` affiche la même description qu’un objet `Car`. Comparez les résultats pour `car3`, qui est un objet `Minivan`. Dans ce cas, la méthode `ShowDetails` déclarée dans la classe `Minivan` substitue la méthode `ShowDetails` déclarée dans la classe `Car` et la description affichée décrit un minivan.  
  
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
  
 `TestCars2` crée une liste d’objets de type `Car`. Les valeurs des objets sont instanciées à partir des classes `Car`, `ConvertibleCar` et `Minivan`. `DescribeCar` est appelé sur chaque élément de la liste. Le code suivant illustre la définition de `TestCars2`.  
  
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
  
 La sortie suivante s’affiche. Notez qu’elle est identique à la sortie affichée par `TestCars1`. La méthode `ShowDetails` de la classe `ConvertibleCar` n’est pas appelée, que le type de l’objet soit `ConvertibleCar`, comme dans `TestCars1`, ou `Car`, comme dans `TestCars2`. À l’inverse, `car3` appelle la méthode `ShowDetails` à partir de la classe `Minivan` dans les deux cas, que son type soit `Minivan` ou `Car`.  
  
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
  
 Les méthodes `TestCars3` et `TestCars4` terminent l’exemple. Ces méthodes appellent `ShowDetails` directement, d’abord à partir des objets déclarés avec le type `ConvertibleCar` et `Minivan` (`TestCars3`), puis à partir des objets déclarés avec le type `Car` (`TestCars4`). Le code suivant définit ces deux méthodes.  
  
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
  
 Les méthodes produisent la sortie suivante, qui correspond aux résultats du premier exemple de cette rubrique.  
  
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
  
 Le code suivant illustre le projet complet et sa sortie.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Classes et structs](./index.md)
- [Gestion de version avec les mots clés override et new](./versioning-with-the-override-and-new-keywords.md)
- [base](../../language-reference/keywords/base.md)
- [Abstrait](../../language-reference/keywords/abstract.md)
