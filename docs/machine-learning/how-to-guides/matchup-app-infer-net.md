---
title: Application Infer.NET match-up App-programmation probabiliste
description: Découvrez comment utiliser la programmation probabiliste avec Infer.NET pour créer une application de liste de correspondance de jeu basée sur une version simplifiée de TrueSkill.
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 8e489d61c5e6cca53ba12b13fddd0b73c7f85ef9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092601"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a>Créer une application de tableau de matchs avec Infer.NET et la programmation probabiliste

Ce guide pratique porte sur la programmation probabiliste avec Infer.NET. La programmation probabiliste est une approche du Machine Learning selon laquelle des modèles personnalisés sont exprimés sous forme de programmes informatiques. Elle permet d’incorporer la connaissance du domaine dans les modèles et rend le système de Machine Learning plus facilement interprétable. Elle gère également l’inférence en ligne, c’est-à-dire le processus d’apprentissage au fil de l’intégration de nouvelles données. Infer.NET est utilisé dans différents produits de Microsoft dans Azure, Xbox et Bing.

## <a name="what-is-probabilistic-programming"></a>Qu’est-ce que la programmation probabiliste ?

La programmation probabiliste permet de créer des modèles statistiques de processus réels.

## <a name="prerequisites"></a>Conditions préalables requises

- Configuration d’un environnement de développement local

  Ce guide pratique suppose de disposer d’un ordinateur utilisable pour le développement. Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur MacOS, Windows ou Linux.

## <a name="create-your-app"></a>Créer votre application

1. Ouvrez une invite de commandes et exécutez les commandes suivantes :

```dotnetcli
dotnet new console -o myApp
cd myApp
```

La commande `dotnet` crée une application `new` de type `console`. Le paramètre `-o` crée un répertoire nommé `myApp` dans lequel est stockée votre application, et le remplit avec les fichiers requis. La commande `cd myApp` ouvre le répertoire de l’application créée.

## <a name="install-infernet-package"></a>Installer le package Infer.NET

Pour utiliser Infer.NET, vous devez installer le package `Microsoft.ML.Probabilistic.Compiler`. Dans votre invite de commandes, exécutez la commande suivante :

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a>Concevoir le modèle

L’exemple s’appuie sur des matchs de tennis de table ou de babyfoot disputés au bureau. Nous connaissons les participants et le résultat de chaque match.  Nous souhaitons déduire de ces données les compétences des joueurs. Supposons que les compétences latentes de chaque joueur suivent une distribution normale, et que leurs performances dans un match donné représentent une version bruitée de cette compétence. Les données contraignent les performances du gagnant à être supérieures à celles du perdant. Il s’agit d’une version simplifiée du célèbre modèle [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/), qui gère également les équipes, les égalités et d’autres extensions. Une [version avancée](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) de ce modèle est utilisée pour le matchmaking des jeux à succès Halo et Gears of War.

Listons les compétences déduites des joueurs, ainsi que leur écart, qui mesure l’incertitude relative aux compétences.

*Exemples de données de résultats des matchs*

Game |Gagnant | Perdant
---------|----------|---------
 1 | Joueur 0 | Joueur 1
 2 | Joueur 0 | Joueur 3
 3 | Joueur 0 | Joueur 4
 4 | Joueur 1 | Joueur 2
 5 | Joueur 3 | Joueur 1
 6 | Joueur 4 | Joueur 2

Si l’on examine plus en détail les exemples de données, on remarque que les joueurs 3 et 4 ont tous deux une victoire et une défaite à leur actif. Regardons les classements obtenus avec la programmation probabiliste. À noter également la présence d’un joueur 0, car on part toujours de zéro dans une tâche de développement.

## <a name="write-some-code"></a>Écrire du code

Maintenant que nous avons conçu le modèle, il est temps de l’exprimer sous la forme d’un programme probabiliste à l’aide de l’API de modélisation Infer.NET. Ouvrez `Program.cs` dans l’éditeur de texte de votre choix et remplacez tout son contenu par le code suivant :

```csharp
namespace myApp

{
    using System;
    using System.Linq;
    using Microsoft.ML.Probabilistic;
    using Microsoft.ML.Probabilistic.Distributions;
    using Microsoft.ML.Probabilistic.Models;

    class Program
    {

        static void Main(string[] args)
        {
            // The winner and loser in each of 6 samples games
            var winnerData = new[] { 0, 0, 0, 1, 3, 4 };
            var loserData = new[] { 1, 3, 4, 2, 1, 2 };

            // Define the statistical model as a probabilistic program
            var game = new Range(winnerData.Length);
            var player = new Range(winnerData.Concat(loserData).Max() + 1);
            var playerSkills = Variable.Array<double>(player);
            playerSkills[player] = Variable.GaussianFromMeanAndVariance(6, 9).ForEach(player);

            var winners = Variable.Array<int>(game);
            var losers = Variable.Array<int>(game);

            using (Variable.ForEach(game))
            {
                // The player performance is a noisy version of their skill
                var winnerPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[winners[game]], 1.0);
                var loserPerformance = Variable.GaussianFromMeanAndVariance(playerSkills[losers[game]], 1.0);

                // The winner performed better in this game
                Variable.ConstrainTrue(winnerPerformance > loserPerformance);
            }

            // Attach the data to the model
            winners.ObservedValue = winnerData;
            losers.ObservedValue = loserData;

            // Run inference
            var inferenceEngine = new InferenceEngine();
            var inferredSkills = inferenceEngine.Infer<Gaussian[]>(playerSkills);

            // The inferred skills are uncertain, which is captured in their variance
            var orderedPlayerSkills = inferredSkills
               .Select((s, i) => new { Player = i, Skill = s })
               .OrderByDescending(ps => ps.Skill.GetMean());

            foreach (var playerSkill in orderedPlayerSkills)
            {
                Console.WriteLine($"Player {playerSkill.Player} skill: {playerSkill.Skill}");
            }
        }
    }
}
```

## <a name="run-your-app"></a>Exécutez l'application.

Dans votre invite de commandes, exécutez la commande suivante :

```dotnetcli
dotnet run
```

## <a name="results"></a>Résultats

Vous devriez obtenir les résultats suivants :

```console
Compiling model...done.
Iterating:
.........|.........|.........|.........|.........| 50
Player 0 skill: Gaussian(9.517, 3.926)
Player 3 skill: Gaussian(6.834, 3.892)
Player 4 skill: Gaussian(6.054, 4.731)
Player 1 skill: Gaussian(4.955, 3.503)
Player 2 skill: Gaussian(2.639, 4.288)
```

Dans les résultats, on remarque que le joueur 3 est légèrement au-dessus du joueur 4 selon notre modèle. Cela s’explique par le fait que la victoire du joueur 3 sur le joueur 1 a plus d’impact que celle du joueur 4 sur le joueur 2 – notons que le joueur 1 bat le joueur 2. Le joueur 0 est le meilleur joueur !

## <a name="keep-learning"></a>Continuer à apprendre

La conception de modèles statistiques est une compétence à part entière. L’équipe Microsoft Research Cambridge a écrit un [ouvrage en ligne gratuit](http://mbmlbook.com/), qui offre une introduction en douceur à l’article. Le chapitre 3 de ce livre couvre plus en détail le modèle TrueSkill. Lorsque vous avez un modèle à l’esprit, vous pouvez le transformer en code à l’aide de la [documentation complète](https://dotnet.github.io/infer/) présente sur le site web Infer.NET.

## <a name="next-steps"></a>Étapes suivantes

Consultez notre référentiel GitHub Infer.NET pour continuer l’apprentissage et trouver d’autres exemples.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/Infer](https://github.com/dotnet/infer)
