---
title: 'Tutoriel : Prédire des prix en utilisant la régression avec Model Builder'
description: Ce tutoriel montre comment créer un modèle de régression Model Builder ML.NET pour prédire des prix, plus précisément celui des courses de taxi à New York.
author: luisquintanilla
ms.author: luquinta
ms.date: 09/18/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bb344a7f01e8ffe0e40578c6fb2f28bebd2eb807
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117959"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="96eab-103">Tutoriel : Prédire des prix en utilisant la régression avec Model Builder</span><span class="sxs-lookup"><span data-stu-id="96eab-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="96eab-104">Découvrez comment utiliser Model Builder ML.NET pour générer un modèle de régression() pour prédire des prix.</span><span class="sxs-lookup"><span data-stu-id="96eab-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="96eab-105">L’application console .NET que vous développez dans ce tutoriel prédit les prix des taxis en fonction de l’historique des prix des courses de taxi à New York.</span><span class="sxs-lookup"><span data-stu-id="96eab-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="96eab-106">Le modèle de prédiction des prix de Model Builder peut être utilisé pour tout scénario nécessitant une valeur de prédiction numérique.</span><span class="sxs-lookup"><span data-stu-id="96eab-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="96eab-107">Voici quelques exemples de scénarios : prédiction des prix de l’immobilier, prédiction de la demande et prévisions des ventes.</span><span class="sxs-lookup"><span data-stu-id="96eab-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="96eab-108">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="96eab-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="96eab-109">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="96eab-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="96eab-110">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="96eab-110">Choose a scenario</span></span>
> - <span data-ttu-id="96eab-111">Charger les données</span><span class="sxs-lookup"><span data-stu-id="96eab-111">Load the data</span></span>
> - <span data-ttu-id="96eab-112">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="96eab-112">Train the model</span></span>
> - <span data-ttu-id="96eab-113">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="96eab-113">Evaluate the model</span></span>
> - <span data-ttu-id="96eab-114">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="96eab-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="96eab-115">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="96eab-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="96eab-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="96eab-116">Pre-requisites</span></span>

<span data-ttu-id="96eab-117">Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="96eab-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="96eab-118">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="96eab-118">Create a console application</span></span>

1. <span data-ttu-id="96eab-119">Créez une **application console .NET Core** appelée « TaxiFarePrediction ».</span><span class="sxs-lookup"><span data-stu-id="96eab-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="96eab-120">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="96eab-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="96eab-121">Créez un répertoire nommé *Data* dans votre projet pour stocker les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="96eab-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="96eab-122">Le jeu de données utilisé pour l’apprentissage et l’évaluation du modèle de Machine Learning provient à l’origine du jeu de données NYC TLC Taxi Trip.</span><span class="sxs-lookup"><span data-stu-id="96eab-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    <span data-ttu-id="96eab-123">Pour télécharger le jeu de données, accédez au lien de téléchargement [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="96eab-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    <span data-ttu-id="96eab-124">Lorsque la page se charge, cliquez avec le bouton droit n’importe où sur la page et sélectionnez **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="96eab-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    <span data-ttu-id="96eab-125">Utilisez la boîte de dialogue **Enregistrer sous** pour enregistrer le fichier dans le dossier *Data* que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="96eab-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="96eab-126">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *taxi-fare-train.csv*, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="96eab-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="96eab-127">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="96eab-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="96eab-128">Chaque ligne du jeu de données `taxi-fare-train.csv` contient les détails de courses effectuées par un taxi.</span><span class="sxs-lookup"><span data-stu-id="96eab-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="96eab-129">Ouvrez le jeu de données **taxi-fare-train.csv**.</span><span class="sxs-lookup"><span data-stu-id="96eab-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="96eab-130">Le jeu de données fourni contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="96eab-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="96eab-131">**vendor_id :** l’ID du taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96eab-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="96eab-132">**rate_code :** le type de tarif de la course de taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96eab-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="96eab-133">**passenger_count :** le nombre de passagers embarqués est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96eab-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="96eab-134">**trip_time_in_secs :** durée totale de la course.</span><span class="sxs-lookup"><span data-stu-id="96eab-134">**trip_time_in_secs:** The amount of time the trip took.</span></span>
    - <span data-ttu-id="96eab-135">**trip_distance :** la distance de la course est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96eab-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="96eab-136">**payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="96eab-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="96eab-137">**fare_amount :** le prix total payé pour la course est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="96eab-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="96eab-138">`label` est la colonne à prédire.</span><span class="sxs-lookup"><span data-stu-id="96eab-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="96eab-139">Quand vous effectuez une tâche de régression, l’objectif est de prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="96eab-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="96eab-140">Dans ce scénario de prédiction des prix, c’est le coût d’une course de taxi qui est prédit.</span><span class="sxs-lookup"><span data-stu-id="96eab-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="96eab-141">Par conséquent, **fare_amount** est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="96eab-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="96eab-142">Les `features` identifiées sont les entrées que vous fournissez au modèle pour prédire `label`.</span><span class="sxs-lookup"><span data-stu-id="96eab-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="96eab-143">Dans ce cas, le reste des colonnes sont utilisées comme caractéristiques ou comme entrées pour prédire le prix de la course.</span><span class="sxs-lookup"><span data-stu-id="96eab-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="96eab-144">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="96eab-144">Choose a scenario</span></span>

<span data-ttu-id="96eab-145">Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="96eab-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="96eab-146">Dans ce cas, le scénario est `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="96eab-146">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="96eab-147">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Ajouter** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="96eab-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="96eab-148">Dans l’étape de scénario de l’outil Model Builder, sélectionnez le scénario *Prédiction de prix*.</span><span class="sxs-lookup"><span data-stu-id="96eab-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="96eab-149">Charger les données</span><span class="sxs-lookup"><span data-stu-id="96eab-149">Load the data</span></span>

<span data-ttu-id="96eab-150">Model Builder accepte des données de deux sources : une base de données SQL Server, ou un fichier csv ou tsv local.</span><span class="sxs-lookup"><span data-stu-id="96eab-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="96eab-151">Dans l’étape des données de l’outil Model Builder, sélectionnez *Fichier* dans la liste déroulante des sources de données.</span><span class="sxs-lookup"><span data-stu-id="96eab-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="96eab-152">Sélectionnez le bouton en regard de la zone de texte *Sélectionner un fichier* et utilisez l’Explorateur de fichiers pour parcourir et sélectionner *taxi-fare-test.csv* dans le répertoire *Data*.</span><span class="sxs-lookup"><span data-stu-id="96eab-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="96eab-153">Choisissez *fare_amount* dans la liste déroulante *Étiquette ou colonne à prédire*, puis accédez à l’étape d’entraînement de l’outil Model Builder.</span><span class="sxs-lookup"><span data-stu-id="96eab-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="96eab-154">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="96eab-154">Train the model</span></span>

<span data-ttu-id="96eab-155">La tâche Machine Learning utilisée pour entraîner le modèle de prédiction des prix de ce tutoriel est la régression.</span><span class="sxs-lookup"><span data-stu-id="96eab-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="96eab-156">Pendant le processus d’entraînement du modèle, Model Builder entraîne des modèles distincts en utilisant différents algorithmes et paramètres de régression pour trouver le modèle le plus performant pour votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="96eab-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="96eab-157">Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="96eab-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="96eab-158">Le générateur de modèles sélectionne automatiquement une valeur par défaut pour le **temps de formation (en secondes)** en fonction de la taille de votre source de données.</span><span class="sxs-lookup"><span data-stu-id="96eab-158">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="96eab-159">Laissez la valeur par défaut telle quelle pour le *temps de formation (en secondes)* , sauf si vous préférez effectuer un apprentissage pour une durée plus longue.</span><span class="sxs-lookup"><span data-stu-id="96eab-159">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="96eab-160">Sélectionnez *Commencer l’entraînement*.</span><span class="sxs-lookup"><span data-stu-id="96eab-160">Select *Start Training*.</span></span>

<span data-ttu-id="96eab-161">Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="96eab-161">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="96eab-162">Le champ État affiche l’état d’achèvement du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="96eab-162">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="96eab-163">Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="96eab-163">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="96eab-164">Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="96eab-164">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="96eab-165">Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="96eab-165">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="96eab-166">Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="96eab-166">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="96eab-167">Une fois l’entraînement terminé, accédez à l’étape d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="96eab-167">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="96eab-168">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="96eab-168">Evaluate the model</span></span>

<span data-ttu-id="96eab-169">Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="96eab-169">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="96eab-170">Dans l’étape d’évaluation de l’outil Model Builder, la section de la sortie contient l’algorithme utilisé par le modèle le plus performant dans l’entrée *Meilleur modèle* ainsi que des métriques dans *Meilleure qualité du modèle (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="96eab-170">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="96eab-171">Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.</span><span class="sxs-lookup"><span data-stu-id="96eab-171">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="96eab-172">Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.</span><span class="sxs-lookup"><span data-stu-id="96eab-172">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="96eab-173">Sinon, accédez à l’étape du code.</span><span class="sxs-lookup"><span data-stu-id="96eab-173">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="96eab-174">Ajouter le code pour effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="96eab-174">Add the code to make predictions</span></span>

<span data-ttu-id="96eab-175">Deux projets sont créés à la suite du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="96eab-175">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="96eab-176">TaxiFarePredictionML.ConsoleApp : Une application console .NET Core qui contient le code d’entraînement et d’utilisation du modèle.</span><span class="sxs-lookup"><span data-stu-id="96eab-176">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="96eab-177">TaxiFarePredictionML.Model : Une bibliothèque de classes .NET Standard contenant les modèles de données qui définissent le schéma des données du modèle en entrée et en sortie, ainsi que la version enregistrée du modèle le plus performant lors de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="96eab-177">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="96eab-178">Dans l’étape du code de l’outil Model Builder, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.</span><span class="sxs-lookup"><span data-stu-id="96eab-178">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="96eab-179">Cliquez avec le bouton droit sur le projet *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="96eab-179">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="96eab-180">Choisissez ensuite **Ajouter > Référence**.</span><span class="sxs-lookup"><span data-stu-id="96eab-180">Then, **Add > Reference**.</span></span> <span data-ttu-id="96eab-181">Choisissez le nœud **Projets > Solution** puis, dans la liste, cochez le projet *TaxiFarePredictionML.Model* et sélectionnez OK.</span><span class="sxs-lookup"><span data-stu-id="96eab-181">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="96eab-182">Ouvrez le fichier *Program.cs* dans le projet *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="96eab-182">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="96eab-183">Ajoutez les instructions using suivantes pour référencer le package NuGet *Microsoft.ML* et le projet *TaxiFarePredictionML.Model* :</span><span class="sxs-lookup"><span data-stu-id="96eab-183">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="96eab-184">Ajoutez la méthode `ConsumeModel` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="96eab-184">Add the `ConsumeModel` method to the `Program` class.</span></span>

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

    <span data-ttu-id="96eab-185">`ConsumeModel` charge le modèle formé, crée un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour le modèle et l’utilise pour effectuer des prédictions sur les nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="96eab-185">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

1. <span data-ttu-id="96eab-186">Pour effectuer une prédiction sur les nouvelles données à l’aide du modèle, créez une nouvelle instance de la classe `ModelInput` et utilisez la méthode `ConsumeModel`.</span><span class="sxs-lookup"><span data-stu-id="96eab-186">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="96eab-187">Notez que le montant de la course ne fait pas partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="96eab-187">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="96eab-188">Cela est dû au fait que le modèle générera la prédiction pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="96eab-188">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="96eab-189">Ajoutez le code suivant à la méthode `Main` et exécutez l’application</span><span class="sxs-lookup"><span data-stu-id="96eab-189">Add the following code to the `Main` method and run the application</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    <span data-ttu-id="96eab-190">La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="96eab-190">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="96eab-191">Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="96eab-191">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="96eab-192">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="96eab-192">Next Steps</span></span>

<span data-ttu-id="96eab-193">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="96eab-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="96eab-194">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="96eab-194">Prepare and understand the data</span></span>
> - <span data-ttu-id="96eab-195">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="96eab-195">Choose a scenario</span></span>
> - <span data-ttu-id="96eab-196">Charger les données</span><span class="sxs-lookup"><span data-stu-id="96eab-196">Load the data</span></span>
> - <span data-ttu-id="96eab-197">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="96eab-197">Train the model</span></span>
> - <span data-ttu-id="96eab-198">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="96eab-198">Evaluate the model</span></span>
> - <span data-ttu-id="96eab-199">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="96eab-199">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="96eab-200">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="96eab-200">Additional Resources</span></span>

<span data-ttu-id="96eab-201">Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="96eab-201">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="96eab-202">Scénarios du Générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="96eab-202">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="96eab-203">Régression</span><span class="sxs-lookup"><span data-stu-id="96eab-203">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="96eab-204">Métriques du modèle de régression</span><span class="sxs-lookup"><span data-stu-id="96eab-204">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- [<span data-ttu-id="96eab-205">Jeu de données NYC TLC Taxi Trip</span><span class="sxs-lookup"><span data-stu-id="96eab-205">NYC TLC Taxi Trip data set</span></span>](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)
