---
title: 'Didacticiel : générer des algorithmes avec des critères spéciaux'
description: Ce tutoriel avancé montre comment utiliser des techniques de critères spéciaux pour créer des fonctionnalités à l’aide de données et d’algorithmes créés séparément.
ms.date: 03/13/2019
ms.technology: csharp-whats-new
ms.custom: contperfq1
ms.openlocfilehash: 9fff9f286bd0aa7baf7632f9144dfe693bab0c32
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91437989"
---
# <a name="tutorial-use-pattern-matching-to-build-type-driven-and-data-driven-algorithms"></a><span data-ttu-id="fa7d0-103">Didacticiel : utiliser des critères spéciaux pour générer des algorithmes pilotés par type et pilotés par les données.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-103">Tutorial: Use pattern matching to build type-driven and data-driven algorithms.</span></span>

<span data-ttu-id="fa7d0-104">C# 7 a introduit des fonctionnalités de critères spéciaux de base.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-104">C# 7 introduced basic pattern matching features.</span></span> <span data-ttu-id="fa7d0-105">Elles ont été étendues dans C# 8 par de nouvelles expressions et de nouveaux modèles.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-105">Those features are extended in C# 8 with new expressions and patterns.</span></span> <span data-ttu-id="fa7d0-106">Il est possible d’écrire des fonctionnalités qui se comportent comme si des types provenant potentiellement d’autres bibliothèques avaient été étendus.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-106">You can write functionality that behaves as though you extended types that may be in other libraries.</span></span> <span data-ttu-id="fa7d0-107">Une autre utilisation des modèles consiste à créer des fonctionnalités requises par une application qui ne sont pas essentielles pour le type étendu.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-107">Another use for patterns is to create functionality your application requires that isn't a fundamental feature of the type being extended.</span></span>

<span data-ttu-id="fa7d0-108">Ce didacticiel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-108">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="fa7d0-109">Reconnaître les situations dans lesquelles les critères spéciaux sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-109">Recognize situations where pattern matching should be used.</span></span>
> - <span data-ttu-id="fa7d0-110">Utiliser des expressions de critères spéciaux pour implémenter des comportements en fonction des types et des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-110">Use pattern matching expressions to implement behavior based on types and property values.</span></span>
> - <span data-ttu-id="fa7d0-111">Combiner des critères spéciaux avec d’autres techniques pour créer des algorithmes complets.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-111">Combine pattern matching with other techniques to create complete algorithms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fa7d0-112">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="fa7d0-112">Prerequisites</span></span>

<span data-ttu-id="fa7d0-113">Vous devez configurer votre ordinateur pour exécuter .NET Core, y compris le compilateur C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-113">You’ll need to set up your machine to run .NET Core, including the C# 8.0 compiler.</span></span> <span data-ttu-id="fa7d0-114">Le compilateur C# 8 est disponible à partir de [Visual Studio 2019 version 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou du [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="fa7d0-114">The C# 8 compiler is available starting with [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).</span></span>

<span data-ttu-id="fa7d0-115">Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-115">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="scenarios-for-pattern-matching"></a><span data-ttu-id="fa7d0-116">Scénarios des critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="fa7d0-116">Scenarios for pattern matching</span></span>

<span data-ttu-id="fa7d0-117">Le développement moderne passe souvent par l’intégration de données provenant de plusieurs sources et par la présentation d’informations et d’insights tirés de ces données dans une seule et même application.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-117">Modern development often includes integrating data from multiple sources and presenting information and insights from that data in a single cohesive application.</span></span> <span data-ttu-id="fa7d0-118">Ni vous ni votre équipe n’aurez accès aux types qui représentent les données entrantes ou ne pourrez les contrôler.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-118">You and your team won't have control or access for all the types that represent the incoming data.</span></span>

<span data-ttu-id="fa7d0-119">Une conception classique orientée objet exigerait de créer dans l’application des types représentant chacun des types de données de ces multiples sources.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-119">The classic object-oriented design would call for creating types in your application that represent each data type from those multiple data sources.</span></span> <span data-ttu-id="fa7d0-120">L’application s’appuierait alors sur ces nouveaux types pour élaborer des hiérarchies d’héritage, créer des méthodes virtuelles et implémenter des abstractions.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-120">Then, your application would work with those new types, build inheritance hierarchies, create virtual methods, and implement abstractions.</span></span> <span data-ttu-id="fa7d0-121">Ces techniques fonctionnent et représentent parfois les meilleurs outils disponibles.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-121">Those techniques work, and sometimes they are the best tools.</span></span> <span data-ttu-id="fa7d0-122">Il est possible dans d’autres cas d’écrire du code moins long</span><span class="sxs-lookup"><span data-stu-id="fa7d0-122">Other times you can write less code.</span></span> <span data-ttu-id="fa7d0-123">et plus clair, à l’aide de techniques qui séparent les données des opérations qui les manipulent.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-123">You can write more clear code using techniques that separate the data from the operations that manipulate that data.</span></span>

<span data-ttu-id="fa7d0-124">Ce tutoriel vise à créer et à explorer une application qui prend en entrée des données provenant de plusieurs sources externes pour un seul scénario.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-124">In this tutorial, you'll create and explore an application that takes incoming data from several external sources for a single scenario.</span></span> <span data-ttu-id="fa7d0-125">Nous verrons en quoi les **critères spéciaux** constituent un moyen efficace de consommer et de traiter ces données d’une autre manière que ce que prévoit le système d’origine.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-125">You'll see how **pattern matching** provides an efficient way to consume and process that data in ways that weren't part of the original system.</span></span>

<span data-ttu-id="fa7d0-126">Prenons une grande zone métropolitaine qui utilise des péages et des tarifs heures creuses/heures de pointe pour réguler le trafic.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-126">Consider a major metropolitan area that is using tolls and peak time pricing to manage traffic.</span></span> <span data-ttu-id="fa7d0-127">Nous allons écrire une application qui calcule le péage en fonction du type de véhicule.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-127">You write an application that calculates tolls for a vehicle based on its type.</span></span> <span data-ttu-id="fa7d0-128">Lors d’améliorations ultérieures, nous intégrerons aux tarifs le nombre de passagers du véhicule</span><span class="sxs-lookup"><span data-stu-id="fa7d0-128">Later enhancements incorporate pricing based on the number of occupants in the vehicle.</span></span> <span data-ttu-id="fa7d0-129">ainsi que l’heure et le jour de la semaine.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-129">Further enhancements add pricing based on the time and the day of the week.</span></span>

<span data-ttu-id="fa7d0-130">À partir de cette brève description, vous avez peut-être rapidement esquissé une hiérarchie d’objets pour modéliser ce système.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-130">From that brief description, you may have quickly sketched out an object hierarchy to model this system.</span></span> <span data-ttu-id="fa7d0-131">Cependant, les données proviennent de plusieurs sources, et notamment d’autres systèmes de gestion de l’immatriculation des véhicules.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-131">However, your data is coming from multiple sources like other vehicle registration management systems.</span></span> <span data-ttu-id="fa7d0-132">Ils fournissent des classes différentes pour modéliser ces données, sans proposer de modèle objet unique.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-132">These systems provide different classes to model that data and you don't have a single object model you can use.</span></span> <span data-ttu-id="fa7d0-133">Dans ce tutoriel, nous allons utiliser ces classes simplifiées pour modéliser les données sur les véhicules issues de ces systèmes externes, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-133">In this tutorial, you'll use these simplified classes to model for the vehicle data from these external systems, as shown in the following code:</span></span>

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

<span data-ttu-id="fa7d0-134">Vous pouvez télécharger l’exemple de démarrage à partir du référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start).</span><span class="sxs-lookup"><span data-stu-id="fa7d0-134">You can download the starter code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start) GitHub repository.</span></span> <span data-ttu-id="fa7d0-135">Comme on peut le voir, les classes de véhicules proviennent de différents systèmes et utilisent différents espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-135">You can see that the vehicle classes are from different systems, and are in different namespaces.</span></span> <span data-ttu-id="fa7d0-136">Aucune classe de base commune, autre que `System.Object`, n’est exploitable.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-136">No common base class, other than `System.Object` can be leveraged.</span></span>

## <a name="pattern-matching-designs"></a><span data-ttu-id="fa7d0-137">Conception avec les critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="fa7d0-137">Pattern matching designs</span></span>

<span data-ttu-id="fa7d0-138">Le scénario utilisé dans ce tutoriel met en évidence les types de problèmes que les critères spéciaux peuvent parfaitement résoudre :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-138">The scenario used in this tutorial highlights the kinds of problems that pattern matching is well-suited to solve:</span></span>

- <span data-ttu-id="fa7d0-139">Les objets dont vous avez besoin ne figurent pas dans une hiérarchie d’objets correspondant à vos objectifs.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-139">The objects you need to work with aren't in an object hierarchy that matches your goals.</span></span> <span data-ttu-id="fa7d0-140">Vous utilisez peut-être des classes faisant partie de systèmes non liés les uns aux autres.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-140">You may be working with classes that are part of unrelated systems.</span></span>
- <span data-ttu-id="fa7d0-141">Les fonctionnalités ajoutées ne font pas partie de l’abstraction de base de ces classes.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-141">The functionality you're adding isn't part of the core abstraction for these classes.</span></span> <span data-ttu-id="fa7d0-142">Le péage payé *change* selon les types de véhicules, mais il ne s’agit pas d’une fonction essentielle du véhicule.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-142">The toll paid by a vehicle *changes* for different types of vehicles, but the toll isn't a core function of the vehicle.</span></span>

<span data-ttu-id="fa7d0-143">Lorsque la *forme* des données et les *opérations* effectuées sur celles-ci ne sont pas décrites ensemble, les fonctionnalités de critères spéciaux de C# facilitent la tâche.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-143">When the *shape* of the data and the *operations* on that data are not described together, the pattern matching features in C# make it easier to work with.</span></span>

## <a name="implement-the-basic-toll-calculations"></a><span data-ttu-id="fa7d0-144">Implémenter les calculs de péage de base</span><span class="sxs-lookup"><span data-stu-id="fa7d0-144">Implement the basic toll calculations</span></span>

<span data-ttu-id="fa7d0-145">Le calcul de péage le plus élémentaire s’appuie uniquement sur le type de véhicule :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-145">The most basic toll calculation relies only on the vehicle type:</span></span>

- <span data-ttu-id="fa7d0-146">`Car` : 2,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-146">A `Car` is $2.00.</span></span>
- <span data-ttu-id="fa7d0-147">`Taxi` : 3,50 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-147">A `Taxi` is $3.50.</span></span>
- <span data-ttu-id="fa7d0-148">`Bus` : 5,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-148">A `Bus` is $5.00.</span></span>
- <span data-ttu-id="fa7d0-149">`DeliveryTruck` : 10,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-149">A `DeliveryTruck` is $10.00</span></span>

<span data-ttu-id="fa7d0-150">Créez une classe `TollCalculator` et implémentez les critères spéciaux sur le type de véhicule pour obtenir le montant du péage.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-150">Create a new `TollCalculator` class, and implement pattern matching on the vehicle type to get the toll amount.</span></span> <span data-ttu-id="fa7d0-151">Le code suivant montre l’implémentation initiale de `TollCalculator`.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-151">The following code shows the initial implementation of the `TollCalculator`.</span></span>

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

<span data-ttu-id="fa7d0-152">Le code précédent utilise une **expression switch** (différente d’une instruction [`switch`](../language-reference/keywords/switch.md)) qui teste le **modèle de type**.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-152">The preceding code uses a **switch expression** (not the same as a [`switch`](../language-reference/keywords/switch.md) statement) that tests the **type pattern**.</span></span> <span data-ttu-id="fa7d0-153">Une **expression switch** commence par la variable, `vehicle` dans le code précédent, suivie du mot clé `switch`.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-153">A **switch expression** begins with the variable, `vehicle` in the preceding code, followed by the `switch` keyword.</span></span> <span data-ttu-id="fa7d0-154">Viennent ensuite toutes les **branches switch** entre accolades.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-154">Next comes all the **switch arms** inside curly braces.</span></span> <span data-ttu-id="fa7d0-155">L’expression `switch` ajoute d’autres perfectionnements à la syntaxe qui entoure l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-155">The `switch` expression makes other refinements to the syntax that surrounds the `switch` statement.</span></span> <span data-ttu-id="fa7d0-156">Le mot clé `case` est omis, et le résultat de chaque branche est une expression.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-156">The `case` keyword is omitted, and the result of each arm is an expression.</span></span> <span data-ttu-id="fa7d0-157">Les deux dernières montrent une nouvelle fonctionnalité du langage.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-157">The last two arms show a new language feature.</span></span> <span data-ttu-id="fa7d0-158">Le cas `{ }` représente n’importe quel objet non Null ne correspondant à aucune des branches antérieures.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-158">The `{ }` case matches any non-null object that didn't match an earlier arm.</span></span> <span data-ttu-id="fa7d0-159">Il intercepte tous les types incorrects passés à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-159">This arm catches any incorrect types passed to this method.</span></span>  <span data-ttu-id="fa7d0-160">Le cas `{ }` doit suivre les cas de chaque type de véhicule.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-160">The `{ }` case must follow the cases for each vehicle type.</span></span> <span data-ttu-id="fa7d0-161">Si l’ordre était inversé, le cas `{ }` serait prioritaire.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-161">If the order were reversed, the `{ }` case would take precedence.</span></span> <span data-ttu-id="fa7d0-162">Enfin, le modèle `null` détecte si un `null` est passé à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-162">Finally, the `null` pattern detects when a `null` is passed to this method.</span></span> <span data-ttu-id="fa7d0-163">Le `null` modèle peut être en dernier, car les autres modèles de type correspondent uniquement à un objet non null du type correct.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-163">The `null` pattern can be last because the other type patterns match only a non-null object of the correct type.</span></span>

<span data-ttu-id="fa7d0-164">Pour tester ce code, utilisez le code suivant dans `Program.cs` :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-164">You can test this code using the following code in `Program.cs`:</span></span>

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
                tollCalc.CalculateToll(null);
            }
            catch (ArgumentNullException e)
            {
                Console.WriteLine("Caught an argument exception when using null");
            }
        }
    }
}
```

<span data-ttu-id="fa7d0-165">Ce code est inclus dans le projet de démarrage, mais il est commenté. Supprimez les commentaires et vous pouvez tester ce que vous avez écrit.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-165">That code is included in the starter project, but is commented out. Remove the comments, and you can test what you've written.</span></span>

<span data-ttu-id="fa7d0-166">On commence à voir comment les modèles peuvent nous aider à créer des algorithmes dans lesquels le code et les données sont séparés.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-166">You're starting to see how patterns can help you create algorithms where the code and the data are separate.</span></span> <span data-ttu-id="fa7d0-167">L’ expression `switch` teste le type et produit différentes valeurs en fonction des résultats.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-167">The `switch` expression tests the type and produces different values based on the results.</span></span> <span data-ttu-id="fa7d0-168">Ce n’est que le début.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-168">That's only the beginning.</span></span>

## <a name="add-occupancy-pricing"></a><span data-ttu-id="fa7d0-169">Ajouter la tarification en fonction du taux d’occupation</span><span class="sxs-lookup"><span data-stu-id="fa7d0-169">Add occupancy pricing</span></span>

<span data-ttu-id="fa7d0-170">L’autorité de péage souhaite inciter les véhicules à circuler à capacité maximale.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-170">The toll authority wants to encourage vehicles to travel at maximum capacity.</span></span> <span data-ttu-id="fa7d0-171">Elle a décidé de fixer un tarif plus élevé pour les véhicules transportant peu de passagers et un prix inférieur pour les véhicules pleins, de façon à encourager ces derniers :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-171">They've decided to charge more when vehicles have fewer passengers, and encourage full vehicles by offering lower pricing:</span></span>

- <span data-ttu-id="fa7d0-172">Voitures et taxis sans passager : +0,50 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-172">Cars and taxis with no passengers pay an extra $0.50.</span></span>
- <span data-ttu-id="fa7d0-173">Voitures et taxis avec deux passagers : remise de 0,50 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-173">Cars and taxis with two passengers get a $0.50 discount.</span></span>
- <span data-ttu-id="fa7d0-174">Voitures et taxis avec trois passagers ou plus : -1,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-174">Cars and taxis with three or more passengers get a $1.00 discount.</span></span>
- <span data-ttu-id="fa7d0-175">Bus remplis à moins de 50 % : +2,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-175">Buses that are less than 50% full pay an extra $2.00.</span></span>
- <span data-ttu-id="fa7d0-176">Bus remplis à plus de 90 % : -1,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-176">Buses that are more than 90% full get a $1.00 discount.</span></span>

<span data-ttu-id="fa7d0-177">Il est possible d’implémenter ces règles avec le **modèle de propriété** dans la même expression switch.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-177">These rules can be implemented using the **property pattern** in the same switch expression.</span></span> <span data-ttu-id="fa7d0-178">Le modèle de propriété examine les propriétés de l’objet une fois que le type a été déterminé.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-178">The property pattern examines properties of the object once the type has been determined.</span></span> <span data-ttu-id="fa7d0-179">L’unique cas `Car` est étendu à quatre cas différents :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-179">The single case for a `Car` expands to four different cases:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1 }       => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    // ...
};
```

<span data-ttu-id="fa7d0-180">Les trois premiers cas testent le type `Car`, puis vérifient la valeur de la propriété `Passengers`.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-180">The first three cases test the type as a `Car`, then check the value of the `Passengers` property.</span></span> <span data-ttu-id="fa7d0-181">Si les deux correspondent, cette expression est évaluée et retournée.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-181">If both match, that expression is evaluated and returned.</span></span>

<span data-ttu-id="fa7d0-182">Les cas des taxis sont étendus de la même manière :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-182">You would also expand the cases for taxis in a similar manner:</span></span>

```csharp
vehicle switch
{
    // ...

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

    // ...
};
```

<span data-ttu-id="fa7d0-183">Dans l’exemple précédent, la clause `when` a été omise sur le cas final.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-183">In the preceding example, the `when` clause was omitted on the final case.</span></span>

<span data-ttu-id="fa7d0-184">Maintenant, implémentons les règles de taux d’occupation en développant les cas des bus, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-184">Next, implement the occupancy rules by expanding the cases for buses, as shown in the following example:</span></span>

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

<span data-ttu-id="fa7d0-185">L’autorité de péage ne se soucie pas du nombre de passagers des camions de livraison,</span><span class="sxs-lookup"><span data-stu-id="fa7d0-185">The toll authority isn't concerned with the number of passengers in the delivery trucks.</span></span> <span data-ttu-id="fa7d0-186">et ajuste le montant en fonction du poids du camion, en procédant ainsi :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-186">Instead, they adjust the toll amount based on the weight class of the trucks as follows:</span></span>

- <span data-ttu-id="fa7d0-187">Camions de plus de 5 000 lb : +5,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-187">Trucks over 5000 lbs are charged an extra $5.00.</span></span>
- <span data-ttu-id="fa7d0-188">Camions de moins de 3000 lb : -2,00 $.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-188">Light trucks under 3000 lbs are given a $2.00 discount.</span></span>

<span data-ttu-id="fa7d0-189">Cette règle est implémentée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-189">That rule is implemented with the following code:</span></span>

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

<span data-ttu-id="fa7d0-190">Le code précédent montre la clause `when` d’une branche switch.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-190">The preceding code shows the `when` clause of a switch arm.</span></span> <span data-ttu-id="fa7d0-191">Cette clause `when` sert à tester les conditions autres que l’égalité sur une propriété.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-191">You use the `when` clause to test conditions other than equality on a property.</span></span> <span data-ttu-id="fa7d0-192">Une fois terminée, la méthode se présente ainsi :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-192">When you've finished, you'll have a method that looks much like the following:</span></span>

```csharp
vehicle switch
{
    Car { Passengers: 0}        => 2.00m + 0.50m,
    Car { Passengers: 1}        => 2.0m,
    Car { Passengers: 2}        => 2.0m - 0.50m,
    Car c                       => 2.00m - 1.0m,

    Taxi { Fares: 0}  => 3.50m + 1.00m,
    Taxi { Fares: 1 } => 3.50m,
    Taxi { Fares: 2}  => 3.50m - 0.50m,
    Taxi t            => 3.50m - 1.00m,

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

<span data-ttu-id="fa7d0-193">La plupart de ces branches switch sont des exemples de **modèles récursifs**.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-193">Many of these switch arms are examples of **recursive patterns**.</span></span> <span data-ttu-id="fa7d0-194">Par exemple, `Car { Passengers: 1}` indique un modèle de constante à l’intérieur d’un modèle de propriété.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-194">For example, `Car { Passengers: 1}` shows a constant pattern inside a property pattern.</span></span>

<span data-ttu-id="fa7d0-195">Il est possible de rendre ce code moins répétitif avec des switch imbriqués.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-195">You can make this code less repetitive by using nested switches.</span></span> <span data-ttu-id="fa7d0-196">Dans les exemples précédents, `Car` et `Taxi` ont chacun quatre branches différentes.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-196">The `Car` and `Taxi` both have four different arms in the preceding examples.</span></span> <span data-ttu-id="fa7d0-197">On peut créer dans les deux cas un modèle de type qui vient alimenter un modèle de propriété.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-197">In both cases, you can create a type pattern that feeds into a property pattern.</span></span> <span data-ttu-id="fa7d0-198">Cette technique est illustrée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-198">This technique is shown in the following code:</span></span>

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

<span data-ttu-id="fa7d0-199">Dans l’exemple précédent, l’expression récursive évite de répéter les branches `Car` et `Taxi` contenant des branches enfant qui testent la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-199">In the preceding sample, using a recursive expression means you don't repeat the `Car` and `Taxi` arms containing child arms that test the property value.</span></span> <span data-ttu-id="fa7d0-200">Cette technique n’est pas utilisée pour les branches `Bus` et `DeliveryTruck`, car elles correspondent à des plages de test pour la propriété, et non à des valeurs discrètes.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-200">This technique isn't used for the `Bus` and `DeliveryTruck` arms because those arms are testing ranges for the property, not discrete values.</span></span>

## <a name="add-peak-pricing"></a><span data-ttu-id="fa7d0-201">Ajouter la tarification heures creuses/heures de pointe</span><span class="sxs-lookup"><span data-stu-id="fa7d0-201">Add peak pricing</span></span>

<span data-ttu-id="fa7d0-202">En guise de fonctionnalité finale, l’autorité de péage souhaite ajouter une tarification soumise à une contrainte horaire.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-202">For the final feature, the toll authority wants to add time sensitive peak pricing.</span></span> <span data-ttu-id="fa7d0-203">Pendant les heures d’affluence du matin et du soir, les péages sont doublés.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-203">During the morning and evening rush hours, the tolls are doubled.</span></span> <span data-ttu-id="fa7d0-204">Cette règle ne s’applique au trafic que dans un sens : en allant vers la ville le matin et en en sortant le soir.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-204">That rule only affects traffic in one direction: inbound to the city in the morning, and outbound in the evening rush hour.</span></span> <span data-ttu-id="fa7d0-205">Le reste du temps, pendant la journée de travail, les péages augmentent de 50 %.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-205">During other times during the workday, tolls increase by 50%.</span></span> <span data-ttu-id="fa7d0-206">Tard le soir et tôt le matin, ils sont réduits de 25 %.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-206">Late night and early morning, tolls are reduced by 25%.</span></span> <span data-ttu-id="fa7d0-207">Le taux normal s’applique le weekend, quelle que soit l’heure.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-207">During the weekend, it's the normal rate, regardless of the time.</span></span>

<span data-ttu-id="fa7d0-208">Pour cette fonctionnalité, nous allons utiliser les critères spéciaux, mais en les associant à d’autres techniques.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-208">You'll use pattern matching for this feature, but you'll integrate it with other techniques.</span></span> <span data-ttu-id="fa7d0-209">Vous pourriez élaborer une seule expression de critères spéciaux qui tiendrait compte de toutes les combinaisons direction/jour de la semaine/heure.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-209">You could build a single pattern match expression that would account for all the combinations of direction, day of the week, and time.</span></span> <span data-ttu-id="fa7d0-210">Elle serait cependant complexe,</span><span class="sxs-lookup"><span data-stu-id="fa7d0-210">The result would be a complicated expression.</span></span> <span data-ttu-id="fa7d0-211">difficile à lire, à comprendre</span><span class="sxs-lookup"><span data-stu-id="fa7d0-211">It would be hard to read and difficult to understand.</span></span> <span data-ttu-id="fa7d0-212">et à vérifier.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-212">That makes it hard to ensure correctness.</span></span> <span data-ttu-id="fa7d0-213">Combinons plutôt ces méthodes afin de créer un tuple de valeurs décrivant de manière concise tous ces états.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-213">Instead, combine those methods to build a tuple of values that concisely describes all those states.</span></span> <span data-ttu-id="fa7d0-214">Ensuite, utilisons les critères spéciaux pour calculer un multiplicateur de péage.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-214">Then use pattern matching to calculate a multiplier for the toll.</span></span> <span data-ttu-id="fa7d0-215">Le tuple comporte trois conditions discrètes :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-215">The tuple contains three discrete conditions:</span></span>

- <span data-ttu-id="fa7d0-216">le jour : semaine / weekend ;</span><span class="sxs-lookup"><span data-stu-id="fa7d0-216">The day is either a weekday or a weekend.</span></span>
- <span data-ttu-id="fa7d0-217">la tranche horaire ;</span><span class="sxs-lookup"><span data-stu-id="fa7d0-217">The band of time when the toll is collected.</span></span>
- <span data-ttu-id="fa7d0-218">la direction : vers l’intérieur ou l’extérieur de la ville.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-218">The direction is into the city or out of the city</span></span>

<span data-ttu-id="fa7d0-219">Le tableau suivant montre les combinaisons de valeurs d’entrée et le multiplicateur tarifaire :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-219">The following table shows the combinations of input values and the peak pricing multiplier:</span></span>

| <span data-ttu-id="fa7d0-220">Jour</span><span class="sxs-lookup"><span data-stu-id="fa7d0-220">Day</span></span>        | <span data-ttu-id="fa7d0-221">Temps</span><span class="sxs-lookup"><span data-stu-id="fa7d0-221">Time</span></span>         | <span data-ttu-id="fa7d0-222">Direction</span><span class="sxs-lookup"><span data-stu-id="fa7d0-222">Direction</span></span> | <span data-ttu-id="fa7d0-223">Premium</span><span class="sxs-lookup"><span data-stu-id="fa7d0-223">Premium</span></span> |
| ---------- | ------------ | --------- |--------:|
| <span data-ttu-id="fa7d0-224">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-224">Weekday</span></span>    | <span data-ttu-id="fa7d0-225">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="fa7d0-225">morning rush</span></span> | <span data-ttu-id="fa7d0-226">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-226">inbound</span></span>   | <span data-ttu-id="fa7d0-227">x 2,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-227">x 2.00</span></span>  |
| <span data-ttu-id="fa7d0-228">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-228">Weekday</span></span>    | <span data-ttu-id="fa7d0-229">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="fa7d0-229">morning rush</span></span> | <span data-ttu-id="fa7d0-230">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-230">outbound</span></span>  | <span data-ttu-id="fa7d0-231">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-231">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-232">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-232">Weekday</span></span>    | <span data-ttu-id="fa7d0-233">Journée</span><span class="sxs-lookup"><span data-stu-id="fa7d0-233">daytime</span></span>      | <span data-ttu-id="fa7d0-234">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-234">inbound</span></span>   | <span data-ttu-id="fa7d0-235">x 1,50</span><span class="sxs-lookup"><span data-stu-id="fa7d0-235">x 1.50</span></span>  |
| <span data-ttu-id="fa7d0-236">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-236">Weekday</span></span>    | <span data-ttu-id="fa7d0-237">Journée</span><span class="sxs-lookup"><span data-stu-id="fa7d0-237">daytime</span></span>      | <span data-ttu-id="fa7d0-238">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-238">outbound</span></span>  | <span data-ttu-id="fa7d0-239">x 1,50</span><span class="sxs-lookup"><span data-stu-id="fa7d0-239">x 1.50</span></span>  |
| <span data-ttu-id="fa7d0-240">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-240">Weekday</span></span>    | <span data-ttu-id="fa7d0-241">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="fa7d0-241">evening rush</span></span> | <span data-ttu-id="fa7d0-242">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-242">inbound</span></span>   | <span data-ttu-id="fa7d0-243">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-243">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-244">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-244">Weekday</span></span>    | <span data-ttu-id="fa7d0-245">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="fa7d0-245">evening rush</span></span> | <span data-ttu-id="fa7d0-246">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-246">outbound</span></span>  | <span data-ttu-id="fa7d0-247">x 2,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-247">x 2.00</span></span>  |
| <span data-ttu-id="fa7d0-248">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-248">Weekday</span></span>    | <span data-ttu-id="fa7d0-249">Nuit</span><span class="sxs-lookup"><span data-stu-id="fa7d0-249">overnight</span></span>    | <span data-ttu-id="fa7d0-250">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-250">inbound</span></span>   | <span data-ttu-id="fa7d0-251">x 0,75</span><span class="sxs-lookup"><span data-stu-id="fa7d0-251">x 0.75</span></span>  |
| <span data-ttu-id="fa7d0-252">Jour de la semaine</span><span class="sxs-lookup"><span data-stu-id="fa7d0-252">Weekday</span></span>    | <span data-ttu-id="fa7d0-253">Nuit</span><span class="sxs-lookup"><span data-stu-id="fa7d0-253">overnight</span></span>    | <span data-ttu-id="fa7d0-254">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-254">outbound</span></span>  | <span data-ttu-id="fa7d0-255">x 0,75</span><span class="sxs-lookup"><span data-stu-id="fa7d0-255">x 0.75</span></span>  |
| <span data-ttu-id="fa7d0-256">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-256">Weekend</span></span>    | <span data-ttu-id="fa7d0-257">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="fa7d0-257">morning rush</span></span> | <span data-ttu-id="fa7d0-258">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-258">inbound</span></span>   | <span data-ttu-id="fa7d0-259">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-259">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-260">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-260">Weekend</span></span>    | <span data-ttu-id="fa7d0-261">Heure de pointe du matin</span><span class="sxs-lookup"><span data-stu-id="fa7d0-261">morning rush</span></span> | <span data-ttu-id="fa7d0-262">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-262">outbound</span></span>  | <span data-ttu-id="fa7d0-263">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-263">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-264">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-264">Weekend</span></span>    | <span data-ttu-id="fa7d0-265">Journée</span><span class="sxs-lookup"><span data-stu-id="fa7d0-265">daytime</span></span>      | <span data-ttu-id="fa7d0-266">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-266">inbound</span></span>   | <span data-ttu-id="fa7d0-267">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-267">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-268">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-268">Weekend</span></span>    | <span data-ttu-id="fa7d0-269">Journée</span><span class="sxs-lookup"><span data-stu-id="fa7d0-269">daytime</span></span>      | <span data-ttu-id="fa7d0-270">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-270">outbound</span></span>  | <span data-ttu-id="fa7d0-271">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-271">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-272">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-272">Weekend</span></span>    | <span data-ttu-id="fa7d0-273">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="fa7d0-273">evening rush</span></span> | <span data-ttu-id="fa7d0-274">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-274">inbound</span></span>   | <span data-ttu-id="fa7d0-275">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-275">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-276">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-276">Weekend</span></span>    | <span data-ttu-id="fa7d0-277">Heure de pointe du soir</span><span class="sxs-lookup"><span data-stu-id="fa7d0-277">evening rush</span></span> | <span data-ttu-id="fa7d0-278">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-278">outbound</span></span>  | <span data-ttu-id="fa7d0-279">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-279">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-280">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-280">Weekend</span></span>    | <span data-ttu-id="fa7d0-281">Nuit</span><span class="sxs-lookup"><span data-stu-id="fa7d0-281">overnight</span></span>    | <span data-ttu-id="fa7d0-282">Vers l’intérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-282">inbound</span></span>   | <span data-ttu-id="fa7d0-283">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-283">x 1.00</span></span>  |
| <span data-ttu-id="fa7d0-284">Week-end</span><span class="sxs-lookup"><span data-stu-id="fa7d0-284">Weekend</span></span>    | <span data-ttu-id="fa7d0-285">Nuit</span><span class="sxs-lookup"><span data-stu-id="fa7d0-285">overnight</span></span>    | <span data-ttu-id="fa7d0-286">Vers l’extérieur de la ville</span><span class="sxs-lookup"><span data-stu-id="fa7d0-286">outbound</span></span>  | <span data-ttu-id="fa7d0-287">x 1,00</span><span class="sxs-lookup"><span data-stu-id="fa7d0-287">x 1.00</span></span>  |

<span data-ttu-id="fa7d0-288">Les trois variables produisent 16 combinaisons différentes.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-288">There are 16 different combinations of the three variables.</span></span> <span data-ttu-id="fa7d0-289">On peut simplifier l’expression switch finale en associant certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-289">By combining some of the conditions, you'll simplify the final switch expression.</span></span>

<span data-ttu-id="fa7d0-290">Le système qui collecte les péages utilise une structure <xref:System.DateTime> pour indiquer l’heure de collecte.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-290">The system that collects the tolls uses a <xref:System.DateTime> structure for the time when the toll was collected.</span></span> <span data-ttu-id="fa7d0-291">Élaborons les méthodes de membre qui créent des variables à partir du tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-291">Build member methods that create the variables from the preceding table.</span></span> <span data-ttu-id="fa7d0-292">La fonction suivante utilise une expression switch de critères spéciaux pour exprimer si <xref:System.DateTime> représente un jour de weekend ou de semaine :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-292">The following function uses a pattern matching switch expression to express whether a <xref:System.DateTime> represents a weekend or a weekday:</span></span>

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

<span data-ttu-id="fa7d0-293">La méthode fonctionne, mais elle est répétitive.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-293">That method works, but it's repetitious.</span></span> <span data-ttu-id="fa7d0-294">On peut la simplifier comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-294">You can simplify it, as shown in the following code:</span></span>

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

<span data-ttu-id="fa7d0-295">Ensuite, ajoutons une fonction similaire pour catégoriser l’heure dans les blocs :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-295">Next, add a similar function to categorize the time into the blocks:</span></span>

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

<span data-ttu-id="fa7d0-296">La méthode précédente n’utilise pas les critères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-296">The previous method doesn't use pattern matching.</span></span> <span data-ttu-id="fa7d0-297">Le code est plus clair avec une cascade bien connue d’instructions `if`.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-297">It's clearer using a familiar cascade of `if` statements.</span></span> <span data-ttu-id="fa7d0-298">On ajoute en revanche un `enum` privé pour convertir chaque plage de temps en une valeur discrète.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-298">You do add a private `enum` to convert each range of time to a discrete value.</span></span>

<span data-ttu-id="fa7d0-299">Maintenant que nous avons créé ces méthodes, utilisons une autre expression `switch` avec le **modèle de tuple** pour calculer le multiplicateur tarifaire.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-299">After you create those methods, you can use another `switch` expression with the **tuple pattern** to calculate the pricing premium.</span></span> <span data-ttu-id="fa7d0-300">On pourrait concevoir une expression `switch` comportant les 16 branches :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-300">You could build a `switch` expression with all 16 arms:</span></span>

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

<span data-ttu-id="fa7d0-301">Le code ci-dessus fonctionne, mais on peut le simplifier.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-301">The above code works, but it can be simplified.</span></span> <span data-ttu-id="fa7d0-302">Les huit combinaisons du weekend correspondent au même péage.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-302">All eight combinations for the weekend have the same toll.</span></span> <span data-ttu-id="fa7d0-303">Elles sont remplaçables par la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-303">You can replace all eight with the following line:</span></span>

```csharp
(false, _, _) => 1.0m,
```

<span data-ttu-id="fa7d0-304">Le trafic entrant et le trafic sortant ont le même multiplicateur pendant la journée en semaine et pendant la nuit.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-304">Both inbound and outbound traffic have the same multiplier during the weekday daytime and overnight hours.</span></span> <span data-ttu-id="fa7d0-305">Ces quatre branches switch peuvent être remplacées par les deux lignes suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-305">Those four switch arms can be replaced with the following two lines:</span></span>

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

<span data-ttu-id="fa7d0-306">Après ces deux modifications, le code devrait se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-306">The code should look like the following code after those two changes:</span></span>

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

<span data-ttu-id="fa7d0-307">Enfin, on peut supprimer les deux branches des heures de pointe au tarif normal,</span><span class="sxs-lookup"><span data-stu-id="fa7d0-307">Finally, you can remove the two rush hour times that pay the regular price.</span></span> <span data-ttu-id="fa7d0-308">ce qui permet de remplacer `false` par un discard (`_`) dans la branche switch finale.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-308">Once you remove those arms, you can replace the `false` with a discard (`_`) in the final switch arm.</span></span> <span data-ttu-id="fa7d0-309">On obtient la méthode suivante une fois terminée :</span><span class="sxs-lookup"><span data-stu-id="fa7d0-309">You'll have the following finished method:</span></span>

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

<span data-ttu-id="fa7d0-310">Cet exemple met en évidence un des avantages des critères spéciaux : les branches du modèle sont évaluées dans l’ordre.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-310">This example highlights one of the advantages of pattern matching: the pattern branches are evaluated in order.</span></span> <span data-ttu-id="fa7d0-311">Si vous les réorganisez de telle sorte qu’une branche antérieure gère un des cas suivants, le compilateur vous avertit que le code est inaccessible.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-311">If you rearrange them so that an earlier branch handles one of your later cases, the compiler warns you about the unreachable code.</span></span> <span data-ttu-id="fa7d0-312">Grâce à ces règles de langage, nous avons pu effectuer facilement les simplifications précédentes sans craindre de modifier le code.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-312">Those language rules made it easier to do the preceding simplifications with confidence that the code didn't change.</span></span>

<span data-ttu-id="fa7d0-313">Les critères spéciaux rendent certains types de code plus lisibles et offrent une alternative aux techniques orientées objet quand vous ne pouvez pas ajouter de code à vos classes.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-313">Pattern matching makes some types of code more readable and offers an alternative to object-oriented techniques when you can't add code to your classes.</span></span> <span data-ttu-id="fa7d0-314">Le cloud est à l’origine d’une séparation entre les données et les fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-314">The cloud is causing data and functionality to live apart.</span></span> <span data-ttu-id="fa7d0-315">La *forme* des données et les *opérations* effectuées sur ces dernières ne sont pas nécessairement décrites ensemble.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-315">The *shape* of the data and the *operations* on it aren't necessarily described together.</span></span> <span data-ttu-id="fa7d0-316">Dans ce tutoriel, nous avons exploité les données existantes d’une manière totalement différente de leur fonction d’origine.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-316">In this tutorial, you consumed existing data in entirely different ways from its original function.</span></span> <span data-ttu-id="fa7d0-317">Les critères spéciaux offrent la possibilité d’écrire des fonctionnalités qui remplacent ces types, même sans pouvoir les étendre.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-317">Pattern matching gave you the ability to write functionality that overrode those types, even though you couldn't extend them.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fa7d0-318">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fa7d0-318">Next steps</span></span>

<span data-ttu-id="fa7d0-319">Vous pouvez télécharger le code terminé dans référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished).</span><span class="sxs-lookup"><span data-stu-id="fa7d0-319">You can download the finished code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished) GitHub repository.</span></span> <span data-ttu-id="fa7d0-320">Explorez les modèles par vous-même et ajoutez cette technique à vos activités de codage régulières.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-320">Explore patterns on your own and add this technique into your regular coding activities.</span></span> <span data-ttu-id="fa7d0-321">Ces techniques représentent une autre façon d’aborder les problèmes et de créer de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="fa7d0-321">Learning these techniques gives you another way to approach problems and create new functionality.</span></span>
