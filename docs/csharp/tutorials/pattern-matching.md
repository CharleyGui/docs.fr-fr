---
title: 'Didacticiel : générer des algorithmes avec des critères spéciaux'
description: Ce tutoriel avancé montre comment utiliser des techniques de critères spéciaux pour créer des fonctionnalités à l’aide de données et d’algorithmes créés séparément.
ms.date: 10/06/2020
ms.technology: csharp-whats-new
ms.custom: contperfq1
ms.openlocfilehash: 015bab574ca4255ffe355bd02bfb54b58e4ea7e0
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877663"
---
# <a name="tutorial-use-pattern-matching-to-build-type-driven-and-data-driven-algorithms"></a>Didacticiel : utiliser des critères spéciaux pour générer des algorithmes pilotés par type et pilotés par les données.

C# 7 a introduit des fonctionnalités de critères spéciaux de base. Ces fonctionnalités sont étendues en C# 8 et C# 9 avec de nouveaux modèles et expressions. Il est possible d’écrire des fonctionnalités qui se comportent comme si des types provenant potentiellement d’autres bibliothèques avaient été étendus. Une autre utilisation des modèles consiste à créer des fonctionnalités requises par une application qui ne sont pas essentielles pour le type étendu.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Reconnaître les situations dans lesquelles les critères spéciaux sont nécessaires.
> - Utiliser des expressions de critères spéciaux pour implémenter des comportements en fonction des types et des valeurs de propriété.
> - Combiner des critères spéciaux avec d’autres techniques pour créer des algorithmes complets.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET 5, qui comprend le compilateur C# 9. Le compilateur C# 8 est disponible à partir de [Visual Studio 2019 version 16,9 Preview 1](https://visualstudio.microsoft.com/vs/preview/) ou [.net 5,0 SDK](https://dot.net/get-dotnet5).

Ce tutoriel suppose de connaître C# et .NET, y compris Visual Studio ou l’interface CLI .NET Core.

## <a name="scenarios-for-pattern-matching"></a>Scénarios des critères spéciaux

Le développement moderne passe souvent par l’intégration de données provenant de plusieurs sources et par la présentation d’informations et d’insights tirés de ces données dans une seule et même application. Ni vous ni votre équipe n’aurez accès aux types qui représentent les données entrantes ou ne pourrez les contrôler.

Une conception classique orientée objet exigerait de créer dans l’application des types représentant chacun des types de données de ces multiples sources. L’application s’appuierait alors sur ces nouveaux types pour élaborer des hiérarchies d’héritage, créer des méthodes virtuelles et implémenter des abstractions. Ces techniques fonctionnent et représentent parfois les meilleurs outils disponibles. Il est possible dans d’autres cas d’écrire du code moins long et plus clair, à l’aide de techniques qui séparent les données des opérations qui les manipulent.

Ce tutoriel vise à créer et à explorer une application qui prend en entrée des données provenant de plusieurs sources externes pour un seul scénario. Nous verrons en quoi les **critères spéciaux** constituent un moyen efficace de consommer et de traiter ces données d’une autre manière que ce que prévoit le système d’origine.

Prenons une grande zone métropolitaine qui utilise des péages et des tarifs heures creuses/heures de pointe pour réguler le trafic. Nous allons écrire une application qui calcule le péage en fonction du type de véhicule. Lors d’améliorations ultérieures, nous intégrerons aux tarifs le nombre de passagers du véhicule ainsi que l’heure et le jour de la semaine.

À partir de cette brève description, vous avez peut-être rapidement esquissé une hiérarchie d’objets pour modéliser ce système. Cependant, les données proviennent de plusieurs sources, et notamment d’autres systèmes de gestion de l’immatriculation des véhicules. Ils fournissent des classes différentes pour modéliser ces données, sans proposer de modèle objet unique. Dans ce tutoriel, nous allons utiliser ces classes simplifiées pour modéliser les données sur les véhicules issues de ces systèmes externes, comme dans le code suivant :

[!code-csharp[ExternalSystems](~/samples/snippets/csharp/tutorials/patterns/start/toll-calculator/ExternalSystems.cs)]

Vous pouvez télécharger l’exemple de démarrage à partir du référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/start). Comme on peut le voir, les classes de véhicules proviennent de différents systèmes et utilisent différents espaces de noms. Aucune classe de base commune, autre que `System.Object`, n’est exploitable.

## <a name="pattern-matching-designs"></a>Conception avec les critères spéciaux

Le scénario utilisé dans ce didacticiel met en évidence les types de problèmes que la correspondance de modèle est bien adaptée pour résoudre :

- Les objets dont vous avez besoin ne figurent pas dans une hiérarchie d’objets correspondant à vos objectifs. Vous utilisez peut-être des classes faisant partie de systèmes non liés les uns aux autres.
- Les fonctionnalités ajoutées ne font pas partie de l’abstraction de base de ces classes. Le péage payé *change* selon les types de véhicules, mais il ne s’agit pas d’une fonction essentielle du véhicule.

Lorsque la *forme* des données et les *opérations* effectuées sur celles-ci ne sont pas décrites ensemble, les fonctionnalités de critères spéciaux de C# facilitent la tâche.

## <a name="implement-the-basic-toll-calculations"></a>Implémenter les calculs de péage de base

Le calcul de péage le plus élémentaire s’appuie uniquement sur le type de véhicule :

- `Car` : 2,00 $.
- `Taxi` : 3,50 $.
- `Bus` : 5,00 $.
- `DeliveryTruck` : 10,00 $.

Créez une classe `TollCalculator` et implémentez les critères spéciaux sur le type de véhicule pour obtenir le montant du péage. Le code suivant montre l’implémentation initiale de `TollCalculator`.

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

Le code précédent utilise une **expression switch** (différente d’une instruction [`switch`](../language-reference/keywords/switch.md)) qui teste le **modèle de type**. Une **expression switch** commence par la variable, `vehicle` dans le code précédent, suivie du mot clé `switch`. Viennent ensuite toutes les **branches switch** entre accolades. L’expression `switch` ajoute d’autres perfectionnements à la syntaxe qui entoure l’instruction `switch`. Le mot clé `case` est omis, et le résultat de chaque branche est une expression. Les deux dernières montrent une nouvelle fonctionnalité du langage. Le cas `{ }` représente n’importe quel objet non Null ne correspondant à aucune des branches antérieures. Il intercepte tous les types incorrects passés à cette méthode.  Le cas `{ }` doit suivre les cas de chaque type de véhicule. Si l’ordre était inversé, le cas `{ }` serait prioritaire. Enfin, le modèle `null` détecte si un `null` est passé à cette méthode. Le `null` modèle peut être en dernier, car les autres modèles de type correspondent uniquement à un objet non null du type correct.

Pour tester ce code, utilisez le code suivant dans `Program.cs` :

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

Ce code est inclus dans le projet de démarrage, mais il est commenté. Supprimez les commentaires et vous pouvez tester ce que vous avez écrit.

On commence à voir comment les modèles peuvent nous aider à créer des algorithmes dans lesquels le code et les données sont séparés. L’ expression `switch` teste le type et produit différentes valeurs en fonction des résultats. Ce n’est que le début.

## <a name="add-occupancy-pricing"></a>Ajouter la tarification en fonction du taux d’occupation

L’autorité de péage souhaite inciter les véhicules à circuler à capacité maximale. Elle a décidé de fixer un tarif plus élevé pour les véhicules transportant peu de passagers et un prix inférieur pour les véhicules pleins, de façon à encourager ces derniers :

- Voitures et taxis sans passager : +0,50 $.
- Voitures et taxis avec deux passagers : remise de 0,50 $.
- Voitures et taxis avec trois passagers ou plus : -1,00 $.
- Bus remplis à moins de 50 % : +2,00 $.
- Bus remplis à plus de 90 % : -1,00 $.

Il est possible d’implémenter ces règles avec le **modèle de propriété** dans la même expression switch. Le modèle de propriété examine les propriétés de l’objet une fois que le type a été déterminé. L’unique cas `Car` est étendu à quatre cas différents :

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

Les trois premiers cas testent le type `Car`, puis vérifient la valeur de la propriété `Passengers`. Si les deux correspondent, cette expression est évaluée et retournée.

Les cas des taxis sont étendus de la même manière :

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

Dans l’exemple précédent, la clause `when` a été omise sur le cas final.

Maintenant, implémentons les règles de taux d’occupation en développant les cas des bus, comme dans l’exemple suivant :

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

L’autorité de péage ne se soucie pas du nombre de passagers des camions de livraison, et ajuste le montant en fonction du poids du camion, en procédant ainsi :

- Camions de plus de 5 000 lb : +5,00 $.
- Camions de moins de 3000 lb : -2,00 $.

Cette règle est implémentée dans le code suivant :

```csharp
vehicle switch
{
    // ...

    DeliveryTruck t when (t.GrossWeightClass > 5000) => 10.00m + 5.00m,
    DeliveryTruck t when (t.GrossWeightClass < 3000) => 10.00m - 2.00m,
    DeliveryTruck t => 10.00m,
};
```

Le code précédent montre la clause `when` d’une branche switch. Cette clause `when` sert à tester les conditions autres que l’égalité sur une propriété. Une fois que vous avez terminé, vous disposez d’une méthode qui ressemble au code suivant :

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

La plupart de ces branches switch sont des exemples de **modèles récursifs**. Par exemple, `Car { Passengers: 1}` indique un modèle de constante à l’intérieur d’un modèle de propriété.

Il est possible de rendre ce code moins répétitif avec des switch imbriqués. Dans les exemples précédents, `Car` et `Taxi` ont chacun quatre branches différentes. On peut créer dans les deux cas un modèle de type qui vient alimenter un modèle de propriété. Cette technique est illustrée dans le code suivant :

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

Dans l’exemple précédent, l’expression récursive évite de répéter les branches `Car` et `Taxi` contenant des branches enfant qui testent la valeur de propriété. Cette technique n’est pas utilisée pour les branches `Bus` et `DeliveryTruck`, car elles correspondent à des plages de test pour la propriété, et non à des valeurs discrètes.

## <a name="add-peak-pricing"></a>Ajouter la tarification heures creuses/heures de pointe

En guise de fonctionnalité finale, l’autorité de péage souhaite ajouter une tarification soumise à une contrainte horaire. Pendant les heures d’affluence du matin et du soir, les péages sont doublés. Cette règle ne s’applique au trafic que dans un sens : en allant vers la ville le matin et en en sortant le soir. Le reste du temps, pendant la journée de travail, les péages augmentent de 50 %. Tard le soir et tôt le matin, ils sont réduits de 25 %. Le taux normal s’applique le weekend, quelle que soit l’heure. Vous pouvez utiliser une série si `if` les `else` instructions et permettent d’exprimer ce qui suit à l’aide du code suivant :

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#SnippetPremiumWithoutPattern)]

Le code précédent fonctionne correctement, mais n’est pas lisible. Vous devez chaîner tous les cas d’entrée et les instructions imbriquées `if` pour la raison du code. Au lieu de cela, vous allez utiliser des critères spéciaux pour cette fonctionnalité, mais vous allez l’intégrer à d’autres techniques. Vous pourriez élaborer une seule expression de critères spéciaux qui tiendrait compte de toutes les combinaisons direction/jour de la semaine/heure. Elle serait cependant complexe, difficile à lire, à comprendre et à vérifier. Combinons plutôt ces méthodes afin de créer un tuple de valeurs décrivant de manière concise tous ces états. Ensuite, utilisons les critères spéciaux pour calculer un multiplicateur de péage. Le tuple comporte trois conditions discrètes :

- le jour : semaine / weekend ;
- la tranche horaire ;
- la direction : vers l’intérieur ou l’extérieur de la ville.

Le tableau suivant montre les combinaisons de valeurs d’entrée et le multiplicateur tarifaire :

| Jour        | Temps         | Sens | Premium |
| ---------- | ------------ | --------- |--------:|
| Jour de la semaine    | Heure de pointe du matin | Vers l’intérieur de la ville   | x 2,00  |
| Jour de la semaine    | Heure de pointe du matin | Vers l’extérieur de la ville  | x 1,00  |
| Jour de la semaine    | Journée      | Vers l’intérieur de la ville   | x 1,50  |
| Jour de la semaine    | Journée      | Vers l’extérieur de la ville  | x 1,50  |
| Jour de la semaine    | Heure de pointe du soir | Vers l’intérieur de la ville   | x 1,00  |
| Jour de la semaine    | Heure de pointe du soir | Vers l’extérieur de la ville  | x 2,00  |
| Jour de la semaine    | Nuit    | Vers l’intérieur de la ville   | x 0,75  |
| Jour de la semaine    | Nuit    | Vers l’extérieur de la ville  | x 0,75  |
| Week-end    | Heure de pointe du matin | Vers l’intérieur de la ville   | x 1,00  |
| Week-end    | Heure de pointe du matin | Vers l’extérieur de la ville  | x 1,00  |
| Week-end    | Journée      | Vers l’intérieur de la ville   | x 1,00  |
| Week-end    | Journée      | Vers l’extérieur de la ville  | x 1,00  |
| Week-end    | Heure de pointe du soir | Vers l’intérieur de la ville   | x 1,00  |
| Week-end    | Heure de pointe du soir | Vers l’extérieur de la ville  | x 1,00  |
| Week-end    | Nuit    | Vers l’intérieur de la ville   | x 1,00  |
| Week-end    | Nuit    | Vers l’extérieur de la ville  | x 1,00  |

Les trois variables produisent 16 combinaisons différentes. On peut simplifier l’expression switch finale en associant certaines conditions.

Le système qui collecte les péages utilise une structure <xref:System.DateTime> pour indiquer l’heure de collecte. Élaborons les méthodes de membre qui créent des variables à partir du tableau précédent. La fonction suivante utilise une expression switch de critères spéciaux pour exprimer si <xref:System.DateTime> représente un jour de weekend ou de semaine :

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

Cette méthode est correcte, mais elle est répétitive. On peut la simplifier comme dans le code suivant :

[!code-csharp[IsWeekDay](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#IsWeekDay)]

Ensuite, ajoutons une fonction similaire pour catégoriser l’heure dans les blocs :

[!code-csharp[GetTimeBand](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#GetTimeBand)]

Vous ajoutez un privé `enum` pour convertir chaque plage horaire en valeur discrète. Ensuite, la `GetTimeBand` méthode utilise des *modèles relationnels*, et des *conjonctives ou des modèles*, tous deux ajoutés en C# 9,0. Le modèle relationnel vous permet de tester une valeur numérique à l’aide `<` de,, `>` `<=` ou `>=` . Le `or` modèle teste si une expression correspond à un ou plusieurs modèles. Vous pouvez également utiliser un `and` modèle pour vous assurer qu’une expression correspond à deux modèles distincts et un `not` modèle pour vérifier qu’une expression ne correspond pas à un modèle.

Maintenant que nous avons créé ces méthodes, utilisons une autre expression `switch` avec le **modèle de tuple** pour calculer le multiplicateur tarifaire. On pourrait concevoir une expression `switch` comportant les 16 branches :

[!code-csharp[FullTuplePattern](~/samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#TuplePatternOne)]

Le code ci-dessus fonctionne, mais on peut le simplifier. Les huit combinaisons du weekend correspondent au même péage. Elles sont remplaçables par la ligne suivante :

```csharp
(false, _, _) => 1.0m,
```

Le trafic entrant et le trafic sortant ont le même multiplicateur pendant la journée en semaine et pendant la nuit. Ces quatre branches switch peuvent être remplacées par les deux lignes suivantes :

```csharp
(true, TimeBand.Overnight, _) => 0.75m,
(true, TimeBand.Daytime, _)   => 1.5m,
```

Après ces deux modifications, le code devrait se présenter ainsi :

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

Enfin, on peut supprimer les deux branches des heures de pointe au tarif normal, ce qui permet de remplacer `false` par un discard (`_`) dans la branche switch finale. On obtient la méthode suivante une fois terminée :

[!code-csharp[SimplifiedTuplePattern](../../../samples/snippets/csharp/tutorials/patterns/finished/toll-calculator/TollCalculator.cs#FinalTuplePattern)]

Cet exemple met en évidence un des avantages des critères spéciaux : les branches du modèle sont évaluées dans l’ordre. Si vous les réorganisez de telle sorte qu’une branche antérieure gère un des cas suivants, le compilateur vous avertit que le code est inaccessible. Grâce à ces règles de langage, nous avons pu effectuer facilement les simplifications précédentes sans craindre de modifier le code.

Les critères spéciaux rendent certains types de code plus lisibles et offrent une alternative aux techniques orientées objet quand vous ne pouvez pas ajouter de code à vos classes. Le cloud est à l’origine d’une séparation entre les données et les fonctionnalités. La *forme* des données et les *opérations* effectuées sur ces dernières ne sont pas nécessairement décrites ensemble. Dans ce tutoriel, nous avons exploité les données existantes d’une manière totalement différente de leur fonction d’origine. Les critères spéciaux offrent la possibilité d’écrire des fonctionnalités qui remplacent ces types, même sans pouvoir les étendre.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez télécharger le code terminé dans référentiel GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/patterns/finished). Explorez les modèles par vous-même et ajoutez cette technique à vos activités de codage régulières. Ces techniques représentent une autre façon d’aborder les problèmes et de créer de nouvelles fonctionnalités.
