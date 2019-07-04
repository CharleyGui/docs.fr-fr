---
title: Prédire des prix en utilisant la régression avec Model Builder
description: Ce tutoriel montre comment créer un modèle de régression Model Builder ML.NET pour prédire des prix, plus précisément celui des courses de taxi à New York.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: db9788e3065a0f2f21d712b2d4826efea2d8a829
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410577"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="369cb-103">Prédire des prix en utilisant la régression avec Model Builder</span><span class="sxs-lookup"><span data-stu-id="369cb-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="369cb-104">Découvrez comment utiliser Model Builder ML.NET pour générer un [modèle de régression](../resources/glossary.md#regression) pour prédire des prix.</span><span class="sxs-lookup"><span data-stu-id="369cb-104">Learn how to use ML.NET Model Builder to build a [regression model](../resources/glossary.md#regression) to predict prices.</span></span>  <span data-ttu-id="369cb-105">L’application console .NET que vous développez dans ce tutoriel prédit les prix des taxis en fonction de l’historique des prix des courses de taxi à New York.</span><span class="sxs-lookup"><span data-stu-id="369cb-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="369cb-106">Le modèle de prédiction des prix de Model Builder peut être utilisé pour tout scénario nécessitant une valeur de prédiction numérique.</span><span class="sxs-lookup"><span data-stu-id="369cb-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="369cb-107">Voici quelques exemples de scénarios : prédiction des prix de l’immobilier, prédiction de la demande et prévisions des ventes.</span><span class="sxs-lookup"><span data-stu-id="369cb-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="369cb-108">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="369cb-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="369cb-109">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="369cb-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="369cb-110">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="369cb-110">Choose a scenario</span></span>
> * <span data-ttu-id="369cb-111">Charger les données</span><span class="sxs-lookup"><span data-stu-id="369cb-111">Load the data</span></span>
> * <span data-ttu-id="369cb-112">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="369cb-112">Train the model</span></span>
> * <span data-ttu-id="369cb-113">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="369cb-113">Evaluate the model</span></span>
> * <span data-ttu-id="369cb-114">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="369cb-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="369cb-115">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="369cb-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="369cb-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="369cb-116">Pre-requisites</span></span>

<span data-ttu-id="369cb-117">Pour obtenir la liste des prérequis et les instructions d’installation, consultez le [Guide d’installation de Model Builder](../how-to-guides/install-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="369cb-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="369cb-118">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="369cb-118">Create a console application</span></span>

1. <span data-ttu-id="369cb-119">Créez une **application console .NET Core** appelée « TaxiFarePrediction ».</span><span class="sxs-lookup"><span data-stu-id="369cb-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="369cb-120">Installez le package NuGet **Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="369cb-120">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="369cb-121">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="369cb-121">In **Solution Explorer**, right-click the *TaxiFarePrediction* project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="369cb-122">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package dans la liste, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="369cb-122">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="369cb-123">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="369cb-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="369cb-124">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="369cb-124">Prepare and understand the data</span></span>

1. <span data-ttu-id="369cb-125">Créez un répertoire nommé *Data* dans votre projet pour stocker les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="369cb-125">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="369cb-126">Téléchargez le jeu de données [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) et enregistrez-le dans le dossier *Data* que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="369cb-126">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) data set and save it to the *Data* folder you created at the previous step.</span></span> <span data-ttu-id="369cb-127">Ce jeu de données est utilisé pour entraîner et évaluer le modèle Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="369cb-127">This data set is used to train and evaluate the machine learning model.</span></span> <span data-ttu-id="369cb-128">Ce jeu de données provient du [jeu de données NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span><span class="sxs-lookup"><span data-stu-id="369cb-128">This data set is originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="369cb-129">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *taxi-fare-train.csv*, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="369cb-129">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="369cb-130">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="369cb-130">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="369cb-131">Chaque ligne du jeu de données `taxi-fare-train.csv` contient les détails de courses effectuées par un taxi.</span><span class="sxs-lookup"><span data-stu-id="369cb-131">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span> 

1. <span data-ttu-id="369cb-132">Ouvrez le jeu de données **taxi-fare-train.csv**.</span><span class="sxs-lookup"><span data-stu-id="369cb-132">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="369cb-133">Le jeu de données fourni contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="369cb-133">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="369cb-134">**vendor_id :** l’ID du taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="369cb-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="369cb-135">**rate_code :** le type de tarif de la course de taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="369cb-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="369cb-136">**passenger_count :** le nombre de passagers embarqués est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="369cb-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="369cb-137">**trip_time_in_secs :** durée totale de la course.</span><span class="sxs-lookup"><span data-stu-id="369cb-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="369cb-138">Vous voulez prédire le prix de la course avant de l’effectuer.</span><span class="sxs-lookup"><span data-stu-id="369cb-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="369cb-139">À ce stade vous ne connaissez pas la durée de la course.</span><span class="sxs-lookup"><span data-stu-id="369cb-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="369cb-140">Par conséquent, la durée de la course n’est pas une fonctionnalité et vous devez exclure cette colonne du modèle.</span><span class="sxs-lookup"><span data-stu-id="369cb-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    * <span data-ttu-id="369cb-141">**trip_distance :** la distance de la course est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="369cb-141">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="369cb-142">**payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="369cb-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="369cb-143">**fare_amount :** le prix total payé pour la course est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="369cb-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="369cb-144">`label` est la colonne à prédire.</span><span class="sxs-lookup"><span data-stu-id="369cb-144">The `label` is the column you want to predict.</span></span> <span data-ttu-id="369cb-145">Quand vous effectuez une tâche de régression, l’objectif est de prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="369cb-145">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="369cb-146">Dans ce scénario de prédiction des prix, c’est le coût d’une course de taxi qui est prédit.</span><span class="sxs-lookup"><span data-stu-id="369cb-146">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="369cb-147">Par conséquent, **fare_amount** est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="369cb-147">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="369cb-148">Les `features` identifiées sont les entrées que vous fournissez au modèle pour prédire `label`.</span><span class="sxs-lookup"><span data-stu-id="369cb-148">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="369cb-149">Dans ce cas, le reste des colonnes sont utilisées comme caractéristiques ou comme entrées pour prédire le prix de la course.</span><span class="sxs-lookup"><span data-stu-id="369cb-149">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="369cb-150">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="369cb-150">Choose a scenario</span></span>

<span data-ttu-id="369cb-151">Pour entraîner votre modèle, vous devez sélectionner dans la liste des scénarios Machine Learning disponibles fournis par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="369cb-151">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="369cb-152">Dans ce cas, le scénario est `Price Prediction`.</span><span class="sxs-lookup"><span data-stu-id="369cb-152">In this case, the scenario is `Price Prediction`.</span></span> <span data-ttu-id="369cb-153">Pour obtenir une liste plus complète, consultez l’[article donnant une vue d’ensemble de Model Builder](../automate-training-with-model-builder.md#scenarios).</span><span class="sxs-lookup"><span data-stu-id="369cb-153">For a more extensive list visit the [Model Builder overview article](../automate-training-with-model-builder.md#scenarios).</span></span>

1. <span data-ttu-id="369cb-154">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*, puis sélectionnez **Ajouter** > **Machine Learning**.</span><span class="sxs-lookup"><span data-stu-id="369cb-154">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="369cb-155">Dans l’étape de scénario de l’outil Model Builder, sélectionnez le scénario *Prédiction de prix*.</span><span class="sxs-lookup"><span data-stu-id="369cb-155">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="369cb-156">Charger les données</span><span class="sxs-lookup"><span data-stu-id="369cb-156">Load the data</span></span>

<span data-ttu-id="369cb-157">Model Builder accepte des données de deux sources : une base de données SQL Server, ou un fichier csv ou tsv local.</span><span class="sxs-lookup"><span data-stu-id="369cb-157">Model Builder accepts data from two sources, a SQL Server database or a local file csv or tsv file.</span></span> <span data-ttu-id="369cb-158">Pour plus d’informations sur les exigences quant aux formats de données, consultez le [lien](../how-to-guides/install-model-builder.md#limitations) suivant.</span><span class="sxs-lookup"><span data-stu-id="369cb-158">For more information on data format requirements, visit the following [link](../how-to-guides/install-model-builder.md#limitations).</span></span>

1. <span data-ttu-id="369cb-159">Dans l’étape des données de l’outil Model Builder, sélectionnez *Fichier* dans la liste déroulante des sources de données.</span><span class="sxs-lookup"><span data-stu-id="369cb-159">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="369cb-160">Sélectionnez le bouton en regard de la zone de texte *Sélectionner un fichier* et utilisez l’Explorateur de fichiers pour parcourir et sélectionner *taxi-fare-test.csv* dans le répertoire *Data*.</span><span class="sxs-lookup"><span data-stu-id="369cb-160">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="369cb-161">Choisissez *fare_amount* dans la liste déroulante *Étiquette ou colonne à prédire*, puis accédez à l’étape d’entraînement de l’outil Model Builder.</span><span class="sxs-lookup"><span data-stu-id="369cb-161">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="369cb-162">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="369cb-162">Train the model</span></span>

<span data-ttu-id="369cb-163">La tâche Machine Learning utilisée pour entraîner le modèle de prédiction des prix de ce tutoriel est la régression.</span><span class="sxs-lookup"><span data-stu-id="369cb-163">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="369cb-164">Pendant le processus d’entraînement du modèle, Model Builder entraîne des modèles distincts en utilisant différents algorithmes et paramètres de régression pour trouver le modèle le plus performant pour votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="369cb-164">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="369cb-165">Le temps nécessaire pour l’entraînement du modèle est proportionnel à la quantité de données.</span><span class="sxs-lookup"><span data-stu-id="369cb-165">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="369cb-166">Utilisez ce graphique pour vous aider à sélectionner une valeur adéquate pour le champ `Time to train (seconds)` :</span><span class="sxs-lookup"><span data-stu-id="369cb-166">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="369cb-167">\*Taille du jeu de données</span><span class="sxs-lookup"><span data-stu-id="369cb-167">\*Dataset Size</span></span>  | <span data-ttu-id="369cb-168">Type du jeu de données</span><span class="sxs-lookup"><span data-stu-id="369cb-168">Dataset Type</span></span>       | <span data-ttu-id="369cb-169">Avg. Durée de l’entraînement\*</span><span class="sxs-lookup"><span data-stu-id="369cb-169">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="369cb-170">0 - 10 Mo</span><span class="sxs-lookup"><span data-stu-id="369cb-170">0 - 10 Mb</span></span>     | <span data-ttu-id="369cb-171">Numérique et texte</span><span class="sxs-lookup"><span data-stu-id="369cb-171">Numeric and Text</span></span>   | <span data-ttu-id="369cb-172">10 s</span><span class="sxs-lookup"><span data-stu-id="369cb-172">10 sec</span></span>
<span data-ttu-id="369cb-173">10 - 100 Mo</span><span class="sxs-lookup"><span data-stu-id="369cb-173">10 - 100 Mb</span></span>   | <span data-ttu-id="369cb-174">Numérique et texte</span><span class="sxs-lookup"><span data-stu-id="369cb-174">Numeric and Text</span></span>   | <span data-ttu-id="369cb-175">10 min</span><span class="sxs-lookup"><span data-stu-id="369cb-175">10 min</span></span>
<span data-ttu-id="369cb-176">100 - 500 Mo</span><span class="sxs-lookup"><span data-stu-id="369cb-176">100 - 500 Mb</span></span>  | <span data-ttu-id="369cb-177">Numérique et texte</span><span class="sxs-lookup"><span data-stu-id="369cb-177">Numeric and Text</span></span>   | <span data-ttu-id="369cb-178">30 min</span><span class="sxs-lookup"><span data-stu-id="369cb-178">30 min</span></span>
<span data-ttu-id="369cb-179">500 - 1 Go</span><span class="sxs-lookup"><span data-stu-id="369cb-179">500 - 1 Gb</span></span>    | <span data-ttu-id="369cb-180">Numérique et texte</span><span class="sxs-lookup"><span data-stu-id="369cb-180">Numeric and Text</span></span>   | <span data-ttu-id="369cb-181">60 min</span><span class="sxs-lookup"><span data-stu-id="369cb-181">60 min</span></span>
<span data-ttu-id="369cb-182">\+ de 1 Go</span><span class="sxs-lookup"><span data-stu-id="369cb-182">1 Gb+</span></span>         | <span data-ttu-id="369cb-183">Numérique et texte</span><span class="sxs-lookup"><span data-stu-id="369cb-183">Numeric and Text</span></span>   | <span data-ttu-id="369cb-184">\+ de 3 heures</span><span class="sxs-lookup"><span data-stu-id="369cb-184">3 hour+</span></span>

1. <span data-ttu-id="369cb-185">Le fichier de données d’entraînement ayant une taille supérieure à 10 Mo, utilisez 600 secondes (10 minutes) comme valeur pour *Durée de l’entraînement (secondes)* .</span><span class="sxs-lookup"><span data-stu-id="369cb-185">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="369cb-186">Sélectionnez *Commencer l’entraînement*.</span><span class="sxs-lookup"><span data-stu-id="369cb-186">Select *Start Training*.</span></span>

<span data-ttu-id="369cb-187">Tout au long du processus d’entraînement, des données sur la progression s’affichent dans la section `Progress` de l’étape d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="369cb-187">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="369cb-188">Le champ État affiche l’état d’achèvement du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="369cb-188">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="369cb-189">Le champ Meilleure précision affiche la précision du modèle le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="369cb-189">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="369cb-190">Une précision plus élevée signifie que le modèle a prédit plus correctement sur les données de test.</span><span class="sxs-lookup"><span data-stu-id="369cb-190">Higher accuracy means the model predicted more correctly on test data.</span></span> 
- <span data-ttu-id="369cb-191">Le champ Meilleur algorithme affiche le nom de l’algorithme le plus performant trouvé jusqu’à présent par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="369cb-191">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="369cb-192">Le champ Dernier algorithme affiche le nom de l’algorithme le plus récemment utilisé par Model Builder pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="369cb-192">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="369cb-193">Une fois l’entraînement terminé, accédez à l’étape d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="369cb-193">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="369cb-194">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="369cb-194">Evaluate the model</span></span>

<span data-ttu-id="369cb-195">Le résultat de l’étape d’entraînement sera le modèle qui a eu les meilleures performances.</span><span class="sxs-lookup"><span data-stu-id="369cb-195">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="369cb-196">Dans l’étape d’évaluation de l’outil Model Builder, la section de la sortie contient l’algorithme utilisé par le modèle le plus performant dans l’entrée *Meilleur modèle* ainsi que des métriques dans *Meilleure qualité du modèle (RSquared)* .</span><span class="sxs-lookup"><span data-stu-id="369cb-196">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="369cb-197">Vous voyez aussi un tableau récapitulatif contenant les cinq meilleurs modèles et leurs métriques.</span><span class="sxs-lookup"><span data-stu-id="369cb-197">Additionally, a summary table containing top five models and their metrics.</span></span> <span data-ttu-id="369cb-198">Pour plus d’informations, consultez [Évaluation des métriques des modèles](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span><span class="sxs-lookup"><span data-stu-id="369cb-198">Visit the following link to learn more about [evaluating model metrics](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span></span>

<span data-ttu-id="369cb-199">Si vous n’êtes pas satisfait de vos métriques de précision, un moyen facile pour améliorer la précision du modèle consiste à augmenter la quantité de temps pour entraîner le modèle ou à utiliser plus de données.</span><span class="sxs-lookup"><span data-stu-id="369cb-199">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="369cb-200">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="369cb-200">Use the model for predictions</span></span>

<span data-ttu-id="369cb-201">Deux projets sont créés à la suite du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="369cb-201">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="369cb-202">TaxiFarePredictionML.ConsoleApp : Une application console .NET qui contient le code d’entraînement et d’utilisation du modèle.</span><span class="sxs-lookup"><span data-stu-id="369cb-202">TaxiFarePredictionML.ConsoleApp: A .NET Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="369cb-203">TaxiFarePredictionML.Model : Une bibliothèque de classes .NET Standard contenant les modèles de données qui définissent le schéma des données du modèle en entrée et en sortie, ainsi que la version enregistrée du modèle le plus performant lors de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="369cb-203">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="369cb-204">Dans la section du code de l’outil Model Builder, sélectionnez **Projets ajoutés** pour ajouter les projets à la solution.</span><span class="sxs-lookup"><span data-stu-id="369cb-204">In the code section of the Model Builder tool, select **Added Projects** to add the projects to the solution.</span></span>
1. <span data-ttu-id="369cb-205">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="369cb-205">In solution explorer, right-click the *TaxiFarePrediction* project.</span></span> <span data-ttu-id="369cb-206">Ensuite, sélectionnez **Ajouter > Élément existant**.</span><span class="sxs-lookup"><span data-stu-id="369cb-206">Then, select **Add > Existing Item**.</span></span> <span data-ttu-id="369cb-207">Dans la liste déroulante des types de fichiers, sélectionnez `All Files`, accédez au répertoire du projet *TaxiFarePredictionML.Model* et sélectionnez le fichier `MLModel.zip`.</span><span class="sxs-lookup"><span data-stu-id="369cb-207">For file type drop down, select `All Files`, navigate to the *TaxiFarePredictionML.Model* project directory and select the `MLModel.zip` file.</span></span> <span data-ttu-id="369cb-208">Ensuite, cliquez avec le bouton droit sur le fichier `MLModel.zip` récemment ajouté, puis sélectionnez *Propriétés*.</span><span class="sxs-lookup"><span data-stu-id="369cb-208">Then right-click the recently added `MLModel.zip` file and select *Properties*.</span></span> <span data-ttu-id="369cb-209">Pour l’option Copier dans le répertoire de sortie, sélectionnez *Copier si plus récent* dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="369cb-209">For the Copy to Output Directory option, select *Copy if Newer* from the dropdown.</span></span>
1. <span data-ttu-id="369cb-210">Cliquez avec le bouton droit sur le projet *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="369cb-210">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="369cb-211">Choisissez ensuite **Ajouter > Référence**.</span><span class="sxs-lookup"><span data-stu-id="369cb-211">Then, **Add > Reference**.</span></span> <span data-ttu-id="369cb-212">Choisissez le nœud **Projets > Solution** puis, dans la liste, cochez le projet *TaxiFarePredictionML.Model* et sélectionnez OK.</span><span class="sxs-lookup"><span data-stu-id="369cb-212">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>

4. <span data-ttu-id="369cb-213">Ouvrez le fichier *Program.cs* dans le projet *TaxiFarePrediction*.</span><span class="sxs-lookup"><span data-stu-id="369cb-213">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
5. <span data-ttu-id="369cb-214">Ajoutez les instructions using suivantes :</span><span class="sxs-lookup"><span data-stu-id="369cb-214">Add the following using statements:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. <span data-ttu-id="369cb-215">Ajoutez la méthode `ConsumeModel` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="369cb-215">Add the `ConsumeModel` method to the `Program` class.</span></span> <span data-ttu-id="369cb-216">Le `ConsumeModel` va créer un `PredictionEngine` basé sur le modèle généré par Model Builder pour effectuer des prédictions sur de nouvelles données et les afficher sur la console.</span><span class="sxs-lookup"><span data-stu-id="369cb-216">The `ConsumeModel` will create a `PredictionEngine` based on the model generated by Model Builder to make predictions on new data and print them out to the console.</span></span>

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

7. <span data-ttu-id="369cb-217">Ajoutez le code suivant à la méthode `Main` et exécutez l’application.</span><span class="sxs-lookup"><span data-stu-id="369cb-217">Add the following code to the `Main` method and run the application.</span></span>

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

    <span data-ttu-id="369cb-218">La sortie générée par le programme doit se présenter comme l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="369cb-218">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="369cb-219">Si vous devez référencer ultérieurement les projets générés à l’intérieur d’une autre solution, vous pouvez les trouver dans le répertoire `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`.</span><span class="sxs-lookup"><span data-stu-id="369cb-219">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="369cb-220">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="369cb-220">Next Steps</span></span>

<span data-ttu-id="369cb-221">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="369cb-221">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="369cb-222">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="369cb-222">Prepare and understand the data</span></span>
> * <span data-ttu-id="369cb-223">Choisir un scénario</span><span class="sxs-lookup"><span data-stu-id="369cb-223">Choose a scenario</span></span>
> * <span data-ttu-id="369cb-224">Charger les données</span><span class="sxs-lookup"><span data-stu-id="369cb-224">Load the data</span></span>
> * <span data-ttu-id="369cb-225">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="369cb-225">Train the model</span></span>
> * <span data-ttu-id="369cb-226">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="369cb-226">Evaluate the model</span></span>
> * <span data-ttu-id="369cb-227">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="369cb-227">Use the model for predictions</span></span>

<span data-ttu-id="369cb-228">Passez à l’un des articles de guide pratique suivants pour découvrir comment déployer votre modèle.</span><span class="sxs-lookup"><span data-stu-id="369cb-228">Advance to either of the following how-to articles to learn how to deploy your model.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="369cb-229">Déployer un modèle sur Azure Functions</span><span class="sxs-lookup"><span data-stu-id="369cb-229">Deploy a model to Azure Functions</span></span>](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="369cb-230">Déployer un modèle sur une API web</span><span class="sxs-lookup"><span data-stu-id="369cb-230">Deploy a model to a Web API</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
