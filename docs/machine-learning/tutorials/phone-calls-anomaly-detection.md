---
title: 'Didacticiel : détecter les anomalies dans les appels téléphoniques'
description: Découvrez comment créer une application de détection des anomalies pour les données de séries chronologiques. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3451a44f8fa7ae85625687b7d52f120c411df1b6
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97634051"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a><span data-ttu-id="72ef6-104">Didacticiel : détecter les anomalies dans les séries chronologiques avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="72ef6-104">Tutorial: Detect anomalies in time series with ML.NET</span></span>

<span data-ttu-id="72ef6-105">Découvrez comment créer une application de détection des anomalies pour les données de séries chronologiques.</span><span class="sxs-lookup"><span data-stu-id="72ef6-105">Learn how to build an anomaly detection application for time series data.</span></span> <span data-ttu-id="72ef6-106">Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="72ef6-106">This tutorial creates a .NET Core console application using C# in Visual Studio 2019.</span></span>

<span data-ttu-id="72ef6-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="72ef6-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="72ef6-108">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="72ef6-108">Load the data</span></span>
> * <span data-ttu-id="72ef6-109">Détecter une période pour une série chronologique</span><span class="sxs-lookup"><span data-stu-id="72ef6-109">Detect period for a time series</span></span>
> * <span data-ttu-id="72ef6-110">Détectez les anomalies pour une série chronologique périodique</span><span class="sxs-lookup"><span data-stu-id="72ef6-110">Detect anomaly for a periodical time series</span></span>

<span data-ttu-id="72ef6-111">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="72ef6-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72ef6-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="72ef6-112">Prerequisites</span></span>

* <span data-ttu-id="72ef6-113">[Visual Studio 2019 version 16.7.8 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="72ef6-113">[Visual Studio 2019 version 16.7.8 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="72ef6-114">Jeu de données phone-calls.csv</span><span class="sxs-lookup"><span data-stu-id="72ef6-114">The phone-calls.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv)

## <a name="create-a-console-application"></a><span data-ttu-id="72ef6-115">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="72ef6-115">Create a console application</span></span>

1. <span data-ttu-id="72ef6-116">Créez une **application console C# .net Core** appelée « ProductSalesAnomalyDetection ».</span><span class="sxs-lookup"><span data-stu-id="72ef6-116">Create a **C# .NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="72ef6-117">Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers de votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="72ef6-117">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="72ef6-118">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="72ef6-118">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="72ef6-119">Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="72ef6-119">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="72ef6-120">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ml** , puis sélectionnez le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="72ef6-120">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="72ef6-121">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="72ef6-121">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="72ef6-122">Répétez ces étapes pour **Microsoft. ml. TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="72ef6-122">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="72ef6-123">Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="72ef6-123">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="72ef6-124">Télécharger vos données</span><span class="sxs-lookup"><span data-stu-id="72ef6-124">Download your data</span></span>

1. <span data-ttu-id="72ef6-125">Téléchargez le jeu de données et enregistrez-le dans le dossier *Data* précédemment créé :</span><span class="sxs-lookup"><span data-stu-id="72ef6-125">Download the dataset and save it to the *Data* folder you previously created:</span></span>

    <span data-ttu-id="72ef6-126">Cliquez avec le bouton droit sur [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv) , puis sélectionnez « Enregistrer le lien (ou la cible) en tant que... »</span><span class="sxs-lookup"><span data-stu-id="72ef6-126">Right click on [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrCnnDetection/Data/phone-calls.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="72ef6-127">Veillez à enregistrer le fichier \*.csv dans le dossier *Data* ou, si vous l’avez enregistré ailleurs, à déplacer le fichier \*.csv dans le dossier *Data*.</span><span class="sxs-lookup"><span data-stu-id="72ef6-127">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="72ef6-128">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier \*.csv et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="72ef6-128">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="72ef6-129">Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="72ef6-129">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="72ef6-130">Le tableau suivant présente un aperçu des données de votre fichier \*.csv :</span><span class="sxs-lookup"><span data-stu-id="72ef6-130">The following table is a data preview from your \*.csv file:</span></span>

| <span data-ttu-id="72ef6-131">timestamp</span><span class="sxs-lookup"><span data-stu-id="72ef6-131">timestamp</span></span>  | <span data-ttu-id="72ef6-132">value</span><span class="sxs-lookup"><span data-stu-id="72ef6-132">value</span></span> |
|--------|--------------|
| <span data-ttu-id="72ef6-133">2018/9/3</span><span class="sxs-lookup"><span data-stu-id="72ef6-133">2018/9/3</span></span>  | <span data-ttu-id="72ef6-134">36,69670857</span><span class="sxs-lookup"><span data-stu-id="72ef6-134">36.69670857</span></span>  |
| <span data-ttu-id="72ef6-135">2018/9/4</span><span class="sxs-lookup"><span data-stu-id="72ef6-135">2018/9/4</span></span>  | <span data-ttu-id="72ef6-136">35,74160571</span><span class="sxs-lookup"><span data-stu-id="72ef6-136">35.74160571</span></span>  |
| <span data-ttu-id="72ef6-137">.....</span><span class="sxs-lookup"><span data-stu-id="72ef6-137">.....</span></span>  | <span data-ttu-id="72ef6-138">.....</span><span class="sxs-lookup"><span data-stu-id="72ef6-138">.....</span></span>  |
| <span data-ttu-id="72ef6-139">2018/10/3</span><span class="sxs-lookup"><span data-stu-id="72ef6-139">2018/10/3</span></span>  | <span data-ttu-id="72ef6-140">34,49893429</span><span class="sxs-lookup"><span data-stu-id="72ef6-140">34.49893429</span></span>  |
| <span data-ttu-id="72ef6-141">...</span><span class="sxs-lookup"><span data-stu-id="72ef6-141">...</span></span>    | <span data-ttu-id="72ef6-142">....</span><span class="sxs-lookup"><span data-stu-id="72ef6-142">....</span></span>   |

<span data-ttu-id="72ef6-143">Ce fichier représente une série chronologique.</span><span class="sxs-lookup"><span data-stu-id="72ef6-143">This file represents a time-series.</span></span> <span data-ttu-id="72ef6-144">Chaque ligne du fichier est un point de données.</span><span class="sxs-lookup"><span data-stu-id="72ef6-144">Each row in the file is a data point.</span></span> <span data-ttu-id="72ef6-145">Chaque point de données a deux attributs, à savoir, `timestamp` et `value` , pour représenter le nombre d’appels téléphoniques à chaque jour.</span><span class="sxs-lookup"><span data-stu-id="72ef6-145">Each data point has two attributes, namely, `timestamp` and `value`, to represent the number of phone calls at each day.</span></span> <span data-ttu-id="72ef6-146">Le nombre d’appels téléphoniques est transformé en désensitivation.</span><span class="sxs-lookup"><span data-stu-id="72ef6-146">The number of phone calls is transformed to de-sensitivity.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="72ef6-147">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="72ef6-147">Create classes and define paths</span></span>

<span data-ttu-id="72ef6-148">Définissez à présent vos structures de données de classe d’entrée et de prédiction.</span><span class="sxs-lookup"><span data-stu-id="72ef6-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="72ef6-149">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="72ef6-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="72ef6-150">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="72ef6-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="72ef6-151">Dans la **boîte de dialogue Ajouter un nouvel élément**, sélectionnez **classe** et modifiez le champ **nom** en *PhoneCallsData.cs*.</span><span class="sxs-lookup"><span data-stu-id="72ef6-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *PhoneCallsData.cs*.</span></span> <span data-ttu-id="72ef6-152">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="72ef6-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="72ef6-153">Le fichier *PhoneCallsData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="72ef6-153">The *PhoneCallsData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="72ef6-154">Ajoutez l' `using` instruction suivante en haut de *PhoneCallsData.cs*:</span><span class="sxs-lookup"><span data-stu-id="72ef6-154">Add the following `using` statement to the top of *PhoneCallsData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="72ef6-155">Supprimez la définition de classe existante et ajoutez le code suivant, qui a deux classes `PhoneCallsData` et `PhoneCallsPrediction` , au fichier *PhoneCallsData.cs* :</span><span class="sxs-lookup"><span data-stu-id="72ef6-155">Remove the existing class definition and add the following code, which has two classes `PhoneCallsData` and `PhoneCallsPrediction`, to the *PhoneCallsData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="72ef6-156">`PhoneCallsData` spécifie une classe de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="72ef6-156">`PhoneCallsData` specifies an input data class.</span></span> <span data-ttu-id="72ef6-157">L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées.</span><span class="sxs-lookup"><span data-stu-id="72ef6-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="72ef6-158">Il a deux attributs `timestamp` et `value` qui correspondent aux mêmes attributs dans le fichier de données.</span><span class="sxs-lookup"><span data-stu-id="72ef6-158">It has two attributes `timestamp` and `value` that correspond to the same attributes in the data file.</span></span>

    <span data-ttu-id="72ef6-159">`PhoneCallsPrediction` spécifie la classe de données de prédiction.</span><span class="sxs-lookup"><span data-stu-id="72ef6-159">`PhoneCallsPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="72ef6-160">Pour le détecteur SR-CNN, la prédiction dépend du [mode de détection](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) spécifié.</span><span class="sxs-lookup"><span data-stu-id="72ef6-160">For SR-CNN detector, the prediction depends on the [detect mode](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) specified.</span></span> <span data-ttu-id="72ef6-161">Dans cet exemple, nous sélectionnons le `AnomalyAndMargin` mode.</span><span class="sxs-lookup"><span data-stu-id="72ef6-161">In this sample, we select the `AnomalyAndMargin` mode.</span></span> <span data-ttu-id="72ef6-162">La sortie contient sept colonnes.</span><span class="sxs-lookup"><span data-stu-id="72ef6-162">The output contains seven columns.</span></span> <span data-ttu-id="72ef6-163">Dans la plupart des cas,,,, `IsAnomaly` `ExpectedValue` `UpperBoundary` et `LowerBoundary` sont suffisamment informatifs.</span><span class="sxs-lookup"><span data-stu-id="72ef6-163">In most cases, `IsAnomaly`, `ExpectedValue`, `UpperBoundary`, and `LowerBoundary` are informative enough.</span></span> <span data-ttu-id="72ef6-164">Ils vous indiquent si un point est une anomalie, la valeur attendue du point et la région de limite inférieure/supérieure du point.</span><span class="sxs-lookup"><span data-stu-id="72ef6-164">They tell you if a point is an anomaly, the expected value of the point and the lower / upper boundary region of the point.</span></span>

5. <span data-ttu-id="72ef6-165">Ajoutez le code suivant à la ligne située juste au-dessus de la `Main` méthode pour spécifier le chemin d’accès à votre fichier de données :</span><span class="sxs-lookup"><span data-stu-id="72ef6-165">Add the following code to the line right above the `Main` method to specify the path to your data file:</span></span>

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="72ef6-166">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="72ef6-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="72ef6-167">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="72ef6-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="72ef6-168">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="72ef6-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="72ef6-169">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="72ef6-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="72ef6-170">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="72ef6-170">Load the data</span></span>

<span data-ttu-id="72ef6-171">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="72ef6-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="72ef6-172">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="72ef6-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="72ef6-173">Les données peuvent être chargées à partir d’un fichier texte ou d’autres sources (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="72ef6-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="72ef6-174">Ajoutez le code suivant comme prochaine ligne de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="72ef6-174">Add the following code as the next line of the `Main` method:</span></span>

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="72ef6-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="72ef6-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="72ef6-176">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="72ef6-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="72ef6-177">Détection des anomalies de série chronologique</span><span class="sxs-lookup"><span data-stu-id="72ef6-177">Time series anomaly detection</span></span>

<span data-ttu-id="72ef6-178">La détection des anomalies de série chronologique est le processus de détection des valeurs hors norme des données de série chronologique ; pointe sur une série chronologique d’entrée donnée où le comportement n’est pas celui attendu, ou « bizarre ».</span><span class="sxs-lookup"><span data-stu-id="72ef6-178">Time series anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span> <span data-ttu-id="72ef6-179">Ces anomalies sont généralement indicatives de certains événements intéressants dans le domaine du problème : une attaque contre les attaques contre les comptes d’utilisateur, une panne de courant, une augmentation de RPS sur un serveur, une fuite de mémoire, etc.</span><span class="sxs-lookup"><span data-stu-id="72ef6-179">These anomalies are typically indicative of some events of interest in the problem domain: a cyber-attack on user accounts, power outage, bursting RPS on a server, memory leak, etc.</span></span>

<span data-ttu-id="72ef6-180">Pour rechercher des anomalies sur les séries chronologiques, vous devez d’abord déterminer la période de la série.</span><span class="sxs-lookup"><span data-stu-id="72ef6-180">To find anomaly on time series, you should first determine the period of the series.</span></span> <span data-ttu-id="72ef6-181">Ensuite, la série chronologique peut être décomposée en plusieurs composants en tant que `Y = T + S + R` , où `Y` est la série d’origine, `T` est le composant de tendance, `S` est le composant saisonnier et `R` est la composante résiduelle de la série.</span><span class="sxs-lookup"><span data-stu-id="72ef6-181">Then, the time series can be decomposed into several components as `Y = T + S + R`, where `Y` is the original series, `T` is the trend component, `S` is the seasonal component, and `R` is the residual component of the series.</span></span> <span data-ttu-id="72ef6-182">Cette étape est appelée [décomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span><span class="sxs-lookup"><span data-stu-id="72ef6-182">This step is called [decomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span></span> <span data-ttu-id="72ef6-183">Enfin, la détection est effectuée sur le composant résiduel pour rechercher les anomalies.</span><span class="sxs-lookup"><span data-stu-id="72ef6-183">Finally, detection is performed on the residual component to find the anomalies.</span></span> <span data-ttu-id="72ef6-184">Dans ML.NET, l’algorithme SR-CNN est un algorithme avancé et un nouvel algorithme basé sur les réseaux de neurones spectraux et de convolution (CNN) pour détecter les anomalies dans les séries chronologiques.</span><span class="sxs-lookup"><span data-stu-id="72ef6-184">In ML.NET, The SR-CNN algorithm is an advanced and novel algorithm that is based on Spectral Residual (SR) and Convolutional Neural Network(CNN) to detect anomaly on time-series.</span></span> <span data-ttu-id="72ef6-185">Pour plus d’informations sur cet algorithme, consultez [service de détection des anomalies de série chronologique chez Microsoft](https://arxiv.org/pdf/1906.03821.pdf).</span><span class="sxs-lookup"><span data-stu-id="72ef6-185">For more information on this algorithm, see [Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf).</span></span>

<span data-ttu-id="72ef6-186">Dans ce didacticiel, vous verrez que ces procédures peuvent être effectuées à l’aide de deux fonctions.</span><span class="sxs-lookup"><span data-stu-id="72ef6-186">In this tutorial, you will see that these procedures can be completed using two functions.</span></span>

## <a name="detect-period"></a><span data-ttu-id="72ef6-187">Période de détection</span><span class="sxs-lookup"><span data-stu-id="72ef6-187">Detect Period</span></span>

<span data-ttu-id="72ef6-188">Dans la première étape, nous invoquons la `DetectSeasonality` fonction pour déterminer la période de la série.</span><span class="sxs-lookup"><span data-stu-id="72ef6-188">In the first step, we invoke the `DetectSeasonality` function to determine the period of the series.</span></span>

### <a name="create-the-detectperiod-method"></a><span data-ttu-id="72ef6-189">Créer la méthode DetectPeriod</span><span class="sxs-lookup"><span data-stu-id="72ef6-189">Create the DetectPeriod method</span></span>

1. <span data-ttu-id="72ef6-190">Créez la `DetectPeriod` méthode, juste en dessous de la `Main` méthode, à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="72ef6-190">Create the `DetectPeriod` method, just below the `Main` method, using the following code:</span></span>

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. <span data-ttu-id="72ef6-191">Utilisez la <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> fonction pour détecter une période.</span><span class="sxs-lookup"><span data-stu-id="72ef6-191">Use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> function to detect period.</span></span> <span data-ttu-id="72ef6-192">Ajoutez-le à la méthode `DetectPeriod` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="72ef6-192">Add it to the `DetectPeriod` method with the following code:</span></span>

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. <span data-ttu-id="72ef6-193">Affichez la valeur de période en ajoutant le code suivant à la ligne de code suivante dans la `DetectPeriod` méthode :</span><span class="sxs-lookup"><span data-stu-id="72ef6-193">Display the period value by adding the following as the next line of code in the `DetectPeriod` method:</span></span>

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. <span data-ttu-id="72ef6-194">Ajoutez l’appel suivant à la `DetectPeriod` méthode dans la `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="72ef6-194">Add the following call to the `DetectPeriod` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a><span data-ttu-id="72ef6-195">Résultats de la détection de période</span><span class="sxs-lookup"><span data-stu-id="72ef6-195">Period detection results</span></span>

<span data-ttu-id="72ef6-196">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="72ef6-196">Run the application.</span></span> <span data-ttu-id="72ef6-197">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="72ef6-197">Your results should be similar to the following.</span></span>

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a><span data-ttu-id="72ef6-198">Détecter les anomalies</span><span class="sxs-lookup"><span data-stu-id="72ef6-198">Detect Anomaly</span></span>

<span data-ttu-id="72ef6-199">Dans cette étape, vous utilisez la <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> méthode pour rechercher des anomalies.</span><span class="sxs-lookup"><span data-stu-id="72ef6-199">In this step, you use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> method to find anomalies.</span></span>

### <a name="create-the-detectanomaly-method"></a><span data-ttu-id="72ef6-200">Créer la méthode DetectAnomaly</span><span class="sxs-lookup"><span data-stu-id="72ef6-200">Create the DetectAnomaly method</span></span>

1. <span data-ttu-id="72ef6-201">Créez la `DetectAnomaly` méthode, juste en dessous de la `DetectPeriod` méthode, à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="72ef6-201">Create the `DetectAnomaly` method, just below the `DetectPeriod` method, using the following code:</span></span>

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. <span data-ttu-id="72ef6-202">Configurez <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> dans la `DetectAnomaly` méthode avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="72ef6-202">Set up <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> in the `DetectAnomaly` method with the following code:</span></span>

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. <span data-ttu-id="72ef6-203">Pour détecter les anomalies par algorithme SR-CNN, ajoutez la ligne de code suivante dans la `DetectAnomaly` méthode :</span><span class="sxs-lookup"><span data-stu-id="72ef6-203">Detect anomaly by SR-CNN algorithm by adding the following line of code in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. <span data-ttu-id="72ef6-204">Convertissez la vue des données de sortie en un type fortement typé `IEnumerable` pour faciliter l’affichage à l’aide de la [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) méthode avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="72ef6-204">Convert the output data view into a strongly typed `IEnumerable` for easier display using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. <span data-ttu-id="72ef6-205">Créez un en-tête d’affichage en ajoutant la ligne de code suivante comme prochaine ligne de la méthode `DetectAnomaly` :</span><span class="sxs-lookup"><span data-stu-id="72ef6-205">Create a display header with the following code as the next line in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    <span data-ttu-id="72ef6-206">Les informations suivantes apparaissent dans vos résultats de détection des points de changement :</span><span class="sxs-lookup"><span data-stu-id="72ef6-206">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="72ef6-207">`Index` est l’index de chaque point.</span><span class="sxs-lookup"><span data-stu-id="72ef6-207">`Index` is the index of each point.</span></span>
    * <span data-ttu-id="72ef6-208">`Anomaly` indique si chaque point est détecté comme une anomalie.</span><span class="sxs-lookup"><span data-stu-id="72ef6-208">`Anomaly` is the indicator of whether each point is detected as anomaly.</span></span>
    * <span data-ttu-id="72ef6-209">`ExpectedValue` valeur estimée de chaque point.</span><span class="sxs-lookup"><span data-stu-id="72ef6-209">`ExpectedValue` is the estimated value of each point.</span></span>
    * <span data-ttu-id="72ef6-210">`LowerBoundary` est la valeur la plus faible que chaque point peut être de ne pas être une anomalie.</span><span class="sxs-lookup"><span data-stu-id="72ef6-210">`LowerBoundary` is the lowest value each point can be to be not anomaly.</span></span>
    * <span data-ttu-id="72ef6-211">`UpperBoundary` est la valeur la plus élevée que chaque point peut être de ne pas être une anomalie.</span><span class="sxs-lookup"><span data-stu-id="72ef6-211">`UpperBoundary` is the highest value each point can be to be not anomaly.</span></span>

6. <span data-ttu-id="72ef6-212">Itérez au sein de `predictions` `IEnumerable` et affichez les résultats avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="72ef6-212">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. <span data-ttu-id="72ef6-213">Ajoutez l’appel suivant à la `DetectAnomaly` méthode dans la `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="72ef6-213">Add the following call to the `DetectAnomaly` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a><span data-ttu-id="72ef6-214">Résultats de la détection d’anomalies</span><span class="sxs-lookup"><span data-stu-id="72ef6-214">Anomaly detection results</span></span>

<span data-ttu-id="72ef6-215">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="72ef6-215">Run the application.</span></span> <span data-ttu-id="72ef6-216">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="72ef6-216">Your results should be similar to the following.</span></span> <span data-ttu-id="72ef6-217">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="72ef6-217">During processing, messages are displayed.</span></span> <span data-ttu-id="72ef6-218">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="72ef6-218">You may see warnings or processing messages.</span></span> <span data-ttu-id="72ef6-219">Certains messages ont été supprimés des résultats suivants par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="72ef6-219">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

<span data-ttu-id="72ef6-220">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="72ef6-220">Congratulations!</span></span> <span data-ttu-id="72ef6-221">Vous avez maintenant réussi à créer des modèles de Machine Learning pour détecter les périodes et les anomalies sur une série périodique.</span><span class="sxs-lookup"><span data-stu-id="72ef6-221">You've now successfully built machine learning models for detecting period and anomaly on a periodical series.</span></span>

<span data-ttu-id="72ef6-222">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="72ef6-222">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

<span data-ttu-id="72ef6-223">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="72ef6-223">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="72ef6-224">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="72ef6-224">Load the data</span></span>
> * <span data-ttu-id="72ef6-225">Détecter la période sur les données de la série chronologique</span><span class="sxs-lookup"><span data-stu-id="72ef6-225">Detect period on the time series data</span></span>
> * <span data-ttu-id="72ef6-226">Détecter les anomalies sur les données de série chronologique</span><span class="sxs-lookup"><span data-stu-id="72ef6-226">Detect anomaly on the time series data</span></span>

## <a name="next-steps"></a><span data-ttu-id="72ef6-227">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="72ef6-227">Next steps</span></span>

<span data-ttu-id="72ef6-228">Consultez le dépôt GitHub d’exemples de machine learning pour explorer un exemple de détection d’anomalie dans le domaine de la consommation d’énergie.</span><span class="sxs-lookup"><span data-stu-id="72ef6-228">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="72ef6-229">Référentiel GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="72ef6-229">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
