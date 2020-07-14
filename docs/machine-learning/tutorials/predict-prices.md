---
title: 'Didacticiel : prédire les prix à l’aide de la régression'
description: Ce tutoriel montre comment générer un modèle de régression avec ML.NET pour prédire des prix, plus précisément, des courses de taxi à New York.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 27054e28f9a4fa628f0d7348d45528b690d7da83
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281769"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="0984e-103">Didacticiel : prédire les prix à l’aide de la régression avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="0984e-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="0984e-104">Ce tutoriel montre comment créer un [modèle de régression](../resources/glossary.md#regression) avec ML.NET pour prédire des prix, plus précisément, des courses de taxi à New York.</span><span class="sxs-lookup"><span data-stu-id="0984e-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="0984e-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="0984e-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="0984e-106">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="0984e-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="0984e-107">Charger et transformer les données</span><span class="sxs-lookup"><span data-stu-id="0984e-107">Load and transform the data</span></span>
> * <span data-ttu-id="0984e-108">Choisir un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="0984e-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="0984e-109">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-109">Train the model</span></span>
> * <span data-ttu-id="0984e-110">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-110">Evaluate the model</span></span>
> * <span data-ttu-id="0984e-111">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="0984e-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0984e-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0984e-112">Prerequisites</span></span>

* <span data-ttu-id="0984e-113">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="0984e-113">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0984e-114">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="0984e-114">Create a console application</span></span>

1. <span data-ttu-id="0984e-115">Créez une **application console .NET Core** appelée « TaxiFarePrediction ».</span><span class="sxs-lookup"><span data-stu-id="0984e-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="0984e-116">Créez un répertoire nommé *Data* (Données) dans votre projet pour y stocker les fichiers du jeu de données et du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="0984e-117">Installez le package NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="0984e-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="0984e-118">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet et sélectionnez **gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="0984e-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0984e-119">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package dans la liste, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="0984e-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0984e-120">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="0984e-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="0984e-121">Procédez de la même façon pour le package NuGet **Microsoft. ml. FastTree** .</span><span class="sxs-lookup"><span data-stu-id="0984e-121">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0984e-122">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="0984e-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="0984e-123">Téléchargez les jeux de données [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) et [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv), puis enregistrez-les dans le dossier *Données* créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="0984e-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="0984e-124">Nous utilisons ces jeux de données pour le modèle Machine Learning et pour évaluer la précision du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="0984e-125">Ces jeux de données proviennent du [jeu de données NYC TLC Taxi Trip](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span><span class="sxs-lookup"><span data-stu-id="0984e-125">These data sets are originally from the [NYC TLC Taxi Trip data set](https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page).</span></span>

1. <span data-ttu-id="0984e-126">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur chacun des \* fichiers. csv et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0984e-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="0984e-127">Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="0984e-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="0984e-128">Ouvrez le jeu de données **taxi-fare-train.csv** et examinez les en-têtes de colonne dans la première ligne.</span><span class="sxs-lookup"><span data-stu-id="0984e-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="0984e-129">Examinons chacune des colonnes.</span><span class="sxs-lookup"><span data-stu-id="0984e-129">Take a look at each of the columns.</span></span> <span data-ttu-id="0984e-130">Analysez les données et identifiez les colonnes qui sont des **fonctionnalités** et celle qui est **l’étiquette**.</span><span class="sxs-lookup"><span data-stu-id="0984e-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="0984e-131">`label` est la colonne à prédire.</span><span class="sxs-lookup"><span data-stu-id="0984e-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="0984e-132">Les valeurs `Features` identifiées sont les entrées que vous fournissez au modèle pour prédire l’étiquette (`Label`).</span><span class="sxs-lookup"><span data-stu-id="0984e-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="0984e-133">Le jeu de données fourni contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0984e-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="0984e-134">**vendor_id :** l’ID du taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0984e-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="0984e-135">**rate_code :** le type de tarif de la course de taxi est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0984e-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="0984e-136">**passenger_count :** le nombre de passagers embarqués est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0984e-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="0984e-137">**trip_time_in_secs :** durée totale de la course.</span><span class="sxs-lookup"><span data-stu-id="0984e-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="0984e-138">Vous voulez prédire le prix de la course avant de l’effectuer.</span><span class="sxs-lookup"><span data-stu-id="0984e-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="0984e-139">À ce moment-là, vous ne savez pas combien de temps le trajet prendra.</span><span class="sxs-lookup"><span data-stu-id="0984e-139">At that moment, you don't know how long the trip would take.</span></span> <span data-ttu-id="0984e-140">Par conséquent, la durée de la course n’est pas une fonctionnalité et vous devez exclure cette colonne du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="0984e-141">**trip_distance :** la distance de la course est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0984e-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="0984e-142">**payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="0984e-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="0984e-143">**fare_amount :** le prix total payé pour la course est l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="0984e-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="0984e-144">Créer des classes de données</span><span class="sxs-lookup"><span data-stu-id="0984e-144">Create data classes</span></span>

<span data-ttu-id="0984e-145">Créez des classes pour les données d’entrée et les prédictions :</span><span class="sxs-lookup"><span data-stu-id="0984e-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="0984e-146">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="0984e-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="0984e-147">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *TaxiTrip.cs*.</span><span class="sxs-lookup"><span data-stu-id="0984e-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="0984e-148">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0984e-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="0984e-149">Ajoutez les directives `using` suivantes au nouveau fichier :</span><span class="sxs-lookup"><span data-stu-id="0984e-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](./snippets/predict-prices/csharp/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="0984e-150">Supprimez la définition de classe existante et ajoutez le code suivant, qui contient deux classes, `TaxiTrip` et `TaxiTripFarePrediction`, au fichier *TaxiTrip.cs* :</span><span class="sxs-lookup"><span data-stu-id="0984e-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](./snippets/predict-prices/csharp/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="0984e-151">`TaxiTrip` est la classe des données d’entrée et a des définitions pour chacune des colonnes du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="0984e-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="0984e-152">Utilisez l’attribut <xref:Microsoft.ML.Data.LoadColumnAttribute> pour spécifier les index des colonnes sources dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="0984e-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="0984e-153">La classe `TaxiTripFarePrediction` représente les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="0984e-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="0984e-154">Il possède un seul champ flottant, `FareAmount` , avec un `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribut appliqué.</span><span class="sxs-lookup"><span data-stu-id="0984e-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="0984e-155">Dans le cas de la tâche de régression, la colonne **score** contient des valeurs d’étiquette prédites.</span><span class="sxs-lookup"><span data-stu-id="0984e-155">In case of the regression task, the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="0984e-156">Utilisez le type `float` pour représenter les valeurs à virgule flottante dans les classes de données d’entrée et de prédiction.</span><span class="sxs-lookup"><span data-stu-id="0984e-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="0984e-157">Définir des chemins de données et de modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-157">Define data and model paths</span></span>

<span data-ttu-id="0984e-158">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : </span><span class="sxs-lookup"><span data-stu-id="0984e-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](./snippets/predict-prices/csharp/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="0984e-159">Il faut créer trois champs qui contiendront les chemins des fichiers comportant des jeux de données et le fichier permettant d’enregistrer le modèle :</span><span class="sxs-lookup"><span data-stu-id="0984e-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="0984e-160">`_trainDataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="0984e-161">`_testDataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’évaluation du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="0984e-162">`_modelPath` contient le chemin du fichier où le modèle formé est stocké.</span><span class="sxs-lookup"><span data-stu-id="0984e-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="0984e-163">Ajoutez le code suivant juste au-dessus de la méthode `Main` pour spécifier ces chemins et pour la variable `_textLoader` :</span><span class="sxs-lookup"><span data-stu-id="0984e-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](./snippets/predict-prices/csharp/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="0984e-164">Toutes les opérations de ML.NET commencent dans la [classe MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="0984e-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="0984e-165">L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="0984e-166">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0984e-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="0984e-167">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="0984e-167">Initialize variables in Main</span></span>

<span data-ttu-id="0984e-168">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="0984e-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](./snippets/predict-prices/csharp/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="0984e-169">Ajoutez le code suivant comme prochaine ligne dans la méthode `Main` afin d’appeler la méthode `Train` :</span><span class="sxs-lookup"><span data-stu-id="0984e-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](./snippets/predict-prices/csharp/Program.cs#5 "Train your model")]

<span data-ttu-id="0984e-170">La méthode `Train()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="0984e-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="0984e-171">Charge les données.</span><span class="sxs-lookup"><span data-stu-id="0984e-171">Loads the data.</span></span>
* <span data-ttu-id="0984e-172">Extrait et transforme les données.</span><span class="sxs-lookup"><span data-stu-id="0984e-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="0984e-173">Effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-173">Trains the model.</span></span>
* <span data-ttu-id="0984e-174">Retourne le modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-174">Returns the model.</span></span>

<span data-ttu-id="0984e-175">La méthode `Train` effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-175">The `Train` method trains the model.</span></span> <span data-ttu-id="0984e-176">Créez cette méthode juste en dessous de `Main`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="0984e-177">Charger et transformer les données</span><span class="sxs-lookup"><span data-stu-id="0984e-177">Load and transform data</span></span>

<span data-ttu-id="0984e-178">ML.NET utilise la [classe IDataView](xref:Microsoft.ML.IDataView) comme un moyen flexible et efficace de décrire des données tabulaires au format numérique ou texte.</span><span class="sxs-lookup"><span data-stu-id="0984e-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="0984e-179">`IDataView` peut charger des fichiers texte ou en temps réel (par exemple, une base de données SQL ou des fichiers journaux).</span><span class="sxs-lookup"><span data-stu-id="0984e-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="0984e-180">Ajoutez le code suivant comme première ligne de la méthode `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](./snippets/predict-prices/csharp/Program.cs#6 "loading training dataset")]

<span data-ttu-id="0984e-181">Au fur et à mesure que vous souhaitez prédire le tarif de la taxi, la `FareAmount` colonne est celle `Label` que vous prévoyez (la sortie du modèle).</span><span class="sxs-lookup"><span data-stu-id="0984e-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model).</span></span> <span data-ttu-id="0984e-182">Utilisez la `CopyColumnsEstimator` classe de transformation pour copier `FareAmount` et ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-182">Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](./snippets/predict-prices/csharp/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="0984e-183">L’algorithme qui forme le modèle requiert des fonctionnalités **numériques** . vous devez donc transformer les valeurs de données catégoriques (, `VendorId` `RateCode` et `PaymentType` ) en nombres ( `VendorIdEncoded` , `RateCodeEncoded` et `PaymentTypeEncoded` ).</span><span class="sxs-lookup"><span data-stu-id="0984e-183">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="0984e-184">Pour cela, utilisez la classe de transformation [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer), qui assigne différentes valeurs de clé numérique aux différentes valeurs de chaque colonne, puis ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-184">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](./snippets/predict-prices/csharp/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="0984e-185">La dernière étape de préparation des données regroupe toutes les colonnes de fonctionnalités dans la colonne **Fonctionnalités** à l’aide de la classe de transformation `mlContext.Transforms.Concatenate`.</span><span class="sxs-lookup"><span data-stu-id="0984e-185">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="0984e-186">Par défaut, un algorithme d’apprentissage traite uniquement les caractéristiques issues de la colonne **Features**.</span><span class="sxs-lookup"><span data-stu-id="0984e-186">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="0984e-187">Ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-187">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](./snippets/predict-prices/csharp/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="0984e-188">Choisir un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="0984e-188">Choose a learning algorithm</span></span>

<span data-ttu-id="0984e-189">Ce problème consiste à prédire le prix d’une course de taxi à New York.</span><span class="sxs-lookup"><span data-stu-id="0984e-189">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="0984e-190">À première vue, ce prix semble dépendre simplement de la distance parcourue.</span><span class="sxs-lookup"><span data-stu-id="0984e-190">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="0984e-191">Mais les chauffeurs de taxi à New York appliquent différents tarifs selon des facteurs comme le nombre de passagers supplémentaires ou le paiement par carte de crédit plutôt que par espèces.</span><span class="sxs-lookup"><span data-stu-id="0984e-191">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="0984e-192">Vous souhaitez prédire le prix, qui est une valeur réelle, en fonction des autres facteurs du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="0984e-192">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="0984e-193">Pour ce faire, choisissez une tâche de machine learning par [régression](../resources/glossary.md#regression).</span><span class="sxs-lookup"><span data-stu-id="0984e-193">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="0984e-194">Ajoutez la tâche de machine learning [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) aux définitions de transformation des données en ajoutant la ligne de code suivante dans `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-194">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](./snippets/predict-prices/csharp/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="0984e-195">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-195">Train the model</span></span>

<span data-ttu-id="0984e-196">Ajustez le modèle aux données d’entraînement `dataview` et retournez le modèle entraîné en ajoutant la ligne de code suivante à la méthode `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-196">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](./snippets/predict-prices/csharp/Program.cs#11 "Train the model")]

<span data-ttu-id="0984e-197">La méthode [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="0984e-197">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="0984e-198">Retournez le modèle entraîné avec la ligne suivante de code dans la méthode `Train()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-198">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](./snippets/predict-prices/csharp/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="0984e-199">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-199">Evaluate the model</span></span>

<span data-ttu-id="0984e-200">Ensuite, évaluez les performances de votre modèle avec vos données de test à des fins d’assurance qualité et de validation.</span><span class="sxs-lookup"><span data-stu-id="0984e-200">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="0984e-201">Créez la méthode `Evaluate()` juste après `Train()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-201">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0984e-202">La méthode `Evaluate` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="0984e-202">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="0984e-203">Charge le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="0984e-203">Loads the test dataset.</span></span>
* <span data-ttu-id="0984e-204">Crée l’évaluateur de régression.</span><span class="sxs-lookup"><span data-stu-id="0984e-204">Creates the regression evaluator.</span></span>
* <span data-ttu-id="0984e-205">Évalue le modèle et crée des métriques.</span><span class="sxs-lookup"><span data-stu-id="0984e-205">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="0984e-206">Affiche les métriques.</span><span class="sxs-lookup"><span data-stu-id="0984e-206">Displays the metrics.</span></span>

<span data-ttu-id="0984e-207">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `Train`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-207">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](./snippets/predict-prices/csharp/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="0984e-208">Chargez le jeu de données de test à l’aide de la méthode [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A).</span><span class="sxs-lookup"><span data-stu-id="0984e-208">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="0984e-209">Évaluez le modèle avec ce jeu de données afin d’en contrôler la qualité, en ajoutant le code suivant à la méthode `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="0984e-209">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](./snippets/predict-prices/csharp/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="0984e-210">Transformez ensuite les données `Test` en ajoutant le code suivant à `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-210">Next, transform the `Test` data by adding the following code to `Evaluate()`:</span></span>

[!code-csharp[PredictWithTransformer](./snippets/predict-prices/csharp/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="0984e-211">La méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) établit des prédictions pour les lignes d’entrée du jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="0984e-211">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="0984e-212">La méthode `RegressionContext.Evaluate` calcule les métriques de qualité pour `PredictionModel` à l’aide du jeu de données spécifié.</span><span class="sxs-lookup"><span data-stu-id="0984e-212">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="0984e-213">Elle retourne un objet <xref:Microsoft.ML.Data.RegressionMetrics> qui contient les métriques globales calculées par les évaluateurs de régression.</span><span class="sxs-lookup"><span data-stu-id="0984e-213">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span>

<span data-ttu-id="0984e-214">Pour afficher ces informations afin d’évaluer la qualité du modèle, vous devez d’abord obtenir les métriques.</span><span class="sxs-lookup"><span data-stu-id="0984e-214">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="0984e-215">Ajoutez le code suivant comme première ligne de la méthode `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="0984e-215">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](./snippets/predict-prices/csharp/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="0984e-216">Une fois que vous avez le jeu de prédiction, la méthode [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) évalue le modèle (elle compare les valeurs prédites aux `Labels` réelles dans le jeu de données de test et retourne des métriques relatives aux performances du modèle).</span><span class="sxs-lookup"><span data-stu-id="0984e-216">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="0984e-217">Ajoutez le code suivant pour évaluer le modèle et produire les métriques d’évaluation :</span><span class="sxs-lookup"><span data-stu-id="0984e-217">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="0984e-218">[RSquared](../resources/glossary.md#coefficient-of-determination) est une autre métrique d’évaluation des modèles de régression.</span><span class="sxs-lookup"><span data-stu-id="0984e-218">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="0984e-219">RSquared prend des valeurs entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="0984e-219">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="0984e-220">Plus sa valeur est proche de 1, plus le modèle est bon.</span><span class="sxs-lookup"><span data-stu-id="0984e-220">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="0984e-221">Ajoutez le code suivant dans la méthode `Evaluate` pour afficher la valeur RSquared :</span><span class="sxs-lookup"><span data-stu-id="0984e-221">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](./snippets/predict-prices/csharp/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="0984e-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) est une des métriques d’évaluation du modèle de régression.</span><span class="sxs-lookup"><span data-stu-id="0984e-222">[RMS](../resources/glossary.md#root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="0984e-223">Plus sa valeur est faible, plus le modèle est bon.</span><span class="sxs-lookup"><span data-stu-id="0984e-223">The lower it is, the better the model is.</span></span> <span data-ttu-id="0984e-224">Ajoutez le code suivant dans la méthode `Evaluate` pour afficher la valeur RMS :</span><span class="sxs-lookup"><span data-stu-id="0984e-224">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](./snippets/predict-prices/csharp/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="0984e-225">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="0984e-225">Use the model for predictions</span></span>

<span data-ttu-id="0984e-226">Créez la méthode `TestSinglePrediction` juste après la méthode `Evaluate`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-226">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0984e-227">La méthode `TestSinglePrediction` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="0984e-227">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="0984e-228">Crée un commentaire unique de données de test.</span><span class="sxs-lookup"><span data-stu-id="0984e-228">Creates a single comment of test data.</span></span>
* <span data-ttu-id="0984e-229">Prédit le prix de la course en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="0984e-229">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="0984e-230">Combine les données de test et les prédictions pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="0984e-230">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0984e-231">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="0984e-231">Displays the predicted results.</span></span>

<span data-ttu-id="0984e-232">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `Evaluate`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0984e-232">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](./snippets/predict-prices/csharp/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="0984e-233">Utilisez `PredictionEngine` pour prédire le prix de la course en ajoutant le code suivant à `TestSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-233">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](./snippets/predict-prices/csharp/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="0984e-234">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="0984e-234">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="0984e-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas thread-safe.</span><span class="sxs-lookup"><span data-stu-id="0984e-235">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="0984e-236">Il est acceptable d’utiliser dans des environnements à thread unique ou prototype.</span><span class="sxs-lookup"><span data-stu-id="0984e-236">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="0984e-237">Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="0984e-237">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="0984e-238">Pour plus d’informations sur l' [utilisation `PredictionEnginePool` de dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application), consultez ce guide.</span><span class="sxs-lookup"><span data-stu-id="0984e-238">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="0984e-239">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="0984e-239">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="0984e-240">Ce tutoriel utilise une course test au sein de cette classe.</span><span class="sxs-lookup"><span data-stu-id="0984e-240">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="0984e-241">Par la suite, vous pouvez ajouter d’autres scénarios à tester avec le modèle.</span><span class="sxs-lookup"><span data-stu-id="0984e-241">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="0984e-242">Ajoutez une course pour tester la prédiction de coût du modèle formé dans la méthode `TestSinglePrediction()` en créant une instance de `TaxiTrip` :</span><span class="sxs-lookup"><span data-stu-id="0984e-242">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](./snippets/predict-prices/csharp/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="0984e-243">Ensuite, prédisez le prix basé sur une instance unique des données d’une course de taxi et passez le résultat à `PredictionEngine` en ajoutant les lignes de code suivantes à la méthode `TestSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="0984e-243">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="0984e-244">La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) établit une prédiction sur une instance unique de données.</span><span class="sxs-lookup"><span data-stu-id="0984e-244">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="0984e-245">Pour afficher le prix prédit de la course spécifiée, ajoutez le code suivant à la méthode `TestSinglePrediction` :</span><span class="sxs-lookup"><span data-stu-id="0984e-245">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](./snippets/predict-prices/csharp/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="0984e-246">Exécutez le programme afin d’afficher le prix prédit de la course pour votre cas de test.</span><span class="sxs-lookup"><span data-stu-id="0984e-246">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="0984e-247">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="0984e-247">Congratulations!</span></span> <span data-ttu-id="0984e-248">Vous avez créé un modèle Machine Learning pour prédire le prix des courses de taxi, avez évalué sa précision et l’avez utilisé pour faire des prédictions.</span><span class="sxs-lookup"><span data-stu-id="0984e-248">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="0984e-249">Vous trouverez le code source de ce tutoriel dans le dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).</span><span class="sxs-lookup"><span data-stu-id="0984e-249">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0984e-250">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0984e-250">Next steps</span></span>

<span data-ttu-id="0984e-251">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="0984e-251">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0984e-252">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="0984e-252">Prepare and understand the data</span></span>
> * <span data-ttu-id="0984e-253">Créer un pipeline d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="0984e-253">Create a learning pipeline</span></span>
> * <span data-ttu-id="0984e-254">Charger et transformer les données</span><span class="sxs-lookup"><span data-stu-id="0984e-254">Load and transform the data</span></span>
> * <span data-ttu-id="0984e-255">Choisir un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="0984e-255">Choose a learning algorithm</span></span>
> * <span data-ttu-id="0984e-256">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-256">Train the model</span></span>
> * <span data-ttu-id="0984e-257">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="0984e-257">Evaluate the model</span></span>
> * <span data-ttu-id="0984e-258">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="0984e-258">Use the model for predictions</span></span>

<span data-ttu-id="0984e-259">Passez au tutoriel suivant pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="0984e-259">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0984e-260">Clustering Iris</span><span class="sxs-lookup"><span data-stu-id="0984e-260">Iris clustering</span></span>](iris-clustering.md)
