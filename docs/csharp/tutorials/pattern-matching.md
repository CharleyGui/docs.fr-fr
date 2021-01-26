---
title: 'Didacticiel : générer des algorithmes avec des critères spéciaux'
description: Ce tutoriel avancé montre comment utiliser des techniques de critères spéciaux pour créer des fonctionnalités à l’aide de données et d’algorithmes créés séparément.
ms.date: 10/06/2020
ms.technology: csharp-whats-new
ms.custom: contperf-fy21q1
ms.openlocfilehash: be1c330973859df62cd4706e5f6f9ca4326fb221
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794821"
---
# <a name="tutorial-use-pattern-matching-to-build-type-driven-and-data-driven-algorithms"></a><span data-ttu-id="e53a5-103">Didacticiel : utiliser des critères spéciaux pour générer des algorithmes pilotés par type et pilotés par les données.</span><span class="sxs-lookup"><span data-stu-id="e53a5-103">Tutorial: Use pattern matching to build type-driven and data-driven algorithms.</span></span>

<span data-ttu-id="e53a5-104">C# 7 a introduit des fonctionnalités de critères spéciaux de base.</span><span class="sxs-lookup"><span data-stu-id="e53a5-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="e53a5-105">Ces fonctionnalités sont étendues en C# 8 et C# 9 avec de nouveaux modèles et expressions.</span><span class="sxs-lookup"><span data-stu-id="e53a5-105">Those features are extended in C# 8 and C# 9 with new expressions and patterns.</span></span> <span data-ttu-id="e53a5-106">Il est possible d’écrire des fonctionnalités qui se comportent comme si des types provenant potentiellement d’autres bibliothèques avaient été étendus.</span><span class="sxs-lookup"><span data-stu-id="e53a5-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="e53a5-107">Une autre utilisation des modèles consiste à créer des fonctionnalités requises par une application qui ne sont pas essentielles pour le type étendu.</span><span class="sxs-lookup"><span data-stu-id="e53a5-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="e53a5-108">Ce didacticiel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e53a5-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="e53a5-109">Reconnaître les situations dans lesquelles les critères spéciaux sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e53a5-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="e53a5-110">Utiliser des expressions de critères spéciaux pour implémenter des comportements en fonction des types et des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="e53a5-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="e53a5-111">Combiner des critères spéciaux avec d’autres techniques pour créer des algorithmes complets.</span><span class="sxs-lookup"><span data-stu-id="e53a5-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e53a5-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="e53a5-112">Prerequisites</span></span>

<span data-ttu-id="e53a5-113">Vous devez configurer votre ordinateur pour exécuter .NET 5, qui comprend le compilateur C# 9.</span><span class="sxs-lookup"><span data-stu-id="e53a5-113">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="e53a5-114">Le compilateur C# 9 est disponible à partir de [Visual Studio 2019 version 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) ou [.net 5,0 SDK](https://dot.net/get-dotnet5).</span><span class="sxs-lookup"><span data-stu-id="e53a5-114">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="e53a5-115">Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e53a5-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="e53a5-116">Scénarios des critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="e53a5-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="e53a5-117">Le développement moderne passe souvent par l’intégration de données provenant de plusieurs sources et par la présentation d’informations et d’insights tirés de ces données dans une seule et même application.</span><span class="sxs-lookup"><span data-stu-id="e53a5-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="e53a5-118">Ni vous ni votre équipe n’aurez accès aux types qui représentent les données entrantes ou ne pourrez les contrôler.</span><span class="sxs-lookup"><span data-stu-id="e53a5-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="e53a5-119">Une conception classique orientée objet exigerait de créer dans l’application des types représentant chacun des types de données de ces multiples sources.</span><span class="sxs-lookup"><span data-stu-id="e53a5-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="e53a5-120">L’application s’appuierait alors sur ces nouveaux types pour élaborer des hiérarchies d’héritage, créer des méthodes virtuelles et implémenter des abstractions.</span><span class="sxs-lookup"><span data-stu-id="e53a5-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="e53a5-121">Ces techniques fonctionnent et représentent parfois les meilleurs outils disponibles.</span><span class="sxs-lookup"><span data-stu-id="e53a5-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="e53a5-122">Il est possible dans d’autres cas d’écrire du code moins long</span><span class="sxs-lookup"><span data-stu-id="e53a5-122">Other times you can write less code.</span></span> <span data-ttu-id="e53a5-123">et plus clair, à l’aide de techniques qui séparent les données des opérations qui les manipulent.</span><span class="sxs-lookup"><span data-stu-id="e53a5-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="e53a5-124">Ce tutoriel vise à créer et à explorer une application qui prend en entrée des données provenant de plusieurs sources externes pour un seul scénario.</span><span class="sxs-lookup"><span data-stu-id="e53a5-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="e53a5-125">Nous verrons en quoi les **critères spéciaux** constituent un moyen efficace de consommer et de traiter ces données d’une autre manière que ce que prévoit le système d’origine.</span><span class="sxs-lookup"><span data-stu-id="e53a5-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="e53a5-126">Prenons une grande zone métropolitaine qui utilise des péages et des tarifs heures creuses/heures de pointe pour réguler le trafic.</span><span class="sxs-lookup"><span data-stu-id="e53a5-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="e53a5-127">Nous allons écrire une application qui calcule le péage en fonction du type de véhicule.</span><span class="sxs-lookup"><span data-stu-id="e53a5-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="e53a5-128">Lors d’améliorations ultérieures, nous intégrerons aux tarifs le nombre de passagers du véhicule</span><span class="sxs-lookup"><span data-stu-id="e53a5-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="e53a5-129">ainsi que l’heure et le jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="e53a5-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="e53a5-130">À partir de cette brève description, vous avez peut-être rapidement esquissé une hiérarchie d’objets pour modéliser ce système.</span><span class="sxs-lookup"><span data-stu-id="e53a5-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="e53a5-131">Cependant, les données proviennent de plusieurs sources, et notamment d’autres systèmes de gestion de l’immatriculation des véhicules.</span><span class="sxs-lookup"><span data-stu-id="e53a5-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="e53a5-132">Ils fournissent des classes différentes pour modéliser ces données, sans proposer de modèle objet unique.</span><span class="sxs-lookup"><span data-stu-id="e53a5-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="e53a5-133">Dans ce tutoriel, nous allons utiliser ces classes simplifiées pour modéliser les données sur les véhicules issues de ces systèmes externes, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="e53a5-134">Vous pouvez télécharger l’exemple de démarrage à partir du référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start).</span><span class="sxs-lookup"><span data-stu-id="e53a5-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="e53a5-135">Comme on peut le voir, les classes de véhicules proviennent de différents systèmes et utilisent différents espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="e53a5-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="e53a5-136">Aucune classe de base commune, autre que `System.Object`, n’est exploitable.</span><span class="sxs-lookup"><span data-stu-id="e53a5-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="e53a5-137">Conception avec les critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="e53a5-137">Pattern matching designs</span></span>

<span data-ttu-id="e53a5-138">Le scénario utilisé dans ce didacticiel met en évidence les types de problèmes que la correspondance de modèle est bien adaptée pour résoudre :</span><span class="sxs-lookup"><span data-stu-id="e53a5-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well suited to solve:</span></span>

- <span data-ttu-id="e53a5-139">Les objets dont vous avez besoin ne figurent pas dans une hiérarchie d’objets correspondant à vos objectifs.</span><span class="sxs-lookup"><span data-stu-id="e53a5-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="e53a5-140">Vous utilisez peut-être des classes faisant partie de systèmes non liés les uns aux autres.</span><span class="sxs-lookup"><span data-stu-id="e53a5-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="e53a5-141">Les fonctionnalités ajoutées ne font pas partie de l’abstraction de base de ces classes.</span><span class="sxs-lookup"><span data-stu-id="e53a5-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="e53a5-142">Le péage payé *change* selon les types de véhicules, mais il ne s’agit pas d’une fonction essentielle du véhicule.</span><span class="sxs-lookup"><span data-stu-id="e53a5-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="e53a5-143">Lorsque la *forme* des données et les *opérations* effectuées sur celles-ci ne sont pas décrites ensemble, les fonctionnalités de critères spéciaux de C# facilitent la tâche.</span><span class="sxs-lookup"><span data-stu-id="e53a5-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="e53a5-144">Implémenter les calculs de péage de base</span><span class="sxs-lookup"><span data-stu-id="e53a5-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="e53a5-145">Le calcul de péage le plus élémentaire s’appuie uniquement sur le type de véhicule :</span><span class="sxs-lookup"><span data-stu-id="e53a5-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="e53a5-146">`Car` : 2,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="e53a5-147">`Taxi` : 3,50 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="e53a5-148">`Bus` : 5,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="e53a5-149">`DeliveryTruck` : 10,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="e53a5-150">Créez une classe `TollCalculator` et implémentez les critères spéciaux sur le type de véhicule pour obtenir le montant du péage.</span><span class="sxs-lookup"><span data-stu-id="e53a5-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="e53a5-151">Le code suivant montre l’implémentation initiale de `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="e53a5-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    public class TollCalculator
    {
        public decimal CalculateToll(object vehicle) =>
            vehicle switch
        {
            Car c           => 2.00m,
            Taxi t          => 3.50m,
            Bus b           => 5.00m,
            DeliveryTruck t => 10.00m,
            { }             => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
            null            => throw new ArgumentNullException(nameof(vehicle))
        };
    }
}
```

<span data-ttu-id="e53a5-152">Le code précédent utilise une **expression switch** (différente d’une instruction [`switch`](../language-reference/keywords/switch.md)) qui teste le **modèle de type**.</span><span class="sxs-lookup"><span data-stu-id="e53a5-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="e53a5-153">Une **expression switch** commence par la variable, `vehicle` dans le code précédent, suivie du mot clé `switch`.</span><span class="sxs-lookup"><span data-stu-id="e53a5-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="e53a5-154">Viennent ensuite toutes les **branches switch** entre accolades.</span><span class="sxs-lookup"><span data-stu-id="e53a5-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="e53a5-155">L’expression `switch` ajoute d’autres perfectionnements à la syntaxe qui entoure l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="e53a5-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="e53a5-156">Le mot clé `case` est omis, et le résultat de chaque branche est une expression.</span><span class="sxs-lookup"><span data-stu-id="e53a5-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="e53a5-157">Les deux dernières montrent une nouvelle fonctionnalité du langage.</span><span class="sxs-lookup"><span data-stu-id="e53a5-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="e53a5-158">Le cas `{ }` représente n’importe quel objet non Null ne correspondant à aucune des branches antérieures.</span><span class="sxs-lookup"><span data-stu-id="e53a5-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="e53a5-159">Il intercepte tous les types incorrects passés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e53a5-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="e53a5-160">Le cas `{ }` doit suivre les cas de chaque type de véhicule.</span><span class="sxs-lookup"><span data-stu-id="e53a5-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="e53a5-161">Si l’ordre était inversé, le cas `{ }` serait prioritaire.</span><span class="sxs-lookup"><span data-stu-id="e53a5-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="e53a5-162">Enfin, le modèle `null` détecte si un `null` est passé à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="e53a5-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="e53a5-163">Le `null` modèle peut être en dernier, car les autres modèles de type correspondent uniquement à un objet non null du type correct.</span><span class="sxs-lookup"><span data-stu-id="e53a5-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="e53a5-164">Pour tester ce code, utilisez le code suivant dans `Program.cs` :</span><span class="sxs-lookup"><span data-stu-id="e53a5-164">You can test this code using the following code in `Program.cs`:</span></span>

```csharp
using System;
using CommercialRegistration;
using ConsumerVehicleRegistration;
using LiveryRegistration;

namespace toll_calculator
{
    class Program
    {
        static void Main(string[] args)
        {
            var tollCalc = new TollCalculator();

            var car = new Car();
            var taxi = new Taxi();
            var bus = new Bus();
            var truck = new DeliveryTruck();

            Console.WriteLine($"The toll for a car is {tollCalc.CalculateToll(car)}");
            Console.WriteLine($"The toll for a taxi is {tollCalc.CalculateToll(taxi)}");
            Console.WriteLine($"The toll for a bus is {tollCalc.CalculateToll(bus)}");
            Console.WriteLine($"The toll for a truck is {tollCalc.CalculateToll(truck)}");

            try
            {
                tollCalc.CalculateToll("this will fail");
            }
            catch (ArgumentException e)
            {
                Console.WriteLine("Caught an argument exception when using the wrong type");
            }
            try
            {
                tollCalc.CalculateToll(null!);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="e53a5-165">Ce code est inclus dans le projet de démarrage, mais il est commenté. Supprimez les commentaires et vous pouvez tester ce que vous avez écrit.</span><span class="sxs-lookup"><span data-stu-id="e53a5-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="e53a5-166">On commence à voir comment les modèles peuvent nous aider à créer des algorithmes dans lesquels le code et les données sont séparés.</span><span class="sxs-lookup"><span data-stu-id="e53a5-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="e53a5-167">L’ expression `switch` teste le type et produit différentes valeurs en fonction des résultats.</span><span class="sxs-lookup"><span data-stu-id="e53a5-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="e53a5-168">Ce n’est que le début.</span><span class="sxs-lookup"><span data-stu-id="e53a5-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="e53a5-169">Ajouter la tarification en fonction du taux d’occupation</span><span class="sxs-lookup"><span data-stu-id="e53a5-169">Add occupancy pricing</span></span>

<span data-ttu-id="e53a5-170">L’autorité de péage souhaite inciter les véhicules à circuler à capacité maximale.</span><span class="sxs-lookup"><span data-stu-id="e53a5-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="e53a5-171">Elle a décidé de fixer un tarif plus élevé pour les véhicules transportant peu de passagers et un prix inférieur pour les véhicules pleins, de façon à encourager ces derniers :</span><span class="sxs-lookup"><span data-stu-id="e53a5-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="e53a5-172">Voitures et taxis sans passager : +0,50 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="e53a5-173">Voitures et taxis avec deux passagers : remise de 0,50 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="e53a5-174">Voitures et taxis avec trois passagers ou plus : -1,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="e53a5-175">Bus remplis à moins de 50 % : +2,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="e53a5-176">Bus remplis à plus de 90 % : -1,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="e53a5-177">Il est possible d’implémenter ces règles avec le **modèle de propriété** dans la même expression switch.</span><span class="sxs-lookup"><span data-stu-id="e53a5-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="e53a5-178">Un modèle de propriété est une `when` clause qui compare une valeur de propriété à une valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="e53a5-178">A property pattern is a `when` clause that compares a property value to a constant value.</span></span> <span data-ttu-id="e53a5-179">Le modèle de propriété examine les propriétés de l’objet une fois que le type a été déterminé.</span><span class="sxs-lookup"><span data-stu-id="e53a5-179">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="e53a5-180">L’unique cas `Car` est étendu à quatre cas différents :</span><span class="sxs-lookup"><span data-stu-id="e53a5-180">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car {Passengers: 0}        => 2.00m + 0.50m,
    Car {Passengers: 1}        => 2.0m,
    Car {Passengers: 2}        => 2.0m - 0.50m,
    Car c                      => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="e53a5-181">Les trois premiers cas testent le type `Car`, puis vérifient la valeur de la propriété `Passengers`.</span><span class="sxs-lookup"><span data-stu-id="e53a5-181">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="e53a5-182">Si les deux correspondent, cette expression est évaluée et retournée.</span><span class="sxs-lookup"><span data-stu-id="e53a5-182">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="e53a5-183">Les cas des taxis sont étendus de la même manière :</span><span class="sxs-lookup"><span data-stu-id="e53a5-183">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi {Fares: 0}  => 3.50m + 1.00m,
    Taxi {Fares: 1}  => 3.50m,
    Taxi {Fares: 2}  => 3.50m - 0.50m,
    Taxi t           => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="e53a5-184">Dans l’exemple précédent, la clause `when` a été omise sur le cas final.</span><span class="sxs-lookup"><span data-stu-id="e53a5-184">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="e53a5-185">Maintenant, implémentons les règles de taux d’occupation en développant les cas des bus, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-185">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

```csharp
vehicle switch
{
    // ...

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    // ...
};
```

<span data-ttu-id="e53a5-186">L’autorité de péage ne se soucie pas du nombre de passagers des camions de livraison,</span><span class="sxs-lookup"><span data-stu-id="e53a5-186">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="e53a5-187">et ajuste le montant en fonction du poids du camion, en procédant ainsi :</span><span class="sxs-lookup"><span data-stu-id="e53a5-187">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="e53a5-188">Camions de plus de 5 000 lb : +5,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-188">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="e53a5-189">Camions de moins de 3000 lb : -2,00 $.</span><span class="sxs-lookup"><span data-stu-id="e53a5-189">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="e53a5-190">Cette règle est implémentée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-190">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="e53a5-191">Le code précédent montre la clause `when` d’une branche switch.</span><span class="sxs-lookup"><span data-stu-id="e53a5-191">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="e53a5-192">Cette clause `when` sert à tester les conditions autres que l’égalité sur une propriété.</span><span class="sxs-lookup"><span data-stu-id="e53a5-192">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="e53a5-193">Une fois que vous avez terminé, vous disposez d’une méthode qui ressemble au code suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-193">When you've finished, you'll have a method that looks much like the following code:</span></span>

```csharp
vehicle switch
{
    Car {Passengers: 0}        => 2.00m + 0.50m,
    Car {Passengers: 1}        => 2.0m,
    Car {Passengers: 2}        => 2.0m - 0.50m,
    Car c                      => 2.00m - 1.0m,

    Taxi {Fares: 0}  => 3.50m + 1.00m,
    Taxi {Fares: 1}  => 3.50m,
    Taxi {Fares: 2}  => 3.50m - 0.50m,
    Taxi t           => 3.50m - 1.00m,

    Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
    Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
    Bus b => 5.00m,

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,

    { }     => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
    null    => throw new ArgumentNullException(nameof(vehicle))
};
```

<span data-ttu-id="e53a5-194">La plupart de ces branches switch sont des exemples de **modèles récursifs**.</span><span class="sxs-lookup"><span data-stu-id="e53a5-194">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="e53a5-195">Par exemple, `Car { Passengers: 1}` indique un modèle de constante à l’intérieur d’un modèle de propriété.</span><span class="sxs-lookup"><span data-stu-id="e53a5-195">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="e53a5-196">Il est possible de rendre ce code moins répétitif avec des switch imbriqués.</span><span class="sxs-lookup"><span data-stu-id="e53a5-196">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="e53a5-197">Dans les exemples précédents, `Car` et `Taxi` ont chacun quatre branches différentes.</span><span class="sxs-lookup"><span data-stu-id="e53a5-197">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="e53a5-198">On peut créer dans les deux cas un modèle de type qui vient alimenter un modèle de propriété.</span><span class="sxs-lookup"><span data-stu-id="e53a5-198">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="e53a5-199">Cette technique est illustrée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-199">This technique is shown in the following code:</span></span>

```csharp
public decimal CalculateToll(object vehicle) =>
    vehicle switch
    {
        Car c => c.Passengers switch
        {
            0 => 2.00m + 0.5m,
            1 => 2.0m,
            2 => 2.0m - 0.5m,
            _ => 2.00m - 1.0m
        },

        Taxi t => t.Fares switch
        {
            0 => 3.50m + 1.00m,
            1 => 3.50m,
            2 => 3.50m - 0.50m,
            _ => 3.50m - 1.00m
        },

        Bus b when ((double)b.Riders / (double)b.Capacity) < 0.50 => 5.00m + 2.00m,
        Bus b when ((double)b.Riders / (double)b.Capacity) > 0.90 => 5.00m - 1.00m,
        Bus b => 5.00m,

        DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
        DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
        DeliveryTruck t => 10.00m,

        { }  => throw new ArgumentException(message: "Not a known vehicle type", paramName: nameof(vehicle)),
        null => throw new ArgumentNullException(nameof(vehicle))
    };
```

<span data-ttu-id="e53a5-200">Dans l’exemple précédent, l’expression récursive évite de répéter les branches `Car` et `Taxi` contenant des branches enfant qui testent la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="e53a5-200">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="e53a5-201">Cette technique n’est pas utilisée pour les branches `Bus` et `DeliveryTruck`, car elles correspondent à des plages de test pour la propriété, et non à des valeurs discrètes.</span><span class="sxs-lookup"><span data-stu-id="e53a5-201">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="e53a5-202">Ajouter la tarification heures creuses/heures de pointe</span><span class="sxs-lookup"><span data-stu-id="e53a5-202">Add peak pricing</span></span>

<span data-ttu-id="e53a5-203">En guise de fonctionnalité finale, l’autorité de péage souhaite ajouter une tarification soumise à une contrainte horaire.</span><span class="sxs-lookup"><span data-stu-id="e53a5-203">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="e53a5-204">Pendant les heures d’affluence du matin et du soir, les péages sont doublés.</span><span class="sxs-lookup"><span data-stu-id="e53a5-204">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="e53a5-205">Cette règle ne s’applique au trafic que dans un sens : en allant vers la ville le matin et en en sortant le soir.</span><span class="sxs-lookup"><span data-stu-id="e53a5-205">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="e53a5-206">Le reste du temps, pendant la journée de travail, les péages augmentent de 50 %.</span><span class="sxs-lookup"><span data-stu-id="e53a5-206">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="e53a5-207">Tard le soir et tôt le matin, ils sont réduits de 25 %.</span><span class="sxs-lookup"><span data-stu-id="e53a5-207">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="e53a5-208">Le taux normal s’applique le weekend, quelle que soit l’heure.</span><span class="sxs-lookup"><span data-stu-id="e53a5-208">During the weekend, it's the normal rate, regardless of the time.</span></span> <span data-ttu-id="e53a5-209">Vous pouvez utiliser une série si `if` les `else` instructions et permettent d’exprimer ce qui suit à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-209">You could use a series if `if` and `else` statements to express this using the following code:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#SnippetPremiumWithoutPattern)]

<span data-ttu-id="e53a5-210">Le code précédent fonctionne correctement, mais n’est pas lisible.</span><span class="sxs-lookup"><span data-stu-id="e53a5-210">The preceding code does work correctly, but isn't readable.</span></span> <span data-ttu-id="e53a5-211">Vous devez chaîner tous les cas d’entrée et les instructions imbriquées `if` pour la raison du code.</span><span class="sxs-lookup"><span data-stu-id="e53a5-211">You have to chain through all the input cases and the nested `if` statements to reason about the code.</span></span> <span data-ttu-id="e53a5-212">Au lieu de cela, vous allez utiliser des critères spéciaux pour cette fonctionnalité, mais vous allez l’intégrer à d’autres techniques.</span><span class="sxs-lookup"><span data-stu-id="e53a5-212">Instead, you'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="e53a5-213">Vous pourriez élaborer une seule expression de critères spéciaux qui tiendrait compte de toutes les combinaisons direction/jour de la semaine/heure.</span><span class="sxs-lookup"><span data-stu-id="e53a5-213">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="e53a5-214">Elle serait cependant complexe,</span><span class="sxs-lookup"><span data-stu-id="e53a5-214">The result would be a complicated expression.</span></span> <span data-ttu-id="e53a5-215">difficile à lire, à comprendre</span><span class="sxs-lookup"><span data-stu-id="e53a5-215">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="e53a5-216">et à vérifier.</span><span class="sxs-lookup"><span data-stu-id="e53a5-216">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="e53a5-217">Combinons plutôt ces méthodes afin de créer un tuple de valeurs décrivant de manière concise tous ces états.</span><span class="sxs-lookup"><span data-stu-id="e53a5-217">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="e53a5-218">Ensuite, utilisons les critères spéciaux pour calculer un multiplicateur de péage.</span><span class="sxs-lookup"><span data-stu-id="e53a5-218">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="e53a5-219">Le tuple comporte trois conditions discrètes :</span><span class="sxs-lookup"><span data-stu-id="e53a5-219">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="e53a5-220">le jour : semaine / weekend ;</span><span class="sxs-lookup"><span data-stu-id="e53a5-220">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="e53a5-221">la tranche horaire ;</span><span class="sxs-lookup"><span data-stu-id="e53a5-221">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="e53a5-222">la direction : vers l’intérieur ou l’extérieur de la ville.</span><span class="sxs-lookup"><span data-stu-id="e53a5-222">The direction is into the city or out of the city</span></span>

<span data-ttu-id="e53a5-223">Le tableau suivant montre les combinaisons de valeurs d’entrée et le multiplicateur tarifaire :</span><span class="sxs-lookup"><span data-stu-id="e53a5-223">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="e53a5-224">Jour</span><span class="sxs-lookup"><span data-stu-id="e53a5-224">Day</span></span>        | <span data-ttu-id="e53a5-225">Temps</span><span class="sxs-lookup"><span data-stu-id="e53a5-225">Time</span></span>         | <span data-ttu-id="e53a5-226">Sens</span><span class="sxs-lookup"><span data-stu-id="e53a5-226">Direction</span></span> | <span data-ttu-id="e53a5-227">Premium</span><span class="sxs-lookup"><span data-stu-id="e53a5-227">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="e53a5-228">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-228">Weekday</span></span>    | <span data-ttu-id="e53a5-229">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="e53a5-229">morning rush</span></span> | <span data-ttu-id="e53a5-230">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-230">inbound</span></span>   | <span data-ttu-id="e53a5-231">x 2,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-231">x 2.00</span></span>  |
| <span data-ttu-id="e53a5-232">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-232">Weekday</span></span>    | <span data-ttu-id="e53a5-233">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="e53a5-233">morning rush</span></span> | <span data-ttu-id="e53a5-234">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-234">outbound</span></span>  | <span data-ttu-id="e53a5-235">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-235">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-236">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-236">Weekday</span></span>    | <span data-ttu-id="e53a5-237">Journée</span><span class="sxs-lookup"><span data-stu-id="e53a5-237">daytime</span></span>      | <span data-ttu-id="e53a5-238">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-238">inbound</span></span>   | <span data-ttu-id="e53a5-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="e53a5-239">x 1.50</span></span>  |
| <span data-ttu-id="e53a5-240">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-240">Weekday</span></span>    | <span data-ttu-id="e53a5-241">Journée</span><span class="sxs-lookup"><span data-stu-id="e53a5-241">daytime</span></span>      | <span data-ttu-id="e53a5-242">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-242">outbound</span></span>  | <span data-ttu-id="e53a5-243">x 1,50</span><span class="sxs-lookup"><span data-stu-id="e53a5-243">x 1.50</span></span>  |
| <span data-ttu-id="e53a5-244">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-244">Weekday</span></span>    | <span data-ttu-id="e53a5-245">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="e53a5-245">evening rush</span></span> | <span data-ttu-id="e53a5-246">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-246">inbound</span></span>   | <span data-ttu-id="e53a5-247">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-247">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-248">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-248">Weekday</span></span>    | <span data-ttu-id="e53a5-249">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="e53a5-249">evening rush</span></span> | <span data-ttu-id="e53a5-250">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-250">outbound</span></span>  | <span data-ttu-id="e53a5-251">x 2,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-251">x 2.00</span></span>  |
| <span data-ttu-id="e53a5-252">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-252">Weekday</span></span>    | <span data-ttu-id="e53a5-253">Nuit</span><span class="sxs-lookup"><span data-stu-id="e53a5-253">overnight</span></span>    | <span data-ttu-id="e53a5-254">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-254">inbound</span></span>   | <span data-ttu-id="e53a5-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="e53a5-255">x 0.75</span></span>  |
| <span data-ttu-id="e53a5-256">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="e53a5-256">Weekday</span></span>    | <span data-ttu-id="e53a5-257">Nuit</span><span class="sxs-lookup"><span data-stu-id="e53a5-257">overnight</span></span>    | <span data-ttu-id="e53a5-258">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-258">outbound</span></span>  | <span data-ttu-id="e53a5-259">x 0,75</span><span class="sxs-lookup"><span data-stu-id="e53a5-259">x 0.75</span></span>  |
| <span data-ttu-id="e53a5-260">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-260">Weekend</span></span>    | <span data-ttu-id="e53a5-261">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="e53a5-261">morning rush</span></span> | <span data-ttu-id="e53a5-262">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-262">inbound</span></span>   | <span data-ttu-id="e53a5-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-263">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-264">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-264">Weekend</span></span>    | <span data-ttu-id="e53a5-265">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="e53a5-265">morning rush</span></span> | <span data-ttu-id="e53a5-266">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-266">outbound</span></span>  | <span data-ttu-id="e53a5-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-267">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-268">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-268">Weekend</span></span>    | <span data-ttu-id="e53a5-269">Journée</span><span class="sxs-lookup"><span data-stu-id="e53a5-269">daytime</span></span>      | <span data-ttu-id="e53a5-270">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-270">inbound</span></span>   | <span data-ttu-id="e53a5-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-271">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-272">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-272">Weekend</span></span>    | <span data-ttu-id="e53a5-273">Journée</span><span class="sxs-lookup"><span data-stu-id="e53a5-273">daytime</span></span>      | <span data-ttu-id="e53a5-274">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-274">outbound</span></span>  | <span data-ttu-id="e53a5-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-275">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-276">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-276">Weekend</span></span>    | <span data-ttu-id="e53a5-277">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="e53a5-277">evening rush</span></span> | <span data-ttu-id="e53a5-278">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-278">inbound</span></span>   | <span data-ttu-id="e53a5-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-279">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-280">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-280">Weekend</span></span>    | <span data-ttu-id="e53a5-281">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="e53a5-281">evening rush</span></span> | <span data-ttu-id="e53a5-282">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-282">outbound</span></span>  | <span data-ttu-id="e53a5-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-283">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-284">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-284">Weekend</span></span>    | <span data-ttu-id="e53a5-285">Nuit</span><span class="sxs-lookup"><span data-stu-id="e53a5-285">overnight</span></span>    | <span data-ttu-id="e53a5-286">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-286">inbound</span></span>   | <span data-ttu-id="e53a5-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-287">x 1.00</span></span>  |
| <span data-ttu-id="e53a5-288">Week-end</span><span class="sxs-lookup"><span data-stu-id="e53a5-288">Weekend</span></span>    | <span data-ttu-id="e53a5-289">Nuit</span><span class="sxs-lookup"><span data-stu-id="e53a5-289">overnight</span></span>    | <span data-ttu-id="e53a5-290">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="e53a5-290">outbound</span></span>  | <span data-ttu-id="e53a5-291">x 1,00</span><span class="sxs-lookup"><span data-stu-id="e53a5-291">x 1.00</span></span>  |

<span data-ttu-id="e53a5-292">Les trois variables produisent 16 combinaisons différentes.</span><span class="sxs-lookup"><span data-stu-id="e53a5-292">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="e53a5-293">On peut simplifier l’expression switch finale en associant certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="e53a5-293">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="e53a5-294">Le système qui collecte les péages utilise une structure <xref:System.DateTime> pour indiquer l’heure de collecte.</span><span class="sxs-lookup"><span data-stu-id="e53a5-294">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="e53a5-295">Élaborons les méthodes de membre qui créent des variables à partir du tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="e53a5-295">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="e53a5-296">La fonction suivante utilise une expression switch de critères spéciaux pour exprimer si <xref:System.DateTime> représente un jour de weekend ou de semaine :</span><span class="sxs-lookup"><span data-stu-id="e53a5-296">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

```csharp
private static bool IsWeekDay(DateTime timeOfToll) =>
    timeOfToll.DayOfWeek switch
    {
        DayOfWeek.Monday    => true,
        DayOfWeek.Tuesday   => true,
        DayOfWeek.Wednesday => true,
        DayOfWeek.Thursday  => true,
        DayOfWeek.Friday    => true,
        DayOfWeek.Saturday  => false,
        DayOfWeek.Sunday    => false
    };
```

<span data-ttu-id="e53a5-297">Cette méthode est correcte, mais elle est répétitive.</span><span class="sxs-lookup"><span data-stu-id="e53a5-297">That method is correct, but it's repetitious.</span></span> <span data-ttu-id="e53a5-298">On peut la simplifier comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e53a5-298">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="e53a5-299">Ensuite, ajoutons une fonction similaire pour catégoriser l’heure dans les blocs :</span><span class="sxs-lookup"><span data-stu-id="e53a5-299">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="e53a5-300">Vous ajoutez un privé `enum` pour convertir chaque plage horaire en valeur discrète.</span><span class="sxs-lookup"><span data-stu-id="e53a5-300">You add a private `enum` to convert each range of time to a discrete value.</span></span> <span data-ttu-id="e53a5-301">Ensuite, la `GetTimeBand` méthode utilise des *modèles relationnels*, et des *conjonctives ou des modèles*, tous deux ajoutés en C# 9,0.</span><span class="sxs-lookup"><span data-stu-id="e53a5-301">Then, the `GetTimeBand` method uses *relational patterns*, and *conjunctive or patterns*, both added in C# 9.0.</span></span> <span data-ttu-id="e53a5-302">Le modèle relationnel vous permet de tester une valeur numérique à l’aide `<` de,, `>` `<=` ou `>=` .</span><span class="sxs-lookup"><span data-stu-id="e53a5-302">The relational pattern lets you test a numeric value using `<`, `>`, `<=`, or `>=`.</span></span> <span data-ttu-id="e53a5-303">Le `or` modèle teste si une expression correspond à un ou plusieurs modèles.</span><span class="sxs-lookup"><span data-stu-id="e53a5-303">The `or` pattern tests if an expression matches one or more patterns.</span></span> <span data-ttu-id="e53a5-304">Vous pouvez également utiliser un `and` modèle pour vous assurer qu’une expression correspond à deux modèles distincts et un `not` modèle pour vérifier qu’une expression ne correspond pas à un modèle.</span><span class="sxs-lookup"><span data-stu-id="e53a5-304">You can also use an `and` pattern to ensure that an expression matches two distinct patterns, and a `not` pattern to test that an expression doesn't match a pattern.</span></span>

<span data-ttu-id="e53a5-305">Maintenant que nous avons créé ces méthodes, utilisons une autre expression `switch` avec le **modèle de tuple** pour calculer le multiplicateur tarifaire.</span><span class="sxs-lookup"><span data-stu-id="e53a5-305">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="e53a5-306">On pourrait concevoir une expression `switch` comportant les 16 branches :</span><span class="sxs-lookup"><span data-stu-id="e53a5-306">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="e53a5-307">Le code ci-dessus fonctionne, mais on peut le simplifier.</span><span class="sxs-lookup"><span data-stu-id="e53a5-307">The above code works, but it can be simplified.</span></span> <span data-ttu-id="e53a5-308">Les huit combinaisons du weekend correspondent au même péage.</span><span class="sxs-lookup"><span data-stu-id="e53a5-308">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="e53a5-309">Elles sont remplaçables par la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="e53a5-309">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="e53a5-310">Le trafic entrant et le trafic sortant ont le même multiplicateur pendant la journée en semaine et pendant la nuit.</span><span class="sxs-lookup"><span data-stu-id="e53a5-310">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="e53a5-311">Ces quatre branches switch peuvent être remplacées par les deux lignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e53a5-311">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="e53a5-312">Après ces deux modifications, le code devrait se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="e53a5-312">The code should look like the following code after those two changes:</span></span>

```csharp
public decimal PeakTimePremium(DateTime timeOfToll, bool inbound) =>
    (IsWeekDay(timeOfToll), GetTimeBand(timeOfToll), inbound) switch
    {
        (true, TimeBand.MorningRush, true)  => 2.00m,
        (true, TimeBand.MorningRush, false) => 1.00m,
        (true, TimeBand.Daytime,     _)     => 1.50m,
        (true, TimeBand.EveningRush, true)  => 1.00m,
        (true, TimeBand.EveningRush, false) => 2.00m,
        (true, TimeBand.Overnight,   _)     => 0.75m,
        (false, _,                   _)     => 1.00m,
    };
```

<span data-ttu-id="e53a5-313">Enfin, on peut supprimer les deux branches des heures de pointe au tarif normal,</span><span class="sxs-lookup"><span data-stu-id="e53a5-313">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="e53a5-314">ce qui permet de remplacer `false` par un discard (`_`) dans la branche switch finale.</span><span class="sxs-lookup"><span data-stu-id="e53a5-314">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="e53a5-315">On obtient la méthode suivante une fois terminée :</span><span class="sxs-lookup"><span data-stu-id="e53a5-315">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="e53a5-316">Cet exemple met en évidence un des avantages des critères spéciaux : les branches du modèle sont évaluées dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="e53a5-316">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="e53a5-317">Si vous les réorganisez de telle sorte qu’une branche antérieure gère un des cas suivants, le compilateur vous avertit que le code est inaccessible.</span><span class="sxs-lookup"><span data-stu-id="e53a5-317">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="e53a5-318">Grâce à ces règles de langage, nous avons pu effectuer facilement les simplifications précédentes sans craindre de modifier le code.</span><span class="sxs-lookup"><span data-stu-id="e53a5-318">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="e53a5-319">Les critères spéciaux rendent certains types de code plus lisibles et offrent une alternative aux techniques orientées objet quand vous ne pouvez pas ajouter de code à vos classes.</span><span class="sxs-lookup"><span data-stu-id="e53a5-319">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="e53a5-320">Le cloud est à l’origine d’une séparation entre les données et les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e53a5-320">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="e53a5-321">La *forme* des données et les *opérations* effectuées sur ces dernières ne sont pas nécessairement décrites ensemble.</span><span class="sxs-lookup"><span data-stu-id="e53a5-321">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="e53a5-322">Dans ce tutoriel, nous avons exploité les données existantes d’une manière totalement différente de leur fonction d’origine.</span><span class="sxs-lookup"><span data-stu-id="e53a5-322">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="e53a5-323">Les critères spéciaux offrent la possibilité d’écrire des fonctionnalités qui remplacent ces types, même sans pouvoir les étendre.</span><span class="sxs-lookup"><span data-stu-id="e53a5-323">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e53a5-324">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e53a5-324">Next steps</span></span>

<span data-ttu-id="e53a5-325">Vous pouvez télécharger le code terminé dans référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished).</span><span class="sxs-lookup"><span data-stu-id="e53a5-325">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="e53a5-326">Explorez les modèles par vous-même et ajoutez cette technique à vos activités de codage régulières.</span><span class="sxs-lookup"><span data-stu-id="e53a5-326">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="e53a5-327">Ces techniques représentent une autre façon d’aborder les problèmes et de créer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="e53a5-327">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
