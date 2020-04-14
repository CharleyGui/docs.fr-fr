---
title: 'Tutorial: Analyser les commentaires du site Web - classification binaire'
description: Ce tutoriel vous montre comment créer une application console .NET Core qui classifie les sentiments analysés dans les commentaires des sites web et qui exécute l’action appropriée. Le classifieur de sentiments binaire utilise C# dans Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c6e13cfca93c54648b1a0423c5983013d3e2a1a0
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243295"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>Tutorial: Analyser le sentiment des commentaires sur le site Web avec la classification binaire en ML.NET

Ce tutoriel vous montre comment créer une application console .NET Core qui classifie les sentiments analysés dans les commentaires des sites web et qui exécute l’action appropriée. Le classifieur binaire de sentiments utilise C# dans Visual Studio 2017.

Dans ce tutoriel, vous allez apprendre à :
> [!div class="checklist"]
>
> - Création d’une application console
> - Préparer les données
> - Chargement des données
> - Générer et entraîner le modèle
> - Évaluer le modèle
> - Utiliser le modèle pour effectuer une prédiction
> - Afficher les résultats

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

## <a name="prerequisites"></a>Prérequis

- [Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail ".NET Core cross-platform development" installée

- [Jeu de données « UCI Sentiment Labeled Sentences »](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (fichier zip)

## <a name="create-a-console-application"></a>Création d’une application console

1. Créez une **application console .NET Core** appelée « SentimentAnalysis ».

2. Créez un répertoire nommé *Données* dans votre projet pour enregistrer vos fichiers de jeux de données.

3. Installez le **package NuGet Microsoft.ML** :

    Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**. Choisissez "nuget.org" comme source de paquet, puis sélectionnez **l’onglet Parcourir.** Rechercher **Microsoft.ML,** sélectionnez le paquet que vous voulez, puis sélectionnez le bouton **Installer.** Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi. Faites de même pour le forfait **Microsoft.ML.FastTree** NuGet.

## <a name="prepare-your-data"></a>Préparer vos données

> [!NOTE]
> Les jeux de données utilisés dans ce tutoriel proviennent de « From Group to Individual Labels using Deep Features » (Kotzias et. al., KDD 2015, et hébergé à l’UCI Machine Learning Repository - Dua, D. et Karra Taniskidou, E. (2017). Référentiel UCI Machine Learning [http://archive.ics.uci.edu/ml]. Irvine, Californie : Université de Californie, School of Information and Computer Science.

1. Téléchargez le [fichier zip du jeu de données UCI Sentiment Labeled Sentences](http://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), puis décompressez-le.

2. Copiez le fichier `yelp_labelled.txt` dans le répertoire *Données* que vous avez créé.

3. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier `yelp_labeled.txt` et sélectionnez **Propriétés**. Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.

### <a name="create-classes-and-define-paths"></a>Créer des classes et définir des chemins

1. Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : 

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. Ajoutez le code suivant à `Main` la ligne juste au-dessus de la méthode, pour créer un champ pour maintenir le chemin de fichier de jeu de données récemment téléchargé :

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. Créez ensuite des classes pour les données d’entrée et les prédictions. Ajoutez une nouvelle classe à votre projet :

    - Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.

    - Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*. Ensuite, sélectionnez le bouton **Ajouter**.

1. Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code. Ajoutez l'instruction suivante `using` en haut du fichier *SentimentData.cs* :

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. Supprimez la définition de classe existante et ajoutez le code suivant, qui contient deux classes, `SentimentData` et `SentimentPrediction`, au fichier *SentimentData.cs* :

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>Comment les données ont-elles été préparées ?

La classe du jeu de données d’entrée, `SentimentData`, a une valeur `string` pour les commentaires utilisateur (`SentimentText`) et une valeur `bool` (`Sentiment`) égale à 1 (sentiment positif) ou 0 (sentiment négatif). Les deux champs ont des attributs [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) associés, qui spécifient l’ordre du fichier de données de chaque champ.  Par ailleurs, la propriété `Sentiment` a un attribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) qui la désigne comme champ `Label`. L’exemple de fichier suivant ne possède pas de ligne d’en-tête :

|SentimentText                         |Sentiment (Label) |
|--------------------------------------|----------|
|La serveuse était un peu lente durant le service.|    0     |
|La pâte n’est pas bonne.                    |    0     |
|Wow... J’ai adoré cet endroit.              |    1     |
|Le service a été très rapide.              |    1     |

`SentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle. Elle hérite de `SentimentData` afin que l’entrée `SentimentText` puisse être affichée en même temps que la prédiction de sortie. La valeur booléenne `Prediction` est la valeur que le modèle prédit quand la nouvelle entrée `SentimentText` lui est fournie.

La classe de sortie `SentimentPrediction` contient deux autres propriétés calculées par le modèle : `Score`, le score brut calculé par le modèle, et `Probability`, le score étalonné à la probabilité que le texte ait un sentiment positif.

Pour ce tutoriel, la propriété la plus importante est `Prediction`.

## <a name="load-the-data"></a>Chargement des données

Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView). `IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte). Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.

La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET. L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

Vous préparez l’application et chargez ensuite les données :

1. Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. Ajoutez le code suivant comme prochaine ligne dans la méthode `Main()` :

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. Créez la méthode `LoadData()` juste après la méthode `Main()`, en utilisant le code suivant :

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    La méthode `LoadData()` exécute les tâches suivantes :

    - Charge les données.
    - Fractionne le jeu de données chargé en jeux de données d’apprentissage et de test.
    - Retourne les jeux de données d’apprentissage et de test fractionnés.

4. Ajoutez le code suivant comme première ligne de la méthode `LoadData()` :

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    La méthode [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et se lit dans le fichier. Elle prend les variables de chemin de données et retourne un `IDataView`.

### <a name="split-the-dataset-for-model-training-and-testing"></a>Fractionner le jeu de données pour l’apprentissage et le test du modèle

Quand vous préparez un modèle, vous utilisez une partie du jeu de données pour entraîner le modèle et une partie du jeu de données pour tester la précision du modèle.

1. Pour fractionner les données chargées dans les jeux de données nécessaires, ajoutez le code suivant sur la ligne suivant la méthode `LoadData()` :

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    Le code précédent utilise la méthode [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pour diviser le jeu de données <xref:Microsoft.ML.DataOperationsCatalog.TrainTestData> chargé en ensembles de données de train et d’essai et les retourner dans la classe. Spécifiez le pourcentage de données du jeu de test avec le paramètre `testFraction`. La valeur par défaut est 10 %, mais dans cet exemple, vous spécifiez 20 % pour évaluer davantage de données.

2. Retournez `splitDataView` à la fin de la méthode `LoadData()` :

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>Générer et entraîner le modèle

1. Ajoutez l’appel suivant à la méthode `BuildAndTrainModel` comme prochaine ligne de code dans la méthode `Main()` :

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    La méthode `BuildAndTrainModel()` exécute les tâches suivantes :

    - Extrait et transforme les données.
    - Effectue l’apprentissage du modèle.
    - Prédit les sentiments en fonction des données de test.
    - Retourne le modèle.

2. Créez la méthode `BuildAndTrainModel()` juste après la méthode `Main()`, en utilisant le code suivant :

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>Extraire et transformer les données

1. Appelez `FeaturizeText` sur la ligne de code suivante :

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    La méthode `FeaturizeText()` dans le code précédent convertit la colonne de texte (`SentimentText`) en une colonne `Features` de type clé numérique, qui est utilisée par l’algorithme de machine learning, et l’ajoute comme nouvelle colonne au jeu de données :

    |SentimentText                         |Sentiments |Fonctionnalités              |
    |--------------------------------------|----------|----------------------|
    |La serveuse était un peu lente durant le service.|    0     |[0.76, 0.65, 0.44, …] |
    |La pâte n’est pas bonne.                    |    0     |[0.98, 0.43, 0.54, …] |
    |Wow... J’ai adoré cet endroit.              |    1     |[0.35, 0.73, 0.46, …] |
    |Le service a été très rapide.              |    1     |[0.39, 0, 0.75, …]    |

### <a name="add-a-learning-algorithm"></a>Ajouter un algorithme d’apprentissage

Cette application utilise un algorithme de classification qui classe les éléments ou lignes de données. Elle classe les commentaires des sites web comme positifs ou négatifs. Vous devez donc utiliser la tâche de classification binaire.

Ajoutez la tâche de machine learning aux définitions de transformations des données en ajoutant la ligne de code suivante dans `BuildAndTrainModel()` :

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) est votre algorithme d’entraînement de classification. Il est ajouté à `estimator` et accepte les caractéristiques `SentimentText` (`Features`) ainsi que les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.

### <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Ajustez le modèle aux données `splitTrainSet` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

La méthode [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.

### <a name="return-the-model-trained-to-use-for-evaluation"></a>Retourner le modèle entraîné à utiliser pour l’évaluation

 Retournez le modèle à la fin de la méthode `BuildAndTrainModel()` :

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>Évaluer le modèle

Une fois que votre modèle est entraîné, vérifiez ses performances avec vos données de test.

1. Créez la méthode `Evaluate()` juste après `BuildAndTrainModel()`, en utilisant le code suivant :

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    La méthode `Evaluate()` exécute les tâches suivantes :

    - Charge le jeu de données de test.
    - Crée l’évaluateur BinaryClassification.
    - Évalue le modèle et crée des métriques.
    - Affiche les métriques.

2. Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main()`, juste sous l’appel à la méthode `BuildAndTrainModel()`, en utilisant le code suivant :

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. Transformez les données `splitTestSet` en ajoutant le code suivant à `Evaluate()` :

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour prédire plusieurs lignes d’entrée d’un jeu de données de test.

4. Évaluez le modèle en ajoutant la ligne de code suivante dans la méthode `Evaluate()` :

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

Une fois que vous avez le jeu de prédiction (`predictions`), la méthode [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) évalue le modèle : elle compare les valeurs prédites aux valeurs `Labels` réelles dans le jeu de données de test et retourne un objet [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) contenant les métriques relatives aux performances du modèle.

### <a name="displaying-the-metrics-for-model-validation"></a>Affichage des métriques pour la validation du modèle

Utilisez le code suivant pour afficher les métriques :

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- La métrique `Accuracy` donne la précision du modèle, qui correspond à la proportion de prédictions correctes dans le jeu de test.

- La métrique `AreaUnderRocCurve` indique le degré de confiance conféré aux résultats de la classification des classes positif/négatif. Vous voulez que la métrique `AreaUnderRocCurve` soit le plus proche possible de la valeur 1.

- La métrique `F1Score` donne le score F1 du modèle, qui mesure l’équilibre entre la [précision](../resources/glossary.md#precision) et le [rappel](../resources/glossary.md#recall).  Vous voulez que la métrique `F1Score` soit le plus proche possible de la valeur 1.

### <a name="predict-the-test-data-outcome"></a>Prédire les résultats des données de test

1. Créez la méthode `UseModelWithSingleItem()` juste après la méthode `Evaluate()`, en utilisant le code suivant :

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    La méthode `UseModelWithSingleItem()` exécute les tâches suivantes :

    - Crée un commentaire unique de données de test.
    - Prédit les sentiments en fonction des données de test.
    - Combine les données de test et les prédictions pour générer des rapports.
    - Affiche les résultats prédits.

2. Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main()`, juste sous l’appel à la méthode `Evaluate()`, en utilisant le code suivant :

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. Ajoutez le code suivant comme première ligne dans la méthode `UseModelWithSingleItem()` :

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données. [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil. Il est acceptable d’utiliser dans des environnements à thread unique ou prototype. Pour améliorer les performances et la `PredictionEnginePool` sécurité des fils [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans les environnements de production, utilisez le service, qui crée un des objets à utiliser dans toute votre application. Voir ce guide sur la façon [d’utiliser `PredictionEnginePool` dans un ASP.NET’API Web de base](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).

    > [!NOTE]
    > L’extension de service `PredictionEnginePool` est disponible en préversion.

4. Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `UseModelWithSingleItem()` en créant une instance de `SentimentData` :

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. Passez les données de [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) commentaire de test à la en `UseModelWithSingleItem()` ajoutant les lignes suivantes de code dans la méthode:

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) effectue une prédiction sur une seule ligne de données.

6. Affichez `SentimentText` et la prédiction de sentiment correspondante en utilisant le code suivant :

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>Utiliser le modèle pour la prédiction

### <a name="deploy-and-predict-batch-items"></a>Déployer et prédire des éléments par lots

1. Créez la méthode `UseModelWithBatchItems()` juste après la méthode `UseModelWithSingleItem()`, en utilisant le code suivant :

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    La méthode `UseModelWithBatchItems()` exécute les tâches suivantes :

    - Crée les données de test par lots.
    - Prédit les sentiments en fonction des données de test.
    - Combine les données de test et les prédictions pour générer des rapports.
    - Affiche les résultats prédits.

2. Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `UseModelWithSingleItem()`, en utilisant le code suivant :

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. Ajoutez des commentaires pour tester les prédictions du modèle formé dans la méthode `UseModelWithBatchItems()` :

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>Prédire le sentiment de commentaire

Utilisez le modèle pour prédire le sentiment de données de commentaire à l’aide de la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) :

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>Combiner et afficher les prédictions

Créez un en-tête des prédictions à l’aide du code suivant :

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

Comme `SentimentPrediction` est hérité de `SentimentData`, la méthode `Transform()` a rempli `SentimentText` avec les champs prédits. À mesure que le processus ML.NET progresse, chaque composant ajoute des colonnes, ce qui rend l’affichage des résultats plus facile :

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>Résultats

Vos résultats doivent être similaires à ce qui suit. Durant le processus, des messages sont affichés. Vous pouvez voir des avertissements ou des messages de traitement. Ils ont été supprimés des résultats ci-dessous par souci de clarté.

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

Félicitations ! Vous venez de créer un modèle d’apprentissage automatique pour la classification et la prédiction des sentiments de messages.

La création de modèles efficaces est un processus itératif. Celui-ci présente une qualité initiale médiocre, car le tutoriel utilise de petits jeux de données pour permettre un apprentissage rapide du modèle. Si vous n’êtes pas satisfait de la qualité du modèle, vous pouvez essayer de l’améliorer en fournissant des jeux de données de formation plus larges ou en choisissant différents algorithmes de formation avec différents [hyper-paramètres](../resources/glossary.md#hyperparameter) pour chaque algorithme.

Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :
> [!div class="checklist"]
>
> - Création d’une application console
> - Préparer les données
> - Chargement des données
> - Générer et entraîner le modèle
> - Évaluer le modèle
> - Utiliser le modèle pour effectuer une prédiction
> - Afficher les résultats

Passer au tutoriel suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Classification des problèmes](github-issue-classification.md)
