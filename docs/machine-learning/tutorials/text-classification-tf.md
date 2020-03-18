---
title: 'Tutorial: Analyser le sentiment d’examen à l’aide d’un modèle TensorFlow'
description: Ce tutoriel vous montre comment utiliser un modèle TensorFlow pré-formé pour classer le sentiment dans les commentaires du site Web. Le classificateur de sentiment binaire est une application de console Cmd développée à l’aide de Visual Studio.
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 688c5b83cef8f21eef8fa24521a85449a9cfbd48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241115"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a>Tutorial: Analyser le sentiment des critiques de films à l’aide d’un modèle TensorFlow pré-formé dans ML.NET

Ce tutoriel vous montre comment utiliser un modèle TensorFlow pré-formé pour classer le sentiment dans les commentaires du site Web. Le classificateur de sentiment binaire est une application de console Cmd développée à l’aide de Visual Studio.

Le modèle TensorFlow utilisé dans ce tutoriel a été formé à l’aide de critiques de films de la base de données IMDB. Une fois que vous avez terminé le développement de l’application, vous serez en mesure de fournir le texte d’examen de film et la demande vous dira si l’examen a un sentiment positif ou négatif.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> * Charger un modèle TensorFlow pré-formé
> * Transformer le texte de commentaire du site Web en fonctionnalités adaptées au modèle
> * Utiliser le modèle pour effectuer une prédiction

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

## <a name="prerequisites"></a>Conditions préalables requises

* [Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec le ".NET Core cross-platform development" charge de travail installé.

## <a name="setup"></a>Programme d’installation

### <a name="create-the-application"></a>Création de l'application

1. Créez une **application console de base .NET** appelée "TextClassificationTF".

2. Créez un répertoire nommé *Données* dans votre projet pour enregistrer vos fichiers de jeux de données.

3. Installez le **package NuGet Microsoft.ML** :

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez "nuget.org" comme source de paquet, puis sélectionnez **l’onglet Parcourir.** Rechercher **Microsoft.ML,** sélectionnez le paquet que vous voulez, puis sélectionnez le bouton **Installer.** Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi. Répétez ces étapes pour **Microsoft.ML.TensorFlow** et **SciSharp.TensorFlow.Redist**.

### <a name="add-the-tensorflow-model-to-the-project"></a>Ajouter le modèle TensorFlow au projet

> [!NOTE]
> Le modèle de ce tutoriel est de la [dotnet / machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo. Le modèle est en format TensorFlow SavedModel.

1. Téléchargez le [fichier zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)et décompressez.

    Le fichier zip contient :

    * `saved_model.pb`: le modèle TensorFlow lui-même. Le modèle prend une longueur fixe (taille 600) gamme de fonctionnalités représentant le texte dans une chaîne d’examen IMDB, et extraie deux probabilités qui s' résument à 1: la probabilité que l’examen des entrées a un sentiment positif, et la probabilité que l’examen des entrées a sentiment négatif.
    * `imdb_word_index.csv`: une cartographie des mots individuels à une valeur integer. La cartographie est utilisée pour générer les fonctionnalités d’entrée pour le modèle TensorFlow.

2. Copiez le contenu `sentiment_model` de l’annuaire le plus `sentiment_model` intime dans votre répertoire de projet *TextClassificationTF.* Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :

   ![contenu sentiment_model répertoire](./media/text-classification-tf/sentiment-model-files.png)

3. Dans Solution Explorer, cliquez à droite `sentiment_model` sur chacun des fichiers de l’annuaire et de la sous-direction et sélectionnez **propriétés**. Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.

### <a name="add-using-statements-and-global-variables"></a>Ajouter à l’aide d’énoncés et de variables globales

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : 

   [!code-csharp[AddUsings](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Créez deux variables globales juste au-dessus de la `Main` méthode pour maintenir la trajectoire de fichier du modèle enregistré, et la longueur du vecteur de fonctionnalité.

   [!code-csharp[DeclareGlobalVariables](../../../samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * `_modelPath`est le chemin de fichier du modèle formé.
    * `FeatureLength`est la longueur de la gamme de fonctionnalités integer que le modèle attend.

### <a name="model-the-data"></a>Modéliser les données

Les critiques de films sont du texte de forme libre. Votre application convertit le texte en format d’entrée attendu par le modèle dans un certain nombre d’étapes distinctes.

La première consiste à diviser le texte en mots distincts et à utiliser le fichier de cartographie fourni pour cartographier chaque mot sur un encodage integer. Le résultat de cette transformation est un tableau d’intégraire de longueur variable avec une longueur correspondant au nombre de mots dans la phrase.

|Propriété| Valeur|Type|
|-------------|-----------------------|------|
|ReviewText (en)|ce film est vraiment bon|string|
|VariableLengthFeatures|14,22,9,66,78,... |int[]|

Le tableau de fonction de longueur variable est ensuite resized à une longueur fixe de 600. C’est la longueur que le modèle TensorFlow attend.

|Propriété| Valeur|Type|
|-------------|-----------------------|------|
|ReviewText (en)|ce film est vraiment bon|string|
|VariableLengthFeatures|14,22,9,66,78,... |int[]|
|Fonctionnalités|14,22,9,66,78,... |int[600]|

1. Créez un cours pour vos `Main` données d’entrée, après la méthode :

    [!code-csharp[MovieReviewClass](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MovieReviewClass "Declare movie review type")]

    La classe de `MovieReview`données `string` d’entrée,`ReviewText`, a un pour les commentaires de l’utilisateur ( ).

1. Créez une classe pour les caractéristiques de longueur variable, après la `Main` méthode :

    [!code-csharp[VariableLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    La `VariableLengthFeatures` propriété a un attribut [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) pour le désigner comme vecteur.  Tous les éléments vectoriels doivent être du même type. Dans les ensembles de données avec un grand nombre de colonnes, le chargement de plusieurs colonnes comme un seul vecteur réduit le nombre de passes de données lorsque vous appliquez des transformations de données.

    Cette classe est `ResizeFeatures` utilisée dans l’action. Les noms de ses propriétés (dans ce cas seulement un) sont utilisés pour indiquer quelles colonnes dans le DataView peuvent être utilisés comme _entrée_ à l’action de cartographie personnalisée.

1. Créez une classe pour les fonctionnalités de longueur fixe, après la `Main` méthode :

    [!code-csharp[FixedLengthFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#FixedLengthFeatures)]

    Cette classe est `ResizeFeatures` utilisée dans l’action. Les noms de ses propriétés (dans ce cas seulement un) sont utilisés pour indiquer quelles colonnes dans le DataView peuvent être utilisés comme _la sortie_ de l’action de cartographie personnalisée.

    Notez que le `Features` nom de la propriété est déterminé par le modèle TensorFlow. Vous ne pouvez pas changer ce nom de propriété.

1. Créez une classe pour `Main` la prédiction après la méthode :

    [!code-csharp[Prediction](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Prediction "Declare prediction class")]

    `MovieReviewSentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle. `MovieReviewSentimentPrediction`a un `float` tableau`Prediction`unique `VectorType` ( ) et un attribut.

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a>Créez le MLContext, le dictionnaire de recherche et l’action pour resize features

La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET. L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

1. Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :

   [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateMLContext "Create the ML Context")]

1. Créez un dictionnaire pour coder les mots [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) comme des intégrants en utilisant la méthode pour charger les données cartographiques à partir d’un fichier, comme on le voit dans le tableau suivant :

    |Word     |Index    |
    |---------|---------|
    |Enfants     |  362    |
    |vouloir     |  181    |
    |erreur    |  355    |
    |effects  |  302    |
    |Sentiment  |  547    |

    Ajouter le code ci-dessous pour créer la carte de recherche:

    [!code-csharp[CreateLookupMap](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateLookupMap)]

1. Ajoutez `Action` un pour resize le tableau d’intégraire de mot de longueur variable à un tableau d’intégrant de taille fixe, avec les lignes suivantes de code :

   [!code-csharp[ResizeFeatures](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a>Chargez le modèle TensorFlow pré-formé

1. Ajouter du code pour charger le modèle TensorFlow :

    [!code-csharp[LoadTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#LoadTensorFlowModel)]

    Une fois que le modèle est chargé, vous pouvez extraire son schéma d’entrée et de sortie. Les schémas sont affichés pour l’intérêt et l’apprentissage seulement. Vous n’avez pas besoin de ce code pour que l’application finale fonctionne :

    [!code-csharp[GetModelSchema](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#GetModelSchema)]

    Le schéma d’entrée est le tableau fixe de mots codés en encodés. Le schéma de sortie est un éventail de probabilités flottantes indiquant si le sentiment d’un examen est négatif, ou positif . Ces valeurs s' résument à 1, car la probabilité d’être positive est le complément de la probabilité que le sentiment soit négatif.

## <a name="create-the-mlnet-pipeline"></a>Créer le pipeline ML.NET

1. Créez le pipeline et divisez le texte d’entrée en mots à l’aide [de TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformer pour briser le texte en mots comme la prochaine ligne de code:

   [!code-csharp[TokenizeIntoWords](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#TokenizeIntoWords)]

   Le [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transformer utilise des espaces pour analyser le texte / corde en mots. Il crée une nouvelle colonne et divise chaque chaîne d’entrée à un vecteur de sous-cordes en fonction du séparateur défini par l’utilisateur.

1. Carte des mots sur leur codage integer à l’aide de la table de recherche que vous avez déclaré ci-dessus:

    [!code-csharp[MapValue](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#MapValue)]

1. Redimensionner les encodages integer de longueur variable à celui de la longueur fixe requis par le modèle :

    [!code-csharp[CustomMapping](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CustomMapping)]

1. Classer l’entrée avec le modèle TensorFlow chargé :

    [!code-csharp[ScoreTensorFlowModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#ScoreTensorFlowModel)]

    La sortie du modèle TensorFlow est appelée `Prediction/Softmax`. Notez que `Prediction/Softmax` le nom est déterminé par le modèle TensorFlow. Vous ne pouvez pas changer ce nom.

1. Créez une nouvelle colonne pour la prévision de sortie :

    [!code-csharp[SnippetCopyColumns](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCopyColumns)]

    Vous devez copier `Prediction/Softmax` la colonne en une avec un nom qui peut `Prediction`être utilisé comme une propriété dans une classe C: . Le `/` personnage n’est pas autorisé dans un nom de propriété C.

## <a name="create-the-mlnet-model-from-the-pipeline"></a>Créer le modèle ML.NET à partir du pipeline

1. Ajoutez le code pour créer le modèle à partir du pipeline :

    [!code-csharp[SnippetCreateModel](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#SnippetCreateModel)]

    Un modèle ML.NET est créé à partir de la chaîne d’estimateurs dans le pipeline en appelant la `Fit` méthode. Dans ce cas, nous n’ajustons aucune donnée pour créer le modèle, car le modèle TensorFlow a déjà été formé. Nous fournissons un objet de vue `Fit` des données vide pour répondre aux exigences de la méthode.

## <a name="use-the-model-to-make-a-prediction"></a>Utiliser le modèle pour effectuer une prédiction

1. Ajouter `PredictSentiment` la méthode `Main` ci-dessous la méthode:

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. Ajoutez le code suivant `PredictionEngine` pour créer la `PredictSentiment()` première ligne de la méthode :

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreatePredictionEngine)]

    Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la `PredictionEnginePool` sécurité des fils [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans les environnements de production, utilisez le service, qui crée un des objets à utiliser dans toute votre application. Voir ce guide sur la façon [d’utiliser `PredictionEnginePool` dans un ASP.NET’API Web de base](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

1. Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `Predict()` en créant une instance de `MovieReview` :

    [!code-csharp[CreateTestData](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CreateTestData)]

1. Passez les données de `Prediction Engine` commentaire de test à la `PredictSentiment()` en ajoutant les lignes de code suivantes dans la méthode:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#Predict)]

1. La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) fait une prédiction sur une seule série de données :

    |Propriété| Valeur|Type|
    |-------------|-----------------------|------|
    |Prédiction|[0.5459937, 0.454006255]|flotteur[]|

1. Afficher la prédiction du sentiment à l’aide du code suivant :

    [!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#DisplayPredictions)]

1. Ajoutez un `PredictSentiment` appel à la `Main` fin de la méthode:

    [!code-csharp[CallPredictSentiment](~/samples/snippets/machine-learning/TextClassificationTF/csharp/Program.cs#CallPredictSentiment)]

## <a name="results"></a>Résultats

Créez et exécutez votre application.

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Ces messages ont été supprimés des résultats suivants par souci de clarté.

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

Félicitations ! Vous avez maintenant construit avec succès un modèle d’apprentissage automatique pour classer `TensorFlow` et prédire le sentiment des messages en réutilisant un modèle pré-formé dans ML.NET.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> * Charger un modèle TensorFlow pré-formé
> * Transformer le texte de commentaire du site Web en fonctionnalités adaptées au modèle
> * Utiliser le modèle pour effectuer une prédiction
