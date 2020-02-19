---
title: Informations de référence sur les commandes CLI ML.NET
description: Vue d’ensemble, exemples et informations de référence sur la commande auto-train dans l’outil CLI ML.NET.
ms.date: 12/18/2019
ms.openlocfilehash: 537f8d361c170378f5fe8cf454320831d7c8cbf2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449697"
---
# <a name="the-mlnet-cli-command-reference"></a><span data-ttu-id="27bca-103">Informations de référence sur la commande CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="27bca-103">The ML.NET CLI command reference</span></span>

<span data-ttu-id="27bca-104">La commande `auto-train` est la commande principale fournie par l’outil CLI ML.NET.</span><span class="sxs-lookup"><span data-stu-id="27bca-104">The `auto-train` command is the main command provided by the ML.NET CLI tool.</span></span> <span data-ttu-id="27bca-105">La commande vous permet de générer un modèle de bonne qualité ML.NET à l’aide de l’Machine Learning automatisée (AutoML C# ), ainsi que l’exemple de code permettant d’exécuter/noter ce modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-105">The command allows you to generate a good quality ML.NET model using automated machine learning (AutoML) as well as the example C# code to run/score that model.</span></span> <span data-ttu-id="27bca-106">En outre, le C# code permettant d’effectuer l’apprentissage du modèle est généré pour vous afin de Rechercher l’algorithme et les paramètres du modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-106">In addition, the C# code to train the model is generated for you to research the algorithm and settings of the model.</span></span>

> [!NOTE]
> <span data-ttu-id="27bca-107">Cette rubrique fait référence à l’interface CLI ML.NET et au moteur AutoML ML.NET, actuellement en préversion. Les ressources sont donc susceptibles d’être changées.</span><span class="sxs-lookup"><span data-stu-id="27bca-107">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="overview"></a><span data-ttu-id="27bca-108">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="27bca-108">Overview</span></span>

<span data-ttu-id="27bca-109">Exemple d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="27bca-109">Example usage:</span></span>

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

<span data-ttu-id="27bca-110">La commande `mlnet auto-train` génère les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="27bca-110">The `mlnet auto-train` command generates the following assets:</span></span>

- <span data-ttu-id="27bca-111">Un fichier .zip de modèle sérialisé (le « meilleur modèle »), prêt à être utilisé.</span><span class="sxs-lookup"><span data-stu-id="27bca-111">A serialized model .zip ("best model") ready to use.</span></span>
- <span data-ttu-id="27bca-112">C#code pour exécuter/noter le modèle généré.</span><span class="sxs-lookup"><span data-stu-id="27bca-112">C# code to run/score that generated model.</span></span>
- <span data-ttu-id="27bca-113">C#Code avec le code d’apprentissage utilisé pour générer ce modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-113">C# code with the training code used to generate that model.</span></span>

<span data-ttu-id="27bca-114">Les deux premières ressources peuvent être utilisées directement dans vos applications d’utilisateur final (ASP.NET Core application Web, services, application de bureau, etc.) pour faire des prédictions avec le modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-114">The first two assets can directly be used in your end-user apps (ASP.NET Core web app, services, desktop app and more) to make predictions with the model.</span></span>

<span data-ttu-id="27bca-115">La troisième ressource, le code de formation, vous montre le code de l’API ML.NET utilisé par l’interface CLI pour former le modèle généré, ce qui vous permet d’examiner l’algorithme et les paramètres spécifiques du modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-115">The third asset, the training code, shows you what ML.NET API code was used by the CLI to train the generated model, so you can investigate the specific algorithm and settings of the model.</span></span>

## <a name="examples"></a><span data-ttu-id="27bca-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="27bca-116">Examples</span></span>

<span data-ttu-id="27bca-117">La commande CLI la plus simple pour un problème de classification binaire (AutoML déduit la majeure partie de la configuration à partir des données fournies) :</span><span class="sxs-lookup"><span data-stu-id="27bca-117">The simplest CLI command for a binary classification problem (AutoML infers most of the configuration from the provided data):</span></span>

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

<span data-ttu-id="27bca-118">Autre commande CLI simple pour un problème de régression :</span><span class="sxs-lookup"><span data-stu-id="27bca-118">Another simple CLI command for a regression problem:</span></span>

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

<span data-ttu-id="27bca-119">Créer et entraîner un modèle de classification binaire avec un jeu de données d’entraînement, un jeu de données de test et des arguments explicites de personnalisation supplémentaire :</span><span class="sxs-lookup"><span data-stu-id="27bca-119">Create and train a binary-classification model with a train dataset, a test dataset, and further customization explicit arguments:</span></span>

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a><span data-ttu-id="27bca-120">Options de commande</span><span class="sxs-lookup"><span data-stu-id="27bca-120">Command options</span></span>

<span data-ttu-id="27bca-121">`mlnet auto-train` effectue l’apprentissage de plusieurs modèles en fonction du jeu de données fourni et sélectionne enfin le meilleur modèle, l’enregistre sous la forme d’un C# fichier. zip sérialisé et génère du code associé pour la notation et l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="27bca-121">`mlnet auto-train` trains multiple models based on the provided dataset and finally selects the best model, saves it as a serialized .zip file plus generates related C# code for scoring and training.</span></span>

```console
mlnet auto-train

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

<span data-ttu-id="27bca-122">Les options d’entrée non valides entraînent l’émission par l’outil CLI d’une liste d’entrées valides et d’un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="27bca-122">Invalid input options cause the CLI tool to emit a list of valid inputs and an error message.</span></span>

## <a name="task"></a><span data-ttu-id="27bca-123">Tâche</span><span class="sxs-lookup"><span data-stu-id="27bca-123">Task</span></span>

<span data-ttu-id="27bca-124">`--task | --mltask | -T` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-124">`--task | --mltask | -T` (string)</span></span>

<span data-ttu-id="27bca-125">Simple chaîne fournissant le problème de ML à résoudre.</span><span class="sxs-lookup"><span data-stu-id="27bca-125">A single string providing the ML problem to solve.</span></span> <span data-ttu-id="27bca-126">Par exemple, toutes les tâches suivantes (l’interface CLI est appelée à prendre en charge toutes les tâches prises en charge dans le moteur AutoML) :</span><span class="sxs-lookup"><span data-stu-id="27bca-126">For instance, any of the following tasks (The CLI will eventually support all tasks supported in AutoML):</span></span>

- <span data-ttu-id="27bca-127">`regression` : choisissez cette tâche si vous envisagez d’utiliser le modèle ML pour prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="27bca-127">`regression` - Choose if the ML Model will be used to predict a numeric value</span></span>
- <span data-ttu-id="27bca-128">`binary-classification` : choisissez cette tâche si le résultat du modèle ML a deux valeurs booléennes de catégorie possibles (0 ou 1).</span><span class="sxs-lookup"><span data-stu-id="27bca-128">`binary-classification` - Choose if the ML Model result has two possible categorical boolean values (0 or 1).</span></span>
- <span data-ttu-id="27bca-129">`multiclass-classification` : choisissez cette tâche si le résultat du modèle ML a plusieurs valeurs de catégorie possibles.</span><span class="sxs-lookup"><span data-stu-id="27bca-129">`multiclass-classification` - Choose if the ML Model result has multiple categorical possible values.</span></span>

<span data-ttu-id="27bca-130">Une seule tâche de ML doit être fournie dans cet argument.</span><span class="sxs-lookup"><span data-stu-id="27bca-130">Only one ML task should be provided in this argument.</span></span>

## <a name="dataset"></a><span data-ttu-id="27bca-131">Dataset</span><span class="sxs-lookup"><span data-stu-id="27bca-131">Dataset</span></span>

<span data-ttu-id="27bca-132">`--dataset | -d` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-132">`--dataset | -d` (string)</span></span>

<span data-ttu-id="27bca-133">Cet argument fournit le chemin de l’une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="27bca-133">This argument provides the filepath to either one of the following options:</span></span>

- <span data-ttu-id="27bca-134">*R : l’intégralité du fichier de jeu de données :* Si vous utilisez cette option et que l’utilisateur ne fournit pas `--test-dataset` et `--validation-dataset`, la validation croisée (RepList, etc.) ou les approches de fractionnement automatique des données sont utilisées en interne pour valider le modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-134">*A: The whole dataset file:* If using this option and the user is not providing `--test-dataset` and `--validation-dataset`, then cross-validation (k-fold, etc.) or automated data split approaches will be used internally for validating the model.</span></span> <span data-ttu-id="27bca-135">Dans ce cas, l’utilisateur doit simplement fournir le chemin du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="27bca-135">In that case, the user will just need to provide the dataset filepath.</span></span>

- <span data-ttu-id="27bca-136">*B : fichier de jeu de données d’apprentissage :* Si l’utilisateur fournit également des jeux de données pour la validation de modèle (à l’aide de `--test-dataset` et éventuellement `--validation-dataset`), l’argument `--dataset` signifie uniquement que « jeu de données d’apprentissage ».</span><span class="sxs-lookup"><span data-stu-id="27bca-136">*B: The training dataset file:* If the user is also providing datasets for model validation (using `--test-dataset` and optionally `--validation-dataset`), then the `--dataset` argument means to only have the "training dataset".</span></span> <span data-ttu-id="27bca-137">Par exemple, quand vous utilisez une approche 80 %-20 % pour valider la qualité du modèle et pour obtenir des métriques de précision, le « jeu de données d’entraînement » a 80 % des données, tandis que le « jeu de données de test » a 20 % des données.</span><span class="sxs-lookup"><span data-stu-id="27bca-137">For example, when using an 80% - 20% approach to validate the quality of the model and to obtain accuracy metrics, the "training dataset" will have 80% of the data and the "test dataset" would have 20% of the data.</span></span>

## <a name="test-dataset"></a><span data-ttu-id="27bca-138">Jeu de données de test</span><span class="sxs-lookup"><span data-stu-id="27bca-138">Test dataset</span></span>

<span data-ttu-id="27bca-139">`--test-dataset | -t` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-139">`--test-dataset | -t` (string)</span></span>

<span data-ttu-id="27bca-140">Chemin pointant vers le fichier de jeu de données de test, par exemple lors de l’utilisation d’une approche 80 %-20 % dans le cadre de validations régulières visant à obtenir des métriques de précision.</span><span class="sxs-lookup"><span data-stu-id="27bca-140">File path pointing to the test dataset file, for example when using an 80% - 20% approach when making regular validations to obtain accuracy metrics.</span></span>

<span data-ttu-id="27bca-141">Si vous utilisez `--test-dataset`, `--dataset` est également requis.</span><span class="sxs-lookup"><span data-stu-id="27bca-141">If using `--test-dataset`, then `--dataset` is also required.</span></span>

<span data-ttu-id="27bca-142">L’argument `--test-dataset` est facultatif, sauf si l’option --validation-dataset est utilisée.</span><span class="sxs-lookup"><span data-stu-id="27bca-142">The `--test-dataset` argument is optional unless the --validation-dataset is used.</span></span> <span data-ttu-id="27bca-143">Dans ce cas, l’utilisateur doit recourir aux trois arguments.</span><span class="sxs-lookup"><span data-stu-id="27bca-143">In that case, the user must use the three arguments.</span></span>

## <a name="validation-dataset"></a><span data-ttu-id="27bca-144">Jeu de données de validation</span><span class="sxs-lookup"><span data-stu-id="27bca-144">Validation dataset</span></span>

<span data-ttu-id="27bca-145">`--validation-dataset | -v` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-145">`--validation-dataset | -v` (string)</span></span>

<span data-ttu-id="27bca-146">Chemin pointant vers le fichier de jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="27bca-146">File path pointing to the validation dataset file.</span></span> <span data-ttu-id="27bca-147">Le jeu de données de validation est toujours facultatif.</span><span class="sxs-lookup"><span data-stu-id="27bca-147">The validation dataset is optional, in any case.</span></span>

<span data-ttu-id="27bca-148">Si vous utilisez un `validation dataset`, le comportement doit être le suivant :</span><span class="sxs-lookup"><span data-stu-id="27bca-148">If using a `validation dataset`, the behavior should be:</span></span>

- <span data-ttu-id="27bca-149">Les arguments `test-dataset` et `--dataset` sont également requis.</span><span class="sxs-lookup"><span data-stu-id="27bca-149">The `test-dataset` and `--dataset` arguments are also required.</span></span>

- <span data-ttu-id="27bca-150">Le jeu de données `validation-dataset` est utilisé pour estimer l’erreur de prédiction pour la sélection de modèle.</span><span class="sxs-lookup"><span data-stu-id="27bca-150">The `validation-dataset` dataset is used to estimate prediction error for model selection.</span></span>

- <span data-ttu-id="27bca-151">`test-dataset` est utilisé pour l’évaluation de l’erreur de généralisation du dernier modèle choisi.</span><span class="sxs-lookup"><span data-stu-id="27bca-151">The `test-dataset` is used for assessment of the generalization error of the final chosen model.</span></span> <span data-ttu-id="27bca-152">Dans l’idéal, le jeu de test doit être conservé dans un « coffre » et récupéré uniquement à la fin de l’analyse des données.</span><span class="sxs-lookup"><span data-stu-id="27bca-152">Ideally, the test set should be kept in a “vault,” and be brought out only at the end of the data analysis.</span></span>

<span data-ttu-id="27bca-153">Quand vous utilisez un `validation dataset` ainsi que `test dataset`, la phase de validation est divisée en deux parties :</span><span class="sxs-lookup"><span data-stu-id="27bca-153">Basically, when using a `validation dataset` plus the `test dataset`, the validation phase is split into two parts:</span></span>

1. <span data-ttu-id="27bca-154">Dans la première partie, vous examinez simplement vos modèles et sélectionnez l’approche la plus performante en utilisant les données de validation (=validation)</span><span class="sxs-lookup"><span data-stu-id="27bca-154">In the first part, you just look at your models and select the best performing approach using the validation data (=validation)</span></span>
2. <span data-ttu-id="27bca-155">Ensuite, vous estimez la précision de l’approche sélectionnée (= test).</span><span class="sxs-lookup"><span data-stu-id="27bca-155">Then you estimate the accuracy of the selected approach (=test).</span></span>

<span data-ttu-id="27bca-156">Ainsi, la séparation des données peut être 80/10/10 ou 75/15/10.</span><span class="sxs-lookup"><span data-stu-id="27bca-156">Hence, the separation of data could be 80/10/10 or 75/15/10.</span></span> <span data-ttu-id="27bca-157">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="27bca-157">For example:</span></span>

- <span data-ttu-id="27bca-158">Le fichier `training-dataset` doit avoir 75 % des données.</span><span class="sxs-lookup"><span data-stu-id="27bca-158">`training-dataset` file should have 75% of the data.</span></span>
- <span data-ttu-id="27bca-159">Le fichier `validation-dataset` doit avoir 15 % des données.</span><span class="sxs-lookup"><span data-stu-id="27bca-159">`validation-dataset` file should have 15% of the data.</span></span>
- <span data-ttu-id="27bca-160">Le fichier `test-dataset` doit avoir 10 % des données.</span><span class="sxs-lookup"><span data-stu-id="27bca-160">`test-dataset` file should have 10% of the data.</span></span>

<span data-ttu-id="27bca-161">Dans tous les cas, ces pourcentages sont déterminés par l’utilisateur à l’aide de l’interface CLI, qui fournit les fichiers déjà fractionnés.</span><span class="sxs-lookup"><span data-stu-id="27bca-161">In any case, those percentages will be decided by the user using the CLI who will provide the files already split.</span></span>

## <a name="label-column-name"></a><span data-ttu-id="27bca-162">Nom de la colonne d’étiquette</span><span class="sxs-lookup"><span data-stu-id="27bca-162">Label column name</span></span>

<span data-ttu-id="27bca-163">`--label-column-name | -n` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-163">`--label-column-name | -n` (string)</span></span>

<span data-ttu-id="27bca-164">Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant le nom de la colonne défini dans l’en-tête du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="27bca-164">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's name set in the dataset's header.</span></span>

<span data-ttu-id="27bca-165">Cet argument est utilisé uniquement pour les tâches de ML supervisées telles qu’un *problème de classification*.</span><span class="sxs-lookup"><span data-stu-id="27bca-165">This argument is used only for supervised ML tasks such as a *classification problem*.</span></span> <span data-ttu-id="27bca-166">Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.</span><span class="sxs-lookup"><span data-stu-id="27bca-166">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="label-column-index"></a><span data-ttu-id="27bca-167">Index de colonne d’étiquette</span><span class="sxs-lookup"><span data-stu-id="27bca-167">Label column index</span></span>

<span data-ttu-id="27bca-168">`--label-column-index | -i` (entier)</span><span class="sxs-lookup"><span data-stu-id="27bca-168">`--label-column-index | -i` (int)</span></span>

<span data-ttu-id="27bca-169">Avec cet argument, vous pouvez spécifier une colonne cible/objectif (la variable que vous souhaitez prédire) en utilisant l’index numérique de la colonne dans le fichier du jeu de données (les valeurs d’index de colonne commencent à 1).</span><span class="sxs-lookup"><span data-stu-id="27bca-169">With this argument, a specific objective/target column (the variable that you want to predict) can be specified by using the column's numeric index in the dataset's file (The column index values start at 1).</span></span>

<span data-ttu-id="27bca-170">*Remarque :* Si l’utilisateur utilise également la `--label-column-name`, la `--label-column-name` est celle qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="27bca-170">*Note:* If the user is also using the `--label-column-name`, the `--label-column-name` is the one being used.</span></span>

<span data-ttu-id="27bca-171">Cet argument est utilisé uniquement pour une tâche de ML supervisée telle qu’un *problème de classification*.</span><span class="sxs-lookup"><span data-stu-id="27bca-171">This argument is used only for supervised ML task such as a *classification problem*.</span></span> <span data-ttu-id="27bca-172">Il ne peut pas être utilisé pour les tâches de ML non supervisées comme le *clustering*.</span><span class="sxs-lookup"><span data-stu-id="27bca-172">It cannot be used for unsupervised ML Tasks such as *clustering*.</span></span>

## <a name="ignore-columns"></a><span data-ttu-id="27bca-173">Ignorer les colonnes</span><span class="sxs-lookup"><span data-stu-id="27bca-173">Ignore columns</span></span>

<span data-ttu-id="27bca-174">`--ignore-columns | -I` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-174">`--ignore-columns | -I` (string)</span></span>

<span data-ttu-id="27bca-175">Avec cet argument, vous pouvez ignorer des colonnes existantes dans le fichier de jeu de données afin qu’elles ne soient pas chargées et utilisées par les processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="27bca-175">With this argument, you can ignore existing columns in the dataset file so they are not loaded and used by the training processes.</span></span>

<span data-ttu-id="27bca-176">Spécifiez les noms des colonnes que vous souhaitez ignorer.</span><span class="sxs-lookup"><span data-stu-id="27bca-176">Specify the columns names that you want to ignore.</span></span> <span data-ttu-id="27bca-177">Utilisez « ,  » (virgule avec espace) ou «   » (espace) pour séparer plusieurs noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="27bca-177">Use ', ' (comma with space) or ' ' (space) to separate multiple column names.</span></span> <span data-ttu-id="27bca-178">Vous pouvez utiliser des guillemets pour les noms de colonnes contenant des espaces (par exemple, "utilisateur connecté").</span><span class="sxs-lookup"><span data-stu-id="27bca-178">You can use quotes for column names containing whitespace (e.g. "logged in").</span></span>

<span data-ttu-id="27bca-179">Exemple :</span><span class="sxs-lookup"><span data-stu-id="27bca-179">Example:</span></span>

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a><span data-ttu-id="27bca-180">A un en-tête</span><span class="sxs-lookup"><span data-stu-id="27bca-180">Has header</span></span>

<span data-ttu-id="27bca-181">`--has-header | -h` (booléen)</span><span class="sxs-lookup"><span data-stu-id="27bca-181">`--has-header | -h` (bool)</span></span>

<span data-ttu-id="27bca-182">Spécifiez si le ou les fichiers de jeu de données ont une ligne d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="27bca-182">Specify if the dataset file(s) have a header row.</span></span>
<span data-ttu-id="27bca-183">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="27bca-183">Possible values are:</span></span>

- `true`
- `false`

<span data-ttu-id="27bca-184">La valeur par défaut est `true` si cet argument n’est pas spécifié par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="27bca-184">The by default value is `true` if this argument is not specified by the user.</span></span>

<span data-ttu-id="27bca-185">Pour que l’argument `--label-column-name` puisse être utilisé, le fichier de jeu de données doit avoir un en-tête et `--has-header` doit être défini sur `true` (paramétrage par défaut).</span><span class="sxs-lookup"><span data-stu-id="27bca-185">In order to use the `--label-column-name` argument, you need to have a header in the dataset file and `--has-header` set to `true` (which is by default).</span></span>

## <a name="max-exploration-time"></a><span data-ttu-id="27bca-186">Durée maximale d’exploration</span><span class="sxs-lookup"><span data-stu-id="27bca-186">Max exploration time</span></span>

<span data-ttu-id="27bca-187">`--max-exploration-time | -x` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-187">`--max-exploration-time | -x` (string)</span></span>

<span data-ttu-id="27bca-188">Par défaut, la durée maximale d’exploration est de 30 minutes.</span><span class="sxs-lookup"><span data-stu-id="27bca-188">By default, the maximum exploration time is 30 minutes.</span></span>

<span data-ttu-id="27bca-189">Cet argument définit la durée maximale (en secondes) dont dispose le processus pour explorer plusieurs entraîneurs et configurations.</span><span class="sxs-lookup"><span data-stu-id="27bca-189">This argument sets the maximum time (in seconds) for the process to explore multiple trainers and configurations.</span></span> <span data-ttu-id="27bca-190">La durée configurée peut être dépassée si la durée fournie est trop courte (par exemple, 2 secondes) pour une seule itération.</span><span class="sxs-lookup"><span data-stu-id="27bca-190">The configured time may be exceeded if the provided time is too short (say 2 seconds) for a single iteration.</span></span> <span data-ttu-id="27bca-191">Dans ce cas, la durée réelle est le temps nécessaire pour produire une seule configuration de modèle dans une seule itération.</span><span class="sxs-lookup"><span data-stu-id="27bca-191">In this case, the actual time is the required time to produce one model configuration in a single iteration.</span></span>

<span data-ttu-id="27bca-192">La durée nécessaire pour les itérations peut varier selon la taille du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="27bca-192">The needed time for iterations can vary depending on the size of the dataset.</span></span>

## <a name="cache"></a><span data-ttu-id="27bca-193">Cache</span><span class="sxs-lookup"><span data-stu-id="27bca-193">Cache</span></span>

<span data-ttu-id="27bca-194">`--cache | -c` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-194">`--cache | -c` (string)</span></span>

<span data-ttu-id="27bca-195">Si vous utilisez la mise en cache, le jeu de données d’entraînement entier est chargé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="27bca-195">If you use caching, the whole training dataset will be loaded in-memory.</span></span>

<span data-ttu-id="27bca-196">Pour les jeux de données petits et moyens, l’utilisation du cache peut considérablement améliorer les performances d’entraînement, ce qui signifie que la durée d’entraînement peut être plus courte que quand vous n’utilisez pas de cache.</span><span class="sxs-lookup"><span data-stu-id="27bca-196">For small and medium datasets, using cache can drastically improve the training performance, meaning the training time can be shorter than when you don't use cache.</span></span>

<span data-ttu-id="27bca-197">Toutefois, pour les grands jeux de données, le chargement de toutes les données en mémoire peut avoir un impact négatif dans la mesure où vous risquez de manquer de mémoire.</span><span class="sxs-lookup"><span data-stu-id="27bca-197">However, for large datasets, loading all the data in memory can impact negatively since you might get out of memory.</span></span> <span data-ttu-id="27bca-198">Si vous effectuez un entraînement avec de grands fichiers de jeu de données sans utiliser de cache, ML.NET récupère des blocs de données du lecteur sous forme de flux s’il doit charger davantage de données.</span><span class="sxs-lookup"><span data-stu-id="27bca-198">When training with large dataset files and not using cache, ML.NET will be streaming chunks of data from the drive when it needs to load more data while training.</span></span>

<span data-ttu-id="27bca-199">Vous pouvez spécifier les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="27bca-199">You can specify the following values:</span></span>

<span data-ttu-id="27bca-200">`on`: force l’utilisation du cache lors de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="27bca-200">`on`: Forces cache to be used when training.</span></span>
<span data-ttu-id="27bca-201">`off`: force le cache à ne pas être utilisé lors de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="27bca-201">`off`: Forces cache not to be used when training.</span></span>
<span data-ttu-id="27bca-202">`auto`: en fonction de l’heuristique AutoML, le cache est utilisé ou non.</span><span class="sxs-lookup"><span data-stu-id="27bca-202">`auto`: Depending on AutoML heuristics, the cache will be used or not.</span></span> <span data-ttu-id="27bca-203">En règle générale, si vous utilisez le choix `auto`, les jeux de données petits et moyens utilisent le cache, tandis que les grands jeux de données ne l’utilisent pas.</span><span class="sxs-lookup"><span data-stu-id="27bca-203">Usually, small/medium datasets will use cache and large datasets won't use cache if you use the `auto` choice.</span></span>

<span data-ttu-id="27bca-204">Si vous ne spécifiez pas le paramètre `--cache`, la configuration `auto` du cache est utilisée par défaut.</span><span class="sxs-lookup"><span data-stu-id="27bca-204">If you don't specify the `--cache` parameter, then the cache `auto` configuration will be used by default.</span></span>

## <a name="name"></a><span data-ttu-id="27bca-205">Name</span><span class="sxs-lookup"><span data-stu-id="27bca-205">Name</span></span>

<span data-ttu-id="27bca-206">`--name | -N` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-206">`--name | -N` (string)</span></span>

<span data-ttu-id="27bca-207">Nom de la solution ou du projet de sortie créé.</span><span class="sxs-lookup"><span data-stu-id="27bca-207">The name for the created output project or solution.</span></span> <span data-ttu-id="27bca-208">Si aucun nom n’est spécifié, le nom `sample-{mltask}` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="27bca-208">If no name is specified, the name `sample-{mltask}` is used.</span></span>

<span data-ttu-id="27bca-209">Le fichier de modèle ML.NET (fichier .ZIP) reçoit également le même nom.</span><span class="sxs-lookup"><span data-stu-id="27bca-209">The ML.NET model file (.ZIP file) will get the same name, as well.</span></span>

## <a name="output-path"></a><span data-ttu-id="27bca-210">Chemin de sortie</span><span class="sxs-lookup"><span data-stu-id="27bca-210">Output path</span></span>

<span data-ttu-id="27bca-211">`--output-path | -o` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-211">`--output-path | -o` (string)</span></span>

<span data-ttu-id="27bca-212">Emplacement/dossier racine où placer la sortie générée.</span><span class="sxs-lookup"><span data-stu-id="27bca-212">Root location/folder to place the generated output.</span></span> <span data-ttu-id="27bca-213">L'emplacement par défaut est le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="27bca-213">The default is the current directory.</span></span>

## <a name="verbosity"></a><span data-ttu-id="27bca-214">Commentaires</span><span class="sxs-lookup"><span data-stu-id="27bca-214">Verbosity</span></span>

<span data-ttu-id="27bca-215">`--verbosity | -V` (chaîne)</span><span class="sxs-lookup"><span data-stu-id="27bca-215">`--verbosity | -V` (string)</span></span>

<span data-ttu-id="27bca-216">Définit le niveau de détail de la sortie standard.</span><span class="sxs-lookup"><span data-stu-id="27bca-216">Sets the verbosity level of the standard output.</span></span>

<span data-ttu-id="27bca-217">Les valeurs autorisées sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="27bca-217">Allowed values are:</span></span>

- `q[uiet]`
- <span data-ttu-id="27bca-218">`m[inimal]` (par défaut)</span><span class="sxs-lookup"><span data-stu-id="27bca-218">`m[inimal]`  (by default)</span></span>
- <span data-ttu-id="27bca-219">`diag[nostic]` (niveau d’informations de journalisation)</span><span class="sxs-lookup"><span data-stu-id="27bca-219">`diag[nostic]` (logging information level)</span></span>

<span data-ttu-id="27bca-220">Par défaut, l’outil CLI doit afficher un minimum de commentaires quand il fonctionne ; il doit par exemple indiquer qu’il fonctionne et, si possible, le temps restant ou le pourcentage de temps écoulé.</span><span class="sxs-lookup"><span data-stu-id="27bca-220">By default, the CLI tool should show some minimum feedback (minimal) when working, such as mentioning that it is working and if possible how much time is left or what % of the time is completed.</span></span>

## <a name="help"></a><span data-ttu-id="27bca-221">Aide</span><span class="sxs-lookup"><span data-stu-id="27bca-221">Help</span></span>

`-h|--help`

<span data-ttu-id="27bca-222">Affiche l’aide de la commande avec une description de chacun de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="27bca-222">Prints out help for the command with a description for each command's parameter.</span></span>

## <a name="see-also"></a><span data-ttu-id="27bca-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27bca-223">See also</span></span>

- [<span data-ttu-id="27bca-224">Guide pratique pour installer l’outil CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="27bca-224">How to install the ML.NET CLI tool</span></span>](../how-to-guides/install-ml-net-cli.md)
- [<span data-ttu-id="27bca-225">Vue d’ensemble de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="27bca-225">Overview of the ML.NET CLI</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="27bca-226">Didacticiel : analyser le sentiment à l’aide de l’interface CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="27bca-226">Tutorial: Analyze sentiment using the ML.NET CLI</span></span>](../tutorials/sentiment-analysis-cli.md)
- [<span data-ttu-id="27bca-227">Télémétrie dans la CLI ML.NET</span><span class="sxs-lookup"><span data-stu-id="27bca-227">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
