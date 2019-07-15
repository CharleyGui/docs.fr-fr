---
title: Automatiser l’entraînement du modèle avec l’interface CLI ML.NET
description: Découvrez comment utiliser l’outil CLI ML.NET pour entraîner automatiquement le meilleur modèle à partir de la ligne de commande.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663924"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a><span data-ttu-id="5099d-103">Automatiser l’entraînement du modèle avec l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="5099d-103">Automate model training with the ML.NET CLI</span></span>

<span data-ttu-id="5099d-104">L’interface CLI ML.NET « démocratise » ML.NET auprès des développeurs .NET qui débutent avec ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5099d-104">The ML.NET CLI "democratizes" ML.NET for .NET developers when learning ML.NET.</span></span>

<span data-ttu-id="5099d-105">Pour utiliser l’API ML.NET seule (c’est-à-dire sans l’interface CLI AutoML ML.NET), vous devez choisir un entraîneur (implémentation d’un algorithme de machine learning pour une tâche particulière) ainsi que l’ensemble des transformations de données (ingénierie des caractéristiques) à appliquer à vos données.</span><span class="sxs-lookup"><span data-stu-id="5099d-105">To use the ML.NET API by itself, (without the ML.NET AutoML CLI) you need to choose a trainer (implementation of a machine learning algorithm for a particular task), and the set of data transformations (feature engineering) to apply to your data.</span></span> <span data-ttu-id="5099d-106">Le pipeline optimal varie en fonction de chaque jeu de données, et choisir l’algorithme optimal parmi toutes les options possibles accroît encore la complexité.</span><span class="sxs-lookup"><span data-stu-id="5099d-106">The optimal pipeline will vary for each dataset and selecting the optimal algorithm from all the choices adds to the complexity.</span></span> <span data-ttu-id="5099d-107">De plus, chaque algorithme est associé à un ensemble d’hyperparamètres que vous devez régler.</span><span class="sxs-lookup"><span data-stu-id="5099d-107">Even further, each algorithm has a set of hyperparameters to be tuned.</span></span> <span data-ttu-id="5099d-108">Bref, vous pouvez passer des semaines et parfois plusieurs mois à optimiser le modèle Machine Learning pour essayer de trouver les meilleures combinaisons possibles entre l’ingénierie des caractéristiques, les algorithmes d’apprentissage et les hyperparamètres.</span><span class="sxs-lookup"><span data-stu-id="5099d-108">Hence, you can spend weeks and sometimes months on machine learning model optimization trying to find the best combinations of feature engineering, learning algorithms, and hyperparameters.</span></span>

<span data-ttu-id="5099d-109">Heureusement, ce processus peut être automatisé avec l’interface CLI ML.NET, qui implémente le moteur intelligent AutoML ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5099d-109">This process can be automated with the ML.NET CLI, which implements the ML.NET AutoML intelligent engine.</span></span>

> [!NOTE]
> <span data-ttu-id="5099d-110">Cette rubrique fait référence à l’interface **CLI** ML.NET et au moteur **AutoML** ML.NET, qui sont actuellement en préversion et donc susceptibles d’être modifiés.</span><span class="sxs-lookup"><span data-stu-id="5099d-110">This topic refers to ML.NET **CLI** and ML.NET **AutoML**, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="what-is-the-mlnet-command-line-interface-cli"></a><span data-ttu-id="5099d-111">Présentation de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="5099d-111">What is the ML.NET Command-line Interface (CLI)?</span></span>

<span data-ttu-id="5099d-112">Vous pouvez exécuter l’interface CLI ML.NET à partir de n’importe quelle invite de commandes (Windows, Mac ou Linux) et générer ensuite des modèles ML.NET et du code source de qualité sur la base de votre jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="5099d-112">You can run the ML.NET CLI on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on your training dataset.</span></span>

<span data-ttu-id="5099d-113">Comme le montre l’illustration ci-dessous, vous pouvez facilement générer un modèle ML.NET de grande qualité (fichier .zip de modèle sérialisé) ainsi que le code C# nécessaire pour exécuter et évaluer ce modèle.</span><span class="sxs-lookup"><span data-stu-id="5099d-113">As shown in the figure below, it is simple to generate a high quality ML.NET model (serialized model .zip file) plus the sample C# code to run/score that model.</span></span> <span data-ttu-id="5099d-114">Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches et des itérations sur l’algorithme et les paramètres appliqués pour ce « meilleur modèle » généré.</span><span class="sxs-lookup"><span data-stu-id="5099d-114">In addition, the C# code to create/train that model is also generated, so that you can research and iterate on the algorithm and settings used for that generated "best model".</span></span>

<span data-ttu-id="5099d-115">![image](media/automate-training-with-cli/cli-high-level-process.png "Fonctionnement du moteur AutoML dans la CLI ML.NET")</span><span class="sxs-lookup"><span data-stu-id="5099d-115">![image](media/automate-training-with-cli/cli-high-level-process.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="5099d-116">Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.</span><span class="sxs-lookup"><span data-stu-id="5099d-116">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="5099d-117">Actuellement, l’interface CLI ML.NET prend en charge les tâches ML suivantes :</span><span class="sxs-lookup"><span data-stu-id="5099d-117">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`
- <span data-ttu-id="5099d-118">À l’avenir, elle prendra d’autres tâches de machine learning comme `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span><span class="sxs-lookup"><span data-stu-id="5099d-118">Future: other machine learning tasks such as `recommendation`, `ranking`, `anomaly-detection`, `clustering`</span></span>

<span data-ttu-id="5099d-119">Exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="5099d-119">Example of usage:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

<span data-ttu-id="5099d-121">Vous pouvez exécuter cette commande de la même façon sur *Windows PowerShell*, \*macOS/Linux Bash ou *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="5099d-121">You can run it the same way on *Windows PowerShell*, \*macOS/Linux bash, or *Windows CMD*.</span></span> <span data-ttu-id="5099d-122">Toutefois, l’autocomplétion via la touche tab (suggestions de paramètres) ne fonctionne pas sur *Windows CMD*.</span><span class="sxs-lookup"><span data-stu-id="5099d-122">However, tabular auto-completion (parameter suggestions) won't work on *Windows CMD*.</span></span>

## <a name="output-assets-generated"></a><span data-ttu-id="5099d-123">Ressources générées en sortie</span><span class="sxs-lookup"><span data-stu-id="5099d-123">Output assets generated</span></span>

<span data-ttu-id="5099d-124">La commande `auto-train` de l’interface CLI génère les ressources suivantes dans le dossier de sortie :</span><span class="sxs-lookup"><span data-stu-id="5099d-124">The CLI `auto-train` command generates the following assets in the output folder:</span></span>

- <span data-ttu-id="5099d-125">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé pour effectuer des prédictions.</span><span class="sxs-lookup"><span data-stu-id="5099d-125">A serialized model .zip ("best model") ready to use for running predictions.</span></span>
- <span data-ttu-id="5099d-126">Une solution C# contenant :</span><span class="sxs-lookup"><span data-stu-id="5099d-126">C# solution with:</span></span>
  - <span data-ttu-id="5099d-127">Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).</span><span class="sxs-lookup"><span data-stu-id="5099d-127">C# code to run/score that generated model (to make predictions in your end-user apps with that model).</span></span>
  - <span data-ttu-id="5099d-128">Le code C# avec le code d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage ou de réentraînement du modèle).</span><span class="sxs-lookup"><span data-stu-id="5099d-128">C# code with the training code used to generate that model (for learning purposes or model retraining).</span></span>
- <span data-ttu-id="5099d-129">Un fichier journal contenant des informations sur l’ensemble des itérations/balayages effectués sur tous les algorithmes évalués, y compris les détails de leur pipeline/configuration.</span><span class="sxs-lookup"><span data-stu-id="5099d-129">Log file with information of all iterations/sweeps across the multiple algorithms evaluated, including their detailed configuration/pipeline.</span></span>

<span data-ttu-id="5099d-130">Les deux premières ressources peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.</span><span class="sxs-lookup"><span data-stu-id="5099d-130">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="5099d-131">La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par l’interface CLI pour entraîner le modèle généré. Vous pouvez alors réentraîner votre modèle et effectuer des recherches/itérations sur l’entraîneur/algorithme et les hyperparamètres spécifiques qui avaient été automatiquement sélectionnés par l’interface CLI et AutoML.</span><span class="sxs-lookup"><span data-stu-id="5099d-131">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can retrain your model and investigate and iterate on which specific trainer/algorithm and hyperparameters were selected by the CLI and AutoML under the covers.</span></span>

## <a name="understanding-the-quality-of-the-model"></a><span data-ttu-id="5099d-132">Déterminer la qualité du modèle</span><span class="sxs-lookup"><span data-stu-id="5099d-132">Understanding the quality of the model</span></span>

<span data-ttu-id="5099d-133">Quand vous générez un « meilleur modèle » avec l’outil CLI, vous voyez des métriques de qualité (telles que la précision et le coefficient de détermination) relatives à la tâche ML que vous ciblez.</span><span class="sxs-lookup"><span data-stu-id="5099d-133">When you generate a 'best model' with the CLI tool, you see quality metrics (such as accuracy, and R-Squared) as appropriate for the ML task you are targeting.</span></span>

<span data-ttu-id="5099d-134">Nous récapitulons ci-après toutes ces métriques par type de tâche ML, qui vous permettront de déterminer la qualité de votre « meilleur modèle » généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="5099d-134">Here we summarize those metrics grouped by ML task so you can understand the quality of your auto-generated 'best model'.</span></span>

### <a name="metrics-for-binary-classification-models"></a><span data-ttu-id="5099d-135">Métriques pour les modèles de classification binaire</span><span class="sxs-lookup"><span data-stu-id="5099d-135">Metrics for Binary Classification models</span></span>

<span data-ttu-id="5099d-136">La capture d’écran suivante liste les métriques des tâches ML de classification binaire pour les cinq meilleurs modèles trouvés par l’outil CLI :</span><span class="sxs-lookup"><span data-stu-id="5099d-136">The following displays the binary classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

<span data-ttu-id="5099d-138">La précision (Accuracy) est une métrique couramment employée pour les problèmes de classification, mais elle ne constitue pas toujours la métrique la plus adaptée pour choisir le meilleur modèle, comme cela est expliqué dans la rubrique indiquée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="5099d-138">Accuracy is a popular metric for classification problems, however accuracy is not always the best metric to select the best model from as explained in the references below.</span></span> <span data-ttu-id="5099d-139">Dans certains cas, vous aurez besoin d’évaluer la qualité de votre modèle à l’aide d’autres métriques.</span><span class="sxs-lookup"><span data-stu-id="5099d-139">There are cases where you need to evaluate the quality of your model with additional metrics.</span></span>

<span data-ttu-id="5099d-140">Pour explorer et comprendre toutes les métriques fournies par l’outil CLI, consultez [Métriques pour la classification binaire](resources/metrics.md#metrics-for-binary-classification).</span><span class="sxs-lookup"><span data-stu-id="5099d-140">To explore and understand the metrics that are output by the CLI, see [Metrics for binary classification](resources/metrics.md#metrics-for-binary-classification).</span></span>

### <a name="metrics-for-multi-class-classification-models"></a><span data-ttu-id="5099d-141">Métriques pour les modèles de classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="5099d-141">Metrics for Multi-class Classification models</span></span>

<span data-ttu-id="5099d-142">La capture d’écran suivante liste les métriques des tâches ML de classification multiclasse pour les cinq meilleurs modèles trouvés par l’outil CLI :</span><span class="sxs-lookup"><span data-stu-id="5099d-142">The following displays the multi-class classification ML task metrics list for the top five models found by the CLI:</span></span>

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

<span data-ttu-id="5099d-144">Pour explorer et comprendre toutes les métriques fournies par l’outil CLI, consultez [Métriques pour la classification multiclasse](resources/metrics.md#metrics-for-multi-class-classification).</span><span class="sxs-lookup"><span data-stu-id="5099d-144">To explore and understand the metrics that are output by the CLI, see [Metrics for multiclass classification](resources/metrics.md#metrics-for-multi-class-classification).</span></span>

### <a name="metrics-for-regression-models"></a><span data-ttu-id="5099d-145">Métriques pour les modèles de régression</span><span class="sxs-lookup"><span data-stu-id="5099d-145">Metrics for Regression models</span></span>

<span data-ttu-id="5099d-146">Le modèle de régression est approprié dans les cas où les différences entre les valeurs observées et les valeurs prédites du modèle sont mineures et non biaisées.</span><span class="sxs-lookup"><span data-stu-id="5099d-146">A regression model fits the data well if the differences between the observed values and the model's predicted values are small and unbiased.</span></span> <span data-ttu-id="5099d-147">La régression peut être évaluée avec des métriques spécifiques.</span><span class="sxs-lookup"><span data-stu-id="5099d-147">Regression can be evaluated with certain metrics.</span></span>

<span data-ttu-id="5099d-148">Vous verrez une liste similaire de métriques pour les cinq meilleurs modèles trouvés par l’outil CLI.</span><span class="sxs-lookup"><span data-stu-id="5099d-148">You will see a similar list of metrics for the best top five quality models found by the CLI.</span></span> <span data-ttu-id="5099d-149">Cas particulier concernant une tâche ML de régression :</span><span class="sxs-lookup"><span data-stu-id="5099d-149">In this particular case related to a regression ML task:</span></span>

![image](media/automate-training-with-cli/cli-regression-metrics.png)

<span data-ttu-id="5099d-151">Pour explorer et comprendre toutes les métriques fournies par l’outil CLI, consultez [Métriques pour la régression](resources/metrics.md#metrics-for-regression).</span><span class="sxs-lookup"><span data-stu-id="5099d-151">To explore and understand the metrics that are output by the CLI, see [Metrics for regression](resources/metrics.md#metrics-for-regression).</span></span>

## <a name="see-also"></a><span data-ttu-id="5099d-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5099d-152">See also</span></span>

- [<span data-ttu-id="5099d-153">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="5099d-153">How to install the ML.NET CLI tool</span></span>](how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="5099d-154">Tutoriel : Générer automatiquement un classifieur binaire à l’aide de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="5099d-154">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](tutorials/mlnet-cli.md)
- [<span data-ttu-id="5099d-155">Informations de référence sur les commandes de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="5099d-155">ML.NET CLI command reference</span></span>](reference/ml-net-cli-reference.md)
- [<span data-ttu-id="5099d-156">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="5099d-156">Telemetry in ML.NET CLI</span></span>](resources/ml-net-cli-telemetry.md)
