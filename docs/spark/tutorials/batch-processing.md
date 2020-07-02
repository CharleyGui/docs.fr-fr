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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Didacticiel : effectuer un traitement par lots avec .NET pour Apache Spark

Dans ce didacticiel, vous allez apprendre à effectuer un traitement par lots à l’aide de .NET pour Apache Spark. Le traitement par lots est la transformation des données au repos, ce qui signifie que les données sources ont déjà été chargées dans le stockage des données.

Le traitement par lots est généralement effectué sur des jeux de données volumineux et plats qui doivent être préparés pour une analyse plus poussée. Le traitement des journaux et l’entreposage des données sont des scénarios courants de traitement par lots. Dans ce scénario, vous analysez des informations sur les projets GitHub, telles que le nombre de fois où différents projets ont été dupliqués ou la manière dont les projets récents ont été mis à jour.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créer et exécuter un .NET pour Apache Spark application
> * Lire des données dans un tableau et les préparer pour l’analyse
> * Traitement des données à l’aide de Spark SQL

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a>Prérequis

Si c’est la première fois que vous utilisez .NET pour Apache Spark, consultez le didacticiel [prise en main de .net pour Apache Spark](get-started.md) pour apprendre à préparer votre environnement et à exécuter votre première application .net pour Apache Spark.

## <a name="download-the-sample-data"></a>Télécharger les exemples de données

[GHTorrent](http://ghtorrent.org/) surveille tous les événements GitHub publics, tels que les informations sur les projets, les validations et les observateurs, et stocke les événements et leur structure dans les bases de données. Les données collectées sur différentes périodes sont disponibles sous forme d’archives téléchargeables. Étant donné que les fichiers de vidage sont très volumineux, ce guide utilise une [version tronquée du fichier dump](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) qui peut être téléchargée à partir de github.

> [!NOTE]
> Le jeu de données GHTorrent est distribué dans le cadre d’un système de gestion de licences double (Creative-licence[+](https://wiki.creativecommons.org/wiki/CCPlus)). Pour les utilisations non commerciales (y compris, mais sans s’y limiter, les utilisations éducatives, de recherche ou personnelles), le jeu de données est distribué dans le cadre de la [licence CC-by-sa](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Création d’une application console

1. À l’invite de commandes, exécutez les commandes suivantes pour créer une nouvelle application console :

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   La `dotnet` commande crée une `new` application de type `console` pour vous. Le `-o` paramètre crée un répertoire nommé *mySparkBatchApp* dans lequel votre application est stockée et le remplit avec les fichiers requis. La `cd mySparkBatchApp` commande remplace le répertoire par le répertoire d’application que vous venez de créer.

1. Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft. Spark. Dans votre console, exécutez la commande suivante :

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Créer un SparkSession

1. Ajoutez les instructions supplémentaires suivantes `using` au début du fichier *Program.cs* dans *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Ajoutez le code suivant à votre espace de noms de projet. *s_referenceData* est utilisé ultérieurement dans le programme pour filtrer en fonction de la date.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Ajoutez le code suivant à l’intérieur de votre méthode main pour établir un nouveau SparkSession. Le SparkSession est le point d’entrée de la programmation Spark avec l’API DataSet et tableau. En appelant l' `spark` objet, vous pouvez accéder aux fonctionnalités Spark et tableau dans votre programme.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Préparer les données

1. Lit le fichier d’entrée dans un `DataFrame` , qui est une collection de données distribuée organisée en colonnes nommées. Vous pouvez définir les colonnes de vos données par le biais de <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> . Utilisez la <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> méthode pour afficher les données dans votre tableau. Veillez à mettre à jour le chemin d’accès au fichier CSV vers l’emplacement des données GitHub que vous avez téléchargées.

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

1. Utilisez la <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> méthode pour supprimer des lignes avec des valeurs na (null) et la <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> méthode pour supprimer certaines colonnes de vos données. Cela permet d’éviter des erreurs si vous essayez d’analyser des données null ou des colonnes qui ne sont pas pertinentes pour votre analyse finale.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analyser les données

Spark SQL vous permet d’effectuer des appels SQL sur vos données. Il est courant de combiner des fonctions définies par l’utilisateur et Spark SQL pour appliquer une fonction définie par l’utilisateur à toutes les lignes de votre tableau.

Vous pouvez appeler spécifiquement `spark.Sql` pour imiter les appels SQL standard détectés dans d’autres types d’applications. Vous pouvez également appeler des méthodes telles que <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> et <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> pour combiner, filtrer et effectuer des calculs spécifiquement sur vos données.

L’objectif de cette application est d’obtenir des Insights sur les données des projets GitHub. Ajoutez les extraits de code suivants à votre programme pour analyser les données.

1. Ajouter le bloc de code suivant recherche le nombre de fois où chaque langue a été dupliquée. Tout d’abord, les données sont regroupées par langue. Ensuite, le nombre moyen de fourches de chaque langue est pris.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Ajoutez le bloc de code suivant pour trier le nombre moyen de fourches dans l’ordre décroissant afin de déterminer les langues les plus dupliquées. Autrement dit, le plus grand nombre de fourches s’affiche en premier.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. Le bloc de code suivant vous montre comment les projets récents ont été mis à jour. Vous inscrivez une nouvelle fonction définie par l’utilisateur appelée *MyUDF* et la Comparez avec une date, *s_referenceDate*, qui a été déclarée au début du didacticiel. La date de chaque projet est comparée à la date de référence. Spark SQL est ensuite utilisé pour appeler l’UDF sur chaque ligne des données pour analyser chaque projet dans le jeu de données.

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

1. Appelez `spark.Stop()` pour terminer le SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Utiliser Spark-submit pour exécuter votre application

1. Utilisez la commande suivante pour générer votre application .NET :

   ```dotnetcli
   dotnet build
   ```

1. Exécutez votre application avec `spark-submit` . Veillez à mettre à jour la commande suivante avec les chemins d’accès réels à votre fichier jar Microsoft Spark.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Obtenir le code

Vous pouvez voir la [solution complète](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) sur GitHub.

## <a name="next-steps"></a>Étapes suivantes

Passez à l’article suivant pour apprendre à traiter les données de streaming avec .NET pour Apache Spark.
> [!div class="nextstepaction"]
> [Didacticiel : diffusion en continu structurée avec .NET pour Apache Spark](streaming.md)
