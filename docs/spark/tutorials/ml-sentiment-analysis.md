---
title: Analyse des sentiments avec .NET pour Apache Spark et didacticiel ML.NET
description: Dans ce didacticiel, vous allez apprendre à utiliser ML.NET avec .NET pour Apache Spark pour l’analyse des sentiments.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 1c2c966a4ff50a9d2f6951e20d909c5c20c75bfb
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688239"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="aa4f1-103">Didacticiel : analyse des sentiments avec .NET pour Apache Spark et ML.NET</span><span class="sxs-lookup"><span data-stu-id="aa4f1-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="aa4f1-104">Ce didacticiel vous apprend à effectuer une analyse des sentiments des analyses en ligne à l’aide de ML.NET et de .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="aa4f1-105">[Ml.net](http://dot.net/ml) est un framework de machine learning Open source gratuit et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="aa4f1-106">Vous pouvez utiliser ML.NET avec .NET pour Apache Spark pour mettre à l’échelle l’apprentissage et la prédiction des algorithmes de Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="aa4f1-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="aa4f1-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="aa4f1-108">Créez un modèle d’analyse des sentiments à l’aide du générateur de modèles ML.NET dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="aa4f1-109">Créez une application console .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="aa4f1-110">Écrivez et implémentez une fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="aa4f1-111">Exécutez une application console .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aa4f1-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="aa4f1-112">Prerequisites</span></span>

* <span data-ttu-id="aa4f1-113">Si vous n’avez pas encore développé de .NET pour Apache Spark application, commencez par le [didacticiel prise en main](get-started.md) pour vous familiariser avec les principes de base.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="aa4f1-114">Avant de poursuivre ce didacticiel, complétez toutes les conditions préalables pour le didacticiel Prise en main.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="aa4f1-115">Ce didacticiel utilise le générateur de modèles ML.NET (version préliminaire), une interface visuelle disponible dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="aa4f1-116">Si vous ne disposez pas de Visual Studio, vous pouvez [Télécharger gratuitement la version Community de Visual Studio](https://visualstudio.microsoft.com/downloads/) .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="aa4f1-117">[Télécharger et installer](https://marketplace.visualstudio.com/items?itemName=MLNET.07) Générateur de modèles ML.NET (version préliminaire).</span><span class="sxs-lookup"><span data-stu-id="aa4f1-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="aa4f1-118">Téléchargez les jeux de données [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) et [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp Review.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="aa4f1-119">Examiner les données</span><span class="sxs-lookup"><span data-stu-id="aa4f1-119">Review the data</span></span>

<span data-ttu-id="aa4f1-120">Le jeu de données Yelp revues contient des révisions Yelp en ligne sur divers services.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="aa4f1-121">Ouvrez [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) et notez la structure des données.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="aa4f1-122">La première colonne contient le texte de révision, tandis que la deuxième colonne contient des scores de sentiment.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="aa4f1-123">Si le score de sentiment est 1, la révision est positive et si le score de sentiment est 0, la révision est négative.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="aa4f1-124">Le tableau suivant contient des exemples de données :</span><span class="sxs-lookup"><span data-stu-id="aa4f1-124">The following table contains sample data:</span></span>

|<span data-ttu-id="aa4f1-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="aa4f1-125">ReviewText</span></span>|<span data-ttu-id="aa4f1-126">Sentiments</span><span class="sxs-lookup"><span data-stu-id="aa4f1-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="aa4f1-127">... J’ai aimé cet endroit.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="aa4f1-128">1</span><span class="sxs-lookup"><span data-stu-id="aa4f1-128">1</span></span>|
|<span data-ttu-id="aa4f1-129">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-129">Crust is not good.</span></span>|    <span data-ttu-id="aa4f1-130">0</span><span class="sxs-lookup"><span data-stu-id="aa4f1-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="aa4f1-131">Générez votre modèle de Machine Learning</span><span class="sxs-lookup"><span data-stu-id="aa4f1-131">Build your machine learning model</span></span>

1. <span data-ttu-id="aa4f1-132">Ouvrez Visual Studio et créez une nouvelle application console C# (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="aa4f1-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="aa4f1-133">Nommez le projet *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="aa4f1-134">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet *MLSparkModel* .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="aa4f1-135">Sélectionnez ensuite **ajouter > machine learning**.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="aa4f1-136">Dans le générateur de modèles ML.NET, sélectionnez la vignette **analyse des sentiments** scénario.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="aa4f1-137">Dans la page **Ajouter des données** , téléchargez le jeu de données de *yelptrain.csv* .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="aa4f1-138">Choisissez *sentiments* dans la liste déroulante **colonnes à prédire** .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="aa4f1-139">Sur la page **train** , définissez l’heure sur l’apprentissage sur *60 secondes* et sélectionnez **Démarrer l’apprentissage**.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="aa4f1-140">Notez l’état de votre formation en **cours**.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="aa4f1-141">Une fois que le générateur de modèles a terminé la formation, **évaluez** les résultats de la formation.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="aa4f1-142">Vous pouvez taper des expressions dans la zone de texte ci-dessous **essayer votre modèle** et sélectionner **prédire** pour voir la sortie.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="aa4f1-143">Sélectionnez **code** , puis sélectionnez **Ajouter des projets** pour ajouter le modèle ml à la solution.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="aa4f1-144">Notez que deux projets sont ajoutés à vos solutions : **MLSparkModelML. ConsoleApp** et **MLSparkModelML. Model**.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="aa4f1-145">Double-cliquez sur votre projet C# *MLSpark* et notez que la référence de projet suivante a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="aa4f1-146">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="aa4f1-146">Create a console app</span></span>

<span data-ttu-id="aa4f1-147">Le générateur de modèles crée une application console pour vous.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="aa4f1-148">Cliquez avec le bouton droit sur **MLSparkModelML. console** dans Explorateur de solutions, puis sélectionnez **gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="aa4f1-149">Recherchez **Microsoft. Spark** et installez le package.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="aa4f1-150">**Microsoft.ml** est automatiquement installé pour vous par le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="aa4f1-151">Créer un SparkSession</span><span class="sxs-lookup"><span data-stu-id="aa4f1-151">Create a SparkSession</span></span>

1. <span data-ttu-id="aa4f1-152">Ouvrez le fichier *Program.cs* pour **MLSparkModelML. ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="aa4f1-153">Ce fichier a été généré automatiquement par le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="aa4f1-154">Supprimez les `using` instructions, le contenu de la méthode main () et la `CreateSingleDataSample` région.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="aa4f1-155">Ajoutez les instructions supplémentaires suivantes `using` en haut de *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="aa4f1-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="aa4f1-156">Remplacez `DATA_FILEPATH` par le chemin d’accès de votre *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="aa4f1-157">Ajoutez le code suivant à votre `Main` méthode pour créer un nouveau `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="aa4f1-158">La session Spark est le point d’entrée de la programmation Spark avec l’API DataSet et tableau.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="aa4f1-159">L’appel de l’objet *Spark* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et tableau dans votre programme.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="aa4f1-160">Créer un tableau et l’imprimer sur la console</span><span class="sxs-lookup"><span data-stu-id="aa4f1-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="aa4f1-161">Lisez les données de l'yelptest.csvexaminez le fichier *yelptest.csv* en tant que `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="aa4f1-162">Inclut `header` les `inferSchema` options et.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="aa4f1-163">L' `header` option lit la première ligne de *yelptest.csv* en tant que noms de colonne au lieu de données.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="aa4f1-164">L' `inferSchema` option déduit les types de colonne en fonction des données.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="aa4f1-165">Inscrire une fonction définie par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="aa4f1-165">Register a user-defined function</span></span>

<span data-ttu-id="aa4f1-166">Vous pouvez utiliser des *fonctions définies par l’utilisateur*(UDF) dans des applications Spark pour effectuer des calculs et des analyses sur vos données.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="aa4f1-167">Dans ce didacticiel, vous allez utiliser ML.NET avec une fonction définie par l’usage (UDF) pour évaluer chaque Yelp.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="aa4f1-168">Ajoutez le code suivant à votre `Main` méthode pour inscrire une fonction UDF appelée `MLudf` .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="aa4f1-169">Cette fonction UDF prend une chaîne de révision Yelp comme entrée et génère la valeur true ou false pour les sentiments positifs ou négatifs, respectivement.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="aa4f1-170">Elle utilise la méthode *Predict ()* que vous définissez dans une étape ultérieure.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="aa4f1-171">Utiliser Spark SQL pour appeler la fonction définie par l’usage</span><span class="sxs-lookup"><span data-stu-id="aa4f1-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="aa4f1-172">Maintenant que vous avez lu vos données et incorporé ML, utilisez Spark SQL pour appeler l’UDF qui exécutera l’analyse des sentiments sur chaque ligne de votre tableau.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="aa4f1-173">Ajoutez le code suivant à votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="aa4f1-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="aa4f1-174">Créer une méthode Predict ()</span><span class="sxs-lookup"><span data-stu-id="aa4f1-174">Create predict() method</span></span>

<span data-ttu-id="aa4f1-175">Ajoutez le code suivant avant votre `Main()` méthode.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="aa4f1-176">Ce code est similaire à ce qui est produit par le générateur de modèles dans *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="aa4f1-177">Le déplacement de cette méthode sur votre console charge le chargement du modèle chaque fois que vous exécutez votre application.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="aa4f1-178">Ajouter le modèle à votre application console</span><span class="sxs-lookup"><span data-stu-id="aa4f1-178">Add the model to your console app</span></span>

<span data-ttu-id="aa4f1-179">Dans Explorateur de solutions, copiez le fichier *MLModel.zip* à partir du projet **MLSparkModelML. Model** et collez-le dans le projet **MLSparkModelML. ConsoleApp** .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="aa4f1-180">Une référence est automatiquement ajoutée dans *MLSparkModelML. ConsoleApp. csproj*.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="aa4f1-181">Exécuter votre code</span><span class="sxs-lookup"><span data-stu-id="aa4f1-181">Run your code</span></span>

<span data-ttu-id="aa4f1-182">Utilisez `spark-submit` pour exécuter votre code.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="aa4f1-183">Accédez au dossier racine de votre application console à l’aide de l’invite de commandes et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="aa4f1-184">Tout d’abord, nettoyez et publiez votre application.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="aa4f1-185">Accédez ensuite au dossier Publish de l’application console et exécutez la `spark-submit` commande suivante.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="aa4f1-186">N’oubliez pas de mettre à jour la commande avec le chemin d’accès réel de votre fichier jar Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2-4_2.11-1.0.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="aa4f1-187">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="aa4f1-187">Get the code</span></span>

<span data-ttu-id="aa4f1-188">Ce didacticiel est similaire au code de l’exemple de [analyse des sentiments avec des données Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) .</span><span class="sxs-lookup"><span data-stu-id="aa4f1-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="aa4f1-189">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="aa4f1-189">Next steps</span></span>

<span data-ttu-id="aa4f1-190">Passez à l’article suivant pour découvrir comment procéder à la diffusion en continu structurée avec .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="aa4f1-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="aa4f1-191">Didacticiel : diffusion en continu structurée avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="aa4f1-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
