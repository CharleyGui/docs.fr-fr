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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>Tutorial: Faire le traitement par lots avec .NET pour Apache Spark

Dans ce tutoriel, vous apprenez à faire le traitement par lots en utilisant .NET pour Apache Spark. Le traitement par lots est la transformation des données au repos, ce qui signifie que les données sources ont déjà été chargées dans le stockage de données.

Le traitement par lots est généralement effectué sur de grands ensembles de données plats qui doivent être préparés pour une analyse plus approfondie. Le traitement des journaux et l’entreposage des données sont des scénarios de traitement de lots courants. Dans ce scénario, vous analysez des informations sur les projets GitHub, telles que le nombre de temps que différents projets ont été mis en fourche ou la rapidité avec laquelle les projets ont été mis à jour récemment.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créez et exécutez une application .NET pour Apache Spark
> * Lire les données dans un DataFrame et les préparer à l’analyse
> * Traiter les données à l’aide de Spark SQL

## <a name="prerequisites"></a>Conditions préalables requises

Si c’est votre première fois en utilisant .NET pour Apache Spark, consultez le [Get a commencé avec .NET pour Apache Spark](../tutorials/get-started.md) tutoriel pour apprendre à préparer votre environnement et exécuter votre premier .NET pour Apache Spark application.

## <a name="download-the-sample-data"></a>Télécharger les exemples de données

[GHTorrent](http://ghtorrent.org/) surveille tous les événements publics GitHub, tels que des informations sur les projets, les commits et les observateurs, et stocke les événements et leur structure dans les bases de données. Les données recueillies sur différentes périodes de temps sont disponibles sous forme d’archives téléchargeables. Parce que les fichiers de décharge sont très volumineux, ce guide utilise une [version tronquée du fichier de décharge](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) qui peut être téléchargé à partir de GitHub.

> [!NOTE]
> Le jeu de données GHTorrent est distribué dans le cadre d’un système de double licence[(Creative Commons (](https://wiki.creativecommons.org/wiki/CCPlus)). Pour les utilisations non commerciales (y compris, mais sans s’y limiter, l’éducation, la recherche ou les usages personnels), l’ensemble de données est distribué sous la [licence CC-BY-SA](https://creativecommons.org/licenses/by-sa/4.0/).

## <a name="create-a-console-application"></a>Création d’une application console

1. Dans votre application rapide, exécutez les commandes suivantes pour créer une nouvelle application de console :

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   La `dotnet` commande `new` crée une `console` application de type pour vous. Le `-o` paramètre crée un répertoire nommé *mySparkBatchApp* où votre application est stockée et le remplit avec les fichiers requis. La `cd mySparkBatchApp` commande modifie l’annuaire de l’annuaire de l’application que vous venez de créer.

1. Pour utiliser .NET pour Apache Spark dans une application, installez le package Microsoft.Spark. Dans votre console, exécutez la commande suivante :

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>Créer une SparkSession

1. Ajoutez les `using` instructions supplémentaires suivantes au haut du fichier *Program.cs* dans *mySparkBatchApp*.

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. Ajoutez le code suivant à votre espace nom de projet. *s_referenceData* est utilisé plus tard dans le programme pour filtrer en fonction de la date.

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. Ajoutez le code suivant à l’intérieur de votre méthode Principale pour établir une nouvelle SparkSession. Le SparkSession est le point d’entrée de la programmation Spark avec l’API Dataset et DataFrame. En appelant `spark` l’objet, vous pouvez accéder aux fonctionnalités Spark et DataFrame tout au long de votre programme.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>Préparer les données

1. Lisez le fichier `DataFrame`d’entrée dans un , qui est une collection distribuée de données organisées en colonnes nommées. Vous pouvez définir les colonnes pour vos données à travers <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>. Utilisez <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> la méthode pour afficher les données dans votre DataFrame. Assurez-vous de mettre à jour le chemin de fichier CSV à l’emplacement des données GitHub que vous avez téléchargées.

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

1. Utilisez <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> la méthode pour laisser tomber les lignes <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> avec des valeurs NA (null), et la méthode pour supprimer certaines colonnes de vos données. Cela permet de prévenir les erreurs si vous essayez d’analyser des données nulles ou des colonnes qui ne sont pas pertinentes à votre analyse finale.

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>Analyser les données

Spark SQL vous permet de faire des appels SQL sur vos données. Il est courant de combiner des fonctions définies par l’utilisateur et Spark SQL pour appliquer une fonction définie par l’utilisateur à toutes les lignes de votre DataFrame.

Vous pouvez `spark.Sql` appeler spécifiquement pour imiter les appels SQL standard vus dans d’autres types d’applications. Vous pouvez également <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> appeler <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> des méthodes comme et combiner spécifiquement, filtrer et effectuer des calculs sur vos données.

Le but de cette application est d’obtenir quelques informations sur les données des projets GitHub. Ajoutez les extraits de code suivants à votre programme pour analyser les données.

1. Ajouter le bloc de code suivant trouve le nombre de fois que chaque langue a été fourchée. Tout d’abord, les données sont regroupées par langue. Ensuite, le nombre moyen de fourchettes de chaque langue est pris.

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. Ajoutez le bloc de code suivant pour commander le nombre moyen de fourchettes dans l’ordre décroissant pour voir quelles langues sont les plus fourchées. Autrement dit, le plus grand nombre de fourchettes apparaîtra en premier.

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. Le prochain bloc de code vous montre la rapidité avec laquelle les projets ont été mis à jour. Vous enregistrez une nouvelle fonction définie par l’utilisateur appelée *MyUDF* et la comparez à une date, *s_referenceDate*, qui a été déclarée au début du tutoriel. La date de chaque projet est comparée à la date de référence. Ensuite, Spark SQL est utilisé pour appeler l’UDF sur chaque rangée des données pour analyser chaque projet dans l’ensemble de données.

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

1. Appelez `spark.Stop()` pour mettre fin à la SparkSession.

## <a name="use-spark-submit-to-run-your-app"></a>Utilisez spark-submit pour exécuter votre application

1. Utilisez la commande suivante pour créer votre application .NET :

   ```dotnetcli
   dotnet build
   ```

1. Exécutez votre `spark-submit`application avec . Assurez-vous de mettre à jour la commande suivante avec les chemins réels de votre fichier de pot Microsoft Spark.

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>Obtenir le code

Vous pouvez voir la [solution complète](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) sur GitHub.

## <a name="next-steps"></a>Étapes suivantes

Avancez à l’article suivant pour apprendre à traiter les données de streaming avec .NET pour Apache Spark.
> [!div class="nextstepaction"]
> [Tutorial: Streaming structuré avec .NET pour Apache Spark](streaming.md)
