---
title: 'Tutoriel : Prédire des prix à l’aide de la régression'
description: Ce tutoriel montre comment générer un modèle de régression avec ML.NET pour prédire des prix, plus précisément, des courses de taxi à New York.
author: jralexander
ms.author: johalex
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 40f70b6d89bf19ae0b20cb00d56e9f7dceb48f61
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377789"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>Tutoriel : Prédire des prix à l’aide de la régression avec ML.NET

Ce tutoriel montre comment créer un [modèle de régression](../resources/glossary.md#regression) avec ML.NET pour prédire des prix, plus précisément, des courses de taxi à New York.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Préparer et comprendre les données
> * Charger et transformer les données
> * Choisir un algorithme d’apprentissage
> * Effectuer l’apprentissage du modèle
> * Évaluer le modèle
> * Utiliser le modèle pour les prévisions

## <a name="prerequisites"></a>Prérequis

* [Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.

## <a name="create-a-console-application"></a>Créer une application console

1. Créez une **application console .NET Core** appelée « TaxiFarePrediction ».

1. Créez un répertoire nommé *Data* (Données) dans votre projet pour y stocker les fichiers du jeu de données et du modèle.

1. Installez le package NuGet **Microsoft.ML** :

    Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Gérer les packages NuGet**. Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package dans la liste, puis sélectionnez le bouton **Installer**. Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés. Faites de même pour le package NuGet **Microsoft.ML.FastTree**.

## <a name="prepare-and-understand-the-data"></a>Préparer et comprendre les données

1. Téléchargez les jeux de données [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) et [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv), puis enregistrez-les dans le dossier *Données* créé à l’étape précédente. Nous utilisons ces jeux de données pour le modèle Machine Learning et pour évaluer la précision du modèle. Ces jeux de données proviennent du [jeu de données NYC TLC Taxi Trip](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).

1. Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur chacun des fichiers \*.csv, puis sélectionnez **Propriétés**. Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.

1. Ouvrez le jeu de données **taxi-fare-train.csv** et examinez les en-têtes de colonne dans la première ligne. Examinons chacune des colonnes. Analysez les données et identifiez les colonnes qui sont des **fonctionnalités** et celle qui est **l’étiquette**.

`label` est la colonne à prédire. Les valeurs `Features` identifiées sont les entrées que vous fournissez au modèle pour prédire l’étiquette (`Label`).

Le jeu de données fourni contient les colonnes suivantes :

* **vendor_id :** l’ID du taxi est une fonctionnalité.
* **rate_code :** le type de tarif de la course de taxi est une fonctionnalité.
* **passenger_count :** le nombre de passagers embarqués est une fonctionnalité.
* **trip_time_in_secs :** durée totale de la course. Vous voulez prédire le prix de la course avant de l’effectuer. À ce stade vous ne connaissez pas la durée de la course. Par conséquent, la durée de la course n’est pas une fonctionnalité et vous devez exclure cette colonne du modèle.
* **trip_distance :** la distance de la course est une fonctionnalité.
* **payment_type :** le mode de paiement (espèces ou carte de crédit) est une fonctionnalité.
* **fare_amount :** le prix total payé pour la course est l’étiquette.

## <a name="create-data-classes"></a>Créer des classes de données

Créez des classes pour les données d’entrée et les prédictions :

1. Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.
1. Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *TaxiTrip.cs*. Ensuite, sélectionnez le bouton **Ajouter**.
1. Ajoutez les directives `using` suivantes au nouveau fichier :

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

Supprimez la définition de classe existante et ajoutez le code suivant, qui contient deux classes, `TaxiTrip` et `TaxiTripFarePrediction`, au fichier *TaxiTrip.cs* :

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` est la classe des données d’entrée et a des définitions pour chacune des colonnes du jeu de données. Utilisez l’attribut <xref:Microsoft.ML.Data.LoadColumnAttribute> pour spécifier les index des colonnes sources dans le jeu de données.

La classe `TaxiTripFarePrediction` représente les résultats prédits. Elle comporte un seul champ float, `FareAmount`, avec un attribut `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> appliqué. Dans le cas de la tâche de régression, la colonne **Score** contient les valeurs d’étiquette prédites.

> [!NOTE]
> Utilisez le type `float` pour représenter les valeurs à virgule flottante dans les classes de données d’entrée et de prédiction.

### <a name="define-data-and-model-paths"></a>Définir des chemins de données et de modèle

Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

Il faut créer trois champs qui contiendront les chemins des fichiers comportant des jeux de données et le fichier permettant d’enregistrer le modèle :

* `_trainDataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’apprentissage du modèle.
* `_testDataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’évaluation du modèle.
* `_modelPath` contient le chemin du fichier où le modèle formé est stocké.

Ajoutez le code suivant juste au-dessus de la méthode `Main` pour spécifier ces chemins et pour la variable `_textLoader` :

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

Toutes les opérations de ML.NET commencent dans la [classe MLContext](xref:Microsoft.ML.MLContext). L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle. Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.

### <a name="initialize-variables-in-main"></a>Initialiser les variables dans Principal

Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable `mlContext` :

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

Ajoutez le code suivant comme prochaine ligne dans la méthode `Main` afin d’appeler la méthode `Train` :

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

La méthode `Train()` exécute les tâches suivantes :

* Charge les données.
* Extrait et transforme les données.
* Effectue l’apprentissage du modèle.
* Retourne le modèle.

La méthode `Train` effectue l’apprentissage du modèle. Créez cette méthode juste en dessous de `Main`, en utilisant le code suivant :

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>Charger et transformer les données

ML.NET utilise la [classe IDataView](xref:Microsoft.ML.IDataView) comme un moyen flexible et efficace de décrire des données tabulaires au format numérique ou texte. `IDataView` peut charger des fichiers texte ou en temps réel (par exemple, une base de données SQL ou des fichiers journaux). Ajoutez le code suivant comme première ligne de la méthode `Train()` :

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

Comme vous voulez prédire le prix de la course de taxi, la colonne `FareAmount` est la valeur `Label` que vous devez prédire (la sortie du modèle). Pour cela, utilisez la classe de transformation `CopyColumnsEstimator` pour copier `FareAmount`, puis ajoutez le code suivant : 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

L’algorithme qui effectue l’apprentissage du modèle exige des fonctionnalités **numériques**. Il faut donc transformer les données catégoriques (`VendorId`, `RateCode` et `PaymentType`) en nombres (`VendorIdEncoded`, `RateCodeEncoded` et `PaymentTypeEncoded`). Pour cela, utilisez la classe de transformation [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer), qui assigne différentes valeurs de clé numérique aux différentes valeurs de chaque colonne, puis ajoutez le code suivant :

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

La dernière étape de préparation des données regroupe toutes les colonnes de fonctionnalités dans la colonne **Fonctionnalités** à l’aide de la classe de transformation `mlContext.Transforms.Concatenate`. Par défaut, un algorithme d’apprentissage traite uniquement les caractéristiques issues de la colonne **Features**. Ajoutez le code suivant :

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>Choisir un algorithme d’apprentissage

Ce problème consiste à prédire le prix d’une course de taxi à New York. À première vue, ce prix semble dépendre simplement de la distance parcourue. Mais les chauffeurs de taxi à New York appliquent différents tarifs selon des facteurs comme le nombre de passagers supplémentaires ou le paiement par carte de crédit plutôt que par espèces. Vous souhaitez prédire le prix, qui est une valeur réelle, en fonction des autres facteurs du jeu de données. Pour ce faire, choisissez une tâche de machine learning par [régression](../resources/glossary.md#regression).

Ajoutez la tâche de machine learning [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) aux définitions de transformation des données en ajoutant la ligne de code suivante dans `Train()` :

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>Effectuer l’apprentissage du modèle

Ajustez le modèle aux données d’entraînement `dataview` et retournez le modèle entraîné en ajoutant la ligne de code suivante à la méthode `Train()` :

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

La méthode [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.

Retournez le modèle entraîné avec la ligne suivante de code dans la méthode `Train()` :

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>Évaluer le modèle

Ensuite, évaluez les performances de votre modèle avec vos données de test à des fins d’assurance qualité et de validation. Créez la méthode `Evaluate()` juste après `Train()`, en utilisant le code suivant :

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

La méthode `Evaluate` exécute les tâches suivantes :

* Charge le jeu de données de test.
* Crée l’évaluateur de régression.
* Évalue le modèle et crée des métriques.
* Affiche les métriques.

Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `Train`, en utilisant le code suivant :

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

Chargez le jeu de données de test à l’aide de la méthode [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A). Évaluez le modèle avec ce jeu de données afin d’en contrôler la qualité, en ajoutant le code suivant à la méthode `Evaluate` :

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

Transformez ensuite les données `Test` en ajoutant le code suivant à `EvaluateModel()` :

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

La méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) établit des prédictions pour les lignes d’entrée du jeu de données de test.

La méthode `RegressionContext.Evaluate` calcule les métriques de qualité pour `PredictionModel` à l’aide du jeu de données spécifié. Elle retourne un objet <xref:Microsoft.ML.Data.RegressionMetrics> qui contient les métriques globales calculées par les évaluateurs de régression. 

Pour afficher ces informations afin d’évaluer la qualité du modèle, vous devez d’abord obtenir les métriques. Ajoutez le code suivant comme première ligne de la méthode `Evaluate` :

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

Une fois que vous avez le jeu de prédiction, la méthode [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) évalue le modèle (elle compare les valeurs prédites aux `Labels` réelles dans le jeu de données de test et retourne des métriques relatives aux performances du modèle).

Ajoutez le code suivant pour évaluer le modèle et produire les métriques d’évaluation :

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) est une autre métrique d’évaluation des modèles de régression. RSquared prend des valeurs entre 0 et 1. Plus sa valeur est proche de 1, plus le modèle est bon. Ajoutez le code suivant dans la méthode `Evaluate` pour afficher la valeur RSquared :

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) est une des métriques d’évaluation du modèle de régression. Plus sa valeur est faible, plus le modèle est bon. Ajoutez le code suivant dans la méthode `Evaluate` pour afficher la valeur RMS :

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>Utiliser le modèle pour les prévisions

Créez la méthode `TestSinglePrediction` juste après la méthode `Evaluate`, en utilisant le code suivant :

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

La méthode `TestSinglePrediction` exécute les tâches suivantes :

* Crée un commentaire unique de données de test.
* Prédit le prix de la course en fonction des données de test.
* Combine les données de test et les prédictions pour générer des rapports.
* Affiche les résultats prédits.

Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `Evaluate`, en utilisant le code suivant :

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

Utilisez `PredictionEngine` pour prédire le prix de la course en ajoutant le code suivant à `TestSinglePrediction()` :

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

La [classe PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API utile qui vous permet de passer une instance unique de données, puis d’établir une prédiction sur elle.

Ce tutoriel utilise une course test au sein de cette classe. Par la suite, vous pouvez ajouter d’autres scénarios à tester avec le modèle. Ajoutez une course pour tester la prédiction de coût du modèle formé dans la méthode `TestSinglePrediction()` en créant une instance de `TaxiTrip` :

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

Ensuite, prédisez le prix basé sur une instance unique des données d’une course de taxi et passez le résultat à `PredictionEngine` en ajoutant les lignes de code suivantes à la méthode `TestSinglePrediction()` :

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) établit une prédiction sur une instance unique de données.

Pour afficher le prix prédit de la course spécifiée, ajoutez le code suivant à la méthode `TestSinglePrediction` :

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

Exécutez le programme afin d’afficher le prix prédit de la course pour votre cas de test.

Félicitations ! Vous avez créé un modèle Machine Learning pour prédire le prix des courses de taxi, avez évalué sa précision et l’avez utilisé pour faire des prédictions. Vous trouverez le code source de ce tutoriel dans le dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction).

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous avez appris à :

> [!div class="checklist"]
> * Préparer et comprendre les données
> * Créer un pipeline d’apprentissage
> * Charger et transformer les données
> * Choisir un algorithme d’apprentissage
> * Effectuer l’apprentissage du modèle
> * Évaluer le modèle
> * Utiliser le modèle pour les prévisions

Passez au tutoriel suivant pour en savoir plus.

> [!div class="nextstepaction"]
> [Clustering Iris](iris-clustering.md)
