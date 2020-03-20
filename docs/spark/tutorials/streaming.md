---
title: Streaming structuré avec .NET pour Apache Spark tutoriel
description: Dans ce tutoriel, vous apprenez à utiliser .NET pour Apache Spark pour Spark Structured Streaming.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186513"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="04275-103">Tutorial: Streaming structuré avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="04275-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="04275-104">Ce tutoriel vous apprend à invoquer Spark Structured Streaming en utilisant .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="04275-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="04275-105">Spark Structured Streaming est le support d’Apache Spark pour le traitement des flux de données en temps réel.</span><span class="sxs-lookup"><span data-stu-id="04275-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="04275-106">Le traitement des flux signifie analyser les données en direct au fur et à mesure qu’elles sont produites.</span><span class="sxs-lookup"><span data-stu-id="04275-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="04275-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="04275-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="04275-108">Créez et exécutez une application .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="04275-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="04275-109">Utilisez netcat pour créer un flux de données</span><span class="sxs-lookup"><span data-stu-id="04275-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="04275-110">Utiliser les fonctions définies par l’utilisateur et SparkSQL pour analyser les données en streaming</span><span class="sxs-lookup"><span data-stu-id="04275-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04275-111">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="04275-111">Prerequisites</span></span>

<span data-ttu-id="04275-112">Si c’est votre premier .NET pour Apache Spark application, commencez par le [tutoriel Getting Started](get-started.md) pour se familiariser avec les bases.</span><span class="sxs-lookup"><span data-stu-id="04275-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="04275-113">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="04275-113">Create a console application</span></span>

1. <span data-ttu-id="04275-114">Dans votre application rapide, exécutez les commandes suivantes pour créer une nouvelle application de console :</span><span class="sxs-lookup"><span data-stu-id="04275-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="04275-115">La `dotnet` commande `new` crée une `console` application de type pour vous.</span><span class="sxs-lookup"><span data-stu-id="04275-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="04275-116">Le `-o` paramètre crée un répertoire nommé *mySparkStreamingApp* où votre application est stockée et la remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="04275-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="04275-117">La `cd mySparkStreamingApp` commande modifie l’annuaire de l’annuaire de l’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="04275-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="04275-118">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft.Spark.</span><span class="sxs-lookup"><span data-stu-id="04275-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="04275-119">Dans votre console, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="04275-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="04275-120">Établir et se connecter à un flux de données</span><span class="sxs-lookup"><span data-stu-id="04275-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="04275-121">Une façon populaire de tester le traitement des flux est par **netcat**.</span><span class="sxs-lookup"><span data-stu-id="04275-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="04275-122">netcat (également connu sous le nom *nc*) vous permet de lire et d’écrire à des connexions réseau.</span><span class="sxs-lookup"><span data-stu-id="04275-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="04275-123">Vous établissez une connexion réseau avec netcat à travers une fenêtre terminale.</span><span class="sxs-lookup"><span data-stu-id="04275-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="04275-124">Créer un flux de données avec netcat</span><span class="sxs-lookup"><span data-stu-id="04275-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="04275-125">[Télécharger netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="04275-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="04275-126">Ensuite, extraire le fichier du téléchargement zip et appendicez le répertoire que vous avez extrait à votre variable d’environnement "PATH".</span><span class="sxs-lookup"><span data-stu-id="04275-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="04275-127">Pour démarrer une nouvelle connexion, ouvrez une nouvelle console et exécutez la commande suivante qui se connecte à localhost sur le port 9999.</span><span class="sxs-lookup"><span data-stu-id="04275-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="04275-128">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="04275-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="04275-129">Sur Linux :</span><span class="sxs-lookup"><span data-stu-id="04275-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="04275-130">Votre programme Spark écoute l’entrée que vous tapez dans cette invite de commande.</span><span class="sxs-lookup"><span data-stu-id="04275-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="04275-131">Créer une SparkSession</span><span class="sxs-lookup"><span data-stu-id="04275-131">Create a SparkSession</span></span>

1. <span data-ttu-id="04275-132">Ajoutez les `using` instructions supplémentaires suivantes en haut du fichier *Program.cs* dans *mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="04275-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="04275-133">Ajoutez le code `Main` suivant à votre `SparkSession`méthode pour créer un nouveau .</span><span class="sxs-lookup"><span data-stu-id="04275-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="04275-134">La spark Session est le point d’entrée de la programmation Spark avec l’API Dataset et DataFrame.</span><span class="sxs-lookup"><span data-stu-id="04275-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="04275-135">L’appel de l’objet *d’étincelle* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et DataFrame tout au long de votre programme.</span><span class="sxs-lookup"><span data-stu-id="04275-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="04275-136">Connectez-vous à un flux avec ReadStream()</span><span class="sxs-lookup"><span data-stu-id="04275-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="04275-137">La `ReadStream()` méthode `DataStreamReader` renvoie un qui peut être `DataFrame`utilisé pour lire les données de streaming en tant que .</span><span class="sxs-lookup"><span data-stu-id="04275-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="04275-138">Inclure les informations d’hôte et de port pour indiquer à votre application Spark où s’attendre à ses données de streaming.</span><span class="sxs-lookup"><span data-stu-id="04275-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="04275-139">Enregistrer une fonction définie par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="04275-139">Register a user-defined function</span></span>

<span data-ttu-id="04275-140">Vous pouvez utiliser des FUD, *des fonctions définies par l’utilisateur,* des applications Spark pour effectuer des calculs et des analyses sur vos données.</span><span class="sxs-lookup"><span data-stu-id="04275-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="04275-141">Ajoutez le code `Main` suivant à votre méthode `udfArray`pour enregistrer un UDF appelé .</span><span class="sxs-lookup"><span data-stu-id="04275-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="04275-142">Cet UDF traite chaque chaîne qu’il reçoit du terminal netcat pour produire un tableau qui comprend la chaîne d’origine (contenue *dans*str ), suivie par la chaîne originale concatenated avec la longueur de la chaîne d’origine.</span><span class="sxs-lookup"><span data-stu-id="04275-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="04275-143">Par exemple, entrer dans *le monde Hello* dans le terminal netcat produit un tableau où :</span><span class="sxs-lookup"><span data-stu-id="04275-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="04275-144">tableau\[0] - Bonjour monde</span><span class="sxs-lookup"><span data-stu-id="04275-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="04275-145">tableau\[1] - Bonjour monde 11</span><span class="sxs-lookup"><span data-stu-id="04275-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="04275-146">Utiliser SparkSQL</span><span class="sxs-lookup"><span data-stu-id="04275-146">Use SparkSQL</span></span>

<span data-ttu-id="04275-147">Utilisez SparkSQL pour effectuer diverses fonctions sur les données stockées dans votre DataFrame.</span><span class="sxs-lookup"><span data-stu-id="04275-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="04275-148">Il est courant de combiner les FUD et SparkSQL pour appliquer un UDF à chaque rangée d’un DataFrame.</span><span class="sxs-lookup"><span data-stu-id="04275-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="04275-149">Cet extrait de code applique *udfArray* à chaque valeur de votre DataFrame, qui représente chaque chaîne lue à partir de votre terminal netcat.</span><span class="sxs-lookup"><span data-stu-id="04275-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="04275-150">Appliquez la méthode <xref:Microsoft.Spark.Sql.Functions.Explode%2A> SparkSQL pour mettre chaque entrée de votre tableau dans sa propre rangée.</span><span class="sxs-lookup"><span data-stu-id="04275-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="04275-151">Enfin, <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> utilisez pour placer les colonnes que vous avez produites dans le nouveau tableau DataFrameDF. *arrayDF.*</span><span class="sxs-lookup"><span data-stu-id="04275-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="04275-152">Affichez votre flux</span><span class="sxs-lookup"><span data-stu-id="04275-152">Display your stream</span></span>

<span data-ttu-id="04275-153">Utilisez <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> pour établir les caractéristiques de votre sortie, telles que l’impression des résultats sur la console et l’affichage seulement de la sortie la plus récente.</span><span class="sxs-lookup"><span data-stu-id="04275-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="04275-154">Exécuter votre code</span><span class="sxs-lookup"><span data-stu-id="04275-154">Run your code</span></span>

<span data-ttu-id="04275-155">Le streaming structuré dans Spark traite les données à travers une série de petits **lots**.</span><span class="sxs-lookup"><span data-stu-id="04275-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="04275-156">Lorsque vous exécutez votre programme, l’invite de commande où vous établissez la connexion netcat vous permet de commencer à taper.</span><span class="sxs-lookup"><span data-stu-id="04275-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="04275-157">Chaque fois que vous appuyez sur la clé Enter après avoir tapé des données dans cette invite de commande, Spark considère votre entrée comme un lot et exécute l’UDF.</span><span class="sxs-lookup"><span data-stu-id="04275-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="04275-158">Utilisez spark-submit pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="04275-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="04275-159">Après avoir commencé une nouvelle session netcat, `spark-submit` ouvrez un nouveau terminal et exécutez votre commande, semblable à la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="04275-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="04275-160">Assurez-vous de mettre à jour la commande ci-dessus avec le chemin réel vers votre fichier de pot Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="04275-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="04275-161">La commande ci-dessus suppose également que votre serveur netcat fonctionne sur le port localhost 9999.</span><span class="sxs-lookup"><span data-stu-id="04275-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="04275-162">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="04275-162">Get the code</span></span>

<span data-ttu-id="04275-163">Ce tutoriel utilise [l’exemple StructuredNetworkCharacterCount.cs,](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) mais il ya trois autres exemples de traitement de flux complet sur GitHub:</span><span class="sxs-lookup"><span data-stu-id="04275-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="04275-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): nombre de mots sur les données diffusées à partir de n’importe quelle source</span><span class="sxs-lookup"><span data-stu-id="04275-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="04275-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): compte de mots sur les données avec logique de fenêtre</span><span class="sxs-lookup"><span data-stu-id="04275-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="04275-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): nombre de mots sur les données diffusées depuis Kafka</span><span class="sxs-lookup"><span data-stu-id="04275-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="04275-167">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="04275-167">Next steps</span></span>

<span data-ttu-id="04275-168">Avancez à l’article suivant pour apprendre à déployer votre application .NET pour Apache Spark à Databricks.</span><span class="sxs-lookup"><span data-stu-id="04275-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="04275-169">Tutorial: Déployer une application .NET pour Apache Spark à Databricks</span><span class="sxs-lookup"><span data-stu-id="04275-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
