---
title: Qu’est-ce que Model Builder et comment fonctionne-t-il ?
description: Comment utiliser Model Builder ML.NET pour entraîner automatiquement un modèle Machine Learning
author: natke
ms.date: 08/07/2019
ms.custom: overview
ms.openlocfilehash: 77fe56dba3532617ad9fb0c89bfaac7c8e031ce7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971527"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="df360-103">Qu’est-ce que Model Builder et comment fonctionne-t-il ?</span><span class="sxs-lookup"><span data-stu-id="df360-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="df360-104">Model Builder ML.NET est une extension graphique intuitive de Visual Studio, qui permet de générer, d’entraîner et de déployer des modèles Machine Learning personnalisés.</span><span class="sxs-lookup"><span data-stu-id="df360-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="df360-105">Model Builder utilise le Machine Learning automatisé (AutoML) pour explorer différents algorithmes et paramètres de machine learning afin de vous aider à trouver le modèle qui convient le mieux à votre scénario.</span><span class="sxs-lookup"><span data-stu-id="df360-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="df360-106">Vous n’avez pas besoin d’une expertise en machine learning pour utiliser Model Builder.</span><span class="sxs-lookup"><span data-stu-id="df360-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="df360-107">Vous avez seulement besoin de quelques données et d’un problème à résoudre.</span><span class="sxs-lookup"><span data-stu-id="df360-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="df360-108">Model Builder génère le code pour ajouter le modèle à votre application .NET.</span><span class="sxs-lookup"><span data-stu-id="df360-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animation de l’interface utilisateur de l’extension Model Builder de Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="df360-110">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="df360-110">Model Builder is currently in Preview.</span></span>

## <a name="scenarios"></a><span data-ttu-id="df360-111">Scénarios</span><span class="sxs-lookup"><span data-stu-id="df360-111">Scenarios</span></span>

<span data-ttu-id="df360-112">Vous pouvez soumettre de nombreux scénarios différents à Model Builder pour générer un modèle Machine Learning pour votre application.</span><span class="sxs-lookup"><span data-stu-id="df360-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="df360-113">Un scénario est une description du type de prédiction que vous voulez faire avec vos données.</span><span class="sxs-lookup"><span data-stu-id="df360-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="df360-114">Exemple :</span><span class="sxs-lookup"><span data-stu-id="df360-114">For example:</span></span>

- <span data-ttu-id="df360-115">prédire le volume futur des ventes d’un produit en fonction de l’historique des données des ventes</span><span class="sxs-lookup"><span data-stu-id="df360-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="df360-116">classer des sentiments en positif ou en négatif en fonction d’avis émis par les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="df360-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="df360-117">détecter si une transaction bancaire est frauduleuse</span><span class="sxs-lookup"><span data-stu-id="df360-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="df360-118">rediriger les problèmes indiqués dans les commentaires des clients vers l’équipe appropriée dans votre entreprise</span><span class="sxs-lookup"><span data-stu-id="df360-118">route customer feedback issues to the correct team in your company</span></span>

## <a name="choose-a-model-type"></a><span data-ttu-id="df360-119">Choisir un type de modèle</span><span class="sxs-lookup"><span data-stu-id="df360-119">Choose a model type</span></span>

<span data-ttu-id="df360-120">Dans Model Builder, vous devez sélectionner un type de modèle Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="df360-120">In Model Builder, you need to select a machine learning model type.</span></span> <span data-ttu-id="df360-121">Le type de modèle dépend du type de prédiction que vous essayez de faire.</span><span class="sxs-lookup"><span data-stu-id="df360-121">The type of model depends on what sort of prediction you are trying to make.</span></span>

<span data-ttu-id="df360-122">Pour les scénarios qui prédisent un nombre, le type de modèle Machine Learning est appelé `regression`.</span><span class="sxs-lookup"><span data-stu-id="df360-122">For scenarios that predict a number, the machine learning model type is called `regression`.</span></span>

<span data-ttu-id="df360-123">Pour les scénarios qui prédisent une catégorie, le type de modèle est `classification`.</span><span class="sxs-lookup"><span data-stu-id="df360-123">For scenarios that predict a category, the model type is `classification`.</span></span> <span data-ttu-id="df360-124">Il existe deux types de classification :</span><span class="sxs-lookup"><span data-stu-id="df360-124">There are two types of classification:</span></span>

- <span data-ttu-id="df360-125">où il n’y a que 2 catégories : `binary classification`.</span><span class="sxs-lookup"><span data-stu-id="df360-125">where there are only 2 categories: `binary classification`.</span></span>
- <span data-ttu-id="df360-126">où il y a 3 catégories ou plus : `multiclass classification`.</span><span class="sxs-lookup"><span data-stu-id="df360-126">where there are three or more categories: `multiclass classification`.</span></span>

### <a name="which-model-type-is-right-for-me"></a><span data-ttu-id="df360-127">Quel est le type de modèle qui me convient ?</span><span class="sxs-lookup"><span data-stu-id="df360-127">Which model type is right for me?</span></span>

#### <a name="predict-a-category-when-there-are-only-two-categories"></a><span data-ttu-id="df360-128">Prédire une catégorie (quand il n’y a que deux catégories)</span><span class="sxs-lookup"><span data-stu-id="df360-128">Predict a category (when there are only two categories)</span></span>

<span data-ttu-id="df360-129">La classification binaire est utilisée pour catégoriser des données en deux catégories (oui/non ; réussite/échec ; vrai/faux ; positif/négatif).</span><span class="sxs-lookup"><span data-stu-id="df360-129">Binary classification is used to categorize data into two categories (yes/no; pass/fail; true/false; positive/negative).</span></span>

![Diagramme montrant des exemples de classification binaire incluant la détection des fraudes, l’atténuation des risques et le filtrage d’applications](media/binary-classification-examples.png)

<span data-ttu-id="df360-131">L’analyse des sentiments peut être utilisée pour prédire le sentiment positif ou négatif des commentaires des clients.</span><span class="sxs-lookup"><span data-stu-id="df360-131">Sentiment analysis can be used to predict positive or negative sentiment of customer feedback.</span></span> <span data-ttu-id="df360-132">C’est un exemple de type de modèle de classification binaire.</span><span class="sxs-lookup"><span data-stu-id="df360-132">It is an example of a binary classification model type.</span></span>

<span data-ttu-id="df360-133">Si votre scénario nécessite une classification en deux catégories, vous pouvez utiliser ce modèle avec votre propre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="df360-133">If your scenario requires classification into two categories, you can use this template with your own dataset.</span></span>

#### <a name="predict-a-category-when-there-are-three-or-more-categories"></a><span data-ttu-id="df360-134">Prédire une catégorie (quand il y a trois catégories ou plus)</span><span class="sxs-lookup"><span data-stu-id="df360-134">Predict a category (when there are three or more categories)</span></span>

<span data-ttu-id="df360-135">La classification multiclasse peut être utilisée pour catégoriser des données en trois classes ou plus.</span><span class="sxs-lookup"><span data-stu-id="df360-135">Multiclass classification can be used to categorize data into three or more classes.</span></span>

![Exemples de classification multiclasse incluant la classification de documents et de produits, le routage de tickets de support et la hiérarchisation des problèmes des clients](media/multiclass-classification-examples.png)

<span data-ttu-id="df360-137">La classification des problèmes peut être utilisée pour catégoriser des problèmes indiqués dans les commentaires de clients (par exemple sur GitHub) en utilisant le titre du problème et sa description.</span><span class="sxs-lookup"><span data-stu-id="df360-137">Issue classification can be used to categorize customer feedback (for example, on GitHub) issues using the issue title and description.</span></span> <span data-ttu-id="df360-138">C’est un exemple de type de modèle de classification multiclasse.</span><span class="sxs-lookup"><span data-stu-id="df360-138">It is an example of the multi-class classification model type.</span></span>

<span data-ttu-id="df360-139">Vous pouvez utiliser le modèle de classification de problèmes pour votre scénario si vous voulez catégoriser des données en trois catégories ou plus.</span><span class="sxs-lookup"><span data-stu-id="df360-139">You can use the issue classification template for your scenario if you want to categorize data into three or more categories.</span></span>

#### <a name="predict-a-number"></a><span data-ttu-id="df360-140">Prédire un nombre</span><span class="sxs-lookup"><span data-stu-id="df360-140">Predict a number</span></span>

<span data-ttu-id="df360-141">La régression est utilisée pour prédire des nombres.</span><span class="sxs-lookup"><span data-stu-id="df360-141">Regression is used to predict numbers.</span></span>

![Diagramme montrant des exemples de régression, comme la prédiction de prix, les prévisions de ventes et la maintenance prédictive](media/regression-examples.png)

<span data-ttu-id="df360-143">La prédiction des prix peut être utilisée pour prédire le prix d’une maison en fonction de son emplacement, de sa taille et d’autres caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="df360-143">Price prediction can be used to predict house prices using location, size, and other characteristics of the house.</span></span> <span data-ttu-id="df360-144">C’est un exemple de type de modèle de régression.</span><span class="sxs-lookup"><span data-stu-id="df360-144">It is an example of a regression model type.</span></span>

<span data-ttu-id="df360-145">Vous pouvez utiliser le modèle de prédiction des prix pour votre scénario si vous voulez prédire une valeur numérique avec votre propre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="df360-145">You can use the price prediction template for your scenario if you want to predict a numerical value with your own dataset.</span></span>

#### <a name="custom-scenario-choose-your-model-type"></a><span data-ttu-id="df360-146">Scénario personnalisé (choisir votre type de modèle)</span><span class="sxs-lookup"><span data-stu-id="df360-146">Custom scenario (choose your model type)</span></span>

<span data-ttu-id="df360-147">Le scénario personnalisé vous permet de choisir manuellement votre type de modèle.</span><span class="sxs-lookup"><span data-stu-id="df360-147">The custom scenario allows you to manually choose your model type.</span></span>

## <a name="data"></a><span data-ttu-id="df360-148">Données</span><span class="sxs-lookup"><span data-stu-id="df360-148">Data</span></span>

<span data-ttu-id="df360-149">Une fois que vous avez choisi votre type de modèle, Model Builder vous demande de fournir un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="df360-149">Once you have chosen your model type, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="df360-150">Les données sont utilisées pour entraîner, évaluer et choisir le meilleur modèle pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="df360-150">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagramme montrant les étapes de Model Builder](media/model-builder-steps.png)

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="df360-152">Choisir le résultat à prédire (étiquette)</span><span class="sxs-lookup"><span data-stu-id="df360-152">Choose the output to predict (label)</span></span>

<span data-ttu-id="df360-153">Un jeu de données est une table de lignes d’exemples et de colonnes d’attributs pour l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df360-153">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="df360-154">Chaque ligne a :</span><span class="sxs-lookup"><span data-stu-id="df360-154">Each row has:</span></span>

- <span data-ttu-id="df360-155">une **étiquette** (l’attribut que vous voulez prédire)</span><span class="sxs-lookup"><span data-stu-id="df360-155">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="df360-156">des **caractéristiques** (des attributs qui sont utilisés comme entrées pour prédire l’étiquette).</span><span class="sxs-lookup"><span data-stu-id="df360-156">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="df360-157">Pour le scénario de prédiction de prix d’une maison, les caractéristiques peuvent être :</span><span class="sxs-lookup"><span data-stu-id="df360-157">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="df360-158">la superficie de la maison</span><span class="sxs-lookup"><span data-stu-id="df360-158">the square footage of the house</span></span>
- <span data-ttu-id="df360-159">le nombre de chambres et de salles de bain</span><span class="sxs-lookup"><span data-stu-id="df360-159">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="df360-160">le code postal</span><span class="sxs-lookup"><span data-stu-id="df360-160">the zip code</span></span>

<span data-ttu-id="df360-161">L’étiquette est l’historique des prix des maisons pour cette ligne de valeurs correspondant à la superficie, aux chambres et aux salles de bain, et au code postal.</span><span class="sxs-lookup"><span data-stu-id="df360-161">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tableau montrant des lignes et des colonnes de données sur les prix de maisons avec des caractéristiques consistant en une taille, un nombre de pièces, un code postal et une étiquette de prix](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="df360-163">Exemples de jeux de données</span><span class="sxs-lookup"><span data-stu-id="df360-163">Example datasets</span></span>

<span data-ttu-id="df360-164">Si vous n’avez pas encore vos propres données, essayez un de ces jeux de données :</span><span class="sxs-lookup"><span data-stu-id="df360-164">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="df360-165">Scénario</span><span class="sxs-lookup"><span data-stu-id="df360-165">Scenario</span></span>|<span data-ttu-id="df360-166">Type de modèle</span><span class="sxs-lookup"><span data-stu-id="df360-166">Model Type</span></span>|<span data-ttu-id="df360-167">Données</span><span class="sxs-lookup"><span data-stu-id="df360-167">Data</span></span>|<span data-ttu-id="df360-168">Etiquette</span><span class="sxs-lookup"><span data-stu-id="df360-168">Label</span></span>|<span data-ttu-id="df360-169">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="df360-169">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="df360-170">Prédiction des prix</span><span class="sxs-lookup"><span data-stu-id="df360-170">Price prediction</span></span>|<span data-ttu-id="df360-171">régression</span><span class="sxs-lookup"><span data-stu-id="df360-171">regression</span></span>|[<span data-ttu-id="df360-172">Données de courses de taxi</span><span class="sxs-lookup"><span data-stu-id="df360-172">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="df360-173">Tarifs</span><span class="sxs-lookup"><span data-stu-id="df360-173">Fare</span></span>|<span data-ttu-id="df360-174">Heure, distance du trajet</span><span class="sxs-lookup"><span data-stu-id="df360-174">Trip time, distance</span></span>|
|<span data-ttu-id="df360-175">Détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="df360-175">Anomaly detection</span></span>|<span data-ttu-id="df360-176">classification binaire</span><span class="sxs-lookup"><span data-stu-id="df360-176">binary classification</span></span>|[<span data-ttu-id="df360-177">Données de ventes de produits</span><span class="sxs-lookup"><span data-stu-id="df360-177">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="df360-178">Ventes de produits</span><span class="sxs-lookup"><span data-stu-id="df360-178">Product Sales</span></span>|<span data-ttu-id="df360-179">Mois</span><span class="sxs-lookup"><span data-stu-id="df360-179">Month</span></span>|
|<span data-ttu-id="df360-180">Analyse des sentiments</span><span class="sxs-lookup"><span data-stu-id="df360-180">Sentiment analysis</span></span>|<span data-ttu-id="df360-181">classification binaire</span><span class="sxs-lookup"><span data-stu-id="df360-181">binary classification</span></span>|[<span data-ttu-id="df360-182">Données de commentaires de site web</span><span class="sxs-lookup"><span data-stu-id="df360-182">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="df360-183">Étiquette (0 quand le sentiment est négatif, 1 quand il est positif)</span><span class="sxs-lookup"><span data-stu-id="df360-183">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="df360-184">Commentaire, Année</span><span class="sxs-lookup"><span data-stu-id="df360-184">Comment, Year</span></span>|
|<span data-ttu-id="df360-185">Détection des fraudes</span><span class="sxs-lookup"><span data-stu-id="df360-185">Fraud detection</span></span>|<span data-ttu-id="df360-186">classification binaire</span><span class="sxs-lookup"><span data-stu-id="df360-186">binary classification</span></span>|[<span data-ttu-id="df360-187">Données de carte de crédit</span><span class="sxs-lookup"><span data-stu-id="df360-187">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="df360-188">Classe (1 en cas de fraude, sinon 0)</span><span class="sxs-lookup"><span data-stu-id="df360-188">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="df360-189">Quantité, V1-V28 (caractéristiques anonymisées)</span><span class="sxs-lookup"><span data-stu-id="df360-189">Amount, V1-V28 (anonymized features)</span></span>|
|<span data-ttu-id="df360-190">Classification de texte</span><span class="sxs-lookup"><span data-stu-id="df360-190">Text classification</span></span>|<span data-ttu-id="df360-191">classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="df360-191">multiclass classification</span></span>|[<span data-ttu-id="df360-192">Données de problèmes GitHub</span><span class="sxs-lookup"><span data-stu-id="df360-192">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="df360-193">Zone</span><span class="sxs-lookup"><span data-stu-id="df360-193">Area</span></span>|<span data-ttu-id="df360-194">Titre, Description</span><span class="sxs-lookup"><span data-stu-id="df360-194">Title, Description</span></span>|

## <a name="train"></a><span data-ttu-id="df360-195">Recyclage</span><span class="sxs-lookup"><span data-stu-id="df360-195">Train</span></span>

<span data-ttu-id="df360-196">Une fois que vous avez sélectionné votre scénario, vos données et votre étiquette, Model Builder entraîne le modèle.</span><span class="sxs-lookup"><span data-stu-id="df360-196">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="df360-197">Qu’est-ce que l’entraînement ?</span><span class="sxs-lookup"><span data-stu-id="df360-197">What is training?</span></span>

<span data-ttu-id="df360-198">L’entraînement est un processus automatique par lequel Model Builder apprend à votre modèle comment répondre aux questions de votre scénario.</span><span class="sxs-lookup"><span data-stu-id="df360-198">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="df360-199">Une fois entraîné, votre modèle peut faire des prédictions avec des données en entrée qu’il n’avait pas vues avant.</span><span class="sxs-lookup"><span data-stu-id="df360-199">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="df360-200">Par exemple, si vous prédisez des prix de maisons et qu’une nouvelle maison apparaît sur le marché, vous pouvez prévoir son prix de vente.</span><span class="sxs-lookup"><span data-stu-id="df360-200">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="df360-201">Comme Model Builder utilise le Machine Learning automatisé (AutoML), il ne nécessite aucune entrée ou optimisation de votre part pendant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="df360-201">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

## <a name="evaluate"></a><span data-ttu-id="df360-202">Évaluer</span><span class="sxs-lookup"><span data-stu-id="df360-202">Evaluate</span></span>

<span data-ttu-id="df360-203">L’évaluation est le processus consistant à utiliser le modèle entraîné pour faire des prédictions avec de nouvelles données de test, puis à mesurer la qualité des prédictions.</span><span class="sxs-lookup"><span data-stu-id="df360-203">Evaluation is the process of using the trained model to make predictions with new test data, and then measuring how good the predictions are.</span></span>

<span data-ttu-id="df360-204">Model Builder divise les données d’entraînement en un jeu d’entraînement et un jeu de test.</span><span class="sxs-lookup"><span data-stu-id="df360-204">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="df360-205">Les données d’entraînement (80 %) sont utilisées pour entraîner votre modèle et les données de test (20 %) sont conservées à part pour évaluer votre modèle.</span><span class="sxs-lookup"><span data-stu-id="df360-205">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span> <span data-ttu-id="df360-206">Model Builder utilise des métriques pour mesurer la qualité du modèle.</span><span class="sxs-lookup"><span data-stu-id="df360-206">Model Builder uses metrics to measure how good the model is.</span></span> <span data-ttu-id="df360-207">Les métriques spécifiques utilisées dépendent du type de modèle.</span><span class="sxs-lookup"><span data-stu-id="df360-207">The specific metrics used are dependent on the type of model.</span></span> <span data-ttu-id="df360-208">Pour plus d’informations, consultez [Métriques d’évaluation des modèles](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="df360-208">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="df360-209">Améliorer</span><span class="sxs-lookup"><span data-stu-id="df360-209">Improve</span></span>

<span data-ttu-id="df360-210">Si le score de performances de votre modèle n’est pas aussi bon que souhaité, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="df360-210">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="df360-211">Entraîner sur une période de temps plus longue.</span><span class="sxs-lookup"><span data-stu-id="df360-211">Train for a longer period of time.</span></span> <span data-ttu-id="df360-212">Avec plus de temps, le moteur Machine Learning automatisé va essayer plus d’algorithmes et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="df360-212">With more time, the automated machine learning engine to try more algorithms and settings.</span></span>

- <span data-ttu-id="df360-213">Ajouter des données.</span><span class="sxs-lookup"><span data-stu-id="df360-213">Add more data.</span></span> <span data-ttu-id="df360-214">Parfois, la quantité de données n’est pas suffisante pour entraîner un modèle Machine Learning de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="df360-214">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="df360-215">Équilibrer vos données.</span><span class="sxs-lookup"><span data-stu-id="df360-215">Balance your data.</span></span> <span data-ttu-id="df360-216">Pour les tâches de classification, vérifiez que le jeu d’entraînement est équilibré entre les différentes catégories.</span><span class="sxs-lookup"><span data-stu-id="df360-216">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="df360-217">Par exemple, si vous avez quatre classes pour 100 exemples d’entraînement et que les deux premières classes (étiquette1 et étiquette2) sont utilisées pour 90 enregistrements, mais que les deux autres (étiquette3 et étiquette4) sont utilisées seulement sur les 10 enregistrements restants, l’absence de données équilibrées peut faire que votre modèle aura du mal à prédire correctement étiquette3 ou étiquette4.</span><span class="sxs-lookup"><span data-stu-id="df360-217">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="df360-218">Code</span><span class="sxs-lookup"><span data-stu-id="df360-218">Code</span></span>

<span data-ttu-id="df360-219">Après la phase d’évaluation, Model Builder génère un fichier de modèle et du code que vous pouvez utiliser pour ajouter le modèle à votre application.</span><span class="sxs-lookup"><span data-stu-id="df360-219">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="df360-220">Les modèles ML.NET sont enregistrés sous la forme d’un fichier zip.</span><span class="sxs-lookup"><span data-stu-id="df360-220">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="df360-221">Le code pour charger et utiliser votre modèle est ajouté en tant que nouveau projet dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="df360-221">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="df360-222">Model Builder ajoute également un exemple d’application console que vous pouvez exécuter pour voir votre modèle en action.</span><span class="sxs-lookup"><span data-stu-id="df360-222">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="df360-223">En outre, Model Builder produit le code qui a généré le modèle, ce qui vous permet de comprendre les étapes utilisées pour cette génération.</span><span class="sxs-lookup"><span data-stu-id="df360-223">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="df360-224">Vous pouvez également utiliser le code de l’entraînement du modèle pour réentraîner votre modèle avec de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="df360-224">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="df360-225">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="df360-225">What's next?</span></span>

<span data-ttu-id="df360-226">[Installer](how-to-guides/install-model-builder.md) l’extension Visual Studio Model Builder</span><span class="sxs-lookup"><span data-stu-id="df360-226">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="df360-227">Essayer [le scénario de prédiction des prix ou un autre scénario de régression](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="df360-227">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
