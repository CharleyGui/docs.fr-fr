---
title: 'Tutorial: Prédire les prix en utilisant la régression avec Model Builder'
description: Ce tutoriel montre comment créer un modèle de régression Model Builder ML.NET pour prédire des prix, plus précisément celui des courses de taxi à New York.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: 750738f8e3c65363e9996667feeccd1b84391f9f
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438243"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="e7940-103">Tutorial: Prédire les prix en utilisant la régression avec Model Builder</span><span class="sxs-lookup"><span data-stu-id="e7940-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="e7940-104">Découvrez comment utiliser Model Builder ML.NET pour générer un modèle de régression pour prédire des prix.</span><span class="sxs-lookup"><span data-stu-id="e7940-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="e7940-105">L’application console .NET que vous développez dans ce tutoriel prédit les prix des taxis en fonction de l’historique des prix des courses de taxi à New York.</span><span class="sxs-lookup"><span data-stu-id="e7940-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="e7940-106">Le modèle de prédiction des prix de Model Builder peut être utilisé pour tout scénario nécessitant une valeur de prédiction numérique.</span><span class="sxs-lookup"><span data-stu-id="e7940-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="e7940-107">Voici quelques exemples de scénarios : prédiction des prix de l’immobilier, prédiction de la demande et prévisions des ventes.</span><span class="sxs-lookup"><span data-stu-id="e7940-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="e7940-108">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="e7940-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e7940-109">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="e7940-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="e7940-110">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="e7940-110">Choose a scenario</span></span>
> - <span data-ttu-id="e7940-111">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="e7940-111">Load the data</span></span>
> - <span data-ttu-id="e7940-112">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="e7940-112">Train the model</span></span>
> - <span data-ttu-id="e7940-113">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="e7940-113">Evaluate the model</span></span>
> - <span data-ttu-id="e7940-114">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="e7940-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="e7940-115">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="e7940-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="e7940-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e7940-116">Pre-requisites</span></span>

<span data-ttu-id="e7940-117">Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="e7940-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e7940-118">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="e7940-118">Create a console application</span></span>

1. <span data-ttu-id="e7940-119">Créez une **application de console de base C .NET** appelée «TaxiFarePrediction».</span><span class="sxs-lookup"><span data-stu-id="e7940-119">Create a **C# .NET Core Console Application** called "TaxiFarePrediction".</span></span> <span data-ttu-id="e7940-120">Assurez-vous que **la solution et le projet Place dans le même répertoire** ne sont pas **contrôlés** (VS 2019), ou **que l’annuaire Créer pour la solution** soit **vérifié** (VS 2017).</span><span class="sxs-lookup"><span data-stu-id="e7940-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="e7940-121">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="e7940-121">Prepare and understand the data</span></span>

1. <span data-ttu-id="e7940-122">Créez un répertoire nommé *Data* dans votre projet pour stocker les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="e7940-122">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="e7940-123">Le jeu de données utilisé pour l’apprentissage et l’évaluation du modèle de Machine Learning provient à l’origine du jeu de données NYC TLC Taxi Trip.</span><span class="sxs-lookup"><span data-stu-id="e7940-123">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="e7940-124">Pour télécharger le jeu de données, accédez au lien de téléchargement [taxi-fare-train.csv](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span><span class="sxs-lookup"><span data-stu-id="e7940-124">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="e7940-125">Lorsque la page se charge, cliquez avec le bouton droit n’importe où sur la page et sélectionnez **Enregistrer sous**.</span><span class="sxs-lookup"><span data-stu-id="e7940-125">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="e7940-126">Utilisez la boîte de dialogue **Enregistrer sous** pour enregistrer le fichier dans le dossier *Data* que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="e7940-126">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="e7940-127">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *taxi-fare-train.csv*, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e7940-127">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="e7940-128">Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.</span><span class="sxs-lookup"><span data-stu-id="e7940-128">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="e7940-129">Chaque ligne du jeu de données `taxi-fare-train.csv` contient les détails de courses effectuées par un taxi.</span><span class="sxs-lookup"><span data-stu-id="e7940-129">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="e7940-130">Ouvrez le jeu de données **taxi-fare-train.csv**.</span><span class="sxs-lookup"><span data-stu-id="e7940-130">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="e7940-131">Le jeu de données fourni contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7940-131">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="e7940-132">**vendor_id :** l’ID du taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e7940-132">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="e7940-133">**rate_code :** le type de tarif de la course de taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e7940-133">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="e7940-134">**passenger_count :** le nombre de passagers embarqués est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e7940-134">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="e7940-135">**trip_time_in_secs :** durée totale de la course.</span><span class="sxs-lookup"><span data-stu-id="e7940-135">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="e7940-136">Vous voulez prédire le prix de la course avant de l’effectuer.</span><span class="sxs-lookup"><span data-stu-id="e7940-136">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="e7940-137">À ce stade vous ne connaissez pas la durée de la course.</span><span class="sxs-lookup"><span data-stu-id="e7940-137">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="e7940-138">Par conséquent, la durée de la course n’est pas une fonctionnalité et vous devez exclure cette colonne du modèle.</span><span class="sxs-lookup"><span data-stu-id="e7940-138">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="e7940-139">**trip_distance :** la distance de la course est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e7940-139">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="e7940-140">**payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="e7940-140">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="e7940-141">**fare_amount :** le prix total payé pour la course est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="e7940-141">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="e7940-142">`label` est la colonne à prédire.</span><span class="sxs-lookup"><span data-stu-id="e7940-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="e7940-143">Quand vous effectuez une tâche de régression, l’objectif est de prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="e7940-143">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="e7940-144">Dans ce scénario de prédiction des prix, c’est le coût d’une course de taxi qui est prédit.</span><span class="sxs-lookup"><span data-stu-id="e7940-144">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="e7940-145">Par conséquent, **fare_amount** est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="e7940-145">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="e7940-146">Les `features` identifiées sont les entrées que vous fournissez au modèle pour prédire `label`.</span><span class="sxs-lookup"><span data-stu-id="e7940-146">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="e7940-147">Dans ce cas, le reste des colonnes, à l’exception de **trip_time_in_secs** sont utilisés comme caractéristiques ou entrées pour prédire le montant du tarif.</span><span class="sxs-lookup"><span data-stu-id="e7940-147">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="e7940-148">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="e7940-148">Choose a scenario</span></span>

<span data-ttu-id="e7940-149">Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="e7940-149">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="e7940-150">Dans ce cas, le scénario est `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="e7940-150">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="e7940-151">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Ajouter** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="e7940-151">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="e7940-152">Dans l’étape de scénario de l’outil Model Builder, sélectionnez le scénario *Prédiction de prix*.</span><span class="sxs-lookup"><span data-stu-id="e7940-152">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="e7940-153">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="e7940-153">Load the data</span></span>

<span data-ttu-id="e7940-154">Model Builder accepte des données de deux sources : une base de données SQL Server, ou un fichier csv ou tsv local.</span><span class="sxs-lookup"><span data-stu-id="e7940-154">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="e7940-155">Dans l’étape des données de l’outil Model Builder, sélectionnez *Fichier* dans la liste déroulante des sources de données.</span><span class="sxs-lookup"><span data-stu-id="e7940-155">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="e7940-156">Sélectionnez le bouton en regard de la zone de texte *Sélectionner un fichier* et utilisez l’Explorateur de fichiers pour parcourir et sélectionner *taxi-fare-test.csv* dans le répertoire *Data*.</span><span class="sxs-lookup"><span data-stu-id="e7940-156">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="e7940-157">Choisissez *fare_amount* dans la *colonne pour prédire (label)* dropdown.</span><span class="sxs-lookup"><span data-stu-id="e7940-157">Choose *fare_amount* in the *Column to Predict (Label)* dropdown.</span></span>
1. <span data-ttu-id="e7940-158">Élargissez le décrochage *des colonnes d’entrée (Caractéristiques)* et décochez la colonne *trip_time_in_secs* pour l’exclure en tant que fonctionnalité pendant la formation.</span><span class="sxs-lookup"><span data-stu-id="e7940-158">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>  <span data-ttu-id="e7940-159">Naviguez jusqu’à l’étape de train de l’outil Model Builder.</span><span class="sxs-lookup"><span data-stu-id="e7940-159">Navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="e7940-160">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="e7940-160">Train the model</span></span>

<span data-ttu-id="e7940-161">La tâche Machine Learning utilisée pour entraîner le modèle de prédiction des prix de ce tutoriel est la régression.</span><span class="sxs-lookup"><span data-stu-id="e7940-161">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="e7940-162">Pendant le processus d’entraînement du modèle, Model Builder entraîne des modèles distincts en utilisant différents algorithmes et paramètres de régression pour trouver le modèle le plus performant pour votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="e7940-162">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="e7940-163">Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="e7940-163">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="e7940-164">Model Builder sélectionne automatiquement une valeur par défaut pour **le temps de train (secondes)** en fonction de la taille de votre source de données.</span><span class="sxs-lookup"><span data-stu-id="e7940-164">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="e7940-165">Laissez la valeur par défaut comme c’est le cas pour *le temps de s’entraîner (secondes)* sauf si vous préférez vous entraîner plus longtemps.</span><span class="sxs-lookup"><span data-stu-id="e7940-165">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="e7940-166">Sélectionnez *Commencer l’entraînement*.</span><span class="sxs-lookup"><span data-stu-id="e7940-166">Select *Start Training*.</span></span>

<span data-ttu-id="e7940-167">Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="e7940-167">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="e7940-168">Le champ État affiche l’état d’achèvement du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="e7940-168">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="e7940-169">Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="e7940-169">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="e7940-170">Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="e7940-170">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="e7940-171">Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="e7940-171">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="e7940-172">Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="e7940-172">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="e7940-173">Une fois l’entraînement terminé, accédez à l’étape d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="e7940-173">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="e7940-174">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="e7940-174">Evaluate the model</span></span>

<span data-ttu-id="e7940-175">Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="e7940-175">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="e7940-176">Dans l’étape d’évaluation de l’outil Model Builder, la section de la sortie contient l’algorithme utilisé par le modèle le plus performant dans l’entrée *Meilleur modèle* ainsi que des métriques dans *Meilleure qualité du modèle (RSquared)*.</span><span class="sxs-lookup"><span data-stu-id="e7940-176">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="e7940-177">Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.</span><span class="sxs-lookup"><span data-stu-id="e7940-177">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="e7940-178">Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.</span><span class="sxs-lookup"><span data-stu-id="e7940-178">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="e7940-179">Sinon, accédez à l’étape du code.</span><span class="sxs-lookup"><span data-stu-id="e7940-179">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="e7940-180">Ajouter le code pour effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="e7940-180">Add the code to make predictions</span></span>

<span data-ttu-id="e7940-181">Deux projets sont créés à la suite du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="e7940-181">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="e7940-182">TaxiFarePredictionML.ConsoleApp: Une application .NET Core Console qui contient le modèle de formation et de code de consommation d’échantillons.</span><span class="sxs-lookup"><span data-stu-id="e7940-182">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="e7940-183">TaxiFarePredictionML.Modèle: Une bibliothèque de classe standard .NET contenant les modèles de données qui définissent le schéma des données des `ConsumeModel` modèles d’entrée et de sortie, la version enregistrée du modèle le plus performant pendant la formation et une classe d’aide appelée à faire des prédictions.</span><span class="sxs-lookup"><span data-stu-id="e7940-183">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="e7940-184">Dans l’étape du code de l’outil Model Builder, sélectionnez **Ajouter des projets** pour ajouter les projets générés automatiquement à la solution.</span><span class="sxs-lookup"><span data-stu-id="e7940-184">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="e7940-185">Ouvrez le fichier *Program.cs* dans le projet *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="e7940-185">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="e7940-186">Ajoutez l’énoncé suivant à référence du projet *TaxiFarePredictionML.Model* :</span><span class="sxs-lookup"><span data-stu-id="e7940-186">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="e7940-187">Pour faire une prédiction sur les nouvelles données à `ModelInput` l’aide du modèle, créez une nouvelle instance de la classe à l’intérieur de la `Main` méthode de votre application.</span><span class="sxs-lookup"><span data-stu-id="e7940-187">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="e7940-188">Notez que le montant de la course ne fait pas partie de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="e7940-188">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="e7940-189">Cela est dû au fait que le modèle générera la prédiction pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e7940-189">This is because the model will generate the prediction for it.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="e7940-190">Utilisez `Predict` la méthode `ConsumeModel` de la classe.</span><span class="sxs-lookup"><span data-stu-id="e7940-190">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="e7940-191">La `Predict` méthode charge le modèle [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) formé, créer un pour le modèle et l’utilise pour faire des prédictions sur de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="e7940-191">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span>

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="e7940-192">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="e7940-192">Run the application.</span></span>

    <span data-ttu-id="e7940-193">La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e7940-193">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="e7940-194">Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="e7940-194">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e7940-195">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e7940-195">Next Steps</span></span>

<span data-ttu-id="e7940-196">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="e7940-196">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e7940-197">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="e7940-197">Prepare and understand the data</span></span>
> - <span data-ttu-id="e7940-198">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="e7940-198">Choose a scenario</span></span>
> - <span data-ttu-id="e7940-199">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="e7940-199">Load the data</span></span>
> - <span data-ttu-id="e7940-200">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="e7940-200">Train the model</span></span>
> - <span data-ttu-id="e7940-201">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="e7940-201">Evaluate the model</span></span>
> - <span data-ttu-id="e7940-202">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="e7940-202">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e7940-203">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="e7940-203">Additional Resources</span></span>

<span data-ttu-id="e7940-204">Pour en savoir plus sur les rubriques mentionnées dans ce tutoriel, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7940-204">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="e7940-205">Scénarios du Générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="e7940-205">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="e7940-206">régression ;</span><span class="sxs-lookup"><span data-stu-id="e7940-206">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="e7940-207">Métriques du modèle de régression</span><span class="sxs-lookup"><span data-stu-id="e7940-207">Regression Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)
- [<span data-ttu-id="e7940-208">Jeu de données NYC TLC Taxi Trip</span><span class="sxs-lookup"><span data-stu-id="e7940-208">NYC TLC Taxi Trip data set</span></span>](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
