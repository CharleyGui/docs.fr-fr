---
title: 'Tutoriel : Classer des iris : clustering k-means'
description: Découvrez comment utiliser ML.NET dans un scénario de clustering
author: pkulikov
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: e360cf2418e2003f9f40628c714e9e8ebd7c3e40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698558"
---
# <a name="tutorial-categorize-iris-flowers-using-k-means-clustering-with-mlnet"></a><span data-ttu-id="4cc85-103">Tutoriel : Classer les fleurs d’iris à l’aide du clustering k-means avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="4cc85-103">Tutorial: Categorize iris flowers using k-means clustering with ML.NET</span></span>

<span data-ttu-id="4cc85-104">Ce tutoriel montre comment utiliser ML.NET pour générer un [modèle de clustering](../resources/tasks.md#clustering) pour le [jeu de données Iris](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span><span class="sxs-lookup"><span data-stu-id="4cc85-104">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="4cc85-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="4cc85-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4cc85-106">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="4cc85-106">Understand the problem</span></span>
> - <span data-ttu-id="4cc85-107">Sélectionner la tâche d’apprentissage automatique appropriée</span><span class="sxs-lookup"><span data-stu-id="4cc85-107">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="4cc85-108">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="4cc85-108">Prepare the data</span></span>
> - <span data-ttu-id="4cc85-109">Charger et transformer les données</span><span class="sxs-lookup"><span data-stu-id="4cc85-109">Load and transform the data</span></span>
> - <span data-ttu-id="4cc85-110">Choisir un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="4cc85-110">Choose a learning algorithm</span></span>
> - <span data-ttu-id="4cc85-111">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="4cc85-111">Train the model</span></span>
> - <span data-ttu-id="4cc85-112">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="4cc85-112">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4cc85-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="4cc85-113">Prerequisites</span></span>

- <span data-ttu-id="4cc85-114">[Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="4cc85-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="4cc85-115">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="4cc85-115">Understand the problem</span></span>

<span data-ttu-id="4cc85-116">Ce problème concerne la division de l’ensemble des iris en différents groupes basés sur les caractéristiques de la fleur.</span><span class="sxs-lookup"><span data-stu-id="4cc85-116">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="4cc85-117">Ces caractéristiques sont la longueur et la largeur d’un sépale, ainsi que la longueur et la largeur d’un pétale.</span><span class="sxs-lookup"><span data-stu-id="4cc85-117">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="4cc85-118">Pour ce tutoriel, supposons que le type de chaque fleur est inconnu.</span><span class="sxs-lookup"><span data-stu-id="4cc85-118">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="4cc85-119">Vous souhaitez connaître la structure d’un jeu de données à partir des caractéristiques et prédire la façon dont une instance de données s’intègre à cette structure.</span><span class="sxs-lookup"><span data-stu-id="4cc85-119">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="4cc85-120">Sélectionner la tâche d’apprentissage automatique appropriée</span><span class="sxs-lookup"><span data-stu-id="4cc85-120">Select the appropriate machine learning task</span></span>

<span data-ttu-id="4cc85-121">Comme vous ne savez pas à quel groupe appartient chaque fleur, vous choisissez la tâche [Apprentissage automatique non supervisé](../resources/glossary.md#unsupervised-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="4cc85-121">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="4cc85-122">Pour diviser un jeu de données en groupes de telle sorte que les éléments dans le même groupe soient plus similaires les uns aux autres qu’à ceux des autres groupes, utilisez une tâche d’apprentissage automatique de [clustering](../resources/tasks.md#clustering).</span><span class="sxs-lookup"><span data-stu-id="4cc85-122">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4cc85-123">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="4cc85-123">Create a console application</span></span>

1. <span data-ttu-id="4cc85-124">Ouvrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4cc85-124">Open Visual Studio.</span></span> <span data-ttu-id="4cc85-125">Sélectionnez **Fichier** > **Nouveau** > **Projet** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="4cc85-125">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="4cc85-126">Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-126">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="4cc85-127">Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)** .</span><span class="sxs-lookup"><span data-stu-id="4cc85-127">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="4cc85-128">Dans la zone de texte **Nom**, tapez « IrisFlowerClustering », puis sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-128">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="4cc85-129">Créez un répertoire nommé *Data* dans votre projet pour enregistrer le jeu de données et les fichiers de modèle :</span><span class="sxs-lookup"><span data-stu-id="4cc85-129">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="4cc85-130">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-130">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="4cc85-131">Tapez « Données » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="4cc85-131">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="4cc85-132">Installez le package NuGet **Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="4cc85-132">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="4cc85-133">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-133">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4cc85-134">Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package **v1.0.0** dans la liste, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-134">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="4cc85-135">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="4cc85-135">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="4cc85-136">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="4cc85-136">Prepare the data</span></span>

1. <span data-ttu-id="4cc85-137">Téléchargez le jeu de données [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) et enregistrez-le dans le dossier *Data* que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="4cc85-137">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="4cc85-138">Pour plus d’informations sur le jeu de données Iris, consultez la page Wikipédia [Iris de Fisher](https://en.wikipedia.org/wiki/Iris_flower_data_set) et la page [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris), qui est la source du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="4cc85-138">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="4cc85-139">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier *iris.data* et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-139">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="4cc85-140">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-140">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="4cc85-141">Le fichier *iris.data* contient cinq colonnes qui représentent :</span><span class="sxs-lookup"><span data-stu-id="4cc85-141">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="4cc85-142">la longueur des sépales en centimètres</span><span class="sxs-lookup"><span data-stu-id="4cc85-142">sepal length in centimetres</span></span>
- <span data-ttu-id="4cc85-143">la largeur des sépales en centimètres</span><span class="sxs-lookup"><span data-stu-id="4cc85-143">sepal width in centimetres</span></span>
- <span data-ttu-id="4cc85-144">la longueur des pétales en centimètres</span><span class="sxs-lookup"><span data-stu-id="4cc85-144">petal length in centimetres</span></span>
- <span data-ttu-id="4cc85-145">la largeur des pétales en centimètres</span><span class="sxs-lookup"><span data-stu-id="4cc85-145">petal width in centimetres</span></span>
- <span data-ttu-id="4cc85-146">le type d’iris</span><span class="sxs-lookup"><span data-stu-id="4cc85-146">type of iris flower</span></span>

<span data-ttu-id="4cc85-147">Dans le cadre de cet exemple de clustering, ce tutoriel ignore la dernière colonne.</span><span class="sxs-lookup"><span data-stu-id="4cc85-147">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="4cc85-148">Créer des classes de données</span><span class="sxs-lookup"><span data-stu-id="4cc85-148">Create data classes</span></span>

<span data-ttu-id="4cc85-149">Créez des classes pour les données d’entrée et les prédictions :</span><span class="sxs-lookup"><span data-stu-id="4cc85-149">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="4cc85-150">Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="4cc85-151">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et définissez la valeur du champ **Nom** sur *IrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="4cc85-151">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="4cc85-152">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-152">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="4cc85-153">Ajoutez la directive `using` suivante au nouveau fichier :</span><span class="sxs-lookup"><span data-stu-id="4cc85-153">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="4cc85-154">Supprimez la définition de classe existante et ajoutez le code suivant, qui définit les classes `IrisData` et `ClusterPrediction`, au fichier *IrisData.cs* :</span><span class="sxs-lookup"><span data-stu-id="4cc85-154">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="4cc85-155">`IrisData` est la classe des données d’entrée et a des définitions pour chaque caractéristique du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="4cc85-155">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="4cc85-156">Utilisez l’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) pour spécifier les index des colonnes sources dans le fichier de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="4cc85-156">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="4cc85-157">La classe `ClusterPrediction` représente la sortie du modèle de clustering appliqué à une instance `IrisData`.</span><span class="sxs-lookup"><span data-stu-id="4cc85-157">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="4cc85-158">Utilisez l’attribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) pour lier les champs `PredictedClusterId` et `Distances` aux colonnes **PredictedLabel** et **Score** respectivement.</span><span class="sxs-lookup"><span data-stu-id="4cc85-158">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="4cc85-159">Dans le cas de la tâche de clustering, ces colonnes ont la signification suivante :</span><span class="sxs-lookup"><span data-stu-id="4cc85-159">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="4cc85-160">La colonne **PredictedLabel** contient l’ID du cluster prédit.</span><span class="sxs-lookup"><span data-stu-id="4cc85-160">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="4cc85-161">La colonne **Score** contient un tableau avec les distances Euclidiennes au carré jusqu’aux centroïdes des clusters.</span><span class="sxs-lookup"><span data-stu-id="4cc85-161">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="4cc85-162">La longueur du tableau est égale au nombre de clusters.</span><span class="sxs-lookup"><span data-stu-id="4cc85-162">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="4cc85-163">Utilisez le type `float` pour représenter les valeurs à virgule flottante dans les classes de données d’entrée et de prédiction.</span><span class="sxs-lookup"><span data-stu-id="4cc85-163">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="4cc85-164">Définir des chemins de données et de modèle</span><span class="sxs-lookup"><span data-stu-id="4cc85-164">Define data and model paths</span></span>

<span data-ttu-id="4cc85-165">Revenez au fichier *Program.cs* et ajoutez deux champs pour contenir les chemins du fichier de jeu de données et du fichier pour enregistrer le modèle :</span><span class="sxs-lookup"><span data-stu-id="4cc85-165">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="4cc85-166">`_dataPath` contient le chemin du fichier avec le jeu de données utilisé pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="4cc85-166">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="4cc85-167">`_modelPath` contient le chemin du fichier où le modèle formé est stocké.</span><span class="sxs-lookup"><span data-stu-id="4cc85-167">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="4cc85-168">Ajoutez le code suivant juste au-dessus de la méthode `Main` pour spécifier ces chemins :</span><span class="sxs-lookup"><span data-stu-id="4cc85-168">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="4cc85-169">Pour compiler le code précédent, ajoutez les directives `using` suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="4cc85-169">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="4cc85-170">Créer un contexte ML</span><span class="sxs-lookup"><span data-stu-id="4cc85-170">Create ML context</span></span>

<span data-ttu-id="4cc85-171">Ajoutez les directives `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="4cc85-171">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="4cc85-172">Dans la méthode `Main`, remplacez la ligne `Console.WriteLine("Hello World!");` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4cc85-172">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="4cc85-173">La classe <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> représente l’environnement Machine Learning et fournit des mécanismes de journalisation et des points d’entrée pour le chargement des données, l’apprentissage du modèle, la prédiction et d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="4cc85-173">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="4cc85-174">Cela s’apparente conceptuellement à l’aide `DbContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4cc85-174">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="4cc85-175">Configurer le chargement des données</span><span class="sxs-lookup"><span data-stu-id="4cc85-175">Setup data loading</span></span>

<span data-ttu-id="4cc85-176">Ajoutez le code suivant à la méthode `Main` pour configurer la façon de charger des données :</span><span class="sxs-lookup"><span data-stu-id="4cc85-176">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

<span data-ttu-id="4cc85-177">La [méthode d’extension générique `MLContext.Data.LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) déduit du type `IrisData` fourni le schéma du jeu de données et retourne <xref:Microsoft.ML.IDataView>, qui peut être utilisé en entrée de transformateurs.</span><span class="sxs-lookup"><span data-stu-id="4cc85-177">The generic [`MLContext.Data.LoadFromTextFile` extension method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) infers the data set schema from the provided `IrisData` type and returns <xref:Microsoft.ML.IDataView> which can be used as input for transformers.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="4cc85-178">Créer un pipeline d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="4cc85-178">Create a learning pipeline</span></span>

<span data-ttu-id="4cc85-179">Pour ce tutoriel, le pipeline d’apprentissage de la tâche de clustering comprend les deux étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="4cc85-179">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="4cc85-180">concaténer des colonnes chargées en une seule colonne **Fonctionnalités**, utilisée par un formateur en clustering ;</span><span class="sxs-lookup"><span data-stu-id="4cc85-180">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="4cc85-181">utiliser un formateur <xref:Microsoft.ML.Trainers.KMeansTrainer> pour former le modèle à l’aide de l’algorithme de clustering k-means++.</span><span class="sxs-lookup"><span data-stu-id="4cc85-181">use a <xref:Microsoft.ML.Trainers.KMeansTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="4cc85-182">Ajoutez le code suivant à la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="4cc85-182">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="4cc85-183">Le code spécifie que le jeu de données doit être divisé en trois clusters.</span><span class="sxs-lookup"><span data-stu-id="4cc85-183">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="4cc85-184">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="4cc85-184">Train the model</span></span>

<span data-ttu-id="4cc85-185">Les étapes ajoutées dans les sections précédentes ont préparé le pipeline pour l’apprentissage, toutefois, aucune n’a été exécutée.</span><span class="sxs-lookup"><span data-stu-id="4cc85-185">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="4cc85-186">Ajoutez la ligne suivante à la méthode `Main` pour effectuer le chargement des données et l’apprentissage du modèle :</span><span class="sxs-lookup"><span data-stu-id="4cc85-186">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="4cc85-187">Enregistrer le modèle</span><span class="sxs-lookup"><span data-stu-id="4cc85-187">Save the model</span></span>

<span data-ttu-id="4cc85-188">À ce stade, vous disposez d’un modèle qui peut être intégré à n’importe laquelle de vos applications .NET existantes ou nouvelles.</span><span class="sxs-lookup"><span data-stu-id="4cc85-188">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="4cc85-189">Pour enregistrer votre modèle dans un fichier .zip, ajoutez le code suivant à la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="4cc85-189">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="4cc85-190">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="4cc85-190">Use the model for predictions</span></span>

<span data-ttu-id="4cc85-191">Pour effectuer des prédictions, utilisez la classe <xref:Microsoft.ML.PredictionEngine%602> qui prend des instances du type d’entrée via le pipeline de transformateur et produit des instances du type de sortie.</span><span class="sxs-lookup"><span data-stu-id="4cc85-191">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="4cc85-192">Ajoutez la ligne suivante à la méthode `Main` pour créer une instance de cette classe :</span><span class="sxs-lookup"><span data-stu-id="4cc85-192">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="4cc85-193">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="4cc85-193">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="4cc85-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="4cc85-194">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="4cc85-195">Il est acceptable d’utiliser dans des environnements à thread unique ou prototype.</span><span class="sxs-lookup"><span data-stu-id="4cc85-195">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="4cc85-196">Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="4cc85-196">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="4cc85-197">Consultez ce guide sur l' [utilisation de `PredictionEnginePool` dans une API Web ASP.net Core](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="4cc85-197">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="4cc85-198">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="4cc85-198">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="4cc85-199">Créez la classe `TestIrisData` qui contiendra les instances de données de test :</span><span class="sxs-lookup"><span data-stu-id="4cc85-199">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="4cc85-200">Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="4cc85-201">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *TestIrisData.cs*.</span><span class="sxs-lookup"><span data-stu-id="4cc85-201">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="4cc85-202">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4cc85-202">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="4cc85-203">Modifiez la classe pour la rendre statique, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="4cc85-203">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="4cc85-204">Ce tutoriel présente une instance de données d’iris au sein de cette classe.</span><span class="sxs-lookup"><span data-stu-id="4cc85-204">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="4cc85-205">Vous pouvez ajouter d’autres scénarios à tester avec le modèle.</span><span class="sxs-lookup"><span data-stu-id="4cc85-205">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="4cc85-206">Ajoutez le code suivant à la classe `TestIrisData` :</span><span class="sxs-lookup"><span data-stu-id="4cc85-206">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="4cc85-207">Pour déterminer à quel cluster l’élément spécifié appartient, revenez au fichier *Program.cs* et ajoutez le code suivant dans la méthode `Main`:</span><span class="sxs-lookup"><span data-stu-id="4cc85-207">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="4cc85-208">Exécutez le programme pour voir quel cluster contient l’instance de données spécifiée et les distances au carré à partir de cette instance jusqu’aux centroïdes des clusters.</span><span class="sxs-lookup"><span data-stu-id="4cc85-208">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="4cc85-209">Vous devriez obtenir les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="4cc85-209">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="4cc85-210">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="4cc85-210">Congratulations!</span></span> <span data-ttu-id="4cc85-211">Vous venez de créer un modèle d’apprentissage automatique de clustering des iris et l’avez utilisé pour réaliser des prédictions.</span><span class="sxs-lookup"><span data-stu-id="4cc85-211">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="4cc85-212">Vous trouverez le code source de ce tutoriel dans le dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering).</span><span class="sxs-lookup"><span data-stu-id="4cc85-212">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4cc85-213">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4cc85-213">Next steps</span></span>

<span data-ttu-id="4cc85-214">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="4cc85-214">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4cc85-215">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="4cc85-215">Understand the problem</span></span>
> - <span data-ttu-id="4cc85-216">Sélectionner la tâche d’apprentissage automatique appropriée</span><span class="sxs-lookup"><span data-stu-id="4cc85-216">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="4cc85-217">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="4cc85-217">Prepare the data</span></span>
> - <span data-ttu-id="4cc85-218">Charger et transformer les données</span><span class="sxs-lookup"><span data-stu-id="4cc85-218">Load and transform the data</span></span>
> - <span data-ttu-id="4cc85-219">Choisir un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="4cc85-219">Choose a learning algorithm</span></span>
> - <span data-ttu-id="4cc85-220">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="4cc85-220">Train the model</span></span>
> - <span data-ttu-id="4cc85-221">Utiliser le modèle pour les prévisions</span><span class="sxs-lookup"><span data-stu-id="4cc85-221">Use the model for predictions</span></span>

<span data-ttu-id="4cc85-222">Consultez notre référentiel GitHub pour continuer l’apprentissage et obtenir d’autres exemples.</span><span class="sxs-lookup"><span data-stu-id="4cc85-222">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4cc85-223">Référentiel GitHub dotnet/machinelearning</span><span class="sxs-lookup"><span data-stu-id="4cc85-223">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
