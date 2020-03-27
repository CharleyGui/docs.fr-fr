---
title: Qu’est-ce que Model Builder et comment fonctionne-t-il ?
description: Comment utiliser Model Builder ML.NET pour entraîner automatiquement un modèle Machine Learning
ms.date: 03/25/2020
ms.custom: overview, mlnet-tooling
ms.openlocfilehash: 9cf66455109908ebd9fc10e62cf4f067609b57d9
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344770"
---
# <a name="what-is-model-builder-and-how-does-it-work"></a><span data-ttu-id="d0a51-103">Qu’est-ce que Model Builder et comment fonctionne-t-il ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-103">What is Model Builder and how does it work?</span></span>

<span data-ttu-id="d0a51-104">Model Builder ML.NET est une extension graphique intuitive de Visual Studio, qui permet de générer, d’entraîner et de déployer des modèles Machine Learning personnalisés.</span><span class="sxs-lookup"><span data-stu-id="d0a51-104">ML.NET Model Builder is an intuitive graphical Visual Studio extension to build, train, and deploy custom machine learning models.</span></span>

<span data-ttu-id="d0a51-105">Model Builder utilise le Machine Learning automatisé (AutoML) pour explorer différents algorithmes et paramètres de machine learning afin de vous aider à trouver le modèle qui convient le mieux à votre scénario.</span><span class="sxs-lookup"><span data-stu-id="d0a51-105">Model Builder uses automated machine learning (AutoML) to explore different machine learning algorithms and settings to help you find the one that best suits your scenario.</span></span>

<span data-ttu-id="d0a51-106">Vous n’avez pas besoin d’une expertise en machine learning pour utiliser Model Builder.</span><span class="sxs-lookup"><span data-stu-id="d0a51-106">You don't need machine learning expertise to use Model Builder.</span></span> <span data-ttu-id="d0a51-107">Vous avez seulement besoin de quelques données et d’un problème à résoudre.</span><span class="sxs-lookup"><span data-stu-id="d0a51-107">All you need is some data, and a problem to solve.</span></span> <span data-ttu-id="d0a51-108">Model Builder génère le code pour ajouter le modèle à votre application .NET.</span><span class="sxs-lookup"><span data-stu-id="d0a51-108">Model Builder generates the code to add the model to your .NET application.</span></span>

![Animation de l’interface utilisateur de l’extension Model Builder de Visual Studio](media/ml-dotnet-model-builder.gif)

> [!NOTE]
> <span data-ttu-id="d0a51-110">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="d0a51-110">Model Builder is currently in Preview.</span></span>

## <a name="scenario"></a><span data-ttu-id="d0a51-111">Scénario</span><span class="sxs-lookup"><span data-stu-id="d0a51-111">Scenario</span></span>

<span data-ttu-id="d0a51-112">Vous pouvez soumettre de nombreux scénarios différents à Model Builder pour générer un modèle Machine Learning pour votre application.</span><span class="sxs-lookup"><span data-stu-id="d0a51-112">You can bring many different scenarios to Model Builder, to generate a machine learning model for your application.</span></span>

<span data-ttu-id="d0a51-113">Un scénario est une description du type de prédiction que vous voulez faire avec vos données.</span><span class="sxs-lookup"><span data-stu-id="d0a51-113">A scenario is a description of the type of prediction you want to make using your data.</span></span> <span data-ttu-id="d0a51-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d0a51-114">For example:</span></span>

- <span data-ttu-id="d0a51-115">prédire le volume futur des ventes d’un produit en fonction de l’historique des données des ventes</span><span class="sxs-lookup"><span data-stu-id="d0a51-115">predict future product sales volume based on historical sales data</span></span>
- <span data-ttu-id="d0a51-116">classer des sentiments en positif ou en négatif en fonction d’avis émis par les utilisateurs</span><span class="sxs-lookup"><span data-stu-id="d0a51-116">classify sentiments as positive or negative based on customer reviews</span></span>
- <span data-ttu-id="d0a51-117">détecter si une transaction bancaire est frauduleuse</span><span class="sxs-lookup"><span data-stu-id="d0a51-117">detect whether a banking transaction is fraudulent</span></span>
- <span data-ttu-id="d0a51-118">rediriger les problèmes indiqués dans les commentaires des clients vers l’équipe appropriée dans votre entreprise</span><span class="sxs-lookup"><span data-stu-id="d0a51-118">route customer feedback issues to the correct team in your company</span></span>

### <a name="which-machine-learning-scenario-is-right-for-me"></a><span data-ttu-id="d0a51-119">Quel est le bon scénario Machine Learning pour moi ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-119">Which machine learning scenario is right for me?</span></span>

<span data-ttu-id="d0a51-120">Dans Model Builder, vous devez sélectionner un scénario.</span><span class="sxs-lookup"><span data-stu-id="d0a51-120">In Model Builder, you need to select a scenario.</span></span> <span data-ttu-id="d0a51-121">Le type de scénario dépend du type de prédiction que vous essayez de faire.</span><span class="sxs-lookup"><span data-stu-id="d0a51-121">The type of scenario depends on what type of prediction you are trying to make.</span></span>

#### <a name="text-classification"></a><span data-ttu-id="d0a51-122">Classification de texte</span><span class="sxs-lookup"><span data-stu-id="d0a51-122">Text classification</span></span>

<span data-ttu-id="d0a51-123">La classification est utilisée pour classer les données en catégories.</span><span class="sxs-lookup"><span data-stu-id="d0a51-123">Classification is used to categorize data into categories.</span></span>

![Diagramme montrant des exemples de classification binaire incluant la détection des fraudes, l’atténuation des risques et le filtrage d’applications](media/binary-classification-examples.png)

![Exemples de classification multiclasse incluant la classification de documents et de produits, le routage de tickets de support et la hiérarchisation des problèmes des clients](media/multiclass-classification-examples.png)

#### <a name="value-prediction"></a><span data-ttu-id="d0a51-126">Prévision de la valeur</span><span class="sxs-lookup"><span data-stu-id="d0a51-126">Value prediction</span></span>

<span data-ttu-id="d0a51-127">La régression est utilisée pour prédire des nombres.</span><span class="sxs-lookup"><span data-stu-id="d0a51-127">Regression is used to predict numbers.</span></span>

![Diagramme montrant des exemples de régression, comme la prédiction de prix, les prévisions de ventes et la maintenance prédictive](media/regression-examples.png)

#### <a name="image-classification"></a><span data-ttu-id="d0a51-129">Classification d’image</span><span class="sxs-lookup"><span data-stu-id="d0a51-129">Image classification</span></span>

<span data-ttu-id="d0a51-130">La classification des images peut être utilisée pour identifier les images de différentes catégories.</span><span class="sxs-lookup"><span data-stu-id="d0a51-130">Image classification can be used to identify images of different categories.</span></span> <span data-ttu-id="d0a51-131">Par exemple, différents types de terrain ou d’animaux ou de défauts de fabrication.</span><span class="sxs-lookup"><span data-stu-id="d0a51-131">For example, different types of terrain or animals or manufacturing defects.</span></span>

<span data-ttu-id="d0a51-132">Vous pouvez utiliser le scénario de classification d’image si vous avez un ensemble d’images, et que vous souhaitez classer les images en différentes catégories.</span><span class="sxs-lookup"><span data-stu-id="d0a51-132">You can use the image classification scenario if you have a set of images, and you want to classify the images into different categories.</span></span>

#### <a name="recommendation"></a><span data-ttu-id="d0a51-133">Recommandation</span><span class="sxs-lookup"><span data-stu-id="d0a51-133">Recommendation</span></span>

<span data-ttu-id="d0a51-134">Le scénario de recommandation prévoit une liste d’éléments suggérés pour un utilisateur particulier, en fonction de la similitude de leurs goûts et de leurs aversions pour les autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d0a51-134">The recommendation scenario predicts a list of suggested items for a particular user, based on how similar their likes and dislikes are to other users'.</span></span>

<span data-ttu-id="d0a51-135">Vous pouvez utiliser le scénario de recommandation lorsque vous avez un ensemble d’utilisateurs et un ensemble de «produits», tels que des articles à acheter, des films, des livres ou des émissions de télévision, ainsi qu’un ensemble de utilisateurs "évaluations" de ces produits.</span><span class="sxs-lookup"><span data-stu-id="d0a51-135">You can use the recommendation scenario when you have a set of users and a set of "products", such as items to purchase, movies, books, or TV shows, along with a set of users' "ratings" of those products.</span></span>

## <a name="environment"></a><span data-ttu-id="d0a51-136">Environnement</span><span class="sxs-lookup"><span data-stu-id="d0a51-136">Environment</span></span>

<span data-ttu-id="d0a51-137">Vous pouvez former votre modèle d’apprentissage automatique localement sur votre machine ou dans le cloud sur Azure.</span><span class="sxs-lookup"><span data-stu-id="d0a51-137">You can train your machine learning model locally on your machine or in the cloud on Azure.</span></span>

<span data-ttu-id="d0a51-138">Lorsque vous vous entraînez localement, vous travaillez dans les contraintes de vos ressources informatiques (processeur, mémoire et disque).</span><span class="sxs-lookup"><span data-stu-id="d0a51-138">When you train locally, you work within the constraints of your computer resources (CPU, memory, and disk).</span></span> <span data-ttu-id="d0a51-139">Lorsque vous vous entraînez dans le cloud, vous pouvez intensifier vos ressources pour répondre aux exigences de votre scénario, en particulier pour les grands jeux de données.</span><span class="sxs-lookup"><span data-stu-id="d0a51-139">When you train in the cloud, you can scale up your resources to meet the demands of your scenario, especially for large datasets.</span></span>

<span data-ttu-id="d0a51-140">La formation locale est soutenue pour tous les scénarios.</span><span class="sxs-lookup"><span data-stu-id="d0a51-140">Local training is supported for all scenarios.</span></span>

<span data-ttu-id="d0a51-141">La formation Azure est soutenue pour la classification d’images.</span><span class="sxs-lookup"><span data-stu-id="d0a51-141">Azure training is supported for Image Classification.</span></span>

## <a name="data"></a><span data-ttu-id="d0a51-142">Données</span><span class="sxs-lookup"><span data-stu-id="d0a51-142">Data</span></span>

<span data-ttu-id="d0a51-143">Une fois que vous avez choisi votre scénario, Model Builder vous demande de fournir un jeu de données.</span><span class="sxs-lookup"><span data-stu-id="d0a51-143">Once you have chosen your scenario, Model Builder asks you to provide a dataset.</span></span> <span data-ttu-id="d0a51-144">Les données sont utilisées pour entraîner, évaluer et choisir le meilleur modèle pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="d0a51-144">The data is used to train, evaluate, and choose the best model for your scenario.</span></span>

![Diagramme montrant les étapes de Model Builder](media/model-builder-steps.png)

<span data-ttu-id="d0a51-146">Modèle Builder prend en charge les ensembles de données dans les formats .tsv, .csv, .txt, ainsi que le format de base de données SQL.</span><span class="sxs-lookup"><span data-stu-id="d0a51-146">Model Builder supports datasets in .tsv, .csv, .txt formats, as well as SQL database format.</span></span> <span data-ttu-id="d0a51-147">Si vous avez un fichier .txt, `,` `;` les `/t` colonnes doivent être séparées avec, ou et le fichier doit avoir une rangée d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="d0a51-147">If you have a .txt file, columns should be separated with `,`, `;` or `/t` and the file must have a header row.</span></span>

<span data-ttu-id="d0a51-148">Si le jeu de données est composé d’images, les types de fichiers pris en charge sont `.jpg` et `.png`.</span><span class="sxs-lookup"><span data-stu-id="d0a51-148">If the dataset is made up of images, the supported file types are `.jpg` and `.png`.</span></span>

<span data-ttu-id="d0a51-149">Pour plus d’informations, voir [les données de formation de charge dans Model Builder](how-to-guides/load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="d0a51-149">For more information, see [Load training data into Model Builder](how-to-guides/load-data-model-builder.md).</span></span>

### <a name="choose-the-output-to-predict-label"></a><span data-ttu-id="d0a51-150">Choisir le résultat à prédire (étiquette)</span><span class="sxs-lookup"><span data-stu-id="d0a51-150">Choose the output to predict (label)</span></span>

<span data-ttu-id="d0a51-151">Un jeu de données est une table de lignes d’exemples et de colonnes d’attributs pour l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="d0a51-151">A dataset is a table of rows of training examples, and columns of attributes.</span></span> <span data-ttu-id="d0a51-152">Chaque ligne a :</span><span class="sxs-lookup"><span data-stu-id="d0a51-152">Each row has:</span></span>

- <span data-ttu-id="d0a51-153">une **étiquette** (l’attribut que vous voulez prédire)</span><span class="sxs-lookup"><span data-stu-id="d0a51-153">a **label** (the attribute that you want to predict)</span></span>
- <span data-ttu-id="d0a51-154">des **caractéristiques** (des attributs qui sont utilisés comme entrées pour prédire l’étiquette).</span><span class="sxs-lookup"><span data-stu-id="d0a51-154">**features** (attributes that are used as inputs to predict the label).</span></span>

<span data-ttu-id="d0a51-155">Pour le scénario de prédiction de prix d’une maison, les caractéristiques peuvent être :</span><span class="sxs-lookup"><span data-stu-id="d0a51-155">For the house-price prediction scenario, the features could be:</span></span>

- <span data-ttu-id="d0a51-156">la superficie de la maison</span><span class="sxs-lookup"><span data-stu-id="d0a51-156">the square footage of the house</span></span>
- <span data-ttu-id="d0a51-157">le nombre de chambres et de salles de bain</span><span class="sxs-lookup"><span data-stu-id="d0a51-157">the number of bedrooms and bathrooms</span></span>
- <span data-ttu-id="d0a51-158">le code postal</span><span class="sxs-lookup"><span data-stu-id="d0a51-158">the zip code</span></span>

<span data-ttu-id="d0a51-159">L’étiquette est l’historique des prix des maisons pour cette ligne de valeurs correspondant à la superficie, aux chambres et aux salles de bain, et au code postal.</span><span class="sxs-lookup"><span data-stu-id="d0a51-159">The label is the historical house price for that row of square footage, bedroom, and bathroom values and zip code.</span></span>

![Tableau montrant des lignes et des colonnes de données sur les prix de maisons avec des caractéristiques consistant en une taille, un nombre de pièces, un code postal et une étiquette de prix](media/model-builder-data.png)

### <a name="example-datasets"></a><span data-ttu-id="d0a51-161">Exemples de jeux de données</span><span class="sxs-lookup"><span data-stu-id="d0a51-161">Example datasets</span></span>

<span data-ttu-id="d0a51-162">Si vous n’avez pas encore vos propres données, essayez un de ces jeux de données :</span><span class="sxs-lookup"><span data-stu-id="d0a51-162">If you don't have your own data yet, try out one of these datasets:</span></span>

|<span data-ttu-id="d0a51-163">Scénario</span><span class="sxs-lookup"><span data-stu-id="d0a51-163">Scenario</span></span>|<span data-ttu-id="d0a51-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0a51-164">Example</span></span>|<span data-ttu-id="d0a51-165">Données</span><span class="sxs-lookup"><span data-stu-id="d0a51-165">Data</span></span>|<span data-ttu-id="d0a51-166">Étiquette</span><span class="sxs-lookup"><span data-stu-id="d0a51-166">Label</span></span>|<span data-ttu-id="d0a51-167">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d0a51-167">Features</span></span>|
|-|-|-|-|-|
|<span data-ttu-id="d0a51-168">classification ;</span><span class="sxs-lookup"><span data-stu-id="d0a51-168">Classification</span></span>|<span data-ttu-id="d0a51-169">Prédire les anomalies de vente</span><span class="sxs-lookup"><span data-stu-id="d0a51-169">Predict sales anomalies</span></span>|[<span data-ttu-id="d0a51-170">Données de ventes de produits</span><span class="sxs-lookup"><span data-stu-id="d0a51-170">product sales data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)|<span data-ttu-id="d0a51-171">Ventes de produits</span><span class="sxs-lookup"><span data-stu-id="d0a51-171">Product Sales</span></span>|<span data-ttu-id="d0a51-172">Month</span><span class="sxs-lookup"><span data-stu-id="d0a51-172">Month</span></span>|
||<span data-ttu-id="d0a51-173">Prédire le sentiment des commentaires sur les sites Web</span><span class="sxs-lookup"><span data-stu-id="d0a51-173">Predict sentiment of website comments</span></span>|[<span data-ttu-id="d0a51-174">Données de commentaires de site web</span><span class="sxs-lookup"><span data-stu-id="d0a51-174">website comment data</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)|<span data-ttu-id="d0a51-175">Étiquette (0 quand le sentiment est négatif, 1 quand il est positif)</span><span class="sxs-lookup"><span data-stu-id="d0a51-175">Label (0 when negative sentiment, 1 when positive)</span></span>|<span data-ttu-id="d0a51-176">Commentaire, Année</span><span class="sxs-lookup"><span data-stu-id="d0a51-176">Comment, Year</span></span>|
||<span data-ttu-id="d0a51-177">Prédire les transactions frauduleuses par carte de crédit</span><span class="sxs-lookup"><span data-stu-id="d0a51-177">Predict fraudulent credit card transactions</span></span>|[<span data-ttu-id="d0a51-178">Données de carte de crédit</span><span class="sxs-lookup"><span data-stu-id="d0a51-178">credit card data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/BinaryClassification_CreditCardFraudDetection/CreditCardFraudDetection.Trainer/assets/input/creditcardfraud-dataset.zip)|<span data-ttu-id="d0a51-179">Classe (1 en cas de fraude, sinon 0)</span><span class="sxs-lookup"><span data-stu-id="d0a51-179">Class (1 when fraudulent, 0 otherwise)</span></span>|<span data-ttu-id="d0a51-180">Quantité, V1-V28 (caractéristiques anonymisées)</span><span class="sxs-lookup"><span data-stu-id="d0a51-180">Amount, V1-V28 (anonymized features)</span></span>|
||<span data-ttu-id="d0a51-181">Prédire le type de problème dans un référentiel GitHub</span><span class="sxs-lookup"><span data-stu-id="d0a51-181">Predict the type of issue in a GitHub repository</span></span>|[<span data-ttu-id="d0a51-182">Données de problèmes GitHub</span><span class="sxs-lookup"><span data-stu-id="d0a51-182">GitHub issue data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/end-to-end-apps/MulticlassClassification-GitHubLabeler/GitHubLabeler/Data/corefx-issues-train.tsv)|<span data-ttu-id="d0a51-183">Domaine</span><span class="sxs-lookup"><span data-stu-id="d0a51-183">Area</span></span>|<span data-ttu-id="d0a51-184">Titre, Description</span><span class="sxs-lookup"><span data-stu-id="d0a51-184">Title, Description</span></span>|
|<span data-ttu-id="d0a51-185">Prévision de la valeur</span><span class="sxs-lookup"><span data-stu-id="d0a51-185">Value prediction</span></span>|<span data-ttu-id="d0a51-186">Prédire le prix du billet de taxi</span><span class="sxs-lookup"><span data-stu-id="d0a51-186">Predict taxi fare price</span></span>|[<span data-ttu-id="d0a51-187">Données de courses de taxi</span><span class="sxs-lookup"><span data-stu-id="d0a51-187">taxi fare data</span></span>](https://github.com/dotnet/machinelearning-samples/blob/master/datasets/taxi-fare-train.csv)|<span data-ttu-id="d0a51-188">Fare</span><span class="sxs-lookup"><span data-stu-id="d0a51-188">Fare</span></span>|<span data-ttu-id="d0a51-189">Heure, distance du trajet</span><span class="sxs-lookup"><span data-stu-id="d0a51-189">Trip time, distance</span></span>|
|<span data-ttu-id="d0a51-190">Classification d’image</span><span class="sxs-lookup"><span data-stu-id="d0a51-190">Image classification</span></span>|<span data-ttu-id="d0a51-191">Prédire la catégorie d’un problème</span><span class="sxs-lookup"><span data-stu-id="d0a51-191">Predict the category of an issue</span></span>|[<span data-ttu-id="d0a51-192">images de fleurs</span><span class="sxs-lookup"><span data-stu-id="d0a51-192">flower images</span></span>](http://download.tensorflow.org/example_images/flower_photos.tgz)|<span data-ttu-id="d0a51-193">Le type de fleur: marguerite, pissenlit, roses, tournesols, tulipes</span><span class="sxs-lookup"><span data-stu-id="d0a51-193">The type of flower: daisy, dandelion, roses, sunflowers, tulips</span></span>|<span data-ttu-id="d0a51-194">Les données d’image elles-mêmes</span><span class="sxs-lookup"><span data-stu-id="d0a51-194">The image data itself</span></span>|
|<span data-ttu-id="d0a51-195">Recommandation</span><span class="sxs-lookup"><span data-stu-id="d0a51-195">Recommendation</span></span>|<span data-ttu-id="d0a51-196">Prédire les films que quelqu’un aimera</span><span class="sxs-lookup"><span data-stu-id="d0a51-196">Predict movies that someone will like</span></span>|[<span data-ttu-id="d0a51-197">notes de film</span><span class="sxs-lookup"><span data-stu-id="d0a51-197">movie ratings</span></span>](http://files.grouplens.org/datasets/movielens/ml-latest-small.zip)|<span data-ttu-id="d0a51-198">Utilisateurs, Films</span><span class="sxs-lookup"><span data-stu-id="d0a51-198">Users, Movies</span></span>|<span data-ttu-id="d0a51-199">Évaluations</span><span class="sxs-lookup"><span data-stu-id="d0a51-199">Ratings</span></span>|

## <a name="train"></a><span data-ttu-id="d0a51-200">Former</span><span class="sxs-lookup"><span data-stu-id="d0a51-200">Train</span></span>

<span data-ttu-id="d0a51-201">Une fois que vous avez sélectionné votre scénario, vos données et votre étiquette, Model Builder entraîne le modèle.</span><span class="sxs-lookup"><span data-stu-id="d0a51-201">Once you select your scenario, data, and label, Model Builder trains the model.</span></span>

### <a name="what-is-training"></a><span data-ttu-id="d0a51-202">Qu’est-ce que l’entraînement ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-202">What is training?</span></span>

<span data-ttu-id="d0a51-203">L’entraînement est un processus automatique par lequel Model Builder apprend à votre modèle comment répondre aux questions de votre scénario.</span><span class="sxs-lookup"><span data-stu-id="d0a51-203">Training is an automatic process by which Model Builder teaches your model how to answer questions for your scenario.</span></span> <span data-ttu-id="d0a51-204">Une fois entraîné, votre modèle peut faire des prédictions avec des données en entrée qu’il n’avait pas vues avant.</span><span class="sxs-lookup"><span data-stu-id="d0a51-204">Once trained, your model can make predictions with input data that it has not seen before.</span></span> <span data-ttu-id="d0a51-205">Par exemple, si vous prédisez des prix de maisons et qu’une nouvelle maison apparaît sur le marché, vous pouvez prévoir son prix de vente.</span><span class="sxs-lookup"><span data-stu-id="d0a51-205">For example, if you are predicting house prices and a new house comes on the market, you can predict its sale price.</span></span>

<span data-ttu-id="d0a51-206">Comme Model Builder utilise le Machine Learning automatisé (AutoML), il ne nécessite aucune entrée ou optimisation de votre part pendant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="d0a51-206">Because Model Builder uses automated machine learning (AutoML), it does not require any input or tuning from you during training.</span></span>

### <a name="how-long-should-i-train-for"></a><span data-ttu-id="d0a51-207">Combien de temps doit durer l’entraînement ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-207">How long should I train for?</span></span>

<span data-ttu-id="d0a51-208">Model Builder utilise AutoML pour explorer plusieurs modèles pour vous trouver le modèle le plus performant.</span><span class="sxs-lookup"><span data-stu-id="d0a51-208">Model Builder uses AutoML to explore multiple models to find you the best performing model.</span></span>

<span data-ttu-id="d0a51-209">Des périodes de formation plus longues permettent à AutoML d’explorer plus de modèles avec un plus large éventail de réglages.</span><span class="sxs-lookup"><span data-stu-id="d0a51-209">Longer training periods allow AutoML to explore more models with a wider range of settings.</span></span>

<span data-ttu-id="d0a51-210">Le tableau ci-dessous résume le temps moyen pris pour obtenir de bonnes performances pour une suite d’exemples de jeux de données, sur une machine locale.</span><span class="sxs-lookup"><span data-stu-id="d0a51-210">The table below summarizes the average time taken to get good performance for a suite of example datasets, on a local machine.</span></span>

|<span data-ttu-id="d0a51-211">Taille de dataset</span><span class="sxs-lookup"><span data-stu-id="d0a51-211">Dataset size</span></span>|<span data-ttu-id="d0a51-212">Temps moyen de formation</span><span class="sxs-lookup"><span data-stu-id="d0a51-212">Average time to train</span></span>|
|------------|---------------------|
|<span data-ttu-id="d0a51-213">0 - 10 Mo</span><span class="sxs-lookup"><span data-stu-id="d0a51-213">0 - 10 MB</span></span>|<span data-ttu-id="d0a51-214">10 s</span><span class="sxs-lookup"><span data-stu-id="d0a51-214">10 sec</span></span>|
|<span data-ttu-id="d0a51-215">10 - 100 Mo</span><span class="sxs-lookup"><span data-stu-id="d0a51-215">10 - 100 MB</span></span>|<span data-ttu-id="d0a51-216">10 min</span><span class="sxs-lookup"><span data-stu-id="d0a51-216">10 min</span></span>|
|<span data-ttu-id="d0a51-217">100 - 500 Mo</span><span class="sxs-lookup"><span data-stu-id="d0a51-217">100 - 500 MB</span></span>|<span data-ttu-id="d0a51-218">30 min</span><span class="sxs-lookup"><span data-stu-id="d0a51-218">30 min</span></span>|
|<span data-ttu-id="d0a51-219">500 - 1 Go</span><span class="sxs-lookup"><span data-stu-id="d0a51-219">500 - 1 GB</span></span>|<span data-ttu-id="d0a51-220">60 min</span><span class="sxs-lookup"><span data-stu-id="d0a51-220">60 min</span></span>|
|<span data-ttu-id="d0a51-221">1 Go</span><span class="sxs-lookup"><span data-stu-id="d0a51-221">1 GB+</span></span>|<span data-ttu-id="d0a51-222">Plus de 3 heures</span><span class="sxs-lookup"><span data-stu-id="d0a51-222">3+ hours</span></span>|

<span data-ttu-id="d0a51-223">Ces chiffres sont un guide seulement.</span><span class="sxs-lookup"><span data-stu-id="d0a51-223">These numbers are a guide only.</span></span> <span data-ttu-id="d0a51-224">La durée exacte de la formation dépend des faits :</span><span class="sxs-lookup"><span data-stu-id="d0a51-224">The exact length of training is dependent on:</span></span>

- <span data-ttu-id="d0a51-225">le nombre de fonctionnalités (colonnes) utilisées comme entrée au modèle</span><span class="sxs-lookup"><span data-stu-id="d0a51-225">the number of features (columns) being used to as input to the model</span></span>
- <span data-ttu-id="d0a51-226">le type de colonnes</span><span class="sxs-lookup"><span data-stu-id="d0a51-226">the type of columns</span></span>
- <span data-ttu-id="d0a51-227">la tâche ML</span><span class="sxs-lookup"><span data-stu-id="d0a51-227">the ML task</span></span>
- <span data-ttu-id="d0a51-228">le processeur, le disque et les performances de mémoire de la machine utilisée pour la formation</span><span class="sxs-lookup"><span data-stu-id="d0a51-228">the CPU, disk, and memory performance of the machine used for training</span></span>

## <a name="evaluate"></a><span data-ttu-id="d0a51-229">Évaluer</span><span class="sxs-lookup"><span data-stu-id="d0a51-229">Evaluate</span></span>

<span data-ttu-id="d0a51-230">L’évaluation est le processus de mesure de la qualité de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="d0a51-230">Evaluation is the process of measuring how good your model is.</span></span> <span data-ttu-id="d0a51-231">Modèle Builder utilise le modèle formé pour faire des prédictions avec de nouvelles données de test, puis mesure la qualité des prédictions sont.</span><span class="sxs-lookup"><span data-stu-id="d0a51-231">Model Builder uses the trained model to make predictions with new test data, and then measures how good the predictions are.</span></span>

<span data-ttu-id="d0a51-232">Model Builder divise les données d’entraînement en un jeu d’entraînement et un jeu de test.</span><span class="sxs-lookup"><span data-stu-id="d0a51-232">Model Builder splits the training data into a training set and a test set.</span></span> <span data-ttu-id="d0a51-233">Les données d’entraînement (80 %) sont utilisées pour entraîner votre modèle et les données de test (20 %) sont conservées à part pour évaluer votre modèle.</span><span class="sxs-lookup"><span data-stu-id="d0a51-233">The training data (80%) is used to train your model and the test data (20%) is held back to evaluate your model.</span></span>

### <a name="how-do-i-understand-my-model-performance"></a><span data-ttu-id="d0a51-234">Comment puis-je comprendre la performance de mon modèle ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-234">How do I understand my model performance?</span></span>

<span data-ttu-id="d0a51-235">Un scénario est adapté à une tâche d’apprentissage automatique.</span><span class="sxs-lookup"><span data-stu-id="d0a51-235">A scenario maps to a machine learning task.</span></span> <span data-ttu-id="d0a51-236">Chaque tâche ML a son propre ensemble de mesures d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="d0a51-236">Each ML task has its own set of evaluation metrics.</span></span>

#### <a name="value-prediction"></a><span data-ttu-id="d0a51-237">Prévision de la valeur</span><span class="sxs-lookup"><span data-stu-id="d0a51-237">Value prediction</span></span>

<span data-ttu-id="d0a51-238">La mesure par défaut pour les problèmes de prédiction de valeur est RSquared, la valeur des gammes RSquared entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="d0a51-238">The default metric for value prediction problems is RSquared, the value of RSquared ranges between 0 and 1.</span></span> <span data-ttu-id="d0a51-239">1 est la meilleure valeur possible ou en d’autres termes plus la valeur de RSquared à 1 mieux votre modèle est performant.</span><span class="sxs-lookup"><span data-stu-id="d0a51-239">1 is the best possible value or in other words the closer the value of RSquared to 1 the better your model is performing.</span></span>

<span data-ttu-id="d0a51-240">D’autres mesures signalées telles que la perte absolue, la perte au carré et la perte de RMS sont des mesures supplémentaires, qui peuvent être utilisées pour comprendre comment votre modèle fonctionne et le compare à d’autres modèles de prédiction de valeur.</span><span class="sxs-lookup"><span data-stu-id="d0a51-240">Other metrics reported such as absolute-loss, squared-loss, and RMS loss are additional metrics, which can be used to understand how your model is performing and comparing it against other value prediction models.</span></span>

#### <a name="classification-2-categories"></a><span data-ttu-id="d0a51-241">Classification (2 catégories)</span><span class="sxs-lookup"><span data-stu-id="d0a51-241">Classification (2 categories)</span></span>

<span data-ttu-id="d0a51-242">La mesure par défaut pour les problèmes de classification est l’exactitude.</span><span class="sxs-lookup"><span data-stu-id="d0a51-242">The default metric for classification problems is accuracy.</span></span> <span data-ttu-id="d0a51-243">L’exactitude définit la proportion de prédictions correctes que votre modèle fait sur le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="d0a51-243">Accuracy defines the proportion of correct predictions your model is making over the test dataset.</span></span> <span data-ttu-id="d0a51-244">Plus il est proche de 100% ou 1,0, mieux c’est.</span><span class="sxs-lookup"><span data-stu-id="d0a51-244">The closer to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="d0a51-245">D’autres mesures signalées comme l’AUC (zone sous la courbe), qui mesure le taux positif réel par rapport au taux de faux positifs devraient être supérieurs à 0,50 pour que les modèles soient acceptables.</span><span class="sxs-lookup"><span data-stu-id="d0a51-245">Other metrics reported such as AUC (Area under the curve), which measures the true positive rate vs. the false positive rate should be greater than 0.50 for models to be acceptable.</span></span>

<span data-ttu-id="d0a51-246">Des mesures supplémentaires comme le score F1 peuvent être utilisées pour contrôler l’équilibre entre précision et rappel.</span><span class="sxs-lookup"><span data-stu-id="d0a51-246">Additional metrics like F1 score can be used to control the balance between Precision and Recall.</span></span>

#### <a name="classification-3-categories"></a><span data-ttu-id="d0a51-247">Classification (3 catégories et plus)</span><span class="sxs-lookup"><span data-stu-id="d0a51-247">Classification (3+ categories)</span></span>

<span data-ttu-id="d0a51-248">La mesure par défaut pour la classification multi-classes est Micro Accuracy.</span><span class="sxs-lookup"><span data-stu-id="d0a51-248">The default metric for Multi-class classification is Micro Accuracy.</span></span> <span data-ttu-id="d0a51-249">Plus la Micro Accuracy est proche à 100% ou 1,0, mieux c’est.</span><span class="sxs-lookup"><span data-stu-id="d0a51-249">The closer the Micro Accuracy to 100% or 1.0 the better it is.</span></span>

<span data-ttu-id="d0a51-250">Une autre mesure importante pour la classification multi-classe est macro-précision, semblable à Micro-précision le plus proche de 1.0 le mieux il est.</span><span class="sxs-lookup"><span data-stu-id="d0a51-250">Another important metric for Multi-class classification is Macro-accuracy, similar to Micro-accuracy the closer to 1.0 the better it is.</span></span> <span data-ttu-id="d0a51-251">Une bonne façon de penser à ces deux types de précision est:</span><span class="sxs-lookup"><span data-stu-id="d0a51-251">A good way to think about these two types of accuracy is:</span></span>

- <span data-ttu-id="d0a51-252">Micro-précision : À quelle fréquence un billet entrant est-il classé à la bonne équipe ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-252">Micro-accuracy: How often does an incoming ticket get classified to the right team?</span></span>
- <span data-ttu-id="d0a51-253">Macro-précision : Pour une équipe moyenne, à quelle fréquence un billet entrant est-il correct pour son équipe ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-253">Macro-accuracy: For an average team, how often is an incoming ticket correct for their team?</span></span>

### <a name="more-information-on-evaluation-metrics"></a><span data-ttu-id="d0a51-254">Plus d’informations sur les mesures d’évaluation</span><span class="sxs-lookup"><span data-stu-id="d0a51-254">More information on evaluation metrics</span></span>

<span data-ttu-id="d0a51-255">Pour plus d’informations, consultez [Métriques d’évaluation des modèles](resources/metrics.md).</span><span class="sxs-lookup"><span data-stu-id="d0a51-255">For more information, see [model evaluation metrics](resources/metrics.md).</span></span>

## <a name="improve"></a><span data-ttu-id="d0a51-256">Améliorer</span><span class="sxs-lookup"><span data-stu-id="d0a51-256">Improve</span></span>

<span data-ttu-id="d0a51-257">Si le score de performances de votre modèle n’est pas aussi bon que souhaité, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="d0a51-257">If your model performance score is not as good as you want it to be, you can:</span></span>

- <span data-ttu-id="d0a51-258">Entraîner sur une période de temps plus longue.</span><span class="sxs-lookup"><span data-stu-id="d0a51-258">Train for a longer period of time.</span></span> <span data-ttu-id="d0a51-259">Avec plus de temps, le moteur d’apprentissage automatique automatisé expérimente avec plus d’algorithmes et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="d0a51-259">With more time, the automated machine learning engine experiments with more algorithms and settings.</span></span>

- <span data-ttu-id="d0a51-260">Ajouter des données.</span><span class="sxs-lookup"><span data-stu-id="d0a51-260">Add more data.</span></span> <span data-ttu-id="d0a51-261">Parfois, la quantité de données n’est pas suffisante pour entraîner un modèle Machine Learning de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="d0a51-261">Sometimes the amount of data is not sufficient to train a high-quality machine learning model.</span></span>

- <span data-ttu-id="d0a51-262">Équilibrer vos données.</span><span class="sxs-lookup"><span data-stu-id="d0a51-262">Balance your data.</span></span> <span data-ttu-id="d0a51-263">Pour les tâches de classification, vérifiez que le jeu d’entraînement est équilibré entre les différentes catégories.</span><span class="sxs-lookup"><span data-stu-id="d0a51-263">For classification tasks, make sure that the training set is balanced across the categories.</span></span> <span data-ttu-id="d0a51-264">Par exemple, si vous avez quatre classes pour 100 exemples d’entraînement et que les deux premières classes (étiquette1 et étiquette2) sont utilisées pour 90 enregistrements, mais que les deux autres (étiquette3 et étiquette4) sont utilisées seulement sur les 10 enregistrements restants, l’absence de données équilibrées peut faire que votre modèle aura du mal à prédire correctement étiquette3 ou étiquette4.</span><span class="sxs-lookup"><span data-stu-id="d0a51-264">For example, if you have four classes for 100 training examples, and the two first classes (tag1 and tag2) are used for 90 records, but the other two (tag3 and tag4) are only used on the remaining 10 records, the lack of balanced data may cause your model to struggle to correctly predict tag3 or tag4.</span></span>

## <a name="code"></a><span data-ttu-id="d0a51-265">Code</span><span class="sxs-lookup"><span data-stu-id="d0a51-265">Code</span></span>

<span data-ttu-id="d0a51-266">Après la phase d’évaluation, Model Builder génère un fichier de modèle et du code que vous pouvez utiliser pour ajouter le modèle à votre application.</span><span class="sxs-lookup"><span data-stu-id="d0a51-266">After the evaluation phase, Model Builder outputs a model file, and code that you can use to add the model to your application.</span></span> <span data-ttu-id="d0a51-267">Les modèles ML.NET sont enregistrés sous la forme d’un fichier zip.</span><span class="sxs-lookup"><span data-stu-id="d0a51-267">ML.NET models are saved as a zip file.</span></span> <span data-ttu-id="d0a51-268">Le code pour charger et utiliser votre modèle est ajouté en tant que nouveau projet dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="d0a51-268">The code to load and use your model is added as a new project in your solution.</span></span> <span data-ttu-id="d0a51-269">Model Builder ajoute également un exemple d’application console que vous pouvez exécuter pour voir votre modèle en action.</span><span class="sxs-lookup"><span data-stu-id="d0a51-269">Model Builder also adds a sample console app that you can run to see your model in action.</span></span>

<span data-ttu-id="d0a51-270">En outre, Model Builder produit le code qui a généré le modèle, ce qui vous permet de comprendre les étapes utilisées pour cette génération.</span><span class="sxs-lookup"><span data-stu-id="d0a51-270">In addition, Model Builder outputs the code that generated the model, so that you can understand the steps used to generate the model.</span></span> <span data-ttu-id="d0a51-271">Vous pouvez également utiliser le code de l’entraînement du modèle pour réentraîner votre modèle avec de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="d0a51-271">You can also use the model training code to retrain your model with new data.</span></span>

## <a name="whats-next"></a><span data-ttu-id="d0a51-272">Quelle est l’étape suivante ?</span><span class="sxs-lookup"><span data-stu-id="d0a51-272">What's next?</span></span>

<span data-ttu-id="d0a51-273">[Installer](how-to-guides/install-model-builder.md) l’extension Visual Studio Model Builder</span><span class="sxs-lookup"><span data-stu-id="d0a51-273">[Install](how-to-guides/install-model-builder.md) the Model Builder Visual Studio extension</span></span>

<span data-ttu-id="d0a51-274">Essayer [le scénario de prédiction des prix ou un autre scénario de régression](tutorials/predict-prices-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="d0a51-274">Try [price prediction or any regression scenario](tutorials/predict-prices-with-model-builder.md)</span></span>
