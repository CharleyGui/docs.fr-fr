---
title: Guide pratique pour utiliser l’API de ML automatisé ML.NET
description: L’API de ML automatisé ML.NET automatise le processus de génération de modèle prêt pour le déploiement. Découvrez les options que vous pouvez utiliser pour configurer des tâches de machine learning automatisé.
ms.date: 04/24/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d624b999384dd92d41033e385d01fe556e10a065
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960415"
---
# <a name="how-to-use-the-mlnet-automated-machine-learning-api"></a><span data-ttu-id="19f43-104">Guide pratique pour utiliser l’API de machine learning automatisé ML.NET</span><span class="sxs-lookup"><span data-stu-id="19f43-104">How to use the ML.NET automated machine learning API</span></span>

<span data-ttu-id="19f43-105">Le machine learning automatisé (AutoML) automatise le processus d’application du machine learning aux données.</span><span class="sxs-lookup"><span data-stu-id="19f43-105">Automated machine learning (AutoML) automates the process of applying machine learning to data.</span></span> <span data-ttu-id="19f43-106">En utilisant un jeu de données, vous pouvez exécuter une **expérience** AutoML pour itérer sur différentes caractérisations de données, algorithmes de machine learning et hyperparamètres afin de sélectionner le meilleur modèle.</span><span class="sxs-lookup"><span data-stu-id="19f43-106">Given a dataset, you can run an AutoML **experiment** to iterate over different data featurizations, machine learning algorithms, and hyperparameters to select the best model.</span></span>

> [!NOTE]
> <span data-ttu-id="19f43-107">Cette rubrique fait référence à l’API de machine learning automatisé pour ML.NET, disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="19f43-107">This topic refers to the automated machine learning API for ML.NET, which is currently in preview.</span></span> <span data-ttu-id="19f43-108">Ce matériau peut être sujet à modification.</span><span class="sxs-lookup"><span data-stu-id="19f43-108">Material may be subject to change.</span></span>

## <a name="load-data"></a><span data-ttu-id="19f43-109">Charger les données</span><span class="sxs-lookup"><span data-stu-id="19f43-109">Load data</span></span>

<span data-ttu-id="19f43-110">Le machine learning automatisé prend en charge le chargement d’un jeu de données dans un [IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="19f43-110">Automated machine learning supports loading a dataset into an [IDataView](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="19f43-111">Les données peuvent se présenter sous la forme de fichiers de valeurs séparées par une tabulation (TSV) et de fichiers de valeurs séparées par une virgule (CSV).</span><span class="sxs-lookup"><span data-stu-id="19f43-111">Data can be in the form of tab-separated value (TSV) files and comma separated value (CSV) files.</span></span>

<span data-ttu-id="19f43-112">Exemple :</span><span class="sxs-lookup"><span data-stu-id="19f43-112">Example:</span></span>

```csharp
using Microsoft.ML;
using Microsoft.ML.AutoML;
    ...
    MLContext mlContext = new MLContext();
    IDataView trainDataView = mlContext.Data.LoadFromTextFile<SentimentIssue>("my-data-file.csv", hasHeader: true);
```

## <a name="select-the-machine-learning-task-type"></a><span data-ttu-id="19f43-113">Sélectionner le type de tâche de machine learning</span><span class="sxs-lookup"><span data-stu-id="19f43-113">Select the machine learning task type</span></span>
<span data-ttu-id="19f43-114">Avant de créer une expérience, déterminer le type de problème de machine learning que vous voulez résoudre.</span><span class="sxs-lookup"><span data-stu-id="19f43-114">Before creating an experiment, determine the kind of machine learning problem you want to solve.</span></span> <span data-ttu-id="19f43-115">Le machine learning automatisé prend en charge les tâches de ML suivantes :</span><span class="sxs-lookup"><span data-stu-id="19f43-115">Automated machine learning supports the following ML tasks:</span></span>
* <span data-ttu-id="19f43-116">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="19f43-116">Binary Classification</span></span>
* <span data-ttu-id="19f43-117">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="19f43-117">Multiclass Classification</span></span>
* <span data-ttu-id="19f43-118">Régression</span><span class="sxs-lookup"><span data-stu-id="19f43-118">Regression</span></span>

## <a name="create-experiment-settings"></a><span data-ttu-id="19f43-119">Créer les paramètres de l’expérience</span><span class="sxs-lookup"><span data-stu-id="19f43-119">Create experiment settings</span></span>

<span data-ttu-id="19f43-120">Créez les paramètres de l’expérience pour le type de tâche de ML déterminé :</span><span class="sxs-lookup"><span data-stu-id="19f43-120">Create experiment settings for the determined ML task type:</span></span>

* <span data-ttu-id="19f43-121">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="19f43-121">Binary Classification</span></span>

  ```csharp
  var experimentSettings = new BinaryExperimentSettings();
  ```

* <span data-ttu-id="19f43-122">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="19f43-122">Multiclass Classification</span></span>

  ```csharp
  var experimentSettings = new MulticlassExperimentSettings();
  ```

* <span data-ttu-id="19f43-123">Régression</span><span class="sxs-lookup"><span data-stu-id="19f43-123">Regression</span></span>

  ```csharp
  var experimentSettings = new RegressionExperimentSettings();
  ```

## <a name="configure-experiment-settings"></a><span data-ttu-id="19f43-124">Configurer les paramètres de l’expérience</span><span class="sxs-lookup"><span data-stu-id="19f43-124">Configure experiment settings</span></span>

<span data-ttu-id="19f43-125">Les expériences sont largement configurables.</span><span class="sxs-lookup"><span data-stu-id="19f43-125">Experiments are highly configurable.</span></span> <span data-ttu-id="19f43-126">Consultez la [documentation sur l’API AutoML](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) pour obtenir la liste complète des paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="19f43-126">See the [AutoML API docs](https://docs.microsoft.com/dotnet/api/?view=automl-dotnet) for a full list of configuration settings.</span></span>

<span data-ttu-id="19f43-127">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="19f43-127">Some examples include:</span></span>

1. <span data-ttu-id="19f43-128">Spécifier la durée maximale pendant laquelle l’expérience est autorisée à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="19f43-128">Specify the maximum time that the experiment is allowed to run.</span></span>

    ```csharp
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    ```

1. <span data-ttu-id="19f43-129">Utiliser un jeton d’annulation pour annuler l’expérience avant sa fin planifiée.</span><span class="sxs-lookup"><span data-stu-id="19f43-129">Use a cancellation token to cancel the experiment before it is scheduled to finish.</span></span>

    ```csharp
    experimentSettings.CancellationToken = cts.Token;

    // Cancel experiment after the user presses any key
    CancelExperimentAfterAnyKeyPress(cts);
    ```

1. <span data-ttu-id="19f43-130">Spécifier une métrique d’optimisation différente.</span><span class="sxs-lookup"><span data-stu-id="19f43-130">Specify a different optimizing metric.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.OptimizingMetric = RegressionMetric.MeanSquaredError;
    ```

1. <span data-ttu-id="19f43-131">Le paramètre `CacheDirectory` est un pointeur vers un répertoire dans lequel tous les modèles entraînés au cours de la tâche AutoML sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="19f43-131">The `CacheDirectory` setting is a pointer to a directory where all models trained during the AutoML task will be saved.</span></span> <span data-ttu-id="19f43-132">Si `CacheDirectory` a la valeur Null, les modèles sont conservés dans la mémoire au lieu d’être écrits sur le disque.</span><span class="sxs-lookup"><span data-stu-id="19f43-132">If `CacheDirectory` is set to null, models will be kept in memory instead of written to disk.</span></span>
 
    ```csharp
    experimentSettings.CacheDirectory = null;
    ```

1. <span data-ttu-id="19f43-133">Demander au ML automatisé de ne pas utiliser certains entraîneurs.</span><span class="sxs-lookup"><span data-stu-id="19f43-133">Instruct automated ML not to use certain trainers.</span></span>

    <span data-ttu-id="19f43-134">Une liste par défaut d’entraîneurs à optimiser est explorée par tâche.</span><span class="sxs-lookup"><span data-stu-id="19f43-134">A default list of trainers to optimize are explored per task.</span></span> <span data-ttu-id="19f43-135">Cette liste peut être modifiée pour chaque expérience.</span><span class="sxs-lookup"><span data-stu-id="19f43-135">This list can be modified for each experiment.</span></span> <span data-ttu-id="19f43-136">Par exemple, vous pouvez supprimer de la liste les entraîneurs qui s’exécutent lentement sur votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="19f43-136">For instance, trainers that run slowly on your dataset can be removed from the list.</span></span> <span data-ttu-id="19f43-137">Pour effectuer une optimisation sur un entraîneur spécifique, appelez `experimentSettings.Trainers.Clear()`, puis ajoutez l’entraîneur que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="19f43-137">To optimize on one specific trainer call `experimentSettings.Trainers.Clear()`, then add the trainer that you want to use.</span></span>

    ```csharp
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.Trainers.Remove(RegressionTrainer.LbfgsPoissonRegression);
    experimentSettings.Trainers.Remove(RegressionTrainer.OnlineGradientDescent);
    ```

<span data-ttu-id="19f43-138">Vous trouverez la liste des entraîneurs pris en charge par tâche de ML en cliquant sur le lien correspondant ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="19f43-138">The list of supported trainers per ML task can be found at the corresponding link below:</span></span>
* [<span data-ttu-id="19f43-139">Algorithmes de classification binaire pris en charge</span><span class="sxs-lookup"><span data-stu-id="19f43-139">Supported Binary Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationTrainer)
* [<span data-ttu-id="19f43-140">Algorithmes de classification multiclasse pris en charge</span><span class="sxs-lookup"><span data-stu-id="19f43-140">Supported Multiclass Classification Algorithms</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationTrainer)
* [<span data-ttu-id="19f43-141">Algorithmes de régression pris en charge</span><span class="sxs-lookup"><span data-stu-id="19f43-141">Supported Regression Algorithms</span></span>](xref:Microsoft.ML.AutoML.RegressionTrainer)

## <a name="optimizing-metric"></a><span data-ttu-id="19f43-142">Métrique d’optimisation</span><span class="sxs-lookup"><span data-stu-id="19f43-142">Optimizing metric</span></span>

<span data-ttu-id="19f43-143">La métrique d’optimisation, comme illustré dans l’exemple ci-dessus, détermine la métrique à optimiser pendant l’entraînement du modèle.</span><span class="sxs-lookup"><span data-stu-id="19f43-143">The optimizing metric, as shown in the example above, determines the metric to be optimized during model training.</span></span> <span data-ttu-id="19f43-144">La métrique d’optimisation que vous pouvez sélectionner est déterminée par le type de tâche que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="19f43-144">The optimizing metric you can select is determined by the task type you choose.</span></span> <span data-ttu-id="19f43-145">Voici la liste des métriques disponibles.</span><span class="sxs-lookup"><span data-stu-id="19f43-145">Below is a list of available metrics.</span></span>

|[<span data-ttu-id="19f43-146">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="19f43-146">Binary Classification</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric) | [<span data-ttu-id="19f43-147">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="19f43-147">Multiclass Classification</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric) |[<span data-ttu-id="19f43-148">Régression</span><span class="sxs-lookup"><span data-stu-id="19f43-148">Regression</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)
|-- |-- |--
|<span data-ttu-id="19f43-149">Précision</span><span class="sxs-lookup"><span data-stu-id="19f43-149">Accuracy</span></span>| <span data-ttu-id="19f43-150">LogLoss</span><span class="sxs-lookup"><span data-stu-id="19f43-150">LogLoss</span></span> | <span data-ttu-id="19f43-151">RSquared</span><span class="sxs-lookup"><span data-stu-id="19f43-151">RSquared</span></span>
|<span data-ttu-id="19f43-152">AreaUnderPrecisionRecallCurve</span><span class="sxs-lookup"><span data-stu-id="19f43-152">AreaUnderPrecisionRecallCurve</span></span> | <span data-ttu-id="19f43-153">LogLossReduction</span><span class="sxs-lookup"><span data-stu-id="19f43-153">LogLossReduction</span></span> | <span data-ttu-id="19f43-154">MeanAbsoluteError</span><span class="sxs-lookup"><span data-stu-id="19f43-154">MeanAbsoluteError</span></span>
|<span data-ttu-id="19f43-155">AreaUnderRocCurve</span><span class="sxs-lookup"><span data-stu-id="19f43-155">AreaUnderRocCurve</span></span> | <span data-ttu-id="19f43-156">MacroAccuracy</span><span class="sxs-lookup"><span data-stu-id="19f43-156">MacroAccuracy</span></span> | <span data-ttu-id="19f43-157">MeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="19f43-157">MeanSquaredError</span></span>
|<span data-ttu-id="19f43-158">F1Score</span><span class="sxs-lookup"><span data-stu-id="19f43-158">F1Score</span></span> | <span data-ttu-id="19f43-159">MicroAccuracy</span><span class="sxs-lookup"><span data-stu-id="19f43-159">MicroAccuracy</span></span> | <span data-ttu-id="19f43-160">RootMeanSquaredError</span><span class="sxs-lookup"><span data-stu-id="19f43-160">RootMeanSquaredError</span></span>
|<span data-ttu-id="19f43-161">NegativePrecision</span><span class="sxs-lookup"><span data-stu-id="19f43-161">NegativePrecision</span></span> | <span data-ttu-id="19f43-162">TopKAccuracy</span><span class="sxs-lookup"><span data-stu-id="19f43-162">TopKAccuracy</span></span>
|<span data-ttu-id="19f43-163">NegativeRecall</span><span class="sxs-lookup"><span data-stu-id="19f43-163">NegativeRecall</span></span> |
|<span data-ttu-id="19f43-164">PositivePrecision</span><span class="sxs-lookup"><span data-stu-id="19f43-164">PositivePrecision</span></span>
|<span data-ttu-id="19f43-165">PositiveRecall</span><span class="sxs-lookup"><span data-stu-id="19f43-165">PositiveRecall</span></span>

## <a name="data-pre-processing-and-featurization"></a><span data-ttu-id="19f43-166">Prétraitement et caractérisation des données</span><span class="sxs-lookup"><span data-stu-id="19f43-166">Data pre-processing and featurization</span></span>

<span data-ttu-id="19f43-167">Le prétraitement des données a lieu par défaut et les étapes suivantes sont effectuées automatiquement :</span><span class="sxs-lookup"><span data-stu-id="19f43-167">Data pre-processing happens by default and the following steps are performed automatically for you:</span></span>

1. <span data-ttu-id="19f43-168">Supprimer les caractéristiques dépourvues d’informations utiles</span><span class="sxs-lookup"><span data-stu-id="19f43-168">Drop features with no useful information</span></span>

    <span data-ttu-id="19f43-169">Supprimer des jeux d’entraînement et de validation les caractéristiques dépourvues d’informations utiles.</span><span class="sxs-lookup"><span data-stu-id="19f43-169">Drop features with no useful information from training and validation sets.</span></span> <span data-ttu-id="19f43-170">Celles-ci incluent les caractéristiques dont toutes les valeurs sont manquantes, dont toutes les lignes ont la même valeur ou présentant une cardinalité très élevée (par exemple, hachages, ID ou GUID).</span><span class="sxs-lookup"><span data-stu-id="19f43-170">These include features with all values missing, same value across all rows or with extremely high cardinality (e.g., hashes, IDs or GUIDs).</span></span>

1. <span data-ttu-id="19f43-171">Indication et imputation des valeurs manquantes</span><span class="sxs-lookup"><span data-stu-id="19f43-171">Missing value indication and imputation</span></span>

    <span data-ttu-id="19f43-172">Remplir les cellules de valeur manquante avec la valeur par défaut pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="19f43-172">Fill missing value cells with the default value for the datatype.</span></span> <span data-ttu-id="19f43-173">Ajouter des caractéristiques d’indicateur avec le même nombre d’emplacements que la colonne d’entrée.</span><span class="sxs-lookup"><span data-stu-id="19f43-173">Append indicator features with the same number of slots as the input column.</span></span> <span data-ttu-id="19f43-174">La valeur dans les caractéristiques d’indicateur ajoutées est `1` si la valeur dans la colonne d’entrée est manquante, `0` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="19f43-174">The value in the appended indicator features is `1` if the value in the input column is missing and `0` otherwise.</span></span>

1. <span data-ttu-id="19f43-175">Générer des caractéristiques supplémentaires</span><span class="sxs-lookup"><span data-stu-id="19f43-175">Generate additional features</span></span>
    
    <span data-ttu-id="19f43-176">Pour les caractéristiques de texte : Caractéristiques de type sac de mots utilisant des unigrammes et des trigrammes.</span><span class="sxs-lookup"><span data-stu-id="19f43-176">For text features: Bag-of-word features using unigrams and tri-character-grams.</span></span>
    
    <span data-ttu-id="19f43-177">Pour les caractéristiques de catégorie : Encodage one-hot des caractéristiques à faible cardinalité et encodage one-hot-hash des caractéristiques de catégorie à cardinalité élevée.</span><span class="sxs-lookup"><span data-stu-id="19f43-177">For categorical features: One-hot encoding for low cardinality features, and one-hot-hash encoding for high cardinality categorical features.</span></span>

1. <span data-ttu-id="19f43-178">Transformations et encodages</span><span class="sxs-lookup"><span data-stu-id="19f43-178">Transformations and encodings</span></span>

    <span data-ttu-id="19f43-179">Les caractéristiques de texte ayant très peu de valeurs uniques sont transformées en caractéristiques de catégorie.</span><span class="sxs-lookup"><span data-stu-id="19f43-179">Text features with very few unique values transformed into categorical features.</span></span> <span data-ttu-id="19f43-180">En fonction de la cardinalité des caractéristiques de catégorie, effectuer un encodage one-hot ou one-hot-hash.</span><span class="sxs-lookup"><span data-stu-id="19f43-180">Depending on cardinality of categorical features, perform one-hot encoding or one-hot hash encoding.</span></span>

## <a name="exit-criteria"></a><span data-ttu-id="19f43-181">Critères de sortie</span><span class="sxs-lookup"><span data-stu-id="19f43-181">Exit criteria</span></span>

<span data-ttu-id="19f43-182">Définissez les critères de fin de votre tâche :</span><span class="sxs-lookup"><span data-stu-id="19f43-182">Define the criteria to complete your task:</span></span>

1. <span data-ttu-id="19f43-183">Sortie après un certain temps : en utilisant `MaxExperimentTimeInSeconds` dans les paramètres de l’expérience, vous pouvez définir la durée en secondes pendant laquelle une tâche doit continuer à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="19f43-183">Exit after a length of time - Using `MaxExperimentTimeInSeconds` in your experiment settings you can define how long in seconds that an task should continue to run.</span></span>

1. <span data-ttu-id="19f43-184">Sortie avec un jeton d’annulation : vous pouvez utiliser un jeton d’annulation pour annuler la tâche avant sa fin planifiée.</span><span class="sxs-lookup"><span data-stu-id="19f43-184">Exit on a cancellation token -  You can use a cancellation token that lets you cancel the task before it is scheduled to finish.</span></span>

    ```csharp
    var cts = new CancellationTokenSource();
    var experimentSettings = new RegressionExperimentSettings();
    experimentSettings.MaxExperimentTimeInSeconds = 3600;
    experimentSettings.CancellationToken = cts.Token;
    ```

## <a name="create-an-experiment"></a><span data-ttu-id="19f43-185">Créer une expérience</span><span class="sxs-lookup"><span data-stu-id="19f43-185">Create an experiment</span></span>

<span data-ttu-id="19f43-186">Une fois configurés les paramètres de l’expérience, vous êtes prêt à créer celle-ci.</span><span class="sxs-lookup"><span data-stu-id="19f43-186">Once you have configured the experiment settings, you are ready to create the experiment.</span></span>

```csharp
RegressionExperiment experiment = mlContext.Auto().CreateRegressionExperiment(experimentSettings);
```

## <a name="run-the-experiment"></a><span data-ttu-id="19f43-187">Exécuter l’expérience</span><span class="sxs-lookup"><span data-stu-id="19f43-187">Run the experiment</span></span>

<span data-ttu-id="19f43-188">L’exécution de l’expérience déclenche le prétraitement des données, la sélection de l’algorithme d’entraînement et le réglage des hyperparamètres.</span><span class="sxs-lookup"><span data-stu-id="19f43-188">Running the experiment triggers data pre-processing, learning algorithm selection, and hyperparameter tuning.</span></span> <span data-ttu-id="19f43-189">AutoML continue de générer des combinaisons de caractérisation, d’algorithmes d’entraînement et d’hyperparamètres jusqu’à ce que `MaxExperimentTimeInSeconds` soit atteint ou que l’expérience soit terminée.</span><span class="sxs-lookup"><span data-stu-id="19f43-189">AutoML will continue to generate combinations of featurization, learning algorithms, and hyperparameters until the `MaxExperimentTimeInSeconds` is reached or the experiment is terminated.</span></span>

```csharp
ExperimentResult<RegressionMetrics> experimentResult = experiment
    .Execute(trainingDataView, LabelColumnName, progressHandler: progressHandler);
```

<span data-ttu-id="19f43-190">Explorez d’autres surcharges pour `Execute()` si vous souhaitez passer des données de validation, des informations de colonne indiquant l’objectif des colonnes ou des précaractériseurs.</span><span class="sxs-lookup"><span data-stu-id="19f43-190">Explore other overloads for `Execute()` if you want to pass in validation data, column information indicating the column purpose, or prefeaturizers.</span></span>

## <a name="training-modes"></a><span data-ttu-id="19f43-191">Modes d’entraînement</span><span class="sxs-lookup"><span data-stu-id="19f43-191">Training modes</span></span>

### <a name="training-dataset"></a><span data-ttu-id="19f43-192">Jeu de données d’entraînement</span><span class="sxs-lookup"><span data-stu-id="19f43-192">Training dataset</span></span>

<span data-ttu-id="19f43-193">AutoML met à votre disposition une méthode d’exécution d’expérience surchargée qui vous permet de fournir des données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="19f43-193">AutoML provides an overloaded experiment execute method which allows you to provide training data.</span></span> <span data-ttu-id="19f43-194">En interne, le ML automatisé divise les données en fractionnements entraînement/validation.</span><span class="sxs-lookup"><span data-stu-id="19f43-194">Internally, automated ML divides the data into train-validate splits.</span></span>

```csharp
experiment.Execute(trainDataView);   
```

### <a name="custom-validation-dataset"></a><span data-ttu-id="19f43-195">Jeu de données de validation personnalisé</span><span class="sxs-lookup"><span data-stu-id="19f43-195">Custom validation dataset</span></span>

<span data-ttu-id="19f43-196">Utilisez un jeu de données de validation personnalisé si un fractionnement aléatoire ne convient pas, comme c’est généralement le cas avec les données de série chronologique.</span><span class="sxs-lookup"><span data-stu-id="19f43-196">Use custom validation dataset if random split is not acceptable, as is usually the case with time series data.</span></span> <span data-ttu-id="19f43-197">Vous pouvez spécifier votre propre jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="19f43-197">You can specify your own validation dataset.</span></span> <span data-ttu-id="19f43-198">Le modèle est évalué par rapport au jeu de données de validation spécifié, plutôt que par rapport à un ou plusieurs jeux de données aléatoires.</span><span class="sxs-lookup"><span data-stu-id="19f43-198">The model will be evaluated against the validation dataset specified instead of one or more random datasets.</span></span>

```csharp
experiment.Execute(trainDataView, validationDataView);   
```

## <a name="explore-model-metrics"></a><span data-ttu-id="19f43-199">Explorer les métriques de modèle</span><span class="sxs-lookup"><span data-stu-id="19f43-199">Explore model metrics</span></span>

<span data-ttu-id="19f43-200">Après chaque itération d’une expérience de ML, les métriques relatives à la tâche concernée sont stockées.</span><span class="sxs-lookup"><span data-stu-id="19f43-200">After each iteration of an ML experiment, metrics relating to that task are stored.</span></span>

<span data-ttu-id="19f43-201">Par exemple, nous pouvons accéder aux métriques de validation issues de la meilleure exécution :</span><span class="sxs-lookup"><span data-stu-id="19f43-201">For example, we can access validation metrics from the best run:</span></span>

```csharp
RegressionMetrics metrics = experimentResult.BestRun.ValidationMetrics;
Console.WriteLine($"R-Squared: {metrics.RSquared:0.##}");
Console.WriteLine($"Root Mean Squared Error: {metrics.RootMeanSquaredError:0.##}");
```

<span data-ttu-id="19f43-202">Voici toutes les métriques disponibles par tâche de ML :</span><span class="sxs-lookup"><span data-stu-id="19f43-202">The following are all the available metrics per ML task:</span></span>
* [<span data-ttu-id="19f43-203">Métriques de classification binaire</span><span class="sxs-lookup"><span data-stu-id="19f43-203">Binary classification metrics</span></span>](xref:Microsoft.ML.AutoML.BinaryClassificationMetric)
* [<span data-ttu-id="19f43-204">Métriques de classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="19f43-204">Multiclass classification metrics</span></span>](xref:Microsoft.ML.AutoML.MulticlassClassificationMetric)
* [<span data-ttu-id="19f43-205">Métriques de régression</span><span class="sxs-lookup"><span data-stu-id="19f43-205">Regression metrics</span></span>](xref:Microsoft.ML.AutoML.RegressionMetric)

## <a name="see-also"></a><span data-ttu-id="19f43-206">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19f43-206">See also</span></span>

<span data-ttu-id="19f43-207">Pour des exemples de code complets et bien plus encore, visitez le dépôt GitHub [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state).</span><span class="sxs-lookup"><span data-stu-id="19f43-207">For full code samples and more visit the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master#automate-mlnet-models-generation-preview-state) GitHub repository.</span></span>
