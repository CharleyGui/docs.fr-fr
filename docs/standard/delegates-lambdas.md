---
title: Délégués et expressions lambda
description: Découvrez comment les délégués, qui définissent un type spécifiant une signature de méthode particulière, peuvent être appelés directement ou passés à une autre méthode et appelés.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 43e896bfe267299d3b0cb12a8f71e42fe2c87a88
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280788"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="5c6bb-103">Délégués et expressions lambda</span><span class="sxs-lookup"><span data-stu-id="5c6bb-103">Delegates and lambdas</span></span>

<span data-ttu-id="5c6bb-104">Les délégués définissent un type qui spécifie une signature de méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="5c6bb-105">Une méthode (statique ou d’instance) qui répond à cette signature peut être attribuée à une variable de ce type, puis appelée directement (avec les arguments appropriés) ou passée elle-même comme argument à une autre méthode, puis appelée.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="5c6bb-106">L’exemple suivant montre l’utilisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="5c6bb-107">La ligne `public delegate string Reverse(string s);` crée un type délégué d’une certaine signature : dans notre exemple, une méthode qui prend un paramètre de type chaîne, puis retourne un paramètre de type chaîne.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="5c6bb-108">La méthode `static string ReverseString(string s)`, qui a exactement la même signature que le type délégué défini, implémente le délégué.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="5c6bb-109">La ligne `Reverse rev = ReverseString;` montre que vous pouvez affecter une méthode à une variable du type délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="5c6bb-110">La ligne `Console.WriteLine(rev("a string"));` montre comment utiliser une variable d’un type délégué pour appeler le délégué.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="5c6bb-111">Pour simplifier le processus de développement, .NET inclut un ensemble de types délégués que les programmeurs peuvent réutiliser sans avoir à en créer.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="5c6bb-112">Ces types sont `Func<>` , `Action<>` et `Predicate<>` , et ils peuvent être utilisés sans avoir à définir de nouveaux types délégués.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="5c6bb-113">Il existe quelques différences entre les trois types qui sont à faire avec la manière dont ils étaient destinés à être utilisés :</span><span class="sxs-lookup"><span data-stu-id="5c6bb-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="5c6bb-114">`Action<>` est utilisé quand une action doit être effectuée à l’aide des arguments du délégué.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="5c6bb-115">La méthode qu’elle encapsule ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="5c6bb-116">`Func<>` est généralement utilisé dans le cas d’une transformation, autrement dit, quand vous devez transformer les arguments du délégué en un résultat différent.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="5c6bb-117">Les projections sont un bon exemple.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-117">Projections are a good example.</span></span> <span data-ttu-id="5c6bb-118">La méthode qu’il encapsule retourne une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="5c6bb-119">`Predicate<>` est utilisé quand vous devez déterminer si l’argument répond à la condition du délégué.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="5c6bb-120">Elle peut également être écrite sous la forme d’un `Func<T, bool>` , ce qui signifie que la méthode retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="5c6bb-121">Nous pouvons maintenant reprendre notre exemple ci-dessus et le réécrire à l’aide du délégué `Func<>` au lieu d’un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="5c6bb-122">Le programme continue à s’exécuter exactement de la même façon.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="5c6bb-123">Dans cet exemple simple, il peut sembler un peu superflu de définir une méthode en dehors de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="5c6bb-124">.NET Framework 2,0 a introduit le concept de *délégués anonymes*, qui vous permettent de créer des délégués « Inline » sans avoir à spécifier de type ou de méthode supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="5c6bb-125">Dans l’exemple suivant, un délégué anonyme filtre une liste uniquement sur les nombres pairs, puis les imprime sur la console.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="5c6bb-126">Comme vous pouvez le voir, le corps du délégué n’est qu’un ensemble d’expressions, comme tout autre délégué.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="5c6bb-127">Mais au lieu d’être une définition distincte, nous l’avons introduite _ad hoc_ dans notre appel à la <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> méthode.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5c6bb-128">Toutefois, même avec cette approche, nous avons encore beaucoup de code inutile.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="5c6bb-129">C’est là que les *expressions lambda* interviennent.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="5c6bb-130">Les expressions lambda, ou simplement des « lambdas », ont été introduites en C# 3,0 comme un des blocs de construction de base de LINQ (Language Integrated Query).</span><span class="sxs-lookup"><span data-stu-id="5c6bb-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="5c6bb-131">Il s’agit simplement d’une syntaxe plus pratique pour l’utilisation des délégués.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="5c6bb-132">Elles déclarent une signature et un corps de méthode, mais n’ont pas d’identité formelle propre, sauf si elles sont assignées à un délégué.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="5c6bb-133">Contrairement aux délégués, elles peuvent être directement affectées comme côté gauche de l’inscription d’un événement, ou dans plusieurs clauses et méthodes LINQ.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="5c6bb-134">Dans la mesure où une expression lambda est simplement une autre façon de spécifier un délégué, nous pouvons réécrire l’exemple ci-dessus pour utiliser une expression lambda au lieu d’un délégué anonyme.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="5c6bb-135">Dans l’exemple précédent, l’expression lambda utilisée est `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="5c6bb-136">Là encore, il s’agit simplement d’une syntaxe pratique pour l’utilisation de délégués.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="5c6bb-137">Ce qui se passe en coulisses est semblable à ce qui se passe avec le délégué anonyme.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="5c6bb-138">Comme les expressions lambda sont juste des délégués, elles peuvent servir de gestionnaire d’événements sans aucun problème, comme l’illustre l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="5c6bb-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="5c6bb-139">Dans ce contexte, l’opérateur `+=` est utilisé pour s’abonner à un [événement](../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="5c6bb-139">The `+=` operator in this context is used to subscribe to an [event](../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="5c6bb-140">Pour plus d’informations, consultez [Comment s’abonner et annuler l’abonnement à des événements](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="5c6bb-140">For more information, see [How to subscribe to and unsubscribe from events](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="5c6bb-141">Ressources et informations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5c6bb-141">Further reading and resources</span></span>

* [<span data-ttu-id="5c6bb-142">Délégués</span><span class="sxs-lookup"><span data-stu-id="5c6bb-142">Delegates</span></span>](../csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="5c6bb-143">Fonctions anonymes</span><span class="sxs-lookup"><span data-stu-id="5c6bb-143">Anonymous Functions</span></span>](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="5c6bb-144">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="5c6bb-144">Lambda expressions</span></span>](../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
