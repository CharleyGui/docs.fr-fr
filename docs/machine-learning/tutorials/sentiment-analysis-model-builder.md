---
title: 'Tutoriel : Analyser le sentiment-classification binaire'
description: Ce didacticiel vous montre comment créer une application Razor Pages qui classe les sentiments à partir de commentaires de site Web et prend les mesures appropriées. Le classifieur de sentiment binaire utilise le générateur de modèles dans Visual Studio.
ms.date: 09/26/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 0878a9318e7c60be29eeac9fb4efd47e408ab660
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332580"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="def68-104">Tutoriel : Analyser les sentiments des commentaires de site Web dans une application Web à l’aide du générateur de modèles ML.NET</span><span class="sxs-lookup"><span data-stu-id="def68-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="def68-105">Découvrez comment analyser les sentiments de commentaires en temps réel dans une application Web.</span><span class="sxs-lookup"><span data-stu-id="def68-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="def68-106">Ce didacticiel vous montre comment créer une application ASP.NET Core Razor Pages qui classe les sentiments à partir de commentaires de site Web en temps réel.</span><span class="sxs-lookup"><span data-stu-id="def68-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="def68-107">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="def68-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="def68-108">Créer une application de Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="def68-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="def68-109">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="def68-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="def68-110">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="def68-110">Choose a scenario</span></span>
> - <span data-ttu-id="def68-111">Charger les données</span><span class="sxs-lookup"><span data-stu-id="def68-111">Load the data</span></span>
> - <span data-ttu-id="def68-112">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="def68-112">Train the model</span></span>
> - <span data-ttu-id="def68-113">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="def68-113">Evaluate the model</span></span>
> - <span data-ttu-id="def68-114">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="def68-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="def68-115">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="def68-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="def68-116">Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="def68-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="def68-117">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="def68-117">Pre-requisites</span></span>

<span data-ttu-id="def68-118">Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="def68-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="def68-119">Créer une application Razor Pages</span><span class="sxs-lookup"><span data-stu-id="def68-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="def68-120">Créer une **application de Razor Pages ASP.net Core**.</span><span class="sxs-lookup"><span data-stu-id="def68-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="def68-121">Ouvrez Visual Studio et sélectionnez **fichier > nouveau > projet** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="def68-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="def68-122">Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#** , suivi du nœud **Web**.</span><span class="sxs-lookup"><span data-stu-id="def68-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="def68-123">Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="def68-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="def68-124">Dans la zone de texte **nom** , tapez « SentimentRazor ».</span><span class="sxs-lookup"><span data-stu-id="def68-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="def68-125">La case à cocher **créer un répertoire pour la solution** doit être activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="def68-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="def68-126">Si ce n’est pas le cas, vérifiez-le.</span><span class="sxs-lookup"><span data-stu-id="def68-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="def68-127">Sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="def68-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="def68-128">Choisissez **application Web** dans la fenêtre qui affiche les différents types de ASP.net Core projets, puis cliquez sur le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="def68-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="def68-129">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="def68-129">Prepare and understand the data</span></span>

<span data-ttu-id="def68-130">Téléchargez le [jeu de données Detox Wikipédia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="def68-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="def68-131">Lorsque la page Web s’ouvre, cliquez avec le bouton droit sur la page, sélectionnez **Enregistrer sous** , puis enregistrez le fichier sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="def68-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="def68-132">Chaque ligne du jeu de données *Wikipédia-Detox-250-Line-Data. TSV* représente une révision différente laissée par un utilisateur sur Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="def68-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="def68-133">La première colonne représente le sentiment du texte (0 est non toxique, 1 est toxique) et la deuxième colonne représente le commentaire laissé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="def68-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="def68-134">Les colonnes sont séparées par des tabulations.</span><span class="sxs-lookup"><span data-stu-id="def68-134">The columns are separated by tabs.</span></span> <span data-ttu-id="def68-135">Les données ressemblent à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="def68-135">The data looks like the following:</span></span>

| <span data-ttu-id="def68-136">Sentiment</span><span class="sxs-lookup"><span data-stu-id="def68-136">Sentiment</span></span> | <span data-ttu-id="def68-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="def68-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="def68-138">1</span><span class="sxs-lookup"><span data-stu-id="def68-138">1</span></span> | <span data-ttu-id="def68-139">= = IMPROPRE = = dude, vous êtes très impropre à charger cette image Carl, ou autre.</span><span class="sxs-lookup"><span data-stu-id="def68-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="def68-140">1</span><span class="sxs-lookup"><span data-stu-id="def68-140">1</span></span> | <span data-ttu-id="def68-141">= = OK !</span><span class="sxs-lookup"><span data-stu-id="def68-141">== OK!</span></span> <span data-ttu-id="def68-142">= = IM VA SE RENDRE COMPTE DU WIKI SAUVAGE, !!!</span><span class="sxs-lookup"><span data-stu-id="def68-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="def68-143">0</span><span class="sxs-lookup"><span data-stu-id="def68-143">0</span></span> | <span data-ttu-id="def68-144">J’espère que cela vous aidera.</span><span class="sxs-lookup"><span data-stu-id="def68-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="def68-145">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="def68-145">Choose a scenario</span></span>

![Assistant Générateur de modèles dans Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="def68-147">Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="def68-147">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="def68-148">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet *SentimentRazor* , puis sélectionnez **Ajouter** > un**machine learning**.</span><span class="sxs-lookup"><span data-stu-id="def68-148">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="def68-149">Pour cet exemple, le scénario est l’analyse de sentiments.</span><span class="sxs-lookup"><span data-stu-id="def68-149">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="def68-150">Dans l’étape de *scénario* de l’outil générateur de modèles, sélectionnez le scénario **analyse des sentiments** .</span><span class="sxs-lookup"><span data-stu-id="def68-150">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="def68-151">Charger les données</span><span class="sxs-lookup"><span data-stu-id="def68-151">Load the data</span></span>

<span data-ttu-id="def68-152">Le générateur de modèles accepte les données de deux sources, une base de données SQL Server `csv` ou `tsv` un fichier local au format ou.</span><span class="sxs-lookup"><span data-stu-id="def68-152">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="def68-153">Dans l’étape des données de l’outil Model Builder, sélectionnez **Fichier** dans la liste déroulante des sources de données.</span><span class="sxs-lookup"><span data-stu-id="def68-153">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="def68-154">Sélectionnez le bouton en regard de la zone de texte **Sélectionner un fichier** et utilisez l’Explorateur de fichiers pour parcourir et sélectionner le fichier *Wikipédia-Detox-250-Line-Data. TSV* .</span><span class="sxs-lookup"><span data-stu-id="def68-154">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="def68-155">Choisissez **sentiments** dans la liste déroulante **colonne à prédire (étiquette)** .</span><span class="sxs-lookup"><span data-stu-id="def68-155">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="def68-156">Laissez les valeurs par défaut pour la liste déroulante **colonnes d’entrée (fonctionnalités)** .</span><span class="sxs-lookup"><span data-stu-id="def68-156">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="def68-157">Sélectionnez le lien **former** pour passer à l’étape suivante dans l’outil générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="def68-157">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="def68-158">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="def68-158">Train the model</span></span>

<span data-ttu-id="def68-159">La tâche de Machine Learning utilisée pour l’apprentissage du modèle de prédiction de prix dans ce didacticiel est la classification binaire.</span><span class="sxs-lookup"><span data-stu-id="def68-159">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="def68-160">Pendant le processus d’apprentissage du modèle, le générateur de modèles forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification binaire pour trouver le modèle le plus performant pour votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="def68-160">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="def68-161">Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="def68-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="def68-162">Le générateur de modèles sélectionne automatiquement une valeur par défaut pour le **temps de formation (en secondes)** en fonction de la taille de votre source de données.</span><span class="sxs-lookup"><span data-stu-id="def68-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="def68-163">Bien que le générateur de modèles définisse la valeur de **temps à former (secondes)** à 10 secondes, augmentez-le à 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="def68-163">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="def68-164">La formation sur une période plus longue permet au générateur de modèles d’explorer un plus grand nombre d’algorithmes et une combinaison de paramètres dans la recherche du meilleur modèle.</span><span class="sxs-lookup"><span data-stu-id="def68-164">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="def68-165">Sélectionnez **Commencer l’entraînement**.</span><span class="sxs-lookup"><span data-stu-id="def68-165">Select **Start Training**.</span></span>

    <span data-ttu-id="def68-166">Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="def68-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="def68-167">Le champ État affiche l’état d’achèvement du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="def68-167">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="def68-168">Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="def68-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="def68-169">Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="def68-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="def68-170">Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="def68-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="def68-171">Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="def68-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="def68-172">Une fois l’apprentissage terminé, sélectionnez le lien **évaluer** pour passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="def68-172">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="def68-173">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="def68-173">Evaluate the model</span></span>

<span data-ttu-id="def68-174">Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="def68-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="def68-175">Dans l’étape d’évaluation de l’outil Model Builder, la section de la sortie contient l’algorithme utilisé par le modèle le plus performant dans l’entrée **Meilleur modèle** ainsi que des métriques dans **Meilleure qualité du modèle (RSquared)** .</span><span class="sxs-lookup"><span data-stu-id="def68-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Quality (RSquared)**.</span></span> <span data-ttu-id="def68-176">Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.</span><span class="sxs-lookup"><span data-stu-id="def68-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="def68-177">Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.</span><span class="sxs-lookup"><span data-stu-id="def68-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="def68-178">Dans le cas contraire, sélectionnez le lien de **code** pour passer à l’étape finale de l’outil générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="def68-178">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="def68-179">Ajouter le code pour effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="def68-179">Add the code to make predictions</span></span>

<span data-ttu-id="def68-180">Deux projets sont créés à la suite du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="def68-180">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="def68-181">Référencer le modèle formé</span><span class="sxs-lookup"><span data-stu-id="def68-181">Reference the trained model</span></span>

1. <span data-ttu-id="def68-182">Dans l’étape de *code* de l’outil générateur de modèles, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.</span><span class="sxs-lookup"><span data-stu-id="def68-182">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="def68-183">Les projets suivants doivent apparaître dans le **Explorateur de solutions**:</span><span class="sxs-lookup"><span data-stu-id="def68-183">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="def68-184">*SentimentRazorML. ConsoleApp*: Application console .NET Core qui contient l’apprentissage du modèle et le code de prédiction.</span><span class="sxs-lookup"><span data-stu-id="def68-184">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="def68-185">*SentimentRazorML. Model*: Bibliothèque de classes .NET Standard contenant les modèles de données qui définissent le schéma des données de modèle d’entrée et de sortie ainsi que la version enregistrée du modèle le plus performant au cours de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="def68-185">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="def68-186">Pour ce didacticiel, seul le projet *SentimentRazorML. Model* est utilisé, car les prédictions sont effectuées dans l’application Web *SentimentRazor* plutôt que dans la console.</span><span class="sxs-lookup"><span data-stu-id="def68-186">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="def68-187">Bien que *SentimentRazorML. ConsoleApp* ne soit pas utilisé pour le calcul de score, il peut être utilisé pour reformer le modèle à l’aide de nouvelles données ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="def68-187">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="def68-188">Toutefois, la reformation n’entre pas dans le cadre de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="def68-188">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="def68-189">Configurer le pool PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="def68-189">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="def68-190">Pour effectuer une prédiction unique, vous devez créer un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="def68-190">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="def68-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="def68-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="def68-192">En outre, vous devez créer une instance de celle-ci partout où elle est nécessaire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="def68-192">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="def68-193">À mesure que votre application croît, ce processus peut devenir non gérable.</span><span class="sxs-lookup"><span data-stu-id="def68-193">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="def68-194">Pour améliorer les performances et la sécurité des threads, utilisez une combinaison d’injection de dépendances et le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="def68-194">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="def68-195">Installez le package NuGet *Microsoft.extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="def68-195">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="def68-196">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="def68-196">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="def68-197">Choisissez « nuget.org » comme source du package.</span><span class="sxs-lookup"><span data-stu-id="def68-197">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="def68-198">Sélectionnez l’onglet **Parcourir** et recherchez **Microsoft.extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="def68-198">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="def68-199">Sélectionnez le package dans la liste, puis cliquez sur le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="def68-199">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="def68-200">Sélectionnez le bouton **OK** dans la boîte de dialogue **aperçu des modifications**</span><span class="sxs-lookup"><span data-stu-id="def68-200">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="def68-201">Sélectionnez le bouton **J’accepte** dans la boîte de dialogue acceptation de la **licence** si vous acceptez les termes du contrat de licence pour les packages listés.</span><span class="sxs-lookup"><span data-stu-id="def68-201">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="def68-202">Ouvrez le fichier *Startup.cs* dans le projet *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="def68-202">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="def68-203">Ajoutez les instructions using suivantes pour référencer le package NuGet *Microsoft.extensions.ml* et le projet *SentimentRazorML. Model* :</span><span class="sxs-lookup"><span data-stu-id="def68-203">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L12-L14)]

1. <span data-ttu-id="def68-204">Créez une variable globale pour stocker l’emplacement du fichier de modèle formé.</span><span class="sxs-lookup"><span data-stu-id="def68-204">Create a global variable to store the location of the trained model file.</span></span>

    [!code-csharp [ModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L20)]

1. <span data-ttu-id="def68-205">Le fichier de modèle est stocké dans le répertoire de build en même temps que les fichiers d’assembly de votre application.</span><span class="sxs-lookup"><span data-stu-id="def68-205">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="def68-206">Pour faciliter l’accès à, créez une méthode d’assistance appelée `GetAbsolutePath` après la `Configure` méthode.</span><span class="sxs-lookup"><span data-stu-id="def68-206">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    [!code-csharp [GetAbsolutePathMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L66-L73)]

1. <span data-ttu-id="def68-207">Utilisez la `GetAbsolutePath` méthode dans le `Startup` constructeur de `_modelPath`classe pour définir.</span><span class="sxs-lookup"><span data-stu-id="def68-207">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    [!code-csharp [InitModelPath](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L25)]

1. <span data-ttu-id="def68-208">Configurez `ConfigureServices`pourvotre application dans la méthode : `PredictionEnginePool`</span><span class="sxs-lookup"><span data-stu-id="def68-208">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    [!code-csharp [InitPredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Startup.cs#L42)]

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="def68-209">Créer un gestionnaire d’analyse de sentiments</span><span class="sxs-lookup"><span data-stu-id="def68-209">Create sentiment analysis handler</span></span>

<span data-ttu-id="def68-210">Les prédictions sont effectuées à l’intérieur de la page principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="def68-210">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="def68-211">Par conséquent, une méthode qui prend l’entrée utilisateur et utilise `PredictionEnginePool` pour retourner une prédiction doit être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="def68-211">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="def68-212">Ouvrez le fichier *index.cshtml.cs* situé dans le répertoire *pages* et ajoutez les instructions using suivantes :</span><span class="sxs-lookup"><span data-stu-id="def68-212">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    [!code-csharp [IndexUsings](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L7-L8)]

    <span data-ttu-id="def68-213">Pour utiliser le `PredictionEnginePool` configuré dans la `Startup` classe, vous devez l’injecter dans le constructeur du modèle où vous souhaitez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="def68-213">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="def68-214">Ajoutez une variable pour référencer `PredictionEnginePool` à l' `IndexModel` intérieur de la classe.</span><span class="sxs-lookup"><span data-stu-id="def68-214">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    [!code-csharp [PredEnginePool](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L14)]

1. <span data-ttu-id="def68-215">Créez un constructeur dans la `IndexModel` classe et injectez `PredictionEnginePool` le service dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="def68-215">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    [!code-csharp [IndexConstructor](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L16-L19)]

1. <span data-ttu-id="def68-216">Créez un gestionnaire de méthode qui utilise `PredictionEnginePool` pour effectuer des prédictions à partir de l’entrée utilisateur reçue de la page Web.</span><span class="sxs-lookup"><span data-stu-id="def68-216">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="def68-217">Sous la `OnGet` méthode, créez une nouvelle méthode appelée`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="def68-217">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="def68-218">À l' `OnGetAnalyzeSentiment` intérieur de la méthode, retournez un sentiment *neutre* si l’entrée de l’utilisateur est vide ou null.</span><span class="sxs-lookup"><span data-stu-id="def68-218">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L28)]

    1. <span data-ttu-id="def68-219">En fonction d’une entrée valide, créez une nouvelle `ModelInput`instance de.</span><span class="sxs-lookup"><span data-stu-id="def68-219">Given a valid input, create a new instance of `ModelInput`.</span></span>

        [!code-csharp [InitInput](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L29)]

    1. <span data-ttu-id="def68-220">Utilisez pour `PredictionEnginePool` prédire le sentiment.</span><span class="sxs-lookup"><span data-stu-id="def68-220">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        [!code-csharp [MakePrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L30)]

    1. <span data-ttu-id="def68-221">Convertissez la `bool` valeur prédite en toxique ou non toxique avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="def68-221">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        [!code-csharp [ConvertPrediction](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L31)]

    1. <span data-ttu-id="def68-222">Enfin, retournez le sentiment à la page Web.</span><span class="sxs-lookup"><span data-stu-id="def68-222">Finally, return the sentiment back to the web page.</span></span>

        [!code-csharp [ReturnSentiment](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml.cs#L32)]

### <a name="configure-the-web-page"></a><span data-ttu-id="def68-223">Configurer la page Web</span><span class="sxs-lookup"><span data-stu-id="def68-223">Configure the web page</span></span>

<span data-ttu-id="def68-224">Les résultats retournés `OnGetAnalyzeSentiment` par le s’affichent dynamiquement `Index` sur la page Web.</span><span class="sxs-lookup"><span data-stu-id="def68-224">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="def68-225">Ouvrez le fichier *index. cshtml* dans le répertoire *pages* et remplacez son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="def68-225">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="def68-226">Ensuite, ajoutez le code de style CSS à la fin de la page *site. CSS* dans le répertoire *wwwroot\css* :</span><span class="sxs-lookup"><span data-stu-id="def68-226">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="def68-227">Après cela, ajoutez du code pour envoyer des entrées de la page Web `OnGetAnalyzeSentiment` au gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="def68-227">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="def68-228">Dans le fichier *site. js* situé dans le répertoire *wwwroot\js* , créez une fonction appelée `getSentiment` pour obtenir une requête HTTP `OnGetAnalyzeSentiment` avec l’entrée utilisateur du gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="def68-228">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="def68-229">En dessous, ajoutez une autre fonction `updateMarker` appelée pour mettre à jour dynamiquement la position du marqueur sur la page Web à mesure que le sentiment est prédit.</span><span class="sxs-lookup"><span data-stu-id="def68-229">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="def68-230">Créez une fonction de gestionnaire d' `updateSentiment` événements appelée pour recevoir l’entrée de l’utilisateur, l’envoyer `OnGetAnalyzeSentiment` à la fonction `getSentiment` à l’aide de la fonction et `updateMarker` mettre à jour le marqueur avec la fonction.</span><span class="sxs-lookup"><span data-stu-id="def68-230">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="def68-231">Enfin, enregistrez le gestionnaire d’événements et liez-le `textarea` à l’élément `id=Message` avec l’attribut.</span><span class="sxs-lookup"><span data-stu-id="def68-231">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="def68-232">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="def68-232">Run the application</span></span>

<span data-ttu-id="def68-233">Maintenant que votre application est configurée, exécutez l’application qui doit être lancée dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="def68-233">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="def68-234">Lorsque l’application démarre, entrez le *Générateur de modèles est cool !*</span><span class="sxs-lookup"><span data-stu-id="def68-234">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="def68-235">dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="def68-235">into the text area.</span></span> <span data-ttu-id="def68-236">Le sentiment prédit affiché ne doit *pas être toxique*.</span><span class="sxs-lookup"><span data-stu-id="def68-236">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Fenêtre en cours d’exécution avec la fenêtre de sentiment prédite](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="def68-238">Si vous devez référencer les projets générés par le générateur de modèles ultérieurement dans une autre solution, vous pouvez les Rechercher dans `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` le répertoire.</span><span class="sxs-lookup"><span data-stu-id="def68-238">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="def68-239">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="def68-239">Next steps</span></span>

<span data-ttu-id="def68-240">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="def68-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="def68-241">Créer une application de Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="def68-241">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="def68-242">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="def68-242">Prepare and understand the data</span></span>
> - <span data-ttu-id="def68-243">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="def68-243">Choose a scenario</span></span>
> - <span data-ttu-id="def68-244">Charger les données</span><span class="sxs-lookup"><span data-stu-id="def68-244">Load the data</span></span>
> - <span data-ttu-id="def68-245">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="def68-245">Train the model</span></span>
> - <span data-ttu-id="def68-246">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="def68-246">Evaluate the model</span></span>
> - <span data-ttu-id="def68-247">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="def68-247">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="def68-248">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="def68-248">Additional Resources</span></span>

<span data-ttu-id="def68-249">Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="def68-249">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="def68-250">Scénarios du Générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="def68-250">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="def68-251">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="def68-251">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="def68-252">Métriques du modèle de classification binaire</span><span class="sxs-lookup"><span data-stu-id="def68-252">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)