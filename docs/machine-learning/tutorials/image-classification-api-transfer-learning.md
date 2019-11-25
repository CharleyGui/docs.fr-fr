---
title: 'Tutorial: Automated visual inspection using transfer learning'
description: This tutorial illustrates how to use transfer learning to train a TensorFlow deep learning model in ML.NET using the image detection API to classify images of concrete surfaces as cracked or not cracked.
author: luisquintanilla
ms.author: luquinta
ms.date: 11/14/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 443f9e9a83ebf31bb6c62323015af4a554323b67
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205053"
---
# <a name="tutorial-automated-visual-inspection-using-transfer-learning-with-the-mlnet-image-classification-api"></a><span data-ttu-id="56fe3-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span><span class="sxs-lookup"><span data-stu-id="56fe3-103">Tutorial: Automated visual inspection using transfer learning with the ML.NET Image Classification API</span></span>

<span data-ttu-id="56fe3-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span><span class="sxs-lookup"><span data-stu-id="56fe3-104">Learn how to train a custom deep learning model using transfer learning, a pretrained TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="56fe3-105">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="56fe3-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="56fe3-106">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="56fe3-106">Understand the problem</span></span>
> - <span data-ttu-id="56fe3-107">Learn about ML.NET Image Classification API</span><span class="sxs-lookup"><span data-stu-id="56fe3-107">Learn about ML.NET Image Classification API</span></span>
> - <span data-ttu-id="56fe3-108">Understand the pretrained model</span><span class="sxs-lookup"><span data-stu-id="56fe3-108">Understand the pretrained model</span></span>
> - <span data-ttu-id="56fe3-109">Use transfer learning to train a custom TensorFlow image classification model</span><span class="sxs-lookup"><span data-stu-id="56fe3-109">Use transfer learning to train a custom TensorFlow image classification model</span></span>
> - <span data-ttu-id="56fe3-110">Classify images with the custom model</span><span class="sxs-lookup"><span data-stu-id="56fe3-110">Classify images with the custom model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56fe3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56fe3-111">Prerequisites</span></span>

- <span data-ttu-id="56fe3-112">[Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="56fe3-112">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="image-classification-transfer-learning-sample-overview"></a><span data-ttu-id="56fe3-113">Image classification transfer learning sample overview</span><span class="sxs-lookup"><span data-stu-id="56fe3-113">Image classification transfer learning sample overview</span></span>

<span data-ttu-id="56fe3-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-114">This sample is a C# .NET Core console application that classifies images using a pretrained deep learning TensorFlow model.</span></span> <span data-ttu-id="56fe3-115">Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="56fe3-115">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary) on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="56fe3-116">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="56fe3-116">Understand the problem</span></span>

<span data-ttu-id="56fe3-117">Image classification is a computer vision problem.</span><span class="sxs-lookup"><span data-stu-id="56fe3-117">Image classification is a computer vision problem.</span></span> <span data-ttu-id="56fe3-118">Image classification takes an image as input and categorizes it into a prescribed class.</span><span class="sxs-lookup"><span data-stu-id="56fe3-118">Image classification takes an image as input and categorizes it into a prescribed class.</span></span> <span data-ttu-id="56fe3-119">Some scenarios where image classification is useful include:</span><span class="sxs-lookup"><span data-stu-id="56fe3-119">Some scenarios where image classification is useful include:</span></span>

- <span data-ttu-id="56fe3-120">Reconnaissance faciale</span><span class="sxs-lookup"><span data-stu-id="56fe3-120">Facial recognition</span></span>
- <span data-ttu-id="56fe3-121">Emotion detection</span><span class="sxs-lookup"><span data-stu-id="56fe3-121">Emotion detection</span></span>
- <span data-ttu-id="56fe3-122">Medical diagnosis</span><span class="sxs-lookup"><span data-stu-id="56fe3-122">Medical diagnosis</span></span>
- <span data-ttu-id="56fe3-123">Landmark detection</span><span class="sxs-lookup"><span data-stu-id="56fe3-123">Landmark detection</span></span>

<span data-ttu-id="56fe3-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span><span class="sxs-lookup"><span data-stu-id="56fe3-124">This tutorial trains a custom image classification model to perform automated visual inspection of bridge decks to identify structures that are damaged by cracks.</span></span>

## <a name="mlnet-image-classification-api"></a><span data-ttu-id="56fe3-125">ML.NET Image Classification API</span><span class="sxs-lookup"><span data-stu-id="56fe3-125">ML.NET Image Classification API</span></span>

<span data-ttu-id="56fe3-126">ML.NET provides various ways of performing image classification.</span><span class="sxs-lookup"><span data-stu-id="56fe3-126">ML.NET provides various ways of performing image classification.</span></span> <span data-ttu-id="56fe3-127">This tutorial applies transfer learning using the Image Classification API.</span><span class="sxs-lookup"><span data-stu-id="56fe3-127">This tutorial applies transfer learning using the Image Classification API.</span></span> <span data-ttu-id="56fe3-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span><span class="sxs-lookup"><span data-stu-id="56fe3-128">The Image Classification API makes use of [TensorFlow.NET](https://github.com/SciSharp/TensorFlow.NET), a low-level library that provides C# bindings for the TensorFlow C++ API.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="56fe3-129">Qu’est-ce que l’apprentissage par transfert ?</span><span class="sxs-lookup"><span data-stu-id="56fe3-129">What is transfer learning?</span></span>

<span data-ttu-id="56fe3-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span><span class="sxs-lookup"><span data-stu-id="56fe3-130">Transfer learning applies knowledge gained from solving one problem to another related problem.</span></span>

<span data-ttu-id="56fe3-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span><span class="sxs-lookup"><span data-stu-id="56fe3-131">Training a deep learning model from scratch requires setting several parameters, a large amount of labeled training data, and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="56fe3-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span><span class="sxs-lookup"><span data-stu-id="56fe3-132">Using a pretrained model along with transfer learning allows you to shortcut the training process.</span></span>

## <a name="training-process"></a><span data-ttu-id="56fe3-133">Training process</span><span class="sxs-lookup"><span data-stu-id="56fe3-133">Training process</span></span>

<span data-ttu-id="56fe3-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-134">The Image Classification API starts the training process by loading a pretrained TensorFlow model.</span></span> <span data-ttu-id="56fe3-135">The training process consists of two steps:</span><span class="sxs-lookup"><span data-stu-id="56fe3-135">The training process consists of two steps:</span></span>

1. <span data-ttu-id="56fe3-136">Bottleneck phase</span><span class="sxs-lookup"><span data-stu-id="56fe3-136">Bottleneck phase</span></span>
2. <span data-ttu-id="56fe3-137">Training phase</span><span class="sxs-lookup"><span data-stu-id="56fe3-137">Training phase</span></span>

![Training Steps](./media/image-classification-api-transfer-learning/training.png)

### <a name="bottleneck-phase"></a><span data-ttu-id="56fe3-139">Bottleneck phase</span><span class="sxs-lookup"><span data-stu-id="56fe3-139">Bottleneck phase</span></span>

<span data-ttu-id="56fe3-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-140">During the bottleneck phase, the set of training images is loaded and the pixel values are used as input, or features, for the frozen layers of the pretrained model.</span></span> <span data-ttu-id="56fe3-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span><span class="sxs-lookup"><span data-stu-id="56fe3-141">The frozen layers include all of the layers in the neural network up to the penultimate layer, informally known as the bottleneck layer.</span></span> <span data-ttu-id="56fe3-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span><span class="sxs-lookup"><span data-stu-id="56fe3-142">These layers are referred to as frozen because no training will occur on these layers and operations are pass-through.</span></span> <span data-ttu-id="56fe3-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span><span class="sxs-lookup"><span data-stu-id="56fe3-143">It's at these frozen layers where the lower-level patterns that help a model differentiate between the different classes are computed.</span></span> <span data-ttu-id="56fe3-144">The larger the number of layers, the more computationally intensive this step is.</span><span class="sxs-lookup"><span data-stu-id="56fe3-144">The larger the number of layers, the more computationally intensive this step is.</span></span> <span data-ttu-id="56fe3-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span><span class="sxs-lookup"><span data-stu-id="56fe3-145">Fortunately, since this is a one-time calculation, the results can be cached and used in later runs when experimenting with different parameters.</span></span>

### <a name="training-phase"></a><span data-ttu-id="56fe3-146">Training phase</span><span class="sxs-lookup"><span data-stu-id="56fe3-146">Training phase</span></span>

<span data-ttu-id="56fe3-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-147">Once the output values from the bottleneck phase are computed, they are used as input to retrain the final layer of the model.</span></span> <span data-ttu-id="56fe3-148">This process is iterative and runs for the number of times specified by model parameters.</span><span class="sxs-lookup"><span data-stu-id="56fe3-148">This process is iterative and runs for the number of times specified by model parameters.</span></span> <span data-ttu-id="56fe3-149">During each run, the loss and accuracy are evaluated.</span><span class="sxs-lookup"><span data-stu-id="56fe3-149">During each run, the loss and accuracy are evaluated.</span></span> <span data-ttu-id="56fe3-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span><span class="sxs-lookup"><span data-stu-id="56fe3-150">Then, the appropriate adjustments are made to improve the model with the goal of minimizing the loss and maximizing the accuracy.</span></span> <span data-ttu-id="56fe3-151">Once training is finished, two model formats are output.</span><span class="sxs-lookup"><span data-stu-id="56fe3-151">Once training is finished, two model formats are output.</span></span> <span data-ttu-id="56fe3-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-152">One of them is the `.pb` version of the model and the other is the `.zip` ML.NET serialized version of the model.</span></span> <span data-ttu-id="56fe3-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-153">When working in environments supported by ML.NET, it is recommended to use the `.zip` version of the model.</span></span> <span data-ttu-id="56fe3-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span><span class="sxs-lookup"><span data-stu-id="56fe3-154">However, in environments where ML.NET is not supported, you have the option of using the `.pb` version.</span></span>

## <a name="understand-the-pretrained-model"></a><span data-ttu-id="56fe3-155">Understand the pretrained model</span><span class="sxs-lookup"><span data-stu-id="56fe3-155">Understand the pretrained model</span></span>

<span data-ttu-id="56fe3-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-156">The pretrained model used in this tutorial is the 101-layer variant of the Residual Network (ResNet) v2 model.</span></span> <span data-ttu-id="56fe3-157">The original model is trained to classify images into a thousand categories.</span><span class="sxs-lookup"><span data-stu-id="56fe3-157">The original model is trained to classify images into a thousand categories.</span></span> <span data-ttu-id="56fe3-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span><span class="sxs-lookup"><span data-stu-id="56fe3-158">The model takes as input an image of size 224 x 224 and outputs the class probabilities for each of the classes it's trained on.</span></span> <span data-ttu-id="56fe3-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span><span class="sxs-lookup"><span data-stu-id="56fe3-159">Part of this model is used to train a new model using custom images to make predictions between two classes.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="56fe3-160">Create console application</span><span class="sxs-lookup"><span data-stu-id="56fe3-160">Create console application</span></span>

<span data-ttu-id="56fe3-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span><span class="sxs-lookup"><span data-stu-id="56fe3-161">Now that you have a general understanding of transfer learning and the Image Classification API, it's time to build the application.</span></span>

1. <span data-ttu-id="56fe3-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span><span class="sxs-lookup"><span data-stu-id="56fe3-162">Create a **C# .NET Core Console Application** called "DeepLearning_ImageClassification_Binary".</span></span>
1. <span data-ttu-id="56fe3-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span><span class="sxs-lookup"><span data-stu-id="56fe3-163">Install the **Microsoft.ML** version **1.4.0** NuGet Package:</span></span>
    1. <span data-ttu-id="56fe3-164">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="56fe3-164">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="56fe3-165">Choose "nuget.org" as the Package source.</span><span class="sxs-lookup"><span data-stu-id="56fe3-165">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="56fe3-166">Sélectionnez l’onglet **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="56fe3-166">Select the **Browse** tab.</span></span>
    1. <span data-ttu-id="56fe3-167">Check the **Include prerelease** checkbox.</span><span class="sxs-lookup"><span data-stu-id="56fe3-167">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="56fe3-168">Search for **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="56fe3-168">Search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="56fe3-169">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="56fe3-169">Select the **Install** button.</span></span>
    1. <span data-ttu-id="56fe3-170">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="56fe3-170">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="56fe3-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span><span class="sxs-lookup"><span data-stu-id="56fe3-171">Repeat these steps for the **Microsoft.ML.Vision** version **1.4.0**, **SciSharp.TensorFlow.Redist** version **1.15.0**, and **Microsoft.ML.ImageAnalytics** version **1.4.0** NuGet packages.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="56fe3-172">Préparer et comprendre les données</span><span class="sxs-lookup"><span data-stu-id="56fe3-172">Prepare and understand the data</span></span>

> [!NOTE]
> <span data-ttu-id="56fe3-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span><span class="sxs-lookup"><span data-stu-id="56fe3-173">The datasets for this tutorial are from Maguire, Marc; Dorafshan, Sattar; and Thomas, Robert J., "SDNET2018: A concrete crack image dataset for machine learning applications" (2018).</span></span> <span data-ttu-id="56fe3-174">Browse all Datasets.</span><span class="sxs-lookup"><span data-stu-id="56fe3-174">Browse all Datasets.</span></span> <span data-ttu-id="56fe3-175">Paper 48.</span><span class="sxs-lookup"><span data-stu-id="56fe3-175">Paper 48.</span></span> <span data-ttu-id="56fe3-176">https://digitalcommons.usu.edu/all_datasets/48</span><span class="sxs-lookup"><span data-stu-id="56fe3-176">https://digitalcommons.usu.edu/all_datasets/48</span></span>

<span data-ttu-id="56fe3-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span><span class="sxs-lookup"><span data-stu-id="56fe3-177">SDNET2018 is an image dataset that contains annotations for cracked and non-cracked concrete structures (bridge decks, walls, and pavement).</span></span>

![SDNET2018 dataset bridge deck samples](./media/image-classification-api-transfer-learning/sdnet2018decksamples.png)

<span data-ttu-id="56fe3-179">The data is organized in three subdirectories:</span><span class="sxs-lookup"><span data-stu-id="56fe3-179">The data is organized in three subdirectories:</span></span>

- <span data-ttu-id="56fe3-180">D contains bridge deck images</span><span class="sxs-lookup"><span data-stu-id="56fe3-180">D contains bridge deck images</span></span>
- <span data-ttu-id="56fe3-181">P contains pavement images</span><span class="sxs-lookup"><span data-stu-id="56fe3-181">P contains pavement images</span></span>
- <span data-ttu-id="56fe3-182">W contains wall images</span><span class="sxs-lookup"><span data-stu-id="56fe3-182">W contains wall images</span></span>

<span data-ttu-id="56fe3-183">Each of these subdirectories contains two additional prefixed subdirectories:</span><span class="sxs-lookup"><span data-stu-id="56fe3-183">Each of these subdirectories contains two additional prefixed subdirectories:</span></span>

- <span data-ttu-id="56fe3-184">C is the prefix used for cracked surfaces</span><span class="sxs-lookup"><span data-stu-id="56fe3-184">C is the prefix used for cracked surfaces</span></span>
- <span data-ttu-id="56fe3-185">U is the prefix used for uncracked surfaces</span><span class="sxs-lookup"><span data-stu-id="56fe3-185">U is the prefix used for uncracked surfaces</span></span>

<span data-ttu-id="56fe3-186">In this tutorial, only bridge deck images are used.</span><span class="sxs-lookup"><span data-stu-id="56fe3-186">In this tutorial, only bridge deck images are used.</span></span>

1. <span data-ttu-id="56fe3-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span><span class="sxs-lookup"><span data-stu-id="56fe3-187">Download the [dataset](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/assets.zip) and unzip.</span></span>
1. <span data-ttu-id="56fe3-188">Create a directory named "assets" in your project to save your dataset files.</span><span class="sxs-lookup"><span data-stu-id="56fe3-188">Create a directory named "assets" in your project to save your dataset files.</span></span>
1. <span data-ttu-id="56fe3-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span><span class="sxs-lookup"><span data-stu-id="56fe3-189">Copy the *CD* and *UD* subdirectories from the recently unzipped directory to the *assets* directory.</span></span>

### <a name="create-input-and-output-classes"></a><span data-ttu-id="56fe3-190">Create input and output classes</span><span class="sxs-lookup"><span data-stu-id="56fe3-190">Create input and output classes</span></span>

1. <span data-ttu-id="56fe3-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span><span class="sxs-lookup"><span data-stu-id="56fe3-191">Open the *Program.cs* file and replace the existing `using` statements at the top of the file with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L1-L7)]

1. <span data-ttu-id="56fe3-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-192">Below the `Program` class in *Program.cs*, create a class called `ImageData`.</span></span> <span data-ttu-id="56fe3-193">This class is used to represent the initially loaded data.</span><span class="sxs-lookup"><span data-stu-id="56fe3-193">This class is used to represent the initially loaded data.</span></span>

    [!code-csharp [ImageDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L137-L142)]

    <span data-ttu-id="56fe3-194">`ImageData` contains the following properties:</span><span class="sxs-lookup"><span data-stu-id="56fe3-194">`ImageData` contains the following properties:</span></span>

    - <span data-ttu-id="56fe3-195">`ImagePath` is the fully qualified path where the image is stored.</span><span class="sxs-lookup"><span data-stu-id="56fe3-195">`ImagePath` is the fully qualified path where the image is stored.</span></span>
    - <span data-ttu-id="56fe3-196">`Label` is the category the image belongs to.</span><span class="sxs-lookup"><span data-stu-id="56fe3-196">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="56fe3-197">This is the value to predict.</span><span class="sxs-lookup"><span data-stu-id="56fe3-197">This is the value to predict.</span></span>

1. <span data-ttu-id="56fe3-198">Create classes for your input and output data</span><span class="sxs-lookup"><span data-stu-id="56fe3-198">Create classes for your input and output data</span></span>

    1. <span data-ttu-id="56fe3-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-199">Below the `ImageData` class, define the schema of your input data in a new class called `ModelInput`.</span></span>

        [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L144-L153)]

        <span data-ttu-id="56fe3-200">`ModelInput` contains the following properties:</span><span class="sxs-lookup"><span data-stu-id="56fe3-200">`ModelInput` contains the following properties:</span></span>

        - <span data-ttu-id="56fe3-201">`ImagePath` is the fully qualified path where the image is stored.</span><span class="sxs-lookup"><span data-stu-id="56fe3-201">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="56fe3-202">`Label` is the category the image belongs to.</span><span class="sxs-lookup"><span data-stu-id="56fe3-202">`Label` is the category the image belongs to.</span></span> <span data-ttu-id="56fe3-203">This is the value to predict.</span><span class="sxs-lookup"><span data-stu-id="56fe3-203">This is the value to predict.</span></span>
        - <span data-ttu-id="56fe3-204">`Image` is the `byte[]` representation of the image.</span><span class="sxs-lookup"><span data-stu-id="56fe3-204">`Image` is the `byte[]` representation of the image.</span></span> <span data-ttu-id="56fe3-205">The model expects image data to be of this type for training.</span><span class="sxs-lookup"><span data-stu-id="56fe3-205">The model expects image data to be of this type for training.</span></span>
        - <span data-ttu-id="56fe3-206">`LabelAsKey` is the numerical representation of the `Label`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-206">`LabelAsKey` is the numerical representation of the `Label`.</span></span>

        <span data-ttu-id="56fe3-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span><span class="sxs-lookup"><span data-stu-id="56fe3-207">Only `Image` and `LabelAsKey` are used to train the model and make predictions.</span></span> <span data-ttu-id="56fe3-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span><span class="sxs-lookup"><span data-stu-id="56fe3-208">The `ImagePath` and `Label` properties are kept for convenience to access the original image file name and category.</span></span>

    1. <span data-ttu-id="56fe3-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-209">Then, below the `ModelInput` class, define the schema of your output data in a new class called `ModelOutput`.</span></span>

        [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L155-L162)]

        <span data-ttu-id="56fe3-210">`ModelOutput` contains the following properties:</span><span class="sxs-lookup"><span data-stu-id="56fe3-210">`ModelOutput` contains the following properties:</span></span>

        - <span data-ttu-id="56fe3-211">`ImagePath` is the fully qualified path where the image is stored.</span><span class="sxs-lookup"><span data-stu-id="56fe3-211">`ImagePath` is the fully qualified path where the image is stored.</span></span>
        - <span data-ttu-id="56fe3-212">`Label` is the original category the image belongs to.</span><span class="sxs-lookup"><span data-stu-id="56fe3-212">`Label` is the original category the image belongs to.</span></span> <span data-ttu-id="56fe3-213">This is the value to predict.</span><span class="sxs-lookup"><span data-stu-id="56fe3-213">This is the value to predict.</span></span>
        - <span data-ttu-id="56fe3-214">`PredictedLabel` is the value predicted by the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-214">`PredictedLabel` is the value predicted by the model.</span></span>

        <span data-ttu-id="56fe3-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-215">Similar to `ModelInput`, only the `PredictedLabel` is required to make predictions since it contains the prediction made by the model.</span></span> <span data-ttu-id="56fe3-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span><span class="sxs-lookup"><span data-stu-id="56fe3-216">The `ImagePath` and `Label` properties are retained for convenience to access the original image file name and category.</span></span>

### <a name="create-workspace-directory"></a><span data-ttu-id="56fe3-217">Create workspace directory</span><span class="sxs-lookup"><span data-stu-id="56fe3-217">Create workspace directory</span></span>

<span data-ttu-id="56fe3-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span><span class="sxs-lookup"><span data-stu-id="56fe3-218">When training and validation data do not change often, it is good practice to cache the computed bottleneck values for further runs.</span></span>

1. <span data-ttu-id="56fe3-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-219">In your project, create a new directory called *workspace* to store the computed bottleneck values and `.pb` version of the model.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="56fe3-220">Define paths and initialize variables</span><span class="sxs-lookup"><span data-stu-id="56fe3-220">Define paths and initialize variables</span></span>

1. <span data-ttu-id="56fe3-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-221">Inside the `Main` method, define the location of your assets, computed bottleneck values and `.pb` version of the model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L15-L17)]

1. <span data-ttu-id="56fe3-222">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span><span class="sxs-lookup"><span data-stu-id="56fe3-222">Then, initialize the `mlContext` variable with a new instance of [MLContext](xref:Microsoft.ML.MLContext).</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L19)]

    <span data-ttu-id="56fe3-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span><span class="sxs-lookup"><span data-stu-id="56fe3-223">The [MLContext](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="56fe3-224">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="56fe3-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="56fe3-225">Charger les données</span><span class="sxs-lookup"><span data-stu-id="56fe3-225">Load the data</span></span>

### <a name="create-data-loading-utility-method"></a><span data-ttu-id="56fe3-226">Create data loading utility method</span><span class="sxs-lookup"><span data-stu-id="56fe3-226">Create data loading utility method</span></span>

<span data-ttu-id="56fe3-227">The images are stored in two subdirectories.</span><span class="sxs-lookup"><span data-stu-id="56fe3-227">The images are stored in two subdirectories.</span></span> <span data-ttu-id="56fe3-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span><span class="sxs-lookup"><span data-stu-id="56fe3-228">Before loading the data, it needs to be formatted into a list of `ImageData` objects.</span></span> <span data-ttu-id="56fe3-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span><span class="sxs-lookup"><span data-stu-id="56fe3-229">To do so, create the `LoadImagesFromDirectory` method below the `Main` method.</span></span>

```csharp
public static IEnumerable<ImageData> LoadImagesFromDirectory(string folder, bool useFolderNameAsLabel = true)
{

}
```

1. <span data-ttu-id="56fe3-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span><span class="sxs-lookup"><span data-stu-id="56fe3-230">Inside the `LoadImagesDirectory` add the following code to get all of the file paths from the subdirectories:</span></span>

    [!code-csharp [GetFiles](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L104-L105)]

1. <span data-ttu-id="56fe3-231">Then, iterate through each of the files using a `foreach` statement.</span><span class="sxs-lookup"><span data-stu-id="56fe3-231">Then, iterate through each of the files using a `foreach` statement.</span></span>

    ```csharp
    foreach (var file in files)
    {

    }
    ```

1. <span data-ttu-id="56fe3-232">Inside the `foreach` statement, check that the file extensions are supported.</span><span class="sxs-lookup"><span data-stu-id="56fe3-232">Inside the `foreach` statement, check that the file extensions are supported.</span></span> <span data-ttu-id="56fe3-233">The Image Classification API supports JPEG and PNG formats.</span><span class="sxs-lookup"><span data-stu-id="56fe3-233">The Image Classification API supports JPEG and PNG formats.</span></span>

    [!code-csharp [CheckExtension](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L109-L110)]

1. <span data-ttu-id="56fe3-234">Then, get the label for the file.</span><span class="sxs-lookup"><span data-stu-id="56fe3-234">Then, get the label for the file.</span></span> <span data-ttu-id="56fe3-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span><span class="sxs-lookup"><span data-stu-id="56fe3-235">If the `useFolderNameAsLabel` parameter is set to `true`, then the parent directory where the file is saved is used as the label.</span></span> <span data-ttu-id="56fe3-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span><span class="sxs-lookup"><span data-stu-id="56fe3-236">Otherwise, it expects the label to be a prefix of the file name or the file name itself.</span></span>

    [!code-csharp [GetLabel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L112-L126)]

1. <span data-ttu-id="56fe3-237">Finally, create a new instance of `ModelInput`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-237">Finally, create a new instance of `ModelInput`.</span></span>

    [!code-csharp [CreateImageData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L128-L132)]

### <a name="prepare-the-data"></a><span data-ttu-id="56fe3-238">Préparer les données</span><span class="sxs-lookup"><span data-stu-id="56fe3-238">Prepare the data</span></span>

1. <span data-ttu-id="56fe3-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span><span class="sxs-lookup"><span data-stu-id="56fe3-239">Back in the `Main` method, use the `LoadFromDirectory` utility method to get the list of images used for training.</span></span>

    [!code-csharp [LoadImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L21)]

1. <span data-ttu-id="56fe3-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span><span class="sxs-lookup"><span data-stu-id="56fe3-240">Then, load the images into an [`IDataView`](xref:Microsoft.ML.IDataView) using the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method.</span></span>

    [!code-csharp [CreateIDataView](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L23)]

1. <span data-ttu-id="56fe3-241">The data is loaded in the order it was read from the directories.</span><span class="sxs-lookup"><span data-stu-id="56fe3-241">The data is loaded in the order it was read from the directories.</span></span> <span data-ttu-id="56fe3-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span><span class="sxs-lookup"><span data-stu-id="56fe3-242">To balance the data, shuffle it using the [`ShuffleRows`](xref:Microsoft.ML.DataOperationsCatalog.ShuffleRows*) method.</span></span>

    [!code-csharp [ShuffleRows](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L25)]

1. <span data-ttu-id="56fe3-243">Machine learning models expect input to be in numerical format.</span><span class="sxs-lookup"><span data-stu-id="56fe3-243">Machine learning models expect input to be in numerical format.</span></span> <span data-ttu-id="56fe3-244">Therefore, some preprocessing needs to be done on the data prior to training.</span><span class="sxs-lookup"><span data-stu-id="56fe3-244">Therefore, some preprocessing needs to be done on the data prior to training.</span></span> <span data-ttu-id="56fe3-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span><span class="sxs-lookup"><span data-stu-id="56fe3-245">Create an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) made up of the [`MapValueToKey`](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey*) and `LoadRawImageBytes` transforms.</span></span> <span data-ttu-id="56fe3-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-246">The `MapValueToKey` transform takes the categorical value in the `Label` column, converts it to a numerical `KeyType` value and stores it in a new column called `LabelAsKey`.</span></span> <span data-ttu-id="56fe3-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span><span class="sxs-lookup"><span data-stu-id="56fe3-247">The `LoadImages` takes the values from the `ImagePath` column along with the `imageFolder` parameter to load images for training.</span></span>

    [!code-csharp [PreprocessingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L27-L33)]

1. <span data-ttu-id="56fe3-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span><span class="sxs-lookup"><span data-stu-id="56fe3-248">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to apply the data to the `preprocessingPipeline` [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) followed by the [`Transform`](xref:Microsoft.ML.Data.TransformerChain`1.Transform*) method, which returns an [`IDataView`](xref:Microsoft.ML.IDataView) containing the pre-processed data.</span></span>

    [!code-csharp [PreprocessData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L35-L37)]

1. <span data-ttu-id="56fe3-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span><span class="sxs-lookup"><span data-stu-id="56fe3-249">To train a model, it's important to have a training dataset as well as a validation dataset.</span></span> <span data-ttu-id="56fe3-250">The model is trained on the training set.</span><span class="sxs-lookup"><span data-stu-id="56fe3-250">The model is trained on the training set.</span></span> <span data-ttu-id="56fe3-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span><span class="sxs-lookup"><span data-stu-id="56fe3-251">How well it makes predictions on unseen data is measured by the performance against the validation set.</span></span> <span data-ttu-id="56fe3-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span><span class="sxs-lookup"><span data-stu-id="56fe3-252">Based on the results of that performance, the model makes adjustments to what it has learned in an effort to improve.</span></span> <span data-ttu-id="56fe3-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span><span class="sxs-lookup"><span data-stu-id="56fe3-253">The validation set can come from either splitting your original dataset or from another source that has already been set aside for this purpose.</span></span> <span data-ttu-id="56fe3-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span><span class="sxs-lookup"><span data-stu-id="56fe3-254">In this case, the pre-processed dataset is split into training, validation and test sets.</span></span>

    [!code-csharp [CreateDataSplits](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L39-L40)]

    <span data-ttu-id="56fe3-255">The code sample above performs two splits.</span><span class="sxs-lookup"><span data-stu-id="56fe3-255">The code sample above performs two splits.</span></span> <span data-ttu-id="56fe3-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span><span class="sxs-lookup"><span data-stu-id="56fe3-256">First, the pre-processed data is split and 70% is used for training while the remaining 30% is used for validation.</span></span> <span data-ttu-id="56fe3-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span><span class="sxs-lookup"><span data-stu-id="56fe3-257">Then, the 30% validation set is further split into validation and test sets where 90% is used for validation and 10% is used for testing.</span></span>

    <span data-ttu-id="56fe3-258">A way to think about the purpose of these data partitions is taking an exam.</span><span class="sxs-lookup"><span data-stu-id="56fe3-258">A way to think about the purpose of these data partitions is taking an exam.</span></span> <span data-ttu-id="56fe3-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span><span class="sxs-lookup"><span data-stu-id="56fe3-259">When studying for an exam, you review your notes, books, or other resources to get a grasp on the concepts that are on the exam.</span></span> <span data-ttu-id="56fe3-260">This is what the train set is for.</span><span class="sxs-lookup"><span data-stu-id="56fe3-260">This is what the train set is for.</span></span> <span data-ttu-id="56fe3-261">Then, you might take a mock exam to validate your knowledge.</span><span class="sxs-lookup"><span data-stu-id="56fe3-261">Then, you might take a mock exam to validate your knowledge.</span></span> <span data-ttu-id="56fe3-262">This is where the validation set comes in handy.</span><span class="sxs-lookup"><span data-stu-id="56fe3-262">This is where the validation set comes in handy.</span></span> <span data-ttu-id="56fe3-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span><span class="sxs-lookup"><span data-stu-id="56fe3-263">You want to check whether you have a good grasp of the concepts before taking the actual exam.</span></span> <span data-ttu-id="56fe3-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span><span class="sxs-lookup"><span data-stu-id="56fe3-264">Based on those results, you take note of what you got wrong or didn't understand well and incorporate your changes as you review for the real exam.</span></span> <span data-ttu-id="56fe3-265">Finally, you take the exam.</span><span class="sxs-lookup"><span data-stu-id="56fe3-265">Finally, you take the exam.</span></span> <span data-ttu-id="56fe3-266">This is what the test set is used for.</span><span class="sxs-lookup"><span data-stu-id="56fe3-266">This is what the test set is used for.</span></span> <span data-ttu-id="56fe3-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span><span class="sxs-lookup"><span data-stu-id="56fe3-267">You've never seen the questions that are on the exam and now use what you learned from training and validation to apply your knowledge to the task at hand.</span></span>

1. <span data-ttu-id="56fe3-268">Assign the partitions their respective values for the train, validation and test data.</span><span class="sxs-lookup"><span data-stu-id="56fe3-268">Assign the partitions their respective values for the train, validation and test data.</span></span>

    [!code-csharp [CreateDatasets](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L42-L44)]

## <a name="define-the-training-pipeline"></a><span data-ttu-id="56fe3-269">Define the training pipeline</span><span class="sxs-lookup"><span data-stu-id="56fe3-269">Define the training pipeline</span></span>

<span data-ttu-id="56fe3-270">Model training consists of a couple of steps.</span><span class="sxs-lookup"><span data-stu-id="56fe3-270">Model training consists of a couple of steps.</span></span> <span data-ttu-id="56fe3-271">First, Image Classification API is used to train the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-271">First, Image Classification API is used to train the model.</span></span> <span data-ttu-id="56fe3-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span><span class="sxs-lookup"><span data-stu-id="56fe3-272">Then, the encoded labels in the `PredictedLabel` column are converted back to their original categorical value using the `MapKeyToValue` transform.</span></span>

1. <span data-ttu-id="56fe3-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-273">Create a new variable to store a set of required and optional parameters for an `ImageClassificationTrainer`.</span></span> 

    [!code-csharp [ClassifierOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L46-L57)]

    <span data-ttu-id="56fe3-274">An `ImageClassificationTrainer` takes several optional parameters:</span><span class="sxs-lookup"><span data-stu-id="56fe3-274">An `ImageClassificationTrainer` takes several optional parameters:</span></span>

    - <span data-ttu-id="56fe3-275">`FeatureColumnName` is the column that is used as input for the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-275">`FeatureColumnName` is the column that is used as input for the model.</span></span>
    - <span data-ttu-id="56fe3-276">`LabelColumnName` is the column for the value to predict.</span><span class="sxs-lookup"><span data-stu-id="56fe3-276">`LabelColumnName` is the column for the value to predict.</span></span>
    - <span data-ttu-id="56fe3-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span><span class="sxs-lookup"><span data-stu-id="56fe3-277">`ValidationSet` is the [`IDataView`](xref:Microsoft.ML.IDataView) containing the validation data.</span></span>
    - <span data-ttu-id="56fe3-278">`Arch` defines which of the pretrained model architectures to use.</span><span class="sxs-lookup"><span data-stu-id="56fe3-278">`Arch` defines which of the pretrained model architectures to use.</span></span> <span data-ttu-id="56fe3-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-279">This tutorial uses the 101-layer variant of the ResNetv2 model.</span></span>
    - <span data-ttu-id="56fe3-280">`MetricsCallback` binds a function to track the progress during training.</span><span class="sxs-lookup"><span data-stu-id="56fe3-280">`MetricsCallback` binds a function to track the progress during training.</span></span>
    - <span data-ttu-id="56fe3-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span><span class="sxs-lookup"><span data-stu-id="56fe3-281">`TestOnTrainSet` tells the model to measure performance against the training set when no validation set is present.</span></span>
    - <span data-ttu-id="56fe3-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span><span class="sxs-lookup"><span data-stu-id="56fe3-282">`ReuseTrainSetBottleneckCachedValues` tells the model whether to use the cached values from the bottleneck phase in subsequent runs.</span></span> <span data-ttu-id="56fe3-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span><span class="sxs-lookup"><span data-stu-id="56fe3-283">The bottleneck phase is a one-time pass-through computation that is computationally intensive the first time it is performed.</span></span> <span data-ttu-id="56fe3-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-284">If the training data does not change and you want to experiment using a different number of epochs or batch size, using the cached values significantly reduces the amount of time required to train a model.</span></span>
    - <span data-ttu-id="56fe3-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span><span class="sxs-lookup"><span data-stu-id="56fe3-285">`ReuseValidationSetBottleneckCachedValues` is similar to `ReuseTrainSetBottleneckCachedValues` only that in this case it's for the validation dataset.</span></span>
    - <span data-ttu-id="56fe3-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-286">`WorkspacePath` defines the directory where to store the computed bottleneck values and `.pb` version of the model.</span></span>

1. <span data-ttu-id="56fe3-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-287">Define the [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) training pipeline that consists of both the `mapLabelEstimator` and the `ImageClassificationTrainer`.</span></span>

    [!code-csharp [TrainingPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L59-L60)]

1. <span data-ttu-id="56fe3-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-288">Use the [`Fit`](xref:Microsoft.ML.Data.EstimatorChain%601.Fit*) method to train your model.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L62)]

## <a name="use-the-model"></a><span data-ttu-id="56fe3-289">Utiliser le modèle</span><span class="sxs-lookup"><span data-stu-id="56fe3-289">Use the model</span></span>

<span data-ttu-id="56fe3-290">Now that you have trained your model, it's time to use it to classify images.</span><span class="sxs-lookup"><span data-stu-id="56fe3-290">Now that you have trained your model, it's time to use it to classify images.</span></span>

<span data-ttu-id="56fe3-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span><span class="sxs-lookup"><span data-stu-id="56fe3-291">Below the `Main` method, create a new utility method called `OutputPrediction` to display prediction information in the console.</span></span>

[!code-csharp [OuputPredictionMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L96-L100)]

### <a name="classify-a-single-image"></a><span data-ttu-id="56fe3-292">Classify a single image</span><span class="sxs-lookup"><span data-stu-id="56fe3-292">Classify a single image</span></span>

1. <span data-ttu-id="56fe3-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span><span class="sxs-lookup"><span data-stu-id="56fe3-293">Add a new method called `ClassifySingleImage` below the `Main` method to make and output a single image prediction.</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="56fe3-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span><span class="sxs-lookup"><span data-stu-id="56fe3-294">Create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) inside the `ClassifySingleImage` method.</span></span> <span data-ttu-id="56fe3-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span><span class="sxs-lookup"><span data-stu-id="56fe3-295">The [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

    [!code-csharp [CreatePredictionEngine](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L73)]

1. <span data-ttu-id="56fe3-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span><span class="sxs-lookup"><span data-stu-id="56fe3-296">To access a single `ModelInput` instance, convert the `data` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first observation.</span></span>

    [!code-csharp [GetTestInputData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L75)]

1. <span data-ttu-id="56fe3-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span><span class="sxs-lookup"><span data-stu-id="56fe3-297">Use the [`Predict`](xref:Microsoft.ML.PredictionEngine%602.Predict*) method to classify the image.</span></span>

    [!code-csharp [MakeSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L77)]

1. <span data-ttu-id="56fe3-298">Output the prediction to the console with the `OutputPrediction` method.</span><span class="sxs-lookup"><span data-stu-id="56fe3-298">Output the prediction to the console with the `OutputPrediction` method.</span></span>

    [!code-csharp [OuputSinglePrediction](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L79-L80)]

1. <span data-ttu-id="56fe3-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span><span class="sxs-lookup"><span data-stu-id="56fe3-299">Inside the `Main` method, call `ClassifySingleImage` using the test set of images.</span></span>

    [!code-csharp [ClassifySingleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L64)]

### <a name="classify-multiple-images"></a><span data-ttu-id="56fe3-300">Classify multiple images</span><span class="sxs-lookup"><span data-stu-id="56fe3-300">Classify multiple images</span></span>

1. <span data-ttu-id="56fe3-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span><span class="sxs-lookup"><span data-stu-id="56fe3-301">Add a new method called `ClassifyImages` below the `ClassifySingleImage` method to make and output multiple image predictions.</span></span>

    ```csharp
    public static void ClassifyImages(MLContext mlContext, IDataView data, ITransformer trainedModel)
    {

    }
    ```

1. <span data-ttu-id="56fe3-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span><span class="sxs-lookup"><span data-stu-id="56fe3-302">Create an [`IDataView`](xref:Microsoft.ML.IDataView) containing the predictions by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method.</span></span> <span data-ttu-id="56fe3-303">Ajoutez le code suivant dans la méthode `ClassifyImages`.</span><span class="sxs-lookup"><span data-stu-id="56fe3-303">Add the following code inside the `ClassifyImages` method.</span></span>

    [!code-csharp [MakeMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L85)]

1. <span data-ttu-id="56fe3-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span><span class="sxs-lookup"><span data-stu-id="56fe3-304">In order to iterate over the predictions, convert the `predictionData` [`IDataView`](xref:Microsoft.ML.IDataView) into an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method and then get the first 10 observations.</span></span>

    [!code-csharp [IEnumerablePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L87)]

1. <span data-ttu-id="56fe3-305">Iterate and output the original and predicted labels for the predictions.</span><span class="sxs-lookup"><span data-stu-id="56fe3-305">Iterate and output the original and predicted labels for the predictions.</span></span>

    [!code-csharp [OutputMultiplePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L89-L93)]

1. <span data-ttu-id="56fe3-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span><span class="sxs-lookup"><span data-stu-id="56fe3-306">Finally, inside the `Main` method, call `ClassifyImages` using the test set of images.</span></span>

    [!code-csharp [ClassifyImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ImageClassification_Binary/DeepLearning_ImageClassification_Binary/Program.cs#L66)]

## <a name="run-the-application"></a><span data-ttu-id="56fe3-307">Exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="56fe3-307">Run the application</span></span>

<span data-ttu-id="56fe3-308">Run your console app.</span><span class="sxs-lookup"><span data-stu-id="56fe3-308">Run your console app.</span></span> <span data-ttu-id="56fe3-309">The output should be similar to that below.</span><span class="sxs-lookup"><span data-stu-id="56fe3-309">The output should be similar to that below.</span></span> <span data-ttu-id="56fe3-310">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="56fe3-310">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span> <span data-ttu-id="56fe3-311">For brevity, the output has been condensed.</span><span class="sxs-lookup"><span data-stu-id="56fe3-311">For brevity, the output has been condensed.</span></span>

<span data-ttu-id="56fe3-312">**Bottleneck phase**</span><span class="sxs-lookup"><span data-stu-id="56fe3-312">**Bottleneck phase**</span></span>

<span data-ttu-id="56fe3-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span><span class="sxs-lookup"><span data-stu-id="56fe3-313">No value is printed for the image name because the images are loaded as a `byte[]` therefore there is no image name to display.</span></span>

```test
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 279
Phase: Bottleneck Computation, Dataset used:      Train, Image Index: 280
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   1
Phase: Bottleneck Computation, Dataset used: Validation, Image Index:   2
```

<span data-ttu-id="56fe3-314">**Training phase**</span><span class="sxs-lookup"><span data-stu-id="56fe3-314">**Training phase**</span></span>

```text
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  21, Accuracy:  0.6797619
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  22, Accuracy:  0.7642857
Phase: Training, Dataset used: Validation, Batch Processed Count:   6, Epoch:  23, Accuracy:  0.7916667
```

<span data-ttu-id="56fe3-315">**Classify images output**</span><span class="sxs-lookup"><span data-stu-id="56fe3-315">**Classify images output**</span></span>

```text
Classifying single image
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD

Classifying multiple images
Image: 7001-220.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-163.jpg | Actual Value: UD | Predicted Value: UD
Image: 7001-210.jpg | Actual Value: UD | Predicted Value: UD
```

<span data-ttu-id="56fe3-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span><span class="sxs-lookup"><span data-stu-id="56fe3-316">Upon inspection of the *7001-220.jpg* image, you can see that it in fact is not cracked.</span></span>

![SDNET2018 dataset image used for prediction](./media/image-classification-api-transfer-learning/predictedimage.jpg)

<span data-ttu-id="56fe3-318">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="56fe3-318">Congratulations!</span></span> <span data-ttu-id="56fe3-319">You've now successfully built a deep learning model for classifying images.</span><span class="sxs-lookup"><span data-stu-id="56fe3-319">You've now successfully built a deep learning model for classifying images.</span></span>

### <a name="improve-the-model"></a><span data-ttu-id="56fe3-320">Improve the model</span><span class="sxs-lookup"><span data-stu-id="56fe3-320">Improve the model</span></span>

<span data-ttu-id="56fe3-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span><span class="sxs-lookup"><span data-stu-id="56fe3-321">If you're not satisfied with the results of your model, you can try to improve its performance by trying some of the following approaches:</span></span>

- <span data-ttu-id="56fe3-322">**More Data**: The more examples a model learns from, the better it performs.</span><span class="sxs-lookup"><span data-stu-id="56fe3-322">**More Data**: The more examples a model learns from, the better it performs.</span></span> <span data-ttu-id="56fe3-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span><span class="sxs-lookup"><span data-stu-id="56fe3-323">Download the full [SDNET2018 dataset](https://digitalcommons.usu.edu/cgi/viewcontent.cgi?filename=2&article=1047&context=all_datasets&type=additional) and use it to train.</span></span>
- <span data-ttu-id="56fe3-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span><span class="sxs-lookup"><span data-stu-id="56fe3-324">**Augment the data**: A common technique to add variety to the data is to augment the data by taking an image and applying different transforms (rotate, flip, shift, crop).</span></span> <span data-ttu-id="56fe3-325">This adds more varied examples for the model to learn from.</span><span class="sxs-lookup"><span data-stu-id="56fe3-325">This adds more varied examples for the model to learn from.</span></span>
- <span data-ttu-id="56fe3-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span><span class="sxs-lookup"><span data-stu-id="56fe3-326">**Train for a longer time**: The longer you train, the more tuned the model will be.</span></span> <span data-ttu-id="56fe3-327">Increasing the number of epochs may improve the performance of your model.</span><span class="sxs-lookup"><span data-stu-id="56fe3-327">Increasing the number of epochs may improve the performance of your model.</span></span>
- <span data-ttu-id="56fe3-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span><span class="sxs-lookup"><span data-stu-id="56fe3-328">**Experiment with the hyper-parameters**: In addition to the parameters used in this tutorial, other parameters can be tuned to potentially improve performance.</span></span> <span data-ttu-id="56fe3-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span><span class="sxs-lookup"><span data-stu-id="56fe3-329">Changing the learning rate, which determines the magnitude of updates made to the model after each epoch may improve performance.</span></span>
- <span data-ttu-id="56fe3-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span><span class="sxs-lookup"><span data-stu-id="56fe3-330">**Use a different model architecture**: Depending on what your data looks like, the model that can best learn its features may differ.</span></span> <span data-ttu-id="56fe3-331">If you're not satisfied with the performance of your model, try changing the architecture.</span><span class="sxs-lookup"><span data-stu-id="56fe3-331">If you're not satisfied with the performance of your model, try changing the architecture.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="56fe3-332">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="56fe3-332">Additional Resources</span></span>

- <span data-ttu-id="56fe3-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span><span class="sxs-lookup"><span data-stu-id="56fe3-333">[Deep Learning vs Machine Learning](/azure/machine-learning/service/concept-deep-learning-vs-machine-learning).</span></span>

## <a name="next-steps"></a><span data-ttu-id="56fe3-334">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="56fe3-334">Next steps</span></span>

<span data-ttu-id="56fe3-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span><span class="sxs-lookup"><span data-stu-id="56fe3-335">In this tutorial, you learned how to build a custom deep learning model using transfer learning, a pretrained image classification TensorFlow model and the ML.NET Image Classification API to classify images of concrete surfaces as cracked or uncracked.</span></span>

<span data-ttu-id="56fe3-336">Passez au tutoriel suivant pour en savoir plus.</span><span class="sxs-lookup"><span data-stu-id="56fe3-336">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56fe3-337">Object Detection</span><span class="sxs-lookup"><span data-stu-id="56fe3-337">Object Detection</span></span>](object-detection-onnx.md)
