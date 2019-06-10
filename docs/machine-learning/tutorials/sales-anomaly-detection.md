---
title: Utiliser ML.NET pour détecter des anomalies dans un scénario de ventes
description: Apprenez à utiliser ML.NET pour détecter des anomalies dans un scénario de ventes d’un produit et découvrez comment identifier des pics et des points de changement dans les données afin de prendre les mesures appropriées.
ms.date: 05/29/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e092aea66ca9f439cf97c1ebee83097def0f520b
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758796"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a><span data-ttu-id="2c3af-103">Tutoriel : Utiliser ML.NET pour détecter des anomalies dans les ventes d’un produit</span><span class="sxs-lookup"><span data-stu-id="2c3af-103">Tutorial: Use ML.NET for product sales anomaly detection</span></span> 

<span data-ttu-id="2c3af-104">Ce tutoriel montre comment utiliser ML.NET pour détecter des anomalies dans les données de ventes d’un produit afin de prendre les mesures appropriées. Pour cela, vous allez créer une application console .NET Core en C# dans Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2c3af-104">This sample tutorial illustrates using ML.NET to detect anomalies in product sales data to take the appropriate action via a .NET Core console application using C# in Visual Studio 2019.</span></span> 

<span data-ttu-id="2c3af-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="2c3af-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2c3af-106">Charger les données</span><span class="sxs-lookup"><span data-stu-id="2c3af-106">Load the data</span></span>
> * <span data-ttu-id="2c3af-107">Entraîner le modèle pour détecter des pics</span><span class="sxs-lookup"><span data-stu-id="2c3af-107">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="2c3af-108">Détecter des pics avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="2c3af-108">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="2c3af-109">Entraîner le modèle pour détecter des points de changement</span><span class="sxs-lookup"><span data-stu-id="2c3af-109">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="2c3af-110">Détecter des points de changement avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="2c3af-110">Detect change point anomalies with the trained model</span></span>

<span data-ttu-id="2c3af-111">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="2c3af-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c3af-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="2c3af-112">Prerequisites</span></span>

* <span data-ttu-id="2c3af-113">[Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="2c3af-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="2c3af-114">Jeu de données product-sales.csv</span><span class="sxs-lookup"><span data-stu-id="2c3af-114">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="2c3af-115">Le format de données dans `product-sales.csv` est basé sur le jeu de données « Shampoo Sales Over a Three Year Period », disponible sur DataMarket et fourni dans la bibliothèque TSDL (Time Series Data Library) créée par Rob Hyndman.</span><span class="sxs-lookup"><span data-stu-id="2c3af-115">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span> <span data-ttu-id="2c3af-116">Ce jeu de données est concédé sous la licence Open par défaut de DataMarket.</span><span class="sxs-lookup"><span data-stu-id="2c3af-116">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2c3af-117">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="2c3af-117">Create a console application</span></span>

1. <span data-ttu-id="2c3af-118">Créez une **application console .NET Core** appelée « ProductSalesAnomalyDetection ».</span><span class="sxs-lookup"><span data-stu-id="2c3af-118">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="2c3af-119">Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="2c3af-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="2c3af-120">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="2c3af-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2c3af-121">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2c3af-122">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez le package **v1.0.0** dans la liste, puis cliquez sur le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-122">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="2c3af-123">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="2c3af-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="2c3af-124">Répétez ces étapes pour **Microsoft.ML.TimeSeries v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-124">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="2c3af-125">Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="2c3af-125">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="2c3af-126">Télécharger vos données</span><span class="sxs-lookup"><span data-stu-id="2c3af-126">Download your data</span></span>

1. <span data-ttu-id="2c3af-127">Téléchargez le jeu de données et enregistrez-le dans le dossier *Data* précédemment créé :</span><span class="sxs-lookup"><span data-stu-id="2c3af-127">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="2c3af-128">Cliquez avec le bouton droit sur [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».</span><span class="sxs-lookup"><span data-stu-id="2c3af-128">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="2c3af-129">Veillez à enregistrer le fichier \*.csv dans le dossier *Data* ou, si vous l’avez enregistré ailleurs, à déplacer le fichier \*.csv dans le dossier *Data*.</span><span class="sxs-lookup"><span data-stu-id="2c3af-129">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="2c3af-130">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier \*.csv et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-130">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="2c3af-131">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-131">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="2c3af-132">Le tableau suivant présente un aperçu des données de votre fichier \*.csv :</span><span class="sxs-lookup"><span data-stu-id="2c3af-132">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="2c3af-133">Mois</span><span class="sxs-lookup"><span data-stu-id="2c3af-133">Month</span></span>  |<span data-ttu-id="2c3af-134">ProductSales</span><span class="sxs-lookup"><span data-stu-id="2c3af-134">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="2c3af-135">1 jan</span><span class="sxs-lookup"><span data-stu-id="2c3af-135">1-Jan</span></span>  |    <span data-ttu-id="2c3af-136">271</span><span class="sxs-lookup"><span data-stu-id="2c3af-136">271</span></span>      |
|<span data-ttu-id="2c3af-137">2 jan</span><span class="sxs-lookup"><span data-stu-id="2c3af-137">2-Jan</span></span>  |    <span data-ttu-id="2c3af-138">150,9</span><span class="sxs-lookup"><span data-stu-id="2c3af-138">150.9</span></span>    |
|<span data-ttu-id="2c3af-139">.....</span><span class="sxs-lookup"><span data-stu-id="2c3af-139">.....</span></span>  |    <span data-ttu-id="2c3af-140">.....</span><span class="sxs-lookup"><span data-stu-id="2c3af-140">.....</span></span>    |
|<span data-ttu-id="2c3af-141">1 fév</span><span class="sxs-lookup"><span data-stu-id="2c3af-141">1-Feb</span></span>  |    <span data-ttu-id="2c3af-142">199,3</span><span class="sxs-lookup"><span data-stu-id="2c3af-142">199.3</span></span>    |
|<span data-ttu-id="2c3af-143">.....</span><span class="sxs-lookup"><span data-stu-id="2c3af-143">.....</span></span>  |    <span data-ttu-id="2c3af-144">.....</span><span class="sxs-lookup"><span data-stu-id="2c3af-144">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="2c3af-145">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="2c3af-145">Create classes and define paths</span></span>

<span data-ttu-id="2c3af-146">Définissez à présent la structure de données de votre classe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2c3af-146">Next, define your input class data structure.</span></span>

<span data-ttu-id="2c3af-147">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="2c3af-147">Add a new class to your project:</span></span>

1. <span data-ttu-id="2c3af-148">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-148">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="2c3af-149">Dans la **boîte de dialogue Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *ProductSalesData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2c3af-149">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="2c3af-150">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2c3af-150">Then, select the **Add** button.</span></span>

<span data-ttu-id="2c3af-151">Le fichier *ProductSalesData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="2c3af-151">The *ProductSalesData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2c3af-152">Ajoutez l’instruction `using` suivante en haut de *ProductSalesData.cs* :</span><span class="sxs-lookup"><span data-stu-id="2c3af-152">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="2c3af-153">Supprimez la définition de classe existante et ajoutez le code suivant, lequel contient deux classes (`ProductSalesData` et `ProductSalesPrediction`), au fichier *ProductSalesData.cs* :</span><span class="sxs-lookup"><span data-stu-id="2c3af-153">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="2c3af-154">`ProductSalesData` spécifie une classe de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="2c3af-154">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="2c3af-155">L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées.</span><span class="sxs-lookup"><span data-stu-id="2c3af-155">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> 

<span data-ttu-id="2c3af-156">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="2c3af-156">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="2c3af-157">Il faut créer deux champs globaux pour le chemin d’accès du fichier de jeu de données téléchargé et celui du fichier de modèle enregistré :</span><span class="sxs-lookup"><span data-stu-id="2c3af-157">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="2c3af-158">`_dataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="2c3af-158">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="2c3af-159">`_docsize` contient le nombre d’enregistrements dans le fichier de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="2c3af-159">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="2c3af-160">Vous allez l’utiliser pour calculer `pvalueHistoryLength`.</span><span class="sxs-lookup"><span data-stu-id="2c3af-160">You'll use this to calculate `pvalueHistoryLength`.</span></span>

<span data-ttu-id="2c3af-161">Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins :</span><span class="sxs-lookup"><span data-stu-id="2c3af-161">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="2c3af-162">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="2c3af-162">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2c3af-163">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2c3af-163">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="2c3af-164">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="2c3af-164">Initialize variables in Main</span></span>

<span data-ttu-id="2c3af-165">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-165">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a><span data-ttu-id="2c3af-166">Charger les données</span><span class="sxs-lookup"><span data-stu-id="2c3af-166">Load the data</span></span>

<span data-ttu-id="2c3af-167">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="2c3af-167">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="2c3af-168">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="2c3af-168">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="2c3af-169">Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="2c3af-169">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span> <span data-ttu-id="2c3af-170">Ajoutez le code suivant comme prochaine ligne de la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-170">Add the following code as the next line of the `Main()` method:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

<span data-ttu-id="2c3af-171">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="2c3af-171">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="2c3af-172">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="2c3af-172">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="ml-task---time-series-anomaly-detection"></a><span data-ttu-id="2c3af-173">Tâche ML - Détection d’anomalie dans une série chronologique</span><span class="sxs-lookup"><span data-stu-id="2c3af-173">ML task - time series anomaly detection</span></span> 

<span data-ttu-id="2c3af-174">La détection d’anomalie signale des événements ou des comportements inattendus ou inhabituels.</span><span class="sxs-lookup"><span data-stu-id="2c3af-174">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="2c3af-175">Elle fournit des indices sur la localisation des problèmes potentiels et vous aide à déterminer si une situation est « étrange ».</span><span class="sxs-lookup"><span data-stu-id="2c3af-175">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![Cette situation est-elle étrange ?](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="2c3af-177">La détection d’anomalie est le processus d’identification des valeurs hors norme dans une série chronologique donnée, c’est-à-dire les points dont le comportement est inattendu ou « étrange ».</span><span class="sxs-lookup"><span data-stu-id="2c3af-177">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="2c3af-178">Cela peut être utile à bien des égards.</span><span class="sxs-lookup"><span data-stu-id="2c3af-178">This can be useful in lots of ways.</span></span> <span data-ttu-id="2c3af-179">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2c3af-179">For instance:</span></span>

<span data-ttu-id="2c3af-180">Si vous avez une voiture, il est bon de savoir si l’indicateur de niveau d’huile est normal ou si vous avez une fuite.</span><span class="sxs-lookup"><span data-stu-id="2c3af-180">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="2c3af-181">Si vous analysez la consommation d’énergie, il est important de connaître l’existence d’une panne.</span><span class="sxs-lookup"><span data-stu-id="2c3af-181">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="2c3af-182">Vous pouvez détecter deux types d’anomalies dans les séries chronologiques :</span><span class="sxs-lookup"><span data-stu-id="2c3af-182">There are two types of time series anomalies that can be detected:</span></span> 

* <span data-ttu-id="2c3af-183">Un **pic** correspond à la poussée temporaire d’un comportement anormal dans le système.</span><span class="sxs-lookup"><span data-stu-id="2c3af-183">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span> 

* <span data-ttu-id="2c3af-184">Un **point de changement** indique le début d’un changement persistant dans le système.</span><span class="sxs-lookup"><span data-stu-id="2c3af-184">**Change points** indicate the beginning of persistent changes over time in the system.</span></span> 

<span data-ttu-id="2c3af-185">Dans ML.NET, les algorithmes de détection de pic ou de point de changement IID sont adaptés aux [jeux de données indépendants et identiquement distribués](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span><span class="sxs-lookup"><span data-stu-id="2c3af-185">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span> 

<span data-ttu-id="2c3af-186">Vous allez analyser les mêmes données de ventes d’un produit pour détecter les pics et les points de changement.</span><span class="sxs-lookup"><span data-stu-id="2c3af-186">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="2c3af-187">Le processus de génération et d’entraînement du modèle est le même pour la détection des pics et des points de changement ; la principale différence réside dans l’algorithme de détection utilisé.</span><span class="sxs-lookup"><span data-stu-id="2c3af-187">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="2c3af-188">Détection des pics</span><span class="sxs-lookup"><span data-stu-id="2c3af-188">Spike detection</span></span> 

<span data-ttu-id="2c3af-189">L’objectif est d’identifier les poussées d’activité, par définition soudaines et temporaires, qui diffèrent considérablement de la majorité des valeurs de données de la série chronologique.</span><span class="sxs-lookup"><span data-stu-id="2c3af-189">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="2c3af-190">Il est important de détecter au plus vite ces éléments, événements ou constats suspects pour pouvoir les minimiser.</span><span class="sxs-lookup"><span data-stu-id="2c3af-190">It's important to detect these suspicious rare items, events or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="2c3af-191">Vous pouvez utiliser l’approche suivante pour détecter de nombreuses anomalies, notamment des pannes, des cyberattaques et du contenu web viral.</span><span class="sxs-lookup"><span data-stu-id="2c3af-191">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="2c3af-192">L’image suivante illustre des pics dans le jeu de données d’une série chronologique :</span><span class="sxs-lookup"><span data-stu-id="2c3af-192">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a><span data-ttu-id="2c3af-194">Créer la méthode DetectSpike()</span><span class="sxs-lookup"><span data-stu-id="2c3af-194">Create the DetectSpike() method</span></span>

<span data-ttu-id="2c3af-195">Ajoutez l’appel suivant à la méthode `DetectSpike()` comme prochaine ligne de code dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-195">Add the following call to the `DetectSpike()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

<span data-ttu-id="2c3af-196">La méthode `DetectSpike()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c3af-196">The `DetectSpike()` method executes the following tasks:</span></span>

* <span data-ttu-id="2c3af-197">Effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="2c3af-197">Trains the model.</span></span>
* <span data-ttu-id="2c3af-198">Détecte les pics par rapport aux données de ventes historiques.</span><span class="sxs-lookup"><span data-stu-id="2c3af-198">Detects spikes based on on historical sales data.</span></span>
* <span data-ttu-id="2c3af-199">Affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="2c3af-199">Displays the results.</span></span>

<span data-ttu-id="2c3af-200">Créez la méthode `DetectSpike()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-200">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="2c3af-201">Utilisez [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) pour entraîner le modèle à la détection de pics.</span><span class="sxs-lookup"><span data-stu-id="2c3af-201">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="2c3af-202">Ajoutez-le à la méthode `DetectChangepoint()` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-202">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

<span data-ttu-id="2c3af-203">Ajustez le modèle aux données `productSales` en ajoutant la ligne de code suivante dans la méthode `DetectSpike()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-203">Fit the model to the `productSales` data by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

<span data-ttu-id="2c3af-204">La méthode [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="2c3af-204">The [Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="2c3af-205">Ajoutez la ligne de code suivante pour transformer les données `productSales` comme prochaine ligne de la méthode `DetectSpike()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-205">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

<span data-ttu-id="2c3af-206">Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour prédire plusieurs lignes d’entrée d’un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="2c3af-206">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="2c3af-207">Convertissez vos données `transformedData` en `IEnumerable` fortement typé pour faciliter l’affichage. Utilisez pour cela la méthode [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-207">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

<span data-ttu-id="2c3af-208">Créez une ligne d’en-tête d’affichage à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-208">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

<span data-ttu-id="2c3af-209">Les informations suivantes apparaissent dans vos résultats de détection des pics :</span><span class="sxs-lookup"><span data-stu-id="2c3af-209">You'll display the following information in your spike detection results:</span></span>

* <span data-ttu-id="2c3af-210">`Alert` indique une alerte de pic pour un point de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="2c3af-210">`Alert` indicates a spike alert for a given data point.</span></span>

* <span data-ttu-id="2c3af-211">`Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="2c3af-211">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>

* <span data-ttu-id="2c3af-212">`P-Value` où « P » correspond à la probabilité.</span><span class="sxs-lookup"><span data-stu-id="2c3af-212">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="2c3af-213">Il s’agit de la probabilité selon laquelle ce point de données constitue une anomalie.</span><span class="sxs-lookup"><span data-stu-id="2c3af-213">This indicates how likely this data point is an anomaly.</span></span> 

<span data-ttu-id="2c3af-214">Utilisez le code suivant pour effectuer une itération dans le `IEnumerable` `predictions` et afficher les résultats :</span><span class="sxs-lookup"><span data-stu-id="2c3af-214">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a><span data-ttu-id="2c3af-215">Résultats de la détection des pics</span><span class="sxs-lookup"><span data-stu-id="2c3af-215">Spike detection results</span></span>

<span data-ttu-id="2c3af-216">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="2c3af-216">Your results should be similar to the following.</span></span> <span data-ttu-id="2c3af-217">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="2c3af-217">During processing, messages are displayed.</span></span> <span data-ttu-id="2c3af-218">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="2c3af-218">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2c3af-219">Ils ont été supprimés des résultats ci-dessous par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="2c3af-219">These have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="2c3af-220">Détection des points de changement</span><span class="sxs-lookup"><span data-stu-id="2c3af-220">Change point detection</span></span>

<span data-ttu-id="2c3af-221">Les points de changement (`Change points`) indiquent des changements persistants dans la distribution de valeurs d’un flux d’événements d’une série chronologique, comme des changements de niveau ou des tendances.</span><span class="sxs-lookup"><span data-stu-id="2c3af-221">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="2c3af-222">Ces changements persistants durent beaucoup plus longtemps que les pics (`spikes`) et peuvent indiquer des événements catastrophiques.</span><span class="sxs-lookup"><span data-stu-id="2c3af-222">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="2c3af-223">`Change points` ne sont généralement pas visibles à l’œil nu, mais vous pouvez les détecter dans vos données à l’aide d’approches comme celles décrites dans la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="2c3af-223">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="2c3af-224">L’image suivante illustre la détection des points de changement :</span><span class="sxs-lookup"><span data-stu-id="2c3af-224">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="2c3af-226">Créer la méthode DetectChangepoint()</span><span class="sxs-lookup"><span data-stu-id="2c3af-226">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="2c3af-227">Ajoutez l’appel suivant à la méthode `DetectChangepoint()` comme prochaine ligne de code dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-227">Add the following call to the `DetectChangepoint()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

<span data-ttu-id="2c3af-228">La méthode `DetectChangepoint()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c3af-228">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="2c3af-229">Effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="2c3af-229">Trains the model.</span></span>
* <span data-ttu-id="2c3af-230">Détecte les points de changement par rapport aux données de ventes historiques.</span><span class="sxs-lookup"><span data-stu-id="2c3af-230">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="2c3af-231">Affiche les résultats.</span><span class="sxs-lookup"><span data-stu-id="2c3af-231">Displays the results.</span></span>

<span data-ttu-id="2c3af-232">Créez la méthode `DetectChangepoint()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-232">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

<span data-ttu-id="2c3af-233">Utilisez [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) pour entraîner le modèle à détecter les points de changement.</span><span class="sxs-lookup"><span data-stu-id="2c3af-233">The [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) is used to train the model for change point detection.</span></span> <span data-ttu-id="2c3af-234">Ajoutez-le à la méthode `DetectChangepoint()` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-234">Add it to the `DetectChangepoint()` method with the following code:</span></span>

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

<span data-ttu-id="2c3af-235">Comme vous l’avez fait précédemment, ajustez le modèle aux données `productSales` en ajoutant la ligne de code suivante dans la méthode `DetectChangePoint()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-235">As you did previously, fit the model to the `productSales` data by adding the following as the next line of code in the `DetectChangePoint()` method:</span></span>

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

<span data-ttu-id="2c3af-236">Utilisez la méthode `Transform()` pour transformer les données `Training` en ajoutant le code suivant à `DetectChangePoint()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-236">Use the `Transform()` method to transform the `Training` data by adding the following code to `DetectChangePoint()`:</span></span>

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

<span data-ttu-id="2c3af-237">Comme précédemment, convertissez vos données `transformedData` en `IEnumerable` fortement typé pour faciliter l’affichage. Utilisez pour cela la méthode `CreateEnumerable()` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-237">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

<span data-ttu-id="2c3af-238">Créez un en-tête d’affichage en ajoutant la ligne de code suivante comme prochaine ligne de la méthode `DetectChangePoint()` :</span><span class="sxs-lookup"><span data-stu-id="2c3af-238">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

<span data-ttu-id="2c3af-239">Les informations suivantes apparaissent dans vos résultats de détection des points de changement :</span><span class="sxs-lookup"><span data-stu-id="2c3af-239">You'll display the following information in your change point detection results:</span></span>

* <span data-ttu-id="2c3af-240">`Alert` indique une alerte de point de changement pour un point de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="2c3af-240">`Alert` indicates a change point alert for a given data point.</span></span>
* <span data-ttu-id="2c3af-241">`Score` est la valeur de `ProductSales` pour un point de données spécifique dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="2c3af-241">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
* <span data-ttu-id="2c3af-242">`P-Value` où « P » correspond à la probabilité.</span><span class="sxs-lookup"><span data-stu-id="2c3af-242">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="2c3af-243">Il s’agit de la probabilité selon laquelle ce point de données constitue une anomalie.</span><span class="sxs-lookup"><span data-stu-id="2c3af-243">This indicates how likely this data point is an anomaly.</span></span> 
* <span data-ttu-id="2c3af-244">`Martingale value` permet d’identifier le « degré d’étrangeté » d’un point de données en fonction de la séquence de valeurs P.</span><span class="sxs-lookup"><span data-stu-id="2c3af-244">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>  

<span data-ttu-id="2c3af-245">Effectuez une itération dans le `IEnumerable` `predictions` et affichez les résultats avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2c3af-245">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a><span data-ttu-id="2c3af-246">Résultats de la détection des points de changement</span><span class="sxs-lookup"><span data-stu-id="2c3af-246">Change point detection results</span></span>

<span data-ttu-id="2c3af-247">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="2c3af-247">Your results should be similar to the following.</span></span> <span data-ttu-id="2c3af-248">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="2c3af-248">During processing, messages are displayed.</span></span> <span data-ttu-id="2c3af-249">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="2c3af-249">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2c3af-250">Ils ont été supprimés des résultats ci-dessous par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="2c3af-250">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="2c3af-251">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="2c3af-251">Congratulations!</span></span> <span data-ttu-id="2c3af-252">Vous venez de générer des modèles de machine learning pour détecter des anomalies (pics et points de changement) dans des données de ventes.</span><span class="sxs-lookup"><span data-stu-id="2c3af-252">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="2c3af-253">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection).</span><span class="sxs-lookup"><span data-stu-id="2c3af-253">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="2c3af-254">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="2c3af-254">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="2c3af-255">Charger les données</span><span class="sxs-lookup"><span data-stu-id="2c3af-255">Load the data</span></span>
> * <span data-ttu-id="2c3af-256">Entraîner le modèle pour détecter des pics</span><span class="sxs-lookup"><span data-stu-id="2c3af-256">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="2c3af-257">Détecter des pics avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="2c3af-257">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="2c3af-258">Entraîner le modèle pour détecter des points de changement</span><span class="sxs-lookup"><span data-stu-id="2c3af-258">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="2c3af-259">Détecter des points de changement avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="2c3af-259">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="2c3af-260">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2c3af-260">Next steps</span></span>

<span data-ttu-id="2c3af-261">Consultez le dépôt GitHub d’exemples de machine learning pour explorer un exemple de détection d’anomalie dans le domaine de la consommation d’énergie.</span><span class="sxs-lookup"><span data-stu-id="2c3af-261">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2c3af-262">Référentiel GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="2c3af-262">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
