---
title: Tâches d’apprentissage automatique
description: Explorez les différentes tâches Machine Learning ainsi que les tâches associées prises en charge dans ML.NET.
ms.date: 12/23/2019
ms.openlocfilehash: e6e36bd65dbadb8cb7b8edbf9e2e82071c208378
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144446"
---
# <a name="machine-learning-tasks-in-mlnet"></a><span data-ttu-id="924c3-103">Tâches Machine Learning dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="924c3-103">Machine learning tasks in ML.NET</span></span>

<span data-ttu-id="924c3-104">Une tâche de Machine Learning est le type de prédiction ou d’inférence qui est effectué, en fonction du problème ou de la question demandée, et des données disponibles.</span><span class="sxs-lookup"><span data-stu-id="924c3-104">A machine learning task is the type of prediction or inference being made, based on the problem or question that is being asked, and the available data.</span></span> <span data-ttu-id="924c3-105">Par exemple, la tâche de classification assigne des données à des catégories, et la tâche de clustering regroupe les données en fonction de la similarité.</span><span class="sxs-lookup"><span data-stu-id="924c3-105">For example, the classification task assigns data to categories, and the clustering task groups data according to similarity.</span></span>

<span data-ttu-id="924c3-106">Les tâches machine learning s’appuient sur des modèles dans les données plutôt que sur des séquences explicitement programmées.</span><span class="sxs-lookup"><span data-stu-id="924c3-106">Machine learning tasks rely on patterns in the data rather than being explicitly programmed.</span></span>

<span data-ttu-id="924c3-107">Cet article décrit les différentes tâches de Machine Learning que vous pouvez choisir dans ML.NET et certains cas d’usage courants.</span><span class="sxs-lookup"><span data-stu-id="924c3-107">This article describes the different machine learning tasks that you can choose from in ML.NET and some common use cases.</span></span>

<span data-ttu-id="924c3-108">Une fois que vous avez décidé de tâche qui fonctionne pour votre scénario, vous devez choisir le meilleur algorithme pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="924c3-108">Once you have decided which task works for your scenario, then you need to choose the best algorithm to train your model.</span></span> <span data-ttu-id="924c3-109">Les algorithmes disponibles sont listés dans la section pour chaque tâche.</span><span class="sxs-lookup"><span data-stu-id="924c3-109">The available algorithms are listed in the section for each task.</span></span>

## <a name="binary-classification"></a><span data-ttu-id="924c3-110">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="924c3-110">Binary classification</span></span>

<span data-ttu-id="924c3-111">Une tâche [Apprentissage automatique supervisé](glossary.md#supervised-machine-learning) utilisée pour prédire à laquelle des deux classes (catégories) appartient une instance de données.</span><span class="sxs-lookup"><span data-stu-id="924c3-111">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict which of two classes (categories) an instance of data belongs to.</span></span> <span data-ttu-id="924c3-112">L’entrée d’un algorithme de classification est un ensemble d’exemples étiquetés, où chaque étiquette est un entier ayant pour valeur 0 ou 1.</span><span class="sxs-lookup"><span data-stu-id="924c3-112">The input of a classification algorithm is a set of labeled examples, where each label is an integer of either 0 or 1.</span></span> <span data-ttu-id="924c3-113">La sortie d’un algorithme de classification binaire est un classifieur, que vous pouvez utiliser pour prédire la classe de nouvelles instances sans étiquette.</span><span class="sxs-lookup"><span data-stu-id="924c3-113">The output of a binary classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="924c3-114">Voici quelques exemples de scénarios de classification binaire :</span><span class="sxs-lookup"><span data-stu-id="924c3-114">Examples of binary classification scenarios include:</span></span>

* <span data-ttu-id="924c3-115">[Déterminer si des commentaires Twitter](../tutorials/sentiment-analysis.md) sont « positifs » ou « négatifs ».</span><span class="sxs-lookup"><span data-stu-id="924c3-115">[Understanding sentiment of Twitter comments](../tutorials/sentiment-analysis.md) as either "positive" or "negative".</span></span>
* <span data-ttu-id="924c3-116">Diagnostiquer si un patient est atteint ou non d’une certaine maladie.</span><span class="sxs-lookup"><span data-stu-id="924c3-116">Diagnosing whether a patient has a certain disease or not.</span></span>
* <span data-ttu-id="924c3-117">Décider si un e-mail doit être considéré comme « spam » ou non.</span><span class="sxs-lookup"><span data-stu-id="924c3-117">Making a decision to mark an email as "spam" or not.</span></span>
* <span data-ttu-id="924c3-118">Déterminer si une photo contient un élément particulier, tel qu’un chien ou un fruit.</span><span class="sxs-lookup"><span data-stu-id="924c3-118">Determining if a photo contains a particular item or not, such as a dog or fruit.</span></span>

<span data-ttu-id="924c3-119">Pour plus d’informations, consultez l’article Wikipédia [Classification binaire](https://en.wikipedia.org/wiki/Binary_classification).</span><span class="sxs-lookup"><span data-stu-id="924c3-119">For more information, see the [Binary classification](https://en.wikipedia.org/wiki/Binary_classification) article on Wikipedia.</span></span>

### <a name="binary-classification-trainers"></a><span data-ttu-id="924c3-120">Entraîneurs de classification binaire</span><span class="sxs-lookup"><span data-stu-id="924c3-120">Binary classification trainers</span></span>

<span data-ttu-id="924c3-121">Vous pouvez entraîner un modèle de classification binaire en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-121">You can train a binary classification model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>
* <xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer>
* <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>
* <xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>
* <xref:Microsoft.ML.Trainers.PriorTrainer>
* <xref:Microsoft.ML.Trainers.LinearSvmTrainer>

### <a name="binary-classification-inputs-and-outputs"></a><span data-ttu-id="924c3-122">Entrées et sorties de classification binaire</span><span class="sxs-lookup"><span data-stu-id="924c3-122">Binary classification inputs and outputs</span></span>

<span data-ttu-id="924c3-123">Pour tirer le meilleur parti de la classification binaire, vous devez équilibrer les données d’entraînement (autrement dit, avoir le même nombre de données d’entraînement positives que négatives).</span><span class="sxs-lookup"><span data-stu-id="924c3-123">For best results with binary classification, the training data should be balanced (that is, equal numbers of positive and negative training data).</span></span> <span data-ttu-id="924c3-124">Les valeurs manquantes doivent être traitées avant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="924c3-124">Missing values should be handled before training.</span></span>

<span data-ttu-id="924c3-125">Les données de la colonne d’étiquettes d’entrée doivent être <xref:System.Boolean>.</span><span class="sxs-lookup"><span data-stu-id="924c3-125">The input label column data must be <xref:System.Boolean>.</span></span>
<span data-ttu-id="924c3-126">Les données de la colonne des caractéristiques d’entrée doivent être un vecteur de taille fixe de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="924c3-126">The input features column data must be a fixed-size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="924c3-127">Ces formateurs génèrent les colonnes suivantes :</span><span class="sxs-lookup"><span data-stu-id="924c3-127">These trainers output the following columns:</span></span>

| <span data-ttu-id="924c3-128">Nom de colonne de sortie</span><span class="sxs-lookup"><span data-stu-id="924c3-128">Output Column Name</span></span> | <span data-ttu-id="924c3-129">Type de colonne</span><span class="sxs-lookup"><span data-stu-id="924c3-129">Column Type</span></span> | <span data-ttu-id="924c3-130">Description</span><span class="sxs-lookup"><span data-stu-id="924c3-130">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="924c3-131">Score brut calculé par le modèle</span><span class="sxs-lookup"><span data-stu-id="924c3-131">The raw score that was calculated by the model</span></span>|
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="924c3-132">Étiquette prédite, en fonction du signe du score.</span><span class="sxs-lookup"><span data-stu-id="924c3-132">The predicted label, based on the sign of the score.</span></span> <span data-ttu-id="924c3-133">Un score négatif est mappé à `false`, tandis qu’un score positif est mappé à `true`.</span><span class="sxs-lookup"><span data-stu-id="924c3-133">A negative score maps to `false` and a positive score maps to `true`.</span></span>|

## <a name="multiclass-classification"></a><span data-ttu-id="924c3-134">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="924c3-134">Multiclass classification</span></span>

<span data-ttu-id="924c3-135">Une tâche [Apprentissage automatique supervisé](glossary.md#supervised-machine-learning) utilisée pour prédire la classe (catégorie) d’une instance de données.</span><span class="sxs-lookup"><span data-stu-id="924c3-135">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the class (category) of an instance of data.</span></span> <span data-ttu-id="924c3-136">L’entrée d’un algorithme de classification est un ensemble d’exemples étiquetés.</span><span class="sxs-lookup"><span data-stu-id="924c3-136">The input of a classification algorithm is a set of labeled examples.</span></span> <span data-ttu-id="924c3-137">Chaque étiquette démarre normalement en tant que texte.</span><span class="sxs-lookup"><span data-stu-id="924c3-137">Each label normally starts as text.</span></span> <span data-ttu-id="924c3-138">Elle est ensuite exécutée via TermTransform, qui la convertit en un type de clé (numérique).</span><span class="sxs-lookup"><span data-stu-id="924c3-138">It is then run through the TermTransform, which converts it to the Key (numeric) type.</span></span> <span data-ttu-id="924c3-139">La sortie d’un algorithme de classification est un classifieur, que vous pouvez utiliser pour prédire la classe de nouvelles instances sans étiquette.</span><span class="sxs-lookup"><span data-stu-id="924c3-139">The output of a classification algorithm is a classifier, which you can use to predict the class of new unlabeled instances.</span></span> <span data-ttu-id="924c3-140">Voici quelques exemples de scénarios de classification multiclasse :</span><span class="sxs-lookup"><span data-stu-id="924c3-140">Examples of multi-class classification scenarios include:</span></span>

* <span data-ttu-id="924c3-141">Déterminer la race d’un chien, par exemple « Husky de Sibérie », « Golden Retriever », « Caniche », etc.</span><span class="sxs-lookup"><span data-stu-id="924c3-141">Determining the breed of a dog as a "Siberian Husky", "Golden Retriever", "Poodle", etc.</span></span>
* <span data-ttu-id="924c3-142">Déterminer si des critiques d’un film sont « positives », « neutres » ou « négatives ».</span><span class="sxs-lookup"><span data-stu-id="924c3-142">Understanding movie reviews as "positive", "neutral", or "negative".</span></span>
* <span data-ttu-id="924c3-143">Classer les évaluations d’un hôtel par « situation géographique », « prix », « propreté », etc.</span><span class="sxs-lookup"><span data-stu-id="924c3-143">Categorizing hotel reviews as "location", "price", "cleanliness", etc.</span></span>

<span data-ttu-id="924c3-144">Pour plus d’informations, consultez l’article Wikipédia [Classification multiclasse](https://en.wikipedia.org/wiki/Multiclass_classification).</span><span class="sxs-lookup"><span data-stu-id="924c3-144">For more information, see the [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification) article on Wikipedia.</span></span>

>[!NOTE]
><span data-ttu-id="924c3-145">OvA (One vs all, Un comparé à tous) met à niveau les [learners de classification binaire](#binary-classification) pour agir sur les jeux de données multiclasses.</span><span class="sxs-lookup"><span data-stu-id="924c3-145">One vs all upgrades any [binary classification learner](#binary-classification) to act on multiclass datasets.</span></span> <span data-ttu-id="924c3-146">Plus d’informations sur [Wikipédia](https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span><span class="sxs-lookup"><span data-stu-id="924c3-146">More information on [Wikipedia](https://en.wikipedia.org/wiki/Multiclass_classification#One-vs.-rest).</span></span>

### <a name="multiclass-classification-trainers"></a><span data-ttu-id="924c3-147">Entraîneurs de classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="924c3-147">Multiclass classification trainers</span></span>

<span data-ttu-id="924c3-148">Vous pouvez entraîner un modèle de classification multiclasse en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-148">You can train a multiclass classification model using the following training algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>
* <xref:Microsoft.ML.Trainers.OneVersusAllTrainer>
* <xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer>
* <xref:Microsoft.ML.Vision.ImageClassificationTrainer>

### <a name="multiclass-classification-inputs-and-outputs"></a><span data-ttu-id="924c3-149">Entrées et sorties de classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="924c3-149">Multiclass classification inputs and outputs</span></span>

<span data-ttu-id="924c3-150">Les données de la colonne d’étiquettes d’entrée doivent être de type [clé](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="924c3-150">The input label column data must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>
<span data-ttu-id="924c3-151">La colonne des caractéristiques doit être un vecteur de taille fixe de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="924c3-151">The feature column must be a fixed size vector of <xref:System.Single>.</span></span>

<span data-ttu-id="924c3-152">Cet entraîneur génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="924c3-152">This trainer outputs the following:</span></span>

| <span data-ttu-id="924c3-153">Nom de sortie</span><span class="sxs-lookup"><span data-stu-id="924c3-153">Output Name</span></span> | <span data-ttu-id="924c3-154">Type</span><span class="sxs-lookup"><span data-stu-id="924c3-154">Type</span></span> | <span data-ttu-id="924c3-155">Description</span><span class="sxs-lookup"><span data-stu-id="924c3-155">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="924c3-156">Vecteur de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="924c3-156">Vector of <xref:System.Single></span></span> | <span data-ttu-id="924c3-157">Les scores de toutes les classes.</span><span class="sxs-lookup"><span data-stu-id="924c3-157">The scores of all classes.</span></span> <span data-ttu-id="924c3-158">Une valeur supérieure signifie une plus forte probabilité d’appartenir à la classe associée.</span><span class="sxs-lookup"><span data-stu-id="924c3-158">Higher value means higher probability to fall into the associated class.</span></span> <span data-ttu-id="924c3-159">Si l’i-ème élément a la plus grande valeur, l’index de l’étiquette prédite est i.</span><span class="sxs-lookup"><span data-stu-id="924c3-159">If the i-th element has the largest value, the predicted label index would be i.</span></span> <span data-ttu-id="924c3-160">Notez que i est l’index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="924c3-160">Note that i is zero-based index.</span></span> |
| `PredictedLabel` | <span data-ttu-id="924c3-161">type de [clé](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="924c3-161">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="924c3-162">Index de l’étiquette prédite.</span><span class="sxs-lookup"><span data-stu-id="924c3-162">The predicted label's index.</span></span> <span data-ttu-id="924c3-163">Si sa valeur est i, l’étiquette réelle est la i-ème catégorie dans le type d’étiquette d’entrée avec une valeur de clé.</span><span class="sxs-lookup"><span data-stu-id="924c3-163">If its value is i, the actual label would be the i-th category in the key-valued input label type.</span></span> |

## <a name="regression"></a><span data-ttu-id="924c3-164">régression ;</span><span class="sxs-lookup"><span data-stu-id="924c3-164">Regression</span></span>

<span data-ttu-id="924c3-165">Une tâche [Apprentissage automatique supervisée](glossary.md#supervised-machine-learning) utilisée pour prédire la valeur de l’étiquette d’un ensemble de fonctionnalités connexes.</span><span class="sxs-lookup"><span data-stu-id="924c3-165">A [supervised machine learning](glossary.md#supervised-machine-learning) task that is used to predict the value of the label from a set of related features.</span></span> <span data-ttu-id="924c3-166">L’étiquette peut avoir n’importe quelle valeur réelle et ne provient pas d’un ensemble fini de valeurs comme dans les tâches de classification.</span><span class="sxs-lookup"><span data-stu-id="924c3-166">The label can be of any real value and is not from a finite set of values as in classification tasks.</span></span> <span data-ttu-id="924c3-167">Les algorithmes de régression modèlent la dépendance de l’étiquette sur ses fonctionnalités connexes pour déterminer la façon dont l’étiquette change avec des valeurs de fonctionnalités différentes.</span><span class="sxs-lookup"><span data-stu-id="924c3-167">Regression algorithms model the dependency of the label on its related features to determine how the label will change as the values of the features are varied.</span></span> <span data-ttu-id="924c3-168">L’entrée d’un algorithme de régression est un ensemble d’exemples avec des étiquettes de valeurs connues.</span><span class="sxs-lookup"><span data-stu-id="924c3-168">The input of a regression algorithm is a set of examples with labels of known values.</span></span> <span data-ttu-id="924c3-169">La sortie d’un algorithme de régression est une fonction, que vous pouvez utiliser pour prédire la valeur de l’étiquette pour tout nouvel ensemble de fonctionnalités d’entrée.</span><span class="sxs-lookup"><span data-stu-id="924c3-169">The output of a regression algorithm is a function, which you can use to predict the label value for any new set of input features.</span></span> <span data-ttu-id="924c3-170">Voici quelques exemples de scénarios de régression :</span><span class="sxs-lookup"><span data-stu-id="924c3-170">Examples of regression scenarios include:</span></span>

* <span data-ttu-id="924c3-171">Prédire le prix d’une maison selon ses attributs, par exemple le nombre de chambres, l’emplacement ou la taille.</span><span class="sxs-lookup"><span data-stu-id="924c3-171">Predicting house prices based on house attributes such as number of bedrooms, location, or size.</span></span>
* <span data-ttu-id="924c3-172">Prédire le cours d’actions en fonction de données historiques et des tendances du marché actuel.</span><span class="sxs-lookup"><span data-stu-id="924c3-172">Predicting future stock prices based on historical data and current market trends.</span></span>
* <span data-ttu-id="924c3-173">Prédire les ventes d’un produit en fonction d’un budget publicitaire.</span><span class="sxs-lookup"><span data-stu-id="924c3-173">Predicting sales of a product based on advertising budgets.</span></span>

### <a name="regression-trainers"></a><span data-ttu-id="924c3-174">Entraîneurs de régression</span><span class="sxs-lookup"><span data-stu-id="924c3-174">Regression trainers</span></span>

<span data-ttu-id="924c3-175">Vous pouvez entraîner un modèle de régression en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-175">You can train a regression model using the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer>
* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer>
* <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer>
* <xref:Microsoft.ML.Trainers.OlsTrainer>
* <xref:Microsoft.ML.Trainers.OnlineGradientDescentTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer>

### <a name="regression-inputs-and-outputs"></a><span data-ttu-id="924c3-176">Entrées et sorties de régression</span><span class="sxs-lookup"><span data-stu-id="924c3-176">Regression inputs and outputs</span></span>

<span data-ttu-id="924c3-177">Les données de la colonne d’étiquettes d’entrée doivent être <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="924c3-177">The input label column data must be <xref:System.Single>.</span></span>

<span data-ttu-id="924c3-178">Les entraîneurs pour cette tâche génèrent le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="924c3-178">The trainers for this task output the following:</span></span>

| <span data-ttu-id="924c3-179">Nom de sortie</span><span class="sxs-lookup"><span data-stu-id="924c3-179">Output Name</span></span> | <span data-ttu-id="924c3-180">Type</span><span class="sxs-lookup"><span data-stu-id="924c3-180">Type</span></span> | <span data-ttu-id="924c3-181">Description</span><span class="sxs-lookup"><span data-stu-id="924c3-181">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="924c3-182">Score brut prédit par le modèle</span><span class="sxs-lookup"><span data-stu-id="924c3-182">The raw score that was predicted by the model</span></span> |

## <a name="clustering"></a><span data-ttu-id="924c3-183">Clustering</span><span class="sxs-lookup"><span data-stu-id="924c3-183">Clustering</span></span>

<span data-ttu-id="924c3-184">Une tâche [Apprentissage automatique non supervisé](glossary.md#unsupervised-machine-learning) utilisée pour regrouper des instances de données dans des clusters contenant des caractéristiques similaires.</span><span class="sxs-lookup"><span data-stu-id="924c3-184">An [unsupervised machine learning](glossary.md#unsupervised-machine-learning) task that is used to group instances of data into clusters that contain similar characteristics.</span></span> <span data-ttu-id="924c3-185">Le clustering permet également d’identifier, dans un jeu de données, les relations qui peuvent ne pas être logiquement dérivées par navigation ou simple observation.</span><span class="sxs-lookup"><span data-stu-id="924c3-185">Clustering can also be used to identify relationships in a dataset that you might not logically derive by browsing or simple observation.</span></span> <span data-ttu-id="924c3-186">Les entrées et sorties d’un algorithme de clustering dépendent de la méthode choisie.</span><span class="sxs-lookup"><span data-stu-id="924c3-186">The inputs and outputs of a clustering algorithm depends on the methodology chosen.</span></span> <span data-ttu-id="924c3-187">Vous pouvez adopter une approche de type distribution, centroïde, connectivité ou basée sur la densité.</span><span class="sxs-lookup"><span data-stu-id="924c3-187">You can take a distribution, centroid, connectivity, or density-based approach.</span></span> <span data-ttu-id="924c3-188">ML.NET prend actuellement en charge une approche de type centroïde à l’aide du clustering K-Means.</span><span class="sxs-lookup"><span data-stu-id="924c3-188">ML.NET currently supports a centroid-based approach using K-Means clustering.</span></span> <span data-ttu-id="924c3-189">Voici quelques exemples de scénarios de clustering :</span><span class="sxs-lookup"><span data-stu-id="924c3-189">Examples of clustering scenarios include:</span></span>

* <span data-ttu-id="924c3-190">Évaluer les segments d’une clientèle d’hôtel en fonction de leurs habitudes et des caractéristiques de l’hôtel.</span><span class="sxs-lookup"><span data-stu-id="924c3-190">Understanding segments of hotel guests based on habits and characteristics of hotel choices.</span></span>
* <span data-ttu-id="924c3-191">Identifier les segments d’une clientèle et les données démographiques pour faciliter la mise en œuvre de campagnes publicitaires ciblées.</span><span class="sxs-lookup"><span data-stu-id="924c3-191">Identifying customer segments and demographics to help build targeted advertising campaigns.</span></span>
* <span data-ttu-id="924c3-192">Classer un inventaire en fonction de métriques de fabrication.</span><span class="sxs-lookup"><span data-stu-id="924c3-192">Categorizing inventory based on manufacturing metrics.</span></span>

### <a name="clustering-trainer"></a><span data-ttu-id="924c3-193">Entraîneur de clustering</span><span class="sxs-lookup"><span data-stu-id="924c3-193">Clustering trainer</span></span>

<span data-ttu-id="924c3-194">Vous pouvez entraîner un modèle de clustering en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-194">You can train a clustering model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.KMeansTrainer>

### <a name="clustering-inputs-and-outputs"></a><span data-ttu-id="924c3-195">Entrées et sorties de clustering</span><span class="sxs-lookup"><span data-stu-id="924c3-195">Clustering inputs and outputs</span></span>

<span data-ttu-id="924c3-196">Les données de caractéristiques d’entrée doivent être <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="924c3-196">The input features data must be <xref:System.Single>.</span></span> <span data-ttu-id="924c3-197">Aucune étiquette n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="924c3-197">No labels are needed.</span></span>

<span data-ttu-id="924c3-198">Cet entraîneur génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="924c3-198">This trainer outputs the following:</span></span>

| <span data-ttu-id="924c3-199">Nom de sortie</span><span class="sxs-lookup"><span data-stu-id="924c3-199">Output Name</span></span> | <span data-ttu-id="924c3-200">Type</span><span class="sxs-lookup"><span data-stu-id="924c3-200">Type</span></span> | <span data-ttu-id="924c3-201">Description</span><span class="sxs-lookup"><span data-stu-id="924c3-201">Description</span></span>|
| -- | -- | -- |
| `Score` | <span data-ttu-id="924c3-202">Vecteur de <xref:System.Single></span><span class="sxs-lookup"><span data-stu-id="924c3-202">vector of <xref:System.Single></span></span> | <span data-ttu-id="924c3-203">Distances entre le point de données spécifique et les centroïdes de tous les clusters</span><span class="sxs-lookup"><span data-stu-id="924c3-203">The distances of the given data point to all clusters' centriods</span></span> |
| `PredictedLabel` | <span data-ttu-id="924c3-204">type de [clé](xref:Microsoft.ML.Data.KeyDataViewType)</span><span class="sxs-lookup"><span data-stu-id="924c3-204">[key](xref:Microsoft.ML.Data.KeyDataViewType) type</span></span> | <span data-ttu-id="924c3-205">Index du cluster le plus proche prédit par le modèle.</span><span class="sxs-lookup"><span data-stu-id="924c3-205">The closest cluster's index predicted by the model.</span></span> |

## <a name="anomaly-detection"></a><span data-ttu-id="924c3-206">Détection des anomalies</span><span class="sxs-lookup"><span data-stu-id="924c3-206">Anomaly detection</span></span>

<span data-ttu-id="924c3-207">Cette tâche crée un modèle de détection d’anomalie à l’aide de la méthode Principal Component Analysis (PCA).</span><span class="sxs-lookup"><span data-stu-id="924c3-207">This task creates an anomaly detection model by using Principal Component Analysis (PCA).</span></span> <span data-ttu-id="924c3-208">La détection d’anomalie PCA vous permet de créer un modèle dans des scénarios où il est facile d’obtenir des données d’apprentissage à partir d’une classe, notamment des transactions valides, mais où il est difficile d’obtenir suffisamment d’échantillons d’anomalies ciblées.</span><span class="sxs-lookup"><span data-stu-id="924c3-208">PCA-Based Anomaly Detection helps you build a model in scenarios where it is easy to obtain training data from one class, such as valid transactions, but difficult to obtain sufficient samples of the targeted anomalies.</span></span>

<span data-ttu-id="924c3-209">Technique éprouvée dans l’apprentissage automatique (Machine Learning), la méthode PCA est fréquemment utilisée dans l’analyse exploratoire des données car elle révèle la structure interne des données et explique la variance dans les données.</span><span class="sxs-lookup"><span data-stu-id="924c3-209">An established technique in machine learning, PCA is frequently used in exploratory data analysis because it reveals the inner structure of the data and explains the variance in the data.</span></span> <span data-ttu-id="924c3-210">PCA fonctionne en analysant les données contenant plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="924c3-210">PCA works by analyzing data that contains multiple variables.</span></span> <span data-ttu-id="924c3-211">Elle recherche des corrélations entre les variables et détermine la combinaison de valeurs qui identifie le mieux les différences dans les résultats.</span><span class="sxs-lookup"><span data-stu-id="924c3-211">It looks for correlations among the variables and determines the combination of values that best captures differences in outcomes.</span></span> <span data-ttu-id="924c3-212">Ces valeurs de fonctionnalité combinées sont utilisées pour créer un espace de fonctionnalités plus compact, appelé principaux composants.</span><span class="sxs-lookup"><span data-stu-id="924c3-212">These combined feature values are used to create a more compact feature space called the principal components.</span></span>

<span data-ttu-id="924c3-213">La détection d’anomalie englobe de nombreuses tâches importantes pour l’apprentissage automatique :</span><span class="sxs-lookup"><span data-stu-id="924c3-213">Anomaly detection encompasses many important tasks in machine learning:</span></span>

* <span data-ttu-id="924c3-214">Identification des transactions potentiellement frauduleuses.</span><span class="sxs-lookup"><span data-stu-id="924c3-214">Identifying transactions that are potentially fraudulent.</span></span>
* <span data-ttu-id="924c3-215">Modèles d’apprentissage signalant une intrusion sur le réseau.</span><span class="sxs-lookup"><span data-stu-id="924c3-215">Learning patterns that indicate that a network intrusion has occurred.</span></span>
* <span data-ttu-id="924c3-216">Recherche de clusters anormaux de patients.</span><span class="sxs-lookup"><span data-stu-id="924c3-216">Finding abnormal clusters of patients.</span></span>
* <span data-ttu-id="924c3-217">Vérification des valeurs entrées dans un système.</span><span class="sxs-lookup"><span data-stu-id="924c3-217">Checking values entered into a system.</span></span>

<span data-ttu-id="924c3-218">Les anomalies constituant, par définition, des événements rares, il peut être difficile de recueillir un échantillon représentatif des données à utiliser pour la modélisation.</span><span class="sxs-lookup"><span data-stu-id="924c3-218">Because anomalies are rare events by definition, it can be difficult to collect a representative sample of data to use for modeling.</span></span> <span data-ttu-id="924c3-219">Les algorithmes inclus dans cette catégorie ont été spécialement conçus pour relever les défis de base qu’impliquent la création et l’apprentissage des modèles à l’aide de jeux de données déséquilibrés.</span><span class="sxs-lookup"><span data-stu-id="924c3-219">The algorithms included in this category have been especially designed to address the core challenges of building and training models by using imbalanced data sets.</span></span>

### <a name="anomaly-detection-trainer"></a><span data-ttu-id="924c3-220">Entraîneur de détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="924c3-220">Anomaly detection trainer</span></span>

<span data-ttu-id="924c3-221">Vous pouvez entraîner un modèle de détection d’anomalie en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-221">You can train an anomaly detection model using the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>

### <a name="anomaly-detection-inputs-and-outputs"></a><span data-ttu-id="924c3-222">Sorties et entrées de la détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="924c3-222">Anomaly detection inputs and outputs</span></span>

<span data-ttu-id="924c3-223">Les caractéristiques d’entrée doivent être un vecteur de taille fixe de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="924c3-223">The input features must be a fixed-sized vector of <xref:System.Single>.</span></span>

<span data-ttu-id="924c3-224">Cet entraîneur génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="924c3-224">This trainer outputs the following:</span></span>

| <span data-ttu-id="924c3-225">Nom de sortie</span><span class="sxs-lookup"><span data-stu-id="924c3-225">Output Name</span></span> | <span data-ttu-id="924c3-226">Type</span><span class="sxs-lookup"><span data-stu-id="924c3-226">Type</span></span> | <span data-ttu-id="924c3-227">Description</span><span class="sxs-lookup"><span data-stu-id="924c3-227">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="924c3-228">Score non négatif sans borne calculé par le modèle de détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="924c3-228">The non-negative, unbounded score that was calculated by the anomaly detection model</span></span> |
| `PredictedLabel` | <xref:System.Boolean> | <span data-ttu-id="924c3-229">Valeur true/false indiquant si l’entrée est une anomalie (PredictedLabel = true) ou non (PredictedLabel = false)</span><span class="sxs-lookup"><span data-stu-id="924c3-229">A true/false value representing whether the input is an anomaly (PredictedLabel=true) or not (PredictedLabel=false)</span></span> |

## <a name="ranking"></a><span data-ttu-id="924c3-230">Classement</span><span class="sxs-lookup"><span data-stu-id="924c3-230">Ranking</span></span>

<span data-ttu-id="924c3-231">Une tâche de classement établit un classement à partir d’un ensemble d’exemples étiquetés.</span><span class="sxs-lookup"><span data-stu-id="924c3-231">A ranking task constructs a ranker from a set of labeled examples.</span></span> <span data-ttu-id="924c3-232">Cet exemple d’ensemble se compose de groupes d’instances qui peuvent être évalués selon un critère donné.</span><span class="sxs-lookup"><span data-stu-id="924c3-232">This example set consists of instance groups that can be scored with a given criteria.</span></span> <span data-ttu-id="924c3-233">Les étiquettes de classement sont {0, 1, 2, 3, 4} pour chaque instance.</span><span class="sxs-lookup"><span data-stu-id="924c3-233">The ranking labels are { 0, 1, 2, 3, 4 } for each instance.</span></span>  <span data-ttu-id="924c3-234">Le classement est formé pour trier les nouveaux groupes d’instance en attribuant un score inconnu à chaque instance.</span><span class="sxs-lookup"><span data-stu-id="924c3-234">The ranker is trained to rank new instance groups with unknown scores for each instance.</span></span> <span data-ttu-id="924c3-235">Les apprenants de classement ML.NET utilisent un [classement basé sur l’apprentissage automatique](https://en.wikipedia.org/wiki/Learning_to_rank).</span><span class="sxs-lookup"><span data-stu-id="924c3-235">ML.NET ranking learners are [machine learned ranking](https://en.wikipedia.org/wiki/Learning_to_rank) based.</span></span>

### <a name="ranking-training-algorithms"></a><span data-ttu-id="924c3-236">Algorithmes d’entraînement de classement</span><span class="sxs-lookup"><span data-stu-id="924c3-236">Ranking training algorithms</span></span>

<span data-ttu-id="924c3-237">Vous pouvez entraîner un modèle de classement en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-237">You can train a ranking model with the following algorithms:</span></span>

* <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer>
* <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer>

### <a name="ranking-input-and-outputs"></a><span data-ttu-id="924c3-238">Entrées et sorties de classement</span><span class="sxs-lookup"><span data-stu-id="924c3-238">Ranking input and outputs</span></span>

<span data-ttu-id="924c3-239">Le type de données des étiquettes d’entrée doit être de type [clé](xref:Microsoft.ML.Data.KeyDataViewType) ou <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="924c3-239">The input label data type must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type or <xref:System.Single>.</span></span> <span data-ttu-id="924c3-240">La valeur de l’étiquette détermine la pertinence, une valeur supérieure indiquant une pertinence plus élevée.</span><span class="sxs-lookup"><span data-stu-id="924c3-240">The value of the label determines relevance, where higher values indicate higher relevance.</span></span> <span data-ttu-id="924c3-241">Si l’étiquette est un type [clé](xref:Microsoft.ML.Data.KeyDataViewType), l’index de clé est la valeur de la pertinence, le plus petit index étant le moins pertinent.</span><span class="sxs-lookup"><span data-stu-id="924c3-241">If the label is a [key](xref:Microsoft.ML.Data.KeyDataViewType) type, then the key index is the relevance value, where the smallest index is the least relevant.</span></span> <span data-ttu-id="924c3-242">Si l’étiquette est un <xref:System.Single>, une valeur plus grande indique une pertinence plus élevée.</span><span class="sxs-lookup"><span data-stu-id="924c3-242">If the label is a <xref:System.Single>, larger values indicate higher relevance.</span></span>

<span data-ttu-id="924c3-243">Les données de caractéristique doivent être un vecteur de taille fixe de <xref:System.Single> et la colonne du groupe de lignes d’entrée doit être de type [clé](xref:Microsoft.ML.Data.KeyDataViewType).</span><span class="sxs-lookup"><span data-stu-id="924c3-243">The feature data must be a fixed size vector of <xref:System.Single> and input row group column must be [key](xref:Microsoft.ML.Data.KeyDataViewType) type.</span></span>

<span data-ttu-id="924c3-244">Cet entraîneur génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="924c3-244">This trainer outputs the following:</span></span>

| <span data-ttu-id="924c3-245">Nom de sortie</span><span class="sxs-lookup"><span data-stu-id="924c3-245">Output Name</span></span> | <span data-ttu-id="924c3-246">Type</span><span class="sxs-lookup"><span data-stu-id="924c3-246">Type</span></span> | <span data-ttu-id="924c3-247">Description</span><span class="sxs-lookup"><span data-stu-id="924c3-247">Description</span></span>|
| -- | -- | -- |
| `Score` | <xref:System.Single> | <span data-ttu-id="924c3-248">Score sans borne calculé par le modèle pour déterminer la prédiction</span><span class="sxs-lookup"><span data-stu-id="924c3-248">The unbounded score that was calculated by the model to determine the prediction</span></span> |

## <a name="recommendation"></a><span data-ttu-id="924c3-249">Recommandation</span><span class="sxs-lookup"><span data-stu-id="924c3-249">Recommendation</span></span>

<span data-ttu-id="924c3-250">Une tâche de recommandation permet de dresser la liste des produits ou services recommandés.</span><span class="sxs-lookup"><span data-stu-id="924c3-250">A recommendation task enables producing a list of recommended products or services.</span></span> <span data-ttu-id="924c3-251">ML.NET utilise la méthode [Factorisation de matrice (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), un algorithme de [filtrage collaboratif](https://en.wikipedia.org/wiki/Collaborative_filtering) pour obtenir des recommandations lorsque votre catalogue contient des données d’évaluation de produit historiques.</span><span class="sxs-lookup"><span data-stu-id="924c3-251">ML.NET uses [Matrix factorization (MF)](https://en.wikipedia.org/wiki/Matrix_factorization_%28recommender_systems%29), a [collaborative filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) algorithm for recommendations when you have historical product rating data in your catalog.</span></span> <span data-ttu-id="924c3-252">Par exemple, vous disposez des données d’évaluation de films historiques pour vos utilisateurs et souhaitez leur recommander d’autres vidéos.</span><span class="sxs-lookup"><span data-stu-id="924c3-252">For example, you have historical movie rating data for your users and want to recommend  other movies they are likely to watch next.</span></span>

### <a name="recommendation-training-algorithms"></a><span data-ttu-id="924c3-253">Algorithmes d’entraînement de recommandation</span><span class="sxs-lookup"><span data-stu-id="924c3-253">Recommendation training algorithms</span></span>

<span data-ttu-id="924c3-254">Vous pouvez entraîner un modèle de recommandation en utilisant les algorithmes suivants :</span><span class="sxs-lookup"><span data-stu-id="924c3-254">You can train a recommendation model with the following algorithm:</span></span>

* <xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer>

## <a name="forecasting"></a><span data-ttu-id="924c3-255">Prévisions</span><span class="sxs-lookup"><span data-stu-id="924c3-255">Forecasting</span></span>

<span data-ttu-id="924c3-256">La tâche de prévision utilise les données de série chronologique antérieures pour faire des prédictions concernant le comportement futur.</span><span class="sxs-lookup"><span data-stu-id="924c3-256">The forecasting task use past time-series data to make predictions about future behavior.</span></span> <span data-ttu-id="924c3-257">Les scénarios applicables aux prévisions sont les prévisions météorologiques, les prédictions de ventes saisonnières et la maintenance prédictive.</span><span class="sxs-lookup"><span data-stu-id="924c3-257">Scenarios applicable to forecasting include weather forecasting, seasonal sales predictions, and predictive maintenance,</span></span>

### <a name="forecasting-trainers"></a><span data-ttu-id="924c3-258">Prédictions de formateurs</span><span class="sxs-lookup"><span data-stu-id="924c3-258">Forecasting trainers</span></span>

<span data-ttu-id="924c3-259">Vous pouvez effectuer l’apprentissage d’un modèle de prévision avec l’algorithme suivant :</span><span class="sxs-lookup"><span data-stu-id="924c3-259">You can train a forecasting model with the following algorithm:</span></span>

<xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa*>
