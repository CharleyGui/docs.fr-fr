---
title: Automatiser l’entraînement du modèle avec l’interface CLI ML.NET
description: Découvrez comment utiliser l’outil CLI ML.NET pour entraîner automatiquement le meilleur modèle à partir de la ligne de commande.
ms.date: 12/17/2019
ms.custom: how-to
ms.openlocfilehash: 9c493b1df0dd326ad2f0a5d1cac0fc11d7cf37e2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240621"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="534bb-103">Automatiser l’entraînement du modèle avec l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="534bb-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="534bb-104">L’interface CLI ML.NET automatise la génération de modèles pour les développeurs .NET.</span><span class="sxs-lookup"><span data-stu-id="534bb-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="534bb-105">Pour utiliser l’API ML.NET seule (c’est-à-dire sans l’interface CLI AutoML ML.NET), vous devez choisir un entraîneur (implémentation d’un algorithme de machine learning pour une tâche particulière) ainsi que l’ensemble des transformations de données (ingénierie des caractéristiques) à appliquer à vos données.</span><span class="sxs-lookup"><span data-stu-id="534bb-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="534bb-106">Le pipeline optimal varie en fonction de chaque jeu de données, et choisir l’algorithme optimal parmi toutes les options possibles accroît encore la complexité.</span><span class="sxs-lookup"><span data-stu-id="534bb-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="534bb-107">De plus, chaque algorithme est associé à un ensemble d’hyperparamètres que vous devez régler.</span><span class="sxs-lookup"><span data-stu-id="534bb-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="534bb-108">Bref, vous pouvez passer des semaines et parfois plusieurs mois à optimiser le modèle Machine Learning pour essayer de trouver les meilleures combinaisons possibles entre l’ingénierie des caractéristiques, les algorithmes d’apprentissage et les hyperparamètres.</span><span class="sxs-lookup"><span data-stu-id="534bb-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="534bb-109">L’interface CLI ML.NET simplifie ce processus à l’aide de Machine Learning automatisés (AutoML).</span><span class="sxs-lookup"><span data-stu-id="534bb-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span> 

> [!NOTE]
> <span data-ttu-id="534bb-110">Cette rubrique fait référence à l’interface **CLI** ML.NET et au moteur **AutoML** ML.NET, qui sont actuellement en préversion et donc susceptibles d’être modifiés.</span><span class="sxs-lookup"><span data-stu-id="534bb-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="534bb-111">Qu’est-ce que l’interface de ligne de commande (CLI) ML.NET ?</span><span class="sxs-lookup"><span data-stu-id="534bb-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="534bb-112">L’interface CLI ML.NET est un [outil .net Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="534bb-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="534bb-113">Une fois installé, vous lui donnez un Machine Learning tâche et un jeu de données d’apprentissage, et il génère un modèle ML.NET, C# ainsi que le code à exécuter pour utiliser le modèle dans votre application.</span><span class="sxs-lookup"><span data-stu-id="534bb-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="534bb-114">Comme indiqué dans l’illustration suivante, il est simple de générer un modèle ML.NET de haute qualité (fichier. zip du modèle sérialisé) plus l' C# exemple de code pour exécuter/noter ce modèle.</span><span class="sxs-lookup"><span data-stu-id="534bb-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="534bb-115">Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches et des itérations sur l’algorithme et les paramètres appliqués pour ce « meilleur modèle » généré.</span><span class="sxs-lookup"><span data-stu-id="534bb-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="534bb-116">![image](media/automate-training-with-cli/cli-high-level-process.png "Le moteur AutoML fonctionne à l’intérieur de l’interface CLI ML.NET")</span><span class="sxs-lookup"><span data-stu-id="534bb-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="534bb-117">Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.</span><span class="sxs-lookup"><span data-stu-id="534bb-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="534bb-118">Actuellement, l’interface CLI ML.NET prend en charge les tâches ML suivantes :</span><span class="sxs-lookup"><span data-stu-id="534bb-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="534bb-119">À l’avenir, elle prendra d’autres tâches de machine learning comme `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="534bb-119">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="534bb-120">Exemple d'utilisation :</span><span class="sxs-lookup"><span data-stu-id="534bb-120">Example of usage:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="534bb-122">Vous pouvez exécuter cette commande de la même façon sur *Windows PowerShell*, \*macOS/Linux Bash ou *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="534bb-122">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="534bb-123">Toutefois, l’autocomplétion via la touche tab (suggestions de paramètres) ne fonctionne pas sur *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="534bb-123">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="534bb-124">Ressources générées en sortie</span><span class="sxs-lookup"><span data-stu-id="534bb-124">Output assets generated</span></span>

<span data-ttu-id="534bb-125">La commande `auto-train` de l’interface CLI génère les ressources suivantes dans le dossier de sortie :</span><span class="sxs-lookup"><span data-stu-id="534bb-125">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="534bb-126">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé pour effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="534bb-126">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="534bb-127">Une solution C# contenant :</span><span class="sxs-lookup"><span data-stu-id="534bb-127">C# solution with:</span></span>
  - <span data-ttu-id="534bb-128">Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).</span><span class="sxs-lookup"><span data-stu-id="534bb-128">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="534bb-129">Le code C# avec le code d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage ou de réentraînement du modèle).</span><span class="sxs-lookup"><span data-stu-id="534bb-129">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="534bb-130">Un fichier journal contenant des informations sur l’ensemble des itérations/balayages effectués sur tous les algorithmes évalués, y compris les détails de leur pipeline/configuration.</span><span class="sxs-lookup"><span data-stu-id="534bb-130">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="534bb-131">Les deux premières ressources peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.</span><span class="sxs-lookup"><span data-stu-id="534bb-131">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="534bb-132">La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par l’interface CLI pour entraîner le modèle généré. Vous pouvez alors réentraîner votre modèle et effectuer des recherches/itérations sur l’entraîneur/algorithme et les hyperparamètres spécifiques qui avaient été automatiquement sélectionnés par l’interface CLI et AutoML.</span><span class="sxs-lookup"><span data-stu-id="534bb-132">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="534bb-133">Déterminer la qualité du modèle</span><span class="sxs-lookup"><span data-stu-id="534bb-133">Understanding the quality of the model</span></span>

<span data-ttu-id="534bb-134">Quand vous générez un « meilleur modèle » à l’aide de l’outil CLI, vous voyez les mesures de qualité (telles que la précision et la R ²) appropriées pour la tâche ML que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="534bb-134">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="534bb-135">Ici, ces métriques sont regroupées par tâche ML, ce qui vous permet de comprendre la qualité de votre « meilleur modèle » généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="534bb-135">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="534bb-136">Métriques pour les modèles de classification binaire</span><span class="sxs-lookup"><span data-stu-id="534bb-136">Metrics for Binary Classification models</span></span>

<span data-ttu-id="534bb-137">La capture d’écran suivante liste les métriques des tâches ML de classification binaire pour les cinq meilleurs modèles trouvés par l’outil CLI :</span><span class="sxs-lookup"><span data-stu-id="534bb-137">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="534bb-139">La précision est une mesure populaire pour les problèmes de classification, mais la précision n’est pas toujours la meilleure mesure pour sélectionner le meilleur modèle à partir de, comme expliqué dans les références suivantes.</span><span class="sxs-lookup"><span data-stu-id="534bb-139">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="534bb-140">Dans certains cas, vous aurez besoin d’évaluer la qualité de votre modèle à l’aide d’autres métriques.</span><span class="sxs-lookup"><span data-stu-id="534bb-140">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="534bb-141">Pour explorer et comprendre les métriques générées par l’interface CLI, consultez [mesures d’évaluation pour la classification binaire](resources/metrics.md#evaluation-metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="534bb-141">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for binary classification](resources/metrics.md#evaluation-metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="534bb-142">Métriques pour les modèles de classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="534bb-142">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="534bb-143">La capture d’écran suivante liste les métriques des tâches ML de classification multiclasse pour les cinq meilleurs modèles trouvés par l’outil CLI :</span><span class="sxs-lookup"><span data-stu-id="534bb-143">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="534bb-145">Pour explorer et comprendre les métriques générées par l’interface CLI, consultez [mesures d’évaluation pour la classification multiclasse](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="534bb-145">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for multiclass classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="534bb-146">Métriques pour les modèles de régression et de recommandation</span><span class="sxs-lookup"><span data-stu-id="534bb-146">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="534bb-147">Le modèle de régression est approprié dans les cas où les différences entre les valeurs observées et les valeurs prédites du modèle sont mineures et non biaisées.</span><span class="sxs-lookup"><span data-stu-id="534bb-147">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="534bb-148">La régression peut être évaluée avec des métriques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="534bb-148">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="534bb-149">Vous verrez une liste similaire de métriques pour les cinq meilleurs modèles de qualité trouvés par l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="534bb-149">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="534bb-150">Cas particulier concernant une tâche ML de régression :</span><span class="sxs-lookup"><span data-stu-id="534bb-150">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="534bb-152">Pour explorer et comprendre les métriques générées par l’interface CLI, consultez [mesures d’évaluation pour la régression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="534bb-152">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="534bb-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="534bb-153">See also</span></span>

- [<span data-ttu-id="534bb-154">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="534bb-154">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="534bb-155">Didacticiel : analyser le sentiment à l’aide de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="534bb-155">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="534bb-156">Informations de référence sur les commandes de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="534bb-156">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="534bb-157">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="534bb-157">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
