---
title: 'Tutorial: Inspection visuelle automatisée à l’aide de l’apprentissage de transfert'
description: Ce tutoriel illustre comment utiliser l’apprentissage de transfert pour former un modèle d’apprentissage profond TensorFlow dans ML.NET en utilisant l’API de détection d’image pour classer les images de surfaces en béton comme fissurés ou non fissurés.
author: luisquintanilla
ms.author: luquinta
ms.date: 12/12/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 2dfa3cdab9de47b55f7a3f73f0d6e9460390700c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76920101"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="70f77-103">Tutorial: Inspection visuelle automatisée à l’aide de l’apprentissage de transfert avec l’API de classification des images ML.NET</span><span class="sxs-lookup"><span data-stu-id="70f77-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="70f77-104">Apprenez à former un modèle d’apprentissage profond personnalisé à l’aide de l’apprentissage de transfert, un modèle TensorFlow préentraîné et l’API de classification d’image ML.NET pour classer les images de surfaces en béton comme fissurées ou non.</span><span class="sxs-lookup"><span data-stu-id="70f77-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="70f77-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="70f77-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="70f77-106">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="70f77-106">Understand the problem</span></span>
> - <span data-ttu-id="70f77-107">En savoir plus sur ML.NET’API de classification d’image</span><span class="sxs-lookup"><span data-stu-id="70f77-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="70f77-108">Comprendre le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="70f77-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="70f77-109">Utiliser l’apprentissage de transfert pour former un modèle personnalisé de classification d’image TensorFlow</span><span class="sxs-lookup"><span data-stu-id="70f77-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="70f77-110">Classer les images avec le modèle personnalisé</span><span class="sxs-lookup"><span data-stu-id="70f77-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="70f77-111">Conditions préalables requises</span><span class="sxs-lookup"><span data-stu-id="70f77-111">Prerequisites</span></span>

- <span data-ttu-id="70f77-112">[Visual Studio 2017 version 15.6 ou plus tard](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec le ".NET Core cross-platform development" charge de travail installé.</span><span class="sxs-lookup"><span data-stu-id="70f77-112">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="70f77-113">Aperçu de l’échantillon d’apprentissage de transfert de classification d’image</span><span class="sxs-lookup"><span data-stu-id="70f77-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="70f77-114">Cet exemple est une application de console C .NET Core qui classe les images à l’aide d’un modèle TensorFlow d’apprentissage profond préentraîné.</span><span class="sxs-lookup"><span data-stu-id="70f77-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="70f77-115">Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="70f77-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="70f77-116">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="70f77-116">Understand the problem</span></span>

<span data-ttu-id="70f77-117">La classification d’image est un problème de vision par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="70f77-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="70f77-118">La classification des images prend une image comme entrée et la classe dans une classe prescrite.</span><span class="sxs-lookup"><span data-stu-id="70f77-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="70f77-119">Voici quelques scénarios où la classification des images est utile :</span><span class="sxs-lookup"><span data-stu-id="70f77-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="70f77-120">Reconnaissance faciale</span><span class="sxs-lookup"><span data-stu-id="70f77-120">Facial recognition</span></span>
- <span data-ttu-id="70f77-121">Détection d’émotions</span><span class="sxs-lookup"><span data-stu-id="70f77-121">Emotion detection</span></span>
- <span data-ttu-id="70f77-122">Diagnostic médical</span><span class="sxs-lookup"><span data-stu-id="70f77-122">Medical diagnosis</span></span>
- <span data-ttu-id="70f77-123">Détection historique</span><span class="sxs-lookup"><span data-stu-id="70f77-123">Landmark detection</span></span>

<span data-ttu-id="70f77-124">Ce tutoriel forme un modèle personnalisé de classification d’image pour effectuer l’inspection visuelle automatisée des ponts pour identifier les structures qui sont endommagées par les fissures.</span><span class="sxs-lookup"><span data-stu-id="70f77-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="70f77-125">ML.NET Image Classification API</span><span class="sxs-lookup"><span data-stu-id="70f77-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="70f77-126">ML.NET fournit différentes façons d’effectuer la classification des images.</span><span class="sxs-lookup"><span data-stu-id="70f77-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="70f77-127">Ce tutoriel applique l’apprentissage de transfert à l’aide de l’API de classification d’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="70f77-128">L’API de classification d’image utilise [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), une bibliothèque de bas niveau qui fournit des liaisons CMD pour l’API TensorFlow CMD.</span><span class="sxs-lookup"><span data-stu-id="70f77-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="70f77-129">Qu’est-ce que l’apprentissage par transfert ?</span><span class="sxs-lookup"><span data-stu-id="70f77-129">What is transfer learning?</span></span>

<span data-ttu-id="70f77-130">L’apprentissage de transfert applique les connaissances acquises en résolvant un problème à un autre problème connexe.</span><span class="sxs-lookup"><span data-stu-id="70f77-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="70f77-131">La formation d’un modèle d’apprentissage profond à partir de zéro nécessite de définir plusieurs paramètres, une grande quantité de données de formation étiquetées, et une grande quantité de ressources de calcul (des centaines d’heures GPU).</span><span class="sxs-lookup"><span data-stu-id="70f77-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="70f77-132">L’utilisation d’un modèle préentraîné avec l’apprentissage de transfert vous permet de raccourcir le processus de formation.</span><span class="sxs-lookup"><span data-stu-id="70f77-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="70f77-133">Processus de formation</span><span class="sxs-lookup"><span data-stu-id="70f77-133">Training process</span></span>

<span data-ttu-id="70f77-134">L’API de classification d’image commence le processus de formation en chargeant un modèle tensorFlow préentraîné.</span><span class="sxs-lookup"><span data-stu-id="70f77-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="70f77-135">Le processus de formation se compose de deux étapes :</span><span class="sxs-lookup"><span data-stu-id="70f77-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="70f77-136">Phase de goulot d’étranglement</span><span class="sxs-lookup"><span data-stu-id="70f77-136">Bottleneck phase</span></span>
2. <span data-ttu-id="70f77-137">Phase de formation</span><span class="sxs-lookup"><span data-stu-id="70f77-137">Training phase</span></span>

![Étapes de formation](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="70f77-139">Phase de goulot d’étranglement</span><span class="sxs-lookup"><span data-stu-id="70f77-139">Bottleneck phase</span></span>

<span data-ttu-id="70f77-140">Pendant la phase de goulot d’étranglement, l’ensemble des images de formation est chargé et les valeurs de pixels sont utilisées comme entrée, ou caractéristiques, pour les couches congelées du modèle préentraîné.</span><span class="sxs-lookup"><span data-stu-id="70f77-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="70f77-141">Les couches gelées comprennent toutes les couches du réseau neuronal jusqu’à l’avant-dernière couche, connue officieusement sous le nom de couche de goulot d’étranglement.</span><span class="sxs-lookup"><span data-stu-id="70f77-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="70f77-142">Ces couches sont appelées congelées parce qu’aucune formation ne se produira sur ces couches et que les opérations sont transmises.</span><span class="sxs-lookup"><span data-stu-id="70f77-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="70f77-143">C’est à ces couches gelées que les modèles de niveau inférieur qui aident un modèle à différencier les différentes classes sont calculés.</span><span class="sxs-lookup"><span data-stu-id="70f77-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="70f77-144">Plus le nombre de couches est élevé, plus cette étape est intensive sur le plan du calcul.</span><span class="sxs-lookup"><span data-stu-id="70f77-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="70f77-145">Heureusement, puisqu’il s’agit d’un calcul ponctuen, les résultats peuvent être mis en cache et utilisés dans des exécutions ultérieures lors de l’expérimentation de différents paramètres.</span><span class="sxs-lookup"><span data-stu-id="70f77-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="70f77-146">Phase de formation</span><span class="sxs-lookup"><span data-stu-id="70f77-146">Training phase</span></span>

<span data-ttu-id="70f77-147">Une fois que les valeurs de sortie de la phase de goulot d’étranglement sont calculées, elles sont utilisées comme entrée pour recycler la couche finale du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="70f77-148">Ce processus est itératif et s’exécute pour le nombre de fois spécifié par les paramètres du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="70f77-149">Au cours de chaque course, la perte et la précision sont évaluées.</span><span class="sxs-lookup"><span data-stu-id="70f77-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="70f77-150">Ensuite, les ajustements appropriés sont effectués pour améliorer le modèle dans le but de minimiser la perte et de maximiser la précision.</span><span class="sxs-lookup"><span data-stu-id="70f77-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="70f77-151">Une fois la formation terminée, deux formats de modèles sont en sortie.</span><span class="sxs-lookup"><span data-stu-id="70f77-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="70f77-152">L’un d’eux est la `.pb` version `.zip` du modèle et l’autre est la ML.NET version sérialisée du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="70f77-153">Lorsque vous travaillez dans des environnements pris en `.zip` charge par ML.NET, il est recommandé d’utiliser la version du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="70f77-154">Toutefois, dans des environnements où ML.NET n’est pas `.pb` pris en charge, vous avez la possibilité d’utiliser la version.</span><span class="sxs-lookup"><span data-stu-id="70f77-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="70f77-155">Comprendre le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="70f77-155">Understand the pretrained model</span></span>

<span data-ttu-id="70f77-156">Le modèle préentraîné utilisé dans ce tutoriel est la variante de 101 couches du modèle V2 du réseau résiduel (ResNet).</span><span class="sxs-lookup"><span data-stu-id="70f77-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="70f77-157">Le modèle original est formé pour classer les images en mille catégories.</span><span class="sxs-lookup"><span data-stu-id="70f77-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="70f77-158">Le modèle prend comme entrée une image de taille 224 x 224 et produit les probabilités de classe pour chacune des classes sur qui il est formé.</span><span class="sxs-lookup"><span data-stu-id="70f77-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="70f77-159">Une partie de ce modèle est utilisée pour former un nouveau modèle à l’aide d’images personnalisées pour faire des prédictions entre deux classes.</span><span class="sxs-lookup"><span data-stu-id="70f77-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="70f77-160">Création d’une application de console</span><span class="sxs-lookup"><span data-stu-id="70f77-160">Create console application</span></span>

<span data-ttu-id="70f77-161">Maintenant que vous avez une compréhension générale de l’apprentissage des transferts et de l’API de classification d’image, il est temps de construire l’application.</span><span class="sxs-lookup"><span data-stu-id="70f77-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="70f77-162">Créez une **application de console de base CMD .NET** appelée « DeepLearning_ImageClassification_Binary ».</span><span class="sxs-lookup"><span data-stu-id="70f77-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="70f77-163">Installer la version **Microsoft.ML** **1.4.0** NuGet Forfait:</span><span class="sxs-lookup"><span data-stu-id="70f77-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="70f77-164">Dans Solution Explorer, cliquez à droite sur votre projet et sélectionnez **Manage NuGet Packages**.</span><span class="sxs-lookup"><span data-stu-id="70f77-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="70f77-165">Choisissez «nuget.org» comme source de paquet.</span><span class="sxs-lookup"><span data-stu-id="70f77-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="70f77-166">Sélectionnez l’onglet **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="70f77-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="70f77-167">Vérifiez la case à cocher **prérelease Inclure.**</span><span class="sxs-lookup"><span data-stu-id="70f77-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="70f77-168">Recherche de **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="70f77-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="70f77-169">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="70f77-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="70f77-170">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="70f77-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="70f77-171">Répétez ces étapes pour la version **Microsoft.ML.Vision** **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, et **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span><span class="sxs-lookup"><span data-stu-id="70f77-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="70f77-172">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="70f77-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="70f77-173">Les jeux de données pour ce tutoriel sont de Maguire, Marc; Dorafshan, Sattar; et Thomas, le juge Robert, "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span><span class="sxs-lookup"><span data-stu-id="70f77-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="70f77-174">Parcourez tous les Jeux de Données.</span><span class="sxs-lookup"><span data-stu-id="70f77-174">Browse all Datasets.</span></span> <span data-ttu-id="70f77-175">Papier 48.</span><span class="sxs-lookup"><span data-stu-id="70f77-175">Paper 48.</span></span> <span data-ttu-id="70f77-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="70f77-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="70f77-177">SDNET2018 est un ensemble de données d’images qui contient des annotations pour les structures en béton fissurées et non fissurées (ponts, murs et chaussée).</span><span class="sxs-lookup"><span data-stu-id="70f77-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![Échantillons de ponts de dataset SDNET2018](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="70f77-179">Les données sont organisées en trois sous-directions :</span><span class="sxs-lookup"><span data-stu-id="70f77-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="70f77-180">D contient des images de pont</span><span class="sxs-lookup"><span data-stu-id="70f77-180">D contains bridge deck images</span></span>
- <span data-ttu-id="70f77-181">P contient des images de chaussée</span><span class="sxs-lookup"><span data-stu-id="70f77-181">P contains pavement images</span></span>
- <span data-ttu-id="70f77-182">W contient des images murales</span><span class="sxs-lookup"><span data-stu-id="70f77-182">W contains wall images</span></span>

<span data-ttu-id="70f77-183">Chacune de ces sous-directions contient deux sous-directions préfixés supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="70f77-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="70f77-184">C est le préfixe utilisé pour les surfaces fissurées</span><span class="sxs-lookup"><span data-stu-id="70f77-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="70f77-185">U est le préfixe utilisé pour les surfaces non encées</span><span class="sxs-lookup"><span data-stu-id="70f77-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="70f77-186">Dans ce tutoriel, seules les images de plate-forme de pont sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="70f77-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="70f77-187">Téléchargez le [jeu de données](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) et unzip.</span><span class="sxs-lookup"><span data-stu-id="70f77-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="70f77-188">Créez un répertoire nommé « actifs » dans votre projet pour enregistrer vos fichiers de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="70f77-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="70f77-189">Copiez les sous-directeurs *CD* et *UD* de l’annuaire récemment décompressé à l’annuaire *des actifs.*</span><span class="sxs-lookup"><span data-stu-id="70f77-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="70f77-190">Créer des classes d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="70f77-190">Create input and output classes</span></span>

1. <span data-ttu-id="70f77-191">Ouvrez le *fichier Program.cs* et `using` remplacez les relevés existants en haut du fichier par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="70f77-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="70f77-192">Ci-dessous la `Program` classe en *Program.cs*, `ImageData`créer une classe appelée .</span><span class="sxs-lookup"><span data-stu-id="70f77-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="70f77-193">Cette classe est utilisée pour représenter les données initialement chargées.</span><span class="sxs-lookup"><span data-stu-id="70f77-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="70f77-194">`ImageData`contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="70f77-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="70f77-195">`ImagePath`est le chemin entièrement qualifié où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="70f77-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="70f77-196">`Label`est la catégorie à laquelle appartient l’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="70f77-197">C’est la valeur à prévoir.</span><span class="sxs-lookup"><span data-stu-id="70f77-197">This is the value to predict.</span></span>

1. <span data-ttu-id="70f77-198">Créez des classes pour vos données d’entrée et de sortie</span><span class="sxs-lookup"><span data-stu-id="70f77-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="70f77-199">Au-dessous de la `ImageData` classe, définissez le schéma `ModelInput`de vos données d’entrée dans une nouvelle classe appelée .</span><span class="sxs-lookup"><span data-stu-id="70f77-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="70f77-200">`ModelInput`contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="70f77-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="70f77-201">`Image`est `byte[]` la représentation de l’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-201">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="70f77-202">Le modèle s’attend à ce que les données d’image soient de ce type pour la formation.</span><span class="sxs-lookup"><span data-stu-id="70f77-202">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="70f77-203">`LabelAsKey`est la représentation `Label`numérique de la .</span><span class="sxs-lookup"><span data-stu-id="70f77-203">`LabelAsKey` is the numerical representation of the `Label`.</span></span>
        - <span data-ttu-id="70f77-204">`ImagePath`est le chemin entièrement qualifié où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="70f77-204">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="70f77-205">`Label`est la catégorie à laquelle appartient l’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-205">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="70f77-206">C’est la valeur à prévoir.</span><span class="sxs-lookup"><span data-stu-id="70f77-206">This is the value to predict.</span></span>

        <span data-ttu-id="70f77-207">Seulement `Image` `LabelAsKey` et sont utilisés pour former le modèle et faire des prédictions.</span><span class="sxs-lookup"><span data-stu-id="70f77-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="70f77-208">Les `ImagePath` `Label` propriétés et les propriétés sont conservées pour plus de commodité pour accéder au nom et à la catégorie de fichier d’image d’origine.</span><span class="sxs-lookup"><span data-stu-id="70f77-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="70f77-209">Ensuite, en `ModelInput` dessous de la classe, définissez le `ModelOutput`schéma de vos données de sortie dans une nouvelle classe appelée .</span><span class="sxs-lookup"><span data-stu-id="70f77-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="70f77-210">`ModelOutput`contient les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="70f77-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="70f77-211">`ImagePath`est le chemin entièrement qualifié où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="70f77-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="70f77-212">`Label`est la catégorie originale à laquelle appartient l’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="70f77-213">C’est la valeur à prévoir.</span><span class="sxs-lookup"><span data-stu-id="70f77-213">This is the value to predict.</span></span>
        - <span data-ttu-id="70f77-214">`PredictedLabel`est la valeur prédite par le modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="70f77-215">Semblable `ModelInput`à , `PredictedLabel` seul le est nécessaire pour faire des prédictions car il contient la prédiction faite par le modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="70f77-216">Les `ImagePath` `Label` propriétés et les propriétés sont conservées pour plus de commodité pour accéder au nom et à la catégorie de fichier d’image d’origine.</span><span class="sxs-lookup"><span data-stu-id="70f77-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="70f77-217">Créer un répertoire d’espace de travail</span><span class="sxs-lookup"><span data-stu-id="70f77-217">Create workspace directory</span></span>

<span data-ttu-id="70f77-218">Lorsque les données de formation et de validation ne changent pas souvent, il est recommandé de mettre en cache les valeurs de goulot d’étranglement calculées pour d’autres exécutions.</span><span class="sxs-lookup"><span data-stu-id="70f77-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="70f77-219">Dans votre projet, créez un nouvel annuaire appelé *espace de* travail `.pb` pour stocker les valeurs de goulot d’étranglement calculées et la version du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="70f77-220">Définir les chemins et les variables d’initialisation</span><span class="sxs-lookup"><span data-stu-id="70f77-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="70f77-221">À `Main` l’intérieur de la méthode, définissez l’emplacement de vos actifs, les valeurs de goulot d’étranglement calculées et `.pb` la version du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="70f77-222">Initialiser `mlContext` la variable avec une nouvelle instance de [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="70f77-222">Initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="70f77-223">La classe [MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation du mlContext crée un nouvel environnement ML.NET qui peut être partagé entre les objets de flux de travail de création de modèles.</span><span class="sxs-lookup"><span data-stu-id="70f77-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="70f77-224">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="70f77-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="70f77-225">Chargement des données</span><span class="sxs-lookup"><span data-stu-id="70f77-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="70f77-226">Créer une méthode d’utilité de chargement de données</span><span class="sxs-lookup"><span data-stu-id="70f77-226">Create data loading utility method</span></span>

<span data-ttu-id="70f77-227">Les images sont stockées dans deux sous-directions.</span><span class="sxs-lookup"><span data-stu-id="70f77-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="70f77-228">Avant de charger les données, elles doivent `ImageData` être formatées en une liste d’objets.</span><span class="sxs-lookup"><span data-stu-id="70f77-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="70f77-229">Pour ce faire, `LoadImagesFromDirectory` créez `Main` la méthode ci-dessous la méthode.</span><span class="sxs-lookup"><span data-stu-id="70f77-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="70f77-230">À `LoadImagesDirectory` l’intérieur de l’ajouter le code suivant pour obtenir tous les chemins de fichier à partir des sous-directions:</span><span class="sxs-lookup"><span data-stu-id="70f77-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="70f77-231">Ensuite, itérer à travers chacun `foreach` des fichiers à l’aide d’une déclaration.</span><span class="sxs-lookup"><span data-stu-id="70f77-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="70f77-232">À `foreach` l’intérieur de la déclaration, vérifiez que les extensions de fichiers sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="70f77-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="70f77-233">L’API de classification d’image prend en charge les formats JPEG et PNG.</span><span class="sxs-lookup"><span data-stu-id="70f77-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="70f77-234">Ensuite, obtenir l’étiquette pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="70f77-234">Then, get the label for the file.</span></span> <span data-ttu-id="70f77-235">Si `useFolderNameAsLabel` le paramètre `true`est défini, alors le répertoire parent où le fichier est enregistré est utilisé comme étiquette.</span><span class="sxs-lookup"><span data-stu-id="70f77-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="70f77-236">Dans le cas contraire, il s’attend à ce que l’étiquette soit un préfixe du nom du fichier ou du nom du fichier lui-même.</span><span class="sxs-lookup"><span data-stu-id="70f77-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="70f77-237">Enfin, créer une `ModelInput`nouvelle instance de .</span><span class="sxs-lookup"><span data-stu-id="70f77-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="70f77-238">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="70f77-238">Prepare the data</span></span>

1. <span data-ttu-id="70f77-239">De retour `Main` dans la `LoadFromDirectory` méthode, utilisez la méthode d’utilité pour obtenir la liste des images utilisées pour la formation.</span><span class="sxs-lookup"><span data-stu-id="70f77-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="70f77-240">Ensuite, chargez les [`IDataView`](xref:Microsoft.ML.IDataView) images [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) dans une méthode utilisant.</span><span class="sxs-lookup"><span data-stu-id="70f77-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="70f77-241">Les données sont chargées dans l’ordre où elles ont été lues dans les répertoires.</span><span class="sxs-lookup"><span data-stu-id="70f77-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="70f77-242">Pour équilibrer les données, [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) mélangez-les en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="70f77-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="70f77-243">Les modèles d’apprentissage automatique s’attendent à ce que les données soient en format numérique.</span><span class="sxs-lookup"><span data-stu-id="70f77-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="70f77-244">Par conséquent, certains prétraitement doivent être effectués sur les données avant la formation.</span><span class="sxs-lookup"><span data-stu-id="70f77-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="70f77-245">Créez [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) un composé [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) de `LoadRawImageBytes` la et transforme.</span><span class="sxs-lookup"><span data-stu-id="70f77-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="70f77-246">La `MapValueToKey` transformation prend la valeur `Label` catégorique dans la colonne, la convertit en valeur numérique `KeyType` et la stocke dans une nouvelle colonne appelée `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="70f77-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="70f77-247">Le `LoadImages` prend les `ImagePath` valeurs de `imageFolder` la colonne avec le paramètre pour charger des images pour la formation.</span><span class="sxs-lookup"><span data-stu-id="70f77-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="70f77-248">Utilisez [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) la méthode pour appliquer `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) les [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) données sur les [`IDataView`](xref:Microsoft.ML.IDataView) données suivies de la méthode, qui renvoie une contenant les données pré-traitées.</span><span class="sxs-lookup"><span data-stu-id="70f77-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="70f77-249">Pour former un modèle, il est important d’avoir un jeu de données de formation ainsi qu’un jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="70f77-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="70f77-250">Le modèle est formé sur l’ensemble de formation.</span><span class="sxs-lookup"><span data-stu-id="70f77-250">The model is trained on the training set.</span></span> <span data-ttu-id="70f77-251">La façon dont il fait des prédictions sur des données invisibles est mesurée par les performances par rapport à l’ensemble de validation.</span><span class="sxs-lookup"><span data-stu-id="70f77-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="70f77-252">Sur la base des résultats de cette performance, le modèle apporte des ajustements à ce qu’il a appris dans un effort pour s’améliorer.</span><span class="sxs-lookup"><span data-stu-id="70f77-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="70f77-253">L’ensemble de validation peut provenir soit du fractionnement de votre jeu de données d’origine, soit d’une autre source qui a déjà été mise de côté à cette fin.</span><span class="sxs-lookup"><span data-stu-id="70f77-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="70f77-254">Dans ce cas, le jeu de données prétrafé par traité est divisé en ensembles de formation, de validation et de test.</span><span class="sxs-lookup"><span data-stu-id="70f77-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="70f77-255">L’échantillon de code ci-dessus effectue deux fractionnements.</span><span class="sxs-lookup"><span data-stu-id="70f77-255">The code sample above performs two splits.</span></span> <span data-ttu-id="70f77-256">Tout d’abord, les données pré-traitées sont divisées et 70% sont utilisées pour la formation tandis que les 30% restants sont utilisés pour validation.</span><span class="sxs-lookup"><span data-stu-id="70f77-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="70f77-257">Ensuite, l’ensemble de validation de 30% est encore divisé en jeux de validation et de test où 90% est utilisé pour la validation et 10% est utilisé pour les tests.</span><span class="sxs-lookup"><span data-stu-id="70f77-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="70f77-258">Une façon de penser à l’objectif de ces partitions de données est de passer un examen.</span><span class="sxs-lookup"><span data-stu-id="70f77-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="70f77-259">Lorsque vous étudiez pour un examen, vous passez en revue vos notes, livres ou autres ressources pour obtenir une compréhension sur les concepts qui sont à l’examen.</span><span class="sxs-lookup"><span data-stu-id="70f77-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="70f77-260">C’est à ça que s’adresse le train.</span><span class="sxs-lookup"><span data-stu-id="70f77-260">This is what the train set is for.</span></span> <span data-ttu-id="70f77-261">Ensuite, vous pourriez passer un faux examen pour valider vos connaissances.</span><span class="sxs-lookup"><span data-stu-id="70f77-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="70f77-262">C’est là que l’ensemble de validation est utile.</span><span class="sxs-lookup"><span data-stu-id="70f77-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="70f77-263">Vous voulez vérifier si vous avez une bonne compréhension des concepts avant de passer l’examen réel.</span><span class="sxs-lookup"><span data-stu-id="70f77-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="70f77-264">Sur la base de ces résultats, vous prenez note de ce que vous vous êtes trompé ou ne comprenait pas bien et d’intégrer vos changements que vous examinez pour l’examen réel.</span><span class="sxs-lookup"><span data-stu-id="70f77-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="70f77-265">Enfin, vous passerez l’examen.</span><span class="sxs-lookup"><span data-stu-id="70f77-265">Finally, you take the exam.</span></span> <span data-ttu-id="70f77-266">C’est pour cela que sert l’ensemble de test.</span><span class="sxs-lookup"><span data-stu-id="70f77-266">This is what the test set is used for.</span></span> <span data-ttu-id="70f77-267">Vous n’avez jamais vu les questions qui sont à l’examen et utilisez maintenant ce que vous avez appris de la formation et de la validation pour appliquer vos connaissances à la tâche à accomplir.</span><span class="sxs-lookup"><span data-stu-id="70f77-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="70f77-268">Attribuez les partitions à leurs valeurs respectives pour les données de train, de validation et de test.</span><span class="sxs-lookup"><span data-stu-id="70f77-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="70f77-269">Définir le pipeline de formation</span><span class="sxs-lookup"><span data-stu-id="70f77-269">Define the training pipeline</span></span>

<span data-ttu-id="70f77-270">La formation modèle se compose d’un couple d’étapes.</span><span class="sxs-lookup"><span data-stu-id="70f77-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="70f77-271">Tout d’abord, l’API de classification d’image est utilisé pour former le modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="70f77-272">Ensuite, les étiquettes codées dans la `PredictedLabel` colonne sont converties `MapKeyToValue` à leur valeur catégorique d’origine à l’aide de la transformation.</span><span class="sxs-lookup"><span data-stu-id="70f77-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="70f77-273">Créez une nouvelle variable pour stocker un ensemble `ImageClassificationTrainer`de paramètres requis et facultatifs pour un .</span><span class="sxs-lookup"><span data-stu-id="70f77-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span>

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="70f77-274">Un `ImageClassificationTrainer` prend plusieurs paramètres facultatifs :</span><span class="sxs-lookup"><span data-stu-id="70f77-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="70f77-275">`FeatureColumnName`est la colonne qui est utilisée comme entrée pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="70f77-276">`LabelColumnName`est la colonne pour la valeur à prévoir.</span><span class="sxs-lookup"><span data-stu-id="70f77-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="70f77-277">`ValidationSet`est [`IDataView`](xref:Microsoft.ML.IDataView) la contenant des données de validation.</span><span class="sxs-lookup"><span data-stu-id="70f77-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="70f77-278">`Arch`définit laquelle des architectures modèles préentraînées à utiliser.</span><span class="sxs-lookup"><span data-stu-id="70f77-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="70f77-279">Ce tutoriel utilise la variante 101 couches du modèle ResNetv2.</span><span class="sxs-lookup"><span data-stu-id="70f77-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="70f77-280">`MetricsCallback`lie une fonction pour suivre les progrès pendant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="70f77-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="70f77-281">`TestOnTrainSet`indique au modèle de mesurer les performances par rapport à l’ensemble de formation lorsqu’aucun ensemble de validation n’est présent.</span><span class="sxs-lookup"><span data-stu-id="70f77-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="70f77-282">`ReuseTrainSetBottleneckCachedValues`indique au modèle s’il faut utiliser les valeurs mises en cache de la phase de goulot d’étranglement dans les exécutions suivantes.</span><span class="sxs-lookup"><span data-stu-id="70f77-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="70f77-283">La phase de goulot d’étranglement est un calcul unique qui est d’une intensité de calcul la première fois qu’il est effectué.</span><span class="sxs-lookup"><span data-stu-id="70f77-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="70f77-284">Si les données de formation ne changent pas et que vous souhaitez expérimenter à l’aide d’un nombre différent d’époques ou de la taille du lot, l’utilisation des valeurs mises en cache réduit considérablement le temps nécessaire pour former un modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="70f77-285">`ReuseValidationSetBottleneckCachedValues`est similaire `ReuseTrainSetBottleneckCachedValues` à celle que dans ce cas, c’est pour le jeu de données de validation.</span><span class="sxs-lookup"><span data-stu-id="70f77-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="70f77-286">`WorkspacePath`définit l’annuaire où stocker les valeurs de `.pb` goulot d’étranglement calculées et la version du modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="70f77-287">Définir [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) le pipeline de formation `mapLabelEstimator` qui `ImageClassificationTrainer`se compose à la fois de la et le .</span><span class="sxs-lookup"><span data-stu-id="70f77-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="70f77-288">Utilisez [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) la méthode pour former votre modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="70f77-289">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="70f77-289">Use the model</span></span>

<span data-ttu-id="70f77-290">Maintenant que vous avez formé votre modèle, il est temps de l’utiliser pour classer les images.</span><span class="sxs-lookup"><span data-stu-id="70f77-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="70f77-291">Ci-dessous la `Main` méthode, créez `OutputPrediction` une nouvelle méthode utilitaire appelée pour afficher les informations de prédiction dans la console.</span><span class="sxs-lookup"><span data-stu-id="70f77-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="70f77-292">Classer une seule image</span><span class="sxs-lookup"><span data-stu-id="70f77-292">Classify a single image</span></span>

1. <span data-ttu-id="70f77-293">Ajoutez une nouvelle `ClassifySingleImage` méthode `Main` appelée ci-dessous la méthode pour faire et sortir une seule prédiction d’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="70f77-294">Créez [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) une `ClassifySingleImage` méthode à l’intérieur de la méthode.</span><span class="sxs-lookup"><span data-stu-id="70f77-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="70f77-295">Il [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) s’agit d’une API pratique, qui vous permet de passer dedans et d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="70f77-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="70f77-296">Pour accéder `ModelInput` à une `data` [`IDataView`](xref:Microsoft.ML.IDataView) seule [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) instance, [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) convertir le en une utilisation de la méthode, puis obtenir la première observation.</span><span class="sxs-lookup"><span data-stu-id="70f77-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="70f77-297">Utilisez [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) la méthode pour classer l’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="70f77-298">Sortie de la prédiction `OutputPrediction` à la console avec la méthode.</span><span class="sxs-lookup"><span data-stu-id="70f77-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="70f77-299">À `Main` l’intérieur `ClassifySingleImage` de la méthode, appelez en utilisant l’ensemble de test d’images.</span><span class="sxs-lookup"><span data-stu-id="70f77-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="70f77-300">Classer plusieurs images</span><span class="sxs-lookup"><span data-stu-id="70f77-300">Classify multiple images</span></span>

1. <span data-ttu-id="70f77-301">Ajoutez une nouvelle `ClassifyImages` méthode `ClassifySingleImage` appelée ci-dessous la méthode pour faire et sortir plusieurs prédictions d’image.</span><span class="sxs-lookup"><span data-stu-id="70f77-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="70f77-302">Créez [`IDataView`](xref:Microsoft.ML.IDataView) un contenant les [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) prédictions en utilisant la méthode.</span><span class="sxs-lookup"><span data-stu-id="70f77-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="70f77-303">Ajoutez le code suivant dans la méthode `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="70f77-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="70f77-304">Afin d’itérer sur les prédictions, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) convertir [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) le `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) en une utilisation de la méthode, puis obtenir les 10 premières observations.</span><span class="sxs-lookup"><span data-stu-id="70f77-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="70f77-305">Itérer et produire les étiquettes originales et prévues pour les prédictions.</span><span class="sxs-lookup"><span data-stu-id="70f77-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="70f77-306">Enfin, à `Main` l’intérieur de la méthode, appelez `ClassifyImages` en utilisant l’ensemble de test d’images.</span><span class="sxs-lookup"><span data-stu-id="70f77-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="70f77-307">Exécuter l’application</span><span class="sxs-lookup"><span data-stu-id="70f77-307">Run the application</span></span>

<span data-ttu-id="70f77-308">Exécutez votre application console.</span><span class="sxs-lookup"><span data-stu-id="70f77-308">Run your console app.</span></span> <span data-ttu-id="70f77-309">La sortie devrait être similaire à celle ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="70f77-309">The output should be similar to that below.</span></span> <span data-ttu-id="70f77-310">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="70f77-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="70f77-311">Pour la brièveté, la sortie a été condensée.</span><span class="sxs-lookup"><span data-stu-id="70f77-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="70f77-312">**Phase de goulot d’étranglement**</span><span class="sxs-lookup"><span data-stu-id="70f77-312">**Bottleneck phase**</span></span>

<span data-ttu-id="70f77-313">Aucune valeur n’est imprimée pour le nom `byte[]` de l’image parce que les images sont chargées car il n’y a donc pas de nom d’image à afficher.</span><span class="sxs-lookup"><span data-stu-id="70f77-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="70f77-314">**Phase de formation**</span><span class="sxs-lookup"><span data-stu-id="70f77-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="70f77-315">**Classer la sortie d’images**</span><span class="sxs-lookup"><span data-stu-id="70f77-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="70f77-316">Lors de l’inspection de l’image *7001-220.jpg,* vous pouvez voir qu’il n’est en fait pas fissuré.</span><span class="sxs-lookup"><span data-stu-id="70f77-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![Image de jeu de données SDNET2018 utilisée pour la prédiction](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="70f77-318">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="70f77-318">Congratulations!</span></span> <span data-ttu-id="70f77-319">Vous avez maintenant construit avec succès un modèle d’apprentissage profond pour classer les images.</span><span class="sxs-lookup"><span data-stu-id="70f77-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="70f77-320">Améliorer le modèle</span><span class="sxs-lookup"><span data-stu-id="70f77-320">Improve the model</span></span>

<span data-ttu-id="70f77-321">Si vous n’êtes pas satisfait des résultats de votre modèle, vous pouvez essayer d’améliorer ses performances en essayant certaines des approches suivantes :</span><span class="sxs-lookup"><span data-stu-id="70f77-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="70f77-322">**Plus de données**: Plus un modèle apprend d’exemples, mieux il fonctionne.</span><span class="sxs-lookup"><span data-stu-id="70f77-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="70f77-323">Téléchargez le [jeu de données SDNET2018](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) complet et utilisez-le pour vous entraîner.</span><span class="sxs-lookup"><span data-stu-id="70f77-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="70f77-324">**Augmenter les données**: Une technique courante pour ajouter de la variété aux données est d’augmenter les données en prenant une image et en appliquant différentes transformations (rotation, flip, shift, crop).</span><span class="sxs-lookup"><span data-stu-id="70f77-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="70f77-325">Cela ajoute des exemples plus variés pour le modèle à apprendre.</span><span class="sxs-lookup"><span data-stu-id="70f77-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="70f77-326">**Entraînez-vous plus longtemps**: Plus vous vous entraînez, plus le modèle sera à l’écoute.</span><span class="sxs-lookup"><span data-stu-id="70f77-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="70f77-327">L’augmentation du nombre d’époques peut améliorer les performances de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="70f77-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="70f77-328">**Expérimentez avec les hyper-paramètres**: En plus des paramètres utilisés dans ce tutoriel, d’autres paramètres peuvent être réglés pour améliorer potentiellement les performances.</span><span class="sxs-lookup"><span data-stu-id="70f77-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="70f77-329">Changer le taux d’apprentissage, qui détermine l’ampleur des mises à jour apportées au modèle après chaque époque peut améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="70f77-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="70f77-330">**Utilisez une architecture de modèle différente**: Selon vos données, le modèle qui peut le mieux apprendre ses fonctionnalités peut différer.</span><span class="sxs-lookup"><span data-stu-id="70f77-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="70f77-331">Si vous n’êtes pas satisfait des performances de votre modèle, essayez de changer l’architecture.</span><span class="sxs-lookup"><span data-stu-id="70f77-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="70f77-332">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="70f77-332">Additional Resources</span></span>

- <span data-ttu-id="70f77-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="70f77-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="70f77-334">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="70f77-334">Next steps</span></span>

<span data-ttu-id="70f77-335">Dans ce tutoriel, vous avez appris à construire un modèle d’apprentissage profond personnalisé en utilisant l’apprentissage de transfert, un modèle de classification d’image pré-formé TensorFlow et l’API de classification d’image ML.NET pour classer des images de surfaces en béton comme fissurées ou non.</span><span class="sxs-lookup"><span data-stu-id="70f77-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="70f77-336">Passez au tutoriel suivant pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="70f77-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="70f77-337">Détection d’objets</span><span class="sxs-lookup"><span data-stu-id="70f77-337">Object Detection</span></span>](object-detection-onnx.md)
