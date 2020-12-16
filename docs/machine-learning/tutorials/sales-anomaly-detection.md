---
title: 'Didacticiel : détecter les anomalies dans les ventes de produits'
description: Découvrez comment créer une application de détection des anomalies pour des données de ventes de produit. Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio 2019.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 48a8b26409b20e2a01aa97425153336b34c9b5b7
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97594174"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="f44fc-104">Didacticiel : détecter les anomalies dans les ventes de produits avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="f44fc-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="f44fc-105">Découvrez comment créer une application de détection des anomalies pour des données de ventes de produit.</span><span class="sxs-lookup"><span data-stu-id="f44fc-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="f44fc-106">Ce didacticiel crée une application de console .NET Core à l’aide de C# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f44fc-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="f44fc-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="f44fc-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f44fc-108">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="f44fc-108">Load the data</span></span>
> * <span data-ttu-id="f44fc-109">Créer une transformation pour la détection d’anomalie de pics</span><span class="sxs-lookup"><span data-stu-id="f44fc-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="f44fc-110">Détecter des anomalies de pics avec la transformation</span><span class="sxs-lookup"><span data-stu-id="f44fc-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="f44fc-111">Créer une transformation pour la détection d’anomalie de points de changement</span><span class="sxs-lookup"><span data-stu-id="f44fc-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="f44fc-112">Détecter des anomalies de points de changement avec la transformation</span><span class="sxs-lookup"><span data-stu-id="f44fc-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="f44fc-113">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="f44fc-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f44fc-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f44fc-114">Prerequisites</span></span>

* <span data-ttu-id="f44fc-115">[Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="f44fc-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="f44fc-116">Jeu de données product-sales.csv</span><span class="sxs-lookup"><span data-stu-id="f44fc-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="f44fc-117">Le format de données dans `product-sales.csv` est basé sur le jeu de données « Shampoo Sales Over a Three Year Period », disponible sur DataMarket et fourni dans la bibliothèque TSDL (Time Series Data Library) créée par Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="f44fc-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="f44fc-118">Ce jeu de données est concédé sous la licence Open par défaut de DataMarket.</span><span class="sxs-lookup"><span data-stu-id="f44fc-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="f44fc-119">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="f44fc-119">Create a console application</span></span>

1. <span data-ttu-id="f44fc-120">Créez une **application console .NET Core** appelée « ProductSalesAnomalyDetection ».</span><span class="sxs-lookup"><span data-stu-id="f44fc-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="f44fc-121">Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers de votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="f44fc-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="f44fc-122">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="f44fc-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="f44fc-123">Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="f44fc-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="f44fc-124">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ml** , puis sélectionnez le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="f44fc-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="f44fc-125">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="f44fc-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="f44fc-126">Répétez ces étapes pour **Microsoft. ml. TimeSeries**.</span><span class="sxs-lookup"><span data-stu-id="f44fc-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="f44fc-127">Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="f44fc-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/sales-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="f44fc-128">Télécharger vos données</span><span class="sxs-lookup"><span data-stu-id="f44fc-128">Download your data</span></span>

1. <span data-ttu-id="f44fc-129">Téléchargez le jeu de données et enregistrez-le dans le dossier *Data* précédemment créé :</span><span class="sxs-lookup"><span data-stu-id="f44fc-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="f44fc-130">Cliquez avec le bouton droit sur [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».</span><span class="sxs-lookup"><span data-stu-id="f44fc-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="f44fc-131">Veillez à enregistrer le fichier \*.csv dans le dossier *Data* ou, si vous l’avez enregistré ailleurs, à déplacer le fichier \*.csv dans le dossier *Data*.</span><span class="sxs-lookup"><span data-stu-id="f44fc-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="f44fc-132">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier \*.csv et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f44fc-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="f44fc-133">Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="f44fc-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="f44fc-134">Le tableau suivant présente un aperçu des données de votre fichier \*.csv :</span><span class="sxs-lookup"><span data-stu-id="f44fc-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="f44fc-135">Month</span><span class="sxs-lookup"><span data-stu-id="f44fc-135">Month</span></span>  |<span data-ttu-id="f44fc-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="f44fc-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="f44fc-137">1 jan</span><span class="sxs-lookup"><span data-stu-id="f44fc-137">1-Jan</span></span>  |    <span data-ttu-id="f44fc-138">271</span><span class="sxs-lookup"><span data-stu-id="f44fc-138">271</span></span>      |
|<span data-ttu-id="f44fc-139">2 jan</span><span class="sxs-lookup"><span data-stu-id="f44fc-139">2-Jan</span></span>  |    <span data-ttu-id="f44fc-140">150,9</span><span class="sxs-lookup"><span data-stu-id="f44fc-140">150.9</span></span>    |
|<span data-ttu-id="f44fc-141">.....</span><span class="sxs-lookup"><span data-stu-id="f44fc-141">.....</span></span>  |    <span data-ttu-id="f44fc-142">.....</span><span class="sxs-lookup"><span data-stu-id="f44fc-142">.....</span></span>    |
|<span data-ttu-id="f44fc-143">1 fév</span><span class="sxs-lookup"><span data-stu-id="f44fc-143">1-Feb</span></span>  |    <span data-ttu-id="f44fc-144">199,3</span><span class="sxs-lookup"><span data-stu-id="f44fc-144">199.3</span></span>    |
|<span data-ttu-id="f44fc-145">.....</span><span class="sxs-lookup"><span data-stu-id="f44fc-145">.....</span></span>  |    <span data-ttu-id="f44fc-146">.....</span><span class="sxs-lookup"><span data-stu-id="f44fc-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="f44fc-147">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="f44fc-147">Create classes and define paths</span></span>

<span data-ttu-id="f44fc-148">Définissez à présent vos structures de données de classe d’entrée et de prédiction.</span><span class="sxs-lookup"><span data-stu-id="f44fc-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="f44fc-149">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="f44fc-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="f44fc-150">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="f44fc-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="f44fc-151">Dans la **boîte de dialogue Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="f44fc-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="f44fc-152">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f44fc-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="f44fc-153">Le fichier *ProductSalesData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="f44fc-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="f44fc-154">Ajoutez l’instruction `using` suivante en haut de *ProductSalesData.cs* :</span><span class="sxs-lookup"><span data-stu-id="f44fc-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="f44fc-155">Supprimez la définition de classe existante et ajoutez le code suivant, lequel contient deux classes (`ProductSalesData` et `ProductSalesPrediction`), au fichier *ProductSalesData.cs* :</span><span class="sxs-lookup"><span data-stu-id="f44fc-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/sales-anomaly-detection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="f44fc-156">`ProductSalesData` spécifie une classe de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44fc-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="f44fc-157">L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées.</span><span class="sxs-lookup"><span data-stu-id="f44fc-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="f44fc-158">`ProductSalesPrediction` spécifie la classe de données de prédiction.</span><span class="sxs-lookup"><span data-stu-id="f44fc-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="f44fc-159">Pour la détection d’anomalies, la prédiction est constituée d’une alerte indiquant s’il existe une anomalie, un score brut et une p-value.</span><span class="sxs-lookup"><span data-stu-id="f44fc-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="f44fc-160">Plus la p-value est proche de 0, plus il est probable qu’une anomalie existe.</span><span class="sxs-lookup"><span data-stu-id="f44fc-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="f44fc-161">Créez deux champs globaux pour le chemin du fichier de jeu de données téléchargé et celui du fichier de modèle enregistré :</span><span class="sxs-lookup"><span data-stu-id="f44fc-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="f44fc-162">`_dataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="f44fc-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="f44fc-163">`_docsize` contient le nombre d’enregistrements dans le fichier de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="f44fc-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="f44fc-164">Vous allez utiliser `_docSize` pour calculer `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="f44fc-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="f44fc-165">Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins :</span><span class="sxs-lookup"><span data-stu-id="f44fc-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](./snippets/sales-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="f44fc-166">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="f44fc-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="f44fc-167">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="f44fc-168">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="f44fc-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="f44fc-169">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="f44fc-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="f44fc-170">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="f44fc-170">Load the data</span></span>

<span data-ttu-id="f44fc-171">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="f44fc-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="f44fc-172">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="f44fc-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="f44fc-173">Les données peuvent être chargées à partir d’un fichier texte ou d’autres sources (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="f44fc-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="f44fc-174">Ajoutez le code suivant comme prochaine ligne de la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](./snippets/sales-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="f44fc-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="f44fc-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="f44fc-176">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="f44fc-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="f44fc-177">Détection des anomalies de série chronologique</span><span class="sxs-lookup"><span data-stu-id="f44fc-177">Time series anomaly detection</span></span>

<span data-ttu-id="f44fc-178">La détection d’anomalies signale des événements ou comportements inattendus ou inhabituels.</span><span class="sxs-lookup"><span data-stu-id="f44fc-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="f44fc-179">Elle fournit des indices sur la localisation des problèmes potentiels et vous aide à déterminer si une situation est « étrange ».</span><span class="sxs-lookup"><span data-stu-id="f44fc-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Exemple de détection d’anomalie « est-ce étrange ».](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="f44fc-181">La détection d’anomalie est le processus d’identification des valeurs hors norme dans une série chronologique donnée, c’est-à-dire les points dont le comportement est inattendu ou « étrange ».</span><span class="sxs-lookup"><span data-stu-id="f44fc-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="f44fc-182">La détection d’anomalie peut se révéler utile dans de nombreux cas.</span><span class="sxs-lookup"><span data-stu-id="f44fc-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="f44fc-183">Exemple :</span><span class="sxs-lookup"><span data-stu-id="f44fc-183">For instance:</span></span>

<span data-ttu-id="f44fc-184">Si vous disposez d’une voiture, vous souhaiterez peut-être en savoir : cette jauge d’huile est-elle normale ou est-ce que j’ai une fuite ?</span><span class="sxs-lookup"><span data-stu-id="f44fc-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="f44fc-185">Si vous surveillez la consommation d’énergie, voulez-vous en savoir : existe-t-il une panne ?</span><span class="sxs-lookup"><span data-stu-id="f44fc-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="f44fc-186">Vous pouvez détecter deux types d’anomalies dans les séries chronologiques :</span><span class="sxs-lookup"><span data-stu-id="f44fc-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="f44fc-187">Un **pic** correspond à la poussée temporaire d’un comportement anormal dans le système.</span><span class="sxs-lookup"><span data-stu-id="f44fc-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="f44fc-188">Un **point de changement** indique le début d’un changement persistant dans le système.</span><span class="sxs-lookup"><span data-stu-id="f44fc-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="f44fc-189">Dans ML.NET, les algorithmes de détection de pic ou de point de changement IID sont adaptés aux [jeux de données indépendants et identiquement distribués](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="f44fc-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="f44fc-190">Contrairement aux modèles des autres tutoriels, les transformations du détecteur d’anomalies de série chronologique opèrent directement sur les données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="f44fc-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="f44fc-191">La méthode `IEstimator.Fit()` n’a pas besoin de données d’entraînement pour produire la transformation.</span><span class="sxs-lookup"><span data-stu-id="f44fc-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="f44fc-192">Toutefois, elle a besoin du schéma de données, qui est fourni par une vue de données générée à partir d’une liste vide de `ProductSalesData`.</span><span class="sxs-lookup"><span data-stu-id="f44fc-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="f44fc-193">Vous allez analyser les mêmes données de ventes d’un produit pour détecter les pics et les points de changement.</span><span class="sxs-lookup"><span data-stu-id="f44fc-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="f44fc-194">Le processus de génération et d’entraînement du modèle est le même pour la détection des pics et des points de changement ; la principale différence réside dans l’algorithme de détection utilisé.</span><span class="sxs-lookup"><span data-stu-id="f44fc-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="f44fc-195">Détection des pics</span><span class="sxs-lookup"><span data-stu-id="f44fc-195">Spike detection</span></span>

<span data-ttu-id="f44fc-196">L’objectif est d’identifier les poussées d’activité, par définition soudaines et temporaires, qui diffèrent considérablement de la majorité des valeurs de données de la série chronologique.</span><span class="sxs-lookup"><span data-stu-id="f44fc-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="f44fc-197">Il est important de détecter au plus vite ces éléments, événements ou constats suspects pour pouvoir les minimiser.</span><span class="sxs-lookup"><span data-stu-id="f44fc-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="f44fc-198">Vous pouvez utiliser l’approche suivante pour détecter de nombreuses anomalies, notamment des pannes, des cyberattaques et du contenu web viral.</span><span class="sxs-lookup"><span data-stu-id="f44fc-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="f44fc-199">L’image suivante illustre des pics dans le jeu de données d’une série chronologique :</span><span class="sxs-lookup"><span data-stu-id="f44fc-199">The following image is an example of spikes in a time series dataset:</span></span>

![Capture d’écran montrant deux détections pic.](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="f44fc-201">Ajouter la méthode CreateEmptyDataView()</span><span class="sxs-lookup"><span data-stu-id="f44fc-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="f44fc-202">Ajoutez la méthode suivante à `Program.cs` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="f44fc-203">La méthode `CreateEmptyDataView()` produit un objet de vue de données vide avec le bon schéma à utiliser comme entrée à la méthode `IEstimator.Fit()`.</span><span class="sxs-lookup"><span data-stu-id="f44fc-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="f44fc-204">Créer la méthode DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="f44fc-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="f44fc-205">La méthode `DetectSpike()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="f44fc-206">Crée la transformation à partir de l’estimateur.</span><span class="sxs-lookup"><span data-stu-id="f44fc-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="f44fc-207">Détecte les pics par rapport aux données de ventes historiques.</span><span class="sxs-lookup"><span data-stu-id="f44fc-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="f44fc-208">Affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="f44fc-208">Displays the results.</span></span>

1. <span data-ttu-id="f44fc-209">Créez la méthode `DetectSpike()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="f44fc-210">Utilisez [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pour entraîner le modèle à la détection de pics.</span><span class="sxs-lookup"><span data-stu-id="f44fc-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="f44fc-211">Ajoutez-le à la méthode `DetectSpike()` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="f44fc-212">Créez la transformation de détection de pics en ajoutant ce qui suit comme ligne de code suivante dans la méthode `DetectSpike()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="f44fc-213">Ajoutez la ligne de code suivante pour transformer les données `productSales` comme prochaine ligne de la méthode `DetectSpike()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="f44fc-214">Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour prédire plusieurs lignes d’entrée d’un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="f44fc-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="f44fc-215">Convertissez votre `transformedData` en un type fortement typé `IEnumerable` pour un affichage plus facile à l’aide de la méthode [CreateEnumerable ()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-215">Convert your `transformedData` into a strongly typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="f44fc-216">Créez une ligne d’en-tête d’affichage à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="f44fc-217">Les informations suivantes apparaissent dans vos résultats de détection des pics :</span><span class="sxs-lookup"><span data-stu-id="f44fc-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="f44fc-218">`Alert` indique une alerte de pic pour un point de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="f44fc-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="f44fc-219">`Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="f44fc-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="f44fc-220">`P-Value` où « P » correspond à la probabilité.</span><span class="sxs-lookup"><span data-stu-id="f44fc-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="f44fc-221">Plus la p-value est proche de 0, plus il est probable que le point de données soit une anomalie.</span><span class="sxs-lookup"><span data-stu-id="f44fc-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="f44fc-222">Utilisez le code suivant pour itérer au sein de `predictions` `IEnumerable` et afficher les résultats :</span><span class="sxs-lookup"><span data-stu-id="f44fc-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="f44fc-223">Ajoutez l’appel à la méthode `DetectSpike()` dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="f44fc-224">Résultats de la détection des pics</span><span class="sxs-lookup"><span data-stu-id="f44fc-224">Spike detection results</span></span>

<span data-ttu-id="f44fc-225">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="f44fc-225">Your results should be similar to the following.</span></span> <span data-ttu-id="f44fc-226">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="f44fc-226">During processing, messages are displayed.</span></span> <span data-ttu-id="f44fc-227">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="f44fc-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f44fc-228">Certains messages ont été supprimés des résultats suivants par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="f44fc-228">Some of the messages have been removed from the following results for clarity.</span></span>

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a><span data-ttu-id="f44fc-229">Détection des points de changement</span><span class="sxs-lookup"><span data-stu-id="f44fc-229">Change point detection</span></span>

<span data-ttu-id="f44fc-230">Les points de changement (`Change points`) indiquent des changements persistants dans la distribution de valeurs d’un flux d’événements d’une série chronologique, comme des changements de niveau ou des tendances.</span><span class="sxs-lookup"><span data-stu-id="f44fc-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="f44fc-231">Ces changements persistants durent beaucoup plus longtemps que les pics (`spikes`) et peuvent indiquer des événements catastrophiques.</span><span class="sxs-lookup"><span data-stu-id="f44fc-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="f44fc-232">`Change points` ne sont généralement pas visibles à l’œil nu, mais vous pouvez les détecter dans vos données à l’aide d’approches comme celles décrites dans la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="f44fc-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="f44fc-233">L’image suivante illustre la détection des points de changement :</span><span class="sxs-lookup"><span data-stu-id="f44fc-233">The following image is an example of a change point detection:</span></span>

![Capture d’écran montrant une détection de point de modification.](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="f44fc-235">Créer la méthode DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="f44fc-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="f44fc-236">La méthode `DetectChangepoint()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="f44fc-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="f44fc-237">Crée la transformation à partir de l’estimateur.</span><span class="sxs-lookup"><span data-stu-id="f44fc-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="f44fc-238">Détecte les points de changement par rapport aux données de ventes historiques.</span><span class="sxs-lookup"><span data-stu-id="f44fc-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="f44fc-239">Affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="f44fc-239">Displays the results.</span></span>

1. <span data-ttu-id="f44fc-240">Créez la méthode `DetectChangepoint()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="f44fc-241">Créez [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) dans la méthode `DetectChangepoint()` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="f44fc-242">Comme vous l’avez fait précédemment, créez la transformation à partir de l’estimateur en ajoutant la ligne de code suivante dans la méthode `DetectChangePoint()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="f44fc-243">Utilisez la méthode `Transform()` pour transformer les données en ajoutant le code suivant à `DetectChangePoint()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="f44fc-244">Comme vous l’avez fait précédemment, convertissez votre `transformedData` en un type fortement typé `IEnumerable` pour un affichage plus facile à l’aide de la `CreateEnumerable()` méthode avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-244">As you did previously, convert your `transformedData` into a strongly typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="f44fc-245">Créez un en-tête d’affichage en ajoutant la ligne de code suivante comme prochaine ligne de la méthode `DetectChangePoint()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="f44fc-246">Les informations suivantes apparaissent dans vos résultats de détection des points de changement :</span><span class="sxs-lookup"><span data-stu-id="f44fc-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="f44fc-247">`Alert` indique une alerte de point de changement pour un point de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="f44fc-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="f44fc-248">`Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="f44fc-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="f44fc-249">`P-Value` où « P » correspond à la probabilité.</span><span class="sxs-lookup"><span data-stu-id="f44fc-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="f44fc-250">Plus la P-value est proche de 0, plus il est probable que le point de données soit une anomalie.</span><span class="sxs-lookup"><span data-stu-id="f44fc-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="f44fc-251">`Martingale value` permet d’identifier le « degré d’étrangeté » d’un point de données en fonction de la séquence de valeurs P.</span><span class="sxs-lookup"><span data-stu-id="f44fc-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="f44fc-252">Itérez au sein de `predictions` `IEnumerable` et affichez les résultats avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="f44fc-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="f44fc-253">Ajoutez l’appel suivant à la méthode `DetectChangepoint()` dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="f44fc-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="f44fc-254">Résultats de la détection des points de changement</span><span class="sxs-lookup"><span data-stu-id="f44fc-254">Change point detection results</span></span>

<span data-ttu-id="f44fc-255">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="f44fc-255">Your results should be similar to the following.</span></span> <span data-ttu-id="f44fc-256">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="f44fc-256">During processing, messages are displayed.</span></span> <span data-ttu-id="f44fc-257">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="f44fc-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="f44fc-258">Certains messages ont été supprimés des résultats suivants par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="f44fc-258">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

<span data-ttu-id="f44fc-259">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="f44fc-259">Congratulations!</span></span> <span data-ttu-id="f44fc-260">Vous venez de générer des modèles de machine learning pour détecter des anomalies (pics et points de changement) dans des données de ventes.</span><span class="sxs-lookup"><span data-stu-id="f44fc-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="f44fc-261">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="f44fc-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="f44fc-262">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="f44fc-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="f44fc-263">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="f44fc-263">Load the data</span></span>
> * <span data-ttu-id="f44fc-264">Entraîner le modèle pour détecter des pics</span><span class="sxs-lookup"><span data-stu-id="f44fc-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="f44fc-265">Détecter des pics avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="f44fc-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="f44fc-266">Entraîner le modèle pour détecter des points de changement</span><span class="sxs-lookup"><span data-stu-id="f44fc-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="f44fc-267">Détecter des points de changement avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="f44fc-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="f44fc-268">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f44fc-268">Next steps</span></span>

<span data-ttu-id="f44fc-269">Consultez Machine Learning le référentiel GitHub samples pour découvrir un exemple de détection d’anomalies de données saisonnier.</span><span class="sxs-lookup"><span data-stu-id="f44fc-269">Check out the Machine Learning samples GitHub repository to explore a seasonality data anomaly detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="f44fc-270">Référentiel GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="f44fc-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls)
