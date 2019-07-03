---
title: 'Tutoriel : Analyser les commentaires des sites web - classification binaire'
description: Ce tutoriel vous montre comment créer une application console .NET Core qui classifie les sentiments analysés dans les commentaires des sites web et qui exécute l’action appropriée. Le classifieur de sentiments binaire utilise C# dans Visual Studio.
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a766d95c62fd3a89e3291e1ab803f5222fac46ea
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306178"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="fde7a-104">Tutoriel : Analyser les sentiments dans les commentaires des sites web à l’aide d’une classification binaire dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="fde7a-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="fde7a-105">Ce tutoriel vous montre comment créer une application console .NET Core qui classifie les sentiments analysés dans les commentaires des sites web et qui exécute l’action appropriée.</span><span class="sxs-lookup"><span data-stu-id="fde7a-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="fde7a-106">Le classifieur binaire de sentiments utilise C# dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="fde7a-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="fde7a-107">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="fde7a-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="fde7a-108">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="fde7a-108">Create a console application</span></span>
> * <span data-ttu-id="fde7a-109">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="fde7a-109">Prepare data</span></span>
> * <span data-ttu-id="fde7a-110">Charger les données</span><span class="sxs-lookup"><span data-stu-id="fde7a-110">Load the data</span></span>
> * <span data-ttu-id="fde7a-111">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-111">Build and train the model</span></span>
> * <span data-ttu-id="fde7a-112">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-112">Evaluate the model</span></span>
> * <span data-ttu-id="fde7a-113">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="fde7a-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="fde7a-114">Consulter les résultats</span><span class="sxs-lookup"><span data-stu-id="fde7a-114">See the results</span></span>

<span data-ttu-id="fde7a-115">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="fde7a-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fde7a-116">Prérequis</span><span class="sxs-lookup"><span data-stu-id="fde7a-116">Prerequisites</span></span>

* <span data-ttu-id="fde7a-117">[Visual Studio 2017 15.6 ou ultérieur](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), avec la charge de travail « Développement multiplateforme .Net Core » installée</span><span class="sxs-lookup"><span data-stu-id="fde7a-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="fde7a-118">[Jeu de données « UCI Sentiment Labeled Sentences »](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (fichier zip)</span><span class="sxs-lookup"><span data-stu-id="fde7a-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="fde7a-119">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="fde7a-119">Create a console application</span></span>

1. <span data-ttu-id="fde7a-120">Créez une **application console .NET Core** appelée « SentimentAnalysis ».</span><span class="sxs-lookup"><span data-stu-id="fde7a-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="fde7a-121">Créez un répertoire nommé *Données* dans votre projet pour y enregistrer les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="fde7a-122">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="fde7a-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="fde7a-123">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="fde7a-124">Choisissez « nuget.org » comme source du package, puis sélectionnez l’onglet **Parcourir**. Recherchez **Microsoft.ML**, sélectionnez le package souhaité, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="fde7a-125">Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi.</span><span class="sxs-lookup"><span data-stu-id="fde7a-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="fde7a-126">Faites de même pour le package NuGet **Microsoft.ML.FastTree**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="fde7a-127">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="fde7a-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="fde7a-128">Les jeux de données utilisés dans ce tutoriel proviennent de « From Group to Individual Labels using Deep Features » (Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="fde7a-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="fde7a-129">al.,</span><span class="sxs-lookup"><span data-stu-id="fde7a-129">al,.</span></span> <span data-ttu-id="fde7a-130">KDD 2015), hébergé dans le référentiel UCI Machine Learning (Dua, D. et Karra Taniskidou, E., 2017).</span><span class="sxs-lookup"><span data-stu-id="fde7a-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="fde7a-131">Référentiel UCI Machine Learning [http://archive.ics.uci.edu/ml ].</span><span class="sxs-lookup"><span data-stu-id="fde7a-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="fde7a-132">Irvine (Californie) : Université de Californie, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="fde7a-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="fde7a-133">Téléchargez le [fichier zip du jeu de données UCI Sentiment Labeled Sentences](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), puis décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="fde7a-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="fde7a-134">Copiez le fichier `yelp_labelled.txt` dans le répertoire *Données* que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="fde7a-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="fde7a-135">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier `yelp_labeled.txt` et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="fde7a-136">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="fde7a-137">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="fde7a-137">Create classes and define paths</span></span>

1. <span data-ttu-id="fde7a-138">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="fde7a-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="fde7a-139">Créez deux champs globaux pour le chemin du fichier de jeu de données téléchargé et celui du fichier de modèle enregistré :</span><span class="sxs-lookup"><span data-stu-id="fde7a-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="fde7a-140">`_dataPath` contient le chemin d’accès au jeu de données utilisé pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="fde7a-141">`_modelPath` contient le chemin d’accès où le modèle formé est enregistré.</span><span class="sxs-lookup"><span data-stu-id="fde7a-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="fde7a-142">Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier les chemins :</span><span class="sxs-lookup"><span data-stu-id="fde7a-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="fde7a-143">Créez ensuite des classes pour les données d’entrée et les prédictions.</span><span class="sxs-lookup"><span data-stu-id="fde7a-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="fde7a-144">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="fde7a-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="fde7a-145">Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="fde7a-146">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="fde7a-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="fde7a-147">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="fde7a-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="fde7a-148">Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="fde7a-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="fde7a-149">Ajoutez l'instruction suivante `using` en haut du fichier *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="fde7a-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="fde7a-150">Supprimez la définition de classe existante et ajoutez le code suivant, qui contient deux classes, `SentimentData` et `SentimentPrediction`, au fichier *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="fde7a-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="fde7a-151">Comment les données ont-elles été préparées ?</span><span class="sxs-lookup"><span data-stu-id="fde7a-151">How the data was prepared</span></span>
<span data-ttu-id="fde7a-152">La classe du jeu de données d’entrée, `SentimentData`, a une valeur `string` pour les commentaires utilisateur (`SentimentText`) et une valeur `bool` (`Sentiment`) égale à 1 (sentiment positif) ou 0 (sentiment négatif).</span><span class="sxs-lookup"><span data-stu-id="fde7a-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="fde7a-153">Les deux champs ont des attributs [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) associés, qui spécifient l’ordre du fichier de données de chaque champ.</span><span class="sxs-lookup"><span data-stu-id="fde7a-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="fde7a-154">Par ailleurs, la propriété `Sentiment` a un attribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) qui la désigne comme champ `Label`.</span><span class="sxs-lookup"><span data-stu-id="fde7a-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="fde7a-155">L’exemple de fichier suivant ne possède pas de ligne d’en-tête :</span><span class="sxs-lookup"><span data-stu-id="fde7a-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="fde7a-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="fde7a-156">SentimentText</span></span>                         |<span data-ttu-id="fde7a-157">Sentiment (Label)</span><span class="sxs-lookup"><span data-stu-id="fde7a-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="fde7a-158">La serveuse était un peu lente durant le service.</span><span class="sxs-lookup"><span data-stu-id="fde7a-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="fde7a-159">0</span><span class="sxs-lookup"><span data-stu-id="fde7a-159">0</span></span>     |
|<span data-ttu-id="fde7a-160">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="fde7a-160">Crust is not good.</span></span>                    |    <span data-ttu-id="fde7a-161">0</span><span class="sxs-lookup"><span data-stu-id="fde7a-161">0</span></span>     |
|<span data-ttu-id="fde7a-162">Super ! J’ai adoré cet endroit.</span><span class="sxs-lookup"><span data-stu-id="fde7a-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="fde7a-163">1</span><span class="sxs-lookup"><span data-stu-id="fde7a-163">1</span></span>     |
|<span data-ttu-id="fde7a-164">Le service a été très rapide.</span><span class="sxs-lookup"><span data-stu-id="fde7a-164">Service was very prompt.</span></span>              |    <span data-ttu-id="fde7a-165">1</span><span class="sxs-lookup"><span data-stu-id="fde7a-165">1</span></span>     |

<span data-ttu-id="fde7a-166">`SentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-166">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="fde7a-167">Elle hérite les données de `SentimentData` et affiche `SentimentText` avec les prédictions.</span><span class="sxs-lookup"><span data-stu-id="fde7a-167">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="fde7a-168">`SentimentPrediction` comporte une valeur booléenne unique (`Sentiment`) et un attribut `PredictedLabel` `ColumnName`.</span><span class="sxs-lookup"><span data-stu-id="fde7a-168">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="fde7a-169">L’attribut `Label` sert à créer le modèle et à effectuer son apprentissage, mais il est aussi utilisé avec le jeu de données de test fractionné pour évaluer le modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-169">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="fde7a-170">L’attribut `PredictedLabel` est utilisé pendant la prédiction et l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="fde7a-170">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="fde7a-171">L’évaluation utilise les données d’entraînement, les valeurs prédites et le modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-171">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="fde7a-172">La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET.</span><span class="sxs-lookup"><span data-stu-id="fde7a-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="fde7a-173">L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="fde7a-174">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="fde7a-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="fde7a-175">Charger les données</span><span class="sxs-lookup"><span data-stu-id="fde7a-175">Load the data</span></span>
<span data-ttu-id="fde7a-176">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="fde7a-176">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="fde7a-177">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="fde7a-177">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="fde7a-178">Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="fde7a-178">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="fde7a-179">Vous préparez l’application et chargez ensuite les données :</span><span class="sxs-lookup"><span data-stu-id="fde7a-179">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="fde7a-180">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :</span><span class="sxs-lookup"><span data-stu-id="fde7a-180">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="fde7a-181">Ajoutez le code suivant comme prochaine ligne dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-181">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="fde7a-182">Créez la méthode `LoadData()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="fde7a-183">La méthode `LoadData()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fde7a-183">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="fde7a-184">Charge les données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-184">Loads the data.</span></span>
    * <span data-ttu-id="fde7a-185">Fractionne le jeu de données chargé en jeux de données d’apprentissage et de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-185">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="fde7a-186">Retourne les jeux de données d’apprentissage et de test fractionnés.</span><span class="sxs-lookup"><span data-stu-id="fde7a-186">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="fde7a-187">Ajoutez le code suivant comme première ligne de la méthode `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-187">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="fde7a-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="fde7a-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="fde7a-189">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="fde7a-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="fde7a-190">Fractionner le jeu de données pour l’apprentissage et le test du modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="fde7a-191">Quand vous préparez un modèle, vous utilisez une partie du jeu de données pour entraîner le modèle et une partie du jeu de données pour tester la précision du modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-191">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="fde7a-192">Pour fractionner les données chargées dans les jeux de données nécessaires, ajoutez le code suivant sur la ligne suivant la méthode `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="fde7a-193">Le code précédent utilise la méthode [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pour diviser le jeu de données chargé en deux jeux de données d’entraînement et de test, et les retourner dans la classe [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData).</span><span class="sxs-lookup"><span data-stu-id="fde7a-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="fde7a-194">Spécifiez le pourcentage de données du jeu de test avec le paramètre `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="fde7a-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="fde7a-195">La valeur par défaut est 10 %, mais dans cet exemple, vous spécifiez 20 % pour évaluer davantage de données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-195">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="fde7a-196">Retournez `splitDataView` à la fin de la méthode `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="fde7a-197">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-197">Build and train the model</span></span>

1. <span data-ttu-id="fde7a-198">Ajoutez l’appel suivant à la méthode `BuildAndTrainModel` comme prochaine ligne de code dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="fde7a-199">La méthode `BuildAndTrainModel()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fde7a-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="fde7a-200">Extrait et transforme les données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-200">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="fde7a-201">Effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-201">Trains the model.</span></span>
    * <span data-ttu-id="fde7a-202">Prédit les sentiments en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-202">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="fde7a-203">Retourne le modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-203">Returns the model.</span></span>

2. <span data-ttu-id="fde7a-204">Créez la méthode `BuildAndTrainModel()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="fde7a-205">Extraire et transformer les données</span><span class="sxs-lookup"><span data-stu-id="fde7a-205">Extract and transform the data</span></span>

1. <span data-ttu-id="fde7a-206">Appelez `FeaturizeText` sur la ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="fde7a-206">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="fde7a-207">La méthode `FeaturizeText()` dans le code précédent convertit la colonne de texte (`SentimentText`) en une colonne `Features` de type clé numérique, qui est utilisée par l’algorithme de machine learning, et l’ajoute comme nouvelle colonne au jeu de données :</span><span class="sxs-lookup"><span data-stu-id="fde7a-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="fde7a-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="fde7a-208">SentimentText</span></span>                         |<span data-ttu-id="fde7a-209">Sentiment</span><span class="sxs-lookup"><span data-stu-id="fde7a-209">Sentiment</span></span> |<span data-ttu-id="fde7a-210">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="fde7a-210">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="fde7a-211">La serveuse était un peu lente durant le service.</span><span class="sxs-lookup"><span data-stu-id="fde7a-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="fde7a-212">0</span><span class="sxs-lookup"><span data-stu-id="fde7a-212">0</span></span>     |<span data-ttu-id="fde7a-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="fde7a-213">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="fde7a-214">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="fde7a-214">Crust is not good.</span></span>                    |    <span data-ttu-id="fde7a-215">0</span><span class="sxs-lookup"><span data-stu-id="fde7a-215">0</span></span>     |<span data-ttu-id="fde7a-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="fde7a-216">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="fde7a-217">Super ! J’ai adoré cet endroit.</span><span class="sxs-lookup"><span data-stu-id="fde7a-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="fde7a-218">1</span><span class="sxs-lookup"><span data-stu-id="fde7a-218">1</span></span>     |<span data-ttu-id="fde7a-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="fde7a-219">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="fde7a-220">Le service a été très rapide.</span><span class="sxs-lookup"><span data-stu-id="fde7a-220">Service was very prompt.</span></span>              |    <span data-ttu-id="fde7a-221">1</span><span class="sxs-lookup"><span data-stu-id="fde7a-221">1</span></span>     |<span data-ttu-id="fde7a-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="fde7a-222">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="fde7a-223">Ajouter un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="fde7a-223">Add a learning algorithm</span></span>

<span data-ttu-id="fde7a-224">Cette application utilise un algorithme de classification qui classe les éléments ou lignes de données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-224">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="fde7a-225">Elle classe les commentaires des sites web comme positifs ou négatifs. Vous devez donc utiliser la tâche de classification binaire.</span><span class="sxs-lookup"><span data-stu-id="fde7a-225">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="fde7a-226">Ajoutez la tâche de machine learning aux définitions de transformations des données en ajoutant la ligne de code suivante dans `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-226">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="fde7a-227">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) est votre algorithme d’entraînement de classification.</span><span class="sxs-lookup"><span data-stu-id="fde7a-227">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="fde7a-228">Il est ajouté à `estimator` et accepte les caractéristiques `SentimentText` (`Features`) ainsi que les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.</span><span class="sxs-lookup"><span data-stu-id="fde7a-228">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="fde7a-229">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-229">Train the model</span></span>

<span data-ttu-id="fde7a-230">Ajustez le modèle aux données `splitTrainSet` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-230">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="fde7a-231">La méthode [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="fde7a-231">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="fde7a-232">Retourner le modèle entraîné à utiliser pour l’évaluation</span><span class="sxs-lookup"><span data-stu-id="fde7a-232">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="fde7a-233">Retournez le modèle à la fin de la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-233">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="fde7a-234">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-234">Evaluate the model</span></span>

<span data-ttu-id="fde7a-235">Une fois que votre modèle est entraîné, vérifiez ses performances avec vos données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-235">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="fde7a-236">Créez la méthode `Evaluate()` juste après `BuildAndTrainModel()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-236">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="fde7a-237">La méthode `Evaluate()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fde7a-237">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="fde7a-238">Charge le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-238">Loads the test dataset.</span></span>
    * <span data-ttu-id="fde7a-239">Crée l’évaluateur BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="fde7a-239">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="fde7a-240">Évalue le modèle et crée des métriques.</span><span class="sxs-lookup"><span data-stu-id="fde7a-240">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="fde7a-241">Affiche les métriques.</span><span class="sxs-lookup"><span data-stu-id="fde7a-241">Displays the metrics.</span></span>

2. <span data-ttu-id="fde7a-242">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main()`, juste sous l’appel à la méthode `BuildAndTrainModel()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-242">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="fde7a-243">Transformez les données `splitTestSet` en ajoutant le code suivant à `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-243">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="fde7a-244">Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour faire des prédictions sur plusieurs lignes d’entrée d’un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-244">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="fde7a-245">Évaluez le modèle en ajoutant la ligne de code suivante dans la méthode `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-245">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="fde7a-246">Une fois que vous avez le jeu de prédiction (`predictions`), la méthode [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) évalue le modèle : elle compare les valeurs prédites aux valeurs `Labels` réelles dans le jeu de données de test et retourne un objet [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) contenant les métriques relatives aux performances du modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-246">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="fde7a-247">Affichage des métriques pour la validation du modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-247">Displaying the metrics for model validation</span></span>

<span data-ttu-id="fde7a-248">Utilisez le code suivant pour afficher les métriques :</span><span class="sxs-lookup"><span data-stu-id="fde7a-248">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="fde7a-249">La métrique `Accuracy` donne la précision du modèle, qui correspond à la proportion de prédictions correctes dans le jeu de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-249">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="fde7a-250">La métrique `AreaUnderRocCurve` indique le degré de confiance conféré aux résultats de la classification des classes positif/négatif.</span><span class="sxs-lookup"><span data-stu-id="fde7a-250">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="fde7a-251">Vous voulez que la métrique `AreaUnderRocCurve` soit le plus proche possible de la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="fde7a-251">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="fde7a-252">La métrique `F1Score` donne le score F1 du modèle, qui mesure l’équilibre entre la [précision](../resources/glossary.md#precision) et le [rappel](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="fde7a-252">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="fde7a-253">Vous voulez que la métrique `F1Score` soit le plus proche possible de la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="fde7a-253">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="fde7a-254">Prédire les résultats des données de test</span><span class="sxs-lookup"><span data-stu-id="fde7a-254">Predict the test data outcome</span></span>

1. <span data-ttu-id="fde7a-255">Créez la méthode `UseModelWithSingleItem()` juste après la méthode `Evaluate()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-255">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="fde7a-256">La méthode `UseModelWithSingleItem()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fde7a-256">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="fde7a-257">Crée un commentaire unique de données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-257">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="fde7a-258">Prédit les sentiments en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-258">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="fde7a-259">Combine les données de test et les prédictions pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="fde7a-259">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="fde7a-260">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="fde7a-260">Displays the predicted results.</span></span>

2. <span data-ttu-id="fde7a-261">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main()`, juste sous l’appel à la méthode `Evaluate()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-261">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="fde7a-262">Ajoutez le code suivant comme première ligne dans la méthode `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-262">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="fde7a-263">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API utile qui vous permet de passer et d’exécuter une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-263">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="fde7a-264">Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `UseModelWithSingleItem()` en créant une instance de `SentimentData` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-264">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="fde7a-265">Passez les données de commentaire de test à `Prediction Engine` en ajoutant les lignes de code suivantes dans la méthode `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-265">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="fde7a-266">La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) effectue une prédiction sur une seule ligne de données.</span><span class="sxs-lookup"><span data-stu-id="fde7a-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="fde7a-267">Affichez `SentimentText` et la prédiction de sentiment correspondante en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="fde7a-268">Utiliser le modèle pour la prédiction</span><span class="sxs-lookup"><span data-stu-id="fde7a-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="fde7a-269">Déployer et prédire des éléments par lots</span><span class="sxs-lookup"><span data-stu-id="fde7a-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="fde7a-270">Créez la méthode `UseModelWithBatchItems()` juste après la méthode `UseModelWithSingleItem()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="fde7a-271">La méthode `UseModelWithBatchItems()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="fde7a-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="fde7a-272">Crée les données de test par lots.</span><span class="sxs-lookup"><span data-stu-id="fde7a-272">Creates batch test data.</span></span>
    * <span data-ttu-id="fde7a-273">Prédit les sentiments en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="fde7a-273">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="fde7a-274">Combine les données de test et les prédictions pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="fde7a-274">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="fde7a-275">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="fde7a-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="fde7a-276">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `UseModelWithSingleItem()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="fde7a-277">Ajoutez des commentaires pour tester les prédictions du modèle formé dans la méthode `UseModelWithBatchItems()` :</span><span class="sxs-lookup"><span data-stu-id="fde7a-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="fde7a-278">Prédire le sentiment de commentaire</span><span class="sxs-lookup"><span data-stu-id="fde7a-278">Predict comment sentiment</span></span>

<span data-ttu-id="fde7a-279">Utilisez le modèle pour prédire le sentiment de données de commentaire à l’aide de la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="fde7a-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="fde7a-280">Combiner et afficher les prédictions</span><span class="sxs-lookup"><span data-stu-id="fde7a-280">Combine and display the predictions</span></span>

<span data-ttu-id="fde7a-281">Créez un en-tête des prédictions à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="fde7a-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="fde7a-282">Comme `SentimentPrediction` est hérité de `SentimentData`, la méthode `Transform()` a rempli `SentimentText` avec les champs prédits.</span><span class="sxs-lookup"><span data-stu-id="fde7a-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="fde7a-283">À mesure que le processus ML.NET progresse, chaque composant ajoute des colonnes, ce qui rend l’affichage des résultats plus facile :</span><span class="sxs-lookup"><span data-stu-id="fde7a-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="fde7a-284">Résultats</span><span class="sxs-lookup"><span data-stu-id="fde7a-284">Results</span></span>

<span data-ttu-id="fde7a-285">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="fde7a-285">Your results should be similar to the following.</span></span> <span data-ttu-id="fde7a-286">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="fde7a-286">During processing, messages are displayed.</span></span> <span data-ttu-id="fde7a-287">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="fde7a-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="fde7a-288">Ils ont été supprimés des résultats ci-dessous par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="fde7a-288">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="fde7a-289">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="fde7a-289">Congratulations!</span></span> <span data-ttu-id="fde7a-290">Vous venez de créer un modèle d’apprentissage automatique pour la classification et la prédiction des sentiments de messages.</span><span class="sxs-lookup"><span data-stu-id="fde7a-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="fde7a-291">La création de modèles efficaces est un processus itératif.</span><span class="sxs-lookup"><span data-stu-id="fde7a-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="fde7a-292">Celui-ci présente une qualité initiale médiocre, car le tutoriel utilise de petits jeux de données pour permettre un apprentissage rapide du modèle.</span><span class="sxs-lookup"><span data-stu-id="fde7a-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="fde7a-293">Si vous n’êtes pas satisfait de la qualité du modèle, essayez de l’améliorer en fournissant de plus gros jeux de données d’entraînement ou en choisissant d’autres algorithmes d’entraînement avec des [hyperparamètres](../resources/glossary.md##hyperparameter) différents pour chacun.</span><span class="sxs-lookup"><span data-stu-id="fde7a-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="fde7a-294">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="fde7a-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="fde7a-295">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fde7a-295">Next steps</span></span>

<span data-ttu-id="fde7a-296">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="fde7a-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="fde7a-297">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="fde7a-297">Create a console application</span></span>
> * <span data-ttu-id="fde7a-298">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="fde7a-298">Prepare data</span></span>
> * <span data-ttu-id="fde7a-299">Charger les données</span><span class="sxs-lookup"><span data-stu-id="fde7a-299">Load the data</span></span>
> * <span data-ttu-id="fde7a-300">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-300">Build and train the model</span></span>
> * <span data-ttu-id="fde7a-301">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="fde7a-301">Evaluate the model</span></span>
> * <span data-ttu-id="fde7a-302">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="fde7a-302">Use the model to make a prediction</span></span>
> * <span data-ttu-id="fde7a-303">Consulter les résultats</span><span class="sxs-lookup"><span data-stu-id="fde7a-303">See the results</span></span>

<span data-ttu-id="fde7a-304">Passer au tutoriel suivant pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="fde7a-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="fde7a-305">Classification des problèmes</span><span class="sxs-lookup"><span data-stu-id="fde7a-305">Issue Classification</span></span>](github-issue-classification.md)
