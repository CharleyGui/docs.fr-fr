---
title: Analyse de sentiment avec .NET pour Apache Spark et ML.NET tutoriel
description: Dans ce tutoriel, vous apprenez à utiliser ML.NET avec .NET pour Apache Spark pour l’analyse du sentiment.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391257"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="0cdaa-103">Tutorial: Analyse de sentiment avec .NET pour Apache Spark et ML.NET</span><span class="sxs-lookup"><span data-stu-id="0cdaa-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="0cdaa-104">Ce tutoriel vous apprend à faire l’analyse du sentiment des commentaires en ligne en utilisant ML.NET et .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="0cdaa-105">[ML.NET](http://dot.net/ml) est un cadre d’apprentissage automatique libre, multiplateforme et open source.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="0cdaa-106">Vous pouvez utiliser ML.NET avec .NET pour Apache Spark pour mettre à l’échelle la formation et la prédiction des algorithmes d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="0cdaa-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="0cdaa-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="0cdaa-108">Créez un modèle d’analyse de sentiment à l’aide de ML.NET Model Builder dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="0cdaa-109">Créez une application de console .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="0cdaa-110">Rédiger et implémenter une fonction définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="0cdaa-111">Exécutez un .NET pour Apache Spark console app.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0cdaa-112">Prérequis</span><span class="sxs-lookup"><span data-stu-id="0cdaa-112">Prerequisites</span></span>

* <span data-ttu-id="0cdaa-113">Si vous n’avez pas développé un .NET pour Apache Spark application avant, commencez par le [tutoriel Getting Started](get-started.md) pour se familiariser avec les bases.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="0cdaa-114">Complétez toutes les conditions préalables pour le tutoriel Getting Started avant de continuer avec ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="0cdaa-115">Ce tutoriel utilise le ML.NET Model Builder (preview), une interface visuelle disponible dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="0cdaa-116">Si vous n’avez pas déjà Visual Studio, vous pouvez [télécharger la version communautaire de Visual Studio](https://visualstudio.microsoft.com/downloads/) gratuitement.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="0cdaa-117">[Télécharger et installer](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (avant-première).</span><span class="sxs-lookup"><span data-stu-id="0cdaa-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="0cdaa-118">Téléchargez les jeux de données [d’examen yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) et [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="0cdaa-119">Examiner les données</span><span class="sxs-lookup"><span data-stu-id="0cdaa-119">Review the data</span></span>

<span data-ttu-id="0cdaa-120">Le jeu de données Yelp avise les commentaires en ligne sur divers services.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="0cdaa-121">Ouvrez [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) et remarquez la structure des données.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="0cdaa-122">La première colonne contient du texte d’examen, et la deuxième colonne contient des scores de sentiment.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="0cdaa-123">Si le score de sentiment est 1, l’examen est positif, et si le score de sentiment est 0, l’examen est négatif.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="0cdaa-124">Le tableau suivant contient des données d’exemple :</span><span class="sxs-lookup"><span data-stu-id="0cdaa-124">The following table contains sample data:</span></span>

|<span data-ttu-id="0cdaa-125">ReviewText (en)</span><span class="sxs-lookup"><span data-stu-id="0cdaa-125">ReviewText</span></span>|<span data-ttu-id="0cdaa-126">Sentiments</span><span class="sxs-lookup"><span data-stu-id="0cdaa-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="0cdaa-127">Wow... J’ai adoré cet endroit.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="0cdaa-128">1</span><span class="sxs-lookup"><span data-stu-id="0cdaa-128">1</span></span>|
|<span data-ttu-id="0cdaa-129">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-129">Crust is not good.</span></span>|    <span data-ttu-id="0cdaa-130">0</span><span class="sxs-lookup"><span data-stu-id="0cdaa-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="0cdaa-131">Construisez votre modèle d’apprentissage automatique</span><span class="sxs-lookup"><span data-stu-id="0cdaa-131">Build your machine learning model</span></span>

1. <span data-ttu-id="0cdaa-132">Ouvrez Visual Studio et créez une nouvelle application console CMD (.NET Core).</span><span class="sxs-lookup"><span data-stu-id="0cdaa-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="0cdaa-133">Nommez le projet *MLSparkModel*.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="0cdaa-134">Dans **Solution Explorer**, cliquez à droite sur le projet *MLSparkModel.*</span><span class="sxs-lookup"><span data-stu-id="0cdaa-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="0cdaa-135">Ensuite, sélectionnez **Ajouter > l’apprentissage automatique**.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="0cdaa-136">Du ML.NET Model Builder, sélectionnez la tuile de scénario **d’analyse de sentiment.**</span><span class="sxs-lookup"><span data-stu-id="0cdaa-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="0cdaa-137">Sur la page **de données Add,** téléchargez l’ensemble de données *yelptrain.csv.*</span><span class="sxs-lookup"><span data-stu-id="0cdaa-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="0cdaa-138">Choisissez *Sentiment* parmi les **colonnes pour prédire** la baisse.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="0cdaa-139">Sur la page **Train,** définissez le temps de vous entraîner jusqu’à *60 secondes* et sélectionnez **l’entraînement Démarrer.**</span><span class="sxs-lookup"><span data-stu-id="0cdaa-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="0cdaa-140">Remarquez l’état de votre formation dans le cadre **de Progress**.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="0cdaa-141">Une fois que Le constructeur modèle a terminé la formation, **évaluez** les résultats de la formation.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="0cdaa-142">Vous pouvez taper des phrases dans la boîte de texte ci-dessous **Essayez votre modèle** et **sélectionnez Prédire** pour voir la sortie.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="0cdaa-143">Sélectionnez **code,** puis sélectionnez **Ajouter des projets** pour ajouter le modèle ML à la solution.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="0cdaa-144">Notez que deux projets sont ajoutés à vos solutions : **MLSparkModelML.ConsoleApp** et **MLSparkModelML.Model**.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="0cdaa-145">Double clic sur votre projet *MLSpark* C et remarquez que la référence de projet suivante a été ajoutée.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="0cdaa-146">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="0cdaa-146">Create a console app</span></span>

<span data-ttu-id="0cdaa-147">Model Builder crée une application console pour vous.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="0cdaa-148">Cliquez à droite sur **MLSparkModelML.Console** dans Solution Explorer, et **sélectionnez Manage NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="0cdaa-149">Recherchez **Microsoft.Spark** et installez le paquet.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="0cdaa-150">**Microsoft.ML** est automatiquement installé pour vous par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="0cdaa-151">Créer une SparkSession</span><span class="sxs-lookup"><span data-stu-id="0cdaa-151">Create a SparkSession</span></span>

1. <span data-ttu-id="0cdaa-152">Ouvrez le fichier *Program.cs* pour **MLSparkModelML.ConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="0cdaa-153">Ce fichier a été autogénéré par Model Builder.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="0cdaa-154">Supprimer `using` les relevés, le contenu de la `CreateSingleDataSample` méthode Main() et la région.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="0cdaa-155">Ajoutez les `using` instructions supplémentaires suivantes au sommet de la *Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="0cdaa-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="0cdaa-156">Changez `DATA_FILEPATH` le chemin de votre *yelptest.csv*.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="0cdaa-157">Ajoutez le code `Main` suivant à votre `SparkSession`méthode pour créer un nouveau .</span><span class="sxs-lookup"><span data-stu-id="0cdaa-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="0cdaa-158">La spark Session est le point d’entrée de la programmation Spark avec l’API Dataset et DataFrame.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="0cdaa-159">L’appel de l’objet *d’étincelle* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et DataFrame tout au long de votre programme.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="0cdaa-160">Créez un DataFrame et imprimez pour consoler</span><span class="sxs-lookup"><span data-stu-id="0cdaa-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="0cdaa-161">Lire dans les données d’examen Yelp du fichier *yelptest.csv* comme un `DataFrame`.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="0cdaa-162">Inclure `header` `inferSchema` et options.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="0cdaa-163">L’option `header` lit la première ligne de *yelptest.csv* comme noms de colonne au lieu de données.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="0cdaa-164">L’option `inferSchema` infère les types de colonnes basés sur les données.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="0cdaa-165">Enregistrer une fonction définie par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="0cdaa-165">Register a user-defined function</span></span>

<span data-ttu-id="0cdaa-166">Vous pouvez utiliser des FUD, *des fonctions définies par l’utilisateur,* des applications Spark pour effectuer des calculs et des analyses sur vos données.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="0cdaa-167">Dans ce tutoriel, vous utilisez ML.NET avec un UDF pour évaluer chaque examen Yelp.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="0cdaa-168">Ajoutez le code `Main` suivant à votre méthode `MLudf`pour enregistrer un UDF appelé .</span><span class="sxs-lookup"><span data-stu-id="0cdaa-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="0cdaa-169">Cet UDF prend une chaîne d’examen Yelp comme entrée, et les sorties vraies ou fausses pour les sentiments positifs ou négatifs, respectivement.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="0cdaa-170">Il utilise la méthode *de prédiction ()* que vous définissez dans une étape ultérieure.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="0cdaa-171">Utilisez Spark SQL pour appeler l’UDF</span><span class="sxs-lookup"><span data-stu-id="0cdaa-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="0cdaa-172">Maintenant que vous avez lu dans vos données et incorporé ML, utilisez Spark SQL pour appeler l’UDF qui exécutera l’analyse de sentiment sur chaque rangée de votre DataFrame.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="0cdaa-173">Ajoutez le code suivant à votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="0cdaa-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="0cdaa-174">Créer une méthode de prévision()</span><span class="sxs-lookup"><span data-stu-id="0cdaa-174">Create predict() method</span></span>

<span data-ttu-id="0cdaa-175">Ajoutez le code `Main()` suivant avant votre méthode.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="0cdaa-176">Ce code est similaire à ce qui est produit par Model Builder dans *ConsumeModel.cs*.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="0cdaa-177">Le déplacement de cette méthode vers votre console charge le chargement du modèle chaque fois que vous exécutez votre application.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="0cdaa-178">Ajoutez le modèle à votre application console</span><span class="sxs-lookup"><span data-stu-id="0cdaa-178">Add the model to your console app</span></span>

<span data-ttu-id="0cdaa-179">Dans Solution Explorer, copiez le fichier *MLModel.zip* du projet **MLSparkModelML.Model** et collez-le dans le projet **MLSparkModelML.ConsoleApp.**</span><span class="sxs-lookup"><span data-stu-id="0cdaa-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="0cdaa-180">Une référence est automatiquement ajoutée dans *MLSparkModelML.ConsoleApp.csproj*.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="0cdaa-181">Exécuter votre code</span><span class="sxs-lookup"><span data-stu-id="0cdaa-181">Run your code</span></span>

<span data-ttu-id="0cdaa-182">Utilisez `spark-submit` pour faire fonctionner votre code.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="0cdaa-183">Naviguez vers le dossier racine de votre application de console à l’aide de l’invite de commande et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="0cdaa-184">Tout d’abord, nettoyez et publiez votre application.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="0cdaa-185">Ensuite, naviguez vers le dossier de publication `spark-submit` de l’application de la console et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="0cdaa-186">N’oubliez pas de mettre à jour la commande avec le chemin réel de votre fichier de pot Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="0cdaa-187">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="0cdaa-187">Get the code</span></span>

<span data-ttu-id="0cdaa-188">Ce tutoriel est similaire au code de [l’analyse du sentiment avec l’exemple Big Data.](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)</span><span class="sxs-lookup"><span data-stu-id="0cdaa-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0cdaa-189">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0cdaa-189">Next steps</span></span>

<span data-ttu-id="0cdaa-190">Avancez à l’article suivant pour apprendre à faire le streaming structuré avec .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="0cdaa-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0cdaa-191">Tutorial: Streaming structuré avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="0cdaa-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
