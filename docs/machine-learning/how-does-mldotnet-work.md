---
title: Présentation de ML.NET et de son fonctionnement
description: ML.NET vous donne la possibilité d’ajouter le Machine Learning aux applications .NET, dans des scénarios en ligne ou hors connexion. Avec cette fonctionnalité, vous pouvez ensuite effectuer des prédictions automatiques à partir des données disponibles dans votre application sans devoir être connecté à un réseau pour utiliser ML.NET. Cet article explique les principes de base du machine learning dans ML.NET.
ms.date: 09/27/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 1ae6b82ada841ad172cbe6a59b667aaaf619e714
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592047"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="87c2b-105">Présentation de ML.NET et de son fonctionnement</span><span class="sxs-lookup"><span data-stu-id="87c2b-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="87c2b-106">ML.NET vous donne la possibilité d’ajouter le Machine Learning aux applications .NET, dans des scénarios en ligne ou hors connexion.</span><span class="sxs-lookup"><span data-stu-id="87c2b-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="87c2b-107">Avec cette fonctionnalité, vous pouvez ensuite effectuer des prédictions automatiques à partir des données disponibles dans votre application sans devoir être connecté à un réseau.</span><span class="sxs-lookup"><span data-stu-id="87c2b-107">With this capability, you can make automatic predictions using the data available to your application without having to be connected to a network.</span></span> <span data-ttu-id="87c2b-108">Cet article explique les principes de base du machine learning dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="87c2b-108">This article explains the basics of machine learning in ML.NET.</span></span>

<span data-ttu-id="87c2b-109">ML.NET s’exécute sur Windows, Linux et macOS à l’aide de .NET Core ou de Windows à l’aide de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="87c2b-109">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="87c2b-110">64 bits est pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="87c2b-110">64 bit is supported on all platforms.</span></span> <span data-ttu-id="87c2b-111">32 bits est pris en charge sur Windows, à l’exception des fonctionnalités liées à TensorFlow, LightGBM et ONNX.</span><span class="sxs-lookup"><span data-stu-id="87c2b-111">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX related functionality.</span></span>

<span data-ttu-id="87c2b-112">Voici des exemples de types de prédictions possibles avec ML.NET :</span><span class="sxs-lookup"><span data-stu-id="87c2b-112">Examples of the type of predictions that you can make with ML.NET include:</span></span>

|||
|-|-|
|<span data-ttu-id="87c2b-113">Classification/Catégorisation</span><span class="sxs-lookup"><span data-stu-id="87c2b-113">Classification/Categorization</span></span>|<span data-ttu-id="87c2b-114">Classer automatiquement les commentaires des clients dans les catégories Positif et Négatif</span><span class="sxs-lookup"><span data-stu-id="87c2b-114">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="87c2b-115">Régression/Prédire les valeurs continues</span><span class="sxs-lookup"><span data-stu-id="87c2b-115">Regression/Predict continuous values</span></span>|<span data-ttu-id="87c2b-116">Prédire les prix des maisons en fonction de la superficie et de l’emplacement</span><span class="sxs-lookup"><span data-stu-id="87c2b-116">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="87c2b-117">Détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="87c2b-117">Anomaly Detection</span></span>|<span data-ttu-id="87c2b-118">Détecter les transactions bancaires frauduleuses</span><span class="sxs-lookup"><span data-stu-id="87c2b-118">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="87c2b-119">Recommandations</span><span class="sxs-lookup"><span data-stu-id="87c2b-119">Recommendations</span></span>|<span data-ttu-id="87c2b-120">Suggérer d’autres produits aux acheteurs en ligne en fonction de leurs achats précédents</span><span class="sxs-lookup"><span data-stu-id="87c2b-120">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="87c2b-121">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="87c2b-121">Hello ML.NET World</span></span>

<span data-ttu-id="87c2b-122">Le code dans l’extrait suivant illustre l’application ML.NET la plus simple.</span><span class="sxs-lookup"><span data-stu-id="87c2b-122">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="87c2b-123">Cet exemple crée un modèle de régression linéaire pour prédire les prix de maisons à partir des données de superficie et des prix immobiliers.</span><span class="sxs-lookup"><span data-stu-id="87c2b-123">This example constructs a linear regression model to predict house prices using house size and price data.</span></span> <span data-ttu-id="87c2b-124">Dans vos applications réelles, vos données et votre modèle seront beaucoup plus complexes.</span><span class="sxs-lookup"><span data-stu-id="87c2b-124">In your real-life applications, your data and model will be much more complex.</span></span>

 ```csharp
    using System;
    using Microsoft.ML;
    using Microsoft.ML.Data;
    
    class Program
    {
        public class HouseData
        {
            public float Size { get; set; }
            public float Price { get; set; }
        }
    
        public class Prediction
        {
            [ColumnName("Score")]
            public float Price { get; set; }
        }
    
        static void Main(string[] args)
        {
            MLContext mlContext = new MLContext();
    
            // 1. Import or create training data
            HouseData[] houseData = {
                new HouseData() { Size = 1.1F, Price = 1.2F },
                new HouseData() { Size = 1.9F, Price = 2.3F },
                new HouseData() { Size = 2.8F, Price = 3.0F },
                new HouseData() { Size = 3.4F, Price = 3.7F } };
            IDataView trainingData = mlContext.Data.LoadFromEnumerable(houseData);

            // 2. Specify data preparation and model training pipeline
            var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
                .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
    
            // 3. Train model
            var model = pipeline.Fit(trainingData);
    
            // 4. Make a prediction
            var size = new HouseData() { Size = 2.5F };
            var price = mlContext.Model.CreatePredictionEngine<HouseData, Prediction>(model).Predict(size);

            Console.WriteLine($"Predicted price for size: {size.Size*1000} sq ft= {price.Price*100:C}k");

            // Predicted price for size: 2500 sq ft= $261.98k
        }
    } 
```

## <a name="code-workflow"></a><span data-ttu-id="87c2b-125">Workflow du code</span><span class="sxs-lookup"><span data-stu-id="87c2b-125">Code workflow</span></span>

<span data-ttu-id="87c2b-126">Le diagramme suivant représente la structure du code de l’application ainsi que le processus itératif de développement du modèle :</span><span class="sxs-lookup"><span data-stu-id="87c2b-126">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="87c2b-127">Collecter et charger des données d’entraînement dans un objet **IDataView**</span><span class="sxs-lookup"><span data-stu-id="87c2b-127">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="87c2b-128">Spécifier un pipeline d’opérations pour extraire des caractéristiques et appliquer un algorithme de machine learning</span><span class="sxs-lookup"><span data-stu-id="87c2b-128">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="87c2b-129">Entraîner un modèle en appelant **Fit()** sur le pipeline</span><span class="sxs-lookup"><span data-stu-id="87c2b-129">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="87c2b-130">Évaluer le modèle et effectuer des itérations pour l’améliorer</span><span class="sxs-lookup"><span data-stu-id="87c2b-130">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="87c2b-131">Enregistrer le modèle au format binaire pour l’utiliser dans une application</span><span class="sxs-lookup"><span data-stu-id="87c2b-131">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="87c2b-132">Recharger le modèle dans un objet **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="87c2b-132">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="87c2b-133">Effectuer des prédictions en appelant **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="87c2b-133">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Workflow du développement d’application ML.NET, avec les composants pour la génération des données, le développement du pipeline, l’entraînement du modèle, l’évaluation du modèle et l’utilisation du modèle](./media/mldotnet-annotated-workflow.png) 

<span data-ttu-id="87c2b-135">Revoyons maintenant tous ces concepts un peu plus en détail.</span><span class="sxs-lookup"><span data-stu-id="87c2b-135">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="87c2b-136">Modèle Machine Learning</span><span class="sxs-lookup"><span data-stu-id="87c2b-136">Machine learning model</span></span>

<span data-ttu-id="87c2b-137">Un modèle ML.NET est un objet qui contient des transformations à effectuer sur vos données d’entrée pour produire la sortie prédite.</span><span class="sxs-lookup"><span data-stu-id="87c2b-137">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="87c2b-138">Basic</span><span class="sxs-lookup"><span data-stu-id="87c2b-138">Basic</span></span>

<span data-ttu-id="87c2b-139">Le modèle de base, le plus simple, est la régression linéaire à deux dimensions, où une quantité continue est proportionnelle à une autre, comme dans l’exemple des prix de maisons ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="87c2b-139">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span> 

![Modèle de régression linéaire avec des paramètres de biais et de poids](./media/linear-regression-model.svg)

<span data-ttu-id="87c2b-141">Le modèle est simple : $Price = b + Size \* w$.</span><span class="sxs-lookup"><span data-stu-id="87c2b-141">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="87c2b-142">Les paramètres $b$ et $w$ sont estimés en ajustant une ligne sur un ensemble de paires de valeurs (size, price).</span><span class="sxs-lookup"><span data-stu-id="87c2b-142">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="87c2b-143">Les données utilisées pour rechercher les paramètres du modèle sont appelées **données d’entraînement**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-143">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="87c2b-144">Les entrées d’un modèle Machine Learning sont des **caractéristiques**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-144">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="87c2b-145">Dans cet exemple, $Size$ est la seule caractéristique.</span><span class="sxs-lookup"><span data-stu-id="87c2b-145">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="87c2b-146">Les valeurs certifiées vraies utilisées pour entraîner un modèle Machine Learning sont appelées des **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-146">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="87c2b-147">Ici, les étiquettes sont les valeurs $Price$ contenues dans le jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="87c2b-147">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="87c2b-148">Plus complexe</span><span class="sxs-lookup"><span data-stu-id="87c2b-148">More complex</span></span>

<span data-ttu-id="87c2b-149">Un modèle plus complexe classe les transactions financières dans différentes catégories en fonction du texte de description de la transaction.</span><span class="sxs-lookup"><span data-stu-id="87c2b-149">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="87c2b-150">Chaque description de transaction est décomposée en un ensemble de caractéristiques, après suppression des mots et caractères redondants, et comptage des combinaisons de mots et caractères.</span><span class="sxs-lookup"><span data-stu-id="87c2b-150">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="87c2b-151">L’ensemble des caractéristiques est ensuite utilisé pour entraîner un modèle linéaire basé sur l’ensemble des catégories trouvées dans les données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="87c2b-151">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="87c2b-152">Plus une nouvelle description se rapproche d’une des descriptions figurant dans le jeu de données d’entraînement, plus elle a de chance d’être attribuée à la même catégorie.</span><span class="sxs-lookup"><span data-stu-id="87c2b-152">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span> 

![Modèle de classification de texte](./media/text-classification-model.svg)

<span data-ttu-id="87c2b-154">Le modèle de prix des maisons et le modèle de classification de texte sont tous les deux des modèles de type **linéaire**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-154">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="87c2b-155">Selon la nature de vos données et le problème à résoudre, vous pouvez également utiliser des modèles d’**arbre de décision**, des modèles **additifs généralisés** et d’autres modèles.</span><span class="sxs-lookup"><span data-stu-id="87c2b-155">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="87c2b-156">Pour plus d’informations sur les modèles, consultez [Tâches](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="87c2b-156">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="87c2b-157">Préparation des données</span><span class="sxs-lookup"><span data-stu-id="87c2b-157">Data preparation</span></span>

<span data-ttu-id="87c2b-158">Dans la plupart des cas, les données dont vous disposez ne peuvent pas être utilisées directement pour entraîner un modèle Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="87c2b-158">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="87c2b-159">Les données brutes doivent être préparées ou prétraitées afin de pouvoir ensuite être utilisées pour rechercher les paramètres de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="87c2b-159">The raw data needs to be prepared, or pre-processed before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="87c2b-160">Par exemple, vous devrez peut-être convertir vos données de valeurs de chaîne en une représentation numérique,</span><span class="sxs-lookup"><span data-stu-id="87c2b-160">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="87c2b-161">supprimer des informations redondantes dans vos données d’entrée,</span><span class="sxs-lookup"><span data-stu-id="87c2b-161">You might have redundant information in your input data.</span></span> <span data-ttu-id="87c2b-162">réduire ou développer les dimensions de vos données d’entrée,</span><span class="sxs-lookup"><span data-stu-id="87c2b-162">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="87c2b-163">ou encore normaliser ou redimensionner vos données.</span><span class="sxs-lookup"><span data-stu-id="87c2b-163">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="87c2b-164">Les [tutoriels ML.NET](./tutorials/index.md) vous montrent différents pipelines de traitement des données (pour les données texte, d’image, numériques et de série chronologique) qui sont utilisés dans le cadre de tâches de machine learning spécifiques.</span><span class="sxs-lookup"><span data-stu-id="87c2b-164">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="87c2b-165">La rubrique [Préparer vos données](./how-to-guides/prepare-data-ml-net.md) explique comment préparer des données de manière plus générale.</span><span class="sxs-lookup"><span data-stu-id="87c2b-165">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to applied data preparation more generally.</span></span>

<span data-ttu-id="87c2b-166">Vous trouverez toutes les [transformations disponibles](./resources/transforms.md) en annexe, dans la section des ressources.</span><span class="sxs-lookup"><span data-stu-id="87c2b-166">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="87c2b-167">Évaluation du modèle</span><span class="sxs-lookup"><span data-stu-id="87c2b-167">Model evaluation</span></span>

<span data-ttu-id="87c2b-168">Une fois que vous avez entraîné votre modèle, comment savoir si ses prédictions futures seront correctes ?</span><span class="sxs-lookup"><span data-stu-id="87c2b-168">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="87c2b-169">Avec ML.NET, vous pouvez évaluer votre modèle par rapport à de nouvelles données de test.</span><span class="sxs-lookup"><span data-stu-id="87c2b-169">With ML.NET, you can evaluate your model against some new test data.</span></span> 

<span data-ttu-id="87c2b-170">Chaque type de tâche de machine learning présente des métriques qui permettent d’évaluer l’exactitude et la précision du modèle par rapport au jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="87c2b-170">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="87c2b-171">Dans notre exemple de prix des maisons, nous avons utilisé la tâche de **régression**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-171">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="87c2b-172">Pour évaluer le modèle, ajoutez le code suivant à l’exemple de code initial.</span><span class="sxs-lookup"><span data-stu-id="87c2b-172">To evaluate the model, add the following code to the original sample.</span></span>

```csharp
        HouseData[] testHouseData =
        {
            new HouseData() { Size = 1.1F, Price = 0.98F },
            new HouseData() { Size = 1.9F, Price = 2.1F },
            new HouseData() { Size = 2.8F, Price = 2.9F },
            new HouseData() { Size = 3.4F, Price = 3.6F }
        };

        var testHouseDataView = mlContext.Data.LoadFromEnumerable(testHouseData);
        var testPriceDataView = model.Transform(testHouseDataView);
                
        var metrics = mlContext.Regression.Evaluate(testPriceDataView, labelColumnName: "Price");

        Console.WriteLine($"R^2: {metrics.RSquared:0.##}");
        Console.WriteLine($"RMS error: {metrics.RootMeanSquaredError:0.##}");

        // R^2: 0.96
        // RMS error: 0.19
```

<span data-ttu-id="87c2b-173">Les métriques d’évaluation indiquent une erreur relativement faible, et une forte corrélation entre la sortie prédite et la sortie du test.</span><span class="sxs-lookup"><span data-stu-id="87c2b-173">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="87c2b-174">C’était facile !</span><span class="sxs-lookup"><span data-stu-id="87c2b-174">That was easy!</span></span> <span data-ttu-id="87c2b-175">En réalité, vous aurez davantage de réglages à faire pour parvenir à des métriques de modèle satisfaisantes.</span><span class="sxs-lookup"><span data-stu-id="87c2b-175">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="87c2b-176">Architecture de ML.NET</span><span class="sxs-lookup"><span data-stu-id="87c2b-176">ML.NET architecture</span></span>

<span data-ttu-id="87c2b-177">Dans cette section, nous allons examiner les modèles architecturaux de ML.NET.</span><span class="sxs-lookup"><span data-stu-id="87c2b-177">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="87c2b-178">Si vous êtes un développeur .NET expérimenté, certains de ces modèles vous sont déjà familiers, et d’autres moins.</span><span class="sxs-lookup"><span data-stu-id="87c2b-178">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="87c2b-179">Ne perdez pas le fil pendant ces explications !</span><span class="sxs-lookup"><span data-stu-id="87c2b-179">Hold tight, while we dive in!</span></span>

<span data-ttu-id="87c2b-180">Au démarrage de toute application ML.NET, il y a un objet <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="87c2b-180">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="87c2b-181">Cet objet singleton contient des **catalogues**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-181">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="87c2b-182">Un catalogue est une fabrique pour les composants de chargement et d’enregistrement des données, des transformations, des entraîneurs et de l’utilisation du modèle.</span><span class="sxs-lookup"><span data-stu-id="87c2b-182">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="87c2b-183">Chaque objet catalogue a des méthodes permettant de créer les différents types de composants :</span><span class="sxs-lookup"><span data-stu-id="87c2b-183">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="87c2b-184">Enregistrement et chargement des données</span><span class="sxs-lookup"><span data-stu-id="87c2b-184">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="87c2b-185">Préparation des données</span><span class="sxs-lookup"><span data-stu-id="87c2b-185">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="87c2b-186">Algorithmes d’entraînement</span><span class="sxs-lookup"><span data-stu-id="87c2b-186">Training algorithms</span></span>|<span data-ttu-id="87c2b-187">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="87c2b-187">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="87c2b-188">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="87c2b-188">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="87c2b-189">Détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="87c2b-189">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="87c2b-190">Clustering</span><span class="sxs-lookup"><span data-stu-id="87c2b-190">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="87c2b-191">Prévision</span><span class="sxs-lookup"><span data-stu-id="87c2b-191">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="87c2b-192">Classement</span><span class="sxs-lookup"><span data-stu-id="87c2b-192">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="87c2b-193">Régression</span><span class="sxs-lookup"><span data-stu-id="87c2b-193">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="87c2b-194">Recommandation</span><span class="sxs-lookup"><span data-stu-id="87c2b-194">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="87c2b-195">Ajouter le package NuGet `Microsoft.ML.Recommender`</span><span class="sxs-lookup"><span data-stu-id="87c2b-195">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="87c2b-196">TimeSeries</span><span class="sxs-lookup"><span data-stu-id="87c2b-196">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="87c2b-197">Ajouter le package NuGet `Microsoft.ML.TimeSeries`</span><span class="sxs-lookup"><span data-stu-id="87c2b-197">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="87c2b-198">Utilisation du modèle</span><span class="sxs-lookup"><span data-stu-id="87c2b-198">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="87c2b-199">Vous pouvez accéder aux méthodes de création dans chacune des catégories ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="87c2b-199">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="87c2b-200">Dans Visual Studio, les catalogues s’affichent via IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="87c2b-200">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![IntelliSense pour les entraîneurs de régression](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="87c2b-202">Créer le pipeline</span><span class="sxs-lookup"><span data-stu-id="87c2b-202">Build the pipeline</span></span>

<span data-ttu-id="87c2b-203">Chaque catalogue contient un ensemble de méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="87c2b-203">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="87c2b-204">Examinons de quelle manière les méthodes d’extension sont utilisées pour créer un pipeline d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="87c2b-204">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="87c2b-205">Dans l’extrait de code, `Concatenate` et `Sdca` sont deux méthodes figurant dans le catalogue.</span><span class="sxs-lookup"><span data-stu-id="87c2b-205">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="87c2b-206">Chaque méthode crée un objet [IEstimator](xref:Microsoft.ML.IEstimator%601) qui est ajouté au pipeline.</span><span class="sxs-lookup"><span data-stu-id="87c2b-206">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="87c2b-207">À ce stade, les objets sont seulement créés.</span><span class="sxs-lookup"><span data-stu-id="87c2b-207">At this point, the objects are created only.</span></span> <span data-ttu-id="87c2b-208">Ils ne sont pas exécutés.</span><span class="sxs-lookup"><span data-stu-id="87c2b-208">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="87c2b-209">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="87c2b-209">Train the model</span></span>

<span data-ttu-id="87c2b-210">Une fois que les objets dans le pipeline ont été créés, les données peuvent être utilisées pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="87c2b-210">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="87c2b-211">L’appel de `Fit()` déclenche l’utilisation des données d’entraînement d’entrée pour estimer les paramètres du modèle.</span><span class="sxs-lookup"><span data-stu-id="87c2b-211">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="87c2b-212">Ce processus est l’entraînement du modèle.</span><span class="sxs-lookup"><span data-stu-id="87c2b-212">This is known as training the model.</span></span> <span data-ttu-id="87c2b-213">Souvenez-vous, le modèle de régression linéaire vu plus haut avait deux paramètres de modèle : le **biais** et le **poids**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-213">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="87c2b-214">Après l’appel de `Fit()`, les valeurs des paramètres sont connues.</span><span class="sxs-lookup"><span data-stu-id="87c2b-214">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="87c2b-215">La plupart des modèles ont beaucoup plus de paramètres que cela.</span><span class="sxs-lookup"><span data-stu-id="87c2b-215">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="87c2b-216">Pour plus d’informations sur l’entraînement du modèle, consultez [Entraîner votre modèle](./how-to-guides/train-machine-learning-model-ml-net.md)</span><span class="sxs-lookup"><span data-stu-id="87c2b-216">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md)</span></span>

<span data-ttu-id="87c2b-217">L’objet modèle obtenu implémente l’interface <xref:Microsoft.ML.ITransformer>.</span><span class="sxs-lookup"><span data-stu-id="87c2b-217">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="87c2b-218">Autrement dit, le modèle transforme les données d’entrée en prédictions.</span><span class="sxs-lookup"><span data-stu-id="87c2b-218">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="87c2b-219">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="87c2b-219">Use the model</span></span>

<span data-ttu-id="87c2b-220">Vous pouvez transformer les données d’entrée en prédictions soit en bloc, soit entrée par entrée.</span><span class="sxs-lookup"><span data-stu-id="87c2b-220">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="87c2b-221">Dans l’exemple des prix de maisons, nous avons fait les deux : en bloc pour l’évaluation du modèle et entrée par entrée pour effectuer une nouvelle prédiction.</span><span class="sxs-lookup"><span data-stu-id="87c2b-221">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="87c2b-222">Examinons le cas des prédictions uniques.</span><span class="sxs-lookup"><span data-stu-id="87c2b-222">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```
 
<span data-ttu-id="87c2b-223">La méthode `CreatePredictionEngine()` a une classe d’entrée et une classe de sortie.</span><span class="sxs-lookup"><span data-stu-id="87c2b-223">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="87c2b-224">Les noms de champs et/ou les attributs de code déterminent les noms des colonnes de données utilisées durant l’entraînement du modèle et la prédiction de données.</span><span class="sxs-lookup"><span data-stu-id="87c2b-224">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="87c2b-225">Pour savoir [comment effectuer une prédiction unique](./how-to-guides/single-predict-model-ml-net.md), consultez la section des guides pratiques.</span><span class="sxs-lookup"><span data-stu-id="87c2b-225">You can read about  [How to make a single prediction](./how-to-guides/single-predict-model-ml-net.md) in the How-to section.</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="87c2b-226">Schéma et modèles de données</span><span class="sxs-lookup"><span data-stu-id="87c2b-226">Data models and schema</span></span>

<span data-ttu-id="87c2b-227">Les objets [DataView](xref:Microsoft.ML.IDataView) sont au cœur du pipeline de machine learning de ML.NET.</span><span class="sxs-lookup"><span data-stu-id="87c2b-227">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="87c2b-228">Chaque transformation dans le pipeline a deux schémas : un schéma d’entrée (noms de données, types et tailles que la transformation s’attend à voir dans son entrée) et un schéma de sortie (noms de données, types et tailles générés suite à l’exécution de la transformation).</span><span class="sxs-lookup"><span data-stu-id="87c2b-228">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span> <span data-ttu-id="87c2b-229">Le document suivant explique de façon détaillée l’[interface IDataView et son système de type](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span><span class="sxs-lookup"><span data-stu-id="87c2b-229">The following document provides an in-depth explanation of the [IDataView interface and its type system](https://xadupre.github.io/machinelearningext/mlnetdocs/idataviewtypesystem.html).</span></span>

<span data-ttu-id="87c2b-230">Si le schéma de sortie d’une transformation dans le pipeline ne correspond pas au schéma d’entrée de la transformation suivante, ML.NET lève une exception.</span><span class="sxs-lookup"><span data-stu-id="87c2b-230">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="87c2b-231">Un objet vue de données contient des colonnes et des lignes.</span><span class="sxs-lookup"><span data-stu-id="87c2b-231">A data view object has columns and rows.</span></span> <span data-ttu-id="87c2b-232">Chaque colonne a un nom, un type et une longueur.</span><span class="sxs-lookup"><span data-stu-id="87c2b-232">Each column has a name and a type and a length.</span></span> <span data-ttu-id="87c2b-233">Par exemple, les colonnes d’entrée dans l’exemple des prix de maisons sont **Size** et **Price**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-233">For example: the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="87c2b-234">Elles ont toutes deux un type et représentent des quantités scalaires plutôt que des quantités de vecteur.</span><span class="sxs-lookup"><span data-stu-id="87c2b-234">They are both type  and they are scalar quantities rather than vector ones.</span></span>

   ![Exemple d’objet vue de données dans ML.NET avec les données de prédiction des prix de maisons](./media/ml-net-dataview.png)

<span data-ttu-id="87c2b-236">Tous les algorithmes ML.NET recherchent une colonne d’entrée de type vecteur.</span><span class="sxs-lookup"><span data-stu-id="87c2b-236">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="87c2b-237">Par défaut, cette colonne vecteur est appelée **Features** (Caractéristiques).</span><span class="sxs-lookup"><span data-stu-id="87c2b-237">By default this vector column is called **Features**.</span></span> <span data-ttu-id="87c2b-238">C’est pourquoi nous avons concaténé la colonne **Size** dans une nouvelle colonne appelée **Features** dans notre exemple de prix de maisons.</span><span class="sxs-lookup"><span data-stu-id="87c2b-238">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="87c2b-239">Tous les algorithmes créent également des colonnes après avoir effectué une prédiction.</span><span class="sxs-lookup"><span data-stu-id="87c2b-239">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="87c2b-240">Les noms fixes de ces nouvelles colonnes dépendent du type d’algorithme de machine learning.</span><span class="sxs-lookup"><span data-stu-id="87c2b-240">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="87c2b-241">Pour la tâche de régression, l’une des nouvelles colonnes s’appelle **Score**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-241">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="87c2b-242">C’est pourquoi nous avons attribué ce nom à nos données de prix.</span><span class="sxs-lookup"><span data-stu-id="87c2b-242">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```    

<span data-ttu-id="87c2b-243">Pour plus d’informations sur les colonnes de sortie des différentes tâches de machine learning, consultez le guide [Tâches de machine learning](resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="87c2b-243">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="87c2b-244">Gardez à l’esprit que les objets DataView sont évalués **tardivement**.</span><span class="sxs-lookup"><span data-stu-id="87c2b-244">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="87c2b-245">Les objets vue de données sont uniquement chargés et traités pendant l’entraînement et l’évaluation du modèle, et durant la prédiction de données.</span><span class="sxs-lookup"><span data-stu-id="87c2b-245">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="87c2b-246">Lors des phases d’écriture et de test de votre application ML.NET, vous pouvez utiliser le débogueur Visual Studio pour avoir un aperçu d’un objet vue de données en appelant la méthode [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*).</span><span class="sxs-lookup"><span data-stu-id="87c2b-246">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview*) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="87c2b-247">Vous pouvez voir la variable `debug` dans le débogueur et examiner son contenu.</span><span class="sxs-lookup"><span data-stu-id="87c2b-247">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="87c2b-248">N’utilisez pas la méthode Preview dans le code de production, car elle dégrade considérablement les performances.</span><span class="sxs-lookup"><span data-stu-id="87c2b-248">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="87c2b-249">Déploiement du modèle</span><span class="sxs-lookup"><span data-stu-id="87c2b-249">Model Deployment</span></span>

<span data-ttu-id="87c2b-250">Dans les applications réelles, votre code d’entraînement et d’évaluation du modèle sera séparé de votre code de prédiction.</span><span class="sxs-lookup"><span data-stu-id="87c2b-250">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="87c2b-251">En fait, ces deux activités sont souvent effectuées par des équipes distinctes.</span><span class="sxs-lookup"><span data-stu-id="87c2b-251">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="87c2b-252">L’équipe de développement du modèle peut enregistrer le modèle pour une utilisation dans l’application de prédiction.</span><span class="sxs-lookup"><span data-stu-id="87c2b-252">Your model development team can save the model for use in the prediction application.</span></span>

```csharp   
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="where-to-now"></a><span data-ttu-id="87c2b-253">Et maintenant ?</span><span class="sxs-lookup"><span data-stu-id="87c2b-253">Where to now?</span></span>

<span data-ttu-id="87c2b-254">Vous pouvez suivre plusieurs [tutoriels](./tutorials/index.md) pour apprendre à créer des applications avec différentes tâches de machine learning en utilisant des jeux de données plus réalistes.</span><span class="sxs-lookup"><span data-stu-id="87c2b-254">You can learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

<span data-ttu-id="87c2b-255">Ou vous pouvez approfondir vos connaissances en consultant les [guides pratiques](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="87c2b-255">Or you can learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

<span data-ttu-id="87c2b-256">Et si vous en avez envie, vous pouvez directement vous plonger dans la [documentation de référence des API](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet) !</span><span class="sxs-lookup"><span data-stu-id="87c2b-256">And if you're super keen, you can dive straight into the [API Reference documentation](https://docs.microsoft.com/dotnet/api/?view=ml-dotnet)!</span></span>
