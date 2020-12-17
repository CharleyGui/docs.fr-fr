---
title: Présentation de ML.NET et de son fonctionnement
description: ML.NET vous donne la possibilité d’ajouter le Machine Learning aux applications .NET, dans des scénarios en ligne ou hors connexion. Avec cette fonctionnalité, vous pouvez ensuite effectuer des prédictions automatiques à partir des données disponibles dans votre application sans devoir être connecté à un réseau pour utiliser ML.NET. Cet article explique les principes de base du machine learning dans ML.NET.
ms.date: 11/5/2019
ms.topic: overview
ms.custom: mvc
ms.openlocfilehash: 2c44a83b4d45c95cbe45f125523207811f6368c2
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97634064"
---
# <a name="what-is-mlnet-and-how-does-it-work"></a><span data-ttu-id="cb13d-105">Présentation de ML.NET et de son fonctionnement</span><span class="sxs-lookup"><span data-stu-id="cb13d-105">What is ML.NET and how does it work?</span></span>

<span data-ttu-id="cb13d-106">ML.NET vous donne la possibilité d’ajouter le Machine Learning aux applications .NET, dans des scénarios en ligne ou hors connexion.</span><span class="sxs-lookup"><span data-stu-id="cb13d-106">ML.NET gives you the ability to add machine learning to .NET applications, in either online or offline scenarios.</span></span> <span data-ttu-id="cb13d-107">Avec cette fonctionnalité, vous pouvez ensuite effectuer des prédictions automatiques à partir des données disponibles dans votre application.</span><span class="sxs-lookup"><span data-stu-id="cb13d-107">With this capability, you can make automatic predictions using the data available to your application.</span></span> <span data-ttu-id="cb13d-108">Les applications machine learning utilisent des modèles dans les données pour faire des prédictions plutôt que de devoir être programmées explicitement.</span><span class="sxs-lookup"><span data-stu-id="cb13d-108">Machine learning applications make use of patterns in the data to make predictions rather than needing to be explicitly programmed.</span></span>

<span data-ttu-id="cb13d-109">Central vers ML.NET est un **modèle** machine learning.</span><span class="sxs-lookup"><span data-stu-id="cb13d-109">Central to ML.NET is a machine learning **model**.</span></span> <span data-ttu-id="cb13d-110">Le modèle spécifie les étapes nécessaires à la transformation des données d’entrée en prédiction.</span><span class="sxs-lookup"><span data-stu-id="cb13d-110">The model specifies the steps needed to transform your input data into a prediction.</span></span> <span data-ttu-id="cb13d-111">Avec ML.NET, vous pouvez effectuer l’apprentissage d’un modèle personnalisé en spécifiant un algorithme, ou vous pouvez importer des modèles TensorFlow et ONNX préformés.</span><span class="sxs-lookup"><span data-stu-id="cb13d-111">With ML.NET, you can train a custom model by specifying an algorithm, or you can import pre-trained TensorFlow and ONNX models.</span></span>

<span data-ttu-id="cb13d-112">Une fois que vous disposez d’un modèle, vous pouvez l’ajouter à votre application pour effectuer les prédictions.</span><span class="sxs-lookup"><span data-stu-id="cb13d-112">Once you have a model, you can add it to your application to make the predictions.</span></span>

<span data-ttu-id="cb13d-113">ML.NET s’exécute sur Windows, Linux et macOS à l’aide de .NET Core ou de Windows à l’aide de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cb13d-113">ML.NET runs on Windows, Linux, and macOS using .NET Core, or Windows using .NET Framework.</span></span> <span data-ttu-id="cb13d-114">64 bits est pris en charge sur toutes les plateformes.</span><span class="sxs-lookup"><span data-stu-id="cb13d-114">64 bit is supported on all platforms.</span></span> <span data-ttu-id="cb13d-115">32 bits est pris en charge sur Windows, à l’exception des fonctionnalités TensorFlow, LightGBM et ONNX.</span><span class="sxs-lookup"><span data-stu-id="cb13d-115">32 bit is supported on Windows, except for TensorFlow, LightGBM, and ONNX-related functionality.</span></span>

<span data-ttu-id="cb13d-116">Exemples du type de prédictions que vous pouvez effectuer avec ML.NET :</span><span class="sxs-lookup"><span data-stu-id="cb13d-116">Examples of the type of predictions that you can make with ML.NET:</span></span>

|||
|-|-|
|<span data-ttu-id="cb13d-117">Classification/catégorisation</span><span class="sxs-lookup"><span data-stu-id="cb13d-117">Classification/Categorization</span></span>|<span data-ttu-id="cb13d-118">Diviser automatiquement les commentaires des clients en catégories positives et négatives</span><span class="sxs-lookup"><span data-stu-id="cb13d-118">Automatically divide customer feedback into positive and negative categories</span></span>|
|<span data-ttu-id="cb13d-119">Régression/prédiction de valeurs continues</span><span class="sxs-lookup"><span data-stu-id="cb13d-119">Regression/Predict continuous values</span></span>|<span data-ttu-id="cb13d-120">Prédire le prix de maisons en fonction de la taille et de l’emplacement</span><span class="sxs-lookup"><span data-stu-id="cb13d-120">Predict the price of houses based on size and location</span></span>|
|<span data-ttu-id="cb13d-121">Détection des anomalies</span><span class="sxs-lookup"><span data-stu-id="cb13d-121">Anomaly Detection</span></span>|<span data-ttu-id="cb13d-122">Détecter les transactions bancaires frauduleuses</span><span class="sxs-lookup"><span data-stu-id="cb13d-122">Detect fraudulent banking transactions</span></span> |
|<span data-ttu-id="cb13d-123">Recommandations</span><span class="sxs-lookup"><span data-stu-id="cb13d-123">Recommendations</span></span>|<span data-ttu-id="cb13d-124">Suggérer des produits que les acheteurs en ligne peuvent souhaiter acheter, en fonction de leurs achats précédents</span><span class="sxs-lookup"><span data-stu-id="cb13d-124">Suggest products that online shoppers may want to buy, based on their previous purchases</span></span>|
|<span data-ttu-id="cb13d-125">Séries chronologiques/données séquentielles</span><span class="sxs-lookup"><span data-stu-id="cb13d-125">Time series/sequential data</span></span>|<span data-ttu-id="cb13d-126">Prévoir les ventes météo/produit</span><span class="sxs-lookup"><span data-stu-id="cb13d-126">Forecast the weather/product sales</span></span>|
|<span data-ttu-id="cb13d-127">Classification d’images</span><span class="sxs-lookup"><span data-stu-id="cb13d-127">Image classification</span></span>|<span data-ttu-id="cb13d-128">Classer les pathologies dans des images médicales</span><span class="sxs-lookup"><span data-stu-id="cb13d-128">Categorize pathologies in medical images</span></span>|

## <a name="hello-mlnet-world"></a><span data-ttu-id="cb13d-129">Hello ML.NET World</span><span class="sxs-lookup"><span data-stu-id="cb13d-129">Hello ML.NET World</span></span>

<span data-ttu-id="cb13d-130">Le code dans l’extrait suivant illustre l’application ML.NET la plus simple.</span><span class="sxs-lookup"><span data-stu-id="cb13d-130">The code in the following snippet demonstrates the simplest ML.NET application.</span></span> <span data-ttu-id="cb13d-131">Cet exemple crée un modèle de régression linéaire pour prédire les prix de maisons à partir des données de superficie et des prix immobiliers.</span><span class="sxs-lookup"><span data-stu-id="cb13d-131">This example constructs a linear regression model to predict house prices using house size and price data.</span></span>

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

## <a name="code-workflow"></a><span data-ttu-id="cb13d-132">Workflow du code</span><span class="sxs-lookup"><span data-stu-id="cb13d-132">Code workflow</span></span>

<span data-ttu-id="cb13d-133">Le diagramme suivant représente la structure du code de l’application ainsi que le processus itératif de développement du modèle :</span><span class="sxs-lookup"><span data-stu-id="cb13d-133">The following diagram represents the application code structure, as well as the iterative process of model development:</span></span>

- <span data-ttu-id="cb13d-134">Collecter et charger des données d’entraînement dans un objet **IDataView**</span><span class="sxs-lookup"><span data-stu-id="cb13d-134">Collect and load training data into an **IDataView** object</span></span>
- <span data-ttu-id="cb13d-135">Spécifier un pipeline d’opérations pour extraire des caractéristiques et appliquer un algorithme de machine learning</span><span class="sxs-lookup"><span data-stu-id="cb13d-135">Specify a pipeline of operations to extract features and apply a machine learning algorithm</span></span>
- <span data-ttu-id="cb13d-136">Entraîner un modèle en appelant **Fit()** sur le pipeline</span><span class="sxs-lookup"><span data-stu-id="cb13d-136">Train a model by calling **Fit()** on the pipeline</span></span>
- <span data-ttu-id="cb13d-137">Évaluer le modèle et effectuer des itérations pour l’améliorer</span><span class="sxs-lookup"><span data-stu-id="cb13d-137">Evaluate the model and iterate to improve</span></span>
- <span data-ttu-id="cb13d-138">Enregistrer le modèle au format binaire pour l’utiliser dans une application</span><span class="sxs-lookup"><span data-stu-id="cb13d-138">Save the model into binary format, for use in an application</span></span>
- <span data-ttu-id="cb13d-139">Recharger le modèle dans un objet **ITransformer**</span><span class="sxs-lookup"><span data-stu-id="cb13d-139">Load the model back into an **ITransformer** object</span></span>
- <span data-ttu-id="cb13d-140">Effectuer des prédictions en appelant **CreatePredictionEngine.Predict()**</span><span class="sxs-lookup"><span data-stu-id="cb13d-140">Make predictions by calling **CreatePredictionEngine.Predict()**</span></span>

![Workflow du développement d’application ML.NET, avec les composants pour la génération des données, le développement du pipeline, l’entraînement du modèle, l’évaluation du modèle et l’utilisation du modèle](./media/mldotnet-annotated-workflow.png)

<span data-ttu-id="cb13d-142">Revoyons maintenant tous ces concepts un peu plus en détail.</span><span class="sxs-lookup"><span data-stu-id="cb13d-142">Let's dig a little deeper into those concepts.</span></span>

## <a name="machine-learning-model"></a><span data-ttu-id="cb13d-143">Modèle Machine Learning</span><span class="sxs-lookup"><span data-stu-id="cb13d-143">Machine learning model</span></span>

<span data-ttu-id="cb13d-144">Un modèle ML.NET est un objet qui contient des transformations à effectuer sur vos données d’entrée pour produire la sortie prédite.</span><span class="sxs-lookup"><span data-stu-id="cb13d-144">An ML.NET model is an object that contains transformations to perform on your input data to arrive at the predicted output.</span></span>

### <a name="basic"></a><span data-ttu-id="cb13d-145">De base</span><span class="sxs-lookup"><span data-stu-id="cb13d-145">Basic</span></span>

<span data-ttu-id="cb13d-146">Le modèle de base, le plus simple, est la régression linéaire à deux dimensions, où une quantité continue est proportionnelle à une autre, comme dans l’exemple des prix de maisons ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="cb13d-146">The most basic model is two-dimensional linear regression, where one continuous quantity is proportional to another, as in the house price example above.</span></span>

![Modèle de régression linéaire avec des paramètres de biais et de poids](./media/linear-regression-model.svg)

<span data-ttu-id="cb13d-148">Le modèle est simple : $Price = b + Size \* w$.</span><span class="sxs-lookup"><span data-stu-id="cb13d-148">The model is simply: $Price = b + Size \* w$.</span></span> <span data-ttu-id="cb13d-149">Les paramètres $b$ et $w$ sont estimés en ajustant une ligne sur un ensemble de paires de valeurs (size, price).</span><span class="sxs-lookup"><span data-stu-id="cb13d-149">The parameters $b$ and $w$ are estimated by fitting a line on a set of (size, price) pairs.</span></span> <span data-ttu-id="cb13d-150">Les données utilisées pour rechercher les paramètres du modèle sont appelées **données d’entraînement**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-150">The data used to find the parameters of the model is called **training data**.</span></span> <span data-ttu-id="cb13d-151">Les entrées d’un modèle Machine Learning sont des **caractéristiques**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-151">The inputs of a machine learning model are called **features**.</span></span> <span data-ttu-id="cb13d-152">Dans cet exemple, $Size$ est la seule caractéristique.</span><span class="sxs-lookup"><span data-stu-id="cb13d-152">In this example, $Size$ is the only feature.</span></span> <span data-ttu-id="cb13d-153">Les valeurs certifiées vraies utilisées pour entraîner un modèle Machine Learning sont appelées des **étiquettes**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-153">The ground-truth values used to train a machine learning model are called **labels**.</span></span> <span data-ttu-id="cb13d-154">Ici, les étiquettes sont les valeurs $Price$ contenues dans le jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="cb13d-154">Here, the $Price$ values in the training data set are the labels.</span></span>

### <a name="more-complex"></a><span data-ttu-id="cb13d-155">Plus complexe</span><span class="sxs-lookup"><span data-stu-id="cb13d-155">More complex</span></span>

<span data-ttu-id="cb13d-156">Un modèle plus complexe classe les transactions financières dans différentes catégories en fonction du texte de description de la transaction.</span><span class="sxs-lookup"><span data-stu-id="cb13d-156">A more complex model classifies financial transactions into categories using the transaction text description.</span></span>

<span data-ttu-id="cb13d-157">Chaque description de transaction est décomposée en un ensemble de caractéristiques, après suppression des mots et caractères redondants, et comptage des combinaisons de mots et caractères.</span><span class="sxs-lookup"><span data-stu-id="cb13d-157">Each transaction description is broken down into a set of features by removing redundant words and characters, and counting word and character combinations.</span></span> <span data-ttu-id="cb13d-158">L’ensemble des caractéristiques est ensuite utilisé pour entraîner un modèle linéaire basé sur l’ensemble des catégories trouvées dans les données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="cb13d-158">The feature set is used to train a linear model based on the set of categories in the training data.</span></span> <span data-ttu-id="cb13d-159">Plus une nouvelle description se rapproche d’une des descriptions figurant dans le jeu de données d’entraînement, plus elle a de chance d’être attribuée à la même catégorie.</span><span class="sxs-lookup"><span data-stu-id="cb13d-159">The more similar a new description is to the ones in the training set, the more likely it will be assigned to the same category.</span></span>

![Modèle de classification de texte](./media/text-classification-model.svg)

<span data-ttu-id="cb13d-161">Le modèle de prix des maisons et le modèle de classification de texte sont tous les deux des modèles de type **linéaire**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-161">Both the house price model and the text classification model are **linear** models.</span></span> <span data-ttu-id="cb13d-162">Selon la nature de vos données et le problème à résoudre, vous pouvez également utiliser des modèles d’**arbre de décision**, des modèles **additifs généralisés** et d’autres modèles.</span><span class="sxs-lookup"><span data-stu-id="cb13d-162">Depending on the nature of your data and the problem you are solving, you can also use **decision tree** models, **generalized additive** models, and others.</span></span> <span data-ttu-id="cb13d-163">Pour plus d’informations sur les modèles, consultez [Tâches](./resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="cb13d-163">You can find out more about the models in [Tasks](./resources/tasks.md).</span></span>

## <a name="data-preparation"></a><span data-ttu-id="cb13d-164">Préparation des données</span><span class="sxs-lookup"><span data-stu-id="cb13d-164">Data preparation</span></span>

<span data-ttu-id="cb13d-165">Dans la plupart des cas, les données dont vous disposez ne peuvent pas être utilisées directement pour entraîner un modèle Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="cb13d-165">In most cases, the data that you have available isn't suitable to be used directly to train a machine learning model.</span></span> <span data-ttu-id="cb13d-166">Les données brutes doivent être préparées ou prétraitées avant de pouvoir être utilisées pour rechercher les paramètres de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="cb13d-166">The raw data needs to be prepared, or pre-processed, before it can be used to find the parameters of your model.</span></span> <span data-ttu-id="cb13d-167">Par exemple, vous devrez peut-être convertir vos données de valeurs de chaîne en une représentation numérique,</span><span class="sxs-lookup"><span data-stu-id="cb13d-167">Your data may need to be converted from string values to a numerical representation.</span></span> <span data-ttu-id="cb13d-168">supprimer des informations redondantes dans vos données d’entrée,</span><span class="sxs-lookup"><span data-stu-id="cb13d-168">You might have redundant information in your input data.</span></span> <span data-ttu-id="cb13d-169">réduire ou développer les dimensions de vos données d’entrée,</span><span class="sxs-lookup"><span data-stu-id="cb13d-169">You may need to reduce or expand the dimensions of your input data.</span></span> <span data-ttu-id="cb13d-170">ou encore normaliser ou redimensionner vos données.</span><span class="sxs-lookup"><span data-stu-id="cb13d-170">Your data might need to be normalized or scaled.</span></span>

<span data-ttu-id="cb13d-171">Les [tutoriels ML.NET](./tutorials/index.md) vous montrent différents pipelines de traitement des données (pour les données texte, d’image, numériques et de série chronologique) qui sont utilisés dans le cadre de tâches de machine learning spécifiques.</span><span class="sxs-lookup"><span data-stu-id="cb13d-171">The [ML.NET tutorials](./tutorials/index.md) teach you about different data processing pipelines for text, image, numerical, and time-series data used for specific machine learning tasks.</span></span>

<span data-ttu-id="cb13d-172">[La préparation de vos données](./how-to-guides/prepare-data-ml-net.md) vous montre comment appliquer la préparation des données plus généralement.</span><span class="sxs-lookup"><span data-stu-id="cb13d-172">[How to prepare your data](./how-to-guides/prepare-data-ml-net.md) shows you how to apply data preparation more generally.</span></span>

<span data-ttu-id="cb13d-173">Vous trouverez toutes les [transformations disponibles](./resources/transforms.md) en annexe, dans la section des ressources.</span><span class="sxs-lookup"><span data-stu-id="cb13d-173">You can find an appendix of all of the [available transformations](./resources/transforms.md) in the resources section.</span></span>

## <a name="model-evaluation"></a><span data-ttu-id="cb13d-174">Évaluation du modèle</span><span class="sxs-lookup"><span data-stu-id="cb13d-174">Model evaluation</span></span>

<span data-ttu-id="cb13d-175">Une fois que vous avez entraîné votre modèle, comment savoir si ses prédictions futures seront correctes ?</span><span class="sxs-lookup"><span data-stu-id="cb13d-175">Once you have trained your model, how do you know how well it will make future predictions?</span></span> <span data-ttu-id="cb13d-176">Avec ML.NET, vous pouvez évaluer votre modèle par rapport à de nouvelles données de test.</span><span class="sxs-lookup"><span data-stu-id="cb13d-176">With ML.NET, you can evaluate your model against some new test data.</span></span>

<span data-ttu-id="cb13d-177">Chaque type de tâche de machine learning présente des métriques qui permettent d’évaluer l’exactitude et la précision du modèle par rapport au jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="cb13d-177">Each type of machine learning task has metrics used to evaluate the accuracy and precision of the model against the test data set.</span></span>

<span data-ttu-id="cb13d-178">Dans notre exemple de prix des maisons, nous avons utilisé la tâche de **régression**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-178">For our house price example, we used the **Regression** task.</span></span> <span data-ttu-id="cb13d-179">Pour évaluer le modèle, ajoutez le code suivant à l’exemple de code initial.</span><span class="sxs-lookup"><span data-stu-id="cb13d-179">To evaluate the model, add the following code to the original sample.</span></span>

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

<span data-ttu-id="cb13d-180">Les métriques d’évaluation indiquent une erreur relativement faible, et une forte corrélation entre la sortie prédite et la sortie du test.</span><span class="sxs-lookup"><span data-stu-id="cb13d-180">The evaluation metrics tell you that the error is low-ish, and that correlation between the predicted output and the test output is high.</span></span> <span data-ttu-id="cb13d-181">Facile, n’est-ce pas ?</span><span class="sxs-lookup"><span data-stu-id="cb13d-181">That was easy!</span></span> <span data-ttu-id="cb13d-182">En réalité, vous aurez davantage de réglages à faire pour parvenir à des métriques de modèle satisfaisantes.</span><span class="sxs-lookup"><span data-stu-id="cb13d-182">In real examples, it takes more tuning to achieve good model metrics.</span></span>

## <a name="mlnet-architecture"></a><span data-ttu-id="cb13d-183">Architecture de ML.NET</span><span class="sxs-lookup"><span data-stu-id="cb13d-183">ML.NET architecture</span></span>

<span data-ttu-id="cb13d-184">Dans cette section, nous allons examiner les modèles architecturaux de ML.NET.</span><span class="sxs-lookup"><span data-stu-id="cb13d-184">In this section, we go through the architectural patterns of ML.NET.</span></span> <span data-ttu-id="cb13d-185">Si vous êtes un développeur .NET expérimenté, certains de ces modèles vous sont déjà familiers, et d’autres moins.</span><span class="sxs-lookup"><span data-stu-id="cb13d-185">If you are an experienced .NET developer, some of these patterns will be familiar to you, and some will be less familiar.</span></span> <span data-ttu-id="cb13d-186">Ne perdez pas le fil pendant ces explications !</span><span class="sxs-lookup"><span data-stu-id="cb13d-186">Hold tight, while we dive in!</span></span>

<span data-ttu-id="cb13d-187">Au démarrage de toute application ML.NET, il y a un objet <xref:Microsoft.ML.MLContext>.</span><span class="sxs-lookup"><span data-stu-id="cb13d-187">An ML.NET application starts with an <xref:Microsoft.ML.MLContext> object.</span></span> <span data-ttu-id="cb13d-188">Cet objet singleton contient des **catalogues**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-188">This singleton object contains **catalogs**.</span></span> <span data-ttu-id="cb13d-189">Un catalogue est une fabrique pour les composants de chargement et d’enregistrement des données, des transformations, des entraîneurs et de l’utilisation du modèle.</span><span class="sxs-lookup"><span data-stu-id="cb13d-189">A catalog is a factory for data loading and saving, transforms, trainers, and model operation components.</span></span> <span data-ttu-id="cb13d-190">Chaque objet catalogue a des méthodes permettant de créer les différents types de composants :</span><span class="sxs-lookup"><span data-stu-id="cb13d-190">Each catalog object has methods to create the different types of components:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="cb13d-191">Enregistrement et chargement des données</span><span class="sxs-lookup"><span data-stu-id="cb13d-191">Data loading and saving</span></span>||<xref:Microsoft.ML.DataOperationsCatalog>||
|<span data-ttu-id="cb13d-192">Préparation des données</span><span class="sxs-lookup"><span data-stu-id="cb13d-192">Data preparation</span></span>||<xref:Microsoft.ML.TransformsCatalog>||
|<span data-ttu-id="cb13d-193">Algorithmes d’entraînement</span><span class="sxs-lookup"><span data-stu-id="cb13d-193">Training algorithms</span></span>|<span data-ttu-id="cb13d-194">Classification binaire</span><span class="sxs-lookup"><span data-stu-id="cb13d-194">Binary classification</span></span>|<xref:Microsoft.ML.BinaryClassificationCatalog>||
||<span data-ttu-id="cb13d-195">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="cb13d-195">Multiclass classification</span></span>|<xref:Microsoft.ML.MulticlassClassificationCatalog>||
||<span data-ttu-id="cb13d-196">Détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="cb13d-196">Anomaly detection</span></span>|<xref:Microsoft.ML.AnomalyDetectionCatalog>||
||<span data-ttu-id="cb13d-197">Clustering</span><span class="sxs-lookup"><span data-stu-id="cb13d-197">Clustering</span></span>|<xref:Microsoft.ML.ClusteringCatalog>||
||<span data-ttu-id="cb13d-198">Prévisions</span><span class="sxs-lookup"><span data-stu-id="cb13d-198">Forecasting</span></span>|<xref:Microsoft.ML.ForecastingCatalog>||
||<span data-ttu-id="cb13d-199">Classement</span><span class="sxs-lookup"><span data-stu-id="cb13d-199">Ranking</span></span>|<xref:Microsoft.ML.RankingCatalog>||
||<span data-ttu-id="cb13d-200">régression ;</span><span class="sxs-lookup"><span data-stu-id="cb13d-200">Regression</span></span>|<xref:Microsoft.ML.RegressionCatalog>||
||<span data-ttu-id="cb13d-201">Recommandation</span><span class="sxs-lookup"><span data-stu-id="cb13d-201">Recommendation</span></span>|<xref:Microsoft.ML.RecommendationCatalog>|<span data-ttu-id="cb13d-202">Ajouter le package NuGet `Microsoft.ML.Recommender`</span><span class="sxs-lookup"><span data-stu-id="cb13d-202">add the `Microsoft.ML.Recommender` NuGet package</span></span>|
||<span data-ttu-id="cb13d-203">TimeSeries</span><span class="sxs-lookup"><span data-stu-id="cb13d-203">TimeSeries</span></span>|<xref:Microsoft.ML.TimeSeriesCatalog>|<span data-ttu-id="cb13d-204">Ajouter le package NuGet `Microsoft.ML.TimeSeries`</span><span class="sxs-lookup"><span data-stu-id="cb13d-204">add the `Microsoft.ML.TimeSeries` NuGet package</span></span>|
|<span data-ttu-id="cb13d-205">Utilisation du modèle</span><span class="sxs-lookup"><span data-stu-id="cb13d-205">Model usage</span></span> ||<xref:Microsoft.ML.ModelOperationsCatalog>||

<span data-ttu-id="cb13d-206">Vous pouvez accéder aux méthodes de création dans chacune des catégories ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="cb13d-206">You can navigate to the creation methods in each of the above categories.</span></span> <span data-ttu-id="cb13d-207">Dans Visual Studio, les catalogues s’affichent via IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="cb13d-207">Using Visual Studio, the catalogs show up via IntelliSense.</span></span>

   ![IntelliSense pour les entraîneurs de régression](./media/catalog-intellisense.png)

### <a name="build-the-pipeline"></a><span data-ttu-id="cb13d-209">Générer le pipeline</span><span class="sxs-lookup"><span data-stu-id="cb13d-209">Build the pipeline</span></span>

<span data-ttu-id="cb13d-210">Chaque catalogue contient un ensemble de méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="cb13d-210">Inside each catalog is a set of extension methods.</span></span> <span data-ttu-id="cb13d-211">Examinons de quelle manière les méthodes d’extension sont utilisées pour créer un pipeline d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="cb13d-211">Let's look at how extension methods are used to create a training pipeline.</span></span>

```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
        .Append(mlContext.Regression.Trainers.Sdca(labelColumnName: "Price", maximumNumberOfIterations: 100));
```

<span data-ttu-id="cb13d-212">Dans l’extrait de code, `Concatenate` et `Sdca` sont deux méthodes figurant dans le catalogue.</span><span class="sxs-lookup"><span data-stu-id="cb13d-212">In the snippet, `Concatenate` and `Sdca` are both methods in the catalog.</span></span> <span data-ttu-id="cb13d-213">Chaque méthode crée un objet [IEstimator](xref:Microsoft.ML.IEstimator%601) qui est ajouté au pipeline.</span><span class="sxs-lookup"><span data-stu-id="cb13d-213">They each create an [IEstimator](xref:Microsoft.ML.IEstimator%601) object that is appended to the pipeline.</span></span>

<span data-ttu-id="cb13d-214">À ce stade, les objets sont seulement créés.</span><span class="sxs-lookup"><span data-stu-id="cb13d-214">At this point, the objects are created only.</span></span> <span data-ttu-id="cb13d-215">Ils ne sont pas exécutés.</span><span class="sxs-lookup"><span data-stu-id="cb13d-215">No execution has happened.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="cb13d-216">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="cb13d-216">Train the model</span></span>

<span data-ttu-id="cb13d-217">Une fois que les objets dans le pipeline ont été créés, les données peuvent être utilisées pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="cb13d-217">Once the objects in the pipeline have been created, data can be used to train the model.</span></span>

```csharp
    var model = pipeline.Fit(trainingData);
```

<span data-ttu-id="cb13d-218">L’appel de `Fit()` déclenche l’utilisation des données d’entraînement d’entrée pour estimer les paramètres du modèle.</span><span class="sxs-lookup"><span data-stu-id="cb13d-218">Calling `Fit()` uses the input training data to estimate the parameters of the model.</span></span> <span data-ttu-id="cb13d-219">Ce processus est l’entraînement du modèle.</span><span class="sxs-lookup"><span data-stu-id="cb13d-219">This is known as training the model.</span></span> <span data-ttu-id="cb13d-220">Souvenez-vous, le modèle de régression linéaire vu plus haut avait deux paramètres de modèle : le **biais** et le **poids**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-220">Remember, the linear regression model above had two model parameters: **bias** and **weight**.</span></span> <span data-ttu-id="cb13d-221">Après l’appel de `Fit()`, les valeurs des paramètres sont connues.</span><span class="sxs-lookup"><span data-stu-id="cb13d-221">After the `Fit()` call, the values of the parameters are known.</span></span> <span data-ttu-id="cb13d-222">La plupart des modèles ont beaucoup plus de paramètres que cela.</span><span class="sxs-lookup"><span data-stu-id="cb13d-222">Most models will have many more parameters than this.</span></span>

<span data-ttu-id="cb13d-223">Vous pouvez en savoir plus sur l’apprentissage du modèle dans [la manière d’effectuer l’apprentissage de votre modèle](./how-to-guides/train-machine-learning-model-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="cb13d-223">You can learn more about model training in [How to train your model](./how-to-guides/train-machine-learning-model-ml-net.md).</span></span>

<span data-ttu-id="cb13d-224">L’objet modèle obtenu implémente l’interface <xref:Microsoft.ML.ITransformer>.</span><span class="sxs-lookup"><span data-stu-id="cb13d-224">The resulting model object implements the <xref:Microsoft.ML.ITransformer> interface.</span></span> <span data-ttu-id="cb13d-225">Autrement dit, le modèle transforme les données d’entrée en prédictions.</span><span class="sxs-lookup"><span data-stu-id="cb13d-225">That is, the model transforms input data into predictions.</span></span>

```csharp
   IDataView predictions = model.Transform(inputData);
```

### <a name="use-the-model"></a><span data-ttu-id="cb13d-226">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="cb13d-226">Use the model</span></span>

<span data-ttu-id="cb13d-227">Vous pouvez transformer les données d’entrée en prédictions soit en bloc, soit entrée par entrée.</span><span class="sxs-lookup"><span data-stu-id="cb13d-227">You can transform input data into predictions in bulk, or one input at a time.</span></span> <span data-ttu-id="cb13d-228">Dans l’exemple des prix de maisons, nous avons fait les deux : en bloc pour l’évaluation du modèle et entrée par entrée pour effectuer une nouvelle prédiction.</span><span class="sxs-lookup"><span data-stu-id="cb13d-228">In the house price example, we did both: in bulk for the purpose of evaluating the model, and one at a time to make a new prediction.</span></span> <span data-ttu-id="cb13d-229">Examinons le cas des prédictions uniques.</span><span class="sxs-lookup"><span data-stu-id="cb13d-229">Let's look at making single predictions.</span></span>

```csharp
    var size = new HouseData() { Size = 2.5F };
    var predEngine = mlContext.CreatePredictionEngine<HouseData, Prediction>(model);
    var price = predEngine.Predict(size);
```

<span data-ttu-id="cb13d-230">La méthode `CreatePredictionEngine()` a une classe d’entrée et une classe de sortie.</span><span class="sxs-lookup"><span data-stu-id="cb13d-230">The `CreatePredictionEngine()` method takes an input class and an output class.</span></span> <span data-ttu-id="cb13d-231">Les noms de champs et/ou les attributs de code déterminent les noms des colonnes de données utilisées durant l’entraînement du modèle et la prédiction de données.</span><span class="sxs-lookup"><span data-stu-id="cb13d-231">The field names and/or code attributes determine the names of the data columns used during model training and prediction.</span></span> <span data-ttu-id="cb13d-232">Pour plus d’informations, consultez [faire des prédictions avec un modèle formé](how-to-guides/machine-learning-model-predictions-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="cb13d-232">For more information, see [Make predictions with a trained model](how-to-guides/machine-learning-model-predictions-ml-net.md).</span></span>

### <a name="data-models-and-schema"></a><span data-ttu-id="cb13d-233">Schéma et modèles de données</span><span class="sxs-lookup"><span data-stu-id="cb13d-233">Data models and schema</span></span>

<span data-ttu-id="cb13d-234">Les objets [DataView](xref:Microsoft.ML.IDataView) sont au cœur du pipeline de machine learning de ML.NET.</span><span class="sxs-lookup"><span data-stu-id="cb13d-234">At the core of an ML.NET machine learning pipeline are [DataView](xref:Microsoft.ML.IDataView) objects.</span></span>

<span data-ttu-id="cb13d-235">Chaque transformation dans le pipeline a deux schémas : un schéma d’entrée (noms de données, types et tailles que la transformation s’attend à voir dans son entrée) et un schéma de sortie (noms de données, types et tailles générés suite à l’exécution de la transformation).</span><span class="sxs-lookup"><span data-stu-id="cb13d-235">Each transformation in the pipeline has an input schema (data names, types, and sizes that the transform expects to see on its input); and an output schema (data names, types, and sizes that the transform produces after the transformation).</span></span>

<span data-ttu-id="cb13d-236">Si le schéma de sortie d’une transformation dans le pipeline ne correspond pas au schéma d’entrée de la transformation suivante, ML.NET lève une exception.</span><span class="sxs-lookup"><span data-stu-id="cb13d-236">If the output schema from one transform in the pipeline doesn't match the input schema of the next transform, ML.NET will throw an exception.</span></span>

<span data-ttu-id="cb13d-237">Un objet vue de données contient des colonnes et des lignes.</span><span class="sxs-lookup"><span data-stu-id="cb13d-237">A data view object has columns and rows.</span></span> <span data-ttu-id="cb13d-238">Chaque colonne a un nom, un type et une longueur.</span><span class="sxs-lookup"><span data-stu-id="cb13d-238">Each column has a name and a type and a length.</span></span> <span data-ttu-id="cb13d-239">Par exemple, les colonnes d’entrée dans l’exemple de prix de la maison sont la **taille** et le **prix**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-239">For example, the input columns in the house price example are **Size** and **Price**.</span></span> <span data-ttu-id="cb13d-240">Ils sont tous deux de type et sont des quantités scalaires plutôt que des vecteurs.</span><span class="sxs-lookup"><span data-stu-id="cb13d-240">They are both type and they are scalar quantities rather than vector ones.</span></span>

   ![Exemple d’objet vue de données dans ML.NET avec les données de prédiction des prix de maisons](./media/ml-net-dataview.png)

<span data-ttu-id="cb13d-242">Tous les algorithmes ML.NET recherchent une colonne d’entrée de type vecteur.</span><span class="sxs-lookup"><span data-stu-id="cb13d-242">All ML.NET algorithms look for an input column that is a vector.</span></span> <span data-ttu-id="cb13d-243">Par défaut, cette colonne vecteur est appelée **Features** (Caractéristiques).</span><span class="sxs-lookup"><span data-stu-id="cb13d-243">By default this vector column is called **Features**.</span></span> <span data-ttu-id="cb13d-244">C’est pourquoi nous avons concaténé la colonne **Size** dans une nouvelle colonne appelée **Features** dans notre exemple de prix de maisons.</span><span class="sxs-lookup"><span data-stu-id="cb13d-244">This is why we concatenated the **Size** column into a new column called **Features** in our house price example.</span></span>

 ```csharp
    var pipeline = mlContext.Transforms.Concatenate("Features", new[] { "Size" })
 ```

<span data-ttu-id="cb13d-245">Tous les algorithmes créent également des colonnes après avoir effectué une prédiction.</span><span class="sxs-lookup"><span data-stu-id="cb13d-245">All algorithms also create new columns after they have performed a prediction.</span></span> <span data-ttu-id="cb13d-246">Les noms fixes de ces nouvelles colonnes dépendent du type d’algorithme de machine learning.</span><span class="sxs-lookup"><span data-stu-id="cb13d-246">The fixed names of these new columns depend on the type of machine learning algorithm.</span></span> <span data-ttu-id="cb13d-247">Pour la tâche de régression, l’une des nouvelles colonnes s’appelle **Score**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-247">For the regression task, one of the new columns is called **Score**.</span></span> <span data-ttu-id="cb13d-248">C’est pourquoi nous avons attribué ce nom à nos données de prix.</span><span class="sxs-lookup"><span data-stu-id="cb13d-248">This is why we attributed our price data with this name.</span></span>

```csharp
    public class Prediction
    {
        [ColumnName("Score")]
        public float Price { get; set; }
    }
```

<span data-ttu-id="cb13d-249">Pour plus d’informations sur les colonnes de sortie des différentes tâches de machine learning, consultez le guide [Tâches de machine learning](resources/tasks.md).</span><span class="sxs-lookup"><span data-stu-id="cb13d-249">You can find out more about output columns of different machine learning tasks in the [Machine Learning Tasks](resources/tasks.md) guide.</span></span>

<span data-ttu-id="cb13d-250">Gardez à l’esprit que les objets DataView sont évalués **tardivement**.</span><span class="sxs-lookup"><span data-stu-id="cb13d-250">An important property of DataView objects is that they are evaluated **lazily**.</span></span> <span data-ttu-id="cb13d-251">Les objets vue de données sont uniquement chargés et traités pendant l’entraînement et l’évaluation du modèle, et durant la prédiction de données.</span><span class="sxs-lookup"><span data-stu-id="cb13d-251">Data views are only loaded and operated on during model training and evaluation, and data prediction.</span></span> <span data-ttu-id="cb13d-252">Lors des phases d’écriture et de test de votre application ML.NET, vous pouvez utiliser le débogueur Visual Studio pour avoir un aperçu d’un objet vue de données en appelant la méthode [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview%2A).</span><span class="sxs-lookup"><span data-stu-id="cb13d-252">While you are writing and testing your ML.NET application, you can use the Visual Studio debugger to take a peek at any data view object by calling the [Preview](xref:Microsoft.ML.DebuggerExtensions.Preview%2A) method.</span></span>

```csharp
    var debug = testPriceDataView.Preview();
```

<span data-ttu-id="cb13d-253">Vous pouvez voir la variable `debug` dans le débogueur et examiner son contenu.</span><span class="sxs-lookup"><span data-stu-id="cb13d-253">You can watch the `debug` variable in the debugger and examine its contents.</span></span> <span data-ttu-id="cb13d-254">N’utilisez pas la méthode Preview dans le code de production, car elle dégrade considérablement les performances.</span><span class="sxs-lookup"><span data-stu-id="cb13d-254">Do not use the Preview method in production code, as it significantly degrades performance.</span></span>

### <a name="model-deployment"></a><span data-ttu-id="cb13d-255">Déploiement de modèle</span><span class="sxs-lookup"><span data-stu-id="cb13d-255">Model Deployment</span></span>

<span data-ttu-id="cb13d-256">Dans les applications réelles, votre code d’entraînement et d’évaluation du modèle sera séparé de votre code de prédiction.</span><span class="sxs-lookup"><span data-stu-id="cb13d-256">In real-life applications, your model training and evaluation code will be separate from your prediction.</span></span> <span data-ttu-id="cb13d-257">En fait, ces deux activités sont souvent effectuées par des équipes distinctes.</span><span class="sxs-lookup"><span data-stu-id="cb13d-257">In fact, these two activities are often performed by separate teams.</span></span> <span data-ttu-id="cb13d-258">L’équipe de développement du modèle peut enregistrer le modèle pour une utilisation dans l’application de prédiction.</span><span class="sxs-lookup"><span data-stu-id="cb13d-258">Your model development team can save the model for use in the prediction application.</span></span>

```csharp
   mlContext.Model.Save(model, trainingData.Schema,"model.zip");
```

## <a name="next-steps"></a><span data-ttu-id="cb13d-259">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cb13d-259">Next steps</span></span>

* <span data-ttu-id="cb13d-260">Découvrez comment créer des applications à l’aide de différentes tâches de Machine Learning avec des jeux de données plus réalistes dans les [didacticiels](./tutorials/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb13d-260">Learn how to build applications using different machine learning tasks with more realistic data sets in the [tutorials](./tutorials/index.md).</span></span>

* <span data-ttu-id="cb13d-261">En savoir plus sur des rubriques spécifiques plus en détail dans les [guides de procédures](./how-to-guides/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb13d-261">Learn about specific topics in more depth in the [How To Guides](./how-to-guides/index.md).</span></span>

* <span data-ttu-id="cb13d-262">Si vous êtes super, vous pouvez vous plonger directement dans la [documentation de référence](../../api/index.md?view=ml-dotnet)sur les API.</span><span class="sxs-lookup"><span data-stu-id="cb13d-262">If you're super keen, you can dive straight into the [API Reference documentation](../../api/index.md?view=ml-dotnet).</span></span>
