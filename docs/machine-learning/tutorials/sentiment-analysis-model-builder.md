---
title: 'Didacticiel : analyser le sentiment-classification binaire'
description: Ce didacticiel vous montre comment créer une application Razor Pages qui classe les sentiments à partir de commentaires de site Web et prend les mesures appropriées. Le classifieur de sentiment binaire utilise le générateur de modèles dans Visual Studio.
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 670c4dd1ac9da496f59d12d2e880cf269d64f309
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344968"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="7cd7c-104">Didacticiel : analyser le sentiment de commentaires de site Web dans une application Web à l’aide du générateur de modèles ML.NET</span><span class="sxs-lookup"><span data-stu-id="7cd7c-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="7cd7c-105">Découvrez comment analyser les sentiments de commentaires en temps réel dans une application Web.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="7cd7c-106">Ce didacticiel vous montre comment créer une application ASP.NET Core Razor Pages qui classe les sentiments à partir de commentaires de site Web en temps réel.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="7cd7c-107">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="7cd7c-108">Créer une application de Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7cd7c-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="7cd7c-109">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="7cd7c-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="7cd7c-110">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="7cd7c-110">Choose a scenario</span></span>
> - <span data-ttu-id="7cd7c-111">Charger les données</span><span class="sxs-lookup"><span data-stu-id="7cd7c-111">Load the data</span></span>
> - <span data-ttu-id="7cd7c-112">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="7cd7c-112">Train the model</span></span>
> - <span data-ttu-id="7cd7c-113">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="7cd7c-113">Evaluate the model</span></span>
> - <span data-ttu-id="7cd7c-114">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="7cd7c-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="7cd7c-115">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="7cd7c-116">Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples) .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="7cd7c-117">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7cd7c-117">Pre-requisites</span></span>

<span data-ttu-id="7cd7c-118">Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="7cd7c-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="7cd7c-119">Créer une application Razor Pages</span><span class="sxs-lookup"><span data-stu-id="7cd7c-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="7cd7c-120">Créer une **application de Razor Pages ASP.net Core**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="7cd7c-121">Ouvrez Visual Studio et sélectionnez **fichier > nouveau > projet** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="7cd7c-122">Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#** , suivi du nœud **Web**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="7cd7c-123">Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="7cd7c-124">Dans la zone de texte **nom** , tapez « SentimentRazor ».</span><span class="sxs-lookup"><span data-stu-id="7cd7c-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="7cd7c-125">Vérifiez que la case à cocher **Placer la solution et le projet dans le même répertoire** est **désactivée** (vs 2019) ou que l’option **créer le répertoire pour la solution** est **cochée** (vs 2017).</span><span class="sxs-lookup"><span data-stu-id="7cd7c-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="7cd7c-126">Sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="7cd7c-127">Choisissez **application Web** dans la fenêtre qui affiche les différents types de ASP.net Core projets, puis cliquez sur le bouton **OK** .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="7cd7c-128">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="7cd7c-128">Prepare and understand the data</span></span>

<span data-ttu-id="7cd7c-129">Téléchargez le [jeu de données Detox Wikipédia](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span><span class="sxs-lookup"><span data-stu-id="7cd7c-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="7cd7c-130">Lorsque la page Web s’ouvre, cliquez avec le bouton droit sur la page, sélectionnez **Enregistrer sous** , puis enregistrez le fichier sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="7cd7c-131">Chaque ligne du jeu de données *Wikipédia-Detox-250-Line-Data. TSV* représente une révision différente laissée par un utilisateur sur Wikipédia.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="7cd7c-132">La première colonne représente le sentiment du texte (0 est non toxique, 1 est toxique) et la deuxième colonne représente le commentaire laissé par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="7cd7c-133">Les colonnes sont séparées par des tabulations.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-133">The columns are separated by tabs.</span></span> <span data-ttu-id="7cd7c-134">Les données ressemblent à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-134">The data looks like the following:</span></span>

| <span data-ttu-id="7cd7c-135">Sentiment</span><span class="sxs-lookup"><span data-stu-id="7cd7c-135">Sentiment</span></span> | <span data-ttu-id="7cd7c-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="7cd7c-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="7cd7c-137">1</span><span class="sxs-lookup"><span data-stu-id="7cd7c-137">1</span></span> | <span data-ttu-id="7cd7c-138">= = IMPROPRE = = dude, vous êtes très impropre à charger cette image Carl, ou autre.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="7cd7c-139">1</span><span class="sxs-lookup"><span data-stu-id="7cd7c-139">1</span></span> | <span data-ttu-id="7cd7c-140">= = OK !</span><span class="sxs-lookup"><span data-stu-id="7cd7c-140">== OK!</span></span> <span data-ttu-id="7cd7c-141">= = IM VA SE RENDRE COMPTE DU WIKI SAUVAGE, !!!</span><span class="sxs-lookup"><span data-stu-id="7cd7c-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="7cd7c-142">0</span><span class="sxs-lookup"><span data-stu-id="7cd7c-142">0</span></span> | <span data-ttu-id="7cd7c-143">J’espère que cela vous aidera.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="7cd7c-144">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="7cd7c-144">Choose a scenario</span></span>

![Assistant Générateur de modèles dans Visual Studio](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="7cd7c-146">Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="7cd7c-147">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet *SentimentRazor* , puis sélectionnez **Ajouter** > **machine learning**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="7cd7c-148">Pour cet exemple, le scénario est l’analyse de sentiments.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="7cd7c-149">Dans l’étape de *scénario* de l’outil générateur de modèles, sélectionnez le scénario **analyse des sentiments** .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="7cd7c-150">Charger les données</span><span class="sxs-lookup"><span data-stu-id="7cd7c-150">Load the data</span></span>

<span data-ttu-id="7cd7c-151">Le générateur de modèles accepte les données de deux sources, une base de données SQL Server ou un fichier local au format `csv` ou `tsv`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="7cd7c-152">Dans l’étape des données de l’outil Model Builder, sélectionnez **Fichier** dans la liste déroulante des sources de données.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="7cd7c-153">Sélectionnez le bouton en regard de la zone de texte **Sélectionner un fichier** et utilisez l’Explorateur de fichiers pour parcourir et sélectionner le fichier *Wikipédia-Detox-250-Line-Data. TSV* .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="7cd7c-154">Choisissez **sentiments** dans la liste déroulante **colonne à prédire (étiquette)** .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="7cd7c-155">Laissez les valeurs par défaut pour la liste déroulante **colonnes d’entrée (fonctionnalités)** .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="7cd7c-156">Sélectionnez le lien **former** pour passer à l’étape suivante dans l’outil générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="7cd7c-157">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="7cd7c-157">Train the model</span></span>

<span data-ttu-id="7cd7c-158">La tâche de Machine Learning utilisée pour l’apprentissage du modèle d’analyse des sentiments dans ce didacticiel est la classification binaire.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="7cd7c-159">Pendant le processus d’apprentissage du modèle, le générateur de modèles forme des modèles distincts à l’aide de différents algorithmes et paramètres de classification binaire pour trouver le modèle le plus performant pour votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="7cd7c-160">Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="7cd7c-161">Le générateur de modèles sélectionne automatiquement une valeur par défaut pour le **temps de formation (en secondes)** en fonction de la taille de votre source de données.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="7cd7c-162">Bien que le générateur de modèles définisse la valeur de **temps à former (secondes)** à 10 secondes, augmentez-le à 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="7cd7c-163">La formation sur une période plus longue permet au générateur de modèles d’explorer un plus grand nombre d’algorithmes et une combinaison de paramètres dans la recherche du meilleur modèle.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="7cd7c-164">Sélectionnez **Commencer l’entraînement**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-164">Select **Start Training**.</span></span>

    <span data-ttu-id="7cd7c-165">Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="7cd7c-166">Le champ État affiche l’état d’achèvement du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="7cd7c-167">Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="7cd7c-168">Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="7cd7c-169">Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="7cd7c-170">Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="7cd7c-171">Une fois l’apprentissage terminé, sélectionnez le lien **évaluer** pour passer à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="7cd7c-172">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="7cd7c-172">Evaluate the model</span></span>

<span data-ttu-id="7cd7c-173">Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="7cd7c-174">Dans l’étape évaluer de l’outil générateur de modèles, la section sortie contient l’algorithme utilisé par le modèle le mieux adapté à l’entrée de **modèle la plus** performante, ainsi que les métriques dont la **précision de modèle**est optimale.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="7cd7c-175">Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="7cd7c-176">Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="7cd7c-177">Dans le cas contraire, sélectionnez le lien de **code** pour passer à l’étape finale de l’outil générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="7cd7c-178">Ajouter le code pour effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="7cd7c-178">Add the code to make predictions</span></span>

<span data-ttu-id="7cd7c-179">Deux projets sont créés à la suite du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="7cd7c-180">Référencer le modèle formé</span><span class="sxs-lookup"><span data-stu-id="7cd7c-180">Reference the trained model</span></span>

1. <span data-ttu-id="7cd7c-181">Dans l’étape de *code* de l’outil générateur de modèles, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="7cd7c-182">Les projets suivants doivent apparaître dans le **Explorateur de solutions**:</span><span class="sxs-lookup"><span data-stu-id="7cd7c-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="7cd7c-183">*SentimentRazorML. ConsoleApp*: application console .net core qui contient l’apprentissage du modèle et le code de prédiction.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="7cd7c-184">*SentimentRazorML. Model*: bibliothèque de classes .NET standard contenant les modèles de données qui définissent le schéma des données de modèle d’entrée et de sortie ainsi que la version enregistrée du modèle le plus performant au cours de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="7cd7c-185">Pour ce didacticiel, seul le projet *SentimentRazorML. Model* est utilisé, car les prédictions sont effectuées dans l’application Web *SentimentRazor* plutôt que dans la console.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="7cd7c-186">Bien que *SentimentRazorML. ConsoleApp* ne soit pas utilisé pour le calcul de score, il peut être utilisé pour reformer le modèle à l’aide de nouvelles données ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="7cd7c-187">Toutefois, la reformation n’entre pas dans le cadre de ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="7cd7c-188">Configurer le pool PredictionEngine</span><span class="sxs-lookup"><span data-stu-id="7cd7c-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="7cd7c-189">Pour effectuer une prédiction unique, vous devez créer un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="7cd7c-189">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="7cd7c-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-190">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="7cd7c-191">En outre, vous devez créer une instance de celle-ci partout où elle est nécessaire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-191">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="7cd7c-192">À mesure que votre application croît, ce processus peut devenir non gérable.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="7cd7c-193">Pour améliorer les performances et la sécurité des threads, utilisez une combinaison d’injection de dépendances et le service `PredictionEnginePool`, qui crée une [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="7cd7c-194">Installez le package NuGet *Microsoft.extensions.ml* :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="7cd7c-195">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="7cd7c-196">Choisissez « nuget.org » comme source du package.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="7cd7c-197">Sélectionnez l’onglet **Parcourir** et recherchez **Microsoft.extensions.ml**.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="7cd7c-198">Sélectionnez le package dans la liste, puis cliquez sur le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="7cd7c-199">Sélectionnez le bouton **OK** dans la boîte de dialogue **aperçu des modifications**</span><span class="sxs-lookup"><span data-stu-id="7cd7c-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="7cd7c-200">Sélectionnez le bouton **J’accepte** dans la boîte de dialogue acceptation de la **licence** si vous acceptez les termes du contrat de licence pour les packages listés.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="7cd7c-201">Ouvrez le fichier *Startup.cs* dans le projet *SentimentRazor* .</span><span class="sxs-lookup"><span data-stu-id="7cd7c-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="7cd7c-202">Ajoutez les instructions using suivantes pour référencer le package NuGet *Microsoft.extensions.ml* et le projet *SentimentRazorML. Model* :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="7cd7c-203">Créez une variable globale pour stocker l’emplacement du fichier de modèle formé.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="7cd7c-204">Le fichier de modèle est stocké dans le répertoire de build en même temps que les fichiers d’assembly de votre application.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="7cd7c-205">Pour faciliter l’accès à, créez une méthode d’assistance appelée `GetAbsolutePath` après la méthode `Configure`</span><span class="sxs-lookup"><span data-stu-id="7cd7c-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="7cd7c-206">Utilisez la méthode `GetAbsolutePath` dans le constructeur de classe `Startup` pour définir le `_modelPath`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="7cd7c-207">Configurez les `PredictionEnginePool` pour votre application dans la méthode `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="7cd7c-208">Créer un gestionnaire d’analyse de sentiments</span><span class="sxs-lookup"><span data-stu-id="7cd7c-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="7cd7c-209">Les prédictions sont effectuées à l’intérieur de la page principale de l’application.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="7cd7c-210">Par conséquent, une méthode qui prend l’entrée utilisateur et utilise le `PredictionEnginePool` pour retourner une prédiction doit être ajoutée.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="7cd7c-211">Ouvrez le fichier *index.cshtml.cs* situé dans le répertoire *pages* et ajoutez les instructions using suivantes :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="7cd7c-212">Pour utiliser le `PredictionEnginePool` configuré dans la classe `Startup`, vous devez l’injecter dans le constructeur du modèle où vous souhaitez l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="7cd7c-213">Ajoutez une variable pour référencer le `PredictionEnginePool` à l’intérieur de la classe `IndexModel`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="7cd7c-214">Créez un constructeur dans la classe `IndexModel` et injectez le service `PredictionEnginePool` dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="7cd7c-215">Créez un gestionnaire de méthode qui utilise la `PredictionEnginePool` pour faire des prédictions à partir de l’entrée utilisateur reçue de la page Web.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="7cd7c-216">Sous la méthode `OnGet`, créez une nouvelle méthode appelée `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="7cd7c-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="7cd7c-217">À l’intérieur de la méthode `OnGetAnalyzeSentiment`, retournez un sentiment *neutre* si l’entrée de l’utilisateur est vide ou null.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="7cd7c-218">En fonction d’une entrée valide, créez une nouvelle instance de `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="7cd7c-219">Utilisez la `PredictionEnginePool` pour prédire le sentiment.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="7cd7c-220">Convertissez la valeur de `bool` prédit en toxique ou non toxique avec le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="7cd7c-221">Enfin, retournez le sentiment à la page Web.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="7cd7c-222">Configurer la page Web</span><span class="sxs-lookup"><span data-stu-id="7cd7c-222">Configure the web page</span></span>

<span data-ttu-id="7cd7c-223">Les résultats retournés par la `OnGetAnalyzeSentiment` seront affichés dynamiquement sur la page Web `Index`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="7cd7c-224">Ouvrez le fichier *index. cshtml* dans le répertoire *pages* et remplacez son contenu par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="7cd7c-225">Ensuite, ajoutez le code de style CSS à la fin de la page *site. CSS* dans le répertoire *wwwroot\css* :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="7cd7c-226">Après cela, ajoutez du code pour envoyer des entrées de la page Web au gestionnaire de `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="7cd7c-227">Dans le fichier *site. js* situé dans le répertoire *wwwroot\js* , créez une fonction appelée `getSentiment` pour effectuer une requête http obtenir avec l’entrée utilisateur dans le gestionnaire de `OnGetAnalyzeSentiment`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="7cd7c-228">En dessous, ajoutez une autre fonction appelée `updateMarker` pour mettre à jour dynamiquement la position du marqueur sur la page Web à mesure que le sentiment est prédit.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="7cd7c-229">Créez une fonction de gestionnaire d’événements appelée `updateSentiment` pour récupérer l’entrée de l’utilisateur, l’envoyer à la fonction `OnGetAnalyzeSentiment` à l’aide de la fonction `getSentiment` et mettre à jour le marqueur avec la fonction `updateMarker`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="7cd7c-230">Enfin, enregistrez le gestionnaire d’événements et liez-le à l’élément `textarea` avec l’attribut `id=Message`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="7cd7c-231">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="7cd7c-231">Run the application</span></span>

<span data-ttu-id="7cd7c-232">Maintenant que votre application est configurée, exécutez l’application qui doit être lancée dans votre navigateur.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-232">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="7cd7c-233">Lorsque l’application démarre, entrez le *Générateur de modèles est cool !*</span><span class="sxs-lookup"><span data-stu-id="7cd7c-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="7cd7c-234">dans la zone de texte.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-234">into the text area.</span></span> <span data-ttu-id="7cd7c-235">Le sentiment prédit affiché ne doit *pas être toxique*.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![Fenêtre en cours d’exécution avec la fenêtre de sentiment prédite](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="7cd7c-237">Si vous devez référencer les projets générés par le générateur de modèles ultérieurement dans une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="7cd7c-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7cd7c-238">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-238">Next steps</span></span>

<span data-ttu-id="7cd7c-239">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="7cd7c-240">Créer une application de Razor Pages ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7cd7c-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="7cd7c-241">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="7cd7c-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="7cd7c-242">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="7cd7c-242">Choose a scenario</span></span>
> - <span data-ttu-id="7cd7c-243">Charger les données</span><span class="sxs-lookup"><span data-stu-id="7cd7c-243">Load the data</span></span>
> - <span data-ttu-id="7cd7c-244">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="7cd7c-244">Train the model</span></span>
> - <span data-ttu-id="7cd7c-245">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="7cd7c-245">Evaluate the model</span></span>
> - <span data-ttu-id="7cd7c-246">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="7cd7c-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7cd7c-247">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="7cd7c-247">Additional Resources</span></span>

<span data-ttu-id="7cd7c-248">Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="7cd7c-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="7cd7c-249">Scénarios du Générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="7cd7c-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="7cd7c-250">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="7cd7c-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="7cd7c-251">Métriques du modèle de classification binaire</span><span class="sxs-lookup"><span data-stu-id="7cd7c-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
