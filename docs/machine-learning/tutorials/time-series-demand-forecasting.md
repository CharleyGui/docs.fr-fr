---
title: 'Didacticiel : prévoir une série chronologique de location de bicyclette'
description: Ce didacticiel vous montre comment prévoir la demande pour un service de location de bicyclettes à l’aide de l’analyse de série chronologique Student et ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 026421d7b1b2a0e39118ae712780ca7fc8f6e444
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921254"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="cbde5-103">Didacticiel : prévoir la demande du service de location de vélos avec l’analyse de série chronologique et ML.NET</span><span class="sxs-lookup"><span data-stu-id="cbde5-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="cbde5-104">Découvrez comment prévoir la demande d’un service de location de bicyclettes à l’aide de l’analyse de série chronologique Student sur les données stockées dans une base de données SQL Server avec ML.NET.</span><span class="sxs-lookup"><span data-stu-id="cbde5-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="cbde5-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="cbde5-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="cbde5-106">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="cbde5-106">Understand the problem</span></span>
> * <span data-ttu-id="cbde5-107">Charger des données à partir d’une base de données</span><span class="sxs-lookup"><span data-stu-id="cbde5-107">Load data from a database</span></span>
> * <span data-ttu-id="cbde5-108">Créer un modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="cbde5-108">Create a forecasting model</span></span>
> * <span data-ttu-id="cbde5-109">Évaluer le modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="cbde5-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="cbde5-110">Enregistrer un modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="cbde5-110">Save a forecasting model</span></span>
> * <span data-ttu-id="cbde5-111">Utiliser un modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="cbde5-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbde5-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="cbde5-112">Prerequisites</span></span>

- <span data-ttu-id="cbde5-113">[Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="cbde5-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="cbde5-114">Vue d’ensemble de l’exemple de prévision de séries chronologiques</span><span class="sxs-lookup"><span data-stu-id="cbde5-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="cbde5-115">Cet exemple est une  **C# application console .net Core** qui prévoit la demande de loyers de bicyclettes à l’aide d’un algorithme d’analyse de série chronologique Student appelé analyse de gamme unique.</span><span class="sxs-lookup"><span data-stu-id="cbde5-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="cbde5-116">Le code de cet exemple se trouve dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="cbde5-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="cbde5-117">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="cbde5-117">Understand the problem</span></span>

<span data-ttu-id="cbde5-118">Pour exécuter une opération efficace, la gestion des stocks joue un rôle clé.</span><span class="sxs-lookup"><span data-stu-id="cbde5-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="cbde5-119">Le fait d’avoir une trop grande partie d’un produit en stock signifie que les produits invendus se trouvent sur les étagères qui ne génèrent aucun chiffre d’affaires.</span><span class="sxs-lookup"><span data-stu-id="cbde5-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="cbde5-120">Le fait d’avoir trop peu de prospects pour les ventes et les clients qui achètent des produits concurrents.</span><span class="sxs-lookup"><span data-stu-id="cbde5-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="cbde5-121">Par conséquent, la question constante est, quelle est la quantité optimale d’inventaire à conserver en main ?</span><span class="sxs-lookup"><span data-stu-id="cbde5-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="cbde5-122">L’analyse des séries chronologiques vous aide à fournir une réponse à ces questions en examinant les données d’historique, en identifiant les modèles et en utilisant ces informations pour prévoir des valeurs à un moment donné dans le futur.</span><span class="sxs-lookup"><span data-stu-id="cbde5-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="cbde5-123">La technique d’analyse des données utilisée dans ce didacticiel est l’analyse de la série chronologique Student.</span><span class="sxs-lookup"><span data-stu-id="cbde5-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="cbde5-124">Les analyses de série chronologique Student examinent une seule observation numérique sur une période à des intervalles spécifiques tels que les ventes mensuelles.</span><span class="sxs-lookup"><span data-stu-id="cbde5-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="cbde5-125">L’algorithme utilisé dans ce didacticiel est l' [analyse à un seul spectre (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="cbde5-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="cbde5-126">La SSA fonctionne en décomposant une série chronologique en un ensemble de composants principaux.</span><span class="sxs-lookup"><span data-stu-id="cbde5-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="cbde5-127">Ces composants peuvent être interprétés comme les parties d’un signal qui correspondent aux tendances, au bruit, au caractère saisonnier et à de nombreux autres facteurs.</span><span class="sxs-lookup"><span data-stu-id="cbde5-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="cbde5-128">Ensuite, ces composants sont reconstruits et utilisés pour prévoir des valeurs à un moment donné dans le futur.</span><span class="sxs-lookup"><span data-stu-id="cbde5-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="cbde5-129">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="cbde5-129">Create console application</span></span>

1. <span data-ttu-id="cbde5-130">Créez une nouvelle  **C# application console .net Core** appelée « BikeDemandForecasting ».</span><span class="sxs-lookup"><span data-stu-id="cbde5-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="cbde5-131">Installer le package NuGet **1.4.0** version **Microsoft.ml**</span><span class="sxs-lookup"><span data-stu-id="cbde5-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="cbde5-132">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="cbde5-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="cbde5-133">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir** , puis recherchez **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="cbde5-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="cbde5-134">Cochez la case **inclure la version préliminaire** .</span><span class="sxs-lookup"><span data-stu-id="cbde5-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="cbde5-135">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="cbde5-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="cbde5-136">Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.</span><span class="sxs-lookup"><span data-stu-id="cbde5-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="cbde5-137">Répétez ces étapes pour **System. Data. SqlClient** version **4.7.0** et **Microsoft. ml. TimeSeries** version **1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="cbde5-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="cbde5-138">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="cbde5-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="cbde5-139">Créez un répertoire nommé *Data*.</span><span class="sxs-lookup"><span data-stu-id="cbde5-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="cbde5-140">Téléchargez le [fichier de base de données *DailyDemand. mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) et enregistrez-le dans le répertoire de *données* .</span><span class="sxs-lookup"><span data-stu-id="cbde5-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="cbde5-141">Les données utilisées dans ce didacticiel proviennent du jeu de données de [partage de bicyclette UCI](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="cbde5-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="cbde5-142">Fanaee-T, Hadi et Gama, Joao, 'étiquetage des événements combinaison de détecteurs d’ensembles et de connaissances en arrière-plan', progression de l’intelligence artificielle (2013) : pp. 1-15, Springer Link Berlin Heidelberg, [lien Web](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="cbde5-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="cbde5-143">Le jeu de données d’origine contient plusieurs colonnes correspondant à caractère saisonnier et météo.</span><span class="sxs-lookup"><span data-stu-id="cbde5-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="cbde5-144">Par souci de concision et parce que l’algorithme utilisé dans ce didacticiel nécessite uniquement les valeurs d’une colonne numérique unique, le jeu de données d’origine a été condensé pour inclure uniquement les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbde5-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="cbde5-145">**dteday**: date de l’observation.</span><span class="sxs-lookup"><span data-stu-id="cbde5-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="cbde5-146">**year**: année encodée de l’observation (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="cbde5-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="cbde5-147">**CNT**: nombre total d’loyers de bicyclettes pour ce jour-là.</span><span class="sxs-lookup"><span data-stu-id="cbde5-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="cbde5-148">Le DataSet d’origine est mappé à une table de base de données avec le schéma suivant dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cbde5-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="cbde5-149">Voici un exemple de données :</span><span class="sxs-lookup"><span data-stu-id="cbde5-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="cbde5-150">RentalDate</span><span class="sxs-lookup"><span data-stu-id="cbde5-150">RentalDate</span></span> | <span data-ttu-id="cbde5-151">Année</span><span class="sxs-lookup"><span data-stu-id="cbde5-151">Year</span></span> | <span data-ttu-id="cbde5-152">TotalRentals</span><span class="sxs-lookup"><span data-stu-id="cbde5-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="cbde5-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="cbde5-153">1/1/2011</span></span>|<span data-ttu-id="cbde5-154">0</span><span class="sxs-lookup"><span data-stu-id="cbde5-154">0</span></span>|<span data-ttu-id="cbde5-155">985</span><span class="sxs-lookup"><span data-stu-id="cbde5-155">985</span></span>|
|<span data-ttu-id="cbde5-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="cbde5-156">1/2/2011</span></span>|<span data-ttu-id="cbde5-157">0</span><span class="sxs-lookup"><span data-stu-id="cbde5-157">0</span></span>|<span data-ttu-id="cbde5-158">801</span><span class="sxs-lookup"><span data-stu-id="cbde5-158">801</span></span>|
|<span data-ttu-id="cbde5-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="cbde5-159">1/3/2011</span></span>|<span data-ttu-id="cbde5-160">0</span><span class="sxs-lookup"><span data-stu-id="cbde5-160">0</span></span>|<span data-ttu-id="cbde5-161">1349</span><span class="sxs-lookup"><span data-stu-id="cbde5-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="cbde5-162">Créer des classes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="cbde5-162">Create input and output classes</span></span>

1. <span data-ttu-id="cbde5-163">Ouvrez le fichier *Program.cs* et remplacez les instructions `using` existantes par ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="cbde5-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="cbde5-164">Créez `ModelInput` classe.</span><span class="sxs-lookup"><span data-stu-id="cbde5-164">Create `ModelInput` class.</span></span> <span data-ttu-id="cbde5-165">Sous la classe `Program`, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="cbde5-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="cbde5-166">La classe `ModelInput` contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbde5-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="cbde5-167">**RentalDate**: date de l’observation.</span><span class="sxs-lookup"><span data-stu-id="cbde5-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="cbde5-168">**Year**: année encodée de l’observation (0 = 2011, 1 = 2012).</span><span class="sxs-lookup"><span data-stu-id="cbde5-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="cbde5-169">**TotalRentals**: nombre total de loyers de vélo pour ce jour-là.</span><span class="sxs-lookup"><span data-stu-id="cbde5-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="cbde5-170">Créez `ModelOutput` classe sous la classe de `ModelInput` nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="cbde5-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="cbde5-171">La classe `ModelOutput` contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbde5-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="cbde5-172">**ForecastedRentals**: valeurs prédites pour la période prévue.</span><span class="sxs-lookup"><span data-stu-id="cbde5-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="cbde5-173">**LowerBoundRentals**: valeurs minimales prédites pour la période prévue.</span><span class="sxs-lookup"><span data-stu-id="cbde5-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="cbde5-174">**UpperBoundRentals**: valeurs maximales prédites pour la période prévue.</span><span class="sxs-lookup"><span data-stu-id="cbde5-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="cbde5-175">Définir des chemins d’accès et initialiser des variables</span><span class="sxs-lookup"><span data-stu-id="cbde5-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="cbde5-176">À l’intérieur de la méthode `Main`, définissez des variables pour stocker l’emplacement de vos données, la chaîne de connexion et l’emplacement où enregistrer le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="cbde5-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="cbde5-177">Initialisez la variable `mlContext` avec une nouvelle instance de [`MLContext`](xref:Microsoft.ML.MLContext) en ajoutant la ligne suivante à la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="cbde5-178">La classe [`MLContext`](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ml.net et l’initialisation de mlContext crée un nouvel environnement ml.net qui peut être partagé entre les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="cbde5-179">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cbde5-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="cbde5-180">Charger les données</span><span class="sxs-lookup"><span data-stu-id="cbde5-180">Load the data</span></span>

1. <span data-ttu-id="cbde5-181">Créez `DatabaseLoader` qui charge les enregistrements de type `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="cbde5-182">Définissez la requête pour charger les données à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="cbde5-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="cbde5-183">Les algorithmes ML.NET attendent que les données soient de type [`Single`](xref:System.Single).</span><span class="sxs-lookup"><span data-stu-id="cbde5-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="cbde5-184">Par conséquent, les valeurs numériques provenant de la base de données qui ne sont pas de type [`Real`](xref:System.Data.SqlDbType), une valeur à virgule flottante simple précision, doivent être converties en [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="cbde5-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="cbde5-185">Les colonnes `Year` et `TotalRental` sont à la fois des types entiers dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="cbde5-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="cbde5-186">À l’aide de la fonction intégrée `CAST`, elles sont toutes les deux transtypées en `Real`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="cbde5-187">Créez un `DatabaseSource` pour vous connecter à la base de données et exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="cbde5-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="cbde5-188">Charger les données dans un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="cbde5-189">Le jeu de données contient deux années de données.</span><span class="sxs-lookup"><span data-stu-id="cbde5-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="cbde5-190">Seules les données de la première année sont utilisées pour l’apprentissage, la deuxième année est conservée pour comparer les valeurs réelles par rapport aux prévisions produites par le modèle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="cbde5-191">Filtrez les données à l’aide de la transformation de [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) .</span><span class="sxs-lookup"><span data-stu-id="cbde5-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="cbde5-192">Pour la première année, seules les valeurs de la colonne `Year` inférieure à 1 sont sélectionnées en affectant la valeur 1 au paramètre `upperBound`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="cbde5-193">À l’inverse, pour la deuxième année, les valeurs supérieures ou égales à 1 sont sélectionnées en affectant la valeur 1 au paramètre `lowerBound`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="cbde5-194">Définir le pipeline d’analyse de série chronologique</span><span class="sxs-lookup"><span data-stu-id="cbde5-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="cbde5-195">Définissez un pipeline qui utilise [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) pour prévoir des valeurs dans un jeu de données de série chronologique.</span><span class="sxs-lookup"><span data-stu-id="cbde5-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="cbde5-196">La `forecastingPipeline` prend 365 points de données pour la première année et échantillonne ou divise le jeu de données de série chronologique en intervalles de 30 jours (mensuels), comme spécifié par le paramètre `seriesLength`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="cbde5-197">Chacun de ces exemples est analysé par une fenêtre hebdomadaire ou de 7 jours.</span><span class="sxs-lookup"><span data-stu-id="cbde5-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="cbde5-198">Lors de la détermination de la valeur prévue pour la ou les périodes suivantes, les valeurs des sept jours précédents sont utilisées pour effectuer une prédiction.</span><span class="sxs-lookup"><span data-stu-id="cbde5-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="cbde5-199">Le modèle est défini pour prévoir sept périodes dans le futur, comme défini par le paramètre `horizon`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="cbde5-200">Comme une prévision est une estimation réfléchie, elle n’est pas toujours de 100% précise.</span><span class="sxs-lookup"><span data-stu-id="cbde5-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="cbde5-201">Par conséquent, il est bon de connaître la plage de valeurs dans les scénarios les plus perversaux et les plus pessimistes, comme défini par les limites supérieure et inférieure.</span><span class="sxs-lookup"><span data-stu-id="cbde5-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="cbde5-202">Dans ce cas, le niveau de confiance pour les limites inférieure et supérieure est défini sur 95%.</span><span class="sxs-lookup"><span data-stu-id="cbde5-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="cbde5-203">Le niveau de confiance peut être augmenté ou réduit en conséquence.</span><span class="sxs-lookup"><span data-stu-id="cbde5-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="cbde5-204">Plus la valeur est élevée, plus la plage est large entre les limites supérieure et inférieure pour atteindre le niveau de confiance souhaité.</span><span class="sxs-lookup"><span data-stu-id="cbde5-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="cbde5-205">Utilisez la méthode [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) pour former le modèle et ajuster les données à la `forecastingPipeline`précédemment définie.</span><span class="sxs-lookup"><span data-stu-id="cbde5-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="cbde5-206">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="cbde5-206">Evaluate the model</span></span>

<span data-ttu-id="cbde5-207">Évaluez le comportement du modèle en prévoyant les données de l’année suivante et en les comparant aux valeurs réelles.</span><span class="sxs-lookup"><span data-stu-id="cbde5-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="cbde5-208">Sous la méthode `Main`, créez une nouvelle méthode utilitaire appelée `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="cbde5-209">À l’intérieur de la méthode `Evaluate`, planifiez les données de la deuxième année à l’aide de la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) avec le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="cbde5-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="cbde5-210">Récupérez les valeurs réelles à partir des données à l’aide de la méthode [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="cbde5-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="cbde5-211">Récupérez les valeurs de prévision à l’aide de la méthode [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) .</span><span class="sxs-lookup"><span data-stu-id="cbde5-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="cbde5-212">Calculez la différence entre les valeurs réelles et les valeurs de prévision, communément appelées « erreur ».</span><span class="sxs-lookup"><span data-stu-id="cbde5-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="cbde5-213">Mesurez les performances en calculant les valeurs d’erreur absolue moyenne et quadratique moyenne.</span><span class="sxs-lookup"><span data-stu-id="cbde5-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="cbde5-214">Pour évaluer les performances, les métriques suivantes sont utilisées :</span><span class="sxs-lookup"><span data-stu-id="cbde5-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="cbde5-215">**Erreur absolue moyenne**: mesure la manière dont les prédictions sont fermées à la valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="cbde5-216">Cette valeur est comprise entre 0 et l’infini.</span><span class="sxs-lookup"><span data-stu-id="cbde5-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="cbde5-217">Plus la valeur est proche de 0, meilleure est la qualité du modèle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="cbde5-218">**Erreur du carré moyen racine**: résume l’erreur dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="cbde5-219">Cette valeur est comprise entre 0 et l’infini.</span><span class="sxs-lookup"><span data-stu-id="cbde5-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="cbde5-220">Plus la valeur est proche de 0, meilleure est la qualité du modèle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="cbde5-221">Sortie des mesures vers la console.</span><span class="sxs-lookup"><span data-stu-id="cbde5-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="cbde5-222">Utilisez la méthode `Evaluate` à l’intérieur de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="cbde5-223">Enregistrer le modèle</span><span class="sxs-lookup"><span data-stu-id="cbde5-223">Save the model</span></span>

<span data-ttu-id="cbde5-224">Si vous êtes satisfait de votre modèle, enregistrez-le pour une utilisation ultérieure dans d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="cbde5-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="cbde5-225">Dans la méthode `Main`, créez un [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="cbde5-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="cbde5-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) est une méthode pratique pour effectuer des prédictions uniques.</span><span class="sxs-lookup"><span data-stu-id="cbde5-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="cbde5-227">Enregistrez le modèle dans un fichier appelé `MLModel.zip` tel que spécifié par la variable `modelPath` précédemment définie.</span><span class="sxs-lookup"><span data-stu-id="cbde5-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="cbde5-228">Utilisez la méthode [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) pour enregistrer le modèle.</span><span class="sxs-lookup"><span data-stu-id="cbde5-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="cbde5-229">Utiliser le modèle pour prévoir la demande</span><span class="sxs-lookup"><span data-stu-id="cbde5-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="cbde5-230">Sous la méthode `Evaluate`, créez une nouvelle méthode utilitaire appelée `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="cbde5-231">À l’intérieur de la méthode `Forecast`, utilisez la méthode [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) pour prévoir les loyers des sept prochains jours.</span><span class="sxs-lookup"><span data-stu-id="cbde5-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="cbde5-232">Alignez les valeurs réelles et les prévisions sur sept périodes.</span><span class="sxs-lookup"><span data-stu-id="cbde5-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="cbde5-233">Itérez au sein de la sortie de la prévision et affichez-la sur la console.</span><span class="sxs-lookup"><span data-stu-id="cbde5-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="cbde5-234">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="cbde5-234">Run the application</span></span>

1. <span data-ttu-id="cbde5-235">À l’intérieur de la méthode `Main`, appelez la méthode `Forecast`.</span><span class="sxs-lookup"><span data-stu-id="cbde5-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="cbde5-236">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="cbde5-236">Run the application.</span></span> <span data-ttu-id="cbde5-237">Une sortie semblable à celle ci-dessous doit apparaître sur la console.</span><span class="sxs-lookup"><span data-stu-id="cbde5-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="cbde5-238">Par souci de concision, la sortie a été condensée.</span><span class="sxs-lookup"><span data-stu-id="cbde5-238">For brevity, the output has been condensed.</span></span>

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

<span data-ttu-id="cbde5-239">L’inspection des valeurs réelles et prévues montre les relations suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbde5-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Comparaison entre les prévisions et les prévisions réelles](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="cbde5-241">Bien que les valeurs prévues ne prédisent pas le nombre exact de loyers, elles fournissent une plage de valeurs plus étroite qui permet à une opération d’optimiser son utilisation des ressources.</span><span class="sxs-lookup"><span data-stu-id="cbde5-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="cbde5-242">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="cbde5-242">Congratulations!</span></span> <span data-ttu-id="cbde5-243">Vous avez maintenant créé avec succès une série chronologique Machine Learning modèle pour prévoir la demande de location de bicyclette.</span><span class="sxs-lookup"><span data-stu-id="cbde5-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="cbde5-244">Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) .</span><span class="sxs-lookup"><span data-stu-id="cbde5-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cbde5-245">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbde5-245">Next steps</span></span>

- [<span data-ttu-id="cbde5-246">Tâches machine learning dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="cbde5-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="cbde5-247">Améliorer la précision du modèle</span><span class="sxs-lookup"><span data-stu-id="cbde5-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
