---
title: Didacticiel sur le traitement par lots avec .NET pour Apache Spark
description: Découvrez comment effectuer un traitement par lots à l’aide de .NET pour Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 06/25/2020
ms.topic: tutorial
ms.openlocfilehash: dbc3ab5cc4bd7f438e9f3f8e5d36c764d785ce4b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618283"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="fdf40-103">Didacticiel : effectuer un traitement par lots avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="fdf40-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="fdf40-104">Dans ce didacticiel, vous allez apprendre à effectuer un traitement par lots à l’aide de .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="fdf40-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="fdf40-105">Le traitement par lots est la transformation des données au repos, ce qui signifie que les données sources ont déjà été chargées dans le stockage des données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="fdf40-106">Le traitement par lots est généralement effectué sur des jeux de données volumineux et plats qui doivent être préparés pour une analyse plus poussée.</span><span class="sxs-lookup"><span data-stu-id="fdf40-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="fdf40-107">Le traitement des journaux et l’entreposage des données sont des scénarios courants de traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="fdf40-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="fdf40-108">Dans ce scénario, vous analysez des informations sur les projets GitHub, telles que le nombre de fois où différents projets ont été dupliqués ou la manière dont les projets récents ont été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="fdf40-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="fdf40-109">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="fdf40-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="fdf40-110">Créer et exécuter un .NET pour Apache Spark application</span><span class="sxs-lookup"><span data-stu-id="fdf40-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="fdf40-111">Lire des données dans un tableau et les préparer pour l’analyse</span><span class="sxs-lookup"><span data-stu-id="fdf40-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="fdf40-112">Traitement des données à l’aide de Spark SQL</span><span class="sxs-lookup"><span data-stu-id="fdf40-112">Process the data using Spark SQL</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="fdf40-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="fdf40-113">Prerequisites</span></span>

<span data-ttu-id="fdf40-114">Si c’est la première fois que vous utilisez .NET pour Apache Spark, consultez le didacticiel [prise en main de .net pour Apache Spark](get-started.md) pour apprendre à préparer votre environnement et à exécuter votre première application .net pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="fdf40-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="fdf40-115">Télécharger les exemples de données</span><span class="sxs-lookup"><span data-stu-id="fdf40-115">Download the sample data</span></span>

<span data-ttu-id="fdf40-116">[GHTorrent](http://ghtorrent.org/) surveille tous les événements GitHub publics, tels que les informations sur les projets, les validations et les observateurs, et stocke les événements et leur structure dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="fdf40-117">Les données collectées sur différentes périodes sont disponibles sous forme d’archives téléchargeables.</span><span class="sxs-lookup"><span data-stu-id="fdf40-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="fdf40-118">Étant donné que les fichiers de vidage sont très volumineux, ce guide utilise une [version tronquée du fichier dump](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) qui peut être téléchargée à partir de github.</span><span class="sxs-lookup"><span data-stu-id="fdf40-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="fdf40-119">Le jeu de données GHTorrent est distribué dans le cadre d’un système de gestion de licences double (Creative-licence[+](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="fdf40-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="fdf40-120">Pour les utilisations non commerciales (y compris, mais sans s’y limiter, les utilisations éducatives, de recherche ou personnelles), le jeu de données est distribué dans le cadre de la [licence CC-by-sa](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="fdf40-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="fdf40-121">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="fdf40-121">Create a console application</span></span>

1. <span data-ttu-id="fdf40-122">À l’invite de commandes, exécutez les commandes suivantes pour créer une nouvelle application console :</span><span class="sxs-lookup"><span data-stu-id="fdf40-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="fdf40-123">La `dotnet` commande crée une `new` application de type `console` pour vous.</span><span class="sxs-lookup"><span data-stu-id="fdf40-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="fdf40-124">Le `-o` paramètre crée un répertoire nommé *mySparkBatchApp* dans lequel votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="fdf40-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="fdf40-125">La `cd mySparkBatchApp` commande remplace le répertoire par le répertoire d’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="fdf40-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="fdf40-126">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="fdf40-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="fdf40-127">Dans votre console, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="fdf40-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="fdf40-128">Créer un SparkSession</span><span class="sxs-lookup"><span data-stu-id="fdf40-128">Create a SparkSession</span></span>

1. <span data-ttu-id="fdf40-129">Ajoutez les instructions supplémentaires suivantes `using` au début du fichier *Program.cs* dans *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="fdf40-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="fdf40-130">Ajoutez le code suivant à votre espace de noms de projet.</span><span class="sxs-lookup"><span data-stu-id="fdf40-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="fdf40-131">*s_referenceData* est utilisé ultérieurement dans le programme pour filtrer en fonction de la date.</span><span class="sxs-lookup"><span data-stu-id="fdf40-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="fdf40-132">Ajoutez le code suivant à l’intérieur de votre méthode main pour établir un nouveau SparkSession.</span><span class="sxs-lookup"><span data-stu-id="fdf40-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="fdf40-133">Le SparkSession est le point d’entrée de la programmation Spark avec l’API DataSet et tableau.</span><span class="sxs-lookup"><span data-stu-id="fdf40-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="fdf40-134">En appelant l' `spark` objet, vous pouvez accéder aux fonctionnalités Spark et tableau dans votre programme.</span><span class="sxs-lookup"><span data-stu-id="fdf40-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="fdf40-135">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="fdf40-135">Prepare the data</span></span>

1. <span data-ttu-id="fdf40-136">Lit le fichier d’entrée dans un `DataFrame` , qui est une collection de données distribuée organisée en colonnes nommées.</span><span class="sxs-lookup"><span data-stu-id="fdf40-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="fdf40-137">Vous pouvez définir les colonnes de vos données par le biais de <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> .</span><span class="sxs-lookup"><span data-stu-id="fdf40-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="fdf40-138">Utilisez la <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> méthode pour afficher les données dans votre tableau.</span><span class="sxs-lookup"><span data-stu-id="fdf40-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="fdf40-139">Veillez à mettre à jour le chemin d’accès au fichier CSV vers l’emplacement des données GitHub que vous avez téléchargées.</span><span class="sxs-lookup"><span data-stu-id="fdf40-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. <span data-ttu-id="fdf40-140">Utilisez la <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> méthode pour supprimer des lignes avec des valeurs na (null) et la <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> méthode pour supprimer certaines colonnes de vos données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="fdf40-141">Cela permet d’éviter des erreurs si vous essayez d’analyser des données null ou des colonnes qui ne sont pas pertinentes pour votre analyse finale.</span><span class="sxs-lookup"><span data-stu-id="fdf40-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="fdf40-142">Analyser les données</span><span class="sxs-lookup"><span data-stu-id="fdf40-142">Analyze the data</span></span>

<span data-ttu-id="fdf40-143">Spark SQL vous permet d’effectuer des appels SQL sur vos données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="fdf40-144">Il est courant de combiner des fonctions définies par l’utilisateur et Spark SQL pour appliquer une fonction définie par l’utilisateur à toutes les lignes de votre tableau.</span><span class="sxs-lookup"><span data-stu-id="fdf40-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="fdf40-145">Vous pouvez appeler spécifiquement `spark.Sql` pour imiter les appels SQL standard détectés dans d’autres types d’applications.</span><span class="sxs-lookup"><span data-stu-id="fdf40-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="fdf40-146">Vous pouvez également appeler des méthodes telles que <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> et <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> pour combiner, filtrer et effectuer des calculs spécifiquement sur vos données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="fdf40-147">L’objectif de cette application est d’obtenir des Insights sur les données des projets GitHub.</span><span class="sxs-lookup"><span data-stu-id="fdf40-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="fdf40-148">Ajoutez les extraits de code suivants à votre programme pour analyser les données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="fdf40-149">Ajouter le bloc de code suivant recherche le nombre de fois où chaque langue a été dupliquée.</span><span class="sxs-lookup"><span data-stu-id="fdf40-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="fdf40-150">Tout d’abord, les données sont regroupées par langue.</span><span class="sxs-lookup"><span data-stu-id="fdf40-150">First, the data is grouped by language.</span></span> <span data-ttu-id="fdf40-151">Ensuite, le nombre moyen de fourches de chaque langue est pris.</span><span class="sxs-lookup"><span data-stu-id="fdf40-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="fdf40-152">Ajoutez le bloc de code suivant pour trier le nombre moyen de fourches dans l’ordre décroissant afin de déterminer les langues les plus dupliquées.</span><span class="sxs-lookup"><span data-stu-id="fdf40-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="fdf40-153">Autrement dit, le plus grand nombre de fourches s’affiche en premier.</span><span class="sxs-lookup"><span data-stu-id="fdf40-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="fdf40-154">Le bloc de code suivant vous montre comment les projets récents ont été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="fdf40-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="fdf40-155">Vous inscrivez une nouvelle fonction définie par l’utilisateur appelée *MyUDF* et la Comparez avec une date, *s_referenceDate*, qui a été déclarée au début du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="fdf40-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="fdf40-156">La date de chaque projet est comparée à la date de référence.</span><span class="sxs-lookup"><span data-stu-id="fdf40-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="fdf40-157">Spark SQL est ensuite utilisé pour appeler l’UDF sur chaque ligne des données pour analyser chaque projet dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="fdf40-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. <span data-ttu-id="fdf40-158">Appelez `spark.Stop()` pour terminer le SparkSession.</span><span class="sxs-lookup"><span data-stu-id="fdf40-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="fdf40-159">Utiliser Spark-submit pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="fdf40-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="fdf40-160">Utilisez la commande suivante pour générer votre application .NET :</span><span class="sxs-lookup"><span data-stu-id="fdf40-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="fdf40-161">Exécutez votre application avec `spark-submit` .</span><span class="sxs-lookup"><span data-stu-id="fdf40-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="fdf40-162">Veillez à mettre à jour la commande suivante avec les chemins d’accès réels à votre fichier jar Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="fdf40-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="fdf40-163">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="fdf40-163">Get the code</span></span>

<span data-ttu-id="fdf40-164">Vous pouvez voir la [solution complète](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="fdf40-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fdf40-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fdf40-165">Next steps</span></span>

<span data-ttu-id="fdf40-166">Passez à l’article suivant pour apprendre à traiter les données de streaming avec .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="fdf40-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="fdf40-167">Didacticiel : diffusion en continu structurée avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="fdf40-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
