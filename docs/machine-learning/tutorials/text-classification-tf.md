---
title: 'Tutoriel : Analyser les sentiments des revues de films à l’aide d’un modèle TensorFlow pré-formé'
description: Ce didacticiel vous montre comment utiliser un modèle TensorFlow pré-formé pour classer les sentiments dans les commentaires de sites Web. Le classifieur de sentiment binaire C# est une application console développée à l’aide de Visual Studio.
ms.date: 09/11/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: nakersha
author: natke
ms.openlocfilehash: 2dd10c0843b2bea4755d5f4f0aceea6509c7cf46
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054306"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="08487-104">Tutoriel : Analyser les sentiments des revues de films à l’aide d’un modèle TensorFlow pré-formé dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="08487-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="08487-105">Ce didacticiel vous montre comment utiliser un modèle TensorFlow pré-formé pour classer les sentiments dans les commentaires de sites Web.</span><span class="sxs-lookup"><span data-stu-id="08487-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="08487-106">Le classifieur de sentiment binaire C# est une application console développée à l’aide de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="08487-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="08487-107">Le modèle TensorFlow utilisé dans ce didacticiel a été formé à l’aide des revues de films à partir de la base de données IMDB.</span><span class="sxs-lookup"><span data-stu-id="08487-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="08487-108">Une fois que vous avez terminé de développer l’application, vous serez en mesure de fournir un texte d’examen de films et l’application vous indiquera si la révision a un sentiment positif ou négatif.</span><span class="sxs-lookup"><span data-stu-id="08487-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="08487-109">Ce tutoriel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="08487-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="08487-110">Charger un modèle TensorFlow pré-formé</span><span class="sxs-lookup"><span data-stu-id="08487-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="08487-111">Transformer le texte de commentaire de site Web en fonctionnalités adaptées au modèle</span><span class="sxs-lookup"><span data-stu-id="08487-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="08487-112">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="08487-112">Use the model to make a prediction</span></span>

<span data-ttu-id="08487-113">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="08487-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="08487-114">Prérequis</span><span class="sxs-lookup"><span data-stu-id="08487-114">Prerequisites</span></span>

* <span data-ttu-id="08487-115">[Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="08487-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="08487-116">Installation</span><span class="sxs-lookup"><span data-stu-id="08487-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="08487-117">Créer l’application</span><span class="sxs-lookup"><span data-stu-id="08487-117">Create the application</span></span>

1. <span data-ttu-id="08487-118">Créez une **application console .net Core** appelée « TextClassificationTF ».</span><span class="sxs-lookup"><span data-stu-id="08487-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="08487-119">Créez un répertoire nommé *Data* dans votre projet pour enregistrer les fichiers du jeu de données.</span><span class="sxs-lookup"><span data-stu-id="08487-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="08487-120">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="08487-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="08487-121">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="08487-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="08487-122">Choisissez « nuget.org » comme source du package, puis sélectionnez l’onglet **Parcourir**. Recherchez **Microsoft.ML**, sélectionnez le package souhaité, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="08487-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="08487-123">Poursuivez l’installation en acceptant les termes du contrat de licence pour le package choisi.</span><span class="sxs-lookup"><span data-stu-id="08487-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="08487-124">Répétez ces étapes pour **Microsoft. ml. TensorFlow**.</span><span class="sxs-lookup"><span data-stu-id="08487-124">Repeat these steps for **Microsoft.ML.TensorFlow**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="08487-125">Ajouter le modèle TensorFlow au projet</span><span class="sxs-lookup"><span data-stu-id="08487-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="08487-126">Le modèle de ce didacticiel provient de la GitHub référentiel [dotnet/machinelearning-TestData](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) .</span><span class="sxs-lookup"><span data-stu-id="08487-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="08487-127">Le modèle est au format TensorFlow SavedModel.</span><span class="sxs-lookup"><span data-stu-id="08487-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="08487-128">Téléchargez le [fichier zip sentiment_model](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="08487-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="08487-129">Le fichier zip contient les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="08487-129">The zip file contains:</span></span>

    * <span data-ttu-id="08487-130">`saved_model.pb`: le modèle TensorFlow lui-même.</span><span class="sxs-lookup"><span data-stu-id="08487-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="08487-131">Le modèle prend un tableau d’entiers de longueur fixe (taille 600) qui représente le texte dans une chaîne de révision IMDB et génère deux probabilités qui totalisent 1 : la probabilité que la revue d’entrée ait un sentiment positif et la probabilité que la révision d’entrée ait sentiment négatif.</span><span class="sxs-lookup"><span data-stu-id="08487-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="08487-132">`imdb_word_index.csv`: mappage de mots individuels à une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="08487-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="08487-133">Le mappage est utilisé pour générer les fonctionnalités d’entrée pour le modèle TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="08487-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="08487-134">Copiez le contenu du répertoire `sentiment_model` le plus profond dans le `sentiment_model` répertoire de votre projet *TextClassificationTF* .</span><span class="sxs-lookup"><span data-stu-id="08487-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="08487-135">Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="08487-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![contenu du répertoire sentiment_model](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="08487-137">Dans Explorateur de solutions, cliquez avec le bouton droit sur chacun des fichiers `sentiment_model` dans le répertoire et sous-répertoire, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="08487-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="08487-138">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="08487-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="08487-139">Ajouter des instructions using et des variables globales</span><span class="sxs-lookup"><span data-stu-id="08487-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="08487-140">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="08487-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="08487-141">Créez deux variables globales juste au `Main` -dessus de la méthode pour contenir le chemin d’accès au fichier de modèle enregistré et la longueur du vecteur de fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="08487-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="08487-142">`_modelPath`chemin d’accès du fichier du modèle formé.</span><span class="sxs-lookup"><span data-stu-id="08487-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="08487-143">`FeatureLength`longueur du tableau de fonctionnalités entières attendue par le modèle.</span><span class="sxs-lookup"><span data-stu-id="08487-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="08487-144">Modéliser les données</span><span class="sxs-lookup"><span data-stu-id="08487-144">Model the data</span></span>

<span data-ttu-id="08487-145">Les revues de film sont du texte en forme libre.</span><span class="sxs-lookup"><span data-stu-id="08487-145">Movie reviews are free form text.</span></span> <span data-ttu-id="08487-146">Votre application convertit le texte dans le format d’entrée attendu par le modèle en plusieurs étapes discrètes.</span><span class="sxs-lookup"><span data-stu-id="08487-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="08487-147">La première consiste à fractionner le texte en mots séparés et à utiliser le fichier de mappage fourni pour mapper chaque mot sur un encodage entier.</span><span class="sxs-lookup"><span data-stu-id="08487-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="08487-148">Le résultat de cette transformation est un tableau d’entiers de longueur variable dont la longueur correspond au nombre de mots de la phrase.</span><span class="sxs-lookup"><span data-stu-id="08487-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="08487-149">Propriété</span><span class="sxs-lookup"><span data-stu-id="08487-149">Property</span></span>| <span data-ttu-id="08487-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="08487-150">Value</span></span>|<span data-ttu-id="08487-151">Type</span><span class="sxs-lookup"><span data-stu-id="08487-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="08487-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="08487-152">ReviewText</span></span>|<span data-ttu-id="08487-153">ce film est vraiment parfait</span><span class="sxs-lookup"><span data-stu-id="08487-153">this film is really good</span></span>|<span data-ttu-id="08487-154">string</span><span class="sxs-lookup"><span data-stu-id="08487-154">string</span></span>|
|<span data-ttu-id="08487-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="08487-155">VariableLengthFeatures</span></span>|<span data-ttu-id="08487-156">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="08487-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="08487-157">int []</span><span class="sxs-lookup"><span data-stu-id="08487-157">int[]</span></span>|

<span data-ttu-id="08487-158">Le tableau de fonctionnalités de longueur variable est ensuite redimensionné à une longueur fixe de 600.</span><span class="sxs-lookup"><span data-stu-id="08487-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="08487-159">Il s’agit de la longueur attendue par le modèle TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="08487-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="08487-160">Propriété</span><span class="sxs-lookup"><span data-stu-id="08487-160">Property</span></span>| <span data-ttu-id="08487-161">Valeur</span><span class="sxs-lookup"><span data-stu-id="08487-161">Value</span></span>|<span data-ttu-id="08487-162">Type</span><span class="sxs-lookup"><span data-stu-id="08487-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="08487-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="08487-163">ReviewText</span></span>|<span data-ttu-id="08487-164">ce film est vraiment parfait</span><span class="sxs-lookup"><span data-stu-id="08487-164">this film is really good</span></span>|<span data-ttu-id="08487-165">string</span><span class="sxs-lookup"><span data-stu-id="08487-165">string</span></span>|
|<span data-ttu-id="08487-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="08487-166">VariableLengthFeatures</span></span>|<span data-ttu-id="08487-167">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="08487-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="08487-168">int []</span><span class="sxs-lookup"><span data-stu-id="08487-168">int[]</span></span>|
|<span data-ttu-id="08487-169">Fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="08487-169">Features</span></span>|<span data-ttu-id="08487-170">14, 22, 9, 66, 78,...</span><span class="sxs-lookup"><span data-stu-id="08487-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="08487-171">int [600]</span><span class="sxs-lookup"><span data-stu-id="08487-171">int[600]</span></span>|

1. <span data-ttu-id="08487-172">Créez une classe pour vos données d’entrée, après `Main` la méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="08487-173">La classe de données d' `MovieReview`entrée,, `string` a un pour les`ReviewText`commentaires de l’utilisateur ().</span><span class="sxs-lookup"><span data-stu-id="08487-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="08487-174">Créez une classe pour les fonctionnalités de longueur variable, après `Main` la méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="08487-175">La `VariableLengthFeatures` propriété a un attribut [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) pour le désigner comme vecteur.</span><span class="sxs-lookup"><span data-stu-id="08487-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="08487-176">Tous les éléments vectoriels doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="08487-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="08487-177">Dans les jeux de données comportant un grand nombre de colonnes, le chargement de plusieurs colonnes en tant que vecteur unique réduit le nombre de passes de données lorsque vous appliquez des transformations de données.</span><span class="sxs-lookup"><span data-stu-id="08487-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="08487-178">Cette classe est utilisée dans l' `ResizeFeatures` action.</span><span class="sxs-lookup"><span data-stu-id="08487-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="08487-179">Les noms de ses propriétés (dans le cas présent, un seul) sont utilisés pour indiquer les colonnes du DataView qui peuvent être utilisées comme _entrée_ de l’action de mappage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08487-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="08487-180">Créez une classe pour les fonctionnalités de longueur fixe, après `Main` la méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="08487-181">Cette classe est utilisée dans l' `ResizeFeatures` action.</span><span class="sxs-lookup"><span data-stu-id="08487-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="08487-182">Les noms de ses propriétés (dans le cas présent, un seul) sont utilisés pour indiquer les colonnes du DataView qui peuvent être utilisées comme _sortie_ de l’action de mappage personnalisé.</span><span class="sxs-lookup"><span data-stu-id="08487-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="08487-183">Notez que le nom de la propriété `Features` est déterminé par le modèle TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="08487-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="08487-184">Vous ne pouvez pas modifier ce nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="08487-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="08487-185">Créez une classe pour la prédiction après la `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="08487-186">`MovieReviewSentimentPrediction` est la classe de prédiction utilisée après l’entraînement du modèle.</span><span class="sxs-lookup"><span data-stu-id="08487-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="08487-187">`MovieReviewSentimentPrediction`a un tableau `float` unique (`Prediction`) et un `VectorType` attribut.</span><span class="sxs-lookup"><span data-stu-id="08487-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>
    
### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="08487-188">Créer le MLContext, le dictionnaire de recherche et l’action pour redimensionner les fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="08487-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="08487-189">La [classe MLContext](xref:Microsoft.ML.MLContext) constitue un point de départ pour toutes les opérations ML.NET.</span><span class="sxs-lookup"><span data-stu-id="08487-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="08487-190">L’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets du workflow de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="08487-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="08487-191">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="08487-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="08487-192">Remplacez la ligne `Console.WriteLine("Hello World!")` dans la méthode `Main` par le code suivant pour déclarer et initialiser la variable mlContext :</span><span class="sxs-lookup"><span data-stu-id="08487-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="08487-193">Créez un dictionnaire pour encoder des mots sous forme d' [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) entiers à l’aide de la méthode pour charger des données de mappage à partir d’un fichier, comme indiqué dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="08487-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="08487-194">Word</span><span class="sxs-lookup"><span data-stu-id="08487-194">Word</span></span>     |<span data-ttu-id="08487-195">Index</span><span class="sxs-lookup"><span data-stu-id="08487-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="08487-196">fête</span><span class="sxs-lookup"><span data-stu-id="08487-196">kids</span></span>     |  <span data-ttu-id="08487-197">362</span><span class="sxs-lookup"><span data-stu-id="08487-197">362</span></span>    |
    |<span data-ttu-id="08487-198">préférable</span><span class="sxs-lookup"><span data-stu-id="08487-198">want</span></span>     |  <span data-ttu-id="08487-199">181</span><span class="sxs-lookup"><span data-stu-id="08487-199">181</span></span>    |
    |<span data-ttu-id="08487-200">Flex</span><span class="sxs-lookup"><span data-stu-id="08487-200">wrong</span></span>    |  <span data-ttu-id="08487-201">355</span><span class="sxs-lookup"><span data-stu-id="08487-201">355</span></span>    |
    |<span data-ttu-id="08487-202">effets</span><span class="sxs-lookup"><span data-stu-id="08487-202">effects</span></span>  |  <span data-ttu-id="08487-203">302</span><span class="sxs-lookup"><span data-stu-id="08487-203">302</span></span>    |
    |<span data-ttu-id="08487-204">sensation</span><span class="sxs-lookup"><span data-stu-id="08487-204">feeling</span></span>  |  <span data-ttu-id="08487-205">547</span><span class="sxs-lookup"><span data-stu-id="08487-205">547</span></span>    |

    <span data-ttu-id="08487-206">Ajoutez le code ci-dessous pour créer le mappage de recherche :</span><span class="sxs-lookup"><span data-stu-id="08487-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="08487-207">Ajoutez un `Action` pour redimensionner le tableau d’entiers de longueur variable en un tableau d’entiers de taille fixe, avec les lignes de code suivantes :</span><span class="sxs-lookup"><span data-stu-id="08487-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="08487-208">Charger le modèle TensorFlow pré-formé</span><span class="sxs-lookup"><span data-stu-id="08487-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="08487-209">Ajoutez du code pour charger le modèle TensorFlow :</span><span class="sxs-lookup"><span data-stu-id="08487-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="08487-210">Une fois le modèle chargé, vous pouvez extraire son schéma d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="08487-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="08487-211">Les schémas sont affichés pour l’intérêt et l’apprentissage uniquement.</span><span class="sxs-lookup"><span data-stu-id="08487-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="08487-212">Vous n’avez pas besoin de ce code pour que l’application finale fonctionne :</span><span class="sxs-lookup"><span data-stu-id="08487-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="08487-213">Le schéma d’entrée est le tableau de longueur fixe des mots encodés entier.</span><span class="sxs-lookup"><span data-stu-id="08487-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="08487-214">Le schéma de sortie est un tableau de probabilités de type float indiquant si le sentiment d’un avis est négatif ou positif.</span><span class="sxs-lookup"><span data-stu-id="08487-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="08487-215">Ces valeurs sont additionnées à 1, car la probabilité d’être positive est le complément de la probabilité que le sentiment soit négatif.</span><span class="sxs-lookup"><span data-stu-id="08487-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="08487-216">Créer le pipeline ML.NET</span><span class="sxs-lookup"><span data-stu-id="08487-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="08487-217">Créez le pipeline et fractionnez le texte d’entrée en mots à l’aide de la transformation [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) pour scinder le texte en mots en tant que ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="08487-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="08487-218">La transformation [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) utilise des espaces pour analyser le texte/la chaîne en mots.</span><span class="sxs-lookup"><span data-stu-id="08487-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="08487-219">Elle crée une nouvelle colonne et fractionne chaque chaîne d’entrée en un vecteur de sous-chaînes en fonction du séparateur défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="08487-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="08487-220">Mappez les mots sur leur encodage entier à l’aide de la table de recherche que vous avez déclarée ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="08487-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="08487-221">Redimensionnez les encodages d’entiers de longueur variable à la longueur fixe requise par le modèle :</span><span class="sxs-lookup"><span data-stu-id="08487-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="08487-222">Classification de l’entrée avec le modèle TensorFlow chargé :</span><span class="sxs-lookup"><span data-stu-id="08487-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="08487-223">La sortie du modèle TensorFlow est `Prediction/Softmax`appelée.</span><span class="sxs-lookup"><span data-stu-id="08487-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="08487-224">Notez que le nom `Prediction/Softmax` est déterminé par le modèle TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="08487-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="08487-225">Vous ne pouvez pas modifier ce nom.</span><span class="sxs-lookup"><span data-stu-id="08487-225">You cannot change this name.</span></span>

1. <span data-ttu-id="08487-226">Créez une nouvelle colonne pour la prédiction de sortie :</span><span class="sxs-lookup"><span data-stu-id="08487-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="08487-227">Vous devez copier la `Prediction/Softmax` colonne dans un nom qui peut être utilisé en tant que propriété dans une C# classe : `Prediction`.</span><span class="sxs-lookup"><span data-stu-id="08487-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="08487-228">Le `/` caractère n’est pas autorisé dans C# un nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="08487-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="08487-229">Créer le modèle ML.NET à partir du pipeline</span><span class="sxs-lookup"><span data-stu-id="08487-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="08487-230">Ajoutez le code pour créer le modèle à partir du pipeline :</span><span class="sxs-lookup"><span data-stu-id="08487-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]  

    <span data-ttu-id="08487-231">Un modèle ml.net est créé à partir de la chaîne d’estimateurs dans le pipeline `Fit` en appelant la méthode.</span><span class="sxs-lookup"><span data-stu-id="08487-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="08487-232">Dans ce cas, nous n’ajustons aucune donnée pour créer le modèle, car le modèle TensorFlow a déjà été formé précédemment.</span><span class="sxs-lookup"><span data-stu-id="08487-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="08487-233">Nous fournissons un objet de vue de données vide pour répondre aux `Fit` exigences de la méthode.</span><span class="sxs-lookup"><span data-stu-id="08487-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="08487-234">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="08487-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="08487-235">Ajoutez la `PredictSentiment` méthode en dessous `Main` de la méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
        public static void PredictSentiment(MLContext mlContext, ITransformer model)
        {

        }
    ```

1. <span data-ttu-id="08487-236">Ajoutez le code suivant pour créer le `PredictionEngine` en tant que première ligne de `PredictSentiment()` la méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="08487-237">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="08487-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to make a prediction on a single instance of data.</span></span>

1. <span data-ttu-id="08487-238">Ajoutez un commentaire pour tester la prédiction du modèle formé dans la méthode `Predict()` en créant une instance de `MovieReview` :</span><span class="sxs-lookup"><span data-stu-id="08487-238">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="08487-239">Transmettez les données de commentaire de `Prediction Engine` test au en ajoutant les lignes de code suivantes `PredictSentiment()` dans la méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-239">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="08487-240">La fonction [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) effectue une prédiction sur une seule ligne de données :</span><span class="sxs-lookup"><span data-stu-id="08487-240">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="08487-241">Propriété</span><span class="sxs-lookup"><span data-stu-id="08487-241">Property</span></span>| <span data-ttu-id="08487-242">Valeur</span><span class="sxs-lookup"><span data-stu-id="08487-242">Value</span></span>|<span data-ttu-id="08487-243">Type</span><span class="sxs-lookup"><span data-stu-id="08487-243">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="08487-244">Prédiction</span><span class="sxs-lookup"><span data-stu-id="08487-244">Prediction</span></span>|<span data-ttu-id="08487-245">[0,5459937, 0,454006255]</span><span class="sxs-lookup"><span data-stu-id="08487-245">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="08487-246">float []</span><span class="sxs-lookup"><span data-stu-id="08487-246">float[]</span></span>|

1. <span data-ttu-id="08487-247">Affichez le sentiment de prédiction à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="08487-247">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="08487-248">Ajoutez un appel à `PredictSentiment` à la fin de la `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="08487-248">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="08487-249">Résultats</span><span class="sxs-lookup"><span data-stu-id="08487-249">Results</span></span>

<span data-ttu-id="08487-250">Générez et exécutez votre application.</span><span class="sxs-lookup"><span data-stu-id="08487-250">Build and run your application.</span></span>

<span data-ttu-id="08487-251">Vos résultats doivent être similaires à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="08487-251">Your results should be similar to the following.</span></span> <span data-ttu-id="08487-252">Durant le processus, des messages sont affichés.</span><span class="sxs-lookup"><span data-stu-id="08487-252">During processing, messages are displayed.</span></span> <span data-ttu-id="08487-253">Vous pouvez voir des avertissements ou des messages de traitement.</span><span class="sxs-lookup"><span data-stu-id="08487-253">You may see warnings, or processing messages.</span></span> <span data-ttu-id="08487-254">Ces messages ont été supprimés des résultats suivants par souci de clarté.</span><span class="sxs-lookup"><span data-stu-id="08487-254">These messages have been removed from the following results for clarity.</span></span>

```console
   Number of classes: 2
   Is sentiment/review positive ? Yes
```

<span data-ttu-id="08487-255">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="08487-255">Congratulations!</span></span> <span data-ttu-id="08487-256">Vous avez maintenant correctement créé un modèle de machine learning pour classer et prédire les sentiments de messages en réutilisant un modèle `TensorFlow` pré-formé dans ml.net.</span><span class="sxs-lookup"><span data-stu-id="08487-256">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="08487-257">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF).</span><span class="sxs-lookup"><span data-stu-id="08487-257">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="08487-258">Dans ce tutoriel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="08487-258">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="08487-259">Charger un modèle TensorFlow pré-formé</span><span class="sxs-lookup"><span data-stu-id="08487-259">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="08487-260">Transformer le texte de commentaire de site Web en fonctionnalités adaptées au modèle</span><span class="sxs-lookup"><span data-stu-id="08487-260">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="08487-261">Utiliser le modèle pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="08487-261">Use the model to make a prediction</span></span>
