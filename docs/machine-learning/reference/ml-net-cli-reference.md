---
title: Commande auto-train dans l’outil CLI ML.NET
description: Vue d’ensemble, exemples et informations de référence sur la commande auto-train dans l’outil CLI ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 73bae0165af76226152de322d2951086646a1a1d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397659"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a><span data-ttu-id="df17f-103">Commande « auto-train » dans l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="df17f-103">The 'auto-train' command in ML.NET CLI</span></span>

> [!NOTE]
> <span data-ttu-id="df17f-104">Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.</span><span class="sxs-lookup"><span data-stu-id="df17f-104">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="df17f-105">La commande `auto-train` est la commande principale fournie par l’outil CLI ML.NET.</span><span class="sxs-lookup"><span data-stu-id="df17f-105">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="df17f-106">Cette commande vous permet de générer un modèle ML.NET de bonne qualité (fichier .zip de modèle sérialisé) ainsi que l’exemple de code C# nécessaire pour exécuter et évaluer ce modèle.</span><span class="sxs-lookup"><span data-stu-id="df17f-106">The command allows you to generate a good quality ML.NET model (serialized model .zip file) plus the example C# code to run/score that model.</span></span> <span data-ttu-id="df17f-107">Le code C# utilisé pour créer et entraîner ce modèle est également généré. Vous pouvez alors effectuer des recherches sur l’algorithme et les paramètres qu’il utilise pour ce « meilleur modèle » généré.</span><span class="sxs-lookup"><span data-stu-id="df17f-107">In addition, the C# code to create/train that model is also generated for you to research what algorithm and settings it is using for that generated "best model".</span></span>

<span data-ttu-id="df17f-108">Vous pouvez générer ces ressources à partir de vos propres jeux de données sans avoir à coder quoi que ce soit. Vous gagnez ainsi en productivité, même si vous connaissez déjà ML.NET.</span><span class="sxs-lookup"><span data-stu-id="df17f-108">You can generate those assets from your own datasets without coding by yourself, so it also improves your productivity even if you already know ML.NET.</span></span>

<span data-ttu-id="df17f-109">La CLI ML.NET prend en charge les tâches de ML suivantes :</span><span class="sxs-lookup"><span data-stu-id="df17f-109">Currently, the ML Tasks supported by the ML.NET CLI are:</span></span>

- `binary-classification`
- `multiclass-classification`
- `regression`

- <span data-ttu-id="df17f-110">À l’avenir, elle prendra d’autres tâches de machine learning comme</span><span class="sxs-lookup"><span data-stu-id="df17f-110">Future: Other machine learning tasks, such as</span></span>
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

<span data-ttu-id="df17f-111">Exemple d’utilisation depuis l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="df17f-111">Example of usage on the command prompt:</span></span>

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="df17f-112">La commande `mlnet auto-train` génère les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="df17f-112">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="df17f-113">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="df17f-113">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="df17f-114">Le code C# nécessaire pour exécuter/évaluer ce modèle généré (et pour effectuer des prédictions dans vos applications utilisateur avec ce modèle).</span><span class="sxs-lookup"><span data-stu-id="df17f-114">C# code to run/score that generated model (To make predictions in your end-user apps with that model).</span></span>
- <span data-ttu-id="df17f-115">Le code C# comportant le code d’entraînement utilisé pour générer ce modèle (à des fins d’apprentissage).</span><span class="sxs-lookup"><span data-stu-id="df17f-115">C# code with the training code used to generate that model (Learning purposes).</span></span>

<span data-ttu-id="df17f-116">Les deux premières ressources peuvent être utilisées directement dans vos applications utilisateur (application web ASP.NET Core, services, application de bureau, etc.) pour effectuer des prédictions à l’aide de ce modèle ML généré.</span><span class="sxs-lookup"><span data-stu-id="df17f-116">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app, etc.) to make predictions with that generated ML model.</span></span>

<span data-ttu-id="df17f-117">La troisième ressource, le code d’entraînement, montre quel code de l’API ML.NET a été utilisé par l’interface CLI pour entraîner le modèle généré. Vous pouvez ainsi savoir quel entraîneur/algorithme et quels hyperparamètres spécifiques ont été sélectionnés par l’interface CLI et le moteur AutoML ML.NET.</span><span class="sxs-lookup"><span data-stu-id="df17f-117">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate what specific trainer/algorithm and hyper-parameters were selected by the CLI and the ML.NET AutoML engine.</span></span>

## <a name="the-auto-train-command-uses-the-automl-engine"></a><span data-ttu-id="df17f-118">La commande « auto-train » utilise le moteur AutoML</span><span class="sxs-lookup"><span data-stu-id="df17f-118">The 'auto-train' command uses the AutoML engine</span></span>

<span data-ttu-id="df17f-119">L’interface CLI utilise le moteur AutoML ML.NET (package NuGet) pour rechercher intelligemment les meilleurs modèles, comme le montre le diagramme suivant :</span><span class="sxs-lookup"><span data-stu-id="df17f-119">The CLI uses the ML.NET AutoML engine (NuGet package) to intelligently search for the best quality models, as shown in the following diagram:</span></span>

<span data-ttu-id="df17f-120">![image](./media/ml-net-automl-working-diagram.png "Fonctionnement du moteur AutoML dans la CLI ML.NET")</span><span class="sxs-lookup"><span data-stu-id="df17f-120">![image](./media/ml-net-automl-working-diagram.png "AutoML engine working inside the ML.NET CLI")</span></span>

<span data-ttu-id="df17f-121">Quand vous exécutez l’outil CLI ML.NET avec la commande « auto-train », il essaie de nombreuses itérations avec différents algorithmes et combinaisons de configuration.</span><span class="sxs-lookup"><span data-stu-id="df17f-121">When running the ML.NET CLI tool with the \`auto-train- command, you'll see the tool trying many iterations with different algorithms and combinations of configuration.</span></span>

## <a name="reference-for-auto-train-command"></a><span data-ttu-id="df17f-122">Informations de référence sur la commande « auto-train »</span><span class="sxs-lookup"><span data-stu-id="df17f-122">Reference for 'auto-train' command</span></span>

## <a name="examples"></a><span data-ttu-id="df17f-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="df17f-123">Examples</span></span>

<span data-ttu-id="df17f-124">Commande CLI la plus simple pour un problème de classification binaire (le moteur AutoML doit déduire la majeure partie de la configuration des données fournies) :</span><span class="sxs-lookup"><span data-stu-id="df17f-124">Simplest CLI command for a binary classification problem (AutoML will need to infer most of the configuration from the provided data):</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="df17f-125">Autre commande CLI simple pour un problème de régression :</span><span class="sxs-lookup"><span data-stu-id="df17f-125">Another simple CLI command for a regression problem:</span></span>

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="df17f-126">Créer et entraîner un modèle de classification binaire avec un jeu de données d’entraînement, un jeu de données de test et des arguments explicites de personnalisation supplémentaire :</span><span class="sxs-lookup"><span data-stu-id="df17f-126">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a><span data-ttu-id="df17f-127">Name</span><span class="sxs-lookup"><span data-stu-id="df17f-127">Name</span></span>

<span data-ttu-id="df17f-128">`mlnet auto-train` : entraîne plusieurs modèles (« n » itérations) en fonction du jeu de données fourni, puis sélectionne le meilleur modèle, l’enregistre dans un fichier .zip sérialisé et génère le code C# associé pour l’évaluation et l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df17f-128">`mlnet auto-train` - Trains multiple models ('n' iterations) based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

## <a name="synopsis"></a><span data-ttu-id="df17f-129">Résumé</span><span class="sxs-lookup"><span data-stu-id="df17f-129">Synopsis</span></span>

```console
> mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

<span data-ttu-id="df17f-130">Les options d’entrée non valides doivent amener l’outil CLI à émettre une liste d’entrées valides et un message d’erreur expliquant quel argument est éventuellement manquant.</span><span class="sxs-lookup"><span data-stu-id="df17f-130">Invalid input options should cause the CLI tool to emit a list of valid inputs and an error message explaining which arg is missing, if that is the case.</span></span>

## <a name="options"></a><span data-ttu-id="df17f-131">Options</span><span class="sxs-lookup"><span data-stu-id="df17f-131">Options</span></span>

 ----------------------------------------------------------

<span data-ttu-id="df17f-132">`--task | --mltask | -T` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-132">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="df17f-133">Simple chaîne fournissant le problème de ML à résoudre.</span><span class="sxs-lookup"><span data-stu-id="df17f-133">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="df17f-134">Par exemple, toutes les tâches suivantes (l’interface CLI est appelée à prendre en charge toutes les tâches prises en charge dans le moteur AutoML) :</span><span class="sxs-lookup"><span data-stu-id="df17f-134">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="df17f-135">`regression` : choisissez cette tâche si vous envisagez d’utiliser le modèle ML pour prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="df17f-135">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="df17f-136">`binary-classification` : choisissez cette tâche si le résultat du modèle ML a deux valeurs booléennes de catégorie possibles (0 ou 1).</span><span class="sxs-lookup"><span data-stu-id="df17f-136">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="df17f-137">`multiclass-classification` : choisissez cette tâche si le résultat du modèle ML a plusieurs valeurs de catégorie possibles.</span><span class="sxs-lookup"><span data-stu-id="df17f-137">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="df17f-138">Dans les versions futures, des tâches et scénarios de ML supplémentaires tels que `recommendations`, `clustering` et `ranking` seront pris en charge.</span><span class="sxs-lookup"><span data-stu-id="df17f-138">In future releases additional ML Tasks and scenarios such as `recommendations`, `clustering` and `ranking` will be supported.</span></span>

 <span data-ttu-id="df17f-139">Une seule tâche de ML doit être fournie dans cet argument.</span><span class="sxs-lookup"><span data-stu-id="df17f-139">Only one ML task should be provided in this argument.</span></span>

 ----------------------------------------------------------

<span data-ttu-id="df17f-140">`--dataset | -d` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-140">`--dataset | -d` (string)</span></span>

<span data-ttu-id="df17f-141">Cet argument fournit le chemin de l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="df17f-141">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="df17f-142">*A : le fichier de jeu de données entier :* si vous utilisez cette option et que l’utilisateur ne fournit pas `--test-dataset` et `--validation-dataset`, des approches de validation croisée (k sous-échantillon, etc.) ou de fractionnement automatisé des données sont utilisées en interne pour la validation du modèle.</span><span class="sxs-lookup"><span data-stu-id="df17f-142">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="df17f-143">Dans ce cas, l’utilisateur doit simplement fournir le chemin du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="df17f-143">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="df17f-144">*B : le fichier de jeu de données d’entraînement :* si l’utilisateur fournit également des jeux de données pour la validation du modèle (à l’aide de `--test-dataset` et éventuellement de `--validation-dataset`), l’argument `--dataset` revient à avoir uniquement le jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df17f-144">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="df17f-145">Par exemple, quand vous utilisez une approche 80 %-20 % pour valider la qualité du modèle et pour obtenir des métriques de précision, le « jeu de données d’entraînement » a 80 % des données, tandis que le « jeu de données de test » a 20 % des données.</span><span class="sxs-lookup"><span data-stu-id="df17f-145">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-146">`--test-dataset | -t` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-146">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="df17f-147">Chemin pointant vers le fichier de jeu de données de test, par exemple lors de l’utilisation d’une approche 80 %-20 % dans le cadre de validations régulières visant à obtenir des métriques de précision.</span><span class="sxs-lookup"><span data-stu-id="df17f-147">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="df17f-148">Si vous utilisez `--test-dataset`, `--dataset` est également requis.</span><span class="sxs-lookup"><span data-stu-id="df17f-148">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="df17f-149">L’argument `--test-dataset` est facultatif, sauf si l’option --validation-dataset est utilisée.</span><span class="sxs-lookup"><span data-stu-id="df17f-149">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="df17f-150">Dans ce cas, l’utilisateur doit recourir aux trois arguments.</span><span class="sxs-lookup"><span data-stu-id="df17f-150">In that case, the user must use the three arguments.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-151">`--validation-dataset | -v` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-151">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="df17f-152">Chemin pointant vers le fichier de jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="df17f-152">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="df17f-153">Le jeu de données de validation est toujours facultatif.</span><span class="sxs-lookup"><span data-stu-id="df17f-153">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="df17f-154">Si vous utilisez un `validation dataset`, le comportement doit être le suivant :</span><span class="sxs-lookup"><span data-stu-id="df17f-154">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="df17f-155">Les arguments `test-dataset` et `--dataset` sont également requis.</span><span class="sxs-lookup"><span data-stu-id="df17f-155">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="df17f-156">Le jeu de données `validation-dataset` est utilisé pour estimer l’erreur de prédiction pour la sélection de modèle.</span><span class="sxs-lookup"><span data-stu-id="df17f-156">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="df17f-157">`test-dataset` est utilisé pour l’évaluation de l’erreur de généralisation du dernier modèle choisi.</span><span class="sxs-lookup"><span data-stu-id="df17f-157">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="df17f-158">Dans l’idéal, le jeu de test doit être conservé dans un « coffre » et récupéré uniquement à la fin de l’analyse des données.</span><span class="sxs-lookup"><span data-stu-id="df17f-158">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="df17f-159">Quand vous utilisez un `validation dataset` ainsi que `test dataset`, la phase de validation est divisée en deux parties :</span><span class="sxs-lookup"><span data-stu-id="df17f-159">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="df17f-160">Dans la première partie, vous examinez simplement vos modèles et sélectionnez l’approche la plus performante en utilisant les données de validation (=validation)</span><span class="sxs-lookup"><span data-stu-id="df17f-160">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="df17f-161">Ensuite, vous estimez la précision de l’approche sélectionnée (= test).</span><span class="sxs-lookup"><span data-stu-id="df17f-161">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="df17f-162">Ainsi, la séparation des données peut être 80/10/10 ou 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="df17f-162">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="df17f-163">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="df17f-163">For example:</span></span>

- <span data-ttu-id="df17f-164">Le fichier `training-dataset` doit avoir 75 % des données.</span><span class="sxs-lookup"><span data-stu-id="df17f-164">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="df17f-165">Le fichier `validation-dataset` doit avoir 15 % des données.</span><span class="sxs-lookup"><span data-stu-id="df17f-165">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="df17f-166">Le fichier `test-dataset` doit avoir 10 % des données.</span><span class="sxs-lookup"><span data-stu-id="df17f-166">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="df17f-167">Dans tous les cas, ces pourcentages sont déterminés par l’utilisateur à l’aide de l’interface CLI, qui fournit les fichiers déjà fractionnés.</span><span class="sxs-lookup"><span data-stu-id="df17f-167">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-168">`--label-column-name | -n` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-168">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="df17f-169">Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant le nom de la colonne défini dans l’en-tête du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="df17f-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="df17f-170">Cet argument est utilisé uniquement pour les tâches de ML supervisées telles qu’un *problème de classification*.</span><span class="sxs-lookup"><span data-stu-id="df17f-170">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="df17f-171">Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.</span><span class="sxs-lookup"><span data-stu-id="df17f-171">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-172">`--label-column-index | -i` (entier)</span><span class="sxs-lookup"><span data-stu-id="df17f-172">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="df17f-173">Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 1).</span><span class="sxs-lookup"><span data-stu-id="df17f-173">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="df17f-174">*Remarque :* Si l’utilisateur recourt également à l’argument `--label-column-name`, c’est celui-ci qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="df17f-174">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="df17f-175">Cet argument est utilisé uniquement pour une tâche de ML supervisée telle qu’un *problème de classification*.</span><span class="sxs-lookup"><span data-stu-id="df17f-175">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="df17f-176">Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.</span><span class="sxs-lookup"><span data-stu-id="df17f-176">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-177">`--ignore-columns | -I` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-177">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="df17f-178">Avec cet argument, vous pouvez ignorer des colonnes existantes dans le fichier de jeu de données afin qu’elles ne soient pas chargées et utilisées par les processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df17f-178">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="df17f-179">Spécifiez les noms des colonnes que vous souhaitez ignorer.</span><span class="sxs-lookup"><span data-stu-id="df17f-179">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="df17f-180">Utilisez « ,  » (virgule avec espace) ou «   » (espace) pour séparer plusieurs noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="df17f-180">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="df17f-181">Vous pouvez utiliser des guillemets pour les noms de colonnes contenant des espaces (par exemple, "utilisateur connecté").</span><span class="sxs-lookup"><span data-stu-id="df17f-181">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="df17f-182">Exemple :</span><span class="sxs-lookup"><span data-stu-id="df17f-182">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

<span data-ttu-id="df17f-183">`--has-header | -h` (booléen)</span><span class="sxs-lookup"><span data-stu-id="df17f-183">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="df17f-184">Spécifiez si le ou les fichiers de jeu de données ont une ligne d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="df17f-184">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="df17f-185">Les valeurs possibles sont :</span><span class="sxs-lookup"><span data-stu-id="df17f-185">Possible values are:</span></span>
- `true`
- `false`

<span data-ttu-id="df17f-186">La valeur par défaut est `true` si cet argument n’est pas spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="df17f-186">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="df17f-187">Pour que l’argument `--label-column-name` puisse être utilisé, le fichier de jeu de données doit avoir un en-tête et `--has-header` doit être défini sur `true` (paramétrage par défaut).</span><span class="sxs-lookup"><span data-stu-id="df17f-187">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-188">`--max-exploration-time | -x` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-188">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="df17f-189">Par défaut, la durée maximale d’exploration est de 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="df17f-189">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="df17f-190">Cet argument définit la durée maximale (en secondes) dont dispose le processus pour explorer plusieurs entraîneurs et configurations.</span><span class="sxs-lookup"><span data-stu-id="df17f-190">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="df17f-191">La durée configurée peut être dépassée si la durée fournie est trop courte (par exemple, 2 secondes) pour une seule itération.</span><span class="sxs-lookup"><span data-stu-id="df17f-191">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="df17f-192">Dans ce cas, la durée réelle est le temps nécessaire pour produire une seule configuration de modèle dans une seule itération.</span><span class="sxs-lookup"><span data-stu-id="df17f-192">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="df17f-193">La durée nécessaire pour les itérations peut varier selon la taille du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="df17f-193">The needed time for iterations can vary depending on the size of the dataset.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-194">`--cache | -c` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="df17f-195">Si vous utilisez la mise en cache, le jeu de données d’entraînement entier est chargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="df17f-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="df17f-196">Pour les jeux de données petits et moyens, l’utilisation du cache peut considérablement améliorer les performances d’entraînement, ce qui signifie que la durée d’entraînement peut être plus courte que quand vous n’utilisez pas de cache.</span><span class="sxs-lookup"><span data-stu-id="df17f-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="df17f-197">Toutefois, pour les grands jeux de données, le chargement de toutes les données en mémoire peut avoir un impact négatif dans la mesure où vous risquez de manquer de mémoire.</span><span class="sxs-lookup"><span data-stu-id="df17f-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="df17f-198">Si vous effectuez un entraînement avec de grands fichiers de jeu de données sans utiliser de cache, ML.NET récupère des blocs de données du lecteur sous forme de flux s’il doit charger davantage de données.</span><span class="sxs-lookup"><span data-stu-id="df17f-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="df17f-199">Vous pouvez indiquer les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="df17f-199">You can specify the following values:</span></span>

<span data-ttu-id="df17f-200">`on`: impose l’utilisation du cache lors de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df17f-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="df17f-201">`off`: impose la non-utilisation du cache lors de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df17f-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="df17f-202">`auto`: selon l’heuristique du moteur AutoML, le cache est utilisé ou non.</span><span class="sxs-lookup"><span data-stu-id="df17f-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="df17f-203">En règle générale, si vous utilisez le choix `auto`, les jeux de données petits et moyens utilisent le cache, tandis que les grands jeux de données ne l’utilisent pas.</span><span class="sxs-lookup"><span data-stu-id="df17f-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="df17f-204">Si vous ne spécifiez pas le paramètre `--cache`, la configuration `auto` du cache est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="df17f-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-205">`--name | -N` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-205">`--name | -N` (string)</span></span>

<span data-ttu-id="df17f-206">Nom de la solution ou du projet de sortie créé.</span><span class="sxs-lookup"><span data-stu-id="df17f-206">The name for the created output project or solution.</span></span> <span data-ttu-id="df17f-207">Si aucun nom n’est spécifié, le nom `sample-{mltask}` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="df17f-207">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="df17f-208">Le fichier de modèle ML.NET (fichier .ZIP) reçoit également le même nom.</span><span class="sxs-lookup"><span data-stu-id="df17f-208">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-209">`--output-path | -o` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-209">`--output-path | -o` (string)</span></span>

<span data-ttu-id="df17f-210">Emplacement/dossier racine où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="df17f-210">Root location/folder to place the generated output.</span></span> <span data-ttu-id="df17f-211">La valeur par défaut correspond au répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="df17f-211">The default is the current directory.</span></span>

----------------------------------------------------------

<span data-ttu-id="df17f-212">`--verbosity | -V` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="df17f-212">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="df17f-213">Définit le niveau de détail de la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="df17f-213">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="df17f-214">Les valeurs autorisées sont :</span><span class="sxs-lookup"><span data-stu-id="df17f-214">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="df17f-215">`m[inimal]` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="df17f-215">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="df17f-216">`diag[nostic]` (niveau d’informations de journalisation)</span><span class="sxs-lookup"><span data-stu-id="df17f-216">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="df17f-217">Par défaut, l’outil CLI doit afficher un minimum de commentaires quand il fonctionne ; il doit par exemple indiquer qu’il fonctionne et, si possible, le temps restant ou le pourcentage de temps écoulé.</span><span class="sxs-lookup"><span data-stu-id="df17f-217">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

----------------------------------------------------------

`-h|--help`

<span data-ttu-id="df17f-218">Affiche l’aide de la commande avec une description de chacun de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="df17f-218">Prints out help for the command with a description for each command's parameter.</span></span>

----------------------------------------------------------

## <a name="see-also"></a><span data-ttu-id="df17f-219">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df17f-219">See also</span></span>

- [<span data-ttu-id="df17f-220">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="df17f-220">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="df17f-221">Automatiser l’entraînement du modèle avec la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="df17f-221">Automate model training with the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="df17f-222">Tutoriel : Générer automatiquement un classifieur binaire à l’aide de la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="df17f-222">Tutorial: Auto generate a binary classifier using the ML.NET CLI</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="df17f-223">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="df17f-223">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
