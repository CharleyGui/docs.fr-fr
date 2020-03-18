---
title: Guide pratique pour utiliser l’API de ML automatisé ML.NET
description: L’API de ML automatisé ML.NET automatise le processus de génération de modèle prêt pour le déploiement. Découvrez les options que vous pouvez utiliser pour configurer des tâches de machine learning automatisé.
ms.date: 12/18/2019
ms.custom: mvc,how-to
ms.openlocfilehash: b322c484282d025033d747d2093f7b5b4d216fde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75636560"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a>Guide pratique pour utiliser l’API de machine learning automatisé ML.NET

Le machine learning automatisé (AutoML) automatise le processus d’application du machine learning aux données. En utilisant un jeu de données, vous pouvez exécuter une **expérience** AutoML pour itérer sur différentes caractérisations de données, algorithmes de machine learning et hyperparamètres afin de sélectionner le meilleur modèle.

> [!NOTE]
> Cette rubrique fait référence à l’API de machine learning automatisé pour ML.NET, disponible en préversion. Ce matériau peut être sujet à modification.

## <a name="load-data"></a>Charger les données

Le machine learning automatisé prend en charge le chargement d’un jeu de données dans un [IDataView](xref:Microsoft.ML.IDataView). Les données peuvent se présenter sous la forme de fichiers de valeurs séparées par une tabulation (TSV) et de fichiers de valeurs séparées par une virgule (CSV).

Exemple :

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    // ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a>Sélectionner le type de tâche de machine learning

Avant de créer une expérience, déterminer le type de problème de machine learning que vous voulez résoudre. Le machine learning automatisé prend en charge les tâches de ML suivantes :

* Classification binaire
* Classification multiclasse
* régression ;
* Recommandation

## <a name="create-experiment-settings"></a>Créer les paramètres de l’expérience

Créez les paramètres de l’expérience pour le type de tâche de ML déterminé :

* Classification binaire

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* Classification multiclasse

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* régression ;

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

* Recommandation

  ```csharp
  var experimentSettings = new RecommendationExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a>Configurer les paramètres de l’expérience

Les expériences sont largement configurables. Consultez la [documentation sur l’API AutoML](https://docs.microsoft.com/dotnet/api/microsoft.ml.automl?view=ml-dotnet-preview) pour obtenir la liste complète des paramètres de configuration.

Voici quelques exemples :

1. Spécifier la durée maximale pendant laquelle l’expérience est autorisée à s’exécuter.

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. Utiliser un jeton d’annulation pour annuler l’expérience avant sa fin planifiée.

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. Spécifier une métrique d’optimisation différente.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. Le paramètre `CacheDirectory` est un pointeur vers un répertoire dans lequel tous les modèles entraînés au cours de la tâche AutoML sont enregistrés. Si `CacheDirectory` a la valeur Null, les modèles sont conservés dans la mémoire au lieu d’être écrits sur le disque.

    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. Demander au ML automatisé de ne pas utiliser certains entraîneurs.

    Une liste par défaut d’entraîneurs à optimiser est explorée par tâche. Cette liste peut être modifiée pour chaque expérience. Par exemple, vous pouvez supprimer de la liste les entraîneurs qui s’exécutent lentement sur votre jeu de données. Pour effectuer une optimisation sur un entraîneur spécifique, appelez `experimentSettings.Trainers.Clear()`, puis ajoutez l’entraîneur que vous souhaitez utiliser.

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

Vous trouverez la liste des entraîneurs pris en charge par tâche de ML en cliquant sur le lien correspondant ci-dessous :

* [Algorithmes de classification binaire pris en charge](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [Algorithmes de classification multiclasse pris en charge](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [Algorithmes de régression pris en charge](xref:Microsoft.ML.AutoML.RegressionTrainer)
* [Algorithmes de recommandation soutenus](xref:Microsoft.ML.AutoML.RecommendationTrainer)

## <a name="optimizing-metric"></a>Métrique d’optimisation

La métrique d’optimisation, comme illustré dans l’exemple ci-dessus, détermine la métrique à optimiser pendant l’entraînement du modèle. La métrique d’optimisation que vous pouvez sélectionner est déterminée par le type de tâche que vous choisissez. Vous trouverez plus bas une liste des métriques disponibles.

|[Classification binaire](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [Classification multiclasse](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[Recommandation de régression &](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|Précision| LogLoss | RSquared
|AreaUnderPrecisionRecallCurve | LogLossReduction | MeanAbsoluteError
|AreaUnderRocCurve | MacroAccuracy | MeanSquaredError
|F1Score | MicroAccuracy | RootMeanSquaredError
|NegativePrecision | TopKAccuracy
|NegativeRecall |
|PositivePrecision
|PositiveRecall

## <a name="data-pre-processing-and-featurization"></a>Prétraitement et caractérisation des données

> [!NOTE]
> La colonne de fonctionnalités <xref:System.Single>ne <xref:System.String>supportait que les types de <xref:System.Boolean>, , et .

Le prétraitement des données a lieu par défaut et les étapes suivantes sont effectuées automatiquement :

1. Supprimer les caractéristiques dépourvues d’informations utiles

    Suppression des caractéristiques sans informations utiles dans les jeux d’entraînement et de validation. Il s’agit des caractéristiques dont toutes les valeurs sont manquantes, ayant la même valeur dans toutes les lignes ou présentant une cardinalité très élevée (par exemple des hachages, des ID ou des GUID).

1. Indication et imputation des valeurs manquantes

    Remplir les cellules de valeur manquante avec la valeur par défaut pour le type de données. Ajouter des caractéristiques d’indicateur avec le même nombre d’emplacements que la colonne d’entrée. La valeur dans les caractéristiques d’indicateur ajoutées est `1` si la valeur dans la colonne d’entrée est manquante, `0` dans le cas contraire.

1. Générer des caractéristiques supplémentaires

    Pour les fonctions de texte : Caractéristiques du sac de mot à l’aide d’unigrammes et de tri-caractère-grammes.

    Pour les caractéristiques catégoriques: Un-chaud codage pour les caractéristiques de faible cardinalité, et un-chaud-hachage codage pour les caractéristiques catégoriques de haute cardinalité.

1. Transformations et encodages

    Les caractéristiques de texte ayant très peu de valeurs uniques sont transformées en caractéristiques de catégorie. En fonction de la cardinalité des caractéristiques de catégorie, effectuer un encodage one-hot ou one-hot-hash.

## <a name="exit-criteria"></a>Critères de sortie

Définissez les critères de fin de votre tâche :

1. Sortie après un certain temps : en utilisant `MaxExperimentTimeInSeconds` dans les paramètres de l’expérience, vous pouvez définir la durée en secondes pendant laquelle une tâche doit continuer à s’exécuter.

1. Sortie avec un jeton d’annulation : vous pouvez utiliser un jeton d’annulation pour annuler la tâche avant sa fin planifiée.

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a>Créer une expérience

Une fois configurés les paramètres de l’expérience, vous êtes prêt à créer celle-ci.

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a>Exécuter l’expérience

L’exécution de l’expérience déclenche le prétraitement des données, la sélection de l’algorithme d’entraînement et le réglage des hyperparamètres. AutoML continue de générer des combinaisons de caractérisation, d’algorithmes d’entraînement et d’hyperparamètres jusqu’à ce que `MaxExperimentTimeInSeconds` soit atteint ou que l’expérience soit terminée.

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

Explorez d’autres surcharges pour `Execute()` si vous souhaitez passer des données de validation, des informations de colonne indiquant l’objectif des colonnes ou des précaractériseurs.

## <a name="training-modes"></a>Modes d’entraînement

### <a name="training-dataset"></a>Jeu de données d’entraînement

AutoML met à votre disposition une méthode d’exécution d’expérience surchargée qui vous permet de fournir des données d’entraînement. En interne, le ML automatisé divise les données en fractionnements entraînement/validation.

```csharp
experiment.Execute(trainDataView);
```

### <a name="custom-validation-dataset"></a>Jeu de données de validation personnalisé

Utilisez un jeu de données de validation personnalisé si un fractionnement aléatoire ne convient pas, comme c’est généralement le cas avec les données de série chronologique. Vous pouvez spécifier votre propre jeu de données de validation. Le modèle est évalué par rapport au jeu de données de validation spécifié, plutôt que par rapport à un ou plusieurs jeux de données aléatoires.

```csharp
experiment.Execute(trainDataView, validationDataView);
```

## <a name="explore-model-metrics"></a>Explorer les métriques du modèle

Après chaque itération d’une expérience de ML, les métriques relatives à la tâche concernée sont stockées.

Par exemple, nous pouvons accéder aux métriques de validation issues de la meilleure exécution :

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

Voici toutes les métriques disponibles par tâche de ML :

* [Métriques de classification binaire](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [Métriques de classification multiclasse](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [Mesures de recommandation & de régression](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a>Voir aussi

Pour des exemples de code complets et bien plus encore, visitez le dépôt GitHub [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state).
