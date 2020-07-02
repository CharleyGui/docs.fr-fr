---
title: 'Didacticiel : analyser le sentiment de révision à l’aide d’un modèle TensorFlow'
description: Ce didacticiel vous montre comment utiliser un modèle TensorFlow pré-formé pour classer les sentiments dans les commentaires de sites Web. Le classifieur de sentiment binaire est une application console C# développée à l’aide de Visual Studio.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9c1e45f183bd5edc488e4f37bea648566d124c65
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803259"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Didacticiel : analyser le sentiment des revues de films à l’aide d’un modèle TensorFlow pré-formé dans ML.NET

Ce didacticiel vous montre comment utiliser un modèle TensorFlow pré-formé pour classer les sentiments dans les commentaires de sites Web. Le classifieur de sentiment binaire est une application console C# développée à l’aide de Visual Studio.

Le modèle TensorFlow utilisé dans ce didacticiel a été formé à l’aide des revues de films à partir de la base de données IMDB. Une fois que vous avez terminé de développer l’application, vous serez en mesure de fournir un texte d’examen de films et l’application vous indiquera si la révision a un sentiment positif ou négatif.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Charger un modèle TensorFlow pré-formé
> * Transformer le texte de commentaire de site Web en fonctionnalités adaptées au modèle
> * Utiliser le modèle pour effectuer une prédiction

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail « développement multiplateforme .net Core » installée.

## <a name="setup"></a>Programme d’installation

### <a name="create-the-application"></a>Création de l'application

1. Créez une **application console .net Core** appelée « TextClassificationTF ».

2. Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers de votre jeu de données.

3. Installez le **package NuGet Microsoft.ML** :

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, puis sélectionnez l’onglet **Parcourir** . recherchez **Microsoft.ml**, sélectionnez le package souhaité, puis cliquez sur le bouton **installer** . Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi. Répétez ces étapes pour **Microsoft. ml. TensorFlow**, **Microsoft. ml. SampleUtils** et **SciSharp. TensorFlow. Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Ajouter le modèle TensorFlow au projet

> [!NOTE]
> Le modèle de ce didacticiel provient de la GitHub référentiel [dotnet/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) . Le modèle est au format TensorFlow SavedModel.

1. Téléchargez le [fichier zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)et décompressez-le.

    Le fichier zip contient les éléments suivants :

    * `saved_model.pb`: le modèle TensorFlow lui-même. Le modèle prend un tableau d’entiers de longueur fixe (taille 600) de fonctionnalités représentant le texte dans une chaîne de révision IMDB et génère deux probabilités qui totalisent 1 : la probabilité que la revue d’entrée ait un sentiment positif et la probabilité que la révision d’entrée ait un sentiment négatif.
    * `imdb_word_index.csv`: mappage de mots individuels à une valeur entière. Le mappage est utilisé pour générer les fonctionnalités d’entrée pour le modèle TensorFlow.

2. Copiez le contenu du répertoire le plus profond `sentiment_model` dans le répertoire de votre projet *TextClassificationTF* `sentiment_model` . Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![contenu du répertoire sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. Dans Explorateur de solutions, cliquez avec le bouton droit sur chacun des fichiers dans le `sentiment_model` répertoire et sous-répertoire, puis sélectionnez **Propriétés**. Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.

### <a name="add-using-statements-and-global-variables"></a>Ajouter des instructions using et des variables globales

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : 

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Créez deux variables globales juste au-dessus de la `Main` méthode pour contenir le chemin d’accès au fichier de modèle enregistré et la longueur du vecteur de fonctionnalité.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`chemin d’accès du fichier du modèle formé.
    * `FeatureLength`longueur du tableau de fonctionnalités entières attendue par le modèle.

### <a name="model-the-data"></a>Modéliser les données

Les revues de film sont du texte en forme libre. Votre application convertit le texte dans le format d’entrée attendu par le modèle en plusieurs étapes discrètes.

La première consiste à fractionner le texte en mots séparés et à utiliser le fichier de mappage fourni pour mapper chaque mot sur un encodage entier. Le résultat de cette transformation est un tableau d’entiers de longueur variable dont la longueur correspond au nombre de mots de la phrase.

|Propriété| Valeur|Type|
|-------------|-----------------------|------|
|ReviewText|ce film est vraiment parfait|string|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|

Le tableau de fonctionnalités de longueur variable est ensuite redimensionné à une longueur fixe de 600. Il s’agit de la longueur attendue par le modèle TensorFlow.

|Propriété| Valeur|Type|
|-------------|-----------------------|------|
|ReviewText|ce film est vraiment parfait|string|
|VariableLengthFeatures|14, 22, 9, 66, 78,... |int []|
|Fonctionnalités|14, 22, 9, 66, 78,... |int [600]|

1. Créez une classe pour vos données d’entrée, après la `Main` méthode :

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    La classe de données d’entrée, `MovieReview` , a un `string` pour les commentaires de l’utilisateur ( `ReviewText` ).

1. Créez une classe pour les fonctionnalités de longueur variable, après la `Main` méthode :

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    La `VariableLengthFeatures` propriété a un attribut [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) pour le désigner comme vecteur.  Tous les éléments vectoriels doivent être du même type. Dans les jeux de données comportant un grand nombre de colonnes, le chargement de plusieurs colonnes en tant que vecteur unique réduit le nombre de passes de données lorsque vous appliquez des transformations de données.

    Cette classe est utilisée dans l' `ResizeFeatures` action. Les noms de ses propriétés (dans le cas présent, un seul) sont utilisés pour indiquer les colonnes du DataView qui peuvent être utilisées comme _entrée_ de l’action de mappage personnalisé.

1. Créez une classe pour les fonctionnalités de longueur fixe, après la `Main` méthode :

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Cette classe est utilisée dans l' `ResizeFeatures` action. Les noms de ses propriétés (dans le cas présent, un seul) sont utilisés pour indiquer les colonnes du DataView qui peuvent être utilisées comme _sortie_ de l’action de mappage personnalisé.

    Notez que le nom de la propriété `Features` est déterminé par le modèle TensorFlow. Vous ne pouvez pas modifier ce nom de propriété.

1. Créez une classe pour la prédiction après la `Main` méthode :

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle. `MovieReviewSentimentPrediction`a un `float` tableau unique ( `Prediction` ) et un `VectorType` attribut.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Créer le MLContext, le dictionnaire de recherche et l’action pour redimensionner les fonctionnalités

La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET. L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

1. Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Créez un dictionnaire pour encoder des mots sous forme d’entiers à l’aide de la [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) méthode pour charger des données de mappage à partir d’un fichier, comme indiqué dans le tableau suivant :

    |Word     |Index    |
    |---------|---------|
    |fête     |  362    |
    |vouloir     |  181    |
    |Flex    |  355    |
    |effects  |  302    |
    |sensation  |  547    |

    Ajoutez le code ci-dessous pour créer le mappage de recherche :

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. Ajoutez un `Action` pour redimensionner le tableau d’entiers de longueur variable en un tableau d’entiers de taille fixe, avec les lignes de code suivantes :

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Charger le modèle TensorFlow pré-formé

1. Ajoutez du code pour charger le modèle TensorFlow :

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Une fois le modèle chargé, vous pouvez extraire son schéma d’entrée et de sortie. Les schémas sont affichés pour l’intérêt et l’apprentissage uniquement. Vous n’avez pas besoin de ce code pour que l’application finale fonctionne :

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    Le schéma d’entrée est le tableau de longueur fixe des mots encodés entier. Le schéma de sortie est un tableau de probabilités de type float indiquant si le sentiment d’un avis est négatif ou positif. Ces valeurs sont additionnées à 1, car la probabilité d’être positive est le complément de la probabilité que le sentiment soit négatif.

## <a name="create-the-mlnet-pipeline"></a>Créer le pipeline ML.NET

1. Créez le pipeline et fractionnez le texte d’entrée en mots à l’aide de la transformation [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) pour scinder le texte en mots en tant que ligne de code suivante :

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   La transformation [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) utilise des espaces pour analyser le texte/la chaîne en mots. Elle crée une nouvelle colonne et fractionne chaque chaîne d’entrée en un vecteur de sous-chaînes en fonction du séparateur défini par l’utilisateur.

1. Mappez les mots sur leur encodage entier à l’aide de la table de recherche que vous avez déclarée ci-dessus :

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Redimensionnez les encodages d’entiers de longueur variable à la longueur fixe requise par le modèle :

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Classification de l’entrée avec le modèle TensorFlow chargé :

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    La sortie du modèle TensorFlow est appelée `Prediction/Softmax` . Notez que le nom `Prediction/Softmax` est déterminé par le modèle TensorFlow. Vous ne pouvez pas modifier ce nom.

1. Créez une nouvelle colonne pour la prédiction de sortie :

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    Vous devez copier la `Prediction/Softmax` colonne dans un nom qui peut être utilisé en tant que propriété dans une classe C# : `Prediction` . Le `/` caractère n’est pas autorisé dans un nom de propriété C#.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Créer le modèle ML.NET à partir du pipeline

1. Ajoutez le code pour créer le modèle à partir du pipeline :

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    Un modèle ML.NET est créé à partir de la chaîne d’estimateurs dans le pipeline en appelant la `Fit` méthode. Dans ce cas, nous n’ajustons aucune donnée pour créer le modèle, car le modèle TensorFlow a déjà été formé précédemment. Nous fournissons un objet de vue de données vide pour répondre aux exigences de la `Fit` méthode.

## <a name="use-the-model-to-make-a-prediction"></a>Utiliser le modèle pour effectuer une prédiction

1. Ajoutez la `PredictSentiment` méthode en dessous de la `Main` méthode :

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Ajoutez le code suivant pour créer le `PredictionEngine` en tant que première ligne de la `PredictSentiment()` méthode :

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas thread-safe. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application. Pour plus d’informations sur l' [utilisation `PredictionEnginePool` de dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application), consultez ce guide.

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

1. Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `Predict()` en créant une instance de `MovieReview` :

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. Transmettez les données de commentaire de test au `Prediction Engine` en ajoutant les lignes de code suivantes dans la `PredictSentiment()` méthode :

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. La fonction [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) effectue une prédiction sur une seule ligne de données :

    |Propriété| Valeur|Type|
    |-------------|-----------------------|------|
    |Prédiction|[0,5459937, 0,454006255]|float []|

1. Affichez le sentiment de prédiction à l’aide du code suivant :

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Ajoutez un appel à à `PredictSentiment` la fin de la `Main` méthode :

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Résultats

Créez et exécutez votre application.

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Ces messages ont été supprimés des résultats suivants par souci de clarté.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Félicitations ! Vous avez maintenant correctement créé un modèle de Machine Learning pour classer et prédire les sentiments de messages en réutilisant un modèle pré-formé `TensorFlow` dans ml.net.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Charger un modèle TensorFlow pré-formé
> * Transformer le texte de commentaire de site Web en fonctionnalités adaptées au modèle
> * Utiliser le modèle pour effectuer une prédiction
