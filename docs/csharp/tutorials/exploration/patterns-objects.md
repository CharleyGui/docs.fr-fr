---
title: Utiliser des modèles dans les objets-didacticiel C#
description: Ce didacticiel vous apprend à utiliser des critères spéciaux dans les membres d’une classe pour créer de meilleurs modèles pour le comportement des objets
ms.date: 11/05/2020
ms.openlocfilehash: 072f6f57696504c2d691473e3a43c1cda53f227f
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94332190"
---
# <a name="use-pattern-matching-to-build-your-class-behavior-for-better-code"></a>Utilisez des critères spéciaux pour générer le comportement de votre classe pour un meilleur code

Les fonctionnalités de critères spéciaux en C# fournissent une syntaxe pour exprimer vos algorithmes. Vous pouvez utiliser ces techniques pour implémenter le comportement dans vos classes. Vous pouvez combiner la conception de classes orientée objet avec une implémentation orientée données pour fournir un code concis lors de la modélisation d’objets réels.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Exprimez vos classes orientées objet à l’aide de modèles de données.
> - Implémentez ces modèles à l’aide des fonctionnalités de critères spéciaux de C#.
> - Tirez parti des diagnostics du compilateur pour valider votre implémentation.

## <a name="prerequisites"></a>Prérequis

Vous devez configurer votre ordinateur pour exécuter .NET 5, y compris le compilateur C# 9,0. Le compilateur C# 9,0 est disponible à partir de [Visual Studio 2019 version 16,8 Preview](https://visualstudio.microsoft.com/vs/preview/) ou de la version [préliminaire du kit de développement logiciel (SDK) .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0).

## <a name="build-a-simulation-of-a-canal-lock"></a>Créer une simulation d’un canal de verrouillage

Dans ce didacticiel, vous allez générer une classe C# qui simule un [verrou de canal](https://en.wikipedia.org/wiki/Lock_(water_navigation)). Brièvement, un canal de verrouillage est un appareil qui soulève et abaisse les canots lorsqu’ils se déplacent entre deux étirés d’eau à différents niveaux. Un verrou a deux portes et un mécanisme pour modifier le niveau d’eau.

Dans son fonctionnement normal, un bateau entre l’un des portails, tandis que le niveau d’eau du verrou correspond au niveau de l’eau sur le côté du bateau. Une fois dans le verrou, le niveau d’eau est modifié pour correspondre au niveau d’eau où le bateau laisse le verrou. Une fois que le niveau d’eau correspond à ce côté, la porte du côté de sortie s’ouvre. Les mesures de sécurité assurent qu’un opérateur ne peut pas créer une situation dangereuse dans le canal. Le niveau d’eau ne peut être modifié que lorsque les deux portes sont fermées. Au plus une porte peut être ouverte. Pour ouvrir une porte, le niveau d’eau dans le verrou doit correspondre au niveau d’eau en dehors de la porte qui est ouverte.

Vous pouvez générer une classe C# pour modéliser ce comportement. Une `CanalLock` classe prend en charge les commandes pour ouvrir ou fermer l’une ou l’autre des portes. Il aurait d’autres commandes pour augmenter ou diminuer l’eau. La classe doit également prendre en charge les propriétés pour lire l’état actuel des portes et du niveau d’eau. Vos méthodes implémentent les mesures de sécurité.

## <a name="define-a-class"></a>Définir une classe

Vous allez générer une application console pour tester votre `CanalLock` classe. Créez un nouveau projet de console pour .NET 5 à l’aide de Visual Studio ou de l’interface de commande .NET. Ensuite, ajoutez une nouvelle classe et nommez-la `CanalLock` . Ensuite, concevez votre API publique, mais laissez les méthodes non implémentées :

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="APIDesign":::

Le code précédent Initialise l’objet afin que les deux portes soient fermées et que le niveau d’eau soit faible. Ensuite, écrivez le code de test suivant dans votre `Main` méthode pour vous guider lors de la création d’une première implémentation de la classe :

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="HappyTests":::

Ensuite, ajoutez une première implémentation de chaque méthode dans la `CanalLock` classe. Le code suivant implémente les méthodes de la classe sans se préoccuper des règles de sécurité. Vous ajouterez des tests de sécurité plus tard :

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="FirstImplementation":::

Les tests que vous avez écrits jusqu’à présent passent. Vous avez implémenté les concepts de base. À présent, écrivez un test pour la première condition d’échec. À la fin des tests précédents, les deux portes sont fermées et le niveau d’eau est défini sur faible. Ajoutez un test pour essayer d’ouvrir la porte supérieure :

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="HighGateSafetyTest":::

Ce test échoue car la porte s’ouvre. En guise de première implémentation, vous pouvez résoudre le problème à l’aide du code suivant :

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="SecondImplementation":::

Vos tests réussissent. Toutefois, à mesure que vous ajoutez d’autres tests, vous ajouterez de plus en plus de `if` clauses et testerez différentes propriétés. Bientôt, ces méthodes seront trop compliquées à mesure que vous ajouterez des conditions supplémentaires.

## <a name="implement-the-commands-with-patterns"></a>Implémenter les commandes avec des modèles

Une meilleure méthode consiste à utiliser des *modèles* pour déterminer si l’objet est dans un état valide pour exécuter une commande. Vous pouvez exprimer si une commande est autorisée en tant que fonction de trois variables : l’état de la porte, le niveau de l’eau et le nouveau paramètre :

| Nouveau paramètre | État de la porte | Niveau d’eau | Résultats             |
| ----------- | ---------- | ----------- | ------------------ |
| Fermé      | Fermé     | Importante        | Fermé             |
| Fermé      | Fermé     | Faible         | Fermé             |
| Fermé      | Ouvrir       | Importante        | Ouvrir               |
| ~~Fermé~~  | ~~Ouvrir~~   | ~~Faible~~     | ~~Fermé~~         |
| Ouvrir        | Fermé     | Importante        | Ouvrir               |
| Ouvrir        | Fermé     | Faible         | Fermé (erreur)     |
| Ouvrir        | Ouvrir       | Importante        | Ouvrir               |
| ~~Ouvrir~~    | ~~Ouvrir~~   | ~~Faible~~     | ~~Fermé (erreur)~~ |

Les quatrième et dernière lignes de la table ont du texte barré, car elles ne sont pas valides. Le code que vous ajoutez maintenant doit s’assurer que la porte de haute-mer n’est jamais ouverte lorsque l’eau est faible.  Ces États peuvent être codés comme une expression de commutateur unique (n’oubliez pas que `false` indique « fermé ») :

:::code language="csharp" source="snippets/pattern-objects/InterimSteps.cs" ID="ThirdImplementation":::

Essayez cette version. Vos tests réussissent, en validant le code. Le tableau complet indique les combinaisons possibles d’entrées et de résultats. Cela signifie que vous et d’autres développeurs pouvez consulter rapidement le tableau et voir que vous avez couvert toutes les entrées possibles. Encore plus facile, le compilateur peut également vous aider. Après avoir ajouté le code précédent, vous pouvez voir que le compilateur génère un avertissement : *CS8524* indique que l’expression de switch ne couvre pas toutes les entrées possibles. La raison de cet avertissement est que l’une des entrées est un `enum` type. Le compilateur interprète « toutes les entrées possibles » comme toutes les entrées du type sous-jacent, généralement `int` . Cette `switch` expression vérifie uniquement les valeurs déclarées dans le `enum` . Pour supprimer l’avertissement, vous pouvez ajouter un modèle de rejet tous pour le dernier ARM de l’expression. Cette condition lève une exception, car elle indique une entrée non valide :

```csharp
_  => throw new InvalidOperationException("Invalid internal state"),
```

Le bras du commutateur précédent doit être le dernier dans votre `switch` expression, car il correspond à toutes les entrées. Essayez en la déplaçant plus tôt dans l’ordre. Cela provoque une erreur du compilateur *CS8510* pour le code inaccessible dans un modèle.  La structure naturelle des expressions de commutateur permet au compilateur de générer des erreurs et des avertissements pour les erreurs éventuelles. Le « filet de sécurité » du compilateur facilite la création d’un code correct en moins d’itérations, et la liberté de combiner des bras de commutateur avec des caractères génériques. Le compilateur émettra des erreurs si votre combinaison produit des bras inaccessibles et des avertissements si vous supprimez un ARM qui est nécessaire.

La première modification consiste à combiner tous les bras où la commande doit fermer la porte ; Cette autorisation est toujours autorisée. Ajoutez le code suivant en tant que premier bras dans votre expression de commutateur :

```csharp
(false, _, _) => false,
```

Une fois que vous avez ajouté le bras du commutateur précédent, vous obtenez quatre erreurs de compilation, une sur chacun des bras où la commande est `false` . Ces bras sont déjà couverts par le bras qui vient d’être ajouté. Vous pouvez supprimer ces quatre lignes en toute sécurité. Vous avez souhaité que ce nouveau bras de commutateur remplace ces conditions.

Ensuite, vous pouvez simplifier les quatre bras où la commande doit ouvrir la porte. Dans les deux cas où le niveau d’eau est élevé, la porte peut être ouverte. (Dans un, il est déjà ouvert.) Un cas où le niveau d’eau est faible lève une exception et l’autre ne doit pas se produire. Il doit être possible de lever la même exception en toute sécurité si le verrouillage de l’eau est déjà dans un État non valide. Vous pouvez effectuer les simplifications suivantes pour ces bras :

```csharp
(true, _, WaterLevel.High) => true,
(true, false, WaterLevel.Low) => throw new InvalidOperationException("Cannot open high gate when the water is low"),
_ => throw new InvalidOperationException("Invalid internal state"),
```

Exécutez à nouveau vos tests, et ils réussissent. Voici la version finale de la `SetHighGate` méthode :

:::code language="csharp" source="snippets/pattern-objects/CanalLock.cs" ID="FinalImplementaton":::

## <a name="implement-patterns-yourself"></a>Implémentez vous-même des modèles

Maintenant que vous avez vu la technique, renseignez les `SetLowGate` `SetWaterLevel` méthodes et vous-même.  Commencez par ajouter le code suivant pour tester les opérations non valides sur ces méthodes :

:::code language="csharp" source="snippets/pattern-objects/Program.cs" ID="FinalTestCode":::

Réexécutez votre application. Vous pouvez voir que les nouveaux tests échouent et que le canal de verrouillage est dans un État non valide. Essayez d’implémenter vous-même les méthodes restantes. La méthode permettant de définir la porte inférieure doit être semblable à la méthode pour définir la porte supérieure. La méthode qui modifie le niveau d’eau a des contrôles différents, mais elle doit suivre une structure similaire. Il peut s’avérer utile d’utiliser le même processus pour la méthode qui définit le niveau d’eau. Commencez avec les quatre entrées : l’état des deux portes, l’état actuel du niveau d’eau et le nouveau niveau d’eau demandé. L’expression de Switch doit commencer par :

```csharp
CanalLockWaterLevel = (newLevel, CanalLockWaterLevel, LowWaterGateOpen, HighWaterGateOpen) switch
{
    // elided
};
```

Vous aurez 16 bras de commutateur total à remplir. Ensuite, testez et simplifiez.

Avez-vous fait des méthodes comme ceci ?

:::code language="csharp" source="snippets/pattern-objects/CanalLock.cs" ID="FinalExercise":::

Vos tests doivent réussir et le canal de verrouillage doit fonctionner en toute sécurité.

## <a name="summary"></a>Résumé

Dans ce didacticiel, vous avez appris à utiliser des critères spéciaux pour vérifier l’état interne d’un objet avant d’appliquer les modifications apportées à cet État. Vous pouvez vérifier les combinaisons de propriétés. Une fois que vous avez créé des tables pour l’une de ces transitions, vous testez votre code, puis vous simplifiez la lisibilité et la maintenabilité. Ces refactorisations initiales peuvent suggérer des refactorisations supplémentaires qui valident l’état interne ou gèrent d’autres modifications de l’API. Ce didacticiel combine des classes et des objets avec une approche plus orientée données et basée sur les modèles pour implémenter ces classes.
