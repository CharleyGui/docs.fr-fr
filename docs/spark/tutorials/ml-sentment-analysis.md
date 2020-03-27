---
title: Analyse de sentiment avec .NET pour Apache Spark et ML.NET tutoriel
description: Dans ce tutoriel, vous apprenez à utiliser ML.NET avec .NET pour Apache Spark pour l’analyse du sentiment.
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345340"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Tutorial: Analyse de sentiment avec .NET pour Apache Spark et ML.NET

Ce tutoriel vous apprend à faire l’analyse du sentiment des commentaires en ligne en utilisant ML.NET et .NET pour Apache Spark. [ML.NET](http://dot.net/ml) est un cadre d’apprentissage automatique libre, multiplateforme et open source. Vous pouvez utiliser ML.NET avec .NET pour Apache Spark pour mettre à l’échelle la formation et la prédiction des algorithmes d’apprentissage automatique.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créez un modèle d’analyse de sentiment à l’aide de ML.NET Model Builder dans Visual Studio.
> * Créez une application de console .NET pour Apache Spark.
> * Rédiger et implémenter une fonction définie par l’utilisateur.
> * Exécutez un .NET pour Apache Spark console app.

## <a name="prerequisites"></a>Prérequis

* Si vous n’avez pas développé un .NET pour Apache Spark application avant, commencez par le [tutoriel Getting Started](get-started.md) pour se familiariser avec les bases. Complétez toutes les conditions préalables pour le tutoriel Getting Started avant de continuer avec ce tutoriel.

* Ce tutoriel utilise le ML.NET Model Builder (preview), une interface visuelle disponible dans Visual Studio. Si vous n’avez pas déjà Visual Studio, vous pouvez [télécharger la version communautaire de Visual Studio](https://visualstudio.microsoft.com/downloads/) gratuitement.

* [Télécharger et installer](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (avant-première).

* Téléchargez les jeux de données [d’examen yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) et [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp.

## <a name="review-the-data"></a>Examiner les données

Le jeu de données Yelp avise les commentaires en ligne sur divers services. Ouvrez [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) et remarquez la structure des données. La première colonne contient du texte d’examen, et la deuxième colonne contient des scores de sentiment. Si le score de sentiment est 1, l’examen est positif, et si le score de sentiment est 0, l’examen est négatif.

Le tableau suivant contient des données d’exemple :

|ReviewText (en)|Sentiments|
|-|-|
|Wow... J’ai adoré cet endroit.|    1|
|La pâte n’est pas bonne.|    0|

## <a name="build-your-machine-learning-model"></a>Construisez votre modèle d’apprentissage automatique

1. Ouvrez Visual Studio et créez une nouvelle application console CMD (.NET Core). Nommez le projet *MLSparkModel*.

1. Dans **Solution Explorer**, cliquez à droite sur le projet *MLSparkModel.* Ensuite, sélectionnez **Ajouter > l’apprentissage automatique**.

1. Du ML.NET Model Builder, sélectionnez la tuile de scénario **d’analyse de sentiment.**

1. Sur la page **de données Add,** téléchargez l’ensemble de données *yelptrain.csv.*

1. Choisissez *Sentiment* parmi les **colonnes pour prédire** la baisse.

1. Sur la page **Train,** définissez le temps de vous entraîner jusqu’à *60 secondes* et sélectionnez **l’entraînement Démarrer.** Remarquez l’état de votre formation dans le cadre **de Progress**.

1. Une fois que Le constructeur modèle a terminé la formation, **évaluez** les résultats de la formation. Vous pouvez taper des phrases dans la boîte de texte ci-dessous **Essayez votre modèle** et **sélectionnez Prédire** pour voir la sortie.

1. Sélectionnez **code,** puis sélectionnez **Ajouter des projets** pour ajouter le modèle ML à la solution.

1. Notez que deux projets sont ajoutés à vos solutions : **MLSparkModelML.ConsoleApp** et **MLSparkModelML.Model**.

1. Double clic sur votre projet *MLSpark* C et remarquez que la référence de projet suivante a été ajoutée.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Créer une application console

Model Builder crée une application console pour vous.

1. Cliquez à droite sur **MLSparkModelML.Console** dans Solution Explorer, et **sélectionnez Manage NuGet Packages**.

1. Recherchez **Microsoft.Spark** et installez le paquet. **Microsoft.ML** est automatiquement installé pour vous par Model Builder.

### <a name="create-a-sparksession"></a>Créer une SparkSession

1. Ouvrez le fichier *Program.cs* pour **MLSparkModelML.ConsoleApp**. Ce fichier a été autogénéré par Model Builder. Supprimer `using` les relevés, le contenu de la `CreateSingleDataSample` méthode Main() et la région.

1. Ajoutez les `using` instructions supplémentaires suivantes au sommet de la *Program.cs*:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Changez `DATA_FILEPATH` le chemin de votre *yelptest.csv*.

1. Ajoutez le code `Main` suivant à votre `SparkSession`méthode pour créer un nouveau . La spark Session est le point d’entrée de la programmation Spark avec l’API Dataset et DataFrame.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   L’appel de l’objet *d’étincelle* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et DataFrame tout au long de votre programme.

### <a name="create-a-dataframe-and-print-to-console"></a>Créez un DataFrame et imprimez pour consoler

Lire dans les données d’examen Yelp du fichier *yelptest.csv* comme un `DataFrame`. Inclure `header` `inferSchema` et options. L’option `header` lit la première ligne de *yelptest.csv* comme noms de colonne au lieu de données. L’option `inferSchema` infère les types de colonnes basés sur les données.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Enregistrer une fonction définie par l’utilisateur

Vous pouvez utiliser des FUD, *des fonctions définies par l’utilisateur,* des applications Spark pour effectuer des calculs et des analyses sur vos données. Dans ce tutoriel, vous utilisez ML.NET avec un UDF pour évaluer chaque examen Yelp.

Ajoutez le code `Main` suivant à votre méthode `MLudf`pour enregistrer un UDF appelé .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Cet UDF prend une chaîne d’examen Yelp comme entrée, et les sorties vraies ou fausses pour les sentiments positifs ou négatifs, respectivement. Il utilise la méthode *de prédiction ()* que vous définissez dans une étape ultérieure.

### <a name="use-spark-sql-to-call-the-udf"></a>Utilisez Spark SQL pour appeler l’UDF

Maintenant que vous avez lu dans vos données et incorporé ML, utilisez Spark SQL pour appeler l’UDF qui exécutera l’analyse de sentiment sur chaque rangée de votre DataFrame. Ajoutez le code suivant à votre méthode `Main` :

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

### <a name="create-predict-method"></a>Créer une méthode de prévision()

Ajoutez le code `Main()` suivant avant votre méthode. Ce code est similaire à ce qui est produit par Model Builder dans *ConsumeModel.cs*. Le déplacement de cette méthode vers votre console charge le chargement du modèle chaque fois que vous exécutez votre application.

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

## <a name="add-the-model-to-your-console-app"></a>Ajoutez le modèle à votre application console

Dans Solution Explorer, copiez le fichier *MLModel.zip* du projet **MLSparkModelML.Model** et collez-le dans le projet **MLSparkModelML.ConsoleApp.** Une référence est automatiquement ajoutée dans *MLSparkModelML.ConsoleApp.csproj*.

## <a name="run-your-code"></a>Exécuter votre code

Utilisez `spark-submit` pour faire fonctionner votre code. Naviguez vers le dossier racine de votre application de console à l’aide de l’invite de commande et exécutez les commandes suivantes.

Tout d’abord, nettoyez et publiez votre application.

```dotnetcli
dotnet clean
dotnet publish
```

Ensuite, naviguez vers le dossier de publication `spark-submit` de l’application de la console et exécutez la commande suivante. N’oubliez pas de mettre à jour la commande avec le chemin réel de votre fichier de pot Microsoft Spark.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Obtenir le code

Ce tutoriel est similaire au code de [l’analyse du sentiment avec l’exemple Big Data.](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)

## <a name="next-steps"></a>Étapes suivantes

Avancez à l’article suivant pour apprendre à faire le streaming structuré avec .NET pour Apache Spark.
> [!div class="nextstepaction"]
> [Tutorial: Streaming structuré avec .NET pour Apache Spark](streaming.md)
