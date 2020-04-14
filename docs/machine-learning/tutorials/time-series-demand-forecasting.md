---
title: 'Tutorial: Prévisions de la demande de location de vélos - série de temps'
description: Ce tutoriel vous montre comment prévoir la demande pour un service de location de vélos en utilisant une analyse de la série temporelle et ML.NET.
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 962c40ea0536d6b6057d936cfc4b95a49ddadbf8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243282"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="050d5-103">Tutorial: Prévisions de la demande de service de location de vélos avec analyse des séries chrono temporelles et ML.NET</span><span class="sxs-lookup"><span data-stu-id="050d5-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="050d5-104">Découvrez comment prévoir la demande d’un service de location de vélos à l’aide d’analyses ponctuelles nonivate sur les données stockées dans une base de données SQL Server avec ML.NET.</span><span class="sxs-lookup"><span data-stu-id="050d5-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="050d5-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="050d5-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="050d5-106">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="050d5-106">Understand the problem</span></span>
> * <span data-ttu-id="050d5-107">Chargez les données d’une base de données</span><span class="sxs-lookup"><span data-stu-id="050d5-107">Load data from a database</span></span>
> * <span data-ttu-id="050d5-108">Créer un modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="050d5-108">Create a forecasting model</span></span>
> * <span data-ttu-id="050d5-109">Évaluer le modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="050d5-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="050d5-110">Enregistrer un modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="050d5-110">Save a forecasting model</span></span>
> * <span data-ttu-id="050d5-111">Utiliser un modèle de prévision</span><span class="sxs-lookup"><span data-stu-id="050d5-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="050d5-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="050d5-112">Prerequisites</span></span>

- <span data-ttu-id="050d5-113">[Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec le ".NET Core cross-platform development" charge de travail installé.</span><span class="sxs-lookup"><span data-stu-id="050d5-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="050d5-114">Aperçu de l’échantillon de prévision des séries chrono temporelles</span><span class="sxs-lookup"><span data-stu-id="050d5-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="050d5-115">Cet exemple est une **application de console de base C .NET** qui prévoit la demande de location de vélos à l’aide d’un algorithme d’analyse de séries chronomètres nonivate connu sous le nom d’analyse du spectre unique.</span><span class="sxs-lookup"><span data-stu-id="050d5-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="050d5-116">Le code de cet échantillon se trouve sur le référentiel [d’échantillons d’achat de points/machines](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="050d5-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="050d5-117">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="050d5-117">Understand the problem</span></span>

<span data-ttu-id="050d5-118">Afin d’exécuter une opération efficace, la gestion des stocks joue un rôle clé.</span><span class="sxs-lookup"><span data-stu-id="050d5-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="050d5-119">Avoir trop d’un produit en stock signifie des produits invendus assis sur les étagères ne générant pas de revenus.</span><span class="sxs-lookup"><span data-stu-id="050d5-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="050d5-120">Avoir trop peu de produits conduit à la perte de ventes et les clients d’acheter auprès de concurrents.</span><span class="sxs-lookup"><span data-stu-id="050d5-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="050d5-121">Par conséquent, la question constante est, quelle est la quantité optimale d’inventaire à garder sous la main?</span><span class="sxs-lookup"><span data-stu-id="050d5-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="050d5-122">L’analyse des séries chrono temporelles aide à répondre à ces questions en examinant les données historiques, en identifiant les tendances et en utilisant ces renseignements pour prévoir les valeurs dans le futur.</span><span class="sxs-lookup"><span data-stu-id="050d5-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="050d5-123">La technique d’analyse des données utilisées dans ce tutoriel est une analyse de séries chronoueuses non ivariée.</span><span class="sxs-lookup"><span data-stu-id="050d5-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="050d5-124">L’analyse de la série temporelle nonivate examine une seule observation numérique sur une période de temps à des intervalles précis tels que les ventes mensuelles.</span><span class="sxs-lookup"><span data-stu-id="050d5-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="050d5-125">L’algorithme utilisé dans ce tutoriel est [Single Spectrum Analysis (SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span><span class="sxs-lookup"><span data-stu-id="050d5-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="050d5-126">SSA travaille en décomposant une série temporelle en un ensemble de composants principaux.</span><span class="sxs-lookup"><span data-stu-id="050d5-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="050d5-127">Ces composants peuvent être interprétés comme les parties d’un signal qui correspondent aux tendances, au bruit, à la saisonnalité et à bien d’autres facteurs.</span><span class="sxs-lookup"><span data-stu-id="050d5-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="050d5-128">Ensuite, ces composants sont reconstruits et utilisés pour prévoir les valeurs dans le futur.</span><span class="sxs-lookup"><span data-stu-id="050d5-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="050d5-129">Création d’une application de console</span><span class="sxs-lookup"><span data-stu-id="050d5-129">Create console application</span></span>

1. <span data-ttu-id="050d5-130">Créez une nouvelle **application de console C .NET Core** appelée "BikeDemandForecasting".</span><span class="sxs-lookup"><span data-stu-id="050d5-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="050d5-131">Installer **Microsoft.ML** version **1.4.0** Paquet NuGet</span><span class="sxs-lookup"><span data-stu-id="050d5-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="050d5-132">Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="050d5-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="050d5-133">Choisissez "nuget.org" comme source de paquet, sélectionnez **l’onglet Parcourir,** recherchez **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="050d5-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="050d5-134">Vérifiez la case à cocher **prérelease Inclure.**</span><span class="sxs-lookup"><span data-stu-id="050d5-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="050d5-135">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="050d5-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="050d5-136">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="050d5-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="050d5-137">Répétez ces étapes pour **System.Data.SqlClient** version **4.7.0** et **Microsoft.ML.TimeSeries** version **1.4.0**.</span><span class="sxs-lookup"><span data-stu-id="050d5-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="050d5-138">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="050d5-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="050d5-139">Créer un répertoire appelé *Data*.</span><span class="sxs-lookup"><span data-stu-id="050d5-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="050d5-140">Téléchargez le fichier de base de données [ *DailyDemand.mdf* ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) et enregistrez-le sur le répertoire *Data.*</span><span class="sxs-lookup"><span data-stu-id="050d5-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="050d5-141">Les données utilisées dans ce tutoriel proviennent de [l’UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span><span class="sxs-lookup"><span data-stu-id="050d5-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="050d5-142">Fanaee-T, Hadi, et Gama, Joao, ' Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span><span class="sxs-lookup"><span data-stu-id="050d5-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="050d5-143">Le jeu de données d’origine contient plusieurs colonnes correspondant à la saisonnalité et aux conditions météorologiques.</span><span class="sxs-lookup"><span data-stu-id="050d5-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="050d5-144">Pour la brièveté et parce que l’algorithme utilisé dans ce tutoriel ne nécessite que les valeurs d’une seule colonne numérique, le jeu de données d’origine a été condensé pour inclure uniquement les colonnes suivantes:</span><span class="sxs-lookup"><span data-stu-id="050d5-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="050d5-145">**dteday**: La date de l’observation.</span><span class="sxs-lookup"><span data-stu-id="050d5-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="050d5-146">**année**: L’année codée de l’observation (0-2011, 1-2012).</span><span class="sxs-lookup"><span data-stu-id="050d5-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="050d5-147">**cnt**: Le nombre total de locations de vélos pour ce jour-là.</span><span class="sxs-lookup"><span data-stu-id="050d5-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="050d5-148">Le jeu de données d’origine est cartographié sur une table de base de données avec le schéma suivant dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="050d5-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="050d5-149">Voici un échantillon des données :</span><span class="sxs-lookup"><span data-stu-id="050d5-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="050d5-150">LocationDate</span><span class="sxs-lookup"><span data-stu-id="050d5-150">RentalDate</span></span> | <span data-ttu-id="050d5-151">Year</span><span class="sxs-lookup"><span data-stu-id="050d5-151">Year</span></span> | <span data-ttu-id="050d5-152">TotalRentals TotalRentals TotalRentals TotalRent</span><span class="sxs-lookup"><span data-stu-id="050d5-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="050d5-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="050d5-153">1/1/2011</span></span>|<span data-ttu-id="050d5-154">0</span><span class="sxs-lookup"><span data-stu-id="050d5-154">0</span></span>|<span data-ttu-id="050d5-155">985</span><span class="sxs-lookup"><span data-stu-id="050d5-155">985</span></span>|
|<span data-ttu-id="050d5-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="050d5-156">1/2/2011</span></span>|<span data-ttu-id="050d5-157">0</span><span class="sxs-lookup"><span data-stu-id="050d5-157">0</span></span>|<span data-ttu-id="050d5-158">801</span><span class="sxs-lookup"><span data-stu-id="050d5-158">801</span></span>|
|<span data-ttu-id="050d5-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="050d5-159">1/3/2011</span></span>|<span data-ttu-id="050d5-160">0</span><span class="sxs-lookup"><span data-stu-id="050d5-160">0</span></span>|<span data-ttu-id="050d5-161">1349</span><span class="sxs-lookup"><span data-stu-id="050d5-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="050d5-162">Créer des classes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="050d5-162">Create input and output classes</span></span>

1. <span data-ttu-id="050d5-163">Ouvrez *Program.cs* fichier et remplacez les relevés existants `using` par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="050d5-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="050d5-164">Créez la classe `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="050d5-164">Create `ModelInput` class.</span></span> <span data-ttu-id="050d5-165">Ci-dessous la `Program` classe, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="050d5-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="050d5-166">La `ModelInput` classe contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="050d5-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="050d5-167">**LocationDate**: La date de l’observation.</span><span class="sxs-lookup"><span data-stu-id="050d5-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="050d5-168">**Année**: L’année codée de l’observation (0-2011, 1-2012).</span><span class="sxs-lookup"><span data-stu-id="050d5-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="050d5-169">**TotalRentals**: Le nombre total de locations de vélos pour ce jour-là.</span><span class="sxs-lookup"><span data-stu-id="050d5-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="050d5-170">Créez `ModelOutput` une classe `ModelInput` en dessous de la classe nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="050d5-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="050d5-171">La `ModelOutput` classe contient les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="050d5-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="050d5-172">**PrévisionsRentales**: Les valeurs prévues pour la période prévue.</span><span class="sxs-lookup"><span data-stu-id="050d5-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="050d5-173">**LowerBoundRentals**: Les valeurs minimales prévues pour la période prévue.</span><span class="sxs-lookup"><span data-stu-id="050d5-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="050d5-174">**UpperBoundRentals**: Les valeurs maximales prévues pour la période prévue.</span><span class="sxs-lookup"><span data-stu-id="050d5-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="050d5-175">Définir les chemins et les variables d’initialisation</span><span class="sxs-lookup"><span data-stu-id="050d5-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="050d5-176">À `Main` l’intérieur de la méthode, définissez les variables pour stocker l’emplacement de vos données, de votre chaîne de connexion et où enregistrer le modèle qualifié.</span><span class="sxs-lookup"><span data-stu-id="050d5-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="050d5-177">Initialiser `mlContext` la variable avec [`MLContext`](xref:Microsoft.ML.MLContext) une nouvelle instance de `Main` en ajoutant la ligne suivante à la méthode.</span><span class="sxs-lookup"><span data-stu-id="050d5-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="050d5-178">La [`MLContext`](xref:Microsoft.ML.MLContext) classe est un point de départ pour toutes les opérations ML.NET, et l’initialisation mlContext crée un nouvel environnement ML.NET qui peut être partagé à travers les objets de flux de travail de création modèle.</span><span class="sxs-lookup"><span data-stu-id="050d5-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="050d5-179">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="050d5-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="050d5-180">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="050d5-180">Load the data</span></span>

1. <span data-ttu-id="050d5-181">Créer `DatabaseLoader` qui charge des `ModelInput`enregistrements de type .</span><span class="sxs-lookup"><span data-stu-id="050d5-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="050d5-182">Définissez la requête pour charger les données de la base de données.</span><span class="sxs-lookup"><span data-stu-id="050d5-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="050d5-183">ML.NET algorithmes s’attendent à [`Single`](xref:System.Single)ce que les données soient de type .</span><span class="sxs-lookup"><span data-stu-id="050d5-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="050d5-184">Par conséquent, les valeurs numériques provenant [`Real`](xref:System.Data.SqlDbType)de la base de données qui ne sont [`Real`](xref:System.Data.SqlDbType)pas de type , une valeur à point flottant de précision unique, doivent être converties en .</span><span class="sxs-lookup"><span data-stu-id="050d5-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="050d5-185">Les `Year` `TotalRental` colonnes et les colonnes sont toutes deux des types d’intégrerie dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="050d5-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="050d5-186">En `CAST` utilisant la fonction intégrée, ils `Real`sont tous deux jetés à .</span><span class="sxs-lookup"><span data-stu-id="050d5-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="050d5-187">Créez `DatabaseSource` un pour vous connecter à la base de données et exécuter la requête.</span><span class="sxs-lookup"><span data-stu-id="050d5-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="050d5-188">Chargez les données dans un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="050d5-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="050d5-189">Le jeu de données contient deux années de données.</span><span class="sxs-lookup"><span data-stu-id="050d5-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="050d5-190">Seules les données de la première année sont utilisées pour la formation, la deuxième année est prévue pour comparer les valeurs réelles avec les prévisions produites par le modèle.</span><span class="sxs-lookup"><span data-stu-id="050d5-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="050d5-191">Filtrer les [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) données à l’aide de la transformation.</span><span class="sxs-lookup"><span data-stu-id="050d5-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="050d5-192">Pour la première année, seules `Year` les valeurs de la colonne `upperBound` inférieures à 1 sont sélectionnées en définissant le paramètre à 1.</span><span class="sxs-lookup"><span data-stu-id="050d5-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="050d5-193">Inversement, pour la deuxième année, des valeurs supérieures ou `lowerBound` égales à 1 sont sélectionnées en fixant le paramètre à 1.</span><span class="sxs-lookup"><span data-stu-id="050d5-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="050d5-194">Décrivez le pipeline d’analyse des séries chronos</span><span class="sxs-lookup"><span data-stu-id="050d5-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="050d5-195">Définissez un pipeline qui utilise le [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) pour prévoir les valeurs dans un jeu de données de série temporelle.</span><span class="sxs-lookup"><span data-stu-id="050d5-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="050d5-196">Le `forecastingPipeline` prend 365 points de données pour la première année et échantillonne ou divise l’ensemble de `seriesLength` données de la série temporelle en intervalles de 30 jours (mensuels) comme spécifié par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="050d5-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="050d5-197">Chacun de ces échantillons est analysé par une fenêtre hebdomadaire ou de 7 jours.</span><span class="sxs-lookup"><span data-stu-id="050d5-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="050d5-198">Lors de la détermination de la valeur prévue pour la prochaine période,s, les valeurs des sept jours précédents sont utilisées pour faire une prédiction.</span><span class="sxs-lookup"><span data-stu-id="050d5-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="050d5-199">Le modèle est configuré pour prévoir sept `horizon` périodes dans l’avenir telles que définies par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="050d5-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="050d5-200">Parce qu’une prévision est une supposition éclairée, elle n’est pas toujours exacte à 100%.</span><span class="sxs-lookup"><span data-stu-id="050d5-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="050d5-201">Par conséquent, il est bon de connaître la gamme de valeurs dans les meilleurs et les pires scénarios tels que définis par les limites supérieures et inférieures.</span><span class="sxs-lookup"><span data-stu-id="050d5-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="050d5-202">Dans ce cas, le niveau de confiance pour les limites inférieures et supérieures est fixé à 95%.</span><span class="sxs-lookup"><span data-stu-id="050d5-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="050d5-203">Le niveau de confiance peut être augmenté ou diminué en conséquence.</span><span class="sxs-lookup"><span data-stu-id="050d5-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="050d5-204">Plus la valeur est élevée, plus la plage est large entre les limites supérieures et inférieures pour atteindre le niveau de confiance souhaité.</span><span class="sxs-lookup"><span data-stu-id="050d5-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="050d5-205">Utilisez [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) la méthode pour former le modèle et `forecastingPipeline`adapter les données à la définition préalable .</span><span class="sxs-lookup"><span data-stu-id="050d5-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="050d5-206">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="050d5-206">Evaluate the model</span></span>

<span data-ttu-id="050d5-207">Évaluez le rendement du modèle en prévoyant les données de l’année prochaine et en les comparant aux valeurs réelles.</span><span class="sxs-lookup"><span data-stu-id="050d5-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="050d5-208">Ci-dessous la `Main` méthode, créer `Evaluate`une nouvelle méthode d’utilité appelée .</span><span class="sxs-lookup"><span data-stu-id="050d5-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="050d5-209">À `Evaluate` l’intérieur de la méthode, prévoir [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) les données de la deuxième année en utilisant la méthode avec le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="050d5-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="050d5-210">Obtenez les valeurs réelles des [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) données en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="050d5-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="050d5-211">Obtenez les valeurs de [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) prévision en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="050d5-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="050d5-212">Calculez la différence entre les valeurs réelles et les valeurs de prévision, communément appelées l’erreur.</span><span class="sxs-lookup"><span data-stu-id="050d5-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="050d5-213">Mesurez les performances en calculant les valeurs d’erreur absolue moyenne et root Mean Squared Error.</span><span class="sxs-lookup"><span data-stu-id="050d5-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="050d5-214">Pour évaluer le rendement, les mesures suivantes sont utilisées :</span><span class="sxs-lookup"><span data-stu-id="050d5-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="050d5-215">**Erreur absolue moyenne**: Mesure la proximité des prédictions avec la valeur réelle.</span><span class="sxs-lookup"><span data-stu-id="050d5-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="050d5-216">Cette valeur varie entre 0 et l’infini.</span><span class="sxs-lookup"><span data-stu-id="050d5-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="050d5-217">Plus le plus proche de 0, mieux la qualité du modèle.</span><span class="sxs-lookup"><span data-stu-id="050d5-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="050d5-218">**Root Mean Squared Error**: résume l’erreur dans le modèle.</span><span class="sxs-lookup"><span data-stu-id="050d5-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="050d5-219">Cette valeur varie entre 0 et l’infini.</span><span class="sxs-lookup"><span data-stu-id="050d5-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="050d5-220">Plus le plus proche de 0, mieux la qualité du modèle.</span><span class="sxs-lookup"><span data-stu-id="050d5-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="050d5-221">Sortie des mesures à la console.</span><span class="sxs-lookup"><span data-stu-id="050d5-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="050d5-222">Utilisez `Evaluate` la méthode `Main` à l’intérieur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="050d5-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="050d5-223">Enregistrer le modèle</span><span class="sxs-lookup"><span data-stu-id="050d5-223">Save the model</span></span>

<span data-ttu-id="050d5-224">Si vous êtes satisfait de votre modèle, enregistrez-le pour une utilisation ultérieure dans d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="050d5-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="050d5-225">Dans `Main` la méthode, [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)créer un .</span><span class="sxs-lookup"><span data-stu-id="050d5-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="050d5-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)est une méthode de commodité pour faire des prédictions uniques.</span><span class="sxs-lookup"><span data-stu-id="050d5-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="050d5-227">Enregistrez le modèle `MLModel.zip` sur un fichier `modelPath` appelé comme spécifié par la variable précédemment définie.</span><span class="sxs-lookup"><span data-stu-id="050d5-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="050d5-228">Utilisez [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) la méthode pour enregistrer le modèle.</span><span class="sxs-lookup"><span data-stu-id="050d5-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="050d5-229">Utiliser le modèle pour prévoir la demande</span><span class="sxs-lookup"><span data-stu-id="050d5-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="050d5-230">Ci-dessous la `Evaluate` méthode, créer `Forecast`une nouvelle méthode d’utilité appelée .</span><span class="sxs-lookup"><span data-stu-id="050d5-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="050d5-231">À `Forecast` l’intérieur [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) de la méthode, utilisez la méthode pour prévoir les locations pour les sept prochains jours.</span><span class="sxs-lookup"><span data-stu-id="050d5-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="050d5-232">Alignez les valeurs réelles et prévisionnelles pendant sept périodes.</span><span class="sxs-lookup"><span data-stu-id="050d5-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="050d5-233">Itérer à travers la sortie de prévision et l’afficher sur la console.</span><span class="sxs-lookup"><span data-stu-id="050d5-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="050d5-234">Exécution de l'application</span><span class="sxs-lookup"><span data-stu-id="050d5-234">Run the application</span></span>

1. <span data-ttu-id="050d5-235">À `Main` l’intérieur `Forecast` de la méthode, appelez la méthode.</span><span class="sxs-lookup"><span data-stu-id="050d5-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="050d5-236">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="050d5-236">Run the application.</span></span> <span data-ttu-id="050d5-237">La sortie similaire à celle ci-dessous doit apparaître sur la console.</span><span class="sxs-lookup"><span data-stu-id="050d5-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="050d5-238">Pour la brièveté, la sortie a été condensée.</span><span class="sxs-lookup"><span data-stu-id="050d5-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="050d5-239">L’inspection des valeurs réelles et prévues montre les relations suivantes :</span><span class="sxs-lookup"><span data-stu-id="050d5-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![Comparaison réelle par rapport aux prévisions](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="050d5-241">Bien que les valeurs prévues ne prédisent pas le nombre exact de locations, elles fournissent une gamme plus étroite de valeurs qui permet à une opération d’optimiser leur utilisation des ressources.</span><span class="sxs-lookup"><span data-stu-id="050d5-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="050d5-242">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="050d5-242">Congratulations!</span></span> <span data-ttu-id="050d5-243">Vous avez maintenant construit avec succès un modèle d’apprentissage automatique de série temporelle pour prévoir la demande de location de vélos.</span><span class="sxs-lookup"><span data-stu-id="050d5-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="050d5-244">Vous pouvez trouver le code source pour ce tutoriel au référentiel [dotnet/machinelearning-échantillons.](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)</span><span class="sxs-lookup"><span data-stu-id="050d5-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="050d5-245">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="050d5-245">Next steps</span></span>

- [<span data-ttu-id="050d5-246">Tâches Machine Learning dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="050d5-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="050d5-247">Améliorer la précision du modèle</span><span class="sxs-lookup"><span data-stu-id="050d5-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
