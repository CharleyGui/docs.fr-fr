---
title: Didacticiel de diffusion en continu structurée avec .NET pour Apache Spark
description: Dans ce didacticiel, vous allez apprendre à utiliser .NET pour Apache Spark pour Spark Structured streaming.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 3a02ac52155971f480c7f0c338d4a2a9a7d1d81c
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688018"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="7096d-103">Didacticiel : diffusion en continu structurée avec .NET pour Apache Spark</span><span class="sxs-lookup"><span data-stu-id="7096d-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="7096d-104">Ce didacticiel vous apprend à appeler Spark Structured streaming à l’aide de .NET pour Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="7096d-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="7096d-105">Spark Structured streaming est la prise en charge par Apache Spark du traitement des flux de données en temps réel.</span><span class="sxs-lookup"><span data-stu-id="7096d-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="7096d-106">Le traitement des flux de données consiste à analyser les données actives à mesure qu’elles sont produites.</span><span class="sxs-lookup"><span data-stu-id="7096d-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="7096d-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="7096d-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7096d-108">Créer et exécuter un .NET pour Apache Spark application</span><span class="sxs-lookup"><span data-stu-id="7096d-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="7096d-109">Utiliser netcat pour créer un flux de données</span><span class="sxs-lookup"><span data-stu-id="7096d-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="7096d-110">Utiliser des fonctions définies par l’utilisateur et SparkSQL pour analyser les données de streaming</span><span class="sxs-lookup"><span data-stu-id="7096d-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7096d-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="7096d-111">Prerequisites</span></span>

<span data-ttu-id="7096d-112">S’il s’agit de votre première application .NET pour Apache Spark, commencez par le [didacticiel prise en main](get-started.md) pour vous familiariser avec les principes de base.</span><span class="sxs-lookup"><span data-stu-id="7096d-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="7096d-113">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="7096d-113">Create a console application</span></span>

1. <span data-ttu-id="7096d-114">À l’invite de commandes, exécutez les commandes suivantes pour créer une nouvelle application console :</span><span class="sxs-lookup"><span data-stu-id="7096d-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="7096d-115">La `dotnet` commande crée une `new` application de type `console` pour vous.</span><span class="sxs-lookup"><span data-stu-id="7096d-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="7096d-116">Le `-o` paramètre crée un répertoire nommé *mySparkStreamingApp* dans lequel votre application est stockée et le remplit avec les fichiers requis.</span><span class="sxs-lookup"><span data-stu-id="7096d-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="7096d-117">La `cd mySparkStreamingApp` commande remplace le répertoire par le répertoire d’application que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="7096d-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="7096d-118">Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark.</span><span class="sxs-lookup"><span data-stu-id="7096d-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="7096d-119">Dans votre console, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7096d-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="7096d-120">Établir et se connecter à un flux de données</span><span class="sxs-lookup"><span data-stu-id="7096d-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="7096d-121">L’un des moyens les plus populaires pour tester le traitement des flux est d’utiliser **netcat**.</span><span class="sxs-lookup"><span data-stu-id="7096d-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="7096d-122">netcat (également appelé *NC*) vous permet de lire et d’écrire sur des connexions réseau.</span><span class="sxs-lookup"><span data-stu-id="7096d-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="7096d-123">Vous établissez une connexion réseau avec netcat via une fenêtre de terminal.</span><span class="sxs-lookup"><span data-stu-id="7096d-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="7096d-124">Créer un flux de données avec netcat</span><span class="sxs-lookup"><span data-stu-id="7096d-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="7096d-125">[Téléchargez netcat](https://sourceforge.net/projects/nc110/files/).</span><span class="sxs-lookup"><span data-stu-id="7096d-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="7096d-126">Ensuite, extrayez le fichier du fichier zip Download et ajoutez le répertoire que vous avez extrait à votre variable d’environnement « PATH ».</span><span class="sxs-lookup"><span data-stu-id="7096d-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="7096d-127">Pour démarrer une nouvelle connexion, ouvrez une nouvelle console et exécutez la commande suivante, qui se connecte à localhost sur le port 9999.</span><span class="sxs-lookup"><span data-stu-id="7096d-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="7096d-128">Sur Windows :</span><span class="sxs-lookup"><span data-stu-id="7096d-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="7096d-129">Sur Linux :</span><span class="sxs-lookup"><span data-stu-id="7096d-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="7096d-130">Votre programme Spark écoute l’entrée que vous tapez dans cette invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7096d-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="7096d-131">Créer un SparkSession</span><span class="sxs-lookup"><span data-stu-id="7096d-131">Create a SparkSession</span></span>

1. <span data-ttu-id="7096d-132">Ajoutez les instructions supplémentaires suivantes `using` en haut du fichier *Program.cs* dans *mySparkStreamingApp*:</span><span class="sxs-lookup"><span data-stu-id="7096d-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="7096d-133">Ajoutez le code suivant à votre `Main` méthode pour créer un nouveau `SparkSession` .</span><span class="sxs-lookup"><span data-stu-id="7096d-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="7096d-134">La session Spark est le point d’entrée de la programmation Spark avec l’API DataSet et tableau.</span><span class="sxs-lookup"><span data-stu-id="7096d-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="7096d-135">L’appel de l’objet *Spark* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et tableau dans votre programme.</span><span class="sxs-lookup"><span data-stu-id="7096d-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="7096d-136">Se connecter à un flux avec ReadStream ()</span><span class="sxs-lookup"><span data-stu-id="7096d-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="7096d-137">La `ReadStream()` méthode retourne un `DataStreamReader` qui peut être utilisé pour lire les données de diffusion en continu dans en tant que `DataFrame` .</span><span class="sxs-lookup"><span data-stu-id="7096d-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="7096d-138">Incluez les informations sur l’hôte et le port pour indiquer à votre application Spark où les données de diffusion en continu sont attendues.</span><span class="sxs-lookup"><span data-stu-id="7096d-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="7096d-139">Inscrire une fonction définie par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="7096d-139">Register a user-defined function</span></span>

<span data-ttu-id="7096d-140">Vous pouvez utiliser des *fonctions définies par l’utilisateur*(UDF) dans des applications Spark pour effectuer des calculs et des analyses sur vos données.</span><span class="sxs-lookup"><span data-stu-id="7096d-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="7096d-141">Ajoutez le code suivant à votre `Main` méthode pour inscrire une fonction UDF appelée `udfArray` .</span><span class="sxs-lookup"><span data-stu-id="7096d-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="7096d-142">Cette FDU traite chaque chaîne qu’elle reçoit du terminal netcat pour produire un tableau qui comprend la chaîne d’origine (contenue dans *Str*), suivie de la chaîne d’origine concaténée avec la longueur de la chaîne d’origine.</span><span class="sxs-lookup"><span data-stu-id="7096d-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="7096d-143">Par exemple, si vous entrez *Hello World* dans le terminal netcat, vous obtenez un tableau où :</span><span class="sxs-lookup"><span data-stu-id="7096d-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="7096d-144">tableau \[ 0] = Hello World</span><span class="sxs-lookup"><span data-stu-id="7096d-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="7096d-145">tableau \[ 1] = Hello World 11</span><span class="sxs-lookup"><span data-stu-id="7096d-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="7096d-146">Utiliser SparkSQL</span><span class="sxs-lookup"><span data-stu-id="7096d-146">Use SparkSQL</span></span>

<span data-ttu-id="7096d-147">Utilisez SparkSQL pour effectuer diverses fonctions sur les données stockées dans votre tableau.</span><span class="sxs-lookup"><span data-stu-id="7096d-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="7096d-148">Il est courant de combiner les fonctions définies par l’utilisateur et SparkSQL pour appliquer une FDU à chaque ligne d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="7096d-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="7096d-149">Cet extrait de code applique *udfArray* à chaque valeur de votre tableau, qui représente chaque chaîne lue à partir de votre terminal netcat.</span><span class="sxs-lookup"><span data-stu-id="7096d-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="7096d-150">Appliquez la méthode SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> pour placer chaque entrée de votre tableau sur sa propre ligne.</span><span class="sxs-lookup"><span data-stu-id="7096d-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="7096d-151">Enfin, utilisez <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> pour placer les colonnes que vous avez produites dans le nouveau *arrayDF tableau.*</span><span class="sxs-lookup"><span data-stu-id="7096d-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="7096d-152">Afficher votre flux</span><span class="sxs-lookup"><span data-stu-id="7096d-152">Display your stream</span></span>

<span data-ttu-id="7096d-153">Utilisez <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> pour définir les caractéristiques de votre sortie, telles que l’impression des résultats sur la console et l’affichage de la sortie la plus récente.</span><span class="sxs-lookup"><span data-stu-id="7096d-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="7096d-154">Exécuter votre code</span><span class="sxs-lookup"><span data-stu-id="7096d-154">Run your code</span></span>

<span data-ttu-id="7096d-155">La diffusion en continu structurée dans Spark traite les données via une série de petits **lots**.</span><span class="sxs-lookup"><span data-stu-id="7096d-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="7096d-156">Lorsque vous exécutez votre programme, l’invite de commandes où vous établissez la connexion netcat vous permet de commencer à taper.</span><span class="sxs-lookup"><span data-stu-id="7096d-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="7096d-157">Chaque fois que vous appuyez sur la touche entrée après avoir tapé les données dans cette invite de commandes, Spark considère votre entrée par un lot et exécute la fonction définie par l’usage.</span><span class="sxs-lookup"><span data-stu-id="7096d-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="7096d-158">Utiliser Spark-submit pour exécuter votre application</span><span class="sxs-lookup"><span data-stu-id="7096d-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="7096d-159">Après avoir démarré une nouvelle session netcat, ouvrez un nouveau terminal et exécutez la `spark-submit` commande, comme dans la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="7096d-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="7096d-160">Veillez à mettre à jour la commande ci-dessus avec le chemin d’accès réel à votre fichier jar Microsoft Spark.</span><span class="sxs-lookup"><span data-stu-id="7096d-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="7096d-161">La commande ci-dessus suppose également que votre serveur netcat est en cours d’exécution sur le port localhost 9999.</span><span class="sxs-lookup"><span data-stu-id="7096d-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="7096d-162">Obtenir le code</span><span class="sxs-lookup"><span data-stu-id="7096d-162">Get the code</span></span>

<span data-ttu-id="7096d-163">Ce didacticiel utilise l’exemple [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , mais il existe trois autres exemples de traitement de flux complet sur GitHub :</span><span class="sxs-lookup"><span data-stu-id="7096d-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="7096d-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): nombre de mots sur les données diffusées en continu à partir de n’importe quelle source</span><span class="sxs-lookup"><span data-stu-id="7096d-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="7096d-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): nombre de mots sur les données avec une logique de fenêtrage</span><span class="sxs-lookup"><span data-stu-id="7096d-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="7096d-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): nombre de mots sur les données diffusées en continu à partir de Kafka</span><span class="sxs-lookup"><span data-stu-id="7096d-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="7096d-167">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7096d-167">Next steps</span></span>

<span data-ttu-id="7096d-168">Passez à l’article suivant pour apprendre à déployer votre application .NET pour Apache Spark sur Databricks.</span><span class="sxs-lookup"><span data-stu-id="7096d-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="7096d-169">Didacticiel : déployer une application .NET pour Apache Spark sur Databricks</span><span class="sxs-lookup"><span data-stu-id="7096d-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
