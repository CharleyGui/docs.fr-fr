---
title: 'Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model'
description: Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model. The TensorFlow model was trained to classify images into a thousand categories. The ML.NET model makes use of transfer learning to classify images into fewer broader categories.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: 952ce5c52bcd09b8c4e4e40d5ddf85835a26478d
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204985"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a>Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model

Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.

The TensorFlow model was trained to classify images into a thousand categories. The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.

Pour entraîner un modèle de [Classification d’images](https://en.wikipedia.org/wiki/Outline_of_object_recognition) à partir de zéro, il faut définir des millions de paramètres, disposer d’une multitude de données d’apprentissage étiquetées et posséder une grande quantité de ressources de calcul (des centaines d’heures GPU). S’il n’est pas aussi efficace que l’apprentissage d’un modèle personnalisé à partir de zéro, l’apprentissage par transfert permet de raccourcir ce processus : il s’agit de travailler avec des milliers (et non des millions) d’images étiquetées et de créer assez vite un modèle personnalisé (en une heure sur un ordinateur sans GPU). This tutorial scales that process down even further, using only a dozen training images.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Incorporate the pre-trained TensorFlow model into the ML.NET pipeline
> * Train and evaluate the ML.NET model
> * Classify a test image

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF). Notez que, par défaut, la configuration de projet .NET pour ce tutoriel cible .NET Core 2.2.

## <a name="what-is-transfer-learning"></a>Qu’est-ce que l’apprentissage par transfert ?

Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.

For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.

## <a name="prerequisites"></a>Configuration requise

* [Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.
* [Le fichier .zip du répertoire de ressources du tutoriel](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)
* [Le modèle Machine Learning InceptionV1](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a>Select the right machine learning task

### <a name="deep-learning"></a>Deep Learning

Le [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) est un sous-ensemble du Machine Learning, qui révolutionne des domaines comme la Vision par ordinateur et la Reconnaissance vocale.

L’entraînement des modèles Deep Learning s’effectue à l’aide de grands ensembles de [données étiquetées](https://en.wikipedia.org/wiki/Labeled_data) et de [réseaux neuronaux](https://en.wikipedia.org/wiki/Artificial_neural_network) comportant plusieurs couches d’apprentissage. Le Deep Learning présente différentes caractéristiques :

* Il fonctionne mieux sur certaines tâches comme la Vision par ordinateur.
* Requires huge amounts of training data.

Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:

* détecter ou non la présence d’un visage dans une image ;
* Detecting cats vs. dogs.

 Or as in the following images, determining if an image is a(n)  food, toy, or appliance:

![image de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![image de nounours](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![image de grille-pain](./media/image-classification/193px-Broodrooster.jpg)

>[!Note]
> Les images précédentes appartiennent à Wikimedia Commons et sont attribuées ainsi :
>
> * « 220px-Pepperoni_pizza.jpg », domaine public, https://commons.wikimedia.org/w/index.php?curid=79505 ;
> * « 119px-Nalle_-_a_small_brown_teddy_bear.jpg », de [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) (photographie personnelle), CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166 ;
> * « 193px Broodrooster.jpg », de [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) (travail personnel), CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.

The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories. Entrez la partie `transfer` de `transfer learning`. Vous pouvez transposer la capacité de `Inception model` à identifier et à classer des images aux nouvelles catégories, en nombre limité, de votre classifieur d’images personnalisé.

* Aliment
* Jouet
* Appareil

This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset. The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.

Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification. We can make use of these internal image features in the model to train a new model with far fewer classes.

Comme le montre le diagramme suivant, vous ajoutez une référence aux packages NuGet ML.NET dans vos applications .NET Core ou .NET Framework. Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.

![Diagramme ML.NET de transformation TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a>Classification multiclasse

After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).

The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).

The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.

### <a name="data"></a>Données

Il y a deux sources de données : le fichier `.tsv` et les fichiers image.  Le fichier `tags.tsv` comporte deux colonnes : la première est définie comme `ImagePath` et la deuxième est le `Label` correspondant à l’image. L’exemple de fichier suivant ne possède pas de ligne d’en-tête :

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

Les images d’apprentissage et de test se trouvent dans les dossiers de ressources que vous allez télécharger dans un fichier zip. Elles appartiennent à Wikimedia Commons.
> *[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), le dépôt de fichiers multimédias sous licence libre.* Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear

## <a name="setup"></a>Installation

### <a name="create-a-project"></a>Créer un projet

1. Créer une **application console .NET Core** appelée « TransferLearningTF ».

1. Installez le **package NuGet Microsoft.ML** :

    * Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.
    * Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.
    * Click on the **Version** drop-down, select the **1.4.0** package in the list, and select the **Install** button.
    * Select the **OK** button on the **Preview Changes** dialog.
    * Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.
    * Repeat these steps for **Microsoft.ML.ImageAnalytics v1.4.0**, **SciSharp.TensorFlow.Redist v1.15.0** and **Microsoft.ML.TensorFlow v1.4.0**.

### <a name="download-assets"></a>Download assets

1. Téléchargez le [fichier zip du répertoire de ressources du projet ](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) et décompressez-le.

1. Copiez le répertoire `assets` dans votre répertoire de projet *TransferLearningTF*. Ce répertoire et ses sous-répertoires contiennent les fichiers de données et d’aide nécessaires à ce tutoriel (sauf pour le modèle Inception, que vous allez télécharger et ajouter à l’étape suivante).

1. Téléchargez le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) et décompressez-le.

1. Copiez le contenu décompressé du répertoire `inception5h` dans le répertoire `assets/inception` de votre projet *TransferLearningTF*. Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![Contenu du répertoire Inception](./media/image-classification/inception-files.png)

1. Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. Add the following code to the line right above the `Main` method to specify the asset paths:

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. Create classes for your input data, and predictions.

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    `ImageData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :

    * `ImagePath` contient le nom du fichier image.
    * `Label` contient la valeur de l’étiquette d’image.

1. Ajoutez une nouvelle classe à votre projet pour `ImagePrediction` :

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    `ImagePrediction` est la classe de prédiction des images, qui comprend les champs suivants :

    * `Score` contient le pourcentage de confiance d’une classification d’image donnée.
    * `PredictedLabelValue` contient la valeur de l’étiquette de classification d’image prédite.

    `ImagePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé. Elle comporte une `string` (`ImagePath`) correspondant au chemin de l’image. The `Label` is used to reuse and train the model. L’attribut `PredictedLabelValue` est utilisé pendant la prédiction et l’évaluation. L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

1. Initialiser la variable `mlContext` avec une nouvelle instance de `MLContext`.  Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="create-a-struct-for-inception-model-parameters"></a>Create a struct for Inception model parameters

1. The Inception model has several parameters you need to pass in. Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a>Créer une méthode d’utilitaire d’affichage

Étant donné que vous allez afficher les données d’image et les prédictions associées plusieurs fois, créez une méthode d’utilitaire d’affichage qui gère l’affichage des données d’image et des résultats de prédiction.

1. Créez la méthode `DisplayResults()` juste après le struct `InceptionSettings` avec le code suivant :

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. Fill in the body of the `DisplayResults` method:

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a>Créez une méthode d’utilitaire de fichier .tsv

1. Créez la méthode `ReadFromTsv()` juste après la méthode `DisplayResults()`, en utilisant le code suivant :

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. Fill in the body of the `ReadFromTsv` method:

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.

### <a name="create-a-method-to-make-a-prediction"></a>Create a method to make a prediction

1. Créez la méthode `ClassifySingleImage()` juste avant la méthode `DisplayResults()`, en utilisant le code suivant :

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`. Ajoutez le code suivant à la fin de la méthode `ClassifySingleImage()` :

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method. The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe. It's acceptable to use in single-threaded or prototype environments. For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application. See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

1. Affichez le résultat de la prédiction à la fin de la méthode `ClassifySingleImage()` :

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a>Construct the ML.NET model pipeline

An ML.NET model pipeline is a chain of estimators. Note that no execution happens during pipeline construction. The estimator objects are created but not executed.

1. Add a method to generate the model

    This method is the heart of the tutorial. It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model. It also evaluates the model against some previously unseen test data.

    Créez la méthode `GenerateModel()`, juste après le struct `InceptionSettings` et juste avant la méthode `DisplayResults()`, avec le code suivant :

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. Add the estimators to load, resize and extract the pixels from the image data:

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    The image data needs to be processed into the format that the TensorFlow model expects. In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.

1. Add the estimator to load the TensorFlow model, and score it:

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network. Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**. When using the model in its entirety, scoring makes an inference, or prediction.

    In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference. The output of the penultimate layer is labeled `softmax_2_preactivation`. The output of this layer is effectively a vector of features that characterize the original input images.

    This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.

1. Add the estimator to map the string labels in the training data to integer key values:

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings. A key is a number that has a one to one mapping to a string value.

1. Add the ML.NET training algorithm:

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. Add the estimator to map the predicted key value back into a string:

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

1. Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper. Ajoutez le code suivant comme première ligne de la méthode `GenerateModel()` :

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

1. Train the model with the data loaded above:

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    The `Fit()` method trains your model by applying the training dataset to the pipeline.

## <a name="evaluate-the-accuracy-of-the-model"></a>Evaluate the accuracy of the model

1. Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    There are a few sample images that you can use to evaluate the model. Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.

1. Add the following code to the `GenerateModel()` method to evaluate the model:

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    Une fois la prédiction définie, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :

    * Assesses the model (compares the predicted values with the test dataset `labels`).
    * Retourne les indicateurs de performances du modèle.

1. Display the model accuracy metrics

    Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    Les indicateurs suivants sont évalués pour la classification d’images :

    * `Log-loss` (voir [Perte logarithmique](../resources/glossary.md#log-loss)). Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.
    * `Per class Log-loss`., La perte logarithmique doit être aussi proche de zéro que possible.

1. Ajoutez le code suivant pour retourner le modèle entraîné à la ligne suivante :

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a>Run the application!

1. Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. Run your console app (Ctrl + F5). Vous devriez obtenir les résultats suivants.  Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

Félicitations ! You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Comprendre le problème
> * Incorporate the pre-trained TensorFlow model into the ML.NET pipeline
> * Train and evaluate the ML.NET model
> * Classify a test image

Consultez le référentiel GitHub d’exemples Machine Learning pour voir un exemple développé de classification d’images.
> [!div class="nextstepaction"]
> [Référentiel GitHub dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/)
