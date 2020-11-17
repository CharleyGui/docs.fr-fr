---
title: Analyse des sentiments avec .NET pour Apache Spark et didacticiel ML.NET
description: Dans ce didacticiel, vous allez apprendre à utiliser ML.NET avec .NET pour Apache Spark pour l’analyse des sentiments.
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 1c2c966a4ff50a9d2f6951e20d909c5c20c75bfb
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688239"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a>Didacticiel : analyse des sentiments avec .NET pour Apache Spark et ML.NET

Ce didacticiel vous apprend à effectuer une analyse des sentiments des analyses en ligne à l’aide de ML.NET et de .NET pour Apache Spark. [Ml.net](http://dot.net/ml) est un framework de machine learning Open source gratuit et multiplateforme. Vous pouvez utiliser ML.NET avec .NET pour Apache Spark pour mettre à l’échelle l’apprentissage et la prédiction des algorithmes de Machine Learning.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> * Créez un modèle d’analyse des sentiments à l’aide du générateur de modèles ML.NET dans Visual Studio.
> * Créez une application console .NET pour Apache Spark.
> * Écrivez et implémentez une fonction définie par l’utilisateur.
> * Exécutez une application console .NET pour Apache Spark.

## <a name="prerequisites"></a>Prérequis

* Si vous n’avez pas encore développé de .NET pour Apache Spark application, commencez par le [didacticiel prise en main](get-started.md) pour vous familiariser avec les principes de base. Avant de poursuivre ce didacticiel, complétez toutes les conditions préalables pour le didacticiel Prise en main.

* Ce didacticiel utilise le générateur de modèles ML.NET (version préliminaire), une interface visuelle disponible dans Visual Studio. Si vous ne disposez pas de Visual Studio, vous pouvez [Télécharger gratuitement la version Community de Visual Studio](https://visualstudio.microsoft.com/downloads/) .

* [Télécharger et installer](https://marketplace.visualstudio.com/items?itemName=MLNET.07) Générateur de modèles ML.NET (version préliminaire).

* Téléchargez les jeux de données [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) et [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp Review.

## <a name="review-the-data"></a>Examiner les données

Le jeu de données Yelp revues contient des révisions Yelp en ligne sur divers services. Ouvrez [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) et notez la structure des données. La première colonne contient le texte de révision, tandis que la deuxième colonne contient des scores de sentiment. Si le score de sentiment est 1, la révision est positive et si le score de sentiment est 0, la révision est négative.

Le tableau suivant contient des exemples de données :

|ReviewText|Sentiments|
|-|-|
|... J’ai aimé cet endroit.|    1|
|La pâte n’est pas bonne.|    0|

## <a name="build-your-machine-learning-model"></a>Générez votre modèle de Machine Learning

1. Ouvrez Visual Studio et créez une nouvelle application console C# (.NET Core). Nommez le projet *MLSparkModel*.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet *MLSparkModel* . Sélectionnez ensuite **ajouter > machine learning**.

1. Dans le générateur de modèles ML.NET, sélectionnez la vignette **analyse des sentiments** scénario.

1. Dans la page **Ajouter des données** , téléchargez le jeu de données de *yelptrain.csv* .

1. Choisissez *sentiments* dans la liste déroulante **colonnes à prédire** .

1. Sur la page **train** , définissez l’heure sur l’apprentissage sur *60 secondes* et sélectionnez **Démarrer l’apprentissage**. Notez l’état de votre formation en **cours**.

1. Une fois que le générateur de modèles a terminé la formation, **évaluez** les résultats de la formation. Vous pouvez taper des expressions dans la zone de texte ci-dessous **essayer votre modèle** et sélectionner **prédire** pour voir la sortie.

1. Sélectionnez **code** , puis sélectionnez **Ajouter des projets** pour ajouter le modèle ml à la solution.

1. Notez que deux projets sont ajoutés à vos solutions : **MLSparkModelML. ConsoleApp** et **MLSparkModelML. Model**.

1. Double-cliquez sur votre projet C# *MLSpark* et notez que la référence de projet suivante a été ajoutée.

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a>Créer une application console

Le générateur de modèles crée une application console pour vous.

1. Cliquez avec le bouton droit sur **MLSparkModelML. console** dans Explorateur de solutions, puis sélectionnez **gérer les packages NuGet**.

1. Recherchez **Microsoft. Spark** et installez le package. **Microsoft.ml** est automatiquement installé pour vous par le générateur de modèles.

### <a name="create-a-sparksession"></a>Créer un SparkSession

1. Ouvrez le fichier *Program.cs* pour **MLSparkModelML. ConsoleApp**. Ce fichier a été généré automatiquement par le générateur de modèles. Supprimez les `using` instructions, le contenu de la méthode main () et la `CreateSingleDataSample` région.

1. Ajoutez les instructions supplémentaires suivantes `using` en haut de *Program.cs*:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. Remplacez `DATA_FILEPATH` par le chemin d’accès de votre *yelptest.csv*.

1. Ajoutez le code suivant à votre `Main` méthode pour créer un nouveau `SparkSession` . La session Spark est le point d’entrée de la programmation Spark avec l’API DataSet et tableau.

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   L’appel de l’objet *Spark* créé ci-dessus vous permet d’accéder aux fonctionnalités Spark et tableau dans votre programme.

### <a name="create-a-dataframe-and-print-to-console"></a>Créer un tableau et l’imprimer sur la console

Lisez les données de l'yelptest.csvexaminez le fichier *yelptest.csv* en tant que `DataFrame` . Inclut `header` les `inferSchema` options et. L' `header` option lit la première ligne de *yelptest.csv* en tant que noms de colonne au lieu de données. L' `inferSchema` option déduit les types de colonne en fonction des données.

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a>Inscrire une fonction définie par l’utilisateur

Vous pouvez utiliser des *fonctions définies par l’utilisateur*(UDF) dans des applications Spark pour effectuer des calculs et des analyses sur vos données. Dans ce didacticiel, vous allez utiliser ML.NET avec une fonction définie par l’usage (UDF) pour évaluer chaque Yelp.

Ajoutez le code suivant à votre `Main` méthode pour inscrire une fonction UDF appelée `MLudf` .

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

Cette fonction UDF prend une chaîne de révision Yelp comme entrée et génère la valeur true ou false pour les sentiments positifs ou négatifs, respectivement. Elle utilise la méthode *Predict ()* que vous définissez dans une étape ultérieure.

### <a name="use-spark-sql-to-call-the-udf"></a>Utiliser Spark SQL pour appeler la fonction définie par l’usage

Maintenant que vous avez lu vos données et incorporé ML, utilisez Spark SQL pour appeler l’UDF qui exécutera l’analyse des sentiments sur chaque ligne de votre tableau. Ajoutez le code suivant à votre méthode `Main` :

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

### <a name="create-predict-method"></a>Créer une méthode Predict ()

Ajoutez le code suivant avant votre `Main()` méthode. Ce code est similaire à ce qui est produit par le générateur de modèles dans *ConsumeModel.cs*. Le déplacement de cette méthode sur votre console charge le chargement du modèle chaque fois que vous exécutez votre application.

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

## <a name="add-the-model-to-your-console-app"></a>Ajouter le modèle à votre application console

Dans Explorateur de solutions, copiez le fichier *MLModel.zip* à partir du projet **MLSparkModelML. Model** et collez-le dans le projet **MLSparkModelML. ConsoleApp** . Une référence est automatiquement ajoutée dans *MLSparkModelML. ConsoleApp. csproj*.

## <a name="run-your-code"></a>Exécuter votre code

Utilisez `spark-submit` pour exécuter votre code. Accédez au dossier racine de votre application console à l’aide de l’invite de commandes et exécutez les commandes suivantes.

Tout d’abord, nettoyez et publiez votre application.

```dotnetcli
dotnet clean
dotnet publish
```

Accédez ensuite au dossier Publish de l’application console et exécutez la `spark-submit` commande suivante. N’oubliez pas de mettre à jour la commande avec le chemin d’accès réel de votre fichier jar Microsoft Spark.

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2-4_2.11-1.0.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a>Obtenir le code

Ce didacticiel est similaire au code de l’exemple de [analyse des sentiments avec des données Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) .

## <a name="next-steps"></a>Étapes suivantes

Passez à l’article suivant pour découvrir comment procéder à la diffusion en continu structurée avec .NET pour Apache Spark.
> [!div class="nextstepaction"]
> [Didacticiel : diffusion en continu structurée avec .NET pour Apache Spark](streaming.md)
