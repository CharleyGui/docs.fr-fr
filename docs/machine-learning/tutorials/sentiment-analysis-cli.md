---
title: Analyser les sentiments à l’aide de la CLI ML.NET
description: Générer automatiquement un modèle ML et le code C# associé à partir d’un exemple de jeu de données
author: cesardl
ms.author: cesardl
ms.date: 12/23/2019
ms.custom: mvc,mlnet-tooling
ms.topic: tutorial
ms.openlocfilehash: 832124e6d027b240c4d06692ee87c84f57b982d3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243334"
---
# <a name="analyze-sentiment-using-the-mlnet-cli"></a><span data-ttu-id="a1c06-103">Analyser les sentiments à l’aide de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="a1c06-103">Analyze sentiment using the ML.NET CLI</span></span>

<span data-ttu-id="a1c06-104">Découvrez comment utiliser la CLI ML.NET pour générer automatiquement un modèle ML.NET et le code C# sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="a1c06-104">Learn how to use ML.NET CLI to automatically generate an ML.NET model and underlying C# code.</span></span> <span data-ttu-id="a1c06-105">Vous fournissez simplement votre jeu de données et la tâche de machine learning que vous souhaitez implémenter, et la CLI utilise le moteur AutoML pour créer le code source nécessaire à la génération et au déploiement du modèle, ainsi que le modèle binaire.</span><span class="sxs-lookup"><span data-stu-id="a1c06-105">You provide your dataset and the machine learning task you want to implement, and the CLI uses the AutoML engine to create model generation and deployment source code, as well as the binary model.</span></span>

<span data-ttu-id="a1c06-106">Dans ce tutoriel, vous allez effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a1c06-106">In this tutorial, you will do the following steps:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a1c06-107">Préparer vos données pour la tâche de machine learning sélectionnée</span><span class="sxs-lookup"><span data-stu-id="a1c06-107">Prepare your data for the selected machine learning task</span></span>
> - <span data-ttu-id="a1c06-108">Exécuter la commande « mlnet auto-train » à partir de la CLI</span><span class="sxs-lookup"><span data-stu-id="a1c06-108">Run the 'mlnet auto-train' command from the CLI</span></span>
> - <span data-ttu-id="a1c06-109">Examiner les résultats des métriques de la qualité</span><span class="sxs-lookup"><span data-stu-id="a1c06-109">Review the quality metric results</span></span>
> - <span data-ttu-id="a1c06-110">Comprendre le code C# généré nécessaire pour utiliser le modèle dans votre application</span><span class="sxs-lookup"><span data-stu-id="a1c06-110">Understand the generated C# code to use the model in your application</span></span>
> - <span data-ttu-id="a1c06-111">Explorer le code C# généré ayant servi à entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="a1c06-111">Explore the generated C# code that was used to train the model</span></span>

> [!NOTE]
> <span data-ttu-id="a1c06-112">Cette rubrique fait référence à l’outil CLI ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être modifiées.</span><span class="sxs-lookup"><span data-stu-id="a1c06-112">This topic refers to the ML.NET CLI tool, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="a1c06-113">Pour plus d’informations, visitez la page [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="a1c06-113">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="a1c06-114">Intégrée à ML.NET, l’interface CLI ML.NET a pour objectif principal de « démocratiser » ML.NET auprès des développeurs .NET qui débutent avec ML.NET afin de leur éviter d’écrire le code de zéro quand ils commencent.</span><span class="sxs-lookup"><span data-stu-id="a1c06-114">The ML.NET CLI is part of ML.NET and its main goal is to "democratize" ML.NET for .NET developers when learning ML.NET so you don't need to code from scratch to get started.</span></span>

<span data-ttu-id="a1c06-115">Vous pouvez exécuter l’interface CLI ML.NET à partir de n’importe quelle invite de commandes (Windows, Mac ou Linux) et générer ensuite des modèles ML.NET et du code source de qualité sur la base des jeux de données d’entraînement que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="a1c06-115">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) to generate good quality ML.NET models and source code based on training datasets you provide.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="a1c06-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a1c06-116">Pre-requisites</span></span>

- <span data-ttu-id="a1c06-117">[SDK .NET Core 2.2 ](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou version ultérieure</span><span class="sxs-lookup"><span data-stu-id="a1c06-117">[.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) or later</span></span>
- <span data-ttu-id="a1c06-118">(Facultatif) [Visual Studio 2017 ou 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="a1c06-118">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>
- [<span data-ttu-id="a1c06-119">CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="a1c06-119">ML.NET CLI</span></span>](../how-to-guides/install-ml-net-cli.md)

<span data-ttu-id="a1c06-120">Une fois que les projets en C# ont été générés, vous pouvez les exécuter à partir de Visual Studio ou à l’aide de la commande `dotnet run` (CLI .NET Core).</span><span class="sxs-lookup"><span data-stu-id="a1c06-120">You can either run the generated C# code projects from Visual Studio or with `dotnet run` (.NET Core CLI).</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="a1c06-121">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="a1c06-121">Prepare your data</span></span>

<span data-ttu-id="a1c06-122">Nous allons utiliser un jeu de données existant issu d’un scénario « Analyse des sentiments », qui est une tâche de machine learning de classification binaire.</span><span class="sxs-lookup"><span data-stu-id="a1c06-122">We are going to use an existing dataset used for a 'Sentiment Analysis' scenario, which is a binary classification machine learning task.</span></span> <span data-ttu-id="a1c06-123">Vous pouvez utiliser votre propre jeu de données de la même façon, et le modèle et le code seront générés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="a1c06-123">You can use your own dataset in a similar way, and the model and code will be generated for you.</span></span>

1. <span data-ttu-id="a1c06-124">Téléchargez le [fichier zip du jeu de données UCI Sentiment Labeled Sentences (voir les citations dans la remarque ci-dessous)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) et décompressez-le dans un dossier de votre choix.</span><span class="sxs-lookup"><span data-stu-id="a1c06-124">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip it on any folder you choose.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a1c06-125">Les jeux de données utilisés dans ce tutoriel incluent un jeu de données provenant de « From Group to Individual Labels using Deep Features » (Kotzias et al,.</span><span class="sxs-lookup"><span data-stu-id="a1c06-125">The datasets this tutorial uses a dataset from the 'From Group to Individual Labels using Deep Features', Kotzias et al,.</span></span> <span data-ttu-id="a1c06-126">KDD 2015, et hébergé à l’UCI Machine Learning Repository - Dua, D. et Karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="a1c06-126">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="a1c06-127">Référentiel UCI Machine Learning [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="a1c06-127">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="a1c06-128">Irvine, Californie : Université de Californie, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="a1c06-128">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

2. <span data-ttu-id="a1c06-129">Copiez le fichier `yelp_labelled.txt` dans un dossier que vous avez créé précédemment (par exemple, `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="a1c06-129">Copy the `yelp_labelled.txt` file into any folder you previously created (such as `/cli-test`).</span></span>

3. <span data-ttu-id="a1c06-130">Ouvrez votre invite de commandes standard et accédez au dossier où vous avez copié le fichier de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="a1c06-130">Open your preferred command prompt and move to the folder where you copied the dataset file.</span></span> <span data-ttu-id="a1c06-131">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a1c06-131">For example:</span></span>

    ```console
    cd /cli-test
    ```

    <span data-ttu-id="a1c06-132">Utilisez un éditeur de texte comme Visual Studio Code pour ouvrir et explorer le fichier de jeu de données `yelp_labelled.txt`.</span><span class="sxs-lookup"><span data-stu-id="a1c06-132">Using any text editor such as Visual Studio Code, you can open, and explore the `yelp_labelled.txt` dataset file.</span></span> <span data-ttu-id="a1c06-133">Vous voyez que le fichier a cette structure :</span><span class="sxs-lookup"><span data-stu-id="a1c06-133">You can see that the structure is:</span></span>

    - <span data-ttu-id="a1c06-134">Le fichier n’a pas d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="a1c06-134">The file has no header.</span></span> <span data-ttu-id="a1c06-135">Vous utiliserez l’index de colonne.</span><span class="sxs-lookup"><span data-stu-id="a1c06-135">You will use the column's index.</span></span>

    - <span data-ttu-id="a1c06-136">Il y a seulement deux colonnes :</span><span class="sxs-lookup"><span data-stu-id="a1c06-136">There are just two columns:</span></span>

        | <span data-ttu-id="a1c06-137">Texte (index de colonne 0)</span><span class="sxs-lookup"><span data-stu-id="a1c06-137">Text (Column index 0)</span></span> | <span data-ttu-id="a1c06-138">Étiquette (index de colonne 1)</span><span class="sxs-lookup"><span data-stu-id="a1c06-138">Label (Column index 1)</span></span>|
        |--------------------------|-------|
        | <span data-ttu-id="a1c06-139">Wow... J’ai adoré cet endroit.</span><span class="sxs-lookup"><span data-stu-id="a1c06-139">Wow... Loved this place.</span></span> | <span data-ttu-id="a1c06-140">1</span><span class="sxs-lookup"><span data-stu-id="a1c06-140">1</span></span> |
        | <span data-ttu-id="a1c06-141">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="a1c06-141">Crust is not good.</span></span> | <span data-ttu-id="a1c06-142">0</span><span class="sxs-lookup"><span data-stu-id="a1c06-142">0</span></span> |
        | <span data-ttu-id="a1c06-143">Elle n’avait aucun goût et sa texture n’était vraiment pas agréable.</span><span class="sxs-lookup"><span data-stu-id="a1c06-143">Not tasty and the texture was just nasty.</span></span> | <span data-ttu-id="a1c06-144">0</span><span class="sxs-lookup"><span data-stu-id="a1c06-144">0</span></span> |
        | <span data-ttu-id="a1c06-145">...BEAUCOUP D’AUTRES LIGNES DE TEXTE...</span><span class="sxs-lookup"><span data-stu-id="a1c06-145">...MANY MORE TEXT ROWS...</span></span> | <span data-ttu-id="a1c06-146">...(1 ou 0)...</span><span class="sxs-lookup"><span data-stu-id="a1c06-146">...(1 or 0)...</span></span> |

    <span data-ttu-id="a1c06-147">N’oubliez pas de fermer le fichier de jeu dans l’éditeur.</span><span class="sxs-lookup"><span data-stu-id="a1c06-147">Make sure you close the dataset file from the editor.</span></span>

    <span data-ttu-id="a1c06-148">Maintenant, vous êtes prêt à commencer à utiliser la CLI pour ce scénario « Analyse des sentiments ».</span><span class="sxs-lookup"><span data-stu-id="a1c06-148">Now, you are ready to start using the CLI for this 'Sentiment Analysis' scenario.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a1c06-149">Quand vous aurez terminé ce tutoriel, vous pourrez également essayer avec vos propres jeux de données, si ceux-ci ont été préparés en vue d’être utilisés pour les tâches ML prises en charge dans la préversion de la CLI ML.NET, à savoir les tâches *« Classification binaire », « Classification multiclasse » et « Régression »*).</span><span class="sxs-lookup"><span data-stu-id="a1c06-149">After finishing this tutorial you can also try with your own datasets as long as they are ready to be used for any of the ML tasks currently supported by the ML.NET CLI Preview which are *'Binary Classification', 'Multi-class Classification' and 'Regression'*).</span></span>

## <a name="run-the-mlnet-auto-train-command"></a><span data-ttu-id="a1c06-150">Exécuter la commande « mlnet auto-train »</span><span class="sxs-lookup"><span data-stu-id="a1c06-150">Run the 'mlnet auto-train' command</span></span>

1. <span data-ttu-id="a1c06-151">Exécutez la commande CLI ML.NET suivante :</span><span class="sxs-lookup"><span data-stu-id="a1c06-151">Run the following ML.NET CLI command:</span></span>

    ```console
    mlnet auto-train --task binary-classification --dataset "yelp_labelled.txt" --label-column-index 1 --has-header false --max-exploration-time 10
    ```

    <span data-ttu-id="a1c06-152">Cette commande \*\* `mlnet auto-train` \*\*exécute la commande :</span><span class="sxs-lookup"><span data-stu-id="a1c06-152">This command runs the **`mlnet auto-train` command**:</span></span>
    - <span data-ttu-id="a1c06-153">pour une **tâche ML** de type **`binary-classification`**</span><span class="sxs-lookup"><span data-stu-id="a1c06-153">for an **ML task** of type **`binary-classification`**</span></span>
    - <span data-ttu-id="a1c06-154">en utilisant le **fichier de jeu de données `yelp_labelled.txt`** comme jeu de données d’entraînement et de test (en interne, la CLI utilise la validation croisée ou divise le jeu de données initial en deux jeux de données distincts pour l’entraînement et le test)</span><span class="sxs-lookup"><span data-stu-id="a1c06-154">uses the **dataset file `yelp_labelled.txt`** as training and testing dataset (internally the CLI will either use cross-validation or split it in two datasets, one for training and one for testing)</span></span>
    - <span data-ttu-id="a1c06-155">où la **colonne objectif/cible** que vous voulez prédire (généralement appelée **« étiquette »**) est la **colonne d’index 1** (soit la deuxième colonne puisqu’il s’agit ici d’un index de base zéro)</span><span class="sxs-lookup"><span data-stu-id="a1c06-155">where the **objective/target column** you want to predict (commonly called **'label'**) is the **column with index 1** (that is the second column, since the index is zero-based)</span></span>
    - <span data-ttu-id="a1c06-156">qui **n’utilise pas d’en-tête de fichier** avec les noms de colonnes étant donné que ce fichier de jeu de données particulier n’a pas d’en-tête</span><span class="sxs-lookup"><span data-stu-id="a1c06-156">does **not use a file header** with column names since this particular dataset file doesn't have a header</span></span>
    - <span data-ttu-id="a1c06-157">où la **durée d’exploration ciblée** pour l’essai est de **10 secondes**</span><span class="sxs-lookup"><span data-stu-id="a1c06-157">the **targeted exploration time** for the experiment is **10 seconds**</span></span>

    <span data-ttu-id="a1c06-158">La CLI affiche une sortie de ce type :</span><span class="sxs-lookup"><span data-stu-id="a1c06-158">You will see output from the CLI, similar to:</span></span>

    <!-- markdownlint-disable MD023 MD025 -->

    # <a name="windows"></a>[<span data-ttu-id="a1c06-159">Windows</span><span class="sxs-lookup"><span data-stu-id="a1c06-159">Windows</span></span>](#tab/windows)

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-powershell.gif)

    # <a name="macos-bash"></a>[<span data-ttu-id="a1c06-161">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="a1c06-161">macOS Bash</span></span>](#tab/macosbash)

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/mlnet-auto-train-binary-classification-bash.gif)

    <span data-ttu-id="a1c06-163">Dans ce cas particulier, en seulement 10 secondes et avec le petit jeu de données fourni, l’outil CLI a eu le temps d’exécuter plusieurs itérations, ce qui signifie qu’il a effectué plusieurs opérations d’entraînement en essayant diverses combinaisons d’algorithmes/configuration, avec différentes transformations de données internes et différents hyperparamètres d’algorithme.</span><span class="sxs-lookup"><span data-stu-id="a1c06-163">In this particular case, in only 10 seconds and with the small dataset provided, the CLI tool was able to run quite a few iterations, meaning training multiple times based on different combinations of algorithms/configuration with different internal data transformations and algorithm's hyper-parameters.</span></span>

    <span data-ttu-id="a1c06-164">Au final, le modèle de « meilleure qualité » trouvé dans le délai de 10 secondes est un modèle qui utilise un entraîneur/algorithme particulier avec une configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="a1c06-164">Finally, the "best quality" model found in 10 seconds is a model using a particular trainer/algorithm with any specific configuration.</span></span> <span data-ttu-id="a1c06-165">La commande peut produire des résultats variables selon la durée de l’exploration.</span><span class="sxs-lookup"><span data-stu-id="a1c06-165">Depending on the exploration time, the command can produce a different result.</span></span> <span data-ttu-id="a1c06-166">La sélection est basée sur toutes les métriques indiquées, comme `Accuracy`.</span><span class="sxs-lookup"><span data-stu-id="a1c06-166">The selection is based on the multiple metrics shown, such as `Accuracy`.</span></span>

    <span data-ttu-id="a1c06-167">**Comprendre les métriques de qualité du modèle**</span><span class="sxs-lookup"><span data-stu-id="a1c06-167">**Understanding the model's quality metrics**</span></span>

    <span data-ttu-id="a1c06-168">La première métrique, et la plus simple, permettant d’évaluer un modèle de classification binaire est la précision, car elle est facile à comprendre.</span><span class="sxs-lookup"><span data-stu-id="a1c06-168">The first and easiest metric to evaluate a binary-classification model is the accuracy, which is simple to understand.</span></span> <span data-ttu-id="a1c06-169">La précision peut se définir comme la proportion de prédictions correctes avec un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="a1c06-169">"Accuracy is the proportion of correct predictions with a test data set.".</span></span> <span data-ttu-id="a1c06-170">Plus la précision est proche de 100 % (1.00), meilleure est la qualité.</span><span class="sxs-lookup"><span data-stu-id="a1c06-170">The closer to 100% (1.00), the better.</span></span>

    <span data-ttu-id="a1c06-171">Toutefois, dans certains cas, faire une évaluation seulement avec la métrique de précision ne suffit pas, en particulier quand l’étiquette (0 et 1 dans ce cas) n’est pas équilibrée dans le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="a1c06-171">However, there are cases where just measuring with the Accuracy metric is not enough, especially when the label (0 and 1 in this case) is unbalanced in the test dataset.</span></span>

    <span data-ttu-id="a1c06-172">Pour des mesures supplémentaires et des informations plus **détaillées sur les mesures** telles que l’exactitude, l’AUC, l’AUCPR et le score F1 utilisés pour évaluer les différents modèles, voir Comprendre ML.NET les [mesures](../resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="a1c06-172">For additional metrics and more **detailed information about the metrics** such as Accuracy, AUC, AUCPR, and F1-score used to evaluate the different models, see [Understanding ML.NET metrics](../resources/metrics.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="a1c06-173">Vous pouvez essayer ce jeu de données très semblable et définir une durée de quelques minutes pour `--max-exploration-time` (par exemple, spécifiez 180 secondes pour une durée de trois minutes). Cela permet de vous trouver un modèle encore « meilleur », avec une configuration de pipeline d’entraînement différente pour ce jeu de données (qui est très petit, avec 1 000 lignes).</span><span class="sxs-lookup"><span data-stu-id="a1c06-173">You can try this very same dataset and specify a few minutes for `--max-exploration-time` (for instance three minutes so you specify 180 seconds) which will find a better "best model" for you with a different training pipeline configuration for this dataset (which is pretty small, 1000 rows).</span></span>

    <span data-ttu-id="a1c06-174">Si vous souhaitez trouver un modèle de « meilleure/bonne qualité » qui soit un « modèle prêt pour la production » et ciblant des jeux de données plus volumineux, vous devez faire des essais avec la CLI, généralement en spécifiant une durée d’exploration beaucoup plus longue selon la taille du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="a1c06-174">In order to find a "best/good quality" model that is a "production-ready model" targeting larger datasets, you should make experiments with the CLI usually specifying much more exploration time depending on the size of the dataset.</span></span> <span data-ttu-id="a1c06-175">En fait, dans de nombreux cas, vous aurez besoin de spécifier une durée d’exploration de plusieurs heures, d’autant plus si le jeu de données contient beaucoup de lignes et de colonnes.</span><span class="sxs-lookup"><span data-stu-id="a1c06-175">In fact, in many cases you might require multiple hours of exploration time especially if the dataset is large on rows and columns.</span></span>

1. <span data-ttu-id="a1c06-176">L’exécution de la commande précédente a généré les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="a1c06-176">The previous command execution has generated the following assets:</span></span>

    - <span data-ttu-id="a1c06-177">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="a1c06-177">A serialized model .zip ("best model") ready to use.</span></span>
    - <span data-ttu-id="a1c06-178">Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).</span><span class="sxs-lookup"><span data-stu-id="a1c06-178">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
    - <span data-ttu-id="a1c06-179">Le code C# d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage).</span><span class="sxs-lookup"><span data-stu-id="a1c06-179">C# training code used to generate that model (Learning purposes).</span></span>
    - <span data-ttu-id="a1c06-180">Un fichier journal présentant toutes les itérations explorées, avec les détails de chaque algorithme essayé avec sa combinaison d’hyperparamètres et de transformations des données.</span><span class="sxs-lookup"><span data-stu-id="a1c06-180">A log file with all the iterations explored having specific detailed information about each algorithm tried with its combination of hyper-parameters and data transformations.</span></span>

    <span data-ttu-id="a1c06-181">Les deux premières ressources (fichier .zip du modèle et code C# pour exécuter ce modèle) peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.</span><span class="sxs-lookup"><span data-stu-id="a1c06-181">The first two assets (.ZIP file model and C# code to run that model) can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

    <span data-ttu-id="a1c06-182">La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par la CLI pour entraîner le modèle généré. Vous pouvez ainsi savoir quels entraîneur/algorithme et hyperparamètres spécifiques ont été sélectionnés par la CLI.</span><span class="sxs-lookup"><span data-stu-id="a1c06-182">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI.</span></span>

<span data-ttu-id="a1c06-183">Toutes les ressources listées ci-dessus seront décrites dans les étapes suivantes du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="a1c06-183">Those enumerated assets are explained in the following steps of the tutorial.</span></span>

## <a name="explore-the-generated-c-code-to-use-for-running-the-model-to-make-predictions"></a><span data-ttu-id="a1c06-184">Explorer le code C# généré à utiliser pour exécuter le modèle et effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="a1c06-184">Explore the generated C# code to use for running the model to make predictions</span></span>

1. <span data-ttu-id="a1c06-185">Dans Visual Studio (2017 ou 2019), ouvrez la solution générée dans le dossier nommé `SampleBinaryClassification`, situé dans votre dossier de destination d’origine (dans le tutoriel qui s’appelait `/cli-test`).</span><span class="sxs-lookup"><span data-stu-id="a1c06-185">In Visual Studio (2017 or 2019) open the solution generated in the folder named `SampleBinaryClassification` within your original destination folder (in the tutorial was named `/cli-test`).</span></span> <span data-ttu-id="a1c06-186">Vous devez voir une solution similaire à celle-ci :</span><span class="sxs-lookup"><span data-stu-id="a1c06-186">You should see a solution similar to:</span></span>

    > [!NOTE]
    > <span data-ttu-id="a1c06-187">Dans le tutoriel, nous vous suggérons d’utiliser Visual Studio, mais vous pouvez aussi explorer le code C# généré (deux projets) dans n’importe quel éditeur de texte et exécuter ensuite l’application console générée avec `dotnet CLI` sur une machine macOS, Linux ou Windows.</span><span class="sxs-lookup"><span data-stu-id="a1c06-187">In the tutorial we suggest to use Visual Studio, but you can also explore the generated C# code (two projects) with any text editor and run the generated console app with the `dotnet CLI` on macOS, Linux or Windows machine.</span></span>

    ![Solution Visual Studio générée par la CLI](./media/mlnet-cli/generated-csharp-solution-detailed.png)

    - <span data-ttu-id="a1c06-189">Vous pouvez utiliser la **bibliothèque de classes** générée, qui contient le modèle ML sérialisé (fichier .zip) et les classes de données (modèles de données), directement dans votre application utilisateur final, éventuellement en référençant directement cette bibliothèque de classes (ou en déplaçant le code, selon votre préférence).</span><span class="sxs-lookup"><span data-stu-id="a1c06-189">The generated **class library** containing the serialized ML model (.zip file) and the data classes (data models) is something you can directly use in your end-user application, even by directly referencing that class library (or moving the code, as you prefer).</span></span>
    - <span data-ttu-id="a1c06-190">L’**application console** générée contient le code d’exécution que vous devez revoir. Ensuite, vous réutilisez généralement le « score d’évaluation » (code qui exécute le modèle ML pour effectuer des prédictions) en déplaçant ce code simple (de quelques lignes) vers l’application utilisateur où vous souhaitez effectuer les prédictions.</span><span class="sxs-lookup"><span data-stu-id="a1c06-190">The generated **console app** contains execution code that you must review and then you usually reuse the 'scoring code' (code that runs the ML model to make predictions) by moving that simple code (just a few lines) to your end-user application where you want to make the predictions.</span></span>

1. <span data-ttu-id="a1c06-191">Ouvrez les fichiers de classes **ModelInput.cs** et **ModelOutput.cs** dans le projet de bibliothèque de classes.</span><span class="sxs-lookup"><span data-stu-id="a1c06-191">Open the **ModelInput.cs** and **ModelOutput.cs** class files within the class library project.</span></span> <span data-ttu-id="a1c06-192">Vous voyez que ces classes sont les « classes de données » ou les classes POCO où sont stockées les données.</span><span class="sxs-lookup"><span data-stu-id="a1c06-192">You will see that these classes are 'data classes' or POCO classes used to hold data.</span></span> <span data-ttu-id="a1c06-193">Il s’agit de « code réutilisable », qui peut être utile de générer si votre jeu de données contient des dizaines ou des centaines de colonnes.</span><span class="sxs-lookup"><span data-stu-id="a1c06-193">It is 'boilerplate code' but useful to have it generated if your dataset has tens or even hundreds of columns.</span></span>
    - <span data-ttu-id="a1c06-194">La classe `ModelInput` est utilisée pour lire les données du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="a1c06-194">The `ModelInput` class is used when reading data from the dataset.</span></span>
    - <span data-ttu-id="a1c06-195">La classe `ModelOutput` est utilisée pour obtenir le résultat de prédiction (données de prédiction).</span><span class="sxs-lookup"><span data-stu-id="a1c06-195">The `ModelOutput` class is used to get the prediction result (prediction data).</span></span>

1. <span data-ttu-id="a1c06-196">Ouvrez le fichier Program.cs et explorez le code.</span><span class="sxs-lookup"><span data-stu-id="a1c06-196">Open the Program.cs file and explore the code.</span></span> <span data-ttu-id="a1c06-197">Quelques lignes suffisent pour exécuter le modèle et effectuer un exemple de prédiction.</span><span class="sxs-lookup"><span data-stu-id="a1c06-197">In just a few lines, you are able to run the model and make a sample prediction.</span></span>

    ```csharp
    static void Main(string[] args)
    {
        MLContext mlContext = new MLContext();

        // Training code used by ML.NET CLI and AutoML to generate the model
        //ModelBuilder.CreateModel();

        ITransformer mlModel = mlContext.Model.Load(MODEL_FILEPATH, out DataViewSchema inputSchema);
        var predEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // Create sample data to do a single prediction with it
        ModelInput sampleData = CreateSingleDataSample(mlContext, DATA_FILEPATH);

        // Try a single prediction
        ModelOutput predictionResult = predEngine.Predict(sampleData);

        Console.WriteLine($"Single Prediction --> Actual value: {sampleData.Label} | Predicted value: {predictionResult.Prediction}");
    }
    ```

    - <span data-ttu-id="a1c06-198">La première ligne de code crée simplement un objet `MLContext`, qui est nécessaire pour exécuter le code ML.NET.</span><span class="sxs-lookup"><span data-stu-id="a1c06-198">The first line of code simply creates an `MLContext` object needed whenever you run ML.NET code.</span></span>

    - <span data-ttu-id="a1c06-199">La deuxième ligne de code est commentée, car vous n’avez pas besoin d’entraîner le modèle dans la mesure où celui-ci a déjà été entraîné automatiquement par l’outil CLI et enregistré dans le fichier .zip sérialisé du modèle.</span><span class="sxs-lookup"><span data-stu-id="a1c06-199">The second line of code is commented because you don't need to train the model since it was already trained for you by the CLI tool and saved into the model's serialized .ZIP file.</span></span> <span data-ttu-id="a1c06-200">Toutefois, si vous souhaitez afficher les commentaires pour savoir *comment le modèle a été entraîné* par la CLI, vous pouvez décommenter cette ligne et exécuter/déboguer le code d’entraînement utilisé pour ce modèle ML spécifique.</span><span class="sxs-lookup"><span data-stu-id="a1c06-200">But if you want to see *"how the model was trained"* by the CLI, you could uncomment that line and run/debug the training code used for that particular ML model.</span></span>

    - <span data-ttu-id="a1c06-201">Dans la troisième ligne de code, vous chargez le modèle du fichier .zip de modèle sérialisé à l’aide de l’API `mlContext.Model.Load()`, en fournissant le chemin de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="a1c06-201">In the third line of code, you load the model from the serialized model .ZIP file with the `mlContext.Model.Load()` API by providing the path to that model .ZIP file.</span></span>

    - <span data-ttu-id="a1c06-202">Dans la quatrième ligne de code, vous chargez le code pour créer l’objet `PredictionEngine` avec l’API `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)`.</span><span class="sxs-lookup"><span data-stu-id="a1c06-202">In the fourth line of code you load create the `PredictionEngine` object with the `mlContext.Model.CreatePredictionEngine<TSrc,TDst>(ITransformer mlModel)` API.</span></span> <span data-ttu-id="a1c06-203">Vous avez besoin de l’objet `PredictionEngine` chaque fois que vous souhaitez effectuer une prédiction ciblant un exemple de données unique (dans ce cas, un seul élément de texte pour prédire le sentiment).</span><span class="sxs-lookup"><span data-stu-id="a1c06-203">You need the `PredictionEngine` object whenever you want to make a prediction targeting a single sample of data (In this case, a single piece of text to predict its sentiment).</span></span>

    - <span data-ttu-id="a1c06-204">La cinquième ligne de code spécifie où vous créez cet *exemple de données unique* à utiliser pour la prédiction, en appelant la fonction `CreateSingleDataSample()`.</span><span class="sxs-lookup"><span data-stu-id="a1c06-204">The fifth line of code is where you create that *single sample data* to be used for the prediction by calling the function `CreateSingleDataSample()`.</span></span> <span data-ttu-id="a1c06-205">Étant donné que l’outil CLI ne sait pas quel type d’exemple de données utiliser, au sein de cette fonction, il charge la première ligne du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="a1c06-205">Since the CLI tool doesn't know what kind of sample data to use, within that function it is loading the first row of the dataset.</span></span> <span data-ttu-id="a1c06-206">Toutefois, dans ce cas, vous pouvez également créer vos propres données « codées en dur » au lieu de l’implémentation actuelle de la fonction `CreateSingleDataSample()`, en mettant à jour ce code plus simple pour implémenter cette fonction :</span><span class="sxs-lookup"><span data-stu-id="a1c06-206">However, for this case you can also create you own 'hard-coded' data instead of the current implementation of the `CreateSingleDataSample()` function by updating this simpler code implementing that function:</span></span>

        ```csharp
        private static ModelInput CreateSingleDataSample()
        {
            ModelInput sampleForPrediction = new ModelInput() { Col0 = "The ML.NET CLI is great for getting started. Very cool!", Label = true };
            return sampleForPrediction;
        }
        ```

1. <span data-ttu-id="a1c06-207">Exécutez le projet, soit en utilisant l’exemple de données initialement chargé de la première ligne du jeu de données, soit en fournissant votre propre exemple de données personnalisées codées en dur.</span><span class="sxs-lookup"><span data-stu-id="a1c06-207">Run the project, either using the original sample data loaded from the first row of the dataset or by providing your own custom hard-coded sample data.</span></span> <span data-ttu-id="a1c06-208">Vous devez obtenir une prédiction comparable à ceci :</span><span class="sxs-lookup"><span data-stu-id="a1c06-208">You should get a prediction comparable to:</span></span>

    # <a name="windows"></a>[<span data-ttu-id="a1c06-209">Windows</span><span class="sxs-lookup"><span data-stu-id="a1c06-209">Windows</span></span>](#tab/windows)

    <span data-ttu-id="a1c06-210">Exécutez l’application console à partir de Visual Studio en appuyant sur F5 (bouton de lecture) :</span><span class="sxs-lookup"><span data-stu-id="a1c06-210">Run the console app from Visual Studio by hitting F5 (Play button):</span></span>

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/sample-cli-prediction-execution.png)<span data-ttu-id="a1c06-212">)</span><span class="sxs-lookup"><span data-stu-id="a1c06-212">)</span></span>

    # <a name="macos-bash"></a>[<span data-ttu-id="a1c06-213">macOS Bash</span><span class="sxs-lookup"><span data-stu-id="a1c06-213">macOS Bash</span></span>](#tab/macosbash)

    <span data-ttu-id="a1c06-214">Exécutez l’application console à partir de l’invite de commandes en tapant les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a1c06-214">Run the console app from the command-prompt by typing the following commands:</span></span>

    ```dotnetcli
    cd SampleBinaryClassification
    cd SampleBinaryClassification.ConsoleApp

    dotnet run
    ```

    ![Commande auto-train de l’interface CLI ML.NET dans PowerShell](./media/mlnet-cli/sample-cli-prediction-execution-bash.png)<span data-ttu-id="a1c06-216">)</span><span class="sxs-lookup"><span data-stu-id="a1c06-216">)</span></span>

    ---

1. <span data-ttu-id="a1c06-217">Essayez de remplacer l’exemple de données codées en dur par d’autres phrases avec un sentiment différent afin de voir comment le modèle prédit un sentiment positif ou négatif.</span><span class="sxs-lookup"><span data-stu-id="a1c06-217">Try changing the hard-coded sample data to other sentences with different sentiment and see how the model predicts positive or negative sentiment.</span></span>

## <a name="infuse-your-end-user-applications-with-ml-model-predictions"></a><span data-ttu-id="a1c06-218">Intégrer les prédictions de modèle ML à vos applications utilisateur</span><span class="sxs-lookup"><span data-stu-id="a1c06-218">Infuse your end-user applications with ML model predictions</span></span>

<span data-ttu-id="a1c06-219">Vous pouvez utiliser du « code d’évaluation de modèle ML » similaire pour exécuter le modèle dans votre application utilisateur et effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="a1c06-219">You can use similar 'ML model scoring code' to run the model in your end-user application and make predictions.</span></span>

<span data-ttu-id="a1c06-220">Par exemple, déplacez ce code directement vers une application de bureau Windows, comme **WPP** et **WinForms**, puis exécutez le modèle de la même façon que dans l’application console.</span><span class="sxs-lookup"><span data-stu-id="a1c06-220">For instance, you could directly move that code to any Windows desktop application such as **WPF** and **WinForms** and run the model in the same way than it was done in the console app.</span></span>

<span data-ttu-id="a1c06-221">Toutefois, la méthode d’implémentation de ces lignes de code pour exécuter un modèle ML doit être optimisée (notamment en mettant en cache le fichier .zip du modèle et en le chargeant une seule fois) et utiliser des objets singleton au lieu de les créer à chaque requête, en particulier si votre application doit être scalable, à l’image des applications web ou des services distribués, comme nous allons le voir dans la section suivante.</span><span class="sxs-lookup"><span data-stu-id="a1c06-221">However, the way you implement those lines of code to run an ML model should be optimized (that is, cache the model .zip file and load it once) and have singleton objects instead of creating them on every request, especially if your application needs to be scalable such as a web application or distributed service, as explained in the following section.</span></span>

### <a name="running-mlnet-models-in-scalable-aspnet-core-web-apps-and-services-multi-threaded-apps"></a><span data-ttu-id="a1c06-222">Exécuter des modèles ML.NET dans des applications ou services web ASP.NET Core scalables (applications multithread)</span><span class="sxs-lookup"><span data-stu-id="a1c06-222">Running ML.NET models in scalable ASP.NET Core web apps and services (multi-threaded apps)</span></span>

<span data-ttu-id="a1c06-223">La création de l’objet modèle (`ITransformer` chargé d’un fichier .zip de modèle) et de l’objet `PredictionEngine` doit être optimisée, surtout en vue d’une exécution sur des applications web ou des services distribués scalables.</span><span class="sxs-lookup"><span data-stu-id="a1c06-223">The creation of the model object (`ITransformer` loaded from a model's .zip file) and the `PredictionEngine` object should be optimized especially when running on scalable web apps and distributed services.</span></span> <span data-ttu-id="a1c06-224">Pour le premier cas, l’objet modèle (`ITransformer`), l’optimisation est simple.</span><span class="sxs-lookup"><span data-stu-id="a1c06-224">For the first case, the model object (`ITransformer`) the optimization is straightforward.</span></span> <span data-ttu-id="a1c06-225">Dans la mesure où l’objet `ITransformer` est thread-safe, vous pouvez le mettre en cache en tant qu’objet singleton ou statique, afin de charger le modèle une seule fois.</span><span class="sxs-lookup"><span data-stu-id="a1c06-225">Since the `ITransformer` object is thread-safe, you can cache the object as a singleton or static object so you load the model once.</span></span>

<span data-ttu-id="a1c06-226">Pour le deuxième objet, l’objet `PredictionEngine`, l’optimisation n’est pas si facile, car l’objet `PredictionEngine` n’est pas thread-safe. Vous ne pouvez donc pas instancier cet objet en tant qu’objet singleton ou statique dans une application ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1c06-226">For the second object, the `PredictionEngine` object, it is not so easy because the `PredictionEngine` object is not thread-safe, therefore you cannot instantiate this object as singleton or static object in an ASP.NET Core app.</span></span> <span data-ttu-id="a1c06-227">Ce problème est traité en détail dans ce [billet de blog](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="a1c06-227">This thread-safe and scalability problem is deeply discussed in this [Blog Post](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>

<span data-ttu-id="a1c06-228">Toutefois, les choses sont heureusement beaucoup plus simples pour vous que ce qui est expliqué dans ce billet de blog.</span><span class="sxs-lookup"><span data-stu-id="a1c06-228">However, things got a lot easier for you than what's explained in that blog post.</span></span> <span data-ttu-id="a1c06-229">Dans un souci de vous proposer une approche plus simple, nous avons créé un **« package d’intégration .NET Core »** très utile. Vous pouvez facilement vous en servir dans vos applications et services ASP.NET Core en l’inscrivant auprès des services DI, puis en l’utilisant directement à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a1c06-229">We worked on a simpler approach for you and have created a nice **'.NET Core Integration Package'** that you can  easily use in your ASP.NET Core apps and services by registering it in the application DI services (Dependency Injection services) and then directly use it from your code.</span></span> <span data-ttu-id="a1c06-230">Consultez le tutoriel et l’exemple ci-dessous pour savoir comment faire :</span><span class="sxs-lookup"><span data-stu-id="a1c06-230">Check the following tutorial and example for doing that:</span></span>

- [<span data-ttu-id="a1c06-231">Tutorial: Exécution de modèles ML.NET sur des applications Web ASP.NET évolutives et WebAPIs</span><span class="sxs-lookup"><span data-stu-id="a1c06-231">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="a1c06-232">Exemple : Modèle de ML.NET évolutif sur ASP.NET WebAPI de base</span><span class="sxs-lookup"><span data-stu-id="a1c06-232">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)

## <a name="explore-the-generated-c-code-that-was-used-to-train-the-best-quality-model"></a><span data-ttu-id="a1c06-233">Explorer le code C# généré ayant servi à entraîner le modèle de « meilleure qualité »</span><span class="sxs-lookup"><span data-stu-id="a1c06-233">Explore the generated C# code that was used to train the "best quality" model</span></span>

<span data-ttu-id="a1c06-234">Pour approfondir l’apprentissage, vous pouvez également explorer le code C# généré qui a été utilisé par l’outil CLI pour entraîner le modèle généré.</span><span class="sxs-lookup"><span data-stu-id="a1c06-234">For more advanced learning purposes, you can also explore the generated C# code that was used by the CLI tool to train the generated model.</span></span>

<span data-ttu-id="a1c06-235">Ce « code de modèle d’entraînement » est actuellement généré dans la classe personnalisée générée, nommée `ModelBuilder`. Vous pouvez y examiner ce code d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="a1c06-235">That 'training model code' is currently generated in the custom class generated named `ModelBuilder` so you can investigate that training code.</span></span>

<span data-ttu-id="a1c06-236">Plus important encore, pour ce scénario particulier (modèle « Analyse des sentiments »), vous pouvez également comparer ce code d’entraînement généré avec le code décrit dans le tutoriel suivant :</span><span class="sxs-lookup"><span data-stu-id="a1c06-236">More importantly, for this particular scenario (Sentiment Analysis model) you can also compare that generated training code with the code explained in the following tutorial:</span></span>

- <span data-ttu-id="a1c06-237">Comparer: [Tutorial: Utilisez ML.NET dans un scénario de classification binaire d’analyse de sentiment](sentiment-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="a1c06-237">Compare: [Tutorial: Use ML.NET in a sentiment analysis binary classification scenario](sentiment-analysis.md).</span></span>

<span data-ttu-id="a1c06-238">Il est intéressant de comparer la configuration d’algorithme et de pipeline choisie dans le tutoriel avec le code généré par l’outil CLI.</span><span class="sxs-lookup"><span data-stu-id="a1c06-238">It is interesting to compare the chosen algorithm and pipeline configuration in the tutorial with the code generated by the CLI tool.</span></span> <span data-ttu-id="a1c06-239">Selon la durée d’itération et de recherche de meilleurs modèles, l’algorithme choisi peut être différent, tout comme sa configuration d’hyperparamètres et de pipeline.</span><span class="sxs-lookup"><span data-stu-id="a1c06-239">Depending on how much time you spend iterating and searching for better models, the chosen algorithm might be different along with its particular hyper-parameters and pipeline configuration.</span></span>

<span data-ttu-id="a1c06-240">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="a1c06-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="a1c06-241">Préparer vos données pour la tâche ML sélectionnée (problème à résoudre)</span><span class="sxs-lookup"><span data-stu-id="a1c06-241">Prepare your data for the selected ML task (problem to solve)</span></span>
> - <span data-ttu-id="a1c06-242">Exécuter la commande « mlnet auto-train » dans l’outil CLI</span><span class="sxs-lookup"><span data-stu-id="a1c06-242">Run the 'mlnet auto-train' command in the CLI tool</span></span>
> - <span data-ttu-id="a1c06-243">Examiner les résultats des métriques de la qualité</span><span class="sxs-lookup"><span data-stu-id="a1c06-243">Review the quality metric results</span></span>
> - <span data-ttu-id="a1c06-244">Comprendre le code C# généré nécessaire pour exécuter le modèle (code à utiliser dans votre application utilisateur)</span><span class="sxs-lookup"><span data-stu-id="a1c06-244">Understand the generated C# code to run the model (Code to use in your end-user app)</span></span>
> - <span data-ttu-id="a1c06-245">Explorer le code C# généré ayant servi à entraîner le modèle de « meilleure qualité » (à des fins d’apprentissage)</span><span class="sxs-lookup"><span data-stu-id="a1c06-245">Explore the generated C# code that was used to train the "best quality" model (Learning purposes)</span></span>

## <a name="see-also"></a><span data-ttu-id="a1c06-246">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1c06-246">See also</span></span>

- [<span data-ttu-id="a1c06-247">Automatiser l’entraînement du modèle avec la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="a1c06-247">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="a1c06-248">Tutorial: Exécution de modèles ML.NET sur des applications Web ASP.NET évolutives et WebAPIs</span><span class="sxs-lookup"><span data-stu-id="a1c06-248">Tutorial: Running ML.NET models on scalable ASP.NET Core web apps and WebAPIs</span></span>](https://aka.ms/mlnet-tutorial-netcoreintegrationpkg)
- [<span data-ttu-id="a1c06-249">Exemple : Modèle de ML.NET évolutif sur ASP.NET WebAPI de base</span><span class="sxs-lookup"><span data-stu-id="a1c06-249">Sample: Scalable ML.NET model on ASP.NET Core WebAPI</span></span>](https://aka.ms/mlnet-sample-netcoreintegrationpkg)
- [<span data-ttu-id="a1c06-250">Informations de référence sur la commande auto-train de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="a1c06-250">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md)
- [<span data-ttu-id="a1c06-251">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="a1c06-251">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
