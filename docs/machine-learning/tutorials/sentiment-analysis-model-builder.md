---
title: 'Tutorial: Analyser le sentiment - classification binaire'
description: Ce tutoriel vous montre comment créer une application Razor Pages qui classe le sentiment à partir de commentaires sur le site Et prend les mesures appropriées. Le classificateur de sentiment binaire utilise Model Builder dans Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 3419afb36d73599b8fdb0417a8c0cc4057f60089
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187634"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="b6dac-104">Tutorial: Analyser le sentiment des commentaires du site Web dans une application web en utilisant ML.NET Model Builder</span><span class="sxs-lookup"><span data-stu-id="b6dac-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="b6dac-105">Apprenez à analyser le sentiment à partir de commentaires en temps réel à l’intérieur d’une application web.</span><span class="sxs-lookup"><span data-stu-id="b6dac-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="b6dac-106">Ce tutoriel vous montre comment créer une application ASP.NET Core Razor Pages qui classe le sentiment des commentaires du site En temps réel.</span><span class="sxs-lookup"><span data-stu-id="b6dac-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="b6dac-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="b6dac-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b6dac-108">Créez une application ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b6dac-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="b6dac-109">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="b6dac-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="b6dac-110">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="b6dac-110">Choose a scenario</span></span>
> - <span data-ttu-id="b6dac-111">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="b6dac-111">Load the data</span></span>
> - <span data-ttu-id="b6dac-112">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="b6dac-112">Train the model</span></span>
> - <span data-ttu-id="b6dac-113">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="b6dac-113">Evaluate the model</span></span>
> - <span data-ttu-id="b6dac-114">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="b6dac-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="b6dac-115">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="b6dac-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="b6dac-116">Vous pouvez trouver le code source pour ce tutoriel au référentiel [dotnet/machinelearning-échantillons.](https://github.com/dotnet/machinelearning-samples)</span><span class="sxs-lookup"><span data-stu-id="b6dac-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="b6dac-117">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b6dac-117">Pre-requisites</span></span>

<span data-ttu-id="b6dac-118">Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="b6dac-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="b6dac-119">Créer une application Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b6dac-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="b6dac-120">Créez une **application ASP.NET Core Razor Pages**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="b6dac-121">Ouvrez Visual Studio et sélectionnez **File > New > Project** à partir de la barre de menu.</span><span class="sxs-lookup"><span data-stu-id="b6dac-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="b6dac-122">Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#**, suivi du nœud **Web**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="b6dac-123">Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="b6dac-124">Dans la boîte à texte **Name,** tapez "SentimentRazor".</span><span class="sxs-lookup"><span data-stu-id="b6dac-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="b6dac-125">Assurez-vous que **la solution et le projet Place dans le même répertoire** ne sont pas **contrôlés** (VS 2019), ou **que l’annuaire Créer pour la solution** soit **vérifié** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="b6dac-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="b6dac-126">Sélectionnez le bouton **OK.**</span><span class="sxs-lookup"><span data-stu-id="b6dac-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="b6dac-127">Choisissez **l’application Web** dans la fenêtre qui affiche les différents types de projets de base ASP.NET, puis sélectionnez le bouton **OK.**</span><span class="sxs-lookup"><span data-stu-id="b6dac-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="b6dac-128">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="b6dac-128">Prepare and understand the data</span></span>

<span data-ttu-id="b6dac-129">Télécharger [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="b6dac-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="b6dac-130">Lorsque la page Web s’ouvre, cliquez à droite sur la page, sélectionnez **Save As** et enregistrez le fichier n’importe où sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b6dac-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="b6dac-131">Chaque ligne dans le jeu de données *wikipedia-detox-250-line-data.tsv* représente un examen différent laissé par un utilisateur sur Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="b6dac-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="b6dac-132">La première colonne représente le sentiment du texte (0 est non toxique, 1 est toxique), et la deuxième colonne représente le commentaire laissé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6dac-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="b6dac-133">Les colonnes sont séparées par des onglets.</span><span class="sxs-lookup"><span data-stu-id="b6dac-133">The columns are separated by tabs.</span></span> <span data-ttu-id="b6dac-134">Les données ressemblent à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b6dac-134">The data looks like the following:</span></span>

| <span data-ttu-id="b6dac-135">Sentiments</span><span class="sxs-lookup"><span data-stu-id="b6dac-135">Sentiment</span></span> | <span data-ttu-id="b6dac-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="b6dac-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="b6dac-137">1</span><span class="sxs-lookup"><span data-stu-id="b6dac-137">1</span></span> | <span data-ttu-id="b6dac-138">Dude de 'RUDE', vous êtes grossier télécharger cette photo de carl en arrière, ou bien.</span><span class="sxs-lookup"><span data-stu-id="b6dac-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="b6dac-139">1</span><span class="sxs-lookup"><span data-stu-id="b6dac-139">1</span></span> | <span data-ttu-id="b6dac-140">OK !</span><span class="sxs-lookup"><span data-stu-id="b6dac-140">== OK!</span></span> <span data-ttu-id="b6dac-141">IM VA VANDALISER LES SAUVAGES WIKI ALORS!!!</span><span class="sxs-lookup"><span data-stu-id="b6dac-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="b6dac-142">0</span><span class="sxs-lookup"><span data-stu-id="b6dac-142">0</span></span> | <span data-ttu-id="b6dac-143">J’espère que ça aidera.</span><span class="sxs-lookup"><span data-stu-id="b6dac-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="b6dac-144">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="b6dac-144">Choose a scenario</span></span>

![Assistant de constructeur de modèle dans visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="b6dac-146">Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="b6dac-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="b6dac-147">Dans **Solution Explorer**, cliquez à droite sur le projet *SentimentRazor,* et sélectionnez **Add** > Machine**Learning**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="b6dac-148">Pour cet échantillon, le scénario est l’analyse du sentiment.</span><span class="sxs-lookup"><span data-stu-id="b6dac-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="b6dac-149">Dans l’étape du *scénario* de l’outil Model Builder, sélectionnez le scénario **d’analyse de sentiment.**</span><span class="sxs-lookup"><span data-stu-id="b6dac-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="b6dac-150">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="b6dac-150">Load the data</span></span>

<span data-ttu-id="b6dac-151">Model Builder accepte les données de deux sources, une `csv` base `tsv` de données SQL Server ou un fichier local dans ou en format.</span><span class="sxs-lookup"><span data-stu-id="b6dac-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="b6dac-152">Dans l’étape des données de l’outil Model Builder, sélectionnez **Fichier** dans la liste déroulante des sources de données.</span><span class="sxs-lookup"><span data-stu-id="b6dac-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="b6dac-153">Sélectionnez le bouton à côté de la boîte de texte **De fichier Sélectionnez** et utilisez File Explorer pour parcourir et sélectionner le fichier *wikipedia-detox-250-line-data.tsv.*</span><span class="sxs-lookup"><span data-stu-id="b6dac-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="b6dac-154">Choisissez **Sentiment** dans la **colonne pour prédire (label)** dropdown.</span><span class="sxs-lookup"><span data-stu-id="b6dac-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="b6dac-155">Laissez les valeurs par défaut pour le dropdown **des colonnes d’entrée (Caractéristiques).**</span><span class="sxs-lookup"><span data-stu-id="b6dac-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="b6dac-156">Sélectionnez le lien **Train** pour passer à l’étape suivante de l’outil Model Builder.</span><span class="sxs-lookup"><span data-stu-id="b6dac-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="b6dac-157">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="b6dac-157">Train the model</span></span>

<span data-ttu-id="b6dac-158">La tâche d’apprentissage automatique utilisée pour former le modèle d’analyse de sentiment dans ce tutoriel est la classification binaire.</span><span class="sxs-lookup"><span data-stu-id="b6dac-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="b6dac-159">Pendant le processus de formation du modèle, Model Builder forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification binaire pour trouver le modèle le plus performant pour votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="b6dac-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="b6dac-160">Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="b6dac-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="b6dac-161">Model Builder sélectionne automatiquement une valeur par défaut pour **le temps de train (secondes)** en fonction de la taille de votre source de données.</span><span class="sxs-lookup"><span data-stu-id="b6dac-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="b6dac-162">Bien que Model Builder fixe la valeur du **temps de train (secondes)** à 10 secondes, l’augmenter à 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="b6dac-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="b6dac-163">La formation pour une plus longue période de temps permet à Model Builder d’explorer un plus grand nombre d’algorithmes et de combinaison de paramètres à la recherche du meilleur modèle.</span><span class="sxs-lookup"><span data-stu-id="b6dac-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="b6dac-164">Sélectionnez **Commencer l’entraînement**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-164">Select **Start Training**.</span></span>

    <span data-ttu-id="b6dac-165">Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="b6dac-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="b6dac-166">Le champ État affiche l’état d’achèvement du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="b6dac-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="b6dac-167">Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="b6dac-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="b6dac-168">Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="b6dac-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="b6dac-169">Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="b6dac-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="b6dac-170">Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="b6dac-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="b6dac-171">Une fois la formation terminée, sélectionnez le lien **d’évaluation** pour passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="b6dac-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="b6dac-172">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="b6dac-172">Evaluate the model</span></span>

<span data-ttu-id="b6dac-173">Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="b6dac-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="b6dac-174">Dans l’étape d’évaluation de l’outil Model Builder, la section de sortie, contiendra l’algorithme utilisé par le modèle le plus performant dans **l’entrée du meilleur modèle** avec des mesures dans **la meilleure précision du modèle**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="b6dac-175">Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.</span><span class="sxs-lookup"><span data-stu-id="b6dac-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="b6dac-176">Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.</span><span class="sxs-lookup"><span data-stu-id="b6dac-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="b6dac-177">Dans le cas contraire, sélectionnez le lien **de code** pour passer à l’étape finale de l’outil Model Builder.</span><span class="sxs-lookup"><span data-stu-id="b6dac-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="b6dac-178">Ajouter le code pour effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="b6dac-178">Add the code to make predictions</span></span>

<span data-ttu-id="b6dac-179">Deux projets sont créés à la suite du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="b6dac-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="b6dac-180">Référence au modèle formé</span><span class="sxs-lookup"><span data-stu-id="b6dac-180">Reference the trained model</span></span>

1. <span data-ttu-id="b6dac-181">Dans l’étape *de code* de l’outil Model Builder, sélectionnez Ajouter **des projets** pour ajouter les projets autogénérés à la solution.</span><span class="sxs-lookup"><span data-stu-id="b6dac-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="b6dac-182">Les projets suivants devraient apparaître dans la **Solution Explorer**:</span><span class="sxs-lookup"><span data-stu-id="b6dac-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="b6dac-183">*SentimentRazorML.ConsoleApp*: Une application .NET Core Console qui contient le modèle de formation et de code de prédiction.</span><span class="sxs-lookup"><span data-stu-id="b6dac-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="b6dac-184">*SentimentRazorML.Model*: Une bibliothèque de classe standard .NET contenant les modèles de données qui définissent le schéma des données des modèles d’entrée et de sortie ainsi que la version enregistrée du modèle le plus performant pendant la formation.</span><span class="sxs-lookup"><span data-stu-id="b6dac-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="b6dac-185">Pour ce tutoriel, seul le projet *SentimentRazorML.Model* est utilisé parce que les prédictions seront faites dans *l’application Web SentimentRazor* plutôt que dans la console.</span><span class="sxs-lookup"><span data-stu-id="b6dac-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="b6dac-186">Bien que le *SentimentRazorML.ConsoleApp* ne sera pas utilisé pour la notation, il peut être utilisé pour recycler le modèle à l’aide de nouvelles données à une date ultérieure.</span><span class="sxs-lookup"><span data-stu-id="b6dac-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="b6dac-187">Le recyclage est en dehors de la portée de ce tutoriel si.</span><span class="sxs-lookup"><span data-stu-id="b6dac-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="b6dac-188">Configurer la piscine PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="b6dac-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="b6dac-189">Pour faire une seule prédiction, [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)vous devez créer un .</span><span class="sxs-lookup"><span data-stu-id="b6dac-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="b6dac-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil.</span><span class="sxs-lookup"><span data-stu-id="b6dac-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="b6dac-191">En outre, vous devez créer une instance de celui-ci partout où il est nécessaire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="b6dac-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="b6dac-192">Au fur et à mesure que votre application se développe, ce processus peut devenir ingérable.</span><span class="sxs-lookup"><span data-stu-id="b6dac-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="b6dac-193">Pour améliorer les performances et la sécurité des `PredictionEnginePool` fils, utilisez [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) une combinaison d’injection de dépendance et le service, qui crée un des objets à utiliser tout au long de votre application.</span><span class="sxs-lookup"><span data-stu-id="b6dac-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="b6dac-194">Installer le *paquet nuGet Microsoft.Extensions.ML* :</span><span class="sxs-lookup"><span data-stu-id="b6dac-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="b6dac-195">Dans **Solution Explorer**, cliquez à droite sur le projet et sélectionnez Manage **NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="b6dac-196">Choisissez «nuget.org» comme source de paquet.</span><span class="sxs-lookup"><span data-stu-id="b6dac-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="b6dac-197">Sélectionnez l’onglet **Parcourir** et recherchez **Microsoft.Extensions.ML**.</span><span class="sxs-lookup"><span data-stu-id="b6dac-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="b6dac-198">Sélectionnez le paquet dans la liste et sélectionnez le bouton **Installer.**</span><span class="sxs-lookup"><span data-stu-id="b6dac-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="b6dac-199">Sélectionnez le bouton **OK** sur le dialogue **de preview Changes**</span><span class="sxs-lookup"><span data-stu-id="b6dac-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="b6dac-200">Sélectionnez le bouton **I Accept** sur le dialogue **d’acceptation de licence** si vous êtes d’accord avec les conditions de licence pour les paquets énumérés.</span><span class="sxs-lookup"><span data-stu-id="b6dac-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="b6dac-201">Ouvrez le fichier *Startup.cs* dans le projet *SentimentRazor.*</span><span class="sxs-lookup"><span data-stu-id="b6dac-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="b6dac-202">Ajoutez les instructions suivantes à l’aide des *instructions pour référencer* le Microsoft.Extensions.ML paquet NuGet et le projet *SentimentRazorML.Model* :</span><span class="sxs-lookup"><span data-stu-id="b6dac-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="b6dac-203">Créez une variable globale pour stocker l’emplacement du fichier modèle formé.</span><span class="sxs-lookup"><span data-stu-id="b6dac-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="b6dac-204">Le fichier modèle est stocké dans l’annuaire de construction aux côtés des fichiers d’assemblage de votre application.</span><span class="sxs-lookup"><span data-stu-id="b6dac-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="b6dac-205">Pour faciliter l’accès, créez une `GetAbsolutePath` méthode `Configure` d’aide appelée après la méthode</span><span class="sxs-lookup"><span data-stu-id="b6dac-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="b6dac-206">Utilisez `GetAbsolutePath` la méthode `Startup` dans le constructeur `_modelPath`de classe pour définir le .</span><span class="sxs-lookup"><span data-stu-id="b6dac-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="b6dac-207">Configurez `PredictionEnginePool` le pour `ConfigureServices` votre application dans la méthode :</span><span class="sxs-lookup"><span data-stu-id="b6dac-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="b6dac-208">Créer un gestionnaire d’analyse de sentiment</span><span class="sxs-lookup"><span data-stu-id="b6dac-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="b6dac-209">Les prédictions seront faites à l’intérieur de la page principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="b6dac-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="b6dac-210">Par conséquent, une méthode qui prend `PredictionEnginePool` l’entrée de l’utilisateur et utilise le pour retourner une prédiction doit être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="b6dac-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="b6dac-211">Ouvrez le fichier *Index.cshtml.cs* situé dans l’annuaire *Pages* et ajoutez les instructions suivantes à l’aide de relevés :</span><span class="sxs-lookup"><span data-stu-id="b6dac-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="b6dac-212">Afin d’utiliser `PredictionEnginePool` le configuré dans la `Startup` classe, vous devez l’injecter dans le constructeur du modèle où vous souhaitez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="b6dac-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="b6dac-213">Ajoutez une variable `PredictionEnginePool` pour `IndexModel` référencer l’intérieur de la classe.</span><span class="sxs-lookup"><span data-stu-id="b6dac-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="b6dac-214">Créez un constructeur `IndexModel` dans la `PredictionEnginePool` classe et injectez le service en elle.</span><span class="sxs-lookup"><span data-stu-id="b6dac-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="b6dac-215">Créez un gestionnaire de `PredictionEnginePool` méthode qui utilise les prédictions à partir des entrées de l’utilisateur reçues de la page Web.</span><span class="sxs-lookup"><span data-stu-id="b6dac-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="b6dac-216">Ci-dessous la `OnGet` méthode, créez une nouvelle méthode appelée`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="b6dac-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="b6dac-217">À `OnGetAnalyzeSentiment` l’intérieur de la méthode, retourner *sentiment neutre* si l’entrée de l’utilisateur est vide ou nul.</span><span class="sxs-lookup"><span data-stu-id="b6dac-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="b6dac-218">Compte tenu d’une entrée `ModelInput`valide, créez une nouvelle instance de .</span><span class="sxs-lookup"><span data-stu-id="b6dac-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="b6dac-219">Utilisez `PredictionEnginePool` le pour prédire le sentiment.</span><span class="sxs-lookup"><span data-stu-id="b6dac-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="b6dac-220">Convertir la `bool` valeur prévue en toxique ou non toxique avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b6dac-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="b6dac-221">Enfin, retournez le sentiment à la page web.</span><span class="sxs-lookup"><span data-stu-id="b6dac-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="b6dac-222">Configurer la page Web</span><span class="sxs-lookup"><span data-stu-id="b6dac-222">Configure the web page</span></span>

<span data-ttu-id="b6dac-223">Les résultats retournés par le `OnGetAnalyzeSentiment` seront `Index` affichés dynamiquement sur la page web.</span><span class="sxs-lookup"><span data-stu-id="b6dac-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="b6dac-224">Ouvrez le fichier *Index.cshtml* dans l’annuaire *Pages* et remplacez son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b6dac-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="b6dac-225">Ensuite, ajoutez du code de style css à la fin de la page *site.css* dans le répertoire *wwwroot-css* :</span><span class="sxs-lookup"><span data-stu-id="b6dac-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="b6dac-226">Après cela, ajoutez du code pour envoyer `OnGetAnalyzeSentiment` des entrées de la page Web au gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="b6dac-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="b6dac-227">Dans le fichier *site.js* situé dans *l’annuaire wwwroot-js,* créez une fonction appelée `getSentiment` `OnGetAnalyzeSentiment` pour faire une demande GET HTTP avec l’entrée de l’utilisateur au gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="b6dac-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="b6dac-228">Ci-dessous, ajouter `updateMarker` une autre fonction appelée à mettre à jour dynamiquement la position du marqueur sur la page Web que le sentiment est prédit.</span><span class="sxs-lookup"><span data-stu-id="b6dac-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="b6dac-229">Créez une fonction `updateSentiment` de gestionnaire d’événements appelée pour `OnGetAnalyzeSentiment` obtenir l’entrée de l’utilisateur, envoyez-la à la fonction en utilisant la `getSentiment` fonction et mettez à jour le marqueur avec la `updateMarker` fonction.</span><span class="sxs-lookup"><span data-stu-id="b6dac-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="b6dac-230">Enfin, enregistrez le gestionnaire d’événements et liez-le à l’élément `textarea` avec l’attribut. `id=Message`</span><span class="sxs-lookup"><span data-stu-id="b6dac-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="b6dac-231">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="b6dac-231">Run the application</span></span>

<span data-ttu-id="b6dac-232">Maintenant que votre application est configuré, exécutez l’application qui doit être lancée dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="b6dac-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="b6dac-233">Lorsque l’application est lancée, entrez *Model Builder est cool!*</span><span class="sxs-lookup"><span data-stu-id="b6dac-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="b6dac-234">dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="b6dac-234">into the text area.</span></span> <span data-ttu-id="b6dac-235">Le sentiment prévu affiché ne doit pas être *toxique*.</span><span class="sxs-lookup"><span data-stu-id="b6dac-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Fenêtre de course avec la fenêtre de sentiment prévue](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="b6dac-237">Si vous avez besoin de référencer les projets générés par Le `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` constructeur modèle à une date ultérieure à l’intérieur d’une autre solution, vous pouvez les trouver à l’intérieur de l’annuaire.</span><span class="sxs-lookup"><span data-stu-id="b6dac-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6dac-238">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b6dac-238">Next steps</span></span>

<span data-ttu-id="b6dac-239">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="b6dac-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="b6dac-240">Créez une application ASP.NET Core Razor Pages</span><span class="sxs-lookup"><span data-stu-id="b6dac-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="b6dac-241">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="b6dac-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="b6dac-242">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="b6dac-242">Choose a scenario</span></span>
> - <span data-ttu-id="b6dac-243">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="b6dac-243">Load the data</span></span>
> - <span data-ttu-id="b6dac-244">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="b6dac-244">Train the model</span></span>
> - <span data-ttu-id="b6dac-245">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="b6dac-245">Evaluate the model</span></span>
> - <span data-ttu-id="b6dac-246">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="b6dac-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b6dac-247">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b6dac-247">Additional Resources</span></span>

<span data-ttu-id="b6dac-248">Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6dac-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="b6dac-249">Scénarios du Générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="b6dac-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="b6dac-250">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="b6dac-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="b6dac-251">Mesures du modèle de classification binaire</span><span class="sxs-lookup"><span data-stu-id="b6dac-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
