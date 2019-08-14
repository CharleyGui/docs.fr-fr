---
title: 'Tutoriel : Détecter des objets à l’aide du deep learning avec ONNX et ML.NET'
description: Ce tutoriel montre comment utiliser un modèle de deep learning ONNX préentraîné dans ML.NET pour détecter des objets dans des images.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/01/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 3e5b6b482dfbd1ff06347883a93a561944200a9f
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733397"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="8adf4-103">Tutoriel : Détecter des objets avec ONNX dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="8adf4-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="8adf4-104">Découvrez comment utiliser un modèle ONNX préentraîné dans ML.NET pour détecter des objets dans des images.</span><span class="sxs-lookup"><span data-stu-id="8adf4-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="8adf4-105">L’entraînement d’un modèle de détection d’objets à partir de zéro nécessite de définir des millions de paramètres et d’avoir un grand nombre de données d’entraînement étiquetées et de ressources de calcul (des centaines d’heures GPU).</span><span class="sxs-lookup"><span data-stu-id="8adf4-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="8adf4-106">L’utilisation d’un modèle préentraîné vous permet de raccourcir le processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="8adf4-107">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="8adf4-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8adf4-108">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="8adf4-108">Understand the problem</span></span>
> * <span data-ttu-id="8adf4-109">Découvrir ce qu’est ONNX et comment il fonctionne avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="8adf4-109">Learn what ONNX is and how it works with ML.NET</span></span>
> * <span data-ttu-id="8adf4-110">Comprendre le modèle</span><span class="sxs-lookup"><span data-stu-id="8adf4-110">Understand the model</span></span>
> * <span data-ttu-id="8adf4-111">Réutiliser le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="8adf4-111">Reuse the pre-trained model</span></span>
> * <span data-ttu-id="8adf4-112">Détecter les objets avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="8adf4-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="8adf4-113">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8adf4-113">Pre-requisites</span></span>

- <span data-ttu-id="8adf4-114">[Visual Studio 2017 15.6 ou ultérieur](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="8adf4-115">Package NuGet Microsoft.ML</span><span class="sxs-lookup"><span data-stu-id="8adf4-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="8adf4-116">Package NuGet Microsoft.ML.ImageAnalytics</span><span class="sxs-lookup"><span data-stu-id="8adf4-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="8adf4-117">Package NuGet Microsoft.ML.OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="8adf4-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="8adf4-118">Modèle préentraîné Tiny YOLOv2</span><span class="sxs-lookup"><span data-stu-id="8adf4-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/tiny_yolov2)
- <span data-ttu-id="8adf4-119">[Netron](https://github.com/lutzroeder/netron) (facultatif)</span><span class="sxs-lookup"><span data-stu-id="8adf4-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="8adf4-120">Vue d’ensemble de l’exemple de détection d’objets ONNX</span><span class="sxs-lookup"><span data-stu-id="8adf4-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="8adf4-121">Cet exemple crée une application console .NET Core qui détecte les objets dans une image à l’aide d’un modèle ONNX de deep learning préentraîné.</span><span class="sxs-lookup"><span data-stu-id="8adf4-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="8adf4-122">Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="8adf4-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="8adf4-123">Qu’est-ce que la détection d’objets ?</span><span class="sxs-lookup"><span data-stu-id="8adf4-123">What is object detection?</span></span>

<span data-ttu-id="8adf4-124">La détection d’objets est un problème de vision par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8adf4-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="8adf4-125">Même si elle est étroitement liée à la classification d’images, la détection d’objets effectue une classification d’images à une échelle plus précise.</span><span class="sxs-lookup"><span data-stu-id="8adf4-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="8adf4-126">La détection d’objets localise _et_ catégorise les entités dans les images.</span><span class="sxs-lookup"><span data-stu-id="8adf4-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="8adf4-127">Utilisez la détection d’objets quand les images contiennent plusieurs objets de différents types.</span><span class="sxs-lookup"><span data-stu-id="8adf4-127">Use object detection when images contain multiple objects of different types.</span></span>

![](./media/object-detection-onnx/img-classification-obj-detection.PNG)

<span data-ttu-id="8adf4-128">Voici quelques cas d’utilisation de la détection d’objets :</span><span class="sxs-lookup"><span data-stu-id="8adf4-128">Some use cases for object detection include:</span></span>

- <span data-ttu-id="8adf4-129">Voitures autonomes</span><span class="sxs-lookup"><span data-stu-id="8adf4-129">Self-Driving Cars</span></span>
- <span data-ttu-id="8adf4-130">Robotique</span><span class="sxs-lookup"><span data-stu-id="8adf4-130">Robotics</span></span>
- <span data-ttu-id="8adf4-131">Détection de visage</span><span class="sxs-lookup"><span data-stu-id="8adf4-131">Face Detection</span></span>
- <span data-ttu-id="8adf4-132">Sécurité des espaces de travail</span><span class="sxs-lookup"><span data-stu-id="8adf4-132">Workplace Safety</span></span>
- <span data-ttu-id="8adf4-133">Dénombrement des objets</span><span class="sxs-lookup"><span data-stu-id="8adf4-133">Object Counting</span></span>
- <span data-ttu-id="8adf4-134">Reconnaissance des activités</span><span class="sxs-lookup"><span data-stu-id="8adf4-134">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="8adf4-135">Sélectionner un modèle de deep learning</span><span class="sxs-lookup"><span data-stu-id="8adf4-135">Select a deep learning model</span></span>

<span data-ttu-id="8adf4-136">Le deep learning fait partie du machine learning.</span><span class="sxs-lookup"><span data-stu-id="8adf4-136">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="8adf4-137">Pour entraîner des modèles de deep learning, de grandes quantités de données sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="8adf4-137">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="8adf4-138">Les différents motifs (patterns) de données sont représentés par une série de couches.</span><span class="sxs-lookup"><span data-stu-id="8adf4-138">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="8adf4-139">Les relations dans les données sont encodées en tant que connexions entre les couches contenant des poids.</span><span class="sxs-lookup"><span data-stu-id="8adf4-139">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="8adf4-140">Plus le poids est élevé, plus la relation est forte.</span><span class="sxs-lookup"><span data-stu-id="8adf4-140">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="8adf4-141">Collectivement, cette série de couches et de connexions est connue sous le nom de réseaux neuronaux artificiels.</span><span class="sxs-lookup"><span data-stu-id="8adf4-141">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="8adf4-142">Plus le nombre de couches d’un réseau est élevé, plus il est profond, ce qui en fait un réseau neuronal profond.</span><span class="sxs-lookup"><span data-stu-id="8adf4-142">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span> 

<span data-ttu-id="8adf4-143">Il existe différents types de réseaux neuronaux, les plus courants étant les perceptrons multicouches (MLP), les réseaux de neurones convolutifs (CNN) et les réseaux de neurones récurrents (RNN).</span><span class="sxs-lookup"><span data-stu-id="8adf4-143">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="8adf4-144">Le plus simple est le MLP, qui mappe un ensemble d’entrées à un ensemble de sorties.</span><span class="sxs-lookup"><span data-stu-id="8adf4-144">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="8adf4-145">Ce réseau neuronal est parfait quand les données n’ont pas de composant spatial ou temporel.</span><span class="sxs-lookup"><span data-stu-id="8adf4-145">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="8adf4-146">Le réseau CNN utilise des couches convolutives pour traiter les informations spatiales contenues dans les données.</span><span class="sxs-lookup"><span data-stu-id="8adf4-146">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="8adf4-147">Un bon cas d’utilisation des réseaux CNN est le traitement d’images pour détecter la présence d’une caractéristique dans une zone d’une image (par exemple, y a-t-il un nez au centre d’une image ?).</span><span class="sxs-lookup"><span data-stu-id="8adf4-147">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="8adf4-148">Enfin, les réseaux RNN autorisent la persistance de l’état ou de la mémoire à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-148">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="8adf4-149">Ils sont utilisés pour l’analyse des séries chronologiques, où le tri séquentiel et le contexte des événements sont importants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-149">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span> 

### <a name="understand-the-model"></a><span data-ttu-id="8adf4-150">Comprendre le modèle</span><span class="sxs-lookup"><span data-stu-id="8adf4-150">Understand the model</span></span>

<span data-ttu-id="8adf4-151">La détection d’objets est une tâche de traitement d’images.</span><span class="sxs-lookup"><span data-stu-id="8adf4-151">Object detection is an image processing task.</span></span> <span data-ttu-id="8adf4-152">C’est pourquoi la plupart des modèles de deep learning préentraînés pour résoudre ce problème sont des réseaux CNN.</span><span class="sxs-lookup"><span data-stu-id="8adf4-152">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="8adf4-153">Le modèle utilisé dans ce tutoriel est le modèle Tiny YOLOv2, une version plus compacte du modèle YOLOv2 décrite dans le livre blanc : ["YOLO9000: Better, Faster, Stronger" de Redmon et Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="8adf4-153">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="8adf4-154">Tiny YOLOv2 est entraîné sur le jeu de données Pascal COV et est constitué de 15 couches qui peuvent prédire 20 classes différentes d’objets.</span><span class="sxs-lookup"><span data-stu-id="8adf4-154">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="8adf4-155">Étant donné que Tiny YOLOv2 est une version condensée du modèle YOLOv2 d’origine, un compromis est établi entre la vitesse et la précision.</span><span class="sxs-lookup"><span data-stu-id="8adf4-155">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="8adf4-156">Les différentes couches qui composent le modèle peuvent être visualisées à l’aide d’outils comme Netron.</span><span class="sxs-lookup"><span data-stu-id="8adf4-156">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="8adf4-157">L’inspection du modèle produit un mappage des connexions entre toutes les couches qui composent le réseau neuronal, où chaque couche contient le nom de la couche ainsi que les dimensions des entrée/sortie respectives.</span><span class="sxs-lookup"><span data-stu-id="8adf4-157">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="8adf4-158">Les structures de données utilisées pour décrire les entrées et les sorties du modèle sont appelées des tenseurs.</span><span class="sxs-lookup"><span data-stu-id="8adf4-158">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="8adf4-159">Les tenseurs peuvent être considérés comme des conteneurs qui stockent des données dans N dimensions.</span><span class="sxs-lookup"><span data-stu-id="8adf4-159">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="8adf4-160">Dans le cas de Tiny YOLOv2, le nom de la couche d’entrée est `image` et il attend un tenseur de dimensions `3 x 416 x 416`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-160">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="8adf4-161">Le nom de la couche de sortie est `grid` et génère un tenseur de sortie de dimensions `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-161">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>  

![](./media/object-detection-onnx/netron-model-map.png)

<span data-ttu-id="8adf4-162">Le modèle YOLO prend une image `3(RGB) x 416px x 416px`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-162">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="8adf4-163">Le modèle prend cette entrée et la passe à travers les différentes couches pour produire une sortie.</span><span class="sxs-lookup"><span data-stu-id="8adf4-163">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="8adf4-164">La sortie divise l’image d’entrée en une grille `13 x 13`, chaque cellule de la grille contenant les valeurs `125`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-164">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span> 

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="8adf4-165">Qu’est-ce qu’un modèle ONNX ?</span><span class="sxs-lookup"><span data-stu-id="8adf4-165">What is an ONNX model?</span></span>

<span data-ttu-id="8adf4-166">ONNX (Open Neural Network Exchange) est un format open source pour les modèles IA.</span><span class="sxs-lookup"><span data-stu-id="8adf4-166">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="8adf4-167">ONNX prend en charge l’interopérabilité entre les frameworks.</span><span class="sxs-lookup"><span data-stu-id="8adf4-167">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="8adf4-168">Cela signifie que vous pouvez entraîner un modèle dans l’un des nombreux frameworks de machine learning connus tels que PyTorch, le convertir au format ONNX et consommer le modèle ONNX dans un autre framework comme ML.NET.</span><span class="sxs-lookup"><span data-stu-id="8adf4-168">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="8adf4-169">Pour en savoir plus, consultez le [site web ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="8adf4-169">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span> 

![](./media/object-detection-onnx/onnx-frameworks.png)

<span data-ttu-id="8adf4-170">Le modèle Tiny YOLOv2 préentraîné est stocké au format ONNX, représentation sérialisée des couches et des motifs appris de ces couches.</span><span class="sxs-lookup"><span data-stu-id="8adf4-170">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="8adf4-171">Dans ML.NET, l’interopérabilité avec ONNX s’obtient avec les packages NuGet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) et [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer).</span><span class="sxs-lookup"><span data-stu-id="8adf4-171">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="8adf4-172">Le package[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) contient une série de transformations qui prennent une image et l’encodent en valeurs numériques pouvant être utilisées comme entrée dans un pipeline de prédiction ou d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-172">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="8adf4-173">Le package [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) tire profit du runtime ONNX afin de charger un modèle ONNX et de l’utiliser pour faire des prédictions en fonction de l’entrée fournie.</span><span class="sxs-lookup"><span data-stu-id="8adf4-173">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span> 

![](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="8adf4-174">Configurer le projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="8adf4-174">Set up the .NET Core project</span></span>

<span data-ttu-id="8adf4-175">Maintenant que vous avez une compréhension générale de ce qu’est ONNX et de la façon dont Tiny YOLOv2 fonctionne, il est temps de générer l’application.</span><span class="sxs-lookup"><span data-stu-id="8adf4-175">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="8adf4-176">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="8adf4-176">Create a console application</span></span>

1. <span data-ttu-id="8adf4-177">Créez une **application console .NET Core** appelée « ObjectDetection ».</span><span class="sxs-lookup"><span data-stu-id="8adf4-177">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="8adf4-178">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="8adf4-178">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="8adf4-179">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-179">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> 
    - <span data-ttu-id="8adf4-180">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-180">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> 
    - <span data-ttu-id="8adf4-181">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-181">Select the **Install** button.</span></span> 
    - <span data-ttu-id="8adf4-182">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="8adf4-182">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> 
    - <span data-ttu-id="8adf4-183">Répétez ces étapes pour **Microsoft.ML.ImageAnalytics** et **Microsoft.ML.OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-183">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="8adf4-184">Préparer vos données et votre modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="8adf4-184">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="8adf4-185">Téléchargez le [fichier zip du répertoire de ressources du projet ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="8adf4-185">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="8adf4-186">Copiez le répertoire `assets` dans votre répertoire de projet *ObjectDetection*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-186">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="8adf4-187">Ce répertoire et ses sous-répertoires contiennent les fichiers image nécessaires à ce tutoriel (sauf pour le modèle Tiny YOLOv2, que vous allez télécharger et ajouter à l’étape suivante).</span><span class="sxs-lookup"><span data-stu-id="8adf4-187">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="8adf4-188">Téléchargez le [modèle Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) depuis [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="8adf4-188">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="8adf4-189">Ouvrez l’invite de commande et entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8adf4-189">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz 
    ```

1. <span data-ttu-id="8adf4-190">Copiez le fichier `model.onnx` extrait du répertoire que vous venez de décompresser dans le répertoire `assets\Model` de votre projet *ObjectDetection* et renommez-le `TinyYolo2_model.onnx`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-190">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="8adf4-191">Ce répertoire contient le modèle nécessaire pour ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="8adf4-191">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="8adf4-192">Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-192">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="8adf4-193">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-193">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="8adf4-194">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="8adf4-194">Create classes and define paths</span></span>

<span data-ttu-id="8adf4-195">Ouvrez le fichier *Program.cs* et ajoutez les instructions `using` supplémentaires suivantes en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="8adf4-195">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L9)]

<span data-ttu-id="8adf4-196">Ensuite, définissez les chemins des différentes ressources.</span><span class="sxs-lookup"><span data-stu-id="8adf4-196">Next, define the paths of the various assets.</span></span> 

1. <span data-ttu-id="8adf4-197">Tout d’abord, ajoutez la méthode `GetAbsolutePath` sous la méthode `Main` dans la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-197">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span> 

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="8adf4-198">Ensuite, dans la méthode `Main`, créez des champs pour stocker l’emplacement de vos ressources :</span><span class="sxs-lookup"><span data-stu-id="8adf4-198">Then, inside the `Main` method, create fields to store the location of your assets:</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="8adf4-199">Ajoutez un nouveau répertoire à votre projet pour stocker vos données d’entrée et vos classes de prédiction.</span><span class="sxs-lookup"><span data-stu-id="8adf4-199">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="8adf4-200">Dans l’**Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-200">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="8adf4-201">Lorsque le nouveau dossier s’affiche dans l’Explorateur de solutions, nommez-le « DataStructures ».</span><span class="sxs-lookup"><span data-stu-id="8adf4-201">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="8adf4-202">Créez votre classe de données d’entrée dans le répertoire *DataStructures* qui vient d’être créé.</span><span class="sxs-lookup"><span data-stu-id="8adf4-202">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="8adf4-203">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *DataStructures*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-203">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8adf4-204">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-204">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="8adf4-205">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-205">Then, select the **Add** button.</span></span>
     
    <span data-ttu-id="8adf4-206">Le fichier *ImageNetData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8adf4-206">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8adf4-207">Ajoutez l’instruction `using` suivante en haut de *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-207">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="8adf4-208">Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageNetData` au fichier *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-208">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>
    
    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="8adf4-209">`ImageNetData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :</span><span class="sxs-lookup"><span data-stu-id="8adf4-209">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="8adf4-210">`ImagePath` contient le chemin où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-210">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="8adf4-211">`Label` contient le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="8adf4-211">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="8adf4-212">De plus, `ImageNetData` contient une méthode `ReadFromFile` qui charge un grand nombre de fichiers image stockés dans le chemin `imageFolder` spécifié et les retourne sous forme de collection d’objets `ImageNetData`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-212">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="8adf4-213">Créez votre classe de prédiction dans le répertoire *DataStructures*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-213">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="8adf4-214">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *DataStructures*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-214">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8adf4-215">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="8adf4-216">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8adf4-217">Le fichier *ImageNetPrediction.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8adf4-217">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="8adf4-218">Ajoutez l’instruction `using` suivante en haut de *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-218">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="8adf4-219">Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageNetPrediction` au fichier *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-219">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="8adf4-220">`ImageNetPrediction` est la classe de données de prédiction et présente le champ `float[]` suivant :</span><span class="sxs-lookup"><span data-stu-id="8adf4-220">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="8adf4-221">`PredictedLabel` contient les dimensions, le score d’objets et les probabilités de classe pour chacun des rectangles englobants détectés dans une image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-221">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="8adf4-222">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="8adf4-222">Initialize variables in Main</span></span>

<span data-ttu-id="8adf4-223">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-223">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="8adf4-224">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="8adf4-224">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="8adf4-225">Initialisez la variable `mlContext` avec une nouvelle instance de `MLContext` en ajoutant la ligne suivante à la méthode `Main` de *Program.cs* sous le champ `outputFolder`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-225">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

### <a name="add-helper-methods"></a><span data-ttu-id="8adf4-226">Ajouter des méthodes d’assistance</span><span class="sxs-lookup"><span data-stu-id="8adf4-226">Add Helper Methods</span></span>

<span data-ttu-id="8adf4-227">Une fois que le modèle a fait une prédiction, communément appelée scoring, et que les sorties ont été traitées, les rectangles englobants doivent être tracés sur l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-227">After the model has made a prediction, commonly referred to as scoring, and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="8adf4-228">Pour ce faire, ajoutez une méthode appelée `DrawBoundingBox` sous la méthode `GetAbsolutePath` dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-228">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method insode of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="8adf4-229">Tout d’abord, chargez l’image et récupérez les dimensions de hauteur et de largeur dans la méthode `DrawBoundingBox`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-229">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="8adf4-230">Ensuite, créez une boucle for-each pour itérer sur chaque rectangle englobant détecté par le modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-230">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="8adf4-231">À l’intérieur de la boucle for-each, récupérez les dimensions du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-231">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="8adf4-232">Étant donné que les dimensions du rectangle englobant correspondent à l’entrée de modèle de `416 x 416`, adaptez les dimensions du rectangle englobant pour qu’elles correspondent à la taille réelle de l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-232">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="8adf4-233">Ensuite, définissez un modèle pour le texte qui apparaîtra au-dessus de chaque rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-233">Then, define a template for text that will apear above each bounding box.</span></span> <span data-ttu-id="8adf4-234">Le texte contient la classe de l’objet qui se trouve dans le rectangle englobant respectif, ainsi que l’indice de confiance.</span><span class="sxs-lookup"><span data-stu-id="8adf4-234">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="8adf4-235">Pour tracer sur l’image, convertissez-la en objet [`Graphics`](xref:System.Drawing.Graphics).</span><span class="sxs-lookup"><span data-stu-id="8adf4-235">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{
    
}
```

<span data-ttu-id="8adf4-236">Dans le bloc de code `using`, réglez les paramètres d’objet [`Graphics`](xref:System.Drawing.Graphics) du graphique.</span><span class="sxs-lookup"><span data-stu-id="8adf4-236">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="8adf4-237">En dessous, définissez les options de police et de couleur du texte et du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-237">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="8adf4-238">Créez et renseignez un rectangle au-dessus du rectangle englobant pour contenir le texte à l’aide de la méthode [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*).</span><span class="sxs-lookup"><span data-stu-id="8adf4-238">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="8adf4-239">Cela permettra de distinguer le texte et d’améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="8adf4-239">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="8adf4-240">Écrivez ensuite le texte et tracez le rectangle englobant sur l’image en utilisant les méthodes [`DrawString`](xref:System.Drawing.Graphics.DrawString*) et [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*).</span><span class="sxs-lookup"><span data-stu-id="8adf4-240">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="8adf4-241">En dehors de la boucle for-each, ajoutez du code pour enregistrer les images dans `outputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-241">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="8adf4-242">Pour obtenir des commentaires supplémentaires indiquant que l’application fait des prédictions comme prévu au moment de l’exécution, ajoutez une méthode appelée `LogDetectedObjects` sous la méthode `DrawBoundingBox` dans le fichier *Program.cs* pour générer les objets détectés dans la console.</span><span class="sxs-lookup"><span data-stu-id="8adf4-242">To get additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOuptuts](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="8adf4-243">Ces deux méthodes sont utiles lorsque le modèle a généré des sorties et que celles-ci ont été traitées.</span><span class="sxs-lookup"><span data-stu-id="8adf4-243">Both of these methods will be useful when the model has produced outputs and those have been processed.</span></span> <span data-ttu-id="8adf4-244">Toutefois, créez d’abord les fonctionnalités pour traiter les sorties du modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-244">First though, create the functionality to process the model outputs.</span></span>

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="8adf4-245">Créer un analyseur pour le post-traitement des sorties du modèle</span><span class="sxs-lookup"><span data-stu-id="8adf4-245">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="8adf4-246">Le modèle segmente une image dans une grille `13 x 13`, où chaque cellule de grille est `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-246">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="8adf4-247">Chaque cellule de grille contient 5 rectangles englobants d’objet potentiels.</span><span class="sxs-lookup"><span data-stu-id="8adf4-247">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="8adf4-248">Un rectangle englobant a 25 éléments :</span><span class="sxs-lookup"><span data-stu-id="8adf4-248">A bounding box has  25 elements:</span></span>

![](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="8adf4-249">`x` position x du centre du rectangle englobant par rapport à la cellule de grille à laquelle il est associé.</span><span class="sxs-lookup"><span data-stu-id="8adf4-249">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="8adf4-250">`y` position y du centre du rectangle englobant par rapport à la cellule de grille à laquelle il est associé.</span><span class="sxs-lookup"><span data-stu-id="8adf4-250">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="8adf4-251">`w` largeur du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-251">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="8adf4-252">`h` hauteur du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-252">`h` the height of the bounding box.</span></span> 
- <span data-ttu-id="8adf4-253">`o` valeur de confiance qu’un objet existe dans le rectangle englobant, également connue sous le nom de score d’objet.</span><span class="sxs-lookup"><span data-stu-id="8adf4-253">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="8adf4-254">`p1-p20` probabilités de classe pour chacune des 20 classes prédites par le modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-254">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="8adf4-255">Au total, les 25 éléments décrivant chacun des 5 rectangles englobants composent les 125 éléments contenus dans chaque cellule de grille.</span><span class="sxs-lookup"><span data-stu-id="8adf4-255">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="8adf4-256">La sortie générée par le modèle ONNX préentraîné est un tableau de type float de longueur `21125`, représentant les éléments d’un tenseur avec les dimensions `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-256">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="8adf4-257">Pour transformer les prédictions générées par le modèle en tenseur, un travail de post-traitement est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8adf4-257">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="8adf4-258">Pour ce faire, créez un ensemble de classes pour permettre l’analyse de la sortie.</span><span class="sxs-lookup"><span data-stu-id="8adf4-258">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="8adf4-259">Ajoutez un nouveau répertoire à votre projet pour organiser l’ensemble des classes d’analyseur.</span><span class="sxs-lookup"><span data-stu-id="8adf4-259">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="8adf4-260">Dans l’**Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-260">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="8adf4-261">Lorsque le nouveau dossier s’affiche dans l’Explorateur de solutions, nommez-le « YoloParser ».</span><span class="sxs-lookup"><span data-stu-id="8adf4-261">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="8adf4-262">Créer des rectangles englobants et des dimensions</span><span class="sxs-lookup"><span data-stu-id="8adf4-262">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="8adf4-263">Les données générées par le modèle contiennent les coordonnées et les dimensions des rectangles englobants des objets dans l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-263">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="8adf4-264">Créez une classe de base pour les dimensions.</span><span class="sxs-lookup"><span data-stu-id="8adf4-264">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="8adf4-265">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-265">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8adf4-266">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-266">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="8adf4-267">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-267">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8adf4-268">Le fichier *DimensionsBase.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8adf4-268">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="8adf4-269">Supprimez toutes les instructions `using` et la définition de classe existante.</span><span class="sxs-lookup"><span data-stu-id="8adf4-269">Remove all `using` statements and existing class definition.</span></span> 

    <span data-ttu-id="8adf4-270">Ajoutez le code suivant pour la classe `DimensionsBase` au fichier *DimensionsBase.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-270">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="8adf4-271">`DimensionsBase` présente les champs `float` suivants :</span><span class="sxs-lookup"><span data-stu-id="8adf4-271">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="8adf4-272">`X` contient la position de l’objet sur l’axe x.</span><span class="sxs-lookup"><span data-stu-id="8adf4-272">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="8adf4-273">`Y` contient la position de l’objet sur l’axe y.</span><span class="sxs-lookup"><span data-stu-id="8adf4-273">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="8adf4-274">`Height` contient la hauteur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8adf4-274">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="8adf4-275">`Width` contient la largeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="8adf4-275">`Width` contains the width of the object.</span></span>

<span data-ttu-id="8adf4-276">Ensuite, créez une classe pour vos rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-276">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="8adf4-277">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-277">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8adf4-278">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-278">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="8adf4-279">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-279">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8adf4-280">Le fichier *YoloBoundingBox.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8adf4-280">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="8adf4-281">Ajoutez l’instruction `using` suivante en haut de *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-281">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="8adf4-282">Juste au-dessus de la définition de classe existante, ajoutez une nouvelle définition de classe nommée `BoundingBoxDimensions` qui hérite de la classe `DimensionsBase` pour contenir les dimensions du rectangle englobant respectif.</span><span class="sxs-lookup"><span data-stu-id="8adf4-282">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="8adf4-283">Supprimez la définition de classe `YoloBoundingBox` existante et ajoutez le code suivant pour la classe `YoloBoundingBox` au fichier *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-283">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]
    
    <span data-ttu-id="8adf4-284">`YoloBoundingBox` présente les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="8adf4-284">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="8adf4-285">`Dimensions` contient les dimensions du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-285">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="8adf4-286">`Label` contient la classe de l’objet détecté dans le rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-286">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="8adf4-287">`Confidence` contient la valeur de confiance de la classe.</span><span class="sxs-lookup"><span data-stu-id="8adf4-287">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="8adf4-288">`Rect` contient la représentation rectangle des dimensions du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-288">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="8adf4-289">`BoxColor` contient la couleur associée à la classe respective utilisée pour dessiner sur l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-289">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="8adf4-290">Créer l’analyseur</span><span class="sxs-lookup"><span data-stu-id="8adf4-290">Create the parser</span></span>

<span data-ttu-id="8adf4-291">Maintenant que les classes pour les dimensions et les rectangles englobants sont créées, il est temps de créer l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="8adf4-291">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="8adf4-292">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-292">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8adf4-293">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-293">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="8adf4-294">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-294">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8adf4-295">Le fichier *YoloOutputParser.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8adf4-295">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="8adf4-296">Ajoutez l’instruction `using` suivante en haut du fichier *YoloOutputParser.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-296">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="8adf4-297">Dans la définition de la classe `YoloOutputParser` existante, ajoutez une classe imbriquée qui contient les dimensions de chacune des cellules de l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-297">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="8adf4-298">Ajoutez le code suivant pour la classe `CellDimensions` qui hérite de la classe `DimensionsBase` en haut de la définition de la classe `YoloOutputParser`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-298">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="8adf4-299">Dans la définition de la classe `YoloOutputParser`, ajoutez la constante et les champs suivants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-299">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]    

    - <span data-ttu-id="8adf4-300">`ROW_COUNT` est le nombre de lignes dans la grille dans laquelle l’image est divisée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-300">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="8adf4-301">`COL_COUNT` est le nombre de colonnes dans la grille dans laquelle l’image est divisée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-301">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="8adf4-302">`CHANNEL_COUNT` est le nombre total de valeurs contenues dans une cellule de la grille.</span><span class="sxs-lookup"><span data-stu-id="8adf4-302">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="8adf4-303">`BOXES_PER_CELL` est le nombre de rectangles englobants dans une cellule.</span><span class="sxs-lookup"><span data-stu-id="8adf4-303">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="8adf4-304">`BOX_INFO_FEATURE_COUNT` est le nombre de caractéristiques contenues dans un rectangle (x, y, hauteur, largeur, confiance).</span><span class="sxs-lookup"><span data-stu-id="8adf4-304">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="8adf4-305">`CLASS_COUNT` est le nombre de prédictions de classe contenues dans chaque rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-305">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="8adf4-306">`CELL_WIDTH` est la largeur d’une cellule dans la grille de l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-306">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="8adf4-307">`CELL_HEIGHT` est la hauteur d’une cellule dans la grille de l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-307">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="8adf4-308">`channelStride` est la position de départ de la cellule active dans la grille.</span><span class="sxs-lookup"><span data-stu-id="8adf4-308">`channelStride` is the starting position of the current cell in the grid.</span></span>


    <span data-ttu-id="8adf4-309">Lorsque le modèle score une image, il divise l’entrée `416px x 416px` en grille de cellules `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-309">When the model scores an image, it divides the `416px x 416px`input into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="8adf4-310">Chaque cellule contient `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-310">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="8adf4-311">Dans chaque cellule, il y a 5 rectangles englobants contenant chacun 5 caractéristiques (x, y, largeur, hauteur, confiance).</span><span class="sxs-lookup"><span data-stu-id="8adf4-311">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="8adf4-312">Chaque rectangle englobant contient aussi la probabilité de chacune des classes qui, dans le cas présent, est de 20.</span><span class="sxs-lookup"><span data-stu-id="8adf4-312">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="8adf4-313">Par conséquent, chaque cellule contient 125 informations différentes (5 caractéristiques + 20 probabilités de classe).</span><span class="sxs-lookup"><span data-stu-id="8adf4-313">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span> 

<span data-ttu-id="8adf4-314">Créez une liste d’ancres sous `channelStride` pour les 5 rectangles englobants :</span><span class="sxs-lookup"><span data-stu-id="8adf4-314">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]   

<span data-ttu-id="8adf4-315">Les ancres sont des ratios de hauteur et de largeur prédéfinis pour les rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-315">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="8adf4-316">La plupart des objets ou classes détectés par un modèle ont des ratios similaires.</span><span class="sxs-lookup"><span data-stu-id="8adf4-316">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="8adf4-317">C’est utile lorsqu’il s’agit de créer des rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-317">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="8adf4-318">Au lieu de prédire les rectangles englobants, le décalage par rapport aux dimensions prédéfinies est calculé, réduisant ainsi le calcul nécessaire pour prédire le rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-318">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="8adf4-319">En général, ces ratios d’ancre sont calculés en fonction du jeu de données utilisé.</span><span class="sxs-lookup"><span data-stu-id="8adf4-319">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="8adf4-320">Dans ce cas, étant donné que le jeu de données est connu et que les valeurs ont été précalculées, les ancres peuvent être codées en dur.</span><span class="sxs-lookup"><span data-stu-id="8adf4-320">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="8adf4-321">Ensuite, définissez les étiquettes ou les classes que le modèle va prédire.</span><span class="sxs-lookup"><span data-stu-id="8adf4-321">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="8adf4-322">Ce modèle prédit 20 classes, qui est un sous-ensemble du nombre total de classes prédites par le modèle YOLOv2 d’origine.</span><span class="sxs-lookup"><span data-stu-id="8adf4-322">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="8adf4-323">Ajoutez votre liste d’étiquettes sous les `anchors`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-323">Add your list of labels below the `anchors`.</span></span> 

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="8adf4-324">Des couleurs sont associées à chacune des classes.</span><span class="sxs-lookup"><span data-stu-id="8adf4-324">There are colors associated with each of the classes.</span></span> <span data-ttu-id="8adf4-325">Attribuez vos couleurs de classe sous vos `labels` :</span><span class="sxs-lookup"><span data-stu-id="8adf4-325">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="8adf4-326">Créer des fonctions d’assistance</span><span class="sxs-lookup"><span data-stu-id="8adf4-326">Create helper functions</span></span>

<span data-ttu-id="8adf4-327">Il faut suivre une série d’étapes dans la phase de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-327">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="8adf4-328">Pour vous aider, vous pouvez faire appel à plusieurs méthodes d’assistance.</span><span class="sxs-lookup"><span data-stu-id="8adf4-328">To help with that, several helper methods can be employed.</span></span> 

<span data-ttu-id="8adf4-329">Les méthodes d’assistance utilisées par l’analyseur sont :</span><span class="sxs-lookup"><span data-stu-id="8adf4-329">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="8adf4-330">`Sigmoid` applique la fonction sigmoïde qui génère un nombre entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="8adf4-330">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="8adf4-331">`Softmax` normalise un vecteur d’entrée dans une distribution de probabilité.</span><span class="sxs-lookup"><span data-stu-id="8adf4-331">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="8adf4-332">`GetOffset` mappe les éléments de la sortie du modèle unidimensionnelle à la position correspondante dans un tenseur `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-332">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="8adf4-333">`ExtractBoundingBoxes` extrait les dimensions du rectangle englobant en utilisant la méthode `GetOffset` de la sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-333">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="8adf4-334">`GetConfidence` extrait la valeur de confiance qui indique le degré de probabilité que le modèle a détecté un objet et utilise la fonction `Sigmoid` pour la convertir en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="8adf4-334">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="8adf4-335">`MapBoundingBoxToCell` utilise les dimensions du rectangle englobant et les mappe à sa cellule respective dans l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-335">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="8adf4-336">`ExtractClasses` extrait les prédictions de classe pour le rectangle englobant de la sortie du modèle en utilisant la méthode `GetOffset` et les transforme en distribution de probabilité en utilisant la méthode `Softmax`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-336">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="8adf4-337">`GetTopResult` sélectionne la classe dans la liste des classes prédites avec la probabilité la plus forte.</span><span class="sxs-lookup"><span data-stu-id="8adf4-337">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="8adf4-338">`IntersectionOverUnion` filtre les rectangles englobants qui se chevauchent avec des probabilités moins fortes.</span><span class="sxs-lookup"><span data-stu-id="8adf4-338">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="8adf4-339">Ajoutez le code pour toutes les méthodes d’assistance sous votre liste de `classColors`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-339">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="8adf4-340">Une fois que vous avez défini toutes les méthodes d’assistance, il est temps de les utiliser pour traiter la sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-340">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="8adf4-341">Sous la méthode `IntersectionOverUnion`, créez la méthode `ParseOutputs` pour traiter la sortie générée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-341">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```
    
<span data-ttu-id="8adf4-342">Créez une liste pour stocker vos rectangles englobants et définir des variables dans la méthode `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-342">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="8adf4-343">Chaque image est divisée en grille de cellules `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-343">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="8adf4-344">Chaque cellule contient cinq rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-344">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="8adf4-345">Sous la variable `boxes`, ajoutez le code pour traiter tous les rectangles de chacune des cellules.</span><span class="sxs-lookup"><span data-stu-id="8adf4-345">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

```csharp
for (int row = 0; row < ROW_COUNT; row++)
{
    for (int column = 0; column < COL_COUNT; column++)
    {
        for (int box = 0; box < BOXES_PER_CELL; box++)
        {

        }
    }
}
```

<span data-ttu-id="8adf4-346">Dans la boucle la plus interne, calculez la position de départ du rectangle actuel au sein de la sortie du modèle unidimensionnelle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-346">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="8adf4-347">Directement en dessous, utilisez la méthode `ExtractBoundingBoxDimensions` pour obtenir les dimensions du rectangle englobant actuel.</span><span class="sxs-lookup"><span data-stu-id="8adf4-347">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="8adf4-348">Utilisez ensuite la méthode `GetConfidence` pour obtenir la confiance du rectangle englobant actuel.</span><span class="sxs-lookup"><span data-stu-id="8adf4-348">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="8adf4-349">Après, utilisez la méthode `MapBoundingBoxToCell` pour mapper le rectangle englobant actuel à la cellule active en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-349">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="8adf4-350">Avant d’aller plus loin dans le traitement, vérifiez si votre valeur de confiance est supérieure au seuil fourni.</span><span class="sxs-lookup"><span data-stu-id="8adf4-350">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="8adf4-351">Si elle ne l’est pas, traitez le rectangle englobant suivant.</span><span class="sxs-lookup"><span data-stu-id="8adf4-351">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="8adf4-352">Sinon, continuez à traiter la sortie.</span><span class="sxs-lookup"><span data-stu-id="8adf4-352">Otherwise, continue processing the output.</span></span> <span data-ttu-id="8adf4-353">L’étape suivante consiste à obtenir la distribution de probabilité des classes prédites pour le rectangle englobant actuel en utilisant la méthode `ExtractClasses`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-353">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="8adf4-354">Utilisez ensuite la méthode `GetTopResult` pour obtenir la valeur et l’index de la classe avec la probabilité la plus forte pour le rectangle actuel et calculer son score.</span><span class="sxs-lookup"><span data-stu-id="8adf4-354">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="8adf4-355">Utilisez `topScore` pour une fois de plus conserver uniquement les rectangles englobants qui se trouvent au-dessus du seuil spécifié.</span><span class="sxs-lookup"><span data-stu-id="8adf4-355">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="8adf4-356">Enfin, si le rectangle englobant actuel dépasse le seuil, créez un objet `BoundingBox` et ajoutez-le à la liste des `boxes`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-356">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="8adf4-357">Une fois que toutes les cellules de l’image ont été traitées, retournez la liste des `boxes`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-357">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="8adf4-358">Ajoutez l’instruction return suivante sous la boucle for la plus externe dans la méthode `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-358">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="8adf4-359">Filtrer les rectangles qui se chevauchent</span><span class="sxs-lookup"><span data-stu-id="8adf4-359">Filter overlapping boxes</span></span>

<span data-ttu-id="8adf4-360">Maintenant que tous les rectangles englobants à confiance élevée ont été extraits de la sortie du modèle, il faut procéder à un autre filtrage pour supprimer les images qui se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="8adf4-360">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="8adf4-361">Ajoutez une méthode appelée `FilterBoundingBoxes` sous la méthode `ParseOutputs` :</span><span class="sxs-lookup"><span data-stu-id="8adf4-361">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="8adf4-362">Dans la méthode `FilterBoundingBoxes`, commencez par créer un tableau égal à la taille des rectangles détectés et par marquer tous les emplacements comme actifs ou prêts pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-362">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="8adf4-363">Triez ensuite la liste contenant vos rectangles englobants dans l’ordre décroissant en fonction de la confiance.</span><span class="sxs-lookup"><span data-stu-id="8adf4-363">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="8adf4-364">Ensuite, créez une liste pour contenir les résultats filtrés.</span><span class="sxs-lookup"><span data-stu-id="8adf4-364">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="8adf4-365">Commencez à traiter chaque rectangle englobant en effectuant une itération sur chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="8adf4-365">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="8adf4-366">Dans cette boucle for, vérifiez si le rectangle englobant actuel peut être traité.</span><span class="sxs-lookup"><span data-stu-id="8adf4-366">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{
    
}
```

<span data-ttu-id="8adf4-367">Dans ce cas, ajoutez le rectangle englobant à la liste des résultats.</span><span class="sxs-lookup"><span data-stu-id="8adf4-367">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="8adf4-368">Si les résultats dépassent la limite spécifiée des rectangles à extraire, rompez la boucle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-368">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="8adf4-369">Ajoutez le code suivant dans l’instruction if.</span><span class="sxs-lookup"><span data-stu-id="8adf4-369">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="8adf4-370">Sinon, regardez les rectangles englobants adjacents.</span><span class="sxs-lookup"><span data-stu-id="8adf4-370">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="8adf4-371">Ajoutez le code suivant sous le contrôle de la limite de rectangle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-371">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="8adf4-372">Comme pour le premier rectangle, si le rectangle adjacent est actif ou prêt à être traité, utilisez la méthode `IntersectionOverUnion` pour vérifier si le premier rectangle et le deuxième rectangle dépassent le seuil spécifié.</span><span class="sxs-lookup"><span data-stu-id="8adf4-372">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="8adf4-373">Ajoutez le code suivant à votre boucle for la plus interne.</span><span class="sxs-lookup"><span data-stu-id="8adf4-373">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="8adf4-374">En dehors de la boucle for la plus interne qui vérifie les rectangles englobants adjacents, regardez s’il reste d’éventuels rectangles englobants à traiter.</span><span class="sxs-lookup"><span data-stu-id="8adf4-374">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="8adf4-375">Si ce n’est pas le cas, rompez la boucle for externe.</span><span class="sxs-lookup"><span data-stu-id="8adf4-375">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="8adf4-376">Enfin, en dehors de la boucle for initiale de la méthode `FilterBoundingBoxes`, retournez les résultats :</span><span class="sxs-lookup"><span data-stu-id="8adf4-376">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="8adf4-377">Parfait !</span><span class="sxs-lookup"><span data-stu-id="8adf4-377">Great!</span></span> <span data-ttu-id="8adf4-378">Il est maintenant temps d’utiliser ce code avec le modèle de scoring.</span><span class="sxs-lookup"><span data-stu-id="8adf4-378">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="8adf4-379">Utiliser le modèle pour le scoring</span><span class="sxs-lookup"><span data-stu-id="8adf4-379">Use the model for scoring</span></span>

<span data-ttu-id="8adf4-380">Tout comme le post-traitement, il faut suivre quelques étapes pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="8adf4-380">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="8adf4-381">Pour vous y aider, ajoutez une classe qui contiendra la logique de scoring à votre projet.</span><span class="sxs-lookup"><span data-stu-id="8adf4-381">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="8adf4-382">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-382">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8adf4-383">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="8adf4-383">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="8adf4-384">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8adf4-384">Then, select the **Add** button.</span></span>

    <span data-ttu-id="8adf4-385">Le fichier *OnnxModelScorer.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8adf4-385">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="8adf4-386">Ajoutez l’instruction `using` suivante en haut de *OnnxModelScorer.cs* :</span><span class="sxs-lookup"><span data-stu-id="8adf4-386">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="8adf4-387">Dans la définition de la classe `OnnxModelScorer`, ajoutez les variables suivantes.</span><span class="sxs-lookup"><span data-stu-id="8adf4-387">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="8adf4-388">Juste en dessous, créez un constructeur pour la classe `OnnxModelScorer` qui initialisera les variables déjà définies.</span><span class="sxs-lookup"><span data-stu-id="8adf4-388">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="8adf4-389">Une fois que vous avez créé le constructeur, définissez quelques structs qui contiennent les variables relatives aux paramètres de l’image et du modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-389">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="8adf4-390">Créez un struct appelé `ImageNetSettings` pour contenir la hauteur et la largeur attendues comme entrée pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-390">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="8adf4-391">Ensuite, créez un autre struct appelé `TinyYoloModelSettings` qui contient les noms des couches d’entrée et de sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-391">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="8adf4-392">Pour visualiser le nom des couches d’entrée et de sortie du modèle, vous pouvez utiliser un outil comme [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="8adf4-392">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="8adf4-393">Après, créez le premier ensemble de méthodes à utiliser pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="8adf4-393">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="8adf4-394">Créez la méthode `LoadModel` dans votre classe `OnnxModelScorer`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-394">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="8adf4-395">Dans la méthode `LoadModel`, ajoutez le code suivant pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="8adf4-395">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="8adf4-396">Les pipelines ML.NET s’attendent généralement à ce que les données soient opérationnelles quand la méthode [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) est appelée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-396">ML.NET pipelines typically expect data to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="8adf4-397">Dans ce cas, un processus similaire à l’entraînement sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="8adf4-397">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="8adf4-398">Toutefois, étant donné qu’aucun véritable entraînement ne se produit, il est acceptable d’utiliser une [`IDataView`](xref:Microsoft.ML.IDataView) vide.</span><span class="sxs-lookup"><span data-stu-id="8adf4-398">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="8adf4-399">Créez une [`IDataView`](xref:Microsoft.ML.IDataView) pour le pipeline à partir d’une liste vide.</span><span class="sxs-lookup"><span data-stu-id="8adf4-399">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]    

    <span data-ttu-id="8adf4-400">En dessous, définissez le pipeline.</span><span class="sxs-lookup"><span data-stu-id="8adf4-400">Below that, define the pipeline.</span></span> <span data-ttu-id="8adf4-401">Le pipeline se compose de quatre transformations.</span><span class="sxs-lookup"><span data-stu-id="8adf4-401">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="8adf4-402">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) charge l’image en tant que bitmap.</span><span class="sxs-lookup"><span data-stu-id="8adf4-402">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="8adf4-403">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) redimensionne l’image à la taille spécifiée (dans le cas présent, `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="8adf4-403">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="8adf4-404">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) change la représentation en pixels de l’image en passant d’une bitmap à un vecteur numérique.</span><span class="sxs-lookup"><span data-stu-id="8adf4-404">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="8adf4-405">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) charge le modèle ONNX et l’utilise pour effectuer un scoring sur les données fournies.</span><span class="sxs-lookup"><span data-stu-id="8adf4-405">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="8adf4-406">Définissez votre pipeline dans la méthode `LoadModel` sous la variable `data`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-406">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="8adf4-407">Il est maintenant temps d’instancier le modèle pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="8adf4-407">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="8adf4-408">Appelez la méthode [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) sur le pipeline et retournez-la pour poursuivre le traitement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-408">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="8adf4-409">Une fois que le modèle est chargé, il peut être utilisé pour faire des prédictions.</span><span class="sxs-lookup"><span data-stu-id="8adf4-409">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="8adf4-410">Pour faciliter ce processus, créez une méthode appelée `PredictDataUsingModel` sous la méthode `LoadModel`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-410">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="8adf4-411">Dans `PredictDataUsingModel`, ajoutez le code suivant pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="8adf4-411">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="8adf4-412">Ensuite, utilisez la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pour le scoring des données.</span><span class="sxs-lookup"><span data-stu-id="8adf4-412">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="8adf4-413">Extrayez les probabilités prédites et retournez-les pour un traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="8adf4-413">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="8adf4-414">Maintenant que les deux étapes sont configurées, fusionnez-les en une seule méthode.</span><span class="sxs-lookup"><span data-stu-id="8adf4-414">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="8adf4-415">Sous la méthode `PredictDataUsingModel`, ajoutez une nouvelle méthode appelée `Score`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-415">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="8adf4-416">Vous avez presque fini !</span><span class="sxs-lookup"><span data-stu-id="8adf4-416">Almost there!</span></span> <span data-ttu-id="8adf4-417">À présent, passons à la pratique.</span><span class="sxs-lookup"><span data-stu-id="8adf4-417">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="8adf4-418">Détecter des objets</span><span class="sxs-lookup"><span data-stu-id="8adf4-418">Detect objects</span></span>

<span data-ttu-id="8adf4-419">Maintenant que la configuration est terminée, il est temps de détecter des objets.</span><span class="sxs-lookup"><span data-stu-id="8adf4-419">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="8adf4-420">Dans la méthode `Main` de votre classe *Program.cs*, ajoutez une instruction try-catch.</span><span class="sxs-lookup"><span data-stu-id="8adf4-420">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="8adf4-421">Dans le bloc `try`, commencez à implémenter la logique de détection d’objet.</span><span class="sxs-lookup"><span data-stu-id="8adf4-421">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="8adf4-422">Chargez d’abord les données dans une [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="8adf4-422">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="8adf4-423">Créez ensuite une instance de `OnnxModelScorer` et utilisez-la pour le scoring des données chargées.</span><span class="sxs-lookup"><span data-stu-id="8adf4-423">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="8adf4-424">À présent, passons à l’étape de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="8adf4-424">Now it's time for the post-processing step.</span></span> <span data-ttu-id="8adf4-425">Créez une instance de `YoloOutputParser` et utilisez-la pour traiter la sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="8adf4-425">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="8adf4-426">Une fois que la sortie du modèle a été traitée, il est temps de tracer les rectangles englobants sur les images.</span><span class="sxs-lookup"><span data-stu-id="8adf4-426">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span> <span data-ttu-id="8adf4-427">Créez une boucle for pour effectuer une itération sur chaque image scorée.</span><span class="sxs-lookup"><span data-stu-id="8adf4-427">Create a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="8adf4-428">Dans la boucle for, récupérez le nom du fichier image et les rectangles englobants associés.</span><span class="sxs-lookup"><span data-stu-id="8adf4-428">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="8adf4-429">Dessous, utilisez la méthode `DrawBoundingBox` pour tracer les rectangles englobants sur l’image.</span><span class="sxs-lookup"><span data-stu-id="8adf4-429">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="8adf4-430">Enfin, ajoutez une logique de journalisation avec la méthode `LogDetectedObjects`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-430">Lastly, add some logging logic with the `LogDetectedObjects` method.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]


<span data-ttu-id="8adf4-431">Après l’instruction try-catch, ajoutez une logique supplémentaire pour indiquer que le processus a fini l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8adf4-431">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="8adf4-432">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="8adf4-432">That's it!</span></span> 

## <a name="results"></a><span data-ttu-id="8adf4-433">Résultats</span><span class="sxs-lookup"><span data-stu-id="8adf4-433">Results</span></span> 

<span data-ttu-id="8adf4-434">Après avoir suivi les étapes précédentes, exécutez votre application console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="8adf4-434">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="8adf4-435">Vous devriez obtenir les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="8adf4-435">Your results should be similar to the following output.</span></span> <span data-ttu-id="8adf4-436">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="8adf4-436">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=====Identify the objects in the images=====

.....The objects in the image image1.jpg are detected as below....
car and its Confidence score: 0.9697262
car and its Confidence score: 0.6674225
person and its Confidence score: 0.5226039
car and its Confidence score: 0.5224892
car and its Confidence score: 0.4675332

.....The objects in the image image2.jpg are detected as below....
cat and its Confidence score: 0.6461141
cat and its Confidence score: 0.6400049

.....The objects in the image image3.jpg are detected as below....
chair and its Confidence score: 0.840578
chair and its Confidence score: 0.796363
diningtable and its Confidence score: 0.6056048
diningtable and its Confidence score: 0.3737402

.....The objects in the image image4.jpg are detected as below....
dog and its Confidence score: 0.7608147
person and its Confidence score: 0.6321323
dog and its Confidence score: 0.5967442
person and its Confidence score: 0.5730394
person and its Confidence score: 0.5551759

========= End of Process..Hit any Key ========
```

<span data-ttu-id="8adf4-437">Pour voir les images avec les rectangles englobants, accédez au répertoire `assets/images/output/`.</span><span class="sxs-lookup"><span data-stu-id="8adf4-437">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="8adf4-438">Voici un exemple de l’une des images traitées.</span><span class="sxs-lookup"><span data-stu-id="8adf4-438">Below is a sample from one of the processed images.</span></span> 

![](./media/object-detection-onnx/image3.jpg)

<span data-ttu-id="8adf4-439">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="8adf4-439">Congratulations!</span></span> <span data-ttu-id="8adf4-440">Vous avez créé un modèle Machine Learning pour la détection d’objets en réutilisant un modèle `ONNX` préentraîné dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="8adf4-440">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="8adf4-441">Vous trouverez le code source de ce tutoriel dans le dépôt [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx).</span><span class="sxs-lookup"><span data-stu-id="8adf4-441">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="8adf4-442">Dans ce tutoriel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="8adf4-442">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8adf4-443">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="8adf4-443">Understand the problem</span></span>
> * <span data-ttu-id="8adf4-444">Découvrir ce qu’est ONNX et comment il fonctionne avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="8adf4-444">Learn what ONNX is and how it works with ML.NET</span></span>
> * <span data-ttu-id="8adf4-445">Comprendre le modèle</span><span class="sxs-lookup"><span data-stu-id="8adf4-445">Understand the model</span></span>
> * <span data-ttu-id="8adf4-446">Réutiliser le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="8adf4-446">Reuse the pre-trained model</span></span>
> * <span data-ttu-id="8adf4-447">Détecter les objets avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="8adf4-447">Detect objects with a loaded model</span></span>

<span data-ttu-id="8adf4-448">Consultez le dépôt d’exemples Machine Learning GitHub pour voir un exemple détaillé de détection d’objets.</span><span class="sxs-lookup"><span data-stu-id="8adf4-448">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8adf4-449">Dépôt GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="8adf4-449">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/DeepLearning_ObjectDetection_Onnx)
