---
title: Délégués et expressions lambda
description: Découvrez comment les délégués définissent un type, qui spécifie une signature de méthode particulière, qui peut être appelée directement ou passée à une autre méthode et appelée.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 34bfa4c6007ec771f784e927675f4e24d52e194f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391232"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="67666-103">Délégués et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="67666-103">Delegates and lambdas</span></span>

<span data-ttu-id="67666-104">Les délégués définissent un type, qui spécifie la signature d’une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="67666-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="67666-105">Une méthode (statique ou d’instance) qui répond à cette signature peut être attribuée à une variable de ce type, puis appelée directement (avec les arguments appropriés) ou passée elle-même comme argument à une autre méthode, puis appelée.</span><span class="sxs-lookup"><span data-stu-id="67666-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="67666-106">L’exemple suivant montre l’utilisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="67666-106">The following example demonstrates delegate use.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* <span data-ttu-id="67666-107">La ligne `public delegate string Reverse(string s);` crée un type délégué d’une certaine signature : dans notre exemple, une méthode qui prend un paramètre de type chaîne, puis retourne un paramètre de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="67666-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="67666-108">La méthode `static string ReverseString(string s)`, qui a exactement la même signature que le type délégué défini, implémente le délégué.</span><span class="sxs-lookup"><span data-stu-id="67666-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="67666-109">La ligne `Reverse rev = ReverseString;` montre que vous pouvez affecter une méthode à une variable du type délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="67666-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="67666-110">La ligne `Console.WriteLine(rev("a string"));` montre comment utiliser une variable d’un type délégué pour appeler le délégué.</span><span class="sxs-lookup"><span data-stu-id="67666-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="67666-111">Pour simplifier le processus de développement, .NET inclut un ensemble de types délégués que les programmeurs peuvent réutiliser sans avoir à en créer.</span><span class="sxs-lookup"><span data-stu-id="67666-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="67666-112">Il s’agit de `Func<>`, `Action<>` et `Predicate<>`. Ils peuvent être utilisés à plusieurs endroits dans les API .NET, sans avoir à définir de nouveaux types délégués.</span><span class="sxs-lookup"><span data-stu-id="67666-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="67666-113">Bien sûr, il existe certaines différences entre ces trois types, comme vous pouvez le constater dans leurs signatures, qui sont principalement liées à la manière dont ils doivent être utilisés :</span><span class="sxs-lookup"><span data-stu-id="67666-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="67666-114">`Action<>` est utilisé quand une action doit être effectuée à l’aide des arguments du délégué.</span><span class="sxs-lookup"><span data-stu-id="67666-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="67666-115">La méthode qu’il encapsule ne retourne pas une valeur.</span><span class="sxs-lookup"><span data-stu-id="67666-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="67666-116">`Func<>` est généralement utilisé dans le cas d’une transformation, autrement dit, quand vous devez transformer les arguments du délégué en un résultat différent.</span><span class="sxs-lookup"><span data-stu-id="67666-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="67666-117">C’est le cas, par exemple, des projections.</span><span class="sxs-lookup"><span data-stu-id="67666-117">Projections are a prime example of this.</span></span> <span data-ttu-id="67666-118">La méthode qu’il encapsule renvoie une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="67666-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="67666-119">`Predicate<>` est utilisé quand vous devez déterminer si l’argument répond à la condition du délégué.</span><span class="sxs-lookup"><span data-stu-id="67666-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="67666-120">Il peut également être `Func<T, bool>`écrit comme un , ce qui signifie que la méthode retourne une valeur boolean.</span><span class="sxs-lookup"><span data-stu-id="67666-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="67666-121">Nous pouvons maintenant reprendre notre exemple ci-dessus et le réécrire à l’aide du délégué `Func<>` au lieu d’un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="67666-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="67666-122">Le programme continue à s’exécuter exactement de la même façon.</span><span class="sxs-lookup"><span data-stu-id="67666-122">The program will continue running exactly the same.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

<span data-ttu-id="67666-123">Dans cet exemple simple, il peut sembler un peu superflu de définir une méthode en dehors de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="67666-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="67666-124">C’est pourquoi .NET Framework 2.0 a introduit le concept des **délégués anonymes**.</span><span class="sxs-lookup"><span data-stu-id="67666-124">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="67666-125">Grâce à eux, vous pouvez créer des délégués « inline », sans avoir à spécifier un autre type ou méthode.</span><span class="sxs-lookup"><span data-stu-id="67666-125">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="67666-126">Vous insérez simplement la définition du délégué là où vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="67666-126">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="67666-127">En guise d’exemple, nous allons utiliser notre délégué anonyme pour filtrer une liste uniquement sur les nombres pairs et les imprimer dans la console.</span><span class="sxs-lookup"><span data-stu-id="67666-127">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="67666-128">Comme vous pouvez le voir, le corps du délégué n’est qu’un ensemble d’expressions, comme tout autre délégué.</span><span class="sxs-lookup"><span data-stu-id="67666-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="67666-129">Mais au lieu d’en faire une définition distincte, nous l’avons introduit _ad hoc_ dans notre appel à la méthode <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67666-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="67666-130">Toutefois, même avec cette approche, nous avons encore beaucoup de code inutile.</span><span class="sxs-lookup"><span data-stu-id="67666-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="67666-131">C’est là que les **expressions lambda** interviennent.</span><span class="sxs-lookup"><span data-stu-id="67666-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="67666-132">Les expressions lambda ont été initialement introduites dans C# 3.0 comme l’un des principaux blocs de construction de la requête LINQ (Language-Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="67666-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="67666-133">Il s’agit simplement d’une syntaxe plus pratique pour l’utilisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="67666-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="67666-134">Ils déclarent une signature et un organisme de méthode, mais n’ont pas leur propre identité formelle, à moins qu’ils ne soient affectés à un délégué.</span><span class="sxs-lookup"><span data-stu-id="67666-134">They declare a signature and a method body, but don’t have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="67666-135">Contrairement aux délégués, elles peuvent être directement affectées comme côté gauche de l’inscription d’un événement, ou dans plusieurs clauses et méthodes LINQ.</span><span class="sxs-lookup"><span data-stu-id="67666-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="67666-136">Dans la mesure où une expression lambda est simplement une autre façon de spécifier un délégué, nous pouvons réécrire l’exemple ci-dessus pour utiliser une expression lambda au lieu d’un délégué anonyme.</span><span class="sxs-lookup"><span data-stu-id="67666-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="67666-137">Dans l’exemple précédent, l’expression lambda utilisée est `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="67666-137">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="67666-138">Là encore, il s’agit simplement d’une syntaxe **très** pratique pour l’utilisation des délégués. Par conséquent, ce qui se passe en coulisses est très proche de ce qui se passe avec le délégué anonyme.</span><span class="sxs-lookup"><span data-stu-id="67666-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="67666-139">Comme les expressions lambda sont juste des délégués, elles peuvent servir de gestionnaire d’événements sans aucun problème, comme l’illustre l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="67666-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

<span data-ttu-id="67666-140">Dans ce contexte, l’opérateur `+=` est utilisé pour s’abonner à un [événement](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="67666-140">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="67666-141">Pour plus d’informations, voir [Comment vous abonner et désabonner des événements](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="67666-141">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="67666-142">Ressources et informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="67666-142">Further reading and resources</span></span>

* [<span data-ttu-id="67666-143">Délégués</span><span class="sxs-lookup"><span data-stu-id="67666-143">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="67666-144">Fonctions anonymes</span><span class="sxs-lookup"><span data-stu-id="67666-144">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="67666-145">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="67666-145">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
