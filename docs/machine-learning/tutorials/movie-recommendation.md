---
title: 'Tutorial: Construire un lecteur de film - factorisation de matrice'
description: Ce tutoriel explique comment créer un système de suggestion de films à l’aide de ML.NET dans une application console .NET. Les étapes de ce tutoriel utilisent le langage C# et Visual Studio 2019.
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: a221289d0c232863f03a275c26dce835f2878bf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241102"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorization-with-mlnet"></a><span data-ttu-id="d73e6-104">Tutorial: Construire un lecteur de film en utilisant la factorisation de matrice avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="d73e6-104">Tutorial: Build a movie recommender using matrix factorization with ML.NET</span></span>

<span data-ttu-id="d73e6-105">Ce tutoriel explique comment créer un système de suggestion de films à l’aide de ML.NET dans une application console .NET.</span><span class="sxs-lookup"><span data-stu-id="d73e6-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="d73e6-106">Les étapes de ce tutoriel utilisent le langage C# et Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="d73e6-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="d73e6-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="d73e6-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="d73e6-108">Sélectionner un algorithme de machine learning.</span><span class="sxs-lookup"><span data-stu-id="d73e6-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="d73e6-109">Préparer et charger vos données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-109">Prepare and load your data</span></span>
> * <span data-ttu-id="d73e6-110">Créer et entraîner un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-110">Build and train a model</span></span>
> * <span data-ttu-id="d73e6-111">Évaluer un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-111">Evaluate a model</span></span>
> * <span data-ttu-id="d73e6-112">Déployer et consommer un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-112">Deploy and consume a model</span></span>

<span data-ttu-id="d73e6-113">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="d73e6-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="d73e6-114">Flux de travail de l’apprentissage automatique</span><span class="sxs-lookup"><span data-stu-id="d73e6-114">Machine learning workflow</span></span>

<span data-ttu-id="d73e6-115">Vous effectuerez les étapes suivantes pour accomplir votre tâche, ainsi que toute autre tâche ML.NET :</span><span class="sxs-lookup"><span data-stu-id="d73e6-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="d73e6-116">Charger vos données</span><span class="sxs-lookup"><span data-stu-id="d73e6-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="d73e6-117">Créer et entraîner votre modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="d73e6-118">Évaluer votre modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="d73e6-119">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="d73e6-120">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="d73e6-120">Prerequisites</span></span>

* <span data-ttu-id="d73e6-121">[Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec le ".NET Core cross-platform development" charge de travail installé.</span><span class="sxs-lookup"><span data-stu-id="d73e6-121">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="d73e6-122">Sélectionner la tâche d’apprentissage automatique appropriée</span><span class="sxs-lookup"><span data-stu-id="d73e6-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="d73e6-123">Il existe plusieurs façons d’aborder les problèmes de suggestion, par exemple la suggestion d’une liste de films ou d’une liste de produits associés. Dans le cas présent, vous allez prédire l’évaluation (1-5) qu’un utilisateur attribuera à un film spécifique et suggérer ce film si la note est supérieure à un seuil défini (plus l’évaluation est élevée, plus il est probable qu’un utilisateur apprécie un film).</span><span class="sxs-lookup"><span data-stu-id="d73e6-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="d73e6-124">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="d73e6-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="d73e6-125">Création d’un projet</span><span class="sxs-lookup"><span data-stu-id="d73e6-125">Create a project</span></span>

1. <span data-ttu-id="d73e6-126">Ouvrez Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d73e6-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="d73e6-127">Sélectionnez **File** > **New** > **Project** à partir de la barre de menu.</span><span class="sxs-lookup"><span data-stu-id="d73e6-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="d73e6-128">Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="d73e6-129">Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="d73e6-130">Dans la zone de texte **Nom**, tapez « MovieRecommender », puis sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="d73e6-131">Créez un répertoire nommé *Données* dans votre projet pour enregistrer le jeu de données :</span><span class="sxs-lookup"><span data-stu-id="d73e6-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="d73e6-132">Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="d73e6-133">Tapez « Données » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="d73e6-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="d73e6-134">Installez les packages NuGet **Microsoft.ML** et **Microsoft.ML.Recommender** :</span><span class="sxs-lookup"><span data-stu-id="d73e6-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="d73e6-135">Dans **Solution Explorer**, cliquez à droite sur le projet et sélectionnez Manage **NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d73e6-136">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet **Parcourir**, recherchez **Microsoft.ML**, sélectionnez le package dans la liste, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d73e6-137">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="d73e6-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="d73e6-138">Répétez ces étapes pour **Microsoft.ML.Recommender**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="d73e6-139">Ajoutez les instructions `using` suivantes en tête de votre fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="d73e6-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="d73e6-140">Télécharger vos données</span><span class="sxs-lookup"><span data-stu-id="d73e6-140">Download your data</span></span>

1. <span data-ttu-id="d73e6-141">Téléchargez les deux jeux de données et enregistrez-les dans le dossier *Données* que vous avez créé :</span><span class="sxs-lookup"><span data-stu-id="d73e6-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="d73e6-142">Cliquez avec le bouton droit sur [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».</span><span class="sxs-lookup"><span data-stu-id="d73e6-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="d73e6-143">Cliquez avec le bouton droit sur [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) et sélectionnez « Enregistrer le lien (ou la cible) sous... ».</span><span class="sxs-lookup"><span data-stu-id="d73e6-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="d73e6-144">Assurez-vous d’enregistrer \*les fichiers .csv dans le dossier De *données,* ou après l’enregistrer ailleurs, déplacez les \*fichiers .csv vers le dossier De *données.*</span><span class="sxs-lookup"><span data-stu-id="d73e6-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="d73e6-145">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur chacun des fichiers \*.csv, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="d73e6-146">Sous **Advanced**, changer la valeur de **la copie à l’annuaire de sortie** à copier si plus **récent**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![GIF d’un utilisateur sélectionnant la copie si plus récent dans VS.](./media/movie-recommendation/copy-to-output-if-newer.gif)

## <a name="load-your-data"></a><span data-ttu-id="d73e6-148">Charger vos données</span><span class="sxs-lookup"><span data-stu-id="d73e6-148">Load your data</span></span>

<span data-ttu-id="d73e6-149">La première étape du processus ML.NET consiste à préparer et à charger les données d’entraînement et de test de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="d73e6-150">Les données d’évaluation pour les suggestions sont divisées en jeux de données `Train` et `Test`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="d73e6-151">Les données `Train` sont utilisées pour ajuster votre modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="d73e6-152">Les données `Test` sont utilisées pour élaborer des prédictions avec votre modèle entraîné et à évaluer les performances du modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="d73e6-153">Il est courant d’avoir une répartition 80/20 avec les données `Train` et `Test`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="d73e6-154">Voici un aperçu des données de vos fichiers \*.csv :</span><span class="sxs-lookup"><span data-stu-id="d73e6-154">Below is a preview of the data from your \*.csv files:</span></span>

![Capture d’écran de l’aperçu du jeu de données CVS.](./media/movie-recommendation/csv-file-dataset-preview.png)

<span data-ttu-id="d73e6-156">Les fichiers \*.csv comportent quatre colonnes :</span><span class="sxs-lookup"><span data-stu-id="d73e6-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="d73e6-157">En machine learning, les colonnes qui servent à élaborer une prédiction sont appelées [Caractéristiques](../resources/glossary.md#feature), et la colonne contenant la prédiction retournée est appelée [Étiquette](../resources/glossary.md#label).</span><span class="sxs-lookup"><span data-stu-id="d73e6-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="d73e6-158">Puisque vous souhaitez prédire des évaluations de films, c’est la colonne d’évaluation qui est la `Label`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="d73e6-159">Les trois autres colonnes, `userId`, `movieId` et `timestamp`, sont toutes des `Features` utilisées pour prédire la `Label`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="d73e6-160">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d73e6-160">Features</span></span>      | <span data-ttu-id="d73e6-161">Étiquette</span><span class="sxs-lookup"><span data-stu-id="d73e6-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="d73e6-162">C’est à vous de décider quelles `Features` sont utilisées pour prévoir la `Label`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="d73e6-163">Vous pouvez également utiliser des méthodes comme [l’importance de la fonction de permutation](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) pour aider à sélectionner le meilleur `Features`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-163">You can also use methods like [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="d73e6-164">Dans ce cas, vous devez retirer la colonne `timestamp` comme `Feature`, car l’horodatage n’affecte pas vraiment comment un utilisateur évalue un film donné et ne contribue donc pas à la précision de la prédiction :</span><span class="sxs-lookup"><span data-stu-id="d73e6-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="d73e6-165">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d73e6-165">Features</span></span>      | <span data-ttu-id="d73e6-166">Étiquette</span><span class="sxs-lookup"><span data-stu-id="d73e6-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="d73e6-167">Ensuite, vous devez définir votre structure de données pour la classe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d73e6-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="d73e6-168">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="d73e6-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="d73e6-169">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="d73e6-170">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *MovieRatingData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d73e6-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="d73e6-171">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d73e6-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="d73e6-172">Le fichier *MovieRatingData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="d73e6-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d73e6-173">Ajoutez l’instruction `using` suivante en haut de *MovieRatingData.cs* :</span><span class="sxs-lookup"><span data-stu-id="d73e6-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="d73e6-174">Créez une classe nommée `MovieRating` en supprimant la définition de classe existante et en ajoutant le code suivant dans *MovieRatingData.cs* :</span><span class="sxs-lookup"><span data-stu-id="d73e6-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="d73e6-175">`MovieRating` spécifie une classe de données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d73e6-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="d73e6-176">L’attribut [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) spécifie les colonnes (par index de colonne) du jeu de données qui doivent être chargées.</span><span class="sxs-lookup"><span data-stu-id="d73e6-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="d73e6-177">Les colonnes `userId` et `movieId` correspondent à vos `Features` (il s’agit des entrées que vous fournirez au modèle pour prédire la `Label`), et la colonne d’évaluation est la `Label` que vous allez prédire (la sortie du modèle).</span><span class="sxs-lookup"><span data-stu-id="d73e6-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="d73e6-178">Créez une autre classe, `MovieRatingPrediction`, pour représenter les résultats prédits en ajoutant le code suivant après la classe `MovieRating` dans *MovieRatingData.cs* :</span><span class="sxs-lookup"><span data-stu-id="d73e6-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/snippets/machine-learning/MovieRecommendation/csharp/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="d73e6-179">Dans *Program.cs*, remplacez `Console.WriteLine("Hello World!")` par le code suivant dans `Main()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="d73e6-180">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d73e6-181">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d73e6-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="d73e6-182">Après `Main()`, créez une méthode nommée `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="d73e6-183">Cette méthode donne une erreur tant que vous n’avez pas ajouté d’instruction de retour aux étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="d73e6-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="d73e6-184">Initialisez vos variables de chemin de données, chargez les données à partir des fichiers \*.csv, et retournez les données `Train` et `Test` en tant qu’objets `IDataView` en ajoutant la ligne de code suivante dans `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="d73e6-185">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="d73e6-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d73e6-186">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="d73e6-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="d73e6-187">Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="d73e6-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="d73e6-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="d73e6-189">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="d73e6-190">Dans ce cas, fournissez le chemin pour vos fichiers `Test` et `Train`, et indiquez l’en-tête du fichier texte (pour qu’elle puisse utiliser les noms de colonnes correctement) et la virgule de séparation des données caractère (le séparateur par défaut est un onglet).</span><span class="sxs-lookup"><span data-stu-id="d73e6-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="d73e6-191">Ajoutez le code suivant dans la méthode `Main()` pour appeler votre méthode `LoadData()` et retourner les données `Train` et `Test` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="d73e6-192">Créer et entraîner votre modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-192">Build and train your model</span></span>

<span data-ttu-id="d73e6-193">Il existe trois concepts majeurs dans ML.NET: [Données](../resources/glossary.md#data), [Transformateurs](../resources/glossary.md#transformer), et [Estimateurs](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="d73e6-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="d73e6-194">Les algorithmes d’entraînement de machine Learning nécessitent des données dans un certain format.</span><span class="sxs-lookup"><span data-stu-id="d73e6-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="d73e6-195">Les `Transformers` servent à transformer les données tabulaires dans un format compatible.</span><span class="sxs-lookup"><span data-stu-id="d73e6-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![Diagramme du flux de données Transformer.](./media/movie-recommendation/data-transformer-transformed.png)

<span data-ttu-id="d73e6-197">Vous créez des `Transformers` dans ML.NET en créant des `Estimators`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="d73e6-198">Les `Estimators` prennent des données et retournent des `Transformers`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-198">`Estimators` take in data and return `Transformers`.</span></span>

![Diagramme du flux de données de l’estimateur.](./media/movie-recommendation/data-estimator-transformer.png)

<span data-ttu-id="d73e6-200">L’algorithme d’entraînement de suggestion que vous utiliserez pour l’entraînement de votre modèle est un exemple d’`Estimator`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="d73e6-201">Générez un `Estimator` en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d73e6-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="d73e6-202">Créez la méthode `BuildAndTrainModel()` juste après la méthode `LoadData()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d73e6-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="d73e6-203">Cette méthode donne une erreur tant que vous n’avez pas ajouté d’instruction de retour aux étapes suivantes.</span><span class="sxs-lookup"><span data-stu-id="d73e6-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="d73e6-204">Définissez les transformations de données en ajoutant le code suivant à `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="d73e6-205">Étant donné que `userId` et `movieId` représentent des utilisateurs et des titres de films, et non des valeurs réelles, vous utilisez la méthode [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) pour transformer chaque `userId` et chaque `movieId` en colonne `Feature` de type de clé numérique (un format accepté par les algorithmes de suggestion) et vous les ajoutez en tant que nouvelles colonnes de jeu de données :</span><span class="sxs-lookup"><span data-stu-id="d73e6-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="d73e6-206">userId</span><span class="sxs-lookup"><span data-stu-id="d73e6-206">userId</span></span> | <span data-ttu-id="d73e6-207">movieId</span><span class="sxs-lookup"><span data-stu-id="d73e6-207">movieId</span></span> | <span data-ttu-id="d73e6-208">Étiquette</span><span class="sxs-lookup"><span data-stu-id="d73e6-208">Label</span></span> | <span data-ttu-id="d73e6-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="d73e6-209">userIdEncoded</span></span> | <span data-ttu-id="d73e6-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="d73e6-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="d73e6-211">1</span><span class="sxs-lookup"><span data-stu-id="d73e6-211">1</span></span> | <span data-ttu-id="d73e6-212">1</span><span class="sxs-lookup"><span data-stu-id="d73e6-212">1</span></span> | <span data-ttu-id="d73e6-213">4</span><span class="sxs-lookup"><span data-stu-id="d73e6-213">4</span></span> | <span data-ttu-id="d73e6-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="d73e6-214">userKey1</span></span> | <span data-ttu-id="d73e6-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="d73e6-215">movieKey1</span></span> |
| <span data-ttu-id="d73e6-216">1</span><span class="sxs-lookup"><span data-stu-id="d73e6-216">1</span></span> | <span data-ttu-id="d73e6-217">3</span><span class="sxs-lookup"><span data-stu-id="d73e6-217">3</span></span> | <span data-ttu-id="d73e6-218">4</span><span class="sxs-lookup"><span data-stu-id="d73e6-218">4</span></span> | <span data-ttu-id="d73e6-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="d73e6-219">userKey1</span></span> | <span data-ttu-id="d73e6-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="d73e6-220">movieKey2</span></span> |
| <span data-ttu-id="d73e6-221">1</span><span class="sxs-lookup"><span data-stu-id="d73e6-221">1</span></span> | <span data-ttu-id="d73e6-222">6</span><span class="sxs-lookup"><span data-stu-id="d73e6-222">6</span></span> | <span data-ttu-id="d73e6-223">4</span><span class="sxs-lookup"><span data-stu-id="d73e6-223">4</span></span> | <span data-ttu-id="d73e6-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="d73e6-224">userKey1</span></span> | <span data-ttu-id="d73e6-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="d73e6-225">movieKey3</span></span> |

<span data-ttu-id="d73e6-226">Choisissez l’algorithme de machine learning et ajoutez-le aux définitions de transformation de données en ajoutant la ligne de code suivante dans `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="d73e6-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) est votre algorithme d’entraînement de suggestion.</span><span class="sxs-lookup"><span data-stu-id="d73e6-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="d73e6-228">La [factorisation de matrice](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) est une approche courante pour la suggestion quand vous avez des données concernant la façon dont les utilisateurs ont évalué des produits dans le passé, ce qui est le cas pour les jeux de données dans ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="d73e6-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="d73e6-229">Il existe d’autres algorithmes de suggestion adaptés quand vous avez des données différentes (voir la section [Autres algorithmes de suggestion](#other-recommendation-algorithms) ci-dessous pour en savoir plus).</span><span class="sxs-lookup"><span data-stu-id="d73e6-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="d73e6-230">Dans ce cas, l’algorithme `Matrix Factorization` utilise une méthode appelée « filtrage collaboratif », qui part du principe que si l’utilisateur 1 a le même avis que l’utilisateur 2 sur une certaine question, alors l’utilisateur 1 est davantage susceptible d’avoir le même avis que l’utilisateur 2 sur une autre question.</span><span class="sxs-lookup"><span data-stu-id="d73e6-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="d73e6-231">Par exemple, si les utilisateurs 1 et 2 donnent une évaluation similaire à des films, il est plus probable que l’utilisateur 2 appréciera un film que l’utilisateur 1 a vu et auquel il a donné une évaluation élevée :</span><span class="sxs-lookup"><span data-stu-id="d73e6-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="d73e6-232">Utilisateur 1</span><span class="sxs-lookup"><span data-stu-id="d73e6-232">User 1</span></span> | <span data-ttu-id="d73e6-233">A vu et apprécié le film</span><span class="sxs-lookup"><span data-stu-id="d73e6-233">Watched and liked movie</span></span> | <span data-ttu-id="d73e6-234">A vu et apprécié le film</span><span class="sxs-lookup"><span data-stu-id="d73e6-234">Watched and liked movie</span></span> | <span data-ttu-id="d73e6-235">A vu et apprécié le film</span><span class="sxs-lookup"><span data-stu-id="d73e6-235">Watched and liked movie</span></span> |
| <span data-ttu-id="d73e6-236">Utilisateur 2</span><span class="sxs-lookup"><span data-stu-id="d73e6-236">User 2</span></span> | <span data-ttu-id="d73e6-237">A vu et apprécié le film</span><span class="sxs-lookup"><span data-stu-id="d73e6-237">Watched and liked movie</span></span> | <span data-ttu-id="d73e6-238">A vu et apprécié le film</span><span class="sxs-lookup"><span data-stu-id="d73e6-238">Watched and liked movie</span></span> | <span data-ttu-id="d73e6-239">N’a pas vu --SUGGÉRER le film</span><span class="sxs-lookup"><span data-stu-id="d73e6-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="d73e6-240">L’entraîneur de `Matrix Factorization` dispose de plusieurs [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), qui sont détaillées dans la section [Hyperparamètres d’algorithme](#algorithm-hyperparameters) ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d73e6-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="d73e6-241">Ajustez le modèle aux données `Train` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="d73e6-242">La méthode [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle avec le jeu de données d’entraînement fourni.</span><span class="sxs-lookup"><span data-stu-id="d73e6-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="d73e6-243">Techniquement, elle exécute les définitions `Estimator` en transformant les données et en appliquant l’entraînement, puis retourne le modèle entraîné, qui est un `Transformer`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="d73e6-244">Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `BuildAndTrainModel()` et retourner le modèle entraîné :</span><span class="sxs-lookup"><span data-stu-id="d73e6-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="d73e6-245">Évaluer votre modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-245">Evaluate your model</span></span>

<span data-ttu-id="d73e6-246">Une fois que vous avez entraîné votre modèle, utilisez vos données de test pour évaluer ses performances.</span><span class="sxs-lookup"><span data-stu-id="d73e6-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="d73e6-247">Créez la méthode `EvaluateModel()` juste après la méthode `BuildAndTrainModel()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d73e6-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="d73e6-248">Transformez les données `Test` en ajoutant le code suivant à `EvaluateModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="d73e6-249">La méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) établit des prédictions pour plusieurs lignes d’entrée fournies d’un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="d73e6-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="d73e6-250">Évaluez le modèle en ajoutant la ligne de code suivante dans la méthode `EvaluateModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="d73e6-251">Une fois que vous avez le jeu de prédiction, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) évalue le modèle (elle compare les valeurs prédites aux `Labels` réelles dans le jeu de données de test et retourne des métriques relatives aux performances du modèle).</span><span class="sxs-lookup"><span data-stu-id="d73e6-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="d73e6-252">Imprimez vos métriques d’évaluation sur la console en ajoutant la ligne de code suivante dans la méthode `EvaluateModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="d73e6-253">Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `EvaluateModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="d73e6-254">À ce stade, la sortie doit ressembler au texte suivant :</span><span class="sxs-lookup"><span data-stu-id="d73e6-254">The output so far should look similar to the following text:</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

<span data-ttu-id="d73e6-255">Dans cette sortie, il existe 20 itérations.</span><span class="sxs-lookup"><span data-stu-id="d73e6-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="d73e6-256">Dans chaque itération, la mesure d’erreur diminue et converge de plus en plus proche de 0.</span><span class="sxs-lookup"><span data-stu-id="d73e6-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="d73e6-257">La mesure RMSE (`root of mean squared error`) sert à mesurer les différences entre les valeurs prédites par un modèle et les valeurs observées dans un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="d73e6-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="d73e6-258">Techniquement, il s’agit de la racine carrée de la moyenne des carrés des erreurs.</span><span class="sxs-lookup"><span data-stu-id="d73e6-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="d73e6-259">Plus sa valeur est faible, plus le modèle est bon.</span><span class="sxs-lookup"><span data-stu-id="d73e6-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="d73e6-260">`R Squared` indique le niveau d’adéquation des données avec un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="d73e6-261">Cette valeur est comprise entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="d73e6-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="d73e6-262">Une valeur de 0 signifie que les données sont aléatoires ou ne s’intègrent pas au modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="d73e6-263">Une valeur de 1 signifie que le modèle correspond exactement aux données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="d73e6-264">Il faut que le score `R Squared` soit le plus proche possible de 1.</span><span class="sxs-lookup"><span data-stu-id="d73e6-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="d73e6-265">La création de modèles efficaces est un processus itératif.</span><span class="sxs-lookup"><span data-stu-id="d73e6-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="d73e6-266">Celui-ci présente une qualité initiale médiocre, car le tutoriel utilise de petits jeux de données pour permettre un apprentissage rapide du modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="d73e6-267">Si vous n’êtes pas satisfait de la qualité du modèle, vous pouvez essayer de l’améliorer en fournissant de plus gros jeux de données d’apprentissage ou en choisissant d’autres algorithmes d’apprentissage avec différents hyperparamètres pour chacun.</span><span class="sxs-lookup"><span data-stu-id="d73e6-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="d73e6-268">Pour plus d’informations, voir la section [Améliorer le modèle](#improve-your-model) ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="d73e6-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="d73e6-269">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-269">Use your model</span></span>

<span data-ttu-id="d73e6-270">Vous pouvez maintenant utiliser votre modèle entraîné pour établir des prédictions sur de nouvelles données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="d73e6-271">Créez la méthode `UseModelForSinglePrediction()` juste après la méthode `EvaluateModel()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d73e6-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="d73e6-272">Utilisez le `PredictionEngine` pour prédire l’évaluation en ajoutant le code suivant à `UseModelForSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="d73e6-273">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="d73e6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas sans fil.</span><span class="sxs-lookup"><span data-stu-id="d73e6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="d73e6-275">Il est acceptable d’utiliser dans des environnements à thread unique ou prototype.</span><span class="sxs-lookup"><span data-stu-id="d73e6-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="d73e6-276">Pour améliorer les performances et la `PredictionEnginePool` sécurité des fils [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans les environnements de production, utilisez le service, qui crée un des objets à utiliser dans toute votre application.</span><span class="sxs-lookup"><span data-stu-id="d73e6-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="d73e6-277">Voir ce guide sur la façon [d’utiliser `PredictionEnginePool` dans un ASP.NET’API Web de base](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="d73e6-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="d73e6-278">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="d73e6-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="d73e6-279">Créez une instance de `MovieRating` nommée `testInput` et transmettez-la au moteur de prédiction en ajoutant les lignes de code suivantes dans la méthode `UseModelForSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="d73e6-280">La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) établit une prédiction sur une seule colonne de données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="d73e6-281">Vous pouvez ensuite utiliser le `Score`, ou évaluation prédite, pour déterminer si vous souhaitez suggérer le film avec movieId 10 à l’utilisateur 6.</span><span class="sxs-lookup"><span data-stu-id="d73e6-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="d73e6-282">Plus `Score` est élevé, plus il est probable qu’un utilisateur appréciera un film donné.</span><span class="sxs-lookup"><span data-stu-id="d73e6-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="d73e6-283">Dans le cas présent, supposez que vous recommandez des films avec une évaluation prédite supérieure à 3,5.</span><span class="sxs-lookup"><span data-stu-id="d73e6-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="d73e6-284">Pour afficher les résultats, ajoutez les lignes de code suivantes dans la méthode `UseModelForSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="d73e6-285">Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `UseModelForSinglePrediction()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="d73e6-286">La sortie de cette méthode doit ressembler au texte suivant :</span><span class="sxs-lookup"><span data-stu-id="d73e6-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="d73e6-287">Enregistrez votre modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-287">Save your model</span></span>

<span data-ttu-id="d73e6-288">Pour utiliser votre modèle afin d’établir des prédictions dans des applications pour utilisateur final, vous devez d’abord enregistrer le modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="d73e6-289">Créez la méthode `SaveModel()` juste après la méthode `UseModelForSinglePrediction()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d73e6-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="d73e6-290">Enregistrez votre modèle entraîné en ajoutant le code suivant dans la méthode `SaveModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="d73e6-291">Cette méthode enregistre votre modèle entraîné dans un fichier .zip (dans le dossier « Données »), qui peut ensuite être utilisé dans d’autres applications .NET pour établir des prédictions.</span><span class="sxs-lookup"><span data-stu-id="d73e6-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="d73e6-292">Ajoutez la ligne de code suivante dans la méthode `Main()` pour appeler votre méthode `SaveModel()` :</span><span class="sxs-lookup"><span data-stu-id="d73e6-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/snippets/machine-learning/MovieRecommendation/csharp/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="d73e6-293">Utiliser le modèle enregistré</span><span class="sxs-lookup"><span data-stu-id="d73e6-293">Use your saved model</span></span>

<span data-ttu-id="d73e6-294">Une fois que vous avez enregistré votre modèle qualifié, vous pouvez consommer le modèle dans différents environnements.</span><span class="sxs-lookup"><span data-stu-id="d73e6-294">Once you have saved your trained model, you can consume the model in different environments.</span></span> <span data-ttu-id="d73e6-295">Consultez [Save et chargez des modèles formés](../how-to-guides/save-load-machine-learning-models-ml-net.md) pour apprendre à mettre en service un modèle d’apprentissage automatique formé dans les applications.</span><span class="sxs-lookup"><span data-stu-id="d73e6-295">See [Save and load trained models](../how-to-guides/save-load-machine-learning-models-ml-net.md) to learn how to operationalize a trained machine learning model in apps.</span></span>

## <a name="results"></a><span data-ttu-id="d73e6-296">Résultats</span><span class="sxs-lookup"><span data-stu-id="d73e6-296">Results</span></span>

<span data-ttu-id="d73e6-297">Après avoir effectué les étapes ci-dessus, exécutez votre application console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="d73e6-297">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="d73e6-298">Les résultats de la prédiction unique ci-dessus doivent ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="d73e6-298">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="d73e6-299">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="d73e6-299">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

<span data-ttu-id="d73e6-300">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="d73e6-300">Congratulations!</span></span> <span data-ttu-id="d73e6-301">Vous avez réussi à créer un modèle Machine Learning pour la suggestion de films.</span><span class="sxs-lookup"><span data-stu-id="d73e6-301">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="d73e6-302">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation).</span><span class="sxs-lookup"><span data-stu-id="d73e6-302">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="d73e6-303">Améliorer votre modèle</span><span class="sxs-lookup"><span data-stu-id="d73e6-303">Improve your model</span></span>

<span data-ttu-id="d73e6-304">Il existe plusieurs façons d’améliorer les performances du modèle afin d’obtenir des prédictions plus précises.</span><span class="sxs-lookup"><span data-stu-id="d73e6-304">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="d73e6-305">Données</span><span class="sxs-lookup"><span data-stu-id="d73e6-305">Data</span></span>

<span data-ttu-id="d73e6-306">L’ajout de données d’entraînement comportant suffisamment d’échantillons pour chaque utilisateur et ID de film peut aider à améliorer la qualité du modèle de suggestion.</span><span class="sxs-lookup"><span data-stu-id="d73e6-306">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="d73e6-307">La [validation croisée](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) est une technique d’évaluation des modèles qui fractionne aléatoirement les données en sous-ensembles (au lieu d’extraire des données de test à partir du jeu de données comme vous l’avez fait dans ce tutoriel) et prend certains groupes comme données d’entraînement et certains autres comme données de test.</span><span class="sxs-lookup"><span data-stu-id="d73e6-307">[Cross validation](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="d73e6-308">En termes de qualité du modèle, cette méthode est supérieure à un fractionnement entraînement-test.</span><span class="sxs-lookup"><span data-stu-id="d73e6-308">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="d73e6-309">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="d73e6-309">Features</span></span>

<span data-ttu-id="d73e6-310">Dans ce tutoriel, vous utilisez uniquement les trois `Features` (`user id`, `movie id` et `rating`) qui sont fournies par le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-310">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="d73e6-311">Même si c’est un bon point de départ, en réalité vous souhaiterez sans doute ajouter d’autres attributs ou `Features` (par exemple l’âge, le sexe, l’emplacement géographique et ainsi de suite) s’ils sont inclus dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-311">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="d73e6-312">L’ajout de `Features` plus pertinentes peut aider à améliorer les performances de votre modèle de suggestion.</span><span class="sxs-lookup"><span data-stu-id="d73e6-312">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="d73e6-313">Si vous n’êtes pas sûr de savoir qui `Features` pourrait être le plus pertinent pour votre tâche d’apprentissage automatique, vous pouvez également faire usage de calcul de la contribution des fonctionnalités (FCC) et [l’importance caractéristique de permutation](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), qui ML.NET fournit de découvrir le plus influent `Features`.</span><span class="sxs-lookup"><span data-stu-id="d73e6-313">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [permutation feature importance](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="d73e6-314">Hyperparamètres d’algorithme</span><span class="sxs-lookup"><span data-stu-id="d73e6-314">Algorithm hyperparameters</span></span>

<span data-ttu-id="d73e6-315">Bien que ML.NET fournisse de bons algorithmes d’entraînement par défaut, vous pouvez optimiser les performances en changeant les [hyperparamètres](../resources/glossary.md#hyperparameter) d’algorithme.</span><span class="sxs-lookup"><span data-stu-id="d73e6-315">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="d73e6-316">Pour la `Matrix Factorization`, vous pouvez expérimenter avec des hyperparamètres comme [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) et [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) pour voir si cela donne de meilleurs résultats.</span><span class="sxs-lookup"><span data-stu-id="d73e6-316">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="d73e6-317">Par exemple, dans ce tutoriel, les options d’algorithme sont :</span><span class="sxs-lookup"><span data-stu-id="d73e6-317">For instance, in this tutorial the algorithm options are:</span></span>

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="d73e6-318">Autres algorithmes de suggestion</span><span class="sxs-lookup"><span data-stu-id="d73e6-318">Other Recommendation Algorithms</span></span>

<span data-ttu-id="d73e6-319">L’algorithme de factorisation de matrice avec filtrage collaboratif n’est qu’une approche parmi d’autres pour effectuer des suggestions de films.</span><span class="sxs-lookup"><span data-stu-id="d73e6-319">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="d73e6-320">Dans de nombreux cas, vous ne disposerez peut-être pas des données d’évaluation et aurez uniquement l’historique des films des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="d73e6-320">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="d73e6-321">Dans d’autres cas, vous aurez peut-être davantage que juste les données d’évaluation de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d73e6-321">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="d73e6-322">Algorithm</span><span class="sxs-lookup"><span data-stu-id="d73e6-322">Algorithm</span></span>       | <span data-ttu-id="d73e6-323">Scénario</span><span class="sxs-lookup"><span data-stu-id="d73e6-323">Scenario</span></span>           | <span data-ttu-id="d73e6-324">Exemple</span><span class="sxs-lookup"><span data-stu-id="d73e6-324">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="d73e6-325">Factorisation de matrice à une classe</span><span class="sxs-lookup"><span data-stu-id="d73e6-325">One Class Matrix Factorization</span></span> | <span data-ttu-id="d73e6-326">Utilisez-la quand vous avez uniquement userId et movieId.</span><span class="sxs-lookup"><span data-stu-id="d73e6-326">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="d73e6-327">Ce style de suggestion est basé sur le scénario de coachat (ou produits fréquemment achetés ensemble), ce qui signifie qu’il suggérera aux clients un ensemble de produits en fonction de leur propre historique de commandes.</span><span class="sxs-lookup"><span data-stu-id="d73e6-327">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="d73e6-328">>Essayez-le</span><span class="sxs-lookup"><span data-stu-id="d73e6-328">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="d73e6-329">Machines de factorisation prenant en charge les champs</span><span class="sxs-lookup"><span data-stu-id="d73e6-329">Field Aware Factorization Machines</span></span> | <span data-ttu-id="d73e6-330">Elles permettent d’effectuer des suggestions quand vous disposez d’autres caractéristiques en plus de userId, productId et rating (par exemple la description du produit ou le prix du produit).</span><span class="sxs-lookup"><span data-stu-id="d73e6-330">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="d73e6-331">Cette méthode adopte également une approche avec filtrage collaboratif.</span><span class="sxs-lookup"><span data-stu-id="d73e6-331">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="d73e6-332">>Essayez-le</span><span class="sxs-lookup"><span data-stu-id="d73e6-332">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="d73e6-333">Scénario avec nouvel utilisateur</span><span class="sxs-lookup"><span data-stu-id="d73e6-333">New user scenario</span></span>

<span data-ttu-id="d73e6-334">L’un des problèmes courants dans le filtrage collaboratif est le problème de démarrage à froid, c’est-à-dire quand vous avez un nouvel utilisateur sans données à partir desquelles tirer des inférences.</span><span class="sxs-lookup"><span data-stu-id="d73e6-334">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="d73e6-335">Pour le résoudre, il suffit souvent de demander aux nouveaux utilisateurs de créer un profil et, par exemple, d’évaluer les films qu’ils ont déjà vus.</span><span class="sxs-lookup"><span data-stu-id="d73e6-335">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="d73e6-336">Même si cette méthode met un poids sur l’utilisateur, elle fournit certaines données de départ pour les nouveaux utilisateurs sans aucun historique d’évaluation.</span><span class="sxs-lookup"><span data-stu-id="d73e6-336">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="d73e6-337">Ressources</span><span class="sxs-lookup"><span data-stu-id="d73e6-337">Resources</span></span>

<span data-ttu-id="d73e6-338">Les données utilisées dans ce tutoriel sont dérivées du [Jeu de données MovieLens](http://files.grouplens.org/datasets/movielens/).</span><span class="sxs-lookup"><span data-stu-id="d73e6-338">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d73e6-339">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d73e6-339">Next steps</span></span>

<span data-ttu-id="d73e6-340">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="d73e6-340">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d73e6-341">Sélectionner un algorithme de machine learning.</span><span class="sxs-lookup"><span data-stu-id="d73e6-341">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="d73e6-342">Préparer et charger vos données.</span><span class="sxs-lookup"><span data-stu-id="d73e6-342">Prepare and load your data</span></span>
> * <span data-ttu-id="d73e6-343">Créer et entraîner un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-343">Build and train a model</span></span>
> * <span data-ttu-id="d73e6-344">Évaluer un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-344">Evaluate a model</span></span>
> * <span data-ttu-id="d73e6-345">Déployer et consommer un modèle.</span><span class="sxs-lookup"><span data-stu-id="d73e6-345">Deploy and consume a model</span></span>

<span data-ttu-id="d73e6-346">Passer au tutoriel suivant pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="d73e6-346">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d73e6-347">Analyse des sentiments</span><span class="sxs-lookup"><span data-stu-id="d73e6-347">Sentiment Analysis</span></span>](sentiment-analysis.md)
