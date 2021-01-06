---
title: Informations de référence sur les commandes CLI ML.NET
description: Vue d’ensemble, exemples et informations de référence sur la commande auto-train dans l’outil CLI ML.NET.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 6f07cd8b4237f8931bbc0ec97bc0bbe18c488f16
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856066"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="e30e2-103">Informations de référence sur la commande CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="e30e2-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="e30e2-104">Les `classification` `regression` commandes, et `recommendation` sont les principales commandes fournies par l’outil CLI ml.net.</span><span class="sxs-lookup"><span data-stu-id="e30e2-104">The `classification`, `regression`, and `recommendation` commands are the main commands provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="e30e2-105">Ces commandes vous permettent de générer des modèles ML.NET de bonne qualité pour la classification, la régression et les modèles de recommandation à l’aide d’Machine Learning automatisés (AutoML), ainsi que l’exemple de code C# pour exécuter/noter ce modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-105">These commands allow you to generate good quality ML.NET models for classification, regression, and recommendation models using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="e30e2-106">En outre, le code C# pour l’apprentissage du modèle est généré pour vous afin de Rechercher l’algorithme et les paramètres du modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="e30e2-107">Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.</span><span class="sxs-lookup"><span data-stu-id="e30e2-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="e30e2-108">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="e30e2-108">Overview</span></span>

<span data-ttu-id="e30e2-109">Exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="e30e2-109">Example usage:</span></span>

```console
mlnet regression --dataset "cars.csv" --label-col price
```

<span data-ttu-id="e30e2-110">Les `mlnet` commandes de tâche ml ( `classification` , `regression` et `recommendation` ) génèrent les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="e30e2-110">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) generate the following assets:</span></span>

- <span data-ttu-id="e30e2-111">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="e30e2-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="e30e2-112">Code C# pour exécuter/noter le modèle généré.</span><span class="sxs-lookup"><span data-stu-id="e30e2-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="e30e2-113">Code C# avec le code d’apprentissage utilisé pour générer ce modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="e30e2-114">Les deux premières ressources peuvent être utilisées directement dans vos applications d’utilisateur final (ASP.NET Core application Web, services, application de bureau, etc.) pour faire des prédictions avec le modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="e30e2-115">La troisième ressource, le code de formation, vous montre le code de l’API ML.NET utilisé par l’interface CLI pour former le modèle généré, ce qui vous permet d’examiner l’algorithme et les paramètres spécifiques du modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="e30e2-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="e30e2-116">Examples</span></span>

<span data-ttu-id="e30e2-117">La commande CLI la plus simple pour un problème de classification (AutoML déduit la majeure partie de la configuration à partir des données fournies) :</span><span class="sxs-lookup"><span data-stu-id="e30e2-117">The simplest CLI command for a classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

<span data-ttu-id="e30e2-118">Autre commande CLI simple pour un problème de régression :</span><span class="sxs-lookup"><span data-stu-id="e30e2-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

<span data-ttu-id="e30e2-119">Créer et effectuer l’apprentissage d’un modèle de classification avec un jeu de données de formation, un jeu de données de test et d’autres arguments explicites de personnalisation :</span><span class="sxs-lookup"><span data-stu-id="e30e2-119">Create and train a classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a><span data-ttu-id="e30e2-120">Options de commande</span><span class="sxs-lookup"><span data-stu-id="e30e2-120">Command options</span></span>

<span data-ttu-id="e30e2-121">Les `mlnet` commandes de tâche ml ( `classification` , `regression` et `recommendation` ) entraînent plusieurs modèles en fonction du jeu de données fourni et des options de l’interface CLI ml.net.</span><span class="sxs-lookup"><span data-stu-id="e30e2-121">The `mlnet` ML task commands (`classification`, `regression`, and `recommendation`) train multiple models based on the provided dataset and ML.NET CLI options.</span></span> <span data-ttu-id="e30e2-122">Ces commandes sélectionnent également le meilleur modèle, enregistrent le modèle sous forme de fichier. zip sérialisé et génèrent le code C# associé pour la notation et l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="e30e2-122">These commands also select the best model, save the model as a serialized .zip file, and generate related C# code for scoring and training.</span></span>

### <a name="classification-options"></a><span data-ttu-id="e30e2-123">Options de classification</span><span class="sxs-lookup"><span data-stu-id="e30e2-123">Classification options</span></span>

<span data-ttu-id="e30e2-124">L’exécution `mlnet classification` de entraîne l’apprentissage d’un modèle de classification.</span><span class="sxs-lookup"><span data-stu-id="e30e2-124">Running `mlnet classification` will train a classification model.</span></span> <span data-ttu-id="e30e2-125">Choisissez cette commande si vous souhaitez qu’un modèle ML classe les données dans au moins deux classes (par exemple, l’analyse des sentiments).</span><span class="sxs-lookup"><span data-stu-id="e30e2-125">Choose this command if you want an ML Model to categorize data into 2 or more classes (e.g. sentiment analysis).</span></span>

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a><span data-ttu-id="e30e2-126">Options de régression</span><span class="sxs-lookup"><span data-stu-id="e30e2-126">Regression options</span></span>

<span data-ttu-id="e30e2-127">L’exécution `mlnet regression` entraîne l’apprentissage d’un modèle de régression.</span><span class="sxs-lookup"><span data-stu-id="e30e2-127">Running `mlnet regression` will train a regression model.</span></span> <span data-ttu-id="e30e2-128">Choisissez cette commande si vous souhaitez qu’un modèle ML prédise une valeur numérique (par exemple, la prédiction de prix).</span><span class="sxs-lookup"><span data-stu-id="e30e2-128">Choose this command if you want an ML Model to predict a numeric value (e.g. price prediction).</span></span>

```console
mlnet regression

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a><span data-ttu-id="e30e2-129">Options de recommandation</span><span class="sxs-lookup"><span data-stu-id="e30e2-129">Recommendation options</span></span>

<span data-ttu-id="e30e2-130">L’exécution `mlnet recommendation` entraîne l’apprentissage d’un modèle de recommandation.</span><span class="sxs-lookup"><span data-stu-id="e30e2-130">Running `mlnet recommendation` will train a recommendation model.</span></span>  <span data-ttu-id="e30e2-131">Choisissez cette commande si vous souhaitez qu’un modèle ML recommande des éléments aux utilisateurs en fonction des évaluations (par exemple, recommandation du produit).</span><span class="sxs-lookup"><span data-stu-id="e30e2-131">Choose this command if you want an ML Model to recommend items to users based on ratings (e.g. product recommendation).</span></span>

```console
mlnet recommendation

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

<span data-ttu-id="e30e2-132">Les options d’entrée non valides entraînent l’émission par l’outil CLI d’une liste d’entrées valides et d’un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e30e2-132">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="dataset"></a><span data-ttu-id="e30e2-133">Dataset</span><span class="sxs-lookup"><span data-stu-id="e30e2-133">Dataset</span></span>

<span data-ttu-id="e30e2-134">`--dataset | -d` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-134">`--dataset | -d` (string)</span></span>

<span data-ttu-id="e30e2-135">Cet argument fournit le chemin de l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="e30e2-135">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="e30e2-136">*R : l’intégralité du fichier de jeu de données :* Si vous utilisez cette option et que l’utilisateur ne fournit pas `--test-dataset` et `--validation-dataset` , la validation croisée (RepList, etc.) ou les approches de fractionnement automatique des données sont utilisées en interne pour valider le modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-136">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="e30e2-137">Dans ce cas, l’utilisateur doit simplement fournir le chemin du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-137">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="e30e2-138">*B : fichier de jeu de données d’apprentissage :* Si l’utilisateur fournit également des jeux de données pour la validation de modèle (à l’aide `--test-dataset` de et éventuellement `--validation-dataset` ), l' `--dataset` argument signifie uniquement que « jeu de données d’apprentissage ».</span><span class="sxs-lookup"><span data-stu-id="e30e2-138">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="e30e2-139">Par exemple, quand vous utilisez une approche 80 %-20 % pour valider la qualité du modèle et pour obtenir des métriques de précision, le « jeu de données d’entraînement » a 80 % des données, tandis que le « jeu de données de test » a 20 % des données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-139">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="e30e2-140">Jeu de données de test</span><span class="sxs-lookup"><span data-stu-id="e30e2-140">Test dataset</span></span>

<span data-ttu-id="e30e2-141">`--test-dataset | -t` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-141">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="e30e2-142">Chemin pointant vers le fichier de jeu de données de test, par exemple lors de l’utilisation d’une approche 80 %-20 % dans le cadre de validations régulières visant à obtenir des métriques de précision.</span><span class="sxs-lookup"><span data-stu-id="e30e2-142">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="e30e2-143">Si vous utilisez `--test-dataset`, `--dataset` est également requis.</span><span class="sxs-lookup"><span data-stu-id="e30e2-143">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="e30e2-144">L’argument `--test-dataset` est facultatif, sauf si l’option --validation-dataset est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e30e2-144">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="e30e2-145">Dans ce cas, l’utilisateur doit recourir aux trois arguments.</span><span class="sxs-lookup"><span data-stu-id="e30e2-145">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="e30e2-146">Jeu de données de validation</span><span class="sxs-lookup"><span data-stu-id="e30e2-146">Validation dataset</span></span>

<span data-ttu-id="e30e2-147">`--validation-dataset | -v` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-147">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="e30e2-148">Chemin pointant vers le fichier de jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="e30e2-148">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="e30e2-149">Le jeu de données de validation est toujours facultatif.</span><span class="sxs-lookup"><span data-stu-id="e30e2-149">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="e30e2-150">Si vous utilisez un `validation dataset`, le comportement doit être le suivant :</span><span class="sxs-lookup"><span data-stu-id="e30e2-150">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="e30e2-151">Les arguments `test-dataset` et `--dataset` sont également requis.</span><span class="sxs-lookup"><span data-stu-id="e30e2-151">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="e30e2-152">Le jeu de données `validation-dataset` est utilisé pour estimer l’erreur de prédiction pour la sélection de modèle.</span><span class="sxs-lookup"><span data-stu-id="e30e2-152">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="e30e2-153">`test-dataset` est utilisé pour l’évaluation de l’erreur de généralisation du dernier modèle choisi.</span><span class="sxs-lookup"><span data-stu-id="e30e2-153">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="e30e2-154">Dans l’idéal, le jeu de test doit être conservé dans un « coffre » et récupéré uniquement à la fin de l’analyse des données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-154">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="e30e2-155">Quand vous utilisez un `validation dataset` ainsi que `test dataset`, la phase de validation est divisée en deux parties :</span><span class="sxs-lookup"><span data-stu-id="e30e2-155">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="e30e2-156">Dans la première partie, vous examinez simplement vos modèles et sélectionnez l’approche la plus performante en utilisant les données de validation (=validation)</span><span class="sxs-lookup"><span data-stu-id="e30e2-156">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="e30e2-157">Ensuite, vous estimez la précision de l’approche sélectionnée (= test).</span><span class="sxs-lookup"><span data-stu-id="e30e2-157">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="e30e2-158">Ainsi, la séparation des données peut être 80/10/10 ou 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="e30e2-158">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="e30e2-159">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e30e2-159">For example:</span></span>

- <span data-ttu-id="e30e2-160">Le fichier `training-dataset` doit avoir 75 % des données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-160">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="e30e2-161">Le fichier `validation-dataset` doit avoir 15 % des données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-161">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="e30e2-162">Le fichier `test-dataset` doit avoir 10 % des données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-162">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="e30e2-163">Dans tous les cas, ces pourcentages sont déterminés par l’utilisateur à l’aide de l’interface CLI, qui fournit les fichiers déjà fractionnés.</span><span class="sxs-lookup"><span data-stu-id="e30e2-163">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column"></a><span data-ttu-id="e30e2-164">Colonne d'étiquette</span><span class="sxs-lookup"><span data-stu-id="e30e2-164">Label column</span></span>

<span data-ttu-id="e30e2-165">`--label-col` (int ou String)</span><span class="sxs-lookup"><span data-stu-id="e30e2-165">`--label-col` (int or string)</span></span>

<span data-ttu-id="e30e2-166">Avec cet argument, vous pouvez spécifier une colonne objective/Target (la variable que vous souhaitez prédire) à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).</span><span class="sxs-lookup"><span data-stu-id="e30e2-166">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e30e2-167">Cet argument est utilisé pour les problèmes de *classification* et de *régression* .</span><span class="sxs-lookup"><span data-stu-id="e30e2-167">This argument is used for *classification* and *regression* problems.</span></span>

## <a name="item-column"></a><span data-ttu-id="e30e2-168">Colonne d’élément</span><span class="sxs-lookup"><span data-stu-id="e30e2-168">Item column</span></span>

<span data-ttu-id="e30e2-169">`--item-col` (int ou String)</span><span class="sxs-lookup"><span data-stu-id="e30e2-169">`--item-col` (int or string)</span></span>

<span data-ttu-id="e30e2-170">La colonne élément contient la liste des éléments que les utilisateurs évaluent (les éléments sont recommandés pour les utilisateurs).</span><span class="sxs-lookup"><span data-stu-id="e30e2-170">The item column has the list of items that users rate (items are recommended to users).</span></span> <span data-ttu-id="e30e2-171">Cette colonne peut être spécifiée à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).</span><span class="sxs-lookup"><span data-stu-id="e30e2-171">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e30e2-172">Cet argument est utilisé uniquement pour la tâche de *recommandation* .</span><span class="sxs-lookup"><span data-stu-id="e30e2-172">This argument is used only for the *recommendation* task.</span></span>

## <a name="rating-column"></a><span data-ttu-id="e30e2-173">Colonne d’évaluation</span><span class="sxs-lookup"><span data-stu-id="e30e2-173">Rating column</span></span>

<span data-ttu-id="e30e2-174">`--rating-col` (int ou String)</span><span class="sxs-lookup"><span data-stu-id="e30e2-174">`--rating-col` (int or string)</span></span>

<span data-ttu-id="e30e2-175">La colonne évaluation contient la liste des évaluations accordées aux éléments par les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e30e2-175">The rating column has the list of ratings that are given to items by users.</span></span> <span data-ttu-id="e30e2-176">Cette colonne peut être spécifiée à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).</span><span class="sxs-lookup"><span data-stu-id="e30e2-176">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e30e2-177">Cet argument est utilisé uniquement pour la tâche de *recommandation* .</span><span class="sxs-lookup"><span data-stu-id="e30e2-177">This argument is used only for the *recommendation* task.</span></span>

## <a name="user-column"></a><span data-ttu-id="e30e2-178">Colonne de l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="e30e2-178">User column</span></span>

<span data-ttu-id="e30e2-179">`--user-col` (int ou String)</span><span class="sxs-lookup"><span data-stu-id="e30e2-179">`--user-col` (int or string)</span></span>

<span data-ttu-id="e30e2-180">La colonne utilisateur contient la liste des utilisateurs qui attribuent des évaluations aux éléments.</span><span class="sxs-lookup"><span data-stu-id="e30e2-180">The user column has the list of users that give ratings to items.</span></span> <span data-ttu-id="e30e2-181">Cette colonne peut être spécifiée à l’aide du nom de la colonne défini dans l’en-tête du DataSet ou de l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 0).</span><span class="sxs-lookup"><span data-stu-id="e30e2-181">This column can be specified by using the column's name set in the dataset's header or the column's numeric index in the dataset's file (the column index values start at 0).</span></span>

<span data-ttu-id="e30e2-182">Cet argument est utilisé uniquement pour la tâche de *recommandation* .</span><span class="sxs-lookup"><span data-stu-id="e30e2-182">This argument is used only for the *recommendation* task.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="e30e2-183">Ignorer les colonnes</span><span class="sxs-lookup"><span data-stu-id="e30e2-183">Ignore columns</span></span>

<span data-ttu-id="e30e2-184">`--ignore-columns` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-184">`--ignore-columns` (string)</span></span>

<span data-ttu-id="e30e2-185">Avec cet argument, vous pouvez ignorer des colonnes existantes dans le fichier de jeu de données afin qu’elles ne soient pas chargées et utilisées par les processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="e30e2-185">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="e30e2-186">Spécifiez les noms des colonnes que vous souhaitez ignorer.</span><span class="sxs-lookup"><span data-stu-id="e30e2-186">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="e30e2-187">Utilisez « ,  » (virgule avec espace) ou «   » (espace) pour séparer plusieurs noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="e30e2-187">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="e30e2-188">Vous pouvez utiliser des guillemets pour les noms de colonnes contenant des espaces (par exemple, "utilisateur connecté").</span><span class="sxs-lookup"><span data-stu-id="e30e2-188">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="e30e2-189">Exemple :</span><span class="sxs-lookup"><span data-stu-id="e30e2-189">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="e30e2-190">A un en-tête</span><span class="sxs-lookup"><span data-stu-id="e30e2-190">Has header</span></span>

<span data-ttu-id="e30e2-191">`--has-header` (booléen)</span><span class="sxs-lookup"><span data-stu-id="e30e2-191">`--has-header` (bool)</span></span>

<span data-ttu-id="e30e2-192">Spécifiez si le ou les fichiers de jeu de données ont une ligne d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="e30e2-192">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="e30e2-193">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e30e2-193">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="e30e2-194">L’interface CLI ML.NET essaiera de détecter cette propriété si cet argument n’est pas spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e30e2-194">The ML.NET CLI will try to detect this property if this argument is not specified by the user.</span></span>

## <a name="train-time"></a><span data-ttu-id="e30e2-195">Temps de formation</span><span class="sxs-lookup"><span data-stu-id="e30e2-195">Train time</span></span>

<span data-ttu-id="e30e2-196">`--train-time` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-196">`--train-time` (string)</span></span>

<span data-ttu-id="e30e2-197">Par défaut, la durée maximale d’exploration/formation est de 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="e30e2-197">By default, the maximum exploration / train time is 30 minutes.</span></span>

<span data-ttu-id="e30e2-198">Cet argument définit la durée maximale (en secondes) dont dispose le processus pour explorer plusieurs entraîneurs et configurations.</span><span class="sxs-lookup"><span data-stu-id="e30e2-198">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="e30e2-199">La durée configurée peut être dépassée si la durée fournie est trop courte (par exemple, 2 secondes) pour une seule itération.</span><span class="sxs-lookup"><span data-stu-id="e30e2-199">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="e30e2-200">Dans ce cas, la durée réelle est le temps nécessaire pour produire une seule configuration de modèle dans une seule itération.</span><span class="sxs-lookup"><span data-stu-id="e30e2-200">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="e30e2-201">La durée nécessaire pour les itérations peut varier selon la taille du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-201">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="e30e2-202">Cache</span><span class="sxs-lookup"><span data-stu-id="e30e2-202">Cache</span></span>

<span data-ttu-id="e30e2-203">`--cache` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-203">`--cache` (string)</span></span>

<span data-ttu-id="e30e2-204">Si vous utilisez la mise en cache, le jeu de données d’entraînement entier est chargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="e30e2-204">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="e30e2-205">Pour les jeux de données petits et moyens, l’utilisation du cache peut considérablement améliorer les performances d’entraînement, ce qui signifie que la durée d’entraînement peut être plus courte que quand vous n’utilisez pas de cache.</span><span class="sxs-lookup"><span data-stu-id="e30e2-205">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="e30e2-206">Toutefois, pour les grands jeux de données, le chargement de toutes les données en mémoire peut avoir un impact négatif dans la mesure où vous risquez de manquer de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e30e2-206">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="e30e2-207">Si vous effectuez un entraînement avec de grands fichiers de jeu de données sans utiliser de cache, ML.NET récupère des blocs de données du lecteur sous forme de flux s’il doit charger davantage de données.</span><span class="sxs-lookup"><span data-stu-id="e30e2-207">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="e30e2-208">Vous pouvez spécifier les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="e30e2-208">You can specify the following values:</span></span>

<span data-ttu-id="e30e2-209">`on`: Force l’utilisation du cache lors de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="e30e2-209">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="e30e2-210">`off`: Force le cache à ne pas être utilisé lors de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="e30e2-210">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="e30e2-211">`auto`: En fonction de l’heuristique AutoML, le cache est utilisé ou non.</span><span class="sxs-lookup"><span data-stu-id="e30e2-211">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="e30e2-212">En règle générale, si vous utilisez le choix `auto`, les jeux de données petits et moyens utilisent le cache, tandis que les grands jeux de données ne l’utilisent pas.</span><span class="sxs-lookup"><span data-stu-id="e30e2-212">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="e30e2-213">Si vous ne spécifiez pas le paramètre `--cache`, la configuration `auto` du cache est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="e30e2-213">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="e30e2-214">Nom</span><span class="sxs-lookup"><span data-stu-id="e30e2-214">Name</span></span>

<span data-ttu-id="e30e2-215">`--name` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-215">`--name` (string)</span></span>

<span data-ttu-id="e30e2-216">Nom de la solution ou du projet de sortie créé.</span><span class="sxs-lookup"><span data-stu-id="e30e2-216">The name for the created output project or solution.</span></span> <span data-ttu-id="e30e2-217">Si aucun nom n’est spécifié, le nom `sample-{mltask}` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e30e2-217">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="e30e2-218">Le fichier de modèle ML.NET (fichier .ZIP) reçoit également le même nom.</span><span class="sxs-lookup"><span data-stu-id="e30e2-218">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="e30e2-219">Chemin de sortie</span><span class="sxs-lookup"><span data-stu-id="e30e2-219">Output path</span></span>

<span data-ttu-id="e30e2-220">`--output | -o` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-220">`--output | -o` (string)</span></span>

<span data-ttu-id="e30e2-221">Emplacement/dossier racine où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="e30e2-221">Root location/folder to place the generated output.</span></span> <span data-ttu-id="e30e2-222">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="e30e2-222">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="e30e2-223">Commentaires</span><span class="sxs-lookup"><span data-stu-id="e30e2-223">Verbosity</span></span>

<span data-ttu-id="e30e2-224">`--verbosity | -v` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="e30e2-224">`--verbosity | -v` (string)</span></span>

<span data-ttu-id="e30e2-225">Définit le niveau de détail de la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="e30e2-225">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="e30e2-226">Les valeurs autorisées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e30e2-226">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="e30e2-227">`m[inimal]` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="e30e2-227">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="e30e2-228">`diag[nostic]` (niveau d’informations de journalisation)</span><span class="sxs-lookup"><span data-stu-id="e30e2-228">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="e30e2-229">Par défaut, l’outil CLI doit afficher un minimum de commentaires ( `minimal` ) lorsque vous travaillez, par exemple pour mentionner qu’il fonctionne et, si possible, le temps restant ou le pourcentage de temps écoulé.</span><span class="sxs-lookup"><span data-stu-id="e30e2-229">By default, the CLI tool should show some minimum feedback (`minimal`) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="e30e2-230">Aide</span><span class="sxs-lookup"><span data-stu-id="e30e2-230">Help</span></span>

`-h |--help`

<span data-ttu-id="e30e2-231">Affiche l’aide de la commande avec une description de chacun de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="e30e2-231">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="e30e2-232">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e30e2-232">See also</span></span>

- [<span data-ttu-id="e30e2-233">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="e30e2-233">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="e30e2-234">Vue d’ensemble de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="e30e2-234">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="e30e2-235">Didacticiel : analyser le sentiment à l’aide de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="e30e2-235">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="e30e2-236">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="e30e2-236">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
