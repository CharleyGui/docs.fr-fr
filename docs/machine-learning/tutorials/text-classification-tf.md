---
title: 'Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model'
description: This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments. The binary sentiment classifier is a C# console application developed using Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 8c3544b60b1fba1d419ca091b0a1d85fbbdbe2d6
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204924"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET

This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments. The binary sentiment classifier is a C# console application developed using Visual Studio.

The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database. Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
>
> * Load a pre-trained TensorFlow model
> * Transform website comment text into features suitable for the model
> * Utiliser le modèle pour effectuer une prédiction

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

## <a name="prerequisites"></a>Configuration requise

* [Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.

## <a name="setup"></a>Installation

### <a name="create-the-application"></a>Créer l’application

1. Create a **.NET Core Console Application** called "TextClassificationTF".

2. Créez un répertoire nommé *Données* dans votre projet pour y enregistrer les fichiers du jeu de données.

3. Installez le **package NuGet Microsoft.ML** :

    Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**. Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button. Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi. Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Add the TensorFlow model to the project

> [!NOTE]
> The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo. The model is in TensorFlow SavedModel format.

1. Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.

    The zip file contains:

    * `saved_model.pb`: the TensorFlow model itself. The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.
    * `imdb_word_index.csv`: a mapping from individual words to an integer value. The mapping is used to generate the input features for the TensorFlow model.

2. Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory. Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![sentiment_model directory contents](./media/text-classification-tf/sentiment-model-files.png)

3. In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

### <a name="add-using-statements-and-global-variables"></a>Add using statements and global variables

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath` is the file path of the trained model.
    * `FeatureLength` is the length of the integer feature array that the model is expecting.

### <a name="model-the-data"></a>Model the data

Movie reviews are free form text. Your application converts the text into the input format expected by the model in a number of discrete stages.

The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding. The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.

|Property| valeur|Tapez|
|-------------|-----------------------|------|
|ReviewText|this film is really good|string|
|VariableLengthFeatures|14,22,9,66,78,... |int[]|

The variable length feature array is then resized to a fixed length of 600. This is the length that the TensorFlow model expects.

|Property| valeur|Tapez|
|-------------|-----------------------|------|
|ReviewText|this film is really good|string|
|VariableLengthFeatures|14,22,9,66,78,... |int[]|
|Fonctionnalités|14,22,9,66,78,... |int[600]|

1. Create a class for your input data, after the `Main` method:

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).

1. Create a class for the variable length features, after the `Main` method:

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.  All of the vector elements must be the same type. In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.

    This class is used in the `ResizeFeatures` action. The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.

1. Create a class for the fixed length features, after the `Main` method:

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    This class is used in the `ResizeFeatures` action. The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.

    Note that the name of the property `Features` is determined by the TensorFlow model. You cannot change this property name.

1. Create a class for the prediction after the `Main` method:

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle. `MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Create the MLContext, lookup dictionary, and action to resize features

La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET. L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

1. Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:

    |Word     |Index    |
    |---------|---------|
    |kids     |  362    |
    |want     |  181    |
    |wrong    |  355    |
    |effets  |  302    |
    |feeling  |  547    |

    Add the code below to create the lookup map:

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Load the pre-trained TensorFlow model

1. Add code to load the TensorFlow model:

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    Once the model is loaded, you can extract its input and output schema. The schemas are displayed for interest and learning only. You do not need this code for the final application to function:

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    The input schema is the fixed-length array of integer encoded words. The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive . These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.

## <a name="create-the-mlnet-pipeline"></a>Create the ML.NET pipeline

1. Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words. It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.

1. Map the words onto their integer encoding using the lookup table that you declared above:

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. Resize the variable length integer encodings to the fixed-length one required by the model:

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. Classify the input with the loaded TensorFlow model:

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    The TensorFlow model output is called `Prediction/Softmax`. Note that the name `Prediction/Softmax` is determined by the TensorFlow model. You cannot change this name.

1. Create a new column for the output prediction:

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`. The `/` character is not allowed in a C# property name.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Create the ML.NET model from the pipeline

1. Add the code to create the model from the pipeline:

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method. In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained. We supply an empty data view object to satisfy the requirements of the `Fit` method.

## <a name="use-the-model-to-make-a-prediction"></a>Utiliser le modèle pour effectuer une prédiction

1. Add the `PredictSentiment` method below the `Main` method:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe. It's acceptable to use in single-threaded or prototype environments. For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application. See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

1. Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `Predict()` en créant une instance de `MovieReview` :

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:

    |Property| valeur|Tapez|
    |-------------|-----------------------|------|
    |Prédiction|[0.5459937, 0.454006255]|float[]|

1. Display sentiment prediction using the following code:

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. Add a call to `PredictSentiment` at the end of the `Main` method:

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Résultats

Générez et exécutez votre application.

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Ces messages ont été supprimés des résultats suivants par souci de clarté.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Félicitations ! You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Load a pre-trained TensorFlow model
> * Transform website comment text into features suitable for the model
> * Utiliser le modèle pour effectuer une prédiction
