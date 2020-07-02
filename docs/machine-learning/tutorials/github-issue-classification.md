---
title: 'Didacticiel : classer les problèmes de support technique-Classification multiclasse'
description: Découvrez comment utiliser ML.NET dans un scénario de classification multiclasse pour classer des problèmes GitHub et les affecter à une zone donnée.
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: 5233924dab063fd1ba0232672613f9701f637385
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803727"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-mlnet"></a><span data-ttu-id="867c4-103">Didacticiel : classer les problèmes de prise en charge à l’aide de la classification multiclasse avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="867c4-103">Tutorial: Categorize support issues using multiclass classification with ML.NET</span></span>

<span data-ttu-id="867c4-104">Ce tutoriel montre comment utiliser ML.NET pour créer un classifieur de problèmes GitHub afin d’entraîner un modèle qui classe et prédit l’étiquette Area d’un problème GitHub par le biais d’une application console .NET Core en C# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="867c4-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="867c4-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="867c4-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="867c4-106">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="867c4-106">Prepare your data</span></span>
> * <span data-ttu-id="867c4-107">Transformer les données</span><span class="sxs-lookup"><span data-stu-id="867c4-107">Transform the data</span></span>
> * <span data-ttu-id="867c4-108">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-108">Train the model</span></span>
> * <span data-ttu-id="867c4-109">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-109">Evaluate the model</span></span>
> * <span data-ttu-id="867c4-110">Prédire avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="867c4-110">Predict with the trained model</span></span>
> * <span data-ttu-id="867c4-111">Déployer et prédire avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="867c4-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="867c4-112">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="867c4-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="867c4-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="867c4-113">Prerequisites</span></span>

* <span data-ttu-id="867c4-114">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="867c4-114">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>
* <span data-ttu-id="867c4-115">Le [fichier séparé par des onglets de problèmes GitHub (issues_train. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span><span class="sxs-lookup"><span data-stu-id="867c4-115">The [GitHub issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="867c4-116">Le [fichier séparé par onglets de test GitHub (issues_test. TSV)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span><span class="sxs-lookup"><span data-stu-id="867c4-116">The [GitHub issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="867c4-117">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="867c4-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="867c4-118">Création d’un projet</span><span class="sxs-lookup"><span data-stu-id="867c4-118">Create a project</span></span>

1. <span data-ttu-id="867c4-119">Ouvrez Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="867c4-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="867c4-120">Sélectionnez **fichier**  >  **nouveau**  >  **projet** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="867c4-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="867c4-121">Dans la boîte de dialogue **Nouveau projet**, sélectionnez le nœud **Visual C#** suivi du nœud **.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="867c4-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="867c4-122">Ensuite, sélectionnez le modèle de projet **Application console (.NET Core)**.</span><span class="sxs-lookup"><span data-stu-id="867c4-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="867c4-123">Dans la zone de texte **Nom**, tapez « GitHubIssueClassification », puis cliquez sur le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="867c4-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="867c4-124">Créez un répertoire nommé *Données* dans votre projet pour enregistrer vos fichiers de jeu de données :</span><span class="sxs-lookup"><span data-stu-id="867c4-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="867c4-125">Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="867c4-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="867c4-126">Tapez « Données » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="867c4-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="867c4-127">Créez un répertoire nommé *Models* dans votre projet pour enregistrer votre modèle :</span><span class="sxs-lookup"><span data-stu-id="867c4-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="867c4-128">Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="867c4-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="867c4-129">Tapez « Models » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="867c4-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="867c4-130">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="867c4-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="867c4-131">Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="867c4-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="867c4-132">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ml** , puis sélectionnez le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="867c4-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="867c4-133">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="867c4-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="867c4-134">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="867c4-134">Prepare your data</span></span>

1. <span data-ttu-id="867c4-135">Téléchargez les jeux de données [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) et [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv), puis enregistrez-les dans le dossier *Données* créé précédemment.</span><span class="sxs-lookup"><span data-stu-id="867c4-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="867c4-136">Le premier jeu de données effectue l’apprentissage automatique du modèle, et le second peut servir à évaluer la précision de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="867c4-137">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur chacun des fichiers \*.tsv, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="867c4-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="867c4-138">Sous **avancé**, remplacez la valeur de **copier dans le répertoire de sortie** par **copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="867c4-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="867c4-139">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="867c4-139">Create classes and define paths</span></span>

<span data-ttu-id="867c4-140">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* : </span><span class="sxs-lookup"><span data-stu-id="867c4-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddUsings)]

<span data-ttu-id="867c4-141">Créez trois champs globaux pour accueillir les chemins des fichiers récemment téléchargés, puis des variables globales pour `MLContext`, `DataView` et `PredictionEngine` :</span><span class="sxs-lookup"><span data-stu-id="867c4-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="867c4-142">`_trainDataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="867c4-143">`_testDataPath` contient le chemin d’accès au jeu de données utilisé pour évaluer le modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="867c4-144">`_modelPath` contient le chemin d’accès où le modèle formé est enregistré.</span><span class="sxs-lookup"><span data-stu-id="867c4-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="867c4-145">`_mlContext` est le <xref:Microsoft.ML.MLContext> qui fournit le contexte de traitement.</span><span class="sxs-lookup"><span data-stu-id="867c4-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="867c4-146">`_trainingDataView` est le <xref:Microsoft.ML.IDataView> utilisé pour traiter le jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="867c4-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="867c4-147">`_predEngine` est le <xref:Microsoft.ML.PredictionEngine%602> utilisé pour des prédictions uniques.</span><span class="sxs-lookup"><span data-stu-id="867c4-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="867c4-148">Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins et les autres variables :</span><span class="sxs-lookup"><span data-stu-id="867c4-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="867c4-149">Créez des classes pour vos données d’entrée et vos prévisions.</span><span class="sxs-lookup"><span data-stu-id="867c4-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="867c4-150">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="867c4-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="867c4-151">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="867c4-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="867c4-152">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *GitHubIssueData.cs*.</span><span class="sxs-lookup"><span data-stu-id="867c4-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="867c4-153">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="867c4-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="867c4-154">Le fichier *GitHubIssueData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="867c4-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="867c4-155">Ajoutez l’instruction `using` suivante en haut de *GitHubIssueData.cs* :</span><span class="sxs-lookup"><span data-stu-id="867c4-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="867c4-156">Supprimez la définition de classe existante et ajoutez le code suivant, lequel contient deux classes (`GitHubIssue` et `IssuePrediction`), au fichier *GitHubIssueData.cs* :</span><span class="sxs-lookup"><span data-stu-id="867c4-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="867c4-157">`label` est la colonne à prédire.</span><span class="sxs-lookup"><span data-stu-id="867c4-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="867c4-158">Les valeurs `Features` identifiées sont les entrées que vous fournissez au modèle pour prédire l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="867c4-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="867c4-159">Utilisez [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) pour spécifier les index des colonnes sources dans le jeu de données.</span><span class="sxs-lookup"><span data-stu-id="867c4-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="867c4-160">`GitHubIssue`, la classe de jeu de données d’entrée, comprend les champs <xref:System.String> suivants :</span><span class="sxs-lookup"><span data-stu-id="867c4-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="867c4-161">La première colonne `ID` est l’ID du problème GitHub.</span><span class="sxs-lookup"><span data-stu-id="867c4-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="867c4-162">La deuxième colonne `Area` est la prédiction pour l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="867c4-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="867c4-163">La troisième colonne `Title` (titre du problème GitHub) est la première caractéristique (`feature`) utilisée pour prédire l’étiquette `Area`</span><span class="sxs-lookup"><span data-stu-id="867c4-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="867c4-164">La quatrième colonne `Description` est la deuxième caractéristique (`feature`) utilisée pour prédire `Area`</span><span class="sxs-lookup"><span data-stu-id="867c4-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="867c4-165">`IssuePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="867c4-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="867c4-166">Il possède un `string` attribut unique ( `Area` ) et un `PredictedLabel` `ColumnName` attribut.</span><span class="sxs-lookup"><span data-stu-id="867c4-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="867c4-167">L’attribut `PredictedLabel` est utilisé pendant la prédiction et l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="867c4-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="867c4-168">L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="867c4-169">Toutes les opérations ML.NET démarrent dans la classe [MLContext](xref:Microsoft.ML.MLContext) .</span><span class="sxs-lookup"><span data-stu-id="867c4-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="867c4-170">L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="867c4-171">Sur le plan conceptuel, cette classe est similaire à `DBContext` dans `Entity Framework`.</span><span class="sxs-lookup"><span data-stu-id="867c4-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="867c4-172">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="867c4-172">Initialize variables in Main</span></span>

<span data-ttu-id="867c4-173">Initialisez la variable globale `_mlContext` à l’aide d’une nouvelle instance de `MLContext` avec une valeur de départ aléatoire (`seed: 0`) pour obtenir des résultats reproductibles/déterministes dans différents entraînements.</span><span class="sxs-lookup"><span data-stu-id="867c4-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="867c4-174">Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="867c4-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="867c4-175">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="867c4-175">Load the data</span></span>

<span data-ttu-id="867c4-176">ML.NET utilise la [classe IDataView](xref:Microsoft.ML.IDataView) comme un moyen flexible et efficace de décrire des données tabulaires au format numérique ou texte.</span><span class="sxs-lookup"><span data-stu-id="867c4-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="867c4-177">`IDataView` peut charger des fichiers texte ou en temps réel (par exemple, une base de données SQL ou des fichiers journaux).</span><span class="sxs-lookup"><span data-stu-id="867c4-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="867c4-178">Pour initialiser et charger la variable globale `_trainingDataView` afin de l’utiliser pour le pipeline, ajoutez le code suivant après l’initialisation de `mlContext` :</span><span class="sxs-lookup"><span data-stu-id="867c4-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTrainData)]

<span data-ttu-id="867c4-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="867c4-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="867c4-180">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="867c4-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="867c4-181">Ajoutez le code suivant comme prochaine ligne dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="867c4-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallProcessData)]

<span data-ttu-id="867c4-182">La méthode `ProcessData` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="867c4-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="867c4-183">Extrait et transforme les données.</span><span class="sxs-lookup"><span data-stu-id="867c4-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="867c4-184">Retourne le pipeline de traitement.</span><span class="sxs-lookup"><span data-stu-id="867c4-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="867c4-185">Créez la méthode `ProcessData` juste après la méthode `Main`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="867c4-186">Extraire des caractéristiques et transformer les données</span><span class="sxs-lookup"><span data-stu-id="867c4-186">Extract Features and transform the data</span></span>

<span data-ttu-id="867c4-187">Pour prédire l’étiquette Area GitHub pour un `GitHubIssue`, utilisez la méthode [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) afin de transformer la colonne `Area` en une colonne `Label` de type clé numérique (un format accepté par les algorithmes de classification) et ajoutez-la comme nouvelle colonne au jeu de données :</span><span class="sxs-lookup"><span data-stu-id="867c4-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#MapValueToKey)]

<span data-ttu-id="867c4-188">Appelez ensuite `mlContext.Transforms.Text.FeaturizeText` , qui transforme les colonnes text ( `Title` et `Description` ) en un vecteur numérique pour chaque appelé `TitleFeaturized` et `DescriptionFeaturized` .</span><span class="sxs-lookup"><span data-stu-id="867c4-188">Next, call `mlContext.Transforms.Text.FeaturizeText`, which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="867c4-189">Utilisez le code suivant pour ajouter la caractérisation des deux colonnes au pipeline :</span><span class="sxs-lookup"><span data-stu-id="867c4-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#FeaturizeText)]

<span data-ttu-id="867c4-190">La dernière étape de préparation des données consiste à combiner toutes les colonnes de caractéristiques dans la colonne **Features** à l’aide de la méthode [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A).</span><span class="sxs-lookup"><span data-stu-id="867c4-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="867c4-191">Par défaut, un algorithme d’apprentissage traite uniquement les caractéristiques issues de la colonne **Features**.</span><span class="sxs-lookup"><span data-stu-id="867c4-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="867c4-192">Utilisez le code suivant pour ajouter cette transformation au pipeline :</span><span class="sxs-lookup"><span data-stu-id="867c4-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Concatenate)]

 <span data-ttu-id="867c4-193">Ajoutez ensuite un <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> pour mettre en cache le DataView. Ainsi, quand vous itérerez plusieurs fois sur les données, l’utilisation du cache vous fera peut-être gagner en performances, à l’instar du code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="867c4-194">Utilisez AppendCacheCheckpoint pour les jeux de données petits/moyens afin de réduire le temps d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="867c4-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="867c4-195">Ne l’utilisez PAS (supprimez .AppendCacheCheckpoint()) lors du traitement de jeux de données très volumineux.</span><span class="sxs-lookup"><span data-stu-id="867c4-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="867c4-196">Retournez le pipeline à la fin de la méthode `ProcessData`.</span><span class="sxs-lookup"><span data-stu-id="867c4-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnPipeline)]

<span data-ttu-id="867c4-197">Cette étape gère le prétraitement/la caractérisation.</span><span class="sxs-lookup"><span data-stu-id="867c4-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="867c4-198">L’utilisation des composants supplémentaires disponibles dans ML.NET peut améliorer les résultats de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="867c4-199">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-199">Build and train the model</span></span>

<span data-ttu-id="867c4-200">Ajoutez l’appel suivant à la méthode `BuildAndTrainModel` comme prochaine ligne de code dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="867c4-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="867c4-201">La méthode `BuildAndTrainModel` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="867c4-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="867c4-202">Crée la classe d’algorithme d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="867c4-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="867c4-203">Effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-203">Trains the model.</span></span>
* <span data-ttu-id="867c4-204">Prédit la zone en fonction des données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="867c4-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="867c4-205">Retourne le modèle.</span><span class="sxs-lookup"><span data-stu-id="867c4-205">Returns the model.</span></span>

<span data-ttu-id="867c4-206">Créez la méthode `BuildAndTrainModel` juste après la méthode `Main`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="867c4-207">À propos de la tâche de classification</span><span class="sxs-lookup"><span data-stu-id="867c4-207">About the classification task</span></span>

<span data-ttu-id="867c4-208">La classification est une tâche de machine learning qui utilise des données pour **déterminer** la catégorie, le type ou la classe d’un élément ou d’une ligne de données. Cette tâche est souvent d’un de ces types :</span><span class="sxs-lookup"><span data-stu-id="867c4-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="867c4-209">Binaire : A ou B.</span><span class="sxs-lookup"><span data-stu-id="867c4-209">Binary: either A or B.</span></span>
* <span data-ttu-id="867c4-210">Multiclasse : plusieurs catégories pouvant être prédites à l’aide d’un modèle unique.</span><span class="sxs-lookup"><span data-stu-id="867c4-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="867c4-211">Pour ce type de problème, utilisez un algorithme de machine learning de classification multiclasse, dans la mesure où votre prédiction de catégorie de problème peut appartenir à une catégorie parmi plusieurs possibles (multiclasse) plutôt qu’à une catégorie parmi deux possibles (binaire).</span><span class="sxs-lookup"><span data-stu-id="867c4-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="867c4-212">Ajoutez l’algorithme de machine learning aux définitions de transformation de données en ajoutant la première ligne de code suivante dans `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="867c4-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTrainer)]

<span data-ttu-id="867c4-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) est l’algorithme de machine learning de classification multiclasse.</span><span class="sxs-lookup"><span data-stu-id="867c4-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="867c4-214">Il est ajouté à `pipeline` et accepte les caractéristiques `Title` et `Description` (`Features`) ainsi que les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.</span><span class="sxs-lookup"><span data-stu-id="867c4-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="867c4-215">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-215">Train the model</span></span>

<span data-ttu-id="867c4-216">Ajustez le modèle aux données `splitTrainSet` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="867c4-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#TrainModel)]

<span data-ttu-id="867c4-217">La méthode `Fit()` entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="867c4-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="867c4-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API utile qui vous permet de passer et d’exécuter une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="867c4-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="867c4-219">Ajoutez ce contenu à la ligne suivante dans la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="867c4-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="867c4-220">Prédire avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="867c4-220">Predict with the trained model</span></span>

<span data-ttu-id="867c4-221">Ajoutez un problème GitHub pour tester la prédiction du modèle entraîné dans la méthode `Predict` en créant une instance de `GitHubIssue` :</span><span class="sxs-lookup"><span data-stu-id="867c4-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreateTestIssue1)]

<span data-ttu-id="867c4-222">Utilisez la fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) pour effectuer une prédiction sur une seule ligne de données :</span><span class="sxs-lookup"><span data-stu-id="867c4-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="867c4-223">Utilisation des résultats du modèle : prédiction</span><span class="sxs-lookup"><span data-stu-id="867c4-223">Using the model: prediction results</span></span>

<span data-ttu-id="867c4-224">Affichez `GitHubIssue` et la prédiction d’étiquette `Area` correspondante pour partager les résultats et prendre les mesures nécessaires.</span><span class="sxs-lookup"><span data-stu-id="867c4-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="867c4-225">Créez une vue des résultats à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="867c4-226">Retourner le modèle entraîné à utiliser pour l’évaluation</span><span class="sxs-lookup"><span data-stu-id="867c4-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="867c4-227">Retournez le modèle à la fin de la méthode `BuildAndTrainModel`.</span><span class="sxs-lookup"><span data-stu-id="867c4-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="867c4-228">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-228">Evaluate the model</span></span>

<span data-ttu-id="867c4-229">Maintenant que vous avez créé et effectué l’apprentissage du modèle, vous devez l’évaluer avec un jeu de données différent à des fins d’assurance qualité et de validation.</span><span class="sxs-lookup"><span data-stu-id="867c4-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="867c4-230">Dans la méthode `Evaluate`, le modèle créé dans `BuildAndTrainModel` est passé pour évaluation.</span><span class="sxs-lookup"><span data-stu-id="867c4-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="867c4-231">Créez la méthode `Evaluate` juste après `BuildAndTrainModel`, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="867c4-232">La méthode `Evaluate` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="867c4-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="867c4-233">Charge le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="867c4-233">Loads the test dataset.</span></span>
* <span data-ttu-id="867c4-234">Crée l’évaluateur multiclasse.</span><span class="sxs-lookup"><span data-stu-id="867c4-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="867c4-235">Évalue le modèle et crée des métriques.</span><span class="sxs-lookup"><span data-stu-id="867c4-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="867c4-236">Affiche les métriques.</span><span class="sxs-lookup"><span data-stu-id="867c4-236">Displays the metrics.</span></span>

<span data-ttu-id="867c4-237">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `BuildAndTrainModel`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallEvaluate)]

<span data-ttu-id="867c4-238">Comme vous l’avez fait précédemment avec le jeu de données d’entraînement, chargez le jeu de données de test en ajoutant le code suivant à la méthode `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="867c4-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#LoadTestDataset)]

<span data-ttu-id="867c4-239">La méthode [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) calcule les métriques de qualité pour le modèle à l’aide du jeu de données spécifié.</span><span class="sxs-lookup"><span data-stu-id="867c4-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="867c4-240">Elle retourne un objet <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> contenant les métriques globales calculées par les évaluateurs de classification multiclasse.</span><span class="sxs-lookup"><span data-stu-id="867c4-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="867c4-241">Pour afficher les métriques permettant de déterminer la qualité du modèle, vous devez d’abord les obtenir.</span><span class="sxs-lookup"><span data-stu-id="867c4-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="867c4-242">Notez l’utilisation de la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) de la variable globale de machine learning `_trainedModel` (un [ITransformer](xref:Microsoft.ML.ITransformer)) pour entrer les caractéristiques et retourner les prédictions.</span><span class="sxs-lookup"><span data-stu-id="867c4-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="867c4-243">Ajoutez comme nouvelle ligne le code suivant à la méthode `Evaluate` :</span><span class="sxs-lookup"><span data-stu-id="867c4-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#Evaluate)]

<span data-ttu-id="867c4-244">Les métriques suivantes sont évaluées pour la classification multiclasse :</span><span class="sxs-lookup"><span data-stu-id="867c4-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="867c4-245">Micro-précision : chaque paire exemple-classe contribue de manière égale à la métrique de précision.</span><span class="sxs-lookup"><span data-stu-id="867c4-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="867c4-246">Vous souhaitez que la micro-précision soit aussi proche que possible.</span><span class="sxs-lookup"><span data-stu-id="867c4-246">You want Micro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="867c4-247">Macro-précision : chaque classe contribue de manière égale à la métrique de précision.</span><span class="sxs-lookup"><span data-stu-id="867c4-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="867c4-248">Les classes minoritaires sont aussi importantes que les classes plus grandes.</span><span class="sxs-lookup"><span data-stu-id="867c4-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="867c4-249">Vous souhaitez que la précision de la macro soit aussi proche que possible.</span><span class="sxs-lookup"><span data-stu-id="867c4-249">You want Macro Accuracy to be as close to one as possible.</span></span>

* <span data-ttu-id="867c4-250">Perte logarithmique : consultez [Perte logarithmique](../resources/glossary.md#log-loss).</span><span class="sxs-lookup"><span data-stu-id="867c4-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="867c4-251">Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.</span><span class="sxs-lookup"><span data-stu-id="867c4-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="867c4-252">Réduction de la perte de journal-plages de [-inf, 1,00], où 1,00 est une prédiction parfaite et 0 indique des prédictions moyennes.</span><span class="sxs-lookup"><span data-stu-id="867c4-252">Log-loss reduction - Ranges from [-inf, 1.00], where 1.00 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="867c4-253">Vous souhaitez que la réduction de la perte de journal soit aussi proche que possible.</span><span class="sxs-lookup"><span data-stu-id="867c4-253">You want Log-loss reduction to be as close to one as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="867c4-254">Affichage des métriques pour la validation du modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="867c4-255">Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :</span><span class="sxs-lookup"><span data-stu-id="867c4-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a><span data-ttu-id="867c4-256">Enregistrer le modèle dans un fichier</span><span class="sxs-lookup"><span data-stu-id="867c4-256">Save the model to a file</span></span>

<span data-ttu-id="867c4-257">Une fois que vous êtes satisfait de votre modèle, enregistrez-le dans un fichier pour faire des prédictions ultérieurement ou dans une autre application.</span><span class="sxs-lookup"><span data-stu-id="867c4-257">Once satisfied with your model, save it to a file to make predictions at a later time or in another application.</span></span> <span data-ttu-id="867c4-258">Ajoutez le code suivant à la méthode `Evaluate` .</span><span class="sxs-lookup"><span data-stu-id="867c4-258">Add the following code to the `Evaluate` method.</span></span>

[!code-csharp[SnippetCallSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetCallSaveModel)]

<span data-ttu-id="867c4-259">Créez la méthode `SaveModelAsFile` sous votre méthode `Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="867c4-259">Create the `SaveModelAsFile` method below your `Evaluate` method.</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="867c4-260">Ajoutez le code suivant à votre méthode `SaveModelAsFile`.</span><span class="sxs-lookup"><span data-stu-id="867c4-260">Add the following code to your `SaveModelAsFile` method.</span></span> <span data-ttu-id="867c4-261">Ce code utilise la [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) méthode pour sérialiser et stocker le modèle formé en tant que fichier zip.</span><span class="sxs-lookup"><span data-stu-id="867c4-261">This code uses the [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) method to serialize and store the trained model as a zip file.</span></span>

[!code-csharp[SnippetSaveModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="867c4-262">Déployer et prédire avec un modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-262">Deploy and Predict with a model</span></span>

<span data-ttu-id="867c4-263">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `Evaluate`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-263">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CallPredictIssue)]

<span data-ttu-id="867c4-264">Créez la méthode `PredictIssue`, juste après la méthode `Evaluate` (et juste avant la méthode `SaveModelAsFile`), en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-264">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="867c4-265">La méthode `PredictIssue` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="867c4-265">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="867c4-266">Charge le modèle enregistré.</span><span class="sxs-lookup"><span data-stu-id="867c4-266">Loads the saved model</span></span>
* <span data-ttu-id="867c4-267">Crée un problème unique de données de test.</span><span class="sxs-lookup"><span data-stu-id="867c4-267">Creates a single issue of test data.</span></span>
* <span data-ttu-id="867c4-268">Prédit Area en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="867c4-268">Predicts Area based on test data.</span></span>
* <span data-ttu-id="867c4-269">Combine les données de test et les prédictions pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="867c4-269">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="867c4-270">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="867c4-270">Displays the predicted results.</span></span>

<span data-ttu-id="867c4-271">Chargez le modèle enregistré dans votre application en ajoutant le code suivant à la méthode `PredictIssue` :</span><span class="sxs-lookup"><span data-stu-id="867c4-271">Load the saved model into your application by adding the following code to the `PredictIssue` method:</span></span>

[!code-csharp[SnippetLoadModel](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#SnippetLoadModel)]

<span data-ttu-id="867c4-272">Ajoutez un problème GitHub pour tester la prédiction du modèle entraîné dans la méthode `Predict` en créant une instance de `GitHubIssue` :</span><span class="sxs-lookup"><span data-stu-id="867c4-272">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#AddTestIssue)]

<span data-ttu-id="867c4-273">Comme vous l’avez fait précédemment, créez une instance `PredictionEngine` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-273">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#CreatePredictionEngine)]

<span data-ttu-id="867c4-274">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="867c4-274">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="867c4-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)n’est pas thread-safe.</span><span class="sxs-lookup"><span data-stu-id="867c4-275">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="867c4-276">Il est acceptable d’utiliser dans des environnements à thread unique ou prototype.</span><span class="sxs-lookup"><span data-stu-id="867c4-276">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="867c4-277">Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le `PredictionEnginePool` service, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d' [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="867c4-277">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="867c4-278">Pour plus d’informations sur l' [utilisation `PredictionEnginePool` de dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application), consultez ce guide.</span><span class="sxs-lookup"><span data-stu-id="867c4-278">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

> [!NOTE]
> <span data-ttu-id="867c4-279">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="867c4-279">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="867c4-280">Utilisez `PredictionEngine` pour prédire l’étiquette Area GitHub en ajoutant le code suivant à la méthode `PredictIssue` servant à la prédiction :</span><span class="sxs-lookup"><span data-stu-id="867c4-280">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="867c4-281">Utilisation du modèle chargé pour la prédiction</span><span class="sxs-lookup"><span data-stu-id="867c4-281">Using the loaded model for prediction</span></span>

<span data-ttu-id="867c4-282">Affichez `Area` pour catégoriser le problème et agir en conséquence.</span><span class="sxs-lookup"><span data-stu-id="867c4-282">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="867c4-283">Créez une vue des résultats à l’aide du code <xref:System.Console.WriteLine?displayProperty=nameWithType> suivant :</span><span class="sxs-lookup"><span data-stu-id="867c4-283">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/snippets/machine-learning/GitHubIssueClassification/csharp/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="867c4-284">Résultats</span><span class="sxs-lookup"><span data-stu-id="867c4-284">Results</span></span>

<span data-ttu-id="867c4-285">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="867c4-285">Your results should be similar to the following.</span></span> <span data-ttu-id="867c4-286">Lors du traitement, le pipeline affiche des messages.</span><span class="sxs-lookup"><span data-stu-id="867c4-286">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="867c4-287">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="867c4-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="867c4-288">Ces messages ont été supprimés des résultats suivants par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="867c4-288">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="867c4-289">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="867c4-289">Congratulations!</span></span> <span data-ttu-id="867c4-290">Vous venez de créer un modèle d’apprentissage automatique pour la classification et la prédiction d’une étiquette Area d’un problème GitHub.</span><span class="sxs-lookup"><span data-stu-id="867c4-290">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="867c4-291">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification).</span><span class="sxs-lookup"><span data-stu-id="867c4-291">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="867c4-292">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="867c4-292">Next steps</span></span>

<span data-ttu-id="867c4-293">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="867c4-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="867c4-294">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="867c4-294">Prepare your data</span></span>
> * <span data-ttu-id="867c4-295">Transformer les données</span><span class="sxs-lookup"><span data-stu-id="867c4-295">Transform the data</span></span>
> * <span data-ttu-id="867c4-296">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-296">Train the model</span></span>
> * <span data-ttu-id="867c4-297">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="867c4-297">Evaluate the model</span></span>
> * <span data-ttu-id="867c4-298">Prédire avec le modèle entraîné</span><span class="sxs-lookup"><span data-stu-id="867c4-298">Predict with the trained model</span></span>
> * <span data-ttu-id="867c4-299">Déployer et prédire avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="867c4-299">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="867c4-300">Passer au tutoriel suivant pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="867c4-300">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="867c4-301">Prédiction du prix d’une course de taxi</span><span class="sxs-lookup"><span data-stu-id="867c4-301">Taxi Fare Predictor</span></span>](predict-prices.md)
