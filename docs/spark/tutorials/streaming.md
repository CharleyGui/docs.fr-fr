---
title: Didacticiel de diffusion en continu structurée avec .NET pour Apache Spark
description: Dans ce didacticiel, vous allez apprendre à utiliser .NET pour Apache Spark pour Spark Structured streaming.
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 83d44af080d95ab6f9311ddd3ca4860806757436
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504046"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>Didacticiel : diffusion en continu structurée avec .NET pour Apache Spark 

Ce didacticiel vous apprend à appeler Spark Structured streaming à l’aide de .NET pour Apache Spark. Spark Structured streaming est la prise en charge par Apache Spark du traitement des flux de données en temps réel. Le traitement des flux de données consiste à analyser les données actives à mesure qu’elles sont produites.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créer et exécuter un .NET pour Apache Spark application
> * Utiliser netcat pour créer un flux de données
> * Utiliser des fonctions définies par l’utilisateur et SparkSQL pour analyser les données de streaming

## <a name="prerequisites"></a>Conditions préalables requises

S’il s’agit de votre première application .NET pour Apache Spark, commencez par le [didacticiel prise en main](get-started.md) pour vous familiariser avec les principes de base.

## <a name="create-a-console-application"></a>Création d’une application console

1. À l’invite de commandes, exécutez les commandes suivantes pour créer une nouvelle application console :

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   La commande `dotnet` crée pour vous une application `new` de type `console`. Le paramètre `-o` crée un répertoire nommé *mySparkStreamingApp* dans lequel votre application est stockée et le remplit avec les fichiers requis. La commande `cd mySparkStreamingApp` remplace le répertoire par le répertoire d’application que vous venez de créer.

1. Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark. Dans votre console, exécutez la commande suivante :

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>Établir et se connecter à un flux de données

L’un des moyens les plus populaires pour tester le traitement des flux est d’utiliser **netcat**. netcat (également appelé *NC*) vous permet de lire et d’écrire sur des connexions réseau. Vous établissez une connexion réseau avec netcat via une fenêtre de terminal. 

### <a name="create-a-data-stream-with-netcat"></a>Créer un flux de données avec netcat

1. [Téléchargez netcat](https://sourceforge.net/projects/nc110/files/). Ensuite, extrayez le fichier du fichier zip Download et ajoutez le répertoire que vous avez extrait à votre variable d’environnement « PATH ».

2. Pour démarrer une nouvelle connexion, ouvrez une nouvelle console et exécutez la commande suivante, qui se connecte à localhost sur le port 9999.

   Sur Windows :

   ```console
   nc -vvv -l -p 9999
   ```

   Sur Linux :

   ```console
   nc -lk 9999
   ```

   Votre programme Spark écoute l’entrée que vous tapez dans cette invite de commandes.

### <a name="create-a-sparksession"></a>Créer un SparkSession

1. Ajoutez les instructions `using` supplémentaires suivantes au début du fichier *Program.cs* dans *mySparkStreamingApp*:

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Ajoutez le code suivant à votre méthode `Main` pour créer une `SparkSession`. La session Spark est le point d’entrée de la programmation Spark avec l’API DataSet et tableau.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   L’appel de l’objet *Spark* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et tableau dans votre programme.

### <a name="connect-to-a-stream-with-readstream"></a>Se connecter à un flux avec ReadStream ()

La méthode `ReadStream()` retourne un `DataStreamReader` qui peut être utilisé pour lire les données de diffusion en continu dans en tant que `DataFrame`. Incluez les informations sur l’hôte et le port pour indiquer à votre application Spark où les données de diffusion en continu sont attendues.

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>Inscrire une fonction définie par l’utilisateur

Vous pouvez utiliser des *fonctions définies par l’utilisateur*(UDF) dans des applications Spark pour effectuer des calculs et des analyses sur vos données.

Ajoutez le code suivant à votre méthode `Main` pour inscrire une fonction UDF appelée `udfArray`. 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

Cette FDU traite chaque chaîne qu’elle reçoit du terminal netcat pour produire un tableau qui comprend la chaîne d’origine (contenue dans *Str*), suivie de la chaîne d’origine concaténée avec la longueur de la chaîne d’origine. 

Par exemple, si vous entrez *Hello World* dans le terminal netcat, vous obtenez un tableau où :

* Tableau\[0] = Hello World
* Tableau\[1] = Hello World 11

## <a name="use-sparksql"></a>Utiliser SparkSQL

Utilisez SparkSQL pour effectuer diverses fonctions sur les données stockées dans votre tableau. Il est courant de combiner les fonctions définies par l’utilisateur et SparkSQL pour appliquer une FDU à chaque ligne d’un tableau.

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

Cet extrait de code applique *udfArray* à chaque valeur de votre tableau, qui représente chaque chaîne lue à partir de votre terminal netcat. Appliquez la méthode SparkSQL <xref:Microsoft.Spark.Sql.Functions.Explode%2A> pour placer chaque entrée de votre tableau sur sa propre ligne. Enfin, utilisez <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> pour placer les colonnes que vous avez produites dans le nouveau *ArrayDF tableau.*

## <a name="display-your-stream"></a>Afficher votre flux

Utilisez <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> pour définir les caractéristiques de votre sortie, telles que l’impression des résultats sur la console et l’affichage de la sortie la plus récente.

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>Exécuter votre code

La diffusion en continu structurée dans Spark traite les données via une série de petits **lots**.  Lorsque vous exécutez votre programme, l’invite de commandes où vous établissez la connexion netcat vous permet de commencer à taper. Chaque fois que vous appuyez sur la touche entrée après avoir tapé les données dans cette invite de commandes, Spark considère votre entrée par un lot et exécute la fonction définie par l’usage.

### <a name="use-spark-submit-to-run-your-app"></a>Utiliser Spark-submit pour exécuter votre application

Après avoir démarré une nouvelle session netcat, ouvrez un nouveau terminal et exécutez votre commande `spark-submit`, comme dans la commande suivante :

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> Veillez à mettre à jour la commande ci-dessus avec le chemin d’accès réel à votre fichier jar Microsoft Spark. La commande ci-dessus suppose également que votre serveur netcat est en cours d’exécution sur le port localhost 9999.

## <a name="get-the-code"></a>Obtenir le code

Ce didacticiel utilise l’exemple [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) , mais il existe trois autres exemples de traitement de flux complet sur GitHub :

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): nombre de mots sur les données diffusées en continu à partir de n’importe quelle source
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): nombre de mots sur les données avec une logique de fenêtrage
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): nombre de mots sur les données diffusées en continu à partir de Kafka

## <a name="next-steps"></a>Étapes suivantes

Passez à l’article suivant pour apprendre à déployer votre application .NET pour Apache Spark sur Databricks.
> [!div class="nextstepaction"]
> [Didacticiel : déployer une application .NET pour Apache Spark sur Databricks](databricks-deployment.md)
