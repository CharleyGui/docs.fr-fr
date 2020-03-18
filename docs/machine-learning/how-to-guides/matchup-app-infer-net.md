---
title: Infer.NET’application match-up de jeu - programmation probabiliste
description: Découvrez comment utiliser la programmation probabiliste avec Infer.NET pour créer une application de liste de jeu basée sur une version simplifiée de TrueSkill.
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 8e489d61c5e6cca53ba12b13fddd0b73c7f85ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092601"
---
# <a name="create-a-game-match-up-list-app-with-infernet-and-probabilistic-programming"></a><span data-ttu-id="30814-103">Créer une application de tableau de matchs avec Infer.NET et la programmation probabiliste</span><span class="sxs-lookup"><span data-stu-id="30814-103">Create a game match up list app with Infer.NET and probabilistic programming</span></span>

<span data-ttu-id="30814-104">Ce guide pratique porte sur la programmation probabiliste avec Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="30814-104">This how-to guide teaches you about probabilistic programming using Infer.NET.</span></span> <span data-ttu-id="30814-105">La programmation probabiliste est une approche du Machine Learning selon laquelle des modèles personnalisés sont exprimés sous forme de programmes informatiques.</span><span class="sxs-lookup"><span data-stu-id="30814-105">Probabilistic programming is a machine learning approach where custom models are expressed as computer programs.</span></span> <span data-ttu-id="30814-106">Elle permet d’incorporer la connaissance du domaine dans les modèles et rend le système de Machine Learning plus facilement interprétable.</span><span class="sxs-lookup"><span data-stu-id="30814-106">It allows for incorporating domain knowledge in the models and makes the machine learning system more interpretable.</span></span> <span data-ttu-id="30814-107">Elle gère également l’inférence en ligne, c’est-à-dire le processus d’apprentissage au fil de l’intégration de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="30814-107">It also supports online inference – the process of learning as new data arrives.</span></span> <span data-ttu-id="30814-108">Infer.NET est utilisé dans différents produits de Microsoft dans Azure, Xbox et Bing.</span><span class="sxs-lookup"><span data-stu-id="30814-108">Infer.NET is used in various products at Microsoft in Azure, Xbox, and Bing.</span></span>

## <a name="what-is-probabilistic-programming"></a><span data-ttu-id="30814-109">Qu’est-ce que la programmation probabiliste ?</span><span class="sxs-lookup"><span data-stu-id="30814-109">What is probabilistic programming?</span></span>

<span data-ttu-id="30814-110">La programmation probabiliste permet de créer des modèles statistiques de processus réels.</span><span class="sxs-lookup"><span data-stu-id="30814-110">Probabilistic programming allows you to create statistical models of real-world processes.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="30814-111">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="30814-111">Prerequisites</span></span>

- <span data-ttu-id="30814-112">Configuration d’un environnement de développement local</span><span class="sxs-lookup"><span data-stu-id="30814-112">Local development environment setup</span></span>

  <span data-ttu-id="30814-113">Ce guide pratique suppose de disposer d’un ordinateur utilisable pour le développement.</span><span class="sxs-lookup"><span data-stu-id="30814-113">This how-to guide expects you to have a machine you can use for development.</span></span> <span data-ttu-id="30814-114">Le tutoriel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) a des instructions pour configurer votre environnement de développement local sur macOS, Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="30814-114">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on macOS, Windows, or Linux.</span></span>

## <a name="create-your-app"></a><span data-ttu-id="30814-115">Créer votre application</span><span class="sxs-lookup"><span data-stu-id="30814-115">Create your app</span></span>

1. <span data-ttu-id="30814-116">Ouvrez une invite de commandes et exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="30814-116">Open a new command prompt and run the following commands:</span></span>

```dotnetcli
dotnet new console -o myApp
cd myApp
```

<span data-ttu-id="30814-117">La commande `dotnet` crée une application `new` de type `console`.</span><span class="sxs-lookup"><span data-stu-id="30814-117">The `dotnet` command creates a `new` application of type `console`.</span></span> <span data-ttu-id="30814-118">Le paramètre `-o` crée un répertoire nommé `myApp` dans lequel est stockée votre application, et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="30814-118">The `-o` parameter creates a directory named `myApp` where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="30814-119">La commande `cd myApp` ouvre le répertoire de l’application créée.</span><span class="sxs-lookup"><span data-stu-id="30814-119">The `cd myApp` command puts you into the newly created app directory.</span></span>

## <a name="install-infernet-package"></a><span data-ttu-id="30814-120">Installer le package Infer.NET</span><span class="sxs-lookup"><span data-stu-id="30814-120">Install Infer.NET package</span></span>

<span data-ttu-id="30814-121">Pour utiliser Infer.NET, vous devez installer le package `Microsoft.ML.Probabilistic.Compiler`.</span><span class="sxs-lookup"><span data-stu-id="30814-121">To use Infer.NET, you need to install the `Microsoft.ML.Probabilistic.Compiler` package.</span></span> <span data-ttu-id="30814-122">Dans votre invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="30814-122">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet add package Microsoft.ML.Probabilistic.Compiler
```

## <a name="design-your-model"></a><span data-ttu-id="30814-123">Concevoir le modèle</span><span class="sxs-lookup"><span data-stu-id="30814-123">Design your model</span></span>

<span data-ttu-id="30814-124">L’exemple s’appuie sur des matchs de tennis de table ou de babyfoot disputés au bureau.</span><span class="sxs-lookup"><span data-stu-id="30814-124">The example sample uses table tennis or foosball matches played in the office.</span></span> <span data-ttu-id="30814-125">Nous connaissons les participants et le résultat de chaque match.</span><span class="sxs-lookup"><span data-stu-id="30814-125">You have the participants and outcome of each match.</span></span>  <span data-ttu-id="30814-126">Nous souhaitons déduire de ces données les compétences des joueurs.</span><span class="sxs-lookup"><span data-stu-id="30814-126">You want to infer the player's skills from this data.</span></span> <span data-ttu-id="30814-127">Supposons que les compétences latentes de chaque joueur suivent une distribution normale, et que leurs performances dans un match donné représentent une version bruitée de cette compétence.</span><span class="sxs-lookup"><span data-stu-id="30814-127">Assume that each player has a normally distributed latent skill and their given match performance is a noisy version of this skill.</span></span> <span data-ttu-id="30814-128">Les données contraignent les performances du gagnant à être supérieures à celles du perdant.</span><span class="sxs-lookup"><span data-stu-id="30814-128">The data constrains the winner’s performance to be greater than the loser’s performance.</span></span> <span data-ttu-id="30814-129">Il s’agit d’une version simplifiée du célèbre modèle [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/), qui gère également les équipes, les égalités et d’autres extensions.</span><span class="sxs-lookup"><span data-stu-id="30814-129">This is a simplified version of the popular [TrueSkill](https://www.microsoft.com/research/project/trueskill-ranking-system/) model, which also supports teams, draws, and other extensions.</span></span> <span data-ttu-id="30814-130">Une [version avancée](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) de ce modèle est utilisée pour le matchmaking des jeux à succès Halo et Gears of War.</span><span class="sxs-lookup"><span data-stu-id="30814-130">An [advanced version](https://www.microsoft.com/research/publication/trueskill-2-improved-bayesian-skill-rating-system/) of this model is used for matchmaking in the best-selling game titles Halo and Gears of War.</span></span>

<span data-ttu-id="30814-131">Listons les compétences déduites des joueurs, ainsi que leur écart, qui mesure l’incertitude relative aux compétences.</span><span class="sxs-lookup"><span data-stu-id="30814-131">You need to list the inferred player skills, alongside with their variance – the measure of uncertainty around the skills.</span></span>

<span data-ttu-id="30814-132">*Exemples de données de résultats des matchs*</span><span class="sxs-lookup"><span data-stu-id="30814-132">*Game result sample data*</span></span>

<span data-ttu-id="30814-133">Game</span><span class="sxs-lookup"><span data-stu-id="30814-133">Game</span></span> |<span data-ttu-id="30814-134">Gagnant</span><span class="sxs-lookup"><span data-stu-id="30814-134">Winner</span></span> | <span data-ttu-id="30814-135">Perdant</span><span class="sxs-lookup"><span data-stu-id="30814-135">Loser</span></span>
---------|----------|---------
 <span data-ttu-id="30814-136">1</span><span class="sxs-lookup"><span data-stu-id="30814-136">1</span></span> | <span data-ttu-id="30814-137">Joueur 0</span><span class="sxs-lookup"><span data-stu-id="30814-137">Player 0</span></span> | <span data-ttu-id="30814-138">Joueur 1</span><span class="sxs-lookup"><span data-stu-id="30814-138">Player 1</span></span>
 <span data-ttu-id="30814-139">2</span><span class="sxs-lookup"><span data-stu-id="30814-139">2</span></span> | <span data-ttu-id="30814-140">Joueur 0</span><span class="sxs-lookup"><span data-stu-id="30814-140">Player 0</span></span> | <span data-ttu-id="30814-141">Joueur 3</span><span class="sxs-lookup"><span data-stu-id="30814-141">Player 3</span></span>
 <span data-ttu-id="30814-142">3</span><span class="sxs-lookup"><span data-stu-id="30814-142">3</span></span> | <span data-ttu-id="30814-143">Joueur 0</span><span class="sxs-lookup"><span data-stu-id="30814-143">Player 0</span></span> | <span data-ttu-id="30814-144">Joueur 4</span><span class="sxs-lookup"><span data-stu-id="30814-144">Player 4</span></span>
 <span data-ttu-id="30814-145">4</span><span class="sxs-lookup"><span data-stu-id="30814-145">4</span></span> | <span data-ttu-id="30814-146">Joueur 1</span><span class="sxs-lookup"><span data-stu-id="30814-146">Player 1</span></span> | <span data-ttu-id="30814-147">Joueur 2</span><span class="sxs-lookup"><span data-stu-id="30814-147">Player 2</span></span>
 <span data-ttu-id="30814-148">5</span><span class="sxs-lookup"><span data-stu-id="30814-148">5</span></span> | <span data-ttu-id="30814-149">Joueur 3</span><span class="sxs-lookup"><span data-stu-id="30814-149">Player 3</span></span> | <span data-ttu-id="30814-150">Joueur 1</span><span class="sxs-lookup"><span data-stu-id="30814-150">Player 1</span></span>
 <span data-ttu-id="30814-151">6</span><span class="sxs-lookup"><span data-stu-id="30814-151">6</span></span> | <span data-ttu-id="30814-152">Joueur 4</span><span class="sxs-lookup"><span data-stu-id="30814-152">Player 4</span></span> | <span data-ttu-id="30814-153">Joueur 2</span><span class="sxs-lookup"><span data-stu-id="30814-153">Player 2</span></span>

<span data-ttu-id="30814-154">Si l’on examine plus en détail les exemples de données, on remarque que les joueurs 3 et 4 ont tous deux une victoire et une défaite à leur actif.</span><span class="sxs-lookup"><span data-stu-id="30814-154">With a closer look at the sample data, you’ll notice that players 3 and 4 both have one win and one loss.</span></span> <span data-ttu-id="30814-155">Regardons les classements obtenus avec la programmation probabiliste.</span><span class="sxs-lookup"><span data-stu-id="30814-155">Let's see what the rankings look like using probabilistic programming.</span></span> <span data-ttu-id="30814-156">À noter également la présence d’un joueur 0, car on part toujours de zéro dans une tâche de développement.</span><span class="sxs-lookup"><span data-stu-id="30814-156">Notice also there is a player zero because even office match up lists are zero based to us developers.</span></span>

## <a name="write-some-code"></a><span data-ttu-id="30814-157">Écrire du code</span><span class="sxs-lookup"><span data-stu-id="30814-157">Write some code</span></span>

<span data-ttu-id="30814-158">Maintenant que nous avons conçu le modèle, il est temps de l’exprimer sous la forme d’un programme probabiliste à l’aide de l’API de modélisation Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="30814-158">Having designed the model, it’s time to express it as a probabilistic program using the Infer.NET modeling API.</span></span> <span data-ttu-id="30814-159">Ouvrez `Program.cs` dans l’éditeur de texte de votre choix et remplacez tout son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="30814-159">Open `Program.cs` in your favorite text editor and replace all of its contents with the following code:</span></span>

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

## <a name="run-your-app"></a><span data-ttu-id="30814-160">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="30814-160">Run your app</span></span>

<span data-ttu-id="30814-161">Dans votre invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="30814-161">In your command prompt, run the following command:</span></span>

```dotnetcli
dotnet run
```

## <a name="results"></a><span data-ttu-id="30814-162">Résultats</span><span class="sxs-lookup"><span data-stu-id="30814-162">Results</span></span>

<span data-ttu-id="30814-163">Vous devriez obtenir les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="30814-163">Your results should be similar to the following:</span></span>

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

<span data-ttu-id="30814-164">Dans les résultats, on remarque que le joueur 3 est légèrement au-dessus du joueur 4 selon notre modèle.</span><span class="sxs-lookup"><span data-stu-id="30814-164">In the results, notice that player 3 ranks slightly higher than player 4 according to our model.</span></span> <span data-ttu-id="30814-165">Cela s’explique par le fait que la victoire du joueur 3 sur le joueur 1 a plus d’impact que celle du joueur 4 sur le joueur 2 – notons que le joueur 1 bat le joueur 2.</span><span class="sxs-lookup"><span data-stu-id="30814-165">That’s because the victory of player 3 over player 1 is more significant than the victory of player 4 over player 2 – note that player 1 beats player 2.</span></span> <span data-ttu-id="30814-166">Le joueur 0 est le meilleur joueur !</span><span class="sxs-lookup"><span data-stu-id="30814-166">Player 0 is the overall champ!</span></span>

## <a name="keep-learning"></a><span data-ttu-id="30814-167">Continuer à apprendre</span><span class="sxs-lookup"><span data-stu-id="30814-167">Keep learning</span></span>

<span data-ttu-id="30814-168">La conception de modèles statistiques est une compétence à part entière.</span><span class="sxs-lookup"><span data-stu-id="30814-168">Designing statistical models is a skill on its own.</span></span> <span data-ttu-id="30814-169">L’équipe Microsoft Research Cambridge a écrit un [ouvrage en ligne gratuit](http://mbmlbook.com/), qui offre une introduction en douceur à l’article.</span><span class="sxs-lookup"><span data-stu-id="30814-169">The Microsoft Research Cambridge team has written a [free online book](http://mbmlbook.com/), which gives a gentle introduction to the article.</span></span> <span data-ttu-id="30814-170">Le chapitre 3 de ce livre couvre plus en détail le modèle TrueSkill.</span><span class="sxs-lookup"><span data-stu-id="30814-170">Chapter 3 of this book covers the TrueSkill model in more detail.</span></span> <span data-ttu-id="30814-171">Lorsque vous avez un modèle à l’esprit, vous pouvez le transformer en code à l’aide de la [documentation complète](https://dotnet.github.io/infer/) présente sur le site web Infer.NET.</span><span class="sxs-lookup"><span data-stu-id="30814-171">Once you have a model in mind, you can transform it into code using the [extensive documentation](https://dotnet.github.io/infer/) on the Infer.NET website.</span></span>

## <a name="next-steps"></a><span data-ttu-id="30814-172">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="30814-172">Next steps</span></span>

<span data-ttu-id="30814-173">Consultez notre référentiel GitHub Infer.NET pour continuer l’apprentissage et trouver d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="30814-173">Check out the Infer.NET GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="30814-174">Référentiel GitHub dotnet/Infer</span><span class="sxs-lookup"><span data-stu-id="30814-174">dotnet/infer GitHub repository</span></span>](https://github.com/dotnet/infer)
