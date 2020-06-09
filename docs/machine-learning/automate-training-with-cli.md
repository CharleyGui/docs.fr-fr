---
title: Automatiser l’entraînement du modèle avec l’interface CLI ML.NET
description: Découvrez comment utiliser l’outil CLI ML.NET pour entraîner automatiquement le meilleur modèle à partir de la ligne de commande.
ms.date: 06/03/2020
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: d7c6102c2257be1daa613fde0edabce83d04b414
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589658"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="71087-103">Automatiser l’entraînement du modèle avec l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="71087-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="71087-104">L’interface CLI ML.NET automatise la génération de modèles pour les développeurs .NET.</span><span class="sxs-lookup"><span data-stu-id="71087-104">The ML.NET CLI automates model generation for .NET developers.</span></span>

<span data-ttu-id="71087-105">Pour utiliser l’API ML.NET seule (c’est-à-dire sans l’interface CLI AutoML ML.NET), vous devez choisir un entraîneur (implémentation d’un algorithme de machine learning pour une tâche particulière) ainsi que l’ensemble des transformations de données (ingénierie des caractéristiques) à appliquer à vos données.</span><span class="sxs-lookup"><span data-stu-id="71087-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="71087-106">Le pipeline optimal varie en fonction de chaque jeu de données, et choisir l’algorithme optimal parmi toutes les options possibles accroît encore la complexité.</span><span class="sxs-lookup"><span data-stu-id="71087-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="71087-107">De plus, chaque algorithme est associé à un ensemble d’hyperparamètres que vous devez régler.</span><span class="sxs-lookup"><span data-stu-id="71087-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="71087-108">Bref, vous pouvez passer des semaines et parfois plusieurs mois à optimiser le modèle Machine Learning pour essayer de trouver les meilleures combinaisons possibles entre l’ingénierie des caractéristiques, les algorithmes d’apprentissage et les hyperparamètres.</span><span class="sxs-lookup"><span data-stu-id="71087-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="71087-109">L’interface CLI ML.NET simplifie ce processus à l’aide de Machine Learning automatisés (AutoML).</span><span class="sxs-lookup"><span data-stu-id="71087-109">The ML.NET CLI simplifies this process using automated machine learning (AutoML).</span></span>

> [!NOTE]
> <span data-ttu-id="71087-110">Cette rubrique fait référence à l’interface **CLI** ML.NET et au moteur **AutoML** ML.NET, qui sont actuellement en préversion et donc susceptibles d’être modifiés.</span><span class="sxs-lookup"><span data-stu-id="71087-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="71087-111">Qu’est-ce que l’interface de ligne de commande (CLI) ML.NET ?</span><span class="sxs-lookup"><span data-stu-id="71087-111">What is the ML.NET command-line interface (CLI)?</span></span>

<span data-ttu-id="71087-112">L’interface CLI ML.NET est un [outil .net Core](../core/tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="71087-112">The ML.NET CLI is a [.NET Core tool](../core/tools/global-tools.md).</span></span> <span data-ttu-id="71087-113">Une fois installé, vous lui donnez un Machine Learning tâche et un jeu de données d’apprentissage, et il génère un modèle ML.NET, ainsi que le code C# à exécuter pour utiliser le modèle dans votre application.</span><span class="sxs-lookup"><span data-stu-id="71087-113">Once installed, you give it a machine learning task and a training dataset, and it generates an ML.NET model, as well as the C# code to run to use the model in your application.</span></span>

<span data-ttu-id="71087-114">Comme indiqué dans l’illustration suivante, il est simple de générer un modèle ML.NET de haute qualité (fichier. zip du modèle sérialisé) plus l’exemple de code C# pour exécuter/noter ce modèle.</span><span class="sxs-lookup"><span data-stu-id="71087-114">As shown in the following figure, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="71087-115">Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches et des itérations sur l’algorithme et les paramètres appliqués pour ce « meilleur modèle » généré.</span><span class="sxs-lookup"><span data-stu-id="71087-115">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="71087-116">![image](media/automate-training-with-cli/cli-high-level-process.png "Le moteur AutoML fonctionne à l’intérieur de l’interface CLI ML.NET")</span><span class="sxs-lookup"><span data-stu-id="71087-116">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="71087-117">Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.</span><span class="sxs-lookup"><span data-stu-id="71087-117">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="71087-118">La CLI ML.NET prend en charge les tâches de ML suivantes :</span><span class="sxs-lookup"><span data-stu-id="71087-118">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- <span data-ttu-id="71087-119">classification (binaire et multi-classe)</span><span class="sxs-lookup"><span data-stu-id="71087-119">classification (binary and multi-class)</span></span>
- <span data-ttu-id="71087-120">régression</span><span class="sxs-lookup"><span data-stu-id="71087-120">regression</span></span>
- <span data-ttu-id="71087-121">Recommandation</span><span class="sxs-lookup"><span data-stu-id="71087-121">recommendation</span></span>
- <span data-ttu-id="71087-122">Demain : autres tâches Machine Learning telles que la classification des images, le classement, la détection des anomalies, le clustering</span><span class="sxs-lookup"><span data-stu-id="71087-122">Future: other machine learning tasks such as image-classification, ranking, anomaly-detection, clustering</span></span>

<span data-ttu-id="71087-123">Exemple d’utilisation (scénario de classification) :</span><span class="sxs-lookup"><span data-stu-id="71087-123">Example of usage (classification scenario):</span></span>

```console
mlnet classification --dataset "yelp_labelled.txt" --label-col 1 --has-header false --train-time 10
```

![image](media/automate-training-with-cli/mlnet-classification-powershell.gif)

<span data-ttu-id="71087-125">Vous pouvez l’exécuter de la même façon sur *Windows PowerShell*, *MacOS/Linux bash*ou *Windows cmd*.</span><span class="sxs-lookup"><span data-stu-id="71087-125">You can run it the same way on *Windows PowerShell*, *macOS/Linux bash*, or *Windows CMD*.</span></span> <span data-ttu-id="71087-126">Toutefois, l’autocomplétion via la touche tab (suggestions de paramètres) ne fonctionne pas sur *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="71087-126">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="71087-127">Ressources générées en sortie</span><span class="sxs-lookup"><span data-stu-id="71087-127">Output assets generated</span></span>

<span data-ttu-id="71087-128">Les commandes de tâche ML dans l’interface CLI génèrent les ressources suivantes dans le dossier de sortie :</span><span class="sxs-lookup"><span data-stu-id="71087-128">The ML task commands in the CLI generate the following assets in the output folder:</span></span>

- <span data-ttu-id="71087-129">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé pour effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="71087-129">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="71087-130">Une solution C# contenant :</span><span class="sxs-lookup"><span data-stu-id="71087-130">C# solution with:</span></span>
  - <span data-ttu-id="71087-131">Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).</span><span class="sxs-lookup"><span data-stu-id="71087-131">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="71087-132">Le code C# avec le code d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage ou de réentraînement du modèle).</span><span class="sxs-lookup"><span data-stu-id="71087-132">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="71087-133">Un fichier journal contenant des informations sur l’ensemble des itérations/balayages effectués sur tous les algorithmes évalués, y compris les détails de leur pipeline/configuration.</span><span class="sxs-lookup"><span data-stu-id="71087-133">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="71087-134">Les deux premières ressources peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.</span><span class="sxs-lookup"><span data-stu-id="71087-134">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="71087-135">La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par l’interface CLI pour entraîner le modèle généré. Vous pouvez alors réentraîner votre modèle et effectuer des recherches/itérations sur l’entraîneur/algorithme et les hyperparamètres spécifiques qui avaient été automatiquement sélectionnés par l’interface CLI et AutoML.</span><span class="sxs-lookup"><span data-stu-id="71087-135">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="71087-136">Déterminer la qualité du modèle</span><span class="sxs-lookup"><span data-stu-id="71087-136">Understanding the quality of the model</span></span>

<span data-ttu-id="71087-137">Quand vous générez un « meilleur modèle » à l’aide de l’outil CLI, vous voyez les mesures de qualité (telles que la précision et la R ²) appropriées pour la tâche ML que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="71087-137">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy and R-Squared) as appropriate for the ML task you're targeting.</span></span>

<span data-ttu-id="71087-138">Ici, ces métriques sont regroupées par tâche ML, ce qui vous permet de comprendre la qualité de votre « meilleur modèle » généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="71087-138">Here those metrics are summarized grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-classification-models"></a><span data-ttu-id="71087-139">Métriques pour les modèles de classification</span><span class="sxs-lookup"><span data-stu-id="71087-139">Metrics for Classification models</span></span>

<span data-ttu-id="71087-140">L’exemple suivant affiche la liste des métriques de classification pour les cinq principaux modèles trouvés par l’interface CLI :</span><span class="sxs-lookup"><span data-stu-id="71087-140">The following displays the classification metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

 <span data-ttu-id="71087-142">La précision est une mesure populaire pour les problèmes de classification, mais la précision n’est pas toujours la meilleure mesure pour sélectionner le meilleur modèle à partir de, comme expliqué dans les références suivantes.</span><span class="sxs-lookup"><span data-stu-id="71087-142">Accuracy is a popular metric for classification problems, however accuracy isn't always the best metric to select the best model from as explained in the following references.</span></span> <span data-ttu-id="71087-143">Dans certains cas, vous aurez besoin d’évaluer la qualité de votre modèle à l’aide d’autres métriques.</span><span class="sxs-lookup"><span data-stu-id="71087-143">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="71087-144">Pour explorer et comprendre les métriques générées par l’interface CLI, consultez [mesures d’évaluation pour la classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="71087-144">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for classification](resources/metrics.md#evaluation-metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-and-recommendation-models"></a><span data-ttu-id="71087-145">Métriques pour les modèles de régression et de recommandation</span><span class="sxs-lookup"><span data-stu-id="71087-145">Metrics for Regression and Recommendation models</span></span>

<span data-ttu-id="71087-146">Le modèle de régression est approprié dans les cas où les différences entre les valeurs observées et les valeurs prédites du modèle sont mineures et non biaisées.</span><span class="sxs-lookup"><span data-stu-id="71087-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="71087-147">La régression peut être évaluée avec des métriques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="71087-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="71087-148">Vous verrez une liste similaire de métriques pour les cinq meilleurs modèles de qualité trouvés par l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="71087-148">You'll see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="71087-149">Cas particulier concernant une tâche ML de régression :</span><span class="sxs-lookup"><span data-stu-id="71087-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="71087-151">Pour explorer et comprendre les métriques générées par l’interface CLI, consultez [mesures d’évaluation pour la régression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span><span class="sxs-lookup"><span data-stu-id="71087-151">To explore and understand the metrics that are output by the CLI, see [Evaluation metrics for regression](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).</span></span>

## <a name="see-also"></a><span data-ttu-id="71087-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71087-152">See also</span></span>

- [<span data-ttu-id="71087-153">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="71087-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="71087-154">Didacticiel : analyser le sentiment à l’aide de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="71087-154">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="71087-155">Informations de référence sur les commandes de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="71087-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="71087-156">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="71087-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
