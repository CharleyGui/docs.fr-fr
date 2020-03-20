---
title: Traitement par lots avec .NET pour Apache Spark tutoriel
description: Apprenez à faire le traitement par lots en utilisant .NET pour Apache Spark.
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187554"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="3a681-103">Tutorial: Faire le traitement par lots avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3a681-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="3a681-104">Dans ce tutoriel, vous apprenez à faire le traitement par lots en utilisant .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3a681-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="3a681-105">Le traitement par lots est la transformation des données au repos, ce qui signifie que les données sources ont déjà été chargées dans le stockage de données.</span><span class="sxs-lookup"><span data-stu-id="3a681-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="3a681-106">Le traitement par lots est généralement effectué sur de grands ensembles de données plats qui doivent être préparés pour une analyse plus approfondie.</span><span class="sxs-lookup"><span data-stu-id="3a681-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="3a681-107">Le traitement des journaux et l’entreposage des données sont des scénarios de traitement de lots courants.</span><span class="sxs-lookup"><span data-stu-id="3a681-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="3a681-108">Dans ce scénario, vous analysez des informations sur les projets GitHub, telles que le nombre de temps que différents projets ont été mis en fourche ou la rapidité avec laquelle les projets ont été mis à jour récemment.</span><span class="sxs-lookup"><span data-stu-id="3a681-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="3a681-109">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="3a681-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="3a681-110">Créez et exécutez une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3a681-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="3a681-111">Lire les données dans un DataFrame et les préparer à l’analyse</span><span class="sxs-lookup"><span data-stu-id="3a681-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="3a681-112">Traiter les données à l’aide de Spark SQL</span><span class="sxs-lookup"><span data-stu-id="3a681-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3a681-113">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="3a681-113">Prerequisites</span></span>

<span data-ttu-id="3a681-114">Si c’est votre première fois en utilisant .NET pour Apache Spark, consultez le [Get a commencé avec .NET pour Apache Spark](../tutorials/get-started.md) tutoriel pour apprendre à préparer votre environnement et exécuter votre premier .NET pour Apache Spark application.</span><span class="sxs-lookup"><span data-stu-id="3a681-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="3a681-115">Télécharger les exemples de données</span><span class="sxs-lookup"><span data-stu-id="3a681-115">Download the sample data</span></span>

<span data-ttu-id="3a681-116">[GHTorrent](http://ghtorrent.org/) surveille tous les événements publics GitHub, tels que des informations sur les projets, les commits et les observateurs, et stocke les événements et leur structure dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="3a681-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="3a681-117">Les données recueillies sur différentes périodes de temps sont disponibles sous forme d’archives téléchargeables.</span><span class="sxs-lookup"><span data-stu-id="3a681-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="3a681-118">Parce que les fichiers de décharge sont très volumineux, ce guide utilise une [version tronquée du fichier de décharge](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) qui peut être téléchargé à partir de GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a681-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="3a681-119">Le jeu de données GHTorrent est distribué dans le cadre d’un système de double licence[(Creative Commons (](https://wiki.creativecommons.org/wiki/CCPlus)).</span><span class="sxs-lookup"><span data-stu-id="3a681-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="3a681-120">Pour les utilisations non commerciales (y compris, mais sans s’y limiter, l’éducation, la recherche ou les usages personnels), l’ensemble de données est distribué sous la [licence CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).</span><span class="sxs-lookup"><span data-stu-id="3a681-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="3a681-121">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="3a681-121">Create a console application</span></span>

1. <span data-ttu-id="3a681-122">Dans votre application rapide, exécutez les commandes suivantes pour créer une nouvelle application de console :</span><span class="sxs-lookup"><span data-stu-id="3a681-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="3a681-123">La `dotnet` commande `new` crée une `console` application de type pour vous.</span><span class="sxs-lookup"><span data-stu-id="3a681-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="3a681-124">Le `-o` paramètre crée un répertoire nommé *mySparkBatchApp* où votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="3a681-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="3a681-125">La `cd mySparkBatchApp` commande modifie l’annuaire de l’annuaire de l’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="3a681-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="3a681-126">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="3a681-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="3a681-127">Dans votre console, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="3a681-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="3a681-128">Créer une SparkSession</span><span class="sxs-lookup"><span data-stu-id="3a681-128">Create a SparkSession</span></span>

1. <span data-ttu-id="3a681-129">Ajoutez les `using` instructions supplémentaires suivantes au haut du fichier *Program.cs* dans *mySparkBatchApp*.</span><span class="sxs-lookup"><span data-stu-id="3a681-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="3a681-130">Ajoutez le code suivant à votre espace nom de projet.</span><span class="sxs-lookup"><span data-stu-id="3a681-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="3a681-131">*s_referenceData* est utilisé plus tard dans le programme pour filtrer en fonction de la date.</span><span class="sxs-lookup"><span data-stu-id="3a681-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="3a681-132">Ajoutez le code suivant à l’intérieur de votre méthode Principale pour établir une nouvelle SparkSession.</span><span class="sxs-lookup"><span data-stu-id="3a681-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="3a681-133">Le SparkSession est le point d’entrée de la programmation Spark avec l’API Dataset et DataFrame.</span><span class="sxs-lookup"><span data-stu-id="3a681-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="3a681-134">En appelant `spark` l’objet, vous pouvez accéder aux fonctionnalités Spark et DataFrame tout au long de votre programme.</span><span class="sxs-lookup"><span data-stu-id="3a681-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="3a681-135">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="3a681-135">Prepare the data</span></span>

1. <span data-ttu-id="3a681-136">Lisez le fichier `DataFrame`d’entrée dans un , qui est une collection distribuée de données organisées en colonnes nommées.</span><span class="sxs-lookup"><span data-stu-id="3a681-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="3a681-137">Vous pouvez définir les colonnes pour vos données à travers <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span><span class="sxs-lookup"><span data-stu-id="3a681-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="3a681-138">Utilisez <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> la méthode pour afficher les données dans votre DataFrame.</span><span class="sxs-lookup"><span data-stu-id="3a681-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="3a681-139">Assurez-vous de mettre à jour le chemin de fichier CSV à l’emplacement des données GitHub que vous avez téléchargées.</span><span class="sxs-lookup"><span data-stu-id="3a681-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="3a681-140">Utilisez <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> la méthode pour laisser tomber les lignes <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> avec des valeurs NA (null), et la méthode pour supprimer certaines colonnes de vos données.</span><span class="sxs-lookup"><span data-stu-id="3a681-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="3a681-141">Cela permet de prévenir les erreurs si vous essayez d’analyser des données nulles ou des colonnes qui ne sont pas pertinentes à votre analyse finale.</span><span class="sxs-lookup"><span data-stu-id="3a681-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="3a681-142">Analyser les données</span><span class="sxs-lookup"><span data-stu-id="3a681-142">Analyze the data</span></span>

<span data-ttu-id="3a681-143">Spark SQL vous permet de faire des appels SQL sur vos données.</span><span class="sxs-lookup"><span data-stu-id="3a681-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="3a681-144">Il est courant de combiner des fonctions définies par l’utilisateur et Spark SQL pour appliquer une fonction définie par l’utilisateur à toutes les lignes de votre DataFrame.</span><span class="sxs-lookup"><span data-stu-id="3a681-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="3a681-145">Vous pouvez `spark.Sql` appeler spécifiquement pour imiter les appels SQL standard vus dans d’autres types d’applications.</span><span class="sxs-lookup"><span data-stu-id="3a681-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="3a681-146">Vous pouvez également <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> appeler <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> des méthodes comme et combiner spécifiquement, filtrer et effectuer des calculs sur vos données.</span><span class="sxs-lookup"><span data-stu-id="3a681-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="3a681-147">Le but de cette application est d’obtenir quelques informations sur les données des projets GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a681-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="3a681-148">Ajoutez les extraits de code suivants à votre programme pour analyser les données.</span><span class="sxs-lookup"><span data-stu-id="3a681-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="3a681-149">Ajouter le bloc de code suivant trouve le nombre de fois que chaque langue a été fourchée.</span><span class="sxs-lookup"><span data-stu-id="3a681-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="3a681-150">Tout d’abord, les données sont regroupées par langue.</span><span class="sxs-lookup"><span data-stu-id="3a681-150">First, the data is grouped by language.</span></span> <span data-ttu-id="3a681-151">Ensuite, le nombre moyen de fourchettes de chaque langue est pris.</span><span class="sxs-lookup"><span data-stu-id="3a681-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="3a681-152">Ajoutez le bloc de code suivant pour commander le nombre moyen de fourchettes dans l’ordre décroissant pour voir quelles langues sont les plus fourchées.</span><span class="sxs-lookup"><span data-stu-id="3a681-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="3a681-153">Autrement dit, le plus grand nombre de fourchettes apparaîtra en premier.</span><span class="sxs-lookup"><span data-stu-id="3a681-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="3a681-154">Le prochain bloc de code vous montre la rapidité avec laquelle les projets ont été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="3a681-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="3a681-155">Vous enregistrez une nouvelle fonction définie par l’utilisateur appelée *MyUDF* et la comparez à une date, *s_referenceDate*, qui a été déclarée au début du tutoriel.</span><span class="sxs-lookup"><span data-stu-id="3a681-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="3a681-156">La date de chaque projet est comparée à la date de référence.</span><span class="sxs-lookup"><span data-stu-id="3a681-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="3a681-157">Ensuite, Spark SQL est utilisé pour appeler l’UDF sur chaque rangée des données pour analyser chaque projet dans l’ensemble de données.</span><span class="sxs-lookup"><span data-stu-id="3a681-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="3a681-158">Appelez `spark.Stop()` pour mettre fin à la SparkSession.</span><span class="sxs-lookup"><span data-stu-id="3a681-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="3a681-159">Utilisez spark-submit pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="3a681-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="3a681-160">Utilisez la commande suivante pour créer votre application .NET :</span><span class="sxs-lookup"><span data-stu-id="3a681-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="3a681-161">Exécutez votre `spark-submit`application avec .</span><span class="sxs-lookup"><span data-stu-id="3a681-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="3a681-162">Assurez-vous de mettre à jour la commande suivante avec les chemins réels de votre fichier de pot Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="3a681-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="3a681-163">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="3a681-163">Get the code</span></span>

<span data-ttu-id="3a681-164">Vous pouvez voir la [solution complète](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="3a681-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3a681-165">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3a681-165">Next steps</span></span>

<span data-ttu-id="3a681-166">Avancez à l’article suivant pour apprendre à traiter les données de streaming avec .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3a681-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3a681-167">Tutorial: Streaming structuré avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3a681-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
