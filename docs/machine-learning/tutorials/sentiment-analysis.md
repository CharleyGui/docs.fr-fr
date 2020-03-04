---
title: 'Didacticiel : analyser les commentaires de site Web-classification binaire'
description: Ce tutoriel vous montre comment créer une application console .NET Core qui classifie les sentiments analysés dans les commentaires des sites web et qui exécute l’action appropriée. Le classifieur de sentiments binaire utilise C# dans Visual Studio.
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241128"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="2603a-104">Didacticiel : analyser le sentiment de commentaires de site Web avec classification binaire dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="2603a-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="2603a-105">Ce tutoriel vous montre comment créer une application console .NET Core qui classifie les sentiments analysés dans les commentaires des sites web et qui exécute l’action appropriée.</span><span class="sxs-lookup"><span data-stu-id="2603a-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="2603a-106">Le classifieur binaire de sentiments utilise C# dans Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="2603a-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="2603a-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="2603a-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2603a-108">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="2603a-108">Create a console application</span></span>
> - <span data-ttu-id="2603a-109">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="2603a-109">Prepare data</span></span>
> - <span data-ttu-id="2603a-110">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="2603a-110">Load the data</span></span>
> - <span data-ttu-id="2603a-111">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-111">Build and train the model</span></span>
> - <span data-ttu-id="2603a-112">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-112">Evaluate the model</span></span>
> - <span data-ttu-id="2603a-113">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="2603a-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="2603a-114">Afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="2603a-114">See the results</span></span>

<span data-ttu-id="2603a-115">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="2603a-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2603a-116">Composants requis</span><span class="sxs-lookup"><span data-stu-id="2603a-116">Prerequisites</span></span>

- <span data-ttu-id="2603a-117">[Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) avec la charge de travail « développement multiplateforme .net Core » installée</span><span class="sxs-lookup"><span data-stu-id="2603a-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="2603a-118">[Jeu de données « UCI Sentiment Labeled Sentences »](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (fichier zip)</span><span class="sxs-lookup"><span data-stu-id="2603a-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2603a-119">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="2603a-119">Create a console application</span></span>

1. <span data-ttu-id="2603a-120">Créez une **application console .NET Core** appelée « SentimentAnalysis ».</span><span class="sxs-lookup"><span data-stu-id="2603a-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="2603a-121">Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="2603a-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="2603a-122">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="2603a-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2603a-123">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2603a-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2603a-124">Choisissez « nuget.org » comme source du package, puis sélectionnez l’onglet **Parcourir** . recherchez **Microsoft.ml**, sélectionnez le package souhaité, puis cliquez sur le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="2603a-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="2603a-125">Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi.</span><span class="sxs-lookup"><span data-stu-id="2603a-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="2603a-126">Faites de même pour le package NuGet **Microsoft.ML.FastTree**.</span><span class="sxs-lookup"><span data-stu-id="2603a-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="2603a-127">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="2603a-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="2603a-128">Les jeux de données utilisés dans ce tutoriel proviennent de « From Group to Individual Labels using Deep Features » (Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="2603a-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="2603a-129">al.,</span><span class="sxs-lookup"><span data-stu-id="2603a-129">al,.</span></span> <span data-ttu-id="2603a-130">KDD 2015 et hébergé dans le référentiel Machine Learning UCI-Dua, D. et karra Taniskidou, E. (2017).</span><span class="sxs-lookup"><span data-stu-id="2603a-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="2603a-131">Référentiel UCI Machine Learning [http://archive.ics.uci.edu/ml].</span><span class="sxs-lookup"><span data-stu-id="2603a-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="2603a-132">Irvine, Californie : Université de Californie, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="2603a-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="2603a-133">Téléchargez le [fichier zip du jeu de données UCI Sentiment Labeled Sentences](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), puis décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="2603a-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="2603a-134">Copiez le fichier `yelp_labelled.txt` dans le répertoire *Données* que vous avez créé.</span><span class="sxs-lookup"><span data-stu-id="2603a-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="2603a-135">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier `yelp_labeled.txt` et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2603a-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="2603a-136">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="2603a-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="2603a-137">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="2603a-137">Create classes and define paths</span></span>

1. <span data-ttu-id="2603a-138">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="2603a-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="2603a-139">Ajoutez le code suivant à la ligne située juste au-dessus de la méthode `Main`, pour créer un champ qui contiendra le chemin d’accès au fichier de jeu de données téléchargé récemment :</span><span class="sxs-lookup"><span data-stu-id="2603a-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="2603a-140">Créez ensuite des classes pour les données d’entrée et les prédictions.</span><span class="sxs-lookup"><span data-stu-id="2603a-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="2603a-141">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="2603a-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="2603a-142">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="2603a-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="2603a-143">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="2603a-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="2603a-144">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2603a-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="2603a-145">Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="2603a-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2603a-146">Ajoutez l'instruction suivante `using` en haut du fichier *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="2603a-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="2603a-147">Supprimez la définition de classe existante et ajoutez le code suivant, qui contient deux classes, `SentimentData` et `SentimentPrediction`, au fichier *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="2603a-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="2603a-148">Comment les données ont-elles été préparées ?</span><span class="sxs-lookup"><span data-stu-id="2603a-148">How the data was prepared</span></span>

<span data-ttu-id="2603a-149">La classe du jeu de données d’entrée, `SentimentData`, a une valeur `string` pour les commentaires utilisateur (`SentimentText`) et une valeur `bool` (`Sentiment`) égale à 1 (sentiment positif) ou 0 (sentiment négatif).</span><span class="sxs-lookup"><span data-stu-id="2603a-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="2603a-150">Les deux champs ont des attributs [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) associés, qui spécifient l’ordre du fichier de données de chaque champ.</span><span class="sxs-lookup"><span data-stu-id="2603a-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="2603a-151">Par ailleurs, la propriété `Sentiment` a un attribut [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) qui la désigne comme champ `Label`.</span><span class="sxs-lookup"><span data-stu-id="2603a-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="2603a-152">L’exemple de fichier suivant ne possède pas de ligne d’en-tête :</span><span class="sxs-lookup"><span data-stu-id="2603a-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="2603a-153">SentimentText</span><span class="sxs-lookup"><span data-stu-id="2603a-153">SentimentText</span></span>                         |<span data-ttu-id="2603a-154">Sentiment (Label)</span><span class="sxs-lookup"><span data-stu-id="2603a-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="2603a-155">La serveuse était un peu lente durant le service.</span><span class="sxs-lookup"><span data-stu-id="2603a-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="2603a-156">0</span><span class="sxs-lookup"><span data-stu-id="2603a-156">0</span></span>     |
|<span data-ttu-id="2603a-157">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="2603a-157">Crust is not good.</span></span>                    |    <span data-ttu-id="2603a-158">0</span><span class="sxs-lookup"><span data-stu-id="2603a-158">0</span></span>     |
|<span data-ttu-id="2603a-159">... J’ai aimé cet endroit.</span><span class="sxs-lookup"><span data-stu-id="2603a-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="2603a-160">1</span><span class="sxs-lookup"><span data-stu-id="2603a-160">1</span></span>     |
|<span data-ttu-id="2603a-161">Le service a été très rapide.</span><span class="sxs-lookup"><span data-stu-id="2603a-161">Service was very prompt.</span></span>              |    <span data-ttu-id="2603a-162">1</span><span class="sxs-lookup"><span data-stu-id="2603a-162">1</span></span>     |

<span data-ttu-id="2603a-163">`SentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="2603a-164">Elle hérite de `SentimentData` afin que l’entrée `SentimentText` puisse être affichée en même temps que la prédiction de sortie.</span><span class="sxs-lookup"><span data-stu-id="2603a-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="2603a-165">La valeur booléenne `Prediction` est la valeur que le modèle prédit quand la nouvelle entrée `SentimentText` lui est fournie.</span><span class="sxs-lookup"><span data-stu-id="2603a-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="2603a-166">La classe de sortie `SentimentPrediction` contient deux autres propriétés calculées par le modèle : `Score`, le score brut calculé par le modèle, et `Probability`, le score étalonné à la probabilité que le texte ait un sentiment positif.</span><span class="sxs-lookup"><span data-stu-id="2603a-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="2603a-167">Pour ce tutoriel, la propriété la plus importante est `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="2603a-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2603a-168">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="2603a-168">Load the data</span></span>

<span data-ttu-id="2603a-169">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="2603a-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="2603a-170">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="2603a-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="2603a-171">Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="2603a-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="2603a-172">La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2603a-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="2603a-173">L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2603a-174">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2603a-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="2603a-175">Vous préparez l’application et chargez ensuite les données :</span><span class="sxs-lookup"><span data-stu-id="2603a-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="2603a-176">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :</span><span class="sxs-lookup"><span data-stu-id="2603a-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="2603a-177">Ajoutez le code suivant comme prochaine ligne dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="2603a-178">Créez la méthode `LoadData()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="2603a-179">La méthode `LoadData()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2603a-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2603a-180">Charge les données.</span><span class="sxs-lookup"><span data-stu-id="2603a-180">Loads the data.</span></span>
    - <span data-ttu-id="2603a-181">Fractionne le jeu de données chargé en jeux de données d’apprentissage et de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="2603a-182">Retourne les jeux de données d’apprentissage et de test fractionnés.</span><span class="sxs-lookup"><span data-stu-id="2603a-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="2603a-183">Ajoutez le code suivant comme première ligne de la méthode `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="2603a-184">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) définit le schéma de données et lit le fichier.</span><span class="sxs-lookup"><span data-stu-id="2603a-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="2603a-185">Elle prend les variables de chemin de données et retourne un `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="2603a-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="2603a-186">Fractionner le jeu de données pour l’apprentissage et le test du modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="2603a-187">Quand vous préparez un modèle, vous utilisez une partie du jeu de données pour entraîner le modèle et une partie du jeu de données pour tester la précision du modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="2603a-188">Pour fractionner les données chargées dans les jeux de données nécessaires, ajoutez le code suivant sur la ligne suivant la méthode `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="2603a-189">Le code précédent utilise la méthode [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) pour diviser le jeu de données chargé en deux jeux de données d’entraînement et de test, et les retourner dans la classe [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData).</span><span class="sxs-lookup"><span data-stu-id="2603a-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="2603a-190">Spécifiez le pourcentage de données du jeu de test avec le paramètre `testFraction`.</span><span class="sxs-lookup"><span data-stu-id="2603a-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="2603a-191">La valeur par défaut est 10 %, mais dans cet exemple, vous spécifiez 20 % pour évaluer davantage de données.</span><span class="sxs-lookup"><span data-stu-id="2603a-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="2603a-192">Retournez `splitDataView` à la fin de la méthode `LoadData()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="2603a-193">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-193">Build and train the model</span></span>

1. <span data-ttu-id="2603a-194">Ajoutez l’appel suivant à la méthode `BuildAndTrainModel` comme prochaine ligne de code dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="2603a-195">La méthode `BuildAndTrainModel()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2603a-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2603a-196">Extrait et transforme les données.</span><span class="sxs-lookup"><span data-stu-id="2603a-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="2603a-197">Effectue l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-197">Trains the model.</span></span>
    - <span data-ttu-id="2603a-198">Prédit les sentiments en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="2603a-199">Retourne le modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-199">Returns the model.</span></span>

2. <span data-ttu-id="2603a-200">Créez la méthode `BuildAndTrainModel()` juste après la méthode `Main()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="2603a-201">Extraire et transformer les données</span><span class="sxs-lookup"><span data-stu-id="2603a-201">Extract and transform the data</span></span>

1. <span data-ttu-id="2603a-202">Appelez `FeaturizeText` sur la ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="2603a-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="2603a-203">La méthode `FeaturizeText()` dans le code précédent convertit la colonne de texte (`SentimentText`) en une colonne `Features` de type clé numérique, qui est utilisée par l’algorithme de machine learning, et l’ajoute comme nouvelle colonne au jeu de données :</span><span class="sxs-lookup"><span data-stu-id="2603a-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="2603a-204">SentimentText</span><span class="sxs-lookup"><span data-stu-id="2603a-204">SentimentText</span></span>                         |<span data-ttu-id="2603a-205">Sentiments</span><span class="sxs-lookup"><span data-stu-id="2603a-205">Sentiment</span></span> |<span data-ttu-id="2603a-206">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="2603a-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="2603a-207">La serveuse était un peu lente durant le service.</span><span class="sxs-lookup"><span data-stu-id="2603a-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="2603a-208">0</span><span class="sxs-lookup"><span data-stu-id="2603a-208">0</span></span>     |<span data-ttu-id="2603a-209">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="2603a-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="2603a-210">La pâte n’est pas bonne.</span><span class="sxs-lookup"><span data-stu-id="2603a-210">Crust is not good.</span></span>                    |    <span data-ttu-id="2603a-211">0</span><span class="sxs-lookup"><span data-stu-id="2603a-211">0</span></span>     |<span data-ttu-id="2603a-212">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="2603a-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="2603a-213">... J’ai aimé cet endroit.</span><span class="sxs-lookup"><span data-stu-id="2603a-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="2603a-214">1</span><span class="sxs-lookup"><span data-stu-id="2603a-214">1</span></span>     |<span data-ttu-id="2603a-215">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="2603a-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="2603a-216">Le service a été très rapide.</span><span class="sxs-lookup"><span data-stu-id="2603a-216">Service was very prompt.</span></span>              |    <span data-ttu-id="2603a-217">1</span><span class="sxs-lookup"><span data-stu-id="2603a-217">1</span></span>     |<span data-ttu-id="2603a-218">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="2603a-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="2603a-219">Ajouter un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="2603a-219">Add a learning algorithm</span></span>

<span data-ttu-id="2603a-220">Cette application utilise un algorithme de classification qui classe les éléments ou lignes de données.</span><span class="sxs-lookup"><span data-stu-id="2603a-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="2603a-221">Elle classe les commentaires des sites web comme positifs ou négatifs. Vous devez donc utiliser la tâche de classification binaire.</span><span class="sxs-lookup"><span data-stu-id="2603a-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="2603a-222">Ajoutez la tâche de machine learning aux définitions de transformations des données en ajoutant la ligne de code suivante dans `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="2603a-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) est votre algorithme d’entraînement de classification.</span><span class="sxs-lookup"><span data-stu-id="2603a-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="2603a-224">Il est ajouté à `estimator` et accepte les caractéristiques `SentimentText` (`Features`) ainsi que les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.</span><span class="sxs-lookup"><span data-stu-id="2603a-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="2603a-225">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-225">Train the model</span></span>

<span data-ttu-id="2603a-226">Ajustez le modèle aux données `splitTrainSet` et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="2603a-227">La méthode [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="2603a-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="2603a-228">Retourner le modèle entraîné à utiliser pour l’évaluation</span><span class="sxs-lookup"><span data-stu-id="2603a-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="2603a-229">Retournez le modèle à la fin de la méthode `BuildAndTrainModel()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="2603a-230">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-230">Evaluate the model</span></span>

<span data-ttu-id="2603a-231">Une fois que votre modèle est entraîné, vérifiez ses performances avec vos données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="2603a-232">Créez la méthode `Evaluate()` juste après `BuildAndTrainModel()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="2603a-233">La méthode `Evaluate()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2603a-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2603a-234">Charge le jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="2603a-235">Crée l’évaluateur BinaryClassification.</span><span class="sxs-lookup"><span data-stu-id="2603a-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="2603a-236">Évalue le modèle et crée des métriques.</span><span class="sxs-lookup"><span data-stu-id="2603a-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="2603a-237">Affiche les métriques.</span><span class="sxs-lookup"><span data-stu-id="2603a-237">Displays the metrics.</span></span>

2. <span data-ttu-id="2603a-238">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main()`, juste sous l’appel à la méthode `BuildAndTrainModel()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="2603a-239">Transformez les données `splitTestSet` en ajoutant le code suivant à `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="2603a-240">Le code précédent utilise la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) pour faire des prédictions sur plusieurs lignes d’entrée d’un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="2603a-241">Évaluez le modèle en ajoutant la ligne de code suivante dans la méthode `Evaluate()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="2603a-242">Une fois que vous avez le jeu de prédiction (`predictions`), la méthode [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) évalue le modèle : elle compare les valeurs prédites aux valeurs `Labels` réelles dans le jeu de données de test et retourne un objet [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) contenant les métriques relatives aux performances du modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="2603a-243">Affichage des métriques pour la validation du modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="2603a-244">Utilisez le code suivant pour afficher les métriques :</span><span class="sxs-lookup"><span data-stu-id="2603a-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="2603a-245">La métrique `Accuracy` donne la précision du modèle, qui correspond à la proportion de prédictions correctes dans le jeu de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="2603a-246">La métrique `AreaUnderRocCurve` indique le degré de confiance conféré aux résultats de la classification des classes positif/négatif.</span><span class="sxs-lookup"><span data-stu-id="2603a-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="2603a-247">Vous voulez que la métrique `AreaUnderRocCurve` soit le plus proche possible de la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="2603a-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="2603a-248">La métrique `F1Score` donne le score F1 du modèle, qui mesure l’équilibre entre la [précision](../resources/glossary.md#precision) et le [rappel](../resources/glossary.md#recall).</span><span class="sxs-lookup"><span data-stu-id="2603a-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="2603a-249">Vous voulez que la métrique `F1Score` soit le plus proche possible de la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="2603a-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="2603a-250">Prédire les résultats des données de test</span><span class="sxs-lookup"><span data-stu-id="2603a-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="2603a-251">Créez la méthode `UseModelWithSingleItem()` juste après la méthode `Evaluate()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="2603a-252">La méthode `UseModelWithSingleItem()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2603a-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2603a-253">Crée un commentaire unique de données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="2603a-254">Prédit les sentiments en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="2603a-255">Combine les données de test et les prédictions pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="2603a-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="2603a-256">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="2603a-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="2603a-257">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main()`, juste sous l’appel à la méthode `Evaluate()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="2603a-258">Ajoutez le code suivant comme première ligne dans la méthode `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="2603a-259">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="2603a-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2603a-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="2603a-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2603a-261">Il est acceptable d’utiliser dans des environnements à thread unique ou prototype.</span><span class="sxs-lookup"><span data-stu-id="2603a-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2603a-262">Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le service `PredictionEnginePool`, qui crée une [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) de [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objets à utiliser dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2603a-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2603a-263">Consultez ce guide sur l' [utilisation de `PredictionEnginePool` dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="2603a-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2603a-264">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="2603a-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="2603a-265">Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `UseModelWithSingleItem()` en créant une instance de `SentimentData` :</span><span class="sxs-lookup"><span data-stu-id="2603a-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="2603a-266">Transmettez les données de commentaire de test au [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) en ajoutant le code suivant en tant que lignes de code suivantes dans la méthode `UseModelWithSingleItem()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="2603a-267">La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) effectue une prédiction sur une seule ligne de données.</span><span class="sxs-lookup"><span data-stu-id="2603a-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="2603a-268">Affichez `SentimentText` et la prédiction de sentiment correspondante en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="2603a-269">Utiliser le modèle pour la prédiction</span><span class="sxs-lookup"><span data-stu-id="2603a-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="2603a-270">Déployer et prédire des éléments par lots</span><span class="sxs-lookup"><span data-stu-id="2603a-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="2603a-271">Créez la méthode `UseModelWithBatchItems()` juste après la méthode `UseModelWithSingleItem()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="2603a-272">La méthode `UseModelWithBatchItems()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2603a-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2603a-273">Crée les données de test par lots.</span><span class="sxs-lookup"><span data-stu-id="2603a-273">Creates batch test data.</span></span>
    - <span data-ttu-id="2603a-274">Prédit les sentiments en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="2603a-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="2603a-275">Combine les données de test et les prédictions pour générer des rapports.</span><span class="sxs-lookup"><span data-stu-id="2603a-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="2603a-276">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="2603a-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="2603a-277">Ajoutez un appel à la nouvelle méthode à partir de la méthode `Main`, juste sous l’appel à la méthode `UseModelWithSingleItem()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="2603a-278">Ajoutez des commentaires pour tester les prédictions du modèle formé dans la méthode `UseModelWithBatchItems()` :</span><span class="sxs-lookup"><span data-stu-id="2603a-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="2603a-279">Prédire le sentiment de commentaire</span><span class="sxs-lookup"><span data-stu-id="2603a-279">Predict comment sentiment</span></span>

<span data-ttu-id="2603a-280">Utilisez le modèle pour prédire le sentiment de données de commentaire à l’aide de la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) :</span><span class="sxs-lookup"><span data-stu-id="2603a-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="2603a-281">Combiner et afficher les prédictions</span><span class="sxs-lookup"><span data-stu-id="2603a-281">Combine and display the predictions</span></span>

<span data-ttu-id="2603a-282">Créez un en-tête des prédictions à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="2603a-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="2603a-283">Comme `SentimentPrediction` est hérité de `SentimentData`, la méthode `Transform()` a rempli `SentimentText` avec les champs prédits.</span><span class="sxs-lookup"><span data-stu-id="2603a-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="2603a-284">À mesure que le processus ML.NET progresse, chaque composant ajoute des colonnes, ce qui rend l’affichage des résultats plus facile :</span><span class="sxs-lookup"><span data-stu-id="2603a-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="2603a-285">Résultats</span><span class="sxs-lookup"><span data-stu-id="2603a-285">Results</span></span>

<span data-ttu-id="2603a-286">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="2603a-286">Your results should be similar to the following.</span></span> <span data-ttu-id="2603a-287">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="2603a-287">During processing, messages are displayed.</span></span> <span data-ttu-id="2603a-288">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="2603a-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2603a-289">Ils ont été supprimés des résultats ci-dessous par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="2603a-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="2603a-290">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="2603a-290">Congratulations!</span></span> <span data-ttu-id="2603a-291">Vous venez de créer un modèle d’apprentissage automatique pour la classification et la prédiction des sentiments de messages.</span><span class="sxs-lookup"><span data-stu-id="2603a-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="2603a-292">La création de modèles efficaces est un processus itératif.</span><span class="sxs-lookup"><span data-stu-id="2603a-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="2603a-293">Celui-ci présente une qualité initiale médiocre, car le tutoriel utilise de petits jeux de données pour permettre un apprentissage rapide du modèle.</span><span class="sxs-lookup"><span data-stu-id="2603a-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="2603a-294">Si vous n’êtes pas satisfait de la qualité du modèle, essayez de l’améliorer en fournissant de plus gros jeux de données d’entraînement ou en choisissant d’autres algorithmes d’entraînement avec des [hyperparamètres](../resources/glossary.md#hyperparameter) différents pour chacun.</span><span class="sxs-lookup"><span data-stu-id="2603a-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="2603a-295">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis).</span><span class="sxs-lookup"><span data-stu-id="2603a-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2603a-296">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2603a-296">Next steps</span></span>

<span data-ttu-id="2603a-297">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="2603a-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2603a-298">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="2603a-298">Create a console application</span></span>
> - <span data-ttu-id="2603a-299">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="2603a-299">Prepare data</span></span>
> - <span data-ttu-id="2603a-300">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="2603a-300">Load the data</span></span>
> - <span data-ttu-id="2603a-301">Générer et entraîner le modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-301">Build and train the model</span></span>
> - <span data-ttu-id="2603a-302">Évaluer le modèle</span><span class="sxs-lookup"><span data-stu-id="2603a-302">Evaluate the model</span></span>
> - <span data-ttu-id="2603a-303">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="2603a-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="2603a-304">Afficher les résultats</span><span class="sxs-lookup"><span data-stu-id="2603a-304">See the results</span></span>

<span data-ttu-id="2603a-305">Passer au tutoriel suivant pour en savoir plus</span><span class="sxs-lookup"><span data-stu-id="2603a-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2603a-306">Classification des problèmes</span><span class="sxs-lookup"><span data-stu-id="2603a-306">Issue Classification</span></span>](github-issue-classification.md)
