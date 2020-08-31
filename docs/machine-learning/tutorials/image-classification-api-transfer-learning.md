---
title: 'Didacticiel : inspection visuelle automatisée à l’aide de l’apprentissage de transfert'
description: Ce didacticiel explique comment utiliser l’apprentissage de transfert pour former un modèle d’apprentissage profond TensorFlow dans ML.NET à l’aide de l’API de détection d’images pour classer les images de surfaces concrètes comme fissurées ou non fissurées.
author: luisquintanilla
ms.author: luquinta
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 593897b31c86e79db2376dde94f3e5c87fdf8289
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89052821"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="217c9-103">Didacticiel : inspection visuelle automatisée à l’aide de l’apprentissage de transfert avec l’API de classification d’image ML.NET</span><span class="sxs-lookup"><span data-stu-id="217c9-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="217c9-104">Apprenez à former un modèle d’apprentissage approfondi personnalisé à l’aide de l’apprentissage de transfert, un modèle TensorFlow préformé et l’API de classification d’image ML.NET pour classer les images de surfaces concrètes comme fissurées ou non.</span><span class="sxs-lookup"><span data-stu-id="217c9-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="217c9-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="217c9-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="217c9-106">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="217c9-106">Understand the problem</span></span>
> - <span data-ttu-id="217c9-107">En savoir plus sur l’API de classification d’image ML.NET</span><span class="sxs-lookup"><span data-stu-id="217c9-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="217c9-108">Comprendre le modèle préformé</span><span class="sxs-lookup"><span data-stu-id="217c9-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="217c9-109">Utilisation de l’apprentissage de transfert pour l’apprentissage d’un modèle de classification d’image TensorFlow personnalisé</span><span class="sxs-lookup"><span data-stu-id="217c9-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="217c9-110">Classer les images avec le modèle personnalisé</span><span class="sxs-lookup"><span data-stu-id="217c9-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="217c9-111">Prérequis</span><span class="sxs-lookup"><span data-stu-id="217c9-111">Prerequisites</span></span>

- <span data-ttu-id="217c9-112">[Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou version ultérieure ou visual studio 2017 version 15,6 ou ultérieure avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="217c9-112">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or later or Visual Studio 2017 version 15.6 or later with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="217c9-113">Vue d’ensemble de l’exemple d’apprentissage de transfert de classification d’image</span><span class="sxs-lookup"><span data-stu-id="217c9-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="217c9-114">Cet exemple est une application console C# .NET Core qui classe les images à l’aide d’un modèle TensorFlow d’apprentissage profond préformé.</span><span class="sxs-lookup"><span data-stu-id="217c9-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="217c9-115">Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="217c9-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="217c9-116">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="217c9-116">Understand the problem</span></span>

<span data-ttu-id="217c9-117">La classification d’images est un problème de vision par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="217c9-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="217c9-118">La classification d’image prend une image en tant qu’entrée et la classe dans une classe prescrite.</span><span class="sxs-lookup"><span data-stu-id="217c9-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="217c9-119">Voici quelques scénarios où la classification d’images est utile :</span><span class="sxs-lookup"><span data-stu-id="217c9-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="217c9-120">Reconnaissance faciale</span><span class="sxs-lookup"><span data-stu-id="217c9-120">Facial recognition</span></span>
- <span data-ttu-id="217c9-121">Détection d’émotions</span><span class="sxs-lookup"><span data-stu-id="217c9-121">Emotion detection</span></span>
- <span data-ttu-id="217c9-122">Diagnostic médical</span><span class="sxs-lookup"><span data-stu-id="217c9-122">Medical diagnosis</span></span>
- <span data-ttu-id="217c9-123">Détection du repère géographique</span><span class="sxs-lookup"><span data-stu-id="217c9-123">Landmark detection</span></span>

<span data-ttu-id="217c9-124">Ce didacticiel forme un modèle de classification d’image personnalisé pour effectuer une inspection visuelle automatisée des ponts de pont afin d’identifier les structures qui sont endommagées par des fissures.</span><span class="sxs-lookup"><span data-stu-id="217c9-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="217c9-125">API de classification d’image ML.NET</span><span class="sxs-lookup"><span data-stu-id="217c9-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="217c9-126">ML.NET fournit différentes façons d’effectuer la classification des images.</span><span class="sxs-lookup"><span data-stu-id="217c9-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="217c9-127">Ce didacticiel applique l’apprentissage de transfert à l’aide de l’API de classification d’image.</span><span class="sxs-lookup"><span data-stu-id="217c9-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="217c9-128">L’API de classification d’image utilise [TensorFlow.net](https://github.com/SciSharp/TensorFlow.NET), une bibliothèque de bas niveau qui fournit des liaisons C# pour l’API C++ TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="217c9-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="217c9-129">Qu’est-ce que l’apprentissage de transfert ?</span><span class="sxs-lookup"><span data-stu-id="217c9-129">What is transfer learning?</span></span>

<span data-ttu-id="217c9-130">Le transfert d’apprentissage applique les connaissances acquises en résolvant un problème à un autre problème.</span><span class="sxs-lookup"><span data-stu-id="217c9-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="217c9-131">La formation d’un modèle d’apprentissage profond à partir de zéro requiert la définition de plusieurs paramètres, une grande quantité de données d’apprentissage étiquetées et une grande quantité de ressources de calcul (des centaines d’heures GPU).</span><span class="sxs-lookup"><span data-stu-id="217c9-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="217c9-132">L’utilisation d’un modèle préformé et de l’apprentissage de transfert vous permet de raccourcir le processus de formation.</span><span class="sxs-lookup"><span data-stu-id="217c9-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="217c9-133">Processus d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="217c9-133">Training process</span></span>

<span data-ttu-id="217c9-134">L’API de classification d’image démarre le processus d’apprentissage en chargeant un modèle TensorFlow préformé.</span><span class="sxs-lookup"><span data-stu-id="217c9-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="217c9-135">Le processus d’apprentissage se compose de deux étapes :</span><span class="sxs-lookup"><span data-stu-id="217c9-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="217c9-136">Phase de goulot d’étranglement</span><span class="sxs-lookup"><span data-stu-id="217c9-136">Bottleneck phase</span></span>
2. <span data-ttu-id="217c9-137">Phase de formation</span><span class="sxs-lookup"><span data-stu-id="217c9-137">Training phase</span></span>

![Étapes de formation](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="217c9-139">Phase de goulot d’étranglement</span><span class="sxs-lookup"><span data-stu-id="217c9-139">Bottleneck phase</span></span>

<span data-ttu-id="217c9-140">Pendant la phase de goulot d’étranglement, l’ensemble des images de formation est chargé et les valeurs de pixel sont utilisées comme entrées ou caractéristiques pour les couches figées du modèle préformé.</span><span class="sxs-lookup"><span data-stu-id="217c9-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="217c9-141">Les couches figées incluent toutes les couches du réseau neuronal jusqu’à l’avant-dernière couche, de manière informellement connue sous le nom de couche de goulot d’étranglement.</span><span class="sxs-lookup"><span data-stu-id="217c9-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="217c9-142">Ces couches sont désignées comme étant figées, car aucune formation ne se produit sur ces couches et les opérations sont directes.</span><span class="sxs-lookup"><span data-stu-id="217c9-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="217c9-143">C’est à ces couches figées où les modèles de niveau inférieur qui aident un modèle à différencier entre les différentes classes sont calculés.</span><span class="sxs-lookup"><span data-stu-id="217c9-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="217c9-144">Plus le nombre de couches est élevé, plus cette étape est gourmande en calculs.</span><span class="sxs-lookup"><span data-stu-id="217c9-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="217c9-145">Heureusement, étant donné qu’il s’agit d’un calcul unique, les résultats peuvent être mis en cache et utilisés ultérieurement lors de l’expérimentation avec des paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="217c9-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="217c9-146">Phase de formation</span><span class="sxs-lookup"><span data-stu-id="217c9-146">Training phase</span></span>

<span data-ttu-id="217c9-147">Une fois les valeurs de sortie de la phase de goulot d’étranglement calculées, elles sont utilisées comme entrée pour reformer la couche finale du modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="217c9-148">Ce processus est itératif et s’exécute pendant le nombre de fois spécifié par les paramètres de modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="217c9-149">Lors de chaque exécution, la perte et la précision sont évaluées.</span><span class="sxs-lookup"><span data-stu-id="217c9-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="217c9-150">Ensuite, les ajustements appropriés sont effectués pour améliorer le modèle avec l’objectif de réduire la perte et d’optimiser la précision.</span><span class="sxs-lookup"><span data-stu-id="217c9-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="217c9-151">Une fois l’apprentissage terminé, deux formats de modèle sont générés.</span><span class="sxs-lookup"><span data-stu-id="217c9-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="217c9-152">L’une d’entre elles est la `.pb` version du modèle et l’autre est la `.zip` version sérialisée ml.net du modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="217c9-153">Quand vous travaillez dans des environnements pris en charge par ML.NET, il est recommandé d’utiliser la `.zip` version du modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="217c9-154">Toutefois, dans les environnements où ML.NET n’est pas pris en charge, vous avez la possibilité d’utiliser la `.pb` version.</span><span class="sxs-lookup"><span data-stu-id="217c9-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="217c9-155">Comprendre le modèle préformé</span><span class="sxs-lookup"><span data-stu-id="217c9-155">Understand the pretrained model</span></span>

<span data-ttu-id="217c9-156">Le modèle préformé utilisé dans ce didacticiel est la variante de couche 101 du modèle de réseau résiduel (ResNet) v2.</span><span class="sxs-lookup"><span data-stu-id="217c9-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="217c9-157">Le modèle d’origine est formé pour classer les images en milliers de catégories.</span><span class="sxs-lookup"><span data-stu-id="217c9-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="217c9-158">Le modèle prend comme entrée une image de taille 224 x 224 et génère les probabilités de la classe pour chacune des classes sur lesquelles il est formé.</span><span class="sxs-lookup"><span data-stu-id="217c9-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="217c9-159">Une partie de ce modèle est utilisée pour l’apprentissage d’un nouveau modèle à l’aide d’images personnalisées pour effectuer des prédictions entre deux classes.</span><span class="sxs-lookup"><span data-stu-id="217c9-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="217c9-160">Création d’une application de console</span><span class="sxs-lookup"><span data-stu-id="217c9-160">Create console application</span></span>

<span data-ttu-id="217c9-161">Maintenant que vous avez une compréhension générale de la formation de transfert et de l’API de classification d’image, il est temps de générer l’application.</span><span class="sxs-lookup"><span data-stu-id="217c9-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="217c9-162">Créez une **application console C# .net Core** appelée « DeepLearning_ImageClassification_Binary ».</span><span class="sxs-lookup"><span data-stu-id="217c9-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="217c9-163">Installez le package NuGet **Microsoft.ml** :</span><span class="sxs-lookup"><span data-stu-id="217c9-163">Install the **Microsoft.ML** NuGet Package:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. <span data-ttu-id="217c9-164">Dans Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez **gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="217c9-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="217c9-165">Choisissez « nuget.org » comme source du package.</span><span class="sxs-lookup"><span data-stu-id="217c9-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="217c9-166">Sélectionnez l’onglet **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="217c9-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="217c9-167">Cochez la case **inclure la version préliminaire** .</span><span class="sxs-lookup"><span data-stu-id="217c9-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="217c9-168">Recherchez **Microsoft.ml**.</span><span class="sxs-lookup"><span data-stu-id="217c9-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="217c9-169">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="217c9-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="217c9-170">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="217c9-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="217c9-171">Répétez ces étapes pour les packages NuGet **Microsoft. ml. vision**, **SciSharp. TensorFlow. Redist**et **Microsoft. ml. ImageAnalytics** .</span><span class="sxs-lookup"><span data-stu-id="217c9-171">Repeat these steps for the **Microsoft.ML.Vision**, **SciSharp.TensorFlow.Redist**, and **Microsoft.ML.ImageAnalytics** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="217c9-172">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="217c9-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="217c9-173">Les jeux de données de ce didacticiel proviennent de Maguire, Marc ; Dorafshan, Sattar; et Thomas, Robert J., « SDNET2018 : jeu de données d’image de piratage concret pour les applications de Machine Learning » (2018).</span><span class="sxs-lookup"><span data-stu-id="217c9-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="217c9-174">Parcourez tous les jeux de données.</span><span class="sxs-lookup"><span data-stu-id="217c9-174">Browse all Datasets.</span></span> <span data-ttu-id="217c9-175">Papier 48.</span><span class="sxs-lookup"><span data-stu-id="217c9-175">Paper 48.</span></span> <https://digitalcommons.usu.edu/all_datasets/48>

<span data-ttu-id="217c9-176">SDNET2018 est un jeu de données d’image qui contient des annotations pour les structures concrètes fissurées et non fissurées (ponts, murs et chaussées de pont).</span><span class="sxs-lookup"><span data-stu-id="217c9-176">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Exemples de jeux de données de pont SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="217c9-178">Les données sont organisées en trois sous-répertoires :</span><span class="sxs-lookup"><span data-stu-id="217c9-178">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="217c9-179">D contient des images de pont de pont</span><span class="sxs-lookup"><span data-stu-id="217c9-179">D contains bridge deck images</span></span>
- <span data-ttu-id="217c9-180">P contient des images de chaussée</span><span class="sxs-lookup"><span data-stu-id="217c9-180">P contains pavement images</span></span>
- <span data-ttu-id="217c9-181">W contient des images de mur</span><span class="sxs-lookup"><span data-stu-id="217c9-181">W contains wall images</span></span>

<span data-ttu-id="217c9-182">Chacun de ces sous-répertoires contient deux sous-répertoires préfixés supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="217c9-182">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="217c9-183">C est le préfixe utilisé pour les surfaces fissurées</span><span class="sxs-lookup"><span data-stu-id="217c9-183">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="217c9-184">U est le préfixe utilisé pour les surfaces non craquées</span><span class="sxs-lookup"><span data-stu-id="217c9-184">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="217c9-185">Dans ce didacticiel, seules les images de pont de pont sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="217c9-185">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="217c9-186">Téléchargez le [jeu de données](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) et décompressez.</span><span class="sxs-lookup"><span data-stu-id="217c9-186">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="217c9-187">Créez un répertoire nommé « ressources » dans votre projet pour enregistrer les fichiers de votre jeu de données.</span><span class="sxs-lookup"><span data-stu-id="217c9-187">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="217c9-188">Copiez les sous-répertoires *CD* et *ud* à partir du répertoire décompressé récemment vers le répertoire *Assets* .</span><span class="sxs-lookup"><span data-stu-id="217c9-188">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="217c9-189">Créer des classes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="217c9-189">Create input and output classes</span></span>

1. <span data-ttu-id="217c9-190">Ouvrez le fichier *Program.cs* et remplacez les `using` instructions existantes en haut du fichier par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="217c9-190">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L1-L7)]

1. <span data-ttu-id="217c9-191">Sous la `Program` classe dans *Program.cs*, créez une classe appelée `ImageData` .</span><span class="sxs-lookup"><span data-stu-id="217c9-191">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="217c9-192">Cette classe est utilisée pour représenter les données initialement chargées.</span><span class="sxs-lookup"><span data-stu-id="217c9-192">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L138-L143)]

    <span data-ttu-id="217c9-193">`ImageData` contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="217c9-193">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="217c9-194">`ImagePath` est le chemin d’accès complet où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="217c9-194">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="217c9-195">`Label` catégorie à laquelle l’image appartient.</span><span class="sxs-lookup"><span data-stu-id="217c9-195">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="217c9-196">Il s’agit de la valeur à prédire.</span><span class="sxs-lookup"><span data-stu-id="217c9-196">This is the value to predict.</span></span>

1. <span data-ttu-id="217c9-197">Créer des classes pour vos données d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="217c9-197">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="217c9-198">Sous la `ImageData` classe, définissez le schéma de vos données d’entrée dans une nouvelle classe appelée `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="217c9-198">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L145-L154)]

        <span data-ttu-id="217c9-199">`ModelInput` contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="217c9-199">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="217c9-200">`Image``byte[]`représentation de l’image.</span><span class="sxs-lookup"><span data-stu-id="217c9-200">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="217c9-201">Le modèle s’attend à ce que les données de l’image soient de ce type pour l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-201">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="217c9-202">`LabelAsKey` représentation numérique de `Label` .</span><span class="sxs-lookup"><span data-stu-id="217c9-202">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="217c9-203">`ImagePath` est le chemin d’accès complet où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="217c9-203">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="217c9-204">`Label` catégorie à laquelle l’image appartient.</span><span class="sxs-lookup"><span data-stu-id="217c9-204">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="217c9-205">Il s’agit de la valeur à prédire.</span><span class="sxs-lookup"><span data-stu-id="217c9-205">This is the value to predict.</span></span>

        <span data-ttu-id="217c9-206">Seuls `Image` et `LabelAsKey` sont utilisés pour l’apprentissage du modèle et la création de prédictions.</span><span class="sxs-lookup"><span data-stu-id="217c9-206">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="217c9-207">Les `ImagePath` `Label` Propriétés et sont conservées par commodité pour accéder au nom et à la catégorie du fichier image d’origine.</span><span class="sxs-lookup"><span data-stu-id="217c9-207">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="217c9-208">Ensuite, sous la `ModelInput` classe, définissez le schéma de vos données de sortie dans une nouvelle classe appelée `ModelOutput` .</span><span class="sxs-lookup"><span data-stu-id="217c9-208">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L156-L163)]

        <span data-ttu-id="217c9-209">`ModelOutput` contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="217c9-209">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="217c9-210">`ImagePath` est le chemin d’accès complet où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="217c9-210">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="217c9-211">`Label` catégorie d’origine à laquelle l’image appartient.</span><span class="sxs-lookup"><span data-stu-id="217c9-211">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="217c9-212">Il s’agit de la valeur à prédire.</span><span class="sxs-lookup"><span data-stu-id="217c9-212">This is the value to predict.</span></span>
        - <span data-ttu-id="217c9-213">`PredictedLabel` valeur prédite par le modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-213">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="217c9-214">Semblable à `ModelInput` , seul `PredictedLabel` est requis pour effectuer des prédictions, car il contient la prédiction effectuée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-214">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="217c9-215">Les `ImagePath` `Label` Propriétés et sont conservées pour plus de commodité afin d’accéder au nom et à la catégorie du fichier image d’origine.</span><span class="sxs-lookup"><span data-stu-id="217c9-215">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="217c9-216">Créer le répertoire de l’espace de travail</span><span class="sxs-lookup"><span data-stu-id="217c9-216">Create workspace directory</span></span>

<span data-ttu-id="217c9-217">Lorsque les données d’apprentissage et de validation ne changent pas souvent, il est recommandé de mettre en cache les valeurs de goulot d’étranglement calculées pour d’autres exécutions.</span><span class="sxs-lookup"><span data-stu-id="217c9-217">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="217c9-218">Dans votre projet, créez un répertoire appelé *espace de travail* pour stocker les valeurs de goulot d’étranglement et la `.pb` version du modèle calculées.</span><span class="sxs-lookup"><span data-stu-id="217c9-218">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="217c9-219">Définir des chemins d’accès et initialiser des variables</span><span class="sxs-lookup"><span data-stu-id="217c9-219">Define paths and initialize variables</span></span>

1. <span data-ttu-id="217c9-220">À l’intérieur de la `Main` méthode, définissez l’emplacement de vos ressources, les valeurs de goulot d’étranglement calculées et `.pb` la version du modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-220">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L15-L17)]

1. <span data-ttu-id="217c9-221">Initialisez la `mlContext` variable avec une nouvelle instance de [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="217c9-221">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L19)]

    <span data-ttu-id="217c9-222">La classe [MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ml.net, et l’initialisation de MLContext crée un nouvel environnement ml.net qui peut être partagé entre les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-222">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="217c9-223">Sur le plan conceptuel, elle est similaire à `DbContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="217c9-223">It's similar, conceptually, to `DbContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="217c9-224">Charger les données</span><span class="sxs-lookup"><span data-stu-id="217c9-224">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="217c9-225">Créer une méthode utilitaire de chargement de données</span><span class="sxs-lookup"><span data-stu-id="217c9-225">Create data loading utility method</span></span>

<span data-ttu-id="217c9-226">Les images sont stockées dans deux sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="217c9-226">The images are stored in two subdirectories.</span></span> <span data-ttu-id="217c9-227">Avant de charger les données, celles-ci doivent être mises en forme dans une liste d' `ImageData` objets.</span><span class="sxs-lookup"><span data-stu-id="217c9-227">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="217c9-228">Pour ce faire, créez la `LoadImagesFromDirectory` méthode en dessous de la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="217c9-228">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="217c9-229">Dans `LoadImagesFromDirectory` , ajoutez le code suivant pour récupérer tous les chemins d’accès aux fichiers à partir des sous-répertoires :</span><span class="sxs-lookup"><span data-stu-id="217c9-229">Inside the `LoadImagesFromDirectory`, add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L105-L106)]

1. <span data-ttu-id="217c9-230">Ensuite, itérez au sein de chacun des fichiers à l’aide d’une `foreach` instruction.</span><span class="sxs-lookup"><span data-stu-id="217c9-230">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="217c9-231">À l’intérieur de l' `foreach` instruction, vérifiez que les extensions de fichier sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="217c9-231">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="217c9-232">L’API de classification d’image prend en charge les formats JPEG et PNG.</span><span class="sxs-lookup"><span data-stu-id="217c9-232">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L110-L111)]

1. <span data-ttu-id="217c9-233">Ensuite, récupérez le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="217c9-233">Then, get the label for the file.</span></span> <span data-ttu-id="217c9-234">Si le `useFolderNameAsLabel` paramètre a la valeur `true` , le répertoire parent dans lequel le fichier est enregistré est utilisé comme étiquette.</span><span class="sxs-lookup"><span data-stu-id="217c9-234">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="217c9-235">Dans le cas contraire, il s’attend à ce que l’étiquette soit un préfixe du nom de fichier ou du nom de fichier lui-même.</span><span class="sxs-lookup"><span data-stu-id="217c9-235">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L113-L127)]

1. <span data-ttu-id="217c9-236">Enfin, créez une nouvelle instance de `ModelInput` .</span><span class="sxs-lookup"><span data-stu-id="217c9-236">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L129-L133)]

### <a name="prepare-the-data"></a><span data-ttu-id="217c9-237">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="217c9-237">Prepare the data</span></span>

1. <span data-ttu-id="217c9-238">De retour dans la `Main` méthode, utilisez la `LoadImagesFromDirectory` méthode utilitaire pour obtenir la liste des images utilisées pour l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-238">Back in the `Main` method, use the `LoadImagesFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L22)]

1. <span data-ttu-id="217c9-239">Ensuite, chargez les images dans un [`IDataView`](xref:Microsoft.ML.IDataView) à l’aide de la [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) méthode.</span><span class="sxs-lookup"><span data-stu-id="217c9-239">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L24)]

1. <span data-ttu-id="217c9-240">Les données sont chargées dans l’ordre dans lequel elles ont été lues à partir des répertoires.</span><span class="sxs-lookup"><span data-stu-id="217c9-240">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="217c9-241">Pour équilibrer les données, vous pouvez les lire à l’aide de la [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) méthode.</span><span class="sxs-lookup"><span data-stu-id="217c9-241">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L26)]

1. <span data-ttu-id="217c9-242">Les modèles d’apprentissage automatique s’attendent à ce que l’entrée soit au format numérique.</span><span class="sxs-lookup"><span data-stu-id="217c9-242">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="217c9-243">Par conséquent, un prétraitement doit être effectué sur les données avant l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-243">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="217c9-244">Créez un [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) composé des [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) `LoadRawImageBytes` transformations et.</span><span class="sxs-lookup"><span data-stu-id="217c9-244">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="217c9-245">La `MapValueToKey` transformation prend la valeur catégorique dans la `Label` colonne, la convertit en une `KeyType` valeur numérique et la stocke dans une nouvelle colonne appelée `LabelAsKey` .</span><span class="sxs-lookup"><span data-stu-id="217c9-245">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="217c9-246">Le `LoadImages` prend les valeurs de la `ImagePath` colonne avec le `imageFolder` paramètre pour charger des images pour l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-246">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L28-L34)]

1. <span data-ttu-id="217c9-247">Utilisez la [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) méthode pour appliquer les données à l' `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) suivie de la [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) méthode, qui retourne un [`IDataView`](xref:Microsoft.ML.IDataView) contenant les données prétraitées.</span><span class="sxs-lookup"><span data-stu-id="217c9-247">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L36-L38)]

1. <span data-ttu-id="217c9-248">Pour effectuer l’apprentissage d’un modèle, il est important de disposer d’un jeu de données d’apprentissage, ainsi que d’un jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="217c9-248">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="217c9-249">Le modèle est formé dans le jeu d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-249">The model is trained on the training set.</span></span> <span data-ttu-id="217c9-250">La façon dont il effectue des prédictions sur les données invisibles est mesurée en fonction des performances par rapport au jeu de validation.</span><span class="sxs-lookup"><span data-stu-id="217c9-250">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="217c9-251">En fonction des résultats de ces performances, le modèle apporte des ajustements à ce qu’il a appris dans un effort d’amélioration.</span><span class="sxs-lookup"><span data-stu-id="217c9-251">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="217c9-252">Le jeu de validation peut provenir soit du fractionnement de votre jeu de données d’origine, soit d’une autre source qui a déjà été réservée à cet effet.</span><span class="sxs-lookup"><span data-stu-id="217c9-252">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="217c9-253">Dans ce cas, le jeu de données préalablement traité est divisé en jeux d’apprentissage, de validation et de test.</span><span class="sxs-lookup"><span data-stu-id="217c9-253">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L40-L41)]

    <span data-ttu-id="217c9-254">L’exemple de code ci-dessus effectue deux fractionnements.</span><span class="sxs-lookup"><span data-stu-id="217c9-254">The code sample above performs two splits.</span></span> <span data-ttu-id="217c9-255">Tout d’abord, les données prétraitées sont fractionnées et 70% est utilisé pour l’apprentissage, tandis que les 30% restants sont utilisés pour la validation.</span><span class="sxs-lookup"><span data-stu-id="217c9-255">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="217c9-256">Le jeu de validation de 30% est ensuite divisé en jeux de validation et de test où 90% est utilisé pour la validation et 10% sont utilisés pour le test.</span><span class="sxs-lookup"><span data-stu-id="217c9-256">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="217c9-257">Un moyen de réfléchir à l’objectif de ces partitions de données consiste à effectuer un examen.</span><span class="sxs-lookup"><span data-stu-id="217c9-257">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="217c9-258">Lorsque vous étudiez un examen, vous examinez vos notes, livres ou autres ressources pour comprendre les concepts qui sont à l’examen.</span><span class="sxs-lookup"><span data-stu-id="217c9-258">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="217c9-259">Il s’agit de ce à quoi sert l’ensemble de rames.</span><span class="sxs-lookup"><span data-stu-id="217c9-259">This is what the train set is for.</span></span> <span data-ttu-id="217c9-260">Ensuite, vous pouvez effectuer un examen fictif pour valider vos connaissances.</span><span class="sxs-lookup"><span data-stu-id="217c9-260">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="217c9-261">C’est là que le jeu de validation est utile.</span><span class="sxs-lookup"><span data-stu-id="217c9-261">This is where the validation set comes in handy.</span></span> <span data-ttu-id="217c9-262">Vous souhaitez vérifier si vous avez une bonne compréhension des concepts avant d’effectuer l’examen réel.</span><span class="sxs-lookup"><span data-stu-id="217c9-262">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="217c9-263">En fonction de ces résultats, vous prenez note de ce que vous avez trouvé ou que vous n’avez pas bien compris et incorporez vos modifications à mesure que vous l’examinez pour l’examen réel.</span><span class="sxs-lookup"><span data-stu-id="217c9-263">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="217c9-264">Enfin, vous prenez l’examen.</span><span class="sxs-lookup"><span data-stu-id="217c9-264">Finally, you take the exam.</span></span> <span data-ttu-id="217c9-265">C’est pour cela que le jeu de test est utilisé.</span><span class="sxs-lookup"><span data-stu-id="217c9-265">This is what the test set is used for.</span></span> <span data-ttu-id="217c9-266">Vous n’avez jamais vu les questions qui sont à l’examen et utilisez maintenant ce que vous avez appris de la formation et de la validation pour appliquer vos connaissances à la tâche en cours.</span><span class="sxs-lookup"><span data-stu-id="217c9-266">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="217c9-267">Affectez les partitions à leurs valeurs respectives pour les données d’apprentissage, de validation et de test.</span><span class="sxs-lookup"><span data-stu-id="217c9-267">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L43-L45)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="217c9-268">Définir le pipeline d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="217c9-268">Define the training pipeline</span></span>

<span data-ttu-id="217c9-269">L’apprentissage du modèle se compose de deux étapes.</span><span class="sxs-lookup"><span data-stu-id="217c9-269">Model training consists of a couple of steps.</span></span> <span data-ttu-id="217c9-270">Tout d’abord, l’API de classification d’image est utilisée pour l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-270">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="217c9-271">Ensuite, les étiquettes encodées dans la `PredictedLabel` colonne sont reconverties en leur valeur catégorique d’origine à l’aide de la `MapKeyToValue` transformation.</span><span class="sxs-lookup"><span data-stu-id="217c9-271">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="217c9-272">Créez une variable pour stocker un ensemble de paramètres obligatoires et facultatifs pour un `ImageClassificationTrainer` .</span><span class="sxs-lookup"><span data-stu-id="217c9-272">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L47-L58)]

    <span data-ttu-id="217c9-273">Un `ImageClassificationTrainer` prend plusieurs paramètres facultatifs :</span><span class="sxs-lookup"><span data-stu-id="217c9-273">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="217c9-274">`FeatureColumnName` colonne utilisée comme entrée pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-274">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="217c9-275">`LabelColumnName` colonne de la valeur à prédire.</span><span class="sxs-lookup"><span data-stu-id="217c9-275">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="217c9-276">`ValidationSet`[`IDataView`](xref:Microsoft.ML.IDataView)contient les données de validation.</span><span class="sxs-lookup"><span data-stu-id="217c9-276">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="217c9-277">`Arch` définit les architectures de modèle préformées à utiliser.</span><span class="sxs-lookup"><span data-stu-id="217c9-277">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="217c9-278">Ce didacticiel utilise la variante de couche 101 du modèle ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="217c9-278">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="217c9-279">`MetricsCallback` lie une fonction pour suivre la progression au cours de l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-279">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="217c9-280">`TestOnTrainSet` indique au modèle de mesurer les performances par rapport au jeu d’apprentissage quand aucun jeu de validation n’est présent.</span><span class="sxs-lookup"><span data-stu-id="217c9-280">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="217c9-281">`ReuseTrainSetBottleneckCachedValues` indique au modèle s’il faut utiliser les valeurs mises en cache à partir de la phase de goulot d’étranglement lors des exécutions suivantes.</span><span class="sxs-lookup"><span data-stu-id="217c9-281">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="217c9-282">La phase de goulot d’étranglement est un calcul direct unique qui exige beaucoup de ressources de calcul la première fois qu’il est exécuté.</span><span class="sxs-lookup"><span data-stu-id="217c9-282">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="217c9-283">Si les données d’apprentissage ne changent pas et que vous souhaitez expérimenter à l’aide d’un nombre d’époques ou d’une taille de lot différent, l’utilisation de valeurs mises en cache réduit considérablement le temps nécessaire pour l’apprentissage d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-283">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="217c9-284">`ReuseValidationSetBottleneckCachedValues` est semblable `ReuseTrainSetBottleneckCachedValues` uniquement à celui-ci dans le cas présent, il s’agit du jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="217c9-284">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="217c9-285">`WorkspacePath` définit le répertoire dans lequel stocker les valeurs de goulot d’étranglement et la `.pb` version du modèle calculées.</span><span class="sxs-lookup"><span data-stu-id="217c9-285">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="217c9-286">Définissez le [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) pipeline d’apprentissage qui se compose des éléments `mapLabelEstimator` et `ImageClassificationTrainer` .</span><span class="sxs-lookup"><span data-stu-id="217c9-286">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L60-L61)]

1. <span data-ttu-id="217c9-287">Utilisez la [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) méthode pour effectuer l’apprentissage de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-287">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L63)]

## <a name="use-the-model"></a><span data-ttu-id="217c9-288">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="217c9-288">Use the model</span></span>

<span data-ttu-id="217c9-289">Maintenant que vous avez formé votre modèle, il est temps de l’utiliser pour classifier les images.</span><span class="sxs-lookup"><span data-stu-id="217c9-289">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="217c9-290">Sous la `Main` méthode, créez une nouvelle méthode utilitaire appelée `OutputPrediction` pour afficher les informations de prédiction dans la console.</span><span class="sxs-lookup"><span data-stu-id="217c9-290">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L97-L101)]

### <a name="classify-a-single-image"></a><span data-ttu-id="217c9-291">Classer une seule image</span><span class="sxs-lookup"><span data-stu-id="217c9-291">Classify a single image</span></span>

1. <span data-ttu-id="217c9-292">Ajoutez une nouvelle méthode appelée `ClassifySingleImage` sous la `Main` méthode pour créer et générer une prédiction d’image unique.</span><span class="sxs-lookup"><span data-stu-id="217c9-292">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="217c9-293">Créez un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) à l’intérieur de la `ClassifySingleImage` méthode.</span><span class="sxs-lookup"><span data-stu-id="217c9-293">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="217c9-294">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)Est une API pratique, qui vous permet de transmettre et d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="217c9-294">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L74)]

1. <span data-ttu-id="217c9-295">Pour accéder à une `ModelInput` instance unique, convertissez le `data` [`IDataView`](xref:Microsoft.ML.IDataView) en un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) à l’aide de la [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) méthode, puis récupérez la première observation.</span><span class="sxs-lookup"><span data-stu-id="217c9-295">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L76)]

1. <span data-ttu-id="217c9-296">Utilisez la [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) méthode pour classifier l’image.</span><span class="sxs-lookup"><span data-stu-id="217c9-296">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L78)]

1. <span data-ttu-id="217c9-297">Sortie de la prédiction de la console avec la `OutputPrediction` méthode.</span><span class="sxs-lookup"><span data-stu-id="217c9-297">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L80-L81)]

1. <span data-ttu-id="217c9-298">À l’intérieur de la `Main` méthode, appelez `ClassifySingleImage` à l’aide du jeu de test d’images.</span><span class="sxs-lookup"><span data-stu-id="217c9-298">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L65)]

### <a name="classify-multiple-images"></a><span data-ttu-id="217c9-299">Classer plusieurs images</span><span class="sxs-lookup"><span data-stu-id="217c9-299">Classify multiple images</span></span>

1. <span data-ttu-id="217c9-300">Ajoutez une nouvelle méthode appelée `ClassifyImages` sous la `ClassifySingleImage` méthode pour créer et générer plusieurs prédictions d’image.</span><span class="sxs-lookup"><span data-stu-id="217c9-300">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="217c9-301">Créez un [`IDataView`](xref:Microsoft.ML.IDataView) contenant les prédictions à l’aide de la [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) méthode.</span><span class="sxs-lookup"><span data-stu-id="217c9-301">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="217c9-302">Ajoutez le code suivant dans la méthode `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="217c9-302">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L86)]

1. <span data-ttu-id="217c9-303">Pour itérer au sein des prédictions, convertissez le `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) en un [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) à l’aide de la [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) méthode, puis récupérez les 10 premières observations.</span><span class="sxs-lookup"><span data-stu-id="217c9-303">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L88)]

1. <span data-ttu-id="217c9-304">Itère et génère les étiquettes d’origine et prédites pour les prédictions.</span><span class="sxs-lookup"><span data-stu-id="217c9-304">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L90-L94)]

1. <span data-ttu-id="217c9-305">Enfin, à l’intérieur de la `Main` méthode, appelez `ClassifyImages` à l’aide du jeu de test d’images.</span><span class="sxs-lookup"><span data-stu-id="217c9-305">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification/Program.cs#L67)]

## <a name="run-the-application"></a><span data-ttu-id="217c9-306">Exécution de l'application</span><span class="sxs-lookup"><span data-stu-id="217c9-306">Run the application</span></span>

<span data-ttu-id="217c9-307">Exécutez votre application console.</span><span class="sxs-lookup"><span data-stu-id="217c9-307">Run your console app.</span></span> <span data-ttu-id="217c9-308">La sortie doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="217c9-308">The output should be similar to that below.</span></span> <span data-ttu-id="217c9-309">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="217c9-309">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="217c9-310">Par souci de concision, la sortie a été condensée.</span><span class="sxs-lookup"><span data-stu-id="217c9-310">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="217c9-311">**Phase de goulot d’étranglement**</span><span class="sxs-lookup"><span data-stu-id="217c9-311">**Bottleneck phase**</span></span>

<span data-ttu-id="217c9-312">Aucune valeur n’est imprimée pour le nom de l’image car les images sont chargées par `byte[]` conséquent, il n’y a pas de nom d’image à afficher.</span><span class="sxs-lookup"><span data-stu-id="217c9-312">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="217c9-313">**Phase de formation**</span><span class="sxs-lookup"><span data-stu-id="217c9-313">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="217c9-314">**Résultat de la classification des images**</span><span class="sxs-lookup"><span data-stu-id="217c9-314">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="217c9-315">Lors de l’inspection de l’image *7001-220.jpg* , vous pouvez constater qu’elle n’est pas piratée.</span><span class="sxs-lookup"><span data-stu-id="217c9-315">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Image du jeu de données SDNET2018 utilisée pour la prédiction](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="217c9-317">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="217c9-317">Congratulations!</span></span> <span data-ttu-id="217c9-318">Vous avez maintenant créé avec succès un modèle d’apprentissage profond pour la classification des images.</span><span class="sxs-lookup"><span data-stu-id="217c9-318">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="217c9-319">Améliorer le modèle</span><span class="sxs-lookup"><span data-stu-id="217c9-319">Improve the model</span></span>

<span data-ttu-id="217c9-320">Si vous n’êtes pas satisfait des résultats de votre modèle, vous pouvez essayer d’améliorer ses performances en essayant certaines des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="217c9-320">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="217c9-321">**Plus de données**: plus d’exemples d’apprentissage d’un modèle, mieux c’est.</span><span class="sxs-lookup"><span data-stu-id="217c9-321">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="217c9-322">Téléchargez le [jeu de données SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) complet et utilisez-le pour effectuer l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="217c9-322">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="217c9-323">**Augmenter les données**: une technique courante pour ajouter de la diversité aux données consiste à augmenter les données en acceptant une image et en appliquant des transformations différentes (rotation, retournement, déplacement, rognage).</span><span class="sxs-lookup"><span data-stu-id="217c9-323">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="217c9-324">Cela permet d’obtenir des exemples variés pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-324">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="217c9-325">**Formation pour une durée plus longue**: plus vous exercez de temps, plus le modèle est ajusté.</span><span class="sxs-lookup"><span data-stu-id="217c9-325">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="217c9-326">L’augmentation du nombre d’époques peut améliorer les performances de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="217c9-326">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="217c9-327">**Expérimentez avec les hyperparamètres**: en plus des paramètres utilisés dans ce didacticiel, d’autres paramètres peuvent être réglés pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="217c9-327">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="217c9-328">La modification du taux d’apprentissage, qui détermine l’amplitude des mises à jour apportées au modèle après chaque époque peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="217c9-328">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="217c9-329">**Utilisez une architecture de modèle différente**: selon l’aspect de vos données, le modèle qui peut mieux apprendre ses fonctionnalités peut être différent.</span><span class="sxs-lookup"><span data-stu-id="217c9-329">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="217c9-330">Si vous n’êtes pas satisfait des performances de votre modèle, essayez de modifier l’architecture.</span><span class="sxs-lookup"><span data-stu-id="217c9-330">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="217c9-331">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="217c9-331">Additional Resources</span></span>

- <span data-ttu-id="217c9-332">[Apprentissage profond et machine learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="217c9-332">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="217c9-333">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="217c9-333">Next steps</span></span>

<span data-ttu-id="217c9-334">Dans ce didacticiel, vous avez appris à créer un modèle d’apprentissage profond personnalisé à l’aide de l’apprentissage de transfert, d’un modèle TensorFlow de classification d’image préformée et de l’API de classification d’image ML.NET pour classer les images de surfaces concrètes comme fissurées ou non.</span><span class="sxs-lookup"><span data-stu-id="217c9-334">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="217c9-335">Passez au tutoriel suivant pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="217c9-335">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="217c9-336">Détection d’objets</span><span class="sxs-lookup"><span data-stu-id="217c9-336">Object Detection</span></span>](object-detection-onnx.md)
