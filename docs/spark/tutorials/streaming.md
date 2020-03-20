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
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Tutorial: Streaming structuré avec .NET pour Apache Spark

Ce tutoriel vous apprend à invoquer Spark Structured Streaming en utilisant .NET pour Apache Spark. Spark Structured Streaming est le support d’Apache Spark pour le traitement des flux de données en temps réel. Le traitement des flux signifie analyser les données en direct au fur et à mesure qu’elles sont produites.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créez et exécutez une application .NET pour Apache Spark
> * Utilisez netcat pour créer un flux de données
> * Utiliser les fonctions définies par l’utilisateur et SparkSQL pour analyser les données en streaming

## <a name="prerequisites"></a>Conditions préalables requises

Si c’est votre premier .NET pour Apache Spark application, commencez par le [tutoriel Getting Started](get-started.md) pour se familiariser avec les bases.

## <a name="create-a-console-application"></a>Création d’une application console

1. Dans votre application rapide, exécutez les commandes suivantes pour créer une nouvelle application de console :

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   La `dotnet` commande `new` crée une `console` application de type pour vous. Le `-o` paramètre crée un répertoire nommé *mySparkStreamingApp* où votre application est stockée et la remplit avec les fichiers requis. La `cd mySparkStreamingApp` commande modifie l’annuaire de l’annuaire de l’application que vous venez de créer.

1. Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft.Spark. Dans votre console, exécutez la commande suivante :

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Établir et se connecter à un flux de données

Une façon populaire de tester le traitement des flux est par **netcat**. netcat (également connu sous le nom *nc*) vous permet de lire et d’écrire à des connexions réseau. Vous établissez une connexion réseau avec netcat à travers une fenêtre terminale.

### <a name="create-a-data-stream-with-netcat"></a>Créer un flux de données avec netcat

1. [Télécharger netcat](https://sourceforge.net/projects/nc110/files/). Ensuite, extraire le fichier du téléchargement zip et appendicez le répertoire que vous avez extrait à votre variable d’environnement "PATH".

2. Pour démarrer une nouvelle connexion, ouvrez une nouvelle console et exécutez la commande suivante qui se connecte à localhost sur le port 9999.

   Sur Windows :

   ```console
   nc -vvv -l -p 9999
   ```

   Sur Linux :

   ```console
   nc -lk 9999
   ```

   Votre programme Spark écoute l’entrée que vous tapez dans cette invite de commande.

### <a name="create-a-sparksession"></a>Créer une SparkSession

1. Ajoutez les `using` instructions supplémentaires suivantes en haut du fichier *Program.cs* dans *mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Ajoutez le code `Main` suivant à votre `SparkSession`méthode pour créer un nouveau . La spark Session est le point d’entrée de la programmation Spark avec l’API Dataset et DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   L’appel de l’objet *d’étincelle* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et DataFrame tout au long de votre programme.

### <a name="connect-to-a-stream-with-readstream"></a>Connectez-vous à un flux avec ReadStream()

La `ReadStream()` méthode `DataStreamReader` renvoie un qui peut être `DataFrame`utilisé pour lire les données de streaming en tant que . Inclure les informations d’hôte et de port pour indiquer à votre application Spark où s’attendre à ses données de streaming.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Enregistrer une fonction définie par l’utilisateur

Vous pouvez utiliser des FUD, *des fonctions définies par l’utilisateur,* des applications Spark pour effectuer des calculs et des analyses sur vos données.

Ajoutez le code `Main` suivant à votre méthode `udfArray`pour enregistrer un UDF appelé .

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Cet UDF traite chaque chaîne qu’il reçoit du terminal netcat pour produire un tableau qui comprend la chaîne d’origine (contenue *dans*str ), suivie par la chaîne originale concatenated avec la longueur de la chaîne d’origine.

Par exemple, entrer dans *le monde Hello* dans le terminal netcat produit un tableau où :

* tableau\[0] - Bonjour monde
* tableau\[1] - Bonjour monde 11

## <a name="use-sparksql"></a>Utiliser SparkSQL

Utilisez SparkSQL pour effectuer diverses fonctions sur les données stockées dans votre DataFrame. Il est courant de combiner les FUD et SparkSQL pour appliquer un UDF à chaque rangée d’un DataFrame.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Cet extrait de code applique *udfArray* à chaque valeur de votre DataFrame, qui représente chaque chaîne lue à partir de votre terminal netcat. Appliquez la méthode <xref:Microsoft.Spark.Sql.Functions.Explode%2A> SparkSQL pour mettre chaque entrée de votre tableau dans sa propre rangée. Enfin, <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> utilisez pour placer les colonnes que vous avez produites dans le nouveau tableau DataFrameDF. *arrayDF.*

## <a name="display-your-stream"></a>Affichez votre flux

Utilisez <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> pour établir les caractéristiques de votre sortie, telles que l’impression des résultats sur la console et l’affichage seulement de la sortie la plus récente.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Exécuter votre code

Le streaming structuré dans Spark traite les données à travers une série de petits **lots**.  Lorsque vous exécutez votre programme, l’invite de commande où vous établissez la connexion netcat vous permet de commencer à taper. Chaque fois que vous appuyez sur la clé Enter après avoir tapé des données dans cette invite de commande, Spark considère votre entrée comme un lot et exécute l’UDF.

### <a name="use-spark-submit-to-run-your-app"></a>Utilisez spark-submit pour exécuter votre application

Après avoir commencé une nouvelle session netcat, `spark-submit` ouvrez un nouveau terminal et exécutez votre commande, semblable à la commande suivante :

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Assurez-vous de mettre à jour la commande ci-dessus avec le chemin réel vers votre fichier de pot Microsoft Spark. La commande ci-dessus suppose également que votre serveur netcat fonctionne sur le port localhost 9999.

## <a name="get-the-code"></a>Obtenir le code

Ce tutoriel utilise [l’exemple StructuredNetworkCharacterCount.cs,](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) mais il ya trois autres exemples de traitement de flux complet sur GitHub:

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): nombre de mots sur les données diffusées à partir de n’importe quelle source
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): compte de mots sur les données avec logique de fenêtre
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): nombre de mots sur les données diffusées depuis Kafka

## <a name="next-steps"></a>Étapes suivantes

Avancez à l’article suivant pour apprendre à déployer votre application .NET pour Apache Spark à Databricks.
> [!div class="nextstepaction"]
> [Tutorial: Déployer une application .NET pour Apache Spark à Databricks](databricks-deployment.md)
