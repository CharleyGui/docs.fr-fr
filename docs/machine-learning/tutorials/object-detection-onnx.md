---
title: 'Didacticiel : détecter des objets à l’aide de l’apprentissage profond avec ONNX et ML.NET'
description: Ce tutoriel montre comment utiliser un modèle de deep learning ONNX préentraîné dans ML.NET pour détecter des objets dans des images.
author: luisquintanilla
ms.author: luquinta
ms.date: 08/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1364b6a1cf6d424975828185a50175b2763c6516
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420066"
---
# <a name="tutorial-detect-objects-using-onnx-in-mlnet"></a><span data-ttu-id="9c5ce-103">Didacticiel : détecter des objets à l’aide de ONNX dans ML.NET</span><span class="sxs-lookup"><span data-stu-id="9c5ce-103">Tutorial: Detect objects using ONNX in ML.NET</span></span>

<span data-ttu-id="9c5ce-104">Découvrez comment utiliser un modèle ONNX préentraîné dans ML.NET pour détecter des objets dans des images.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-104">Learn how to use a pre-trained ONNX model in ML.NET to detect objects in images.</span></span>

<span data-ttu-id="9c5ce-105">L’entraînement d’un modèle de détection d’objets à partir de zéro nécessite de définir des millions de paramètres et d’avoir un grand nombre de données d’entraînement étiquetées et de ressources de calcul (des centaines d’heures GPU).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-105">Training an object detection model from scratch requires setting millions of parameters, a large amount of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="9c5ce-106">L’utilisation d’un modèle préentraîné vous permet de raccourcir le processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-106">Using a pre-trained model allows you to shortcut the training process.</span></span>

<span data-ttu-id="9c5ce-107">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9c5ce-108">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="9c5ce-108">Understand the problem</span></span>
> - <span data-ttu-id="9c5ce-109">Découvrir ce qu’est ONNX et comment il fonctionne avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="9c5ce-109">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="9c5ce-110">Comprendre le modèle</span><span class="sxs-lookup"><span data-stu-id="9c5ce-110">Understand the model</span></span>
> - <span data-ttu-id="9c5ce-111">Réutiliser le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="9c5ce-111">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="9c5ce-112">Détecter les objets avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="9c5ce-112">Detect objects with a loaded model</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="9c5ce-113">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9c5ce-113">Pre-requisites</span></span>

- <span data-ttu-id="9c5ce-114">[Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-114">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- [<span data-ttu-id="9c5ce-115">Package NuGet Microsoft.ML</span><span class="sxs-lookup"><span data-stu-id="9c5ce-115">Microsoft.ML NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML/)
- [<span data-ttu-id="9c5ce-116">Package NuGet Microsoft.ML.ImageAnalytics</span><span class="sxs-lookup"><span data-stu-id="9c5ce-116">Microsoft.ML.ImageAnalytics NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.ImageAnalytics/)
- [<span data-ttu-id="9c5ce-117">Package NuGet Microsoft.ML.OnnxTransformer</span><span class="sxs-lookup"><span data-stu-id="9c5ce-117">Microsoft.ML.OnnxTransformer NuGet Package</span></span>](https://www.nuget.org/packages/Microsoft.ML.OnnxTransformer/)
- [<span data-ttu-id="9c5ce-118">Modèle préentraîné Tiny YOLOv2</span><span class="sxs-lookup"><span data-stu-id="9c5ce-118">Tiny YOLOv2 pre-trained model</span></span>](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2)
- <span data-ttu-id="9c5ce-119">[Netron](https://github.com/lutzroeder/netron) (facultatif)</span><span class="sxs-lookup"><span data-stu-id="9c5ce-119">[Netron](https://github.com/lutzroeder/netron) (optional)</span></span>

## <a name="onnx-object-detection-sample-overview"></a><span data-ttu-id="9c5ce-120">Vue d’ensemble de l’exemple de détection d’objets ONNX</span><span class="sxs-lookup"><span data-stu-id="9c5ce-120">ONNX object detection sample overview</span></span>

<span data-ttu-id="9c5ce-121">Cet exemple crée une application console .NET Core qui détecte les objets dans une image à l’aide d’un modèle ONNX de deep learning préentraîné.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-121">This sample creates a .NET core console application that detects objects within an image using a pre-trained deep learning ONNX model.</span></span> <span data-ttu-id="9c5ce-122">Vous trouverez le code de cet exemple dans le [dépôt dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-122">The code for this sample can be found on the [dotnet/machinelearning-samples repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) on GitHub.</span></span>

## <a name="what-is-object-detection"></a><span data-ttu-id="9c5ce-123">Qu’est-ce que la détection d’objets ?</span><span class="sxs-lookup"><span data-stu-id="9c5ce-123">What is object detection?</span></span>

<span data-ttu-id="9c5ce-124">La détection d’objets est un problème de vision par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-124">Object detection is a computer vision problem.</span></span> <span data-ttu-id="9c5ce-125">Même si elle est étroitement liée à la classification d’images, la détection d’objets effectue une classification d’images à une échelle plus précise.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-125">While closely related to image classification, object detection performs image classification at a more granular scale.</span></span> <span data-ttu-id="9c5ce-126">La détection d’objets localise _et_ catégorise les entités dans les images.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-126">Object detection both locates _and_ categorizes entities within images.</span></span> <span data-ttu-id="9c5ce-127">Utilisez la détection d’objets quand les images contiennent plusieurs objets de différents types.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-127">Use object detection when images contain multiple objects of different types.</span></span>

![Captures d’écran montrant la classification des images par rapport à la classification des objets.](./media/object-detection-onnx/img-classification-obj-detection.png)

<span data-ttu-id="9c5ce-129">Voici quelques cas d’utilisation de la détection d’objets :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-129">Some use cases for object detection include:</span></span>

- <span data-ttu-id="9c5ce-130">Voitures autonomes</span><span class="sxs-lookup"><span data-stu-id="9c5ce-130">Self-Driving Cars</span></span>
- <span data-ttu-id="9c5ce-131">Robotique</span><span class="sxs-lookup"><span data-stu-id="9c5ce-131">Robotics</span></span>
- <span data-ttu-id="9c5ce-132">Détection de visage</span><span class="sxs-lookup"><span data-stu-id="9c5ce-132">Face Detection</span></span>
- <span data-ttu-id="9c5ce-133">Sécurité des espaces de travail</span><span class="sxs-lookup"><span data-stu-id="9c5ce-133">Workplace Safety</span></span>
- <span data-ttu-id="9c5ce-134">Dénombrement des objets</span><span class="sxs-lookup"><span data-stu-id="9c5ce-134">Object Counting</span></span>
- <span data-ttu-id="9c5ce-135">Reconnaissance des activités</span><span class="sxs-lookup"><span data-stu-id="9c5ce-135">Activity Recognition</span></span>

## <a name="select-a-deep-learning-model"></a><span data-ttu-id="9c5ce-136">Sélectionner un modèle de deep learning</span><span class="sxs-lookup"><span data-stu-id="9c5ce-136">Select a deep learning model</span></span>

<span data-ttu-id="9c5ce-137">Le deep learning fait partie du machine learning.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-137">Deep learning is a subset of machine learning.</span></span> <span data-ttu-id="9c5ce-138">Pour entraîner des modèles de deep learning, de grandes quantités de données sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-138">To train deep learning models, large quantities of data are required.</span></span> <span data-ttu-id="9c5ce-139">Les différents motifs (patterns) de données sont représentés par une série de couches.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-139">Patterns in the data are represented by a series of layers.</span></span> <span data-ttu-id="9c5ce-140">Les relations dans les données sont encodées en tant que connexions entre les couches contenant des poids.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-140">The relationships in the data are encoded as connections between the layers containing weights.</span></span> <span data-ttu-id="9c5ce-141">Plus le poids est élevé, plus la relation est forte.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-141">The higher the weight, the stronger the relationship.</span></span> <span data-ttu-id="9c5ce-142">Collectivement, cette série de couches et de connexions est connue sous le nom de réseaux neuronaux artificiels.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-142">Collectively, this series of layers and connections are known as artificial neural networks.</span></span> <span data-ttu-id="9c5ce-143">Plus le nombre de couches d’un réseau est élevé, plus il est profond, ce qui en fait un réseau neuronal profond.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-143">The more layers in a network, the "deeper" it is, making it a deep neural network.</span></span>

<span data-ttu-id="9c5ce-144">Il existe différents types de réseaux neuronaux, les plus courants étant les perceptrons multicouches (MLP), les réseaux de neurones convolutifs (CNN) et les réseaux de neurones récurrents (RNN).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-144">There are different types of neural networks, the most common being Multi-Layered Perceptron (MLP), Convolutional Neural Network (CNN) and Recurrent Neural Network (RNN).</span></span> <span data-ttu-id="9c5ce-145">Le plus simple est le MLP, qui mappe un ensemble d’entrées à un ensemble de sorties.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-145">The most basic is the MLP, which maps a set of inputs to a set of outputs.</span></span> <span data-ttu-id="9c5ce-146">Ce réseau neuronal est parfait quand les données n’ont pas de composant spatial ou temporel.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-146">This neural network is good when the data does not have a spatial or time component.</span></span> <span data-ttu-id="9c5ce-147">Le réseau CNN utilise des couches convolutives pour traiter les informations spatiales contenues dans les données.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-147">The CNN makes use of convolutional layers to process spatial information contained in the data.</span></span> <span data-ttu-id="9c5ce-148">Un bon cas d’utilisation des réseaux CNN est le traitement d’images pour détecter la présence d’une caractéristique dans une zone d’une image (par exemple, y a-t-il un nez au centre d’une image ?).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-148">A good use case for CNNs is image processing to detect the presence of a feature in a region of an image (for example, is there a nose in the center of an image?).</span></span> <span data-ttu-id="9c5ce-149">Enfin, les réseaux RNN autorisent la persistance de l’état ou de la mémoire à utiliser comme entrée.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-149">Finally, RNNs allow for the persistence of state or memory to be used as input.</span></span> <span data-ttu-id="9c5ce-150">Ils sont utilisés pour l’analyse des séries chronologiques, où le tri séquentiel et le contexte des événements sont importants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-150">RNNs are used for time-series analysis, where the sequential ordering and context of events is important.</span></span>

### <a name="understand-the-model"></a><span data-ttu-id="9c5ce-151">Comprendre le modèle</span><span class="sxs-lookup"><span data-stu-id="9c5ce-151">Understand the model</span></span>

<span data-ttu-id="9c5ce-152">La détection d’objets est une tâche de traitement d’images.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-152">Object detection is an image processing task.</span></span> <span data-ttu-id="9c5ce-153">C’est pourquoi la plupart des modèles de deep learning préentraînés pour résoudre ce problème sont des réseaux CNN.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-153">Therefore, most deep learning models trained to solve this problem are CNNs.</span></span> <span data-ttu-id="9c5ce-154">Le modèle utilisé dans ce didacticiel est le petit modèle YOLOv2, une version plus compacte du modèle YOLOv2 décrit dans le document : [« YOLO9000 : meilleur, plus rapide et plus puissant » par RedMon et Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-154">The model used in this tutorial is the Tiny YOLOv2 model, a more compact version of the YOLOv2 model described in the paper: ["YOLO9000: Better, Faster, Stronger" by Redmon and Fadhari](https://arxiv.org/pdf/1612.08242.pdf).</span></span> <span data-ttu-id="9c5ce-155">Tiny YOLOv2 est entraîné sur le jeu de données Pascal COV et est constitué de 15 couches qui peuvent prédire 20 classes différentes d’objets.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-155">Tiny YOLOv2 is trained on the Pascal VOC dataset and is made up of 15 layers that can predict 20 different classes of objects.</span></span> <span data-ttu-id="9c5ce-156">Étant donné que Tiny YOLOv2 est une version condensée du modèle YOLOv2 d’origine, un compromis est établi entre la vitesse et la précision.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-156">Because Tiny YOLOv2 is a condensed version of the original YOLOv2 model, a tradeoff is made between speed and accuracy.</span></span> <span data-ttu-id="9c5ce-157">Les différentes couches qui composent le modèle peuvent être visualisées à l’aide d’outils comme Netron.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-157">The different layers that make up the model can be visualized using tools like Netron.</span></span> <span data-ttu-id="9c5ce-158">L’inspection du modèle produit un mappage des connexions entre toutes les couches qui composent le réseau neuronal, où chaque couche contient le nom de la couche ainsi que les dimensions des entrée/sortie respectives.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-158">Inspecting the model would yield a mapping of the connections between all the layers that make up the neural network, where each layer would contain the name of the layer along with the dimensions of the respective input / output.</span></span> <span data-ttu-id="9c5ce-159">Les structures de données utilisées pour décrire les entrées et les sorties du modèle sont appelées des tenseurs.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-159">The data structures used to describe the inputs and outputs of the model are known as tensors.</span></span> <span data-ttu-id="9c5ce-160">Les tenseurs peuvent être considérés comme des conteneurs qui stockent des données dans N dimensions.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-160">Tensors can be thought of as containers that store data in N-dimensions.</span></span> <span data-ttu-id="9c5ce-161">Dans le cas de Tiny YOLOv2, le nom de la couche d’entrée est `image` et il attend un tenseur de dimensions `3 x 416 x 416`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-161">In the case of Tiny YOLOv2, the name of the input layer is `image` and it expects a tensor of dimensions `3 x 416 x 416`.</span></span> <span data-ttu-id="9c5ce-162">Le nom de la couche de sortie est `grid` et génère un tenseur de sortie de dimensions `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-162">The name of the output layer is `grid` and generates an output tensor of dimensions `125 x 13 x 13`.</span></span>

![Couche d’entrée fractionnée en couches masquées, puis couche de sortie](./media/object-detection-onnx/netron-model-map-layers.png)

<span data-ttu-id="9c5ce-164">Le modèle YOLO prend une image `3(RGB) x 416px x 416px`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-164">The YOLO model takes an image `3(RGB) x 416px x 416px`.</span></span> <span data-ttu-id="9c5ce-165">Le modèle prend cette entrée et la passe à travers les différentes couches pour produire une sortie.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-165">The model takes this input and passes it through the different layers to produce an output.</span></span> <span data-ttu-id="9c5ce-166">La sortie divise l’image d’entrée en une grille `13 x 13`, chaque cellule de la grille contenant les valeurs `125`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-166">The output divides the input image into a `13 x 13` grid, with each cell in the grid consisting of `125` values.</span></span>

### <a name="what-is-an-onnx-model"></a><span data-ttu-id="9c5ce-167">Qu’est-ce qu’un modèle ONNX ?</span><span class="sxs-lookup"><span data-stu-id="9c5ce-167">What is an ONNX model?</span></span>

<span data-ttu-id="9c5ce-168">ONNX (Open Neural Network Exchange) est un format open source pour les modèles IA.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-168">The Open Neural Network Exchange (ONNX) is an open source format for AI models.</span></span> <span data-ttu-id="9c5ce-169">ONNX prend en charge l’interopérabilité entre les frameworks.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-169">ONNX supports interoperability between frameworks.</span></span> <span data-ttu-id="9c5ce-170">Cela signifie que vous pouvez entraîner un modèle dans l’un des nombreux frameworks de machine learning connus tels que PyTorch, le convertir au format ONNX et consommer le modèle ONNX dans un autre framework comme ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-170">This means you can train a model in one of the many popular machine learning frameworks like PyTorch, convert it into ONNX format and consume the ONNX model in a different framework like ML.NET.</span></span> <span data-ttu-id="9c5ce-171">Pour en savoir plus, consultez le [site web ONNX](https://onnx.ai/).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-171">To learn more, visit the [ONNX website](https://onnx.ai/).</span></span>

![Diagramme des formats pris en charge par ONNX.](./media/object-detection-onnx/onyx-supported-formats.png)

<span data-ttu-id="9c5ce-173">Le modèle Tiny YOLOv2 préentraîné est stocké au format ONNX, représentation sérialisée des couches et des motifs appris de ces couches.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-173">The pre-trained Tiny YOLOv2 model is stored in ONNX format, a serialized representation of the layers and learned patterns of those layers.</span></span> <span data-ttu-id="9c5ce-174">Dans ML.NET, l’interopérabilité avec ONNX s’obtient avec les packages NuGet [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) et [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-174">In ML.NET, interoperability with ONNX is achieved with the [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) and [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) NuGet packages.</span></span> <span data-ttu-id="9c5ce-175">Le package[`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) contient une série de transformations qui prennent une image et l’encodent en valeurs numériques pouvant être utilisées comme entrée dans un pipeline de prédiction ou d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-175">The [`ImageAnalytics`](xref:Microsoft.ML.Transforms.Image) package contains a series of transforms that take an image and encode it into numerical values that can be used as input into a prediction or training pipeline.</span></span> <span data-ttu-id="9c5ce-176">Le package [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) tire profit du runtime ONNX afin de charger un modèle ONNX et de l’utiliser pour faire des prédictions en fonction de l’entrée fournie.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-176">The [`OnnxTransformer`](xref:Microsoft.ML.Transforms.Onnx.OnnxTransformer) package leverages the ONNX Runtime to load an ONNX model and use it to make predictions based on input provided.</span></span>

![Le workflow de données du fichier ONNX dans le runtime ONNX.](./media/object-detection-onnx/onnx-ml-net-integration.png)

## <a name="set-up-the-net-core-project"></a><span data-ttu-id="9c5ce-178">Configurer le projet .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c5ce-178">Set up the .NET Core project</span></span>

<span data-ttu-id="9c5ce-179">Maintenant que vous avez une compréhension générale de ce qu’est ONNX et de la façon dont Tiny YOLOv2 fonctionne, il est temps de générer l’application.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-179">Now that you have a general understanding of what ONNX is and how Tiny YOLOv2 works, it's time to build the application.</span></span>

### <a name="create-a-console-application"></a><span data-ttu-id="9c5ce-180">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="9c5ce-180">Create a console application</span></span>

1. <span data-ttu-id="9c5ce-181">Créez une **application console .NET Core** appelée « ObjectDetection ».</span><span class="sxs-lookup"><span data-stu-id="9c5ce-181">Create a **.NET Core Console Application** called "ObjectDetection".</span></span>

1. <span data-ttu-id="9c5ce-182">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-182">Install the **Microsoft.ML NuGet Package**:</span></span>

    - <span data-ttu-id="9c5ce-183">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-183">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    - <span data-ttu-id="9c5ce-184">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-184">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    - <span data-ttu-id="9c5ce-185">Sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-185">Select the **Install** button.</span></span>
    - <span data-ttu-id="9c5ce-186">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-186">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    - <span data-ttu-id="9c5ce-187">Répétez ces étapes pour **Microsoft.ML.ImageAnalytics** et **Microsoft.ML.OnnxTransformer**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-187">Repeat these steps for **Microsoft.ML.ImageAnalytics** and **Microsoft.ML.OnnxTransformer**.</span></span>

### <a name="prepare-your-data-and-pre-trained-model"></a><span data-ttu-id="9c5ce-188">Préparer vos données et votre modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="9c5ce-188">Prepare your data and pre-trained model</span></span>

1. <span data-ttu-id="9c5ce-189">Téléchargez le [fichier zip du répertoire de ressources du projet ](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-189">Download [The project assets directory zip file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/assets.zip) and unzip.</span></span>

1. <span data-ttu-id="9c5ce-190">Copiez le répertoire `assets` dans votre répertoire de projet *ObjectDetection*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-190">Copy the `assets` directory into your *ObjectDetection* project directory.</span></span> <span data-ttu-id="9c5ce-191">Ce répertoire et ses sous-répertoires contiennent les fichiers image nécessaires à ce tutoriel (sauf pour le modèle Tiny YOLOv2, que vous allez télécharger et ajouter à l’étape suivante).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-191">This directory and its subdirectories contain the image files (except for the Tiny YOLOv2 model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="9c5ce-192">Téléchargez le [modèle Tiny YOLOv2](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) depuis [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-192">Download the [Tiny YOLOv2 model](https://onnxzoo.blob.core.windows.net/models/opset_8/tiny_yolov2/tiny_yolov2.tar.gz) from the [ONNX Model Zoo](https://github.com/onnx/models/tree/master/vision/object_detection_segmentation/tiny_yolov2), and unzip.</span></span>

    <span data-ttu-id="9c5ce-193">Ouvrez l’invite de commande et entrez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-193">Open the command prompt and enter the following command:</span></span>

    ```shell
    tar -xvzf tiny_yolov2.tar.gz
    ```

1. <span data-ttu-id="9c5ce-194">Copiez le fichier `model.onnx` extrait du répertoire que vous venez de décompresser dans le répertoire `assets\Model` de votre projet *ObjectDetection* et renommez-le `TinyYolo2_model.onnx`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-194">Copy the extracted `model.onnx` file from the directory just unzipped into your *ObjectDetection* project `assets\Model` directory and rename it to `TinyYolo2_model.onnx`.</span></span> <span data-ttu-id="9c5ce-195">Ce répertoire contient le modèle nécessaire pour ce tutoriel.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-195">This directory contains the model needed for this tutorial.</span></span>

1. <span data-ttu-id="9c5ce-196">Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-196">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="9c5ce-197">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-197">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="9c5ce-198">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="9c5ce-198">Create classes and define paths</span></span>

<span data-ttu-id="9c5ce-199">Ouvrez le fichier *Program.cs* et ajoutez les instructions `using` supplémentaires suivantes en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-199">Open the *Program.cs* file and add the following additional `using` statements to the top of the file:</span></span>

[!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L1-L7)]

<span data-ttu-id="9c5ce-200">Ensuite, définissez les chemins des différentes ressources.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-200">Next, define the paths of the various assets.</span></span>

1. <span data-ttu-id="9c5ce-201">Tout d’abord, ajoutez la méthode `GetAbsolutePath` sous la méthode `Main` dans la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-201">First, add the `GetAbsolutePath` method below the `Main` method in the `Program` class.</span></span>

    [!code-csharp [GetAbsolutePath](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L66-L74)]

1. <span data-ttu-id="9c5ce-202">Ensuite, dans la méthode `Main`, créez des champs pour stocker l’emplacement de vos ressources.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-202">Then, inside the `Main` method, create fields to store the location of your assets.</span></span>

    [!code-csharp [AssetDefinition](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L17-L21)]

<span data-ttu-id="9c5ce-203">Ajoutez un nouveau répertoire à votre projet pour stocker vos données d’entrée et vos classes de prédiction.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-203">Add a new directory to your project to store your input data and prediction classes.</span></span>

<span data-ttu-id="9c5ce-204">Dans l’**Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-204">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="9c5ce-205">Lorsque le nouveau dossier s’affiche dans l’Explorateur de solutions, nommez-le « DataStructures ».</span><span class="sxs-lookup"><span data-stu-id="9c5ce-205">When the new folder appears in the Solution Explorer, name it "DataStructures".</span></span>

<span data-ttu-id="9c5ce-206">Créez votre classe de données d’entrée dans le répertoire *DataStructures* qui vient d’être créé.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-206">Create your input data class in the newly created *DataStructures* directory.</span></span>

1. <span data-ttu-id="9c5ce-207">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *DataStructures*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-207">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9c5ce-208">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageNetData.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-208">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetData.cs*.</span></span> <span data-ttu-id="9c5ce-209">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-209">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9c5ce-210">Le fichier *ImageNetData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-210">The *ImageNetData.cs* file opens in the code editor.</span></span> <span data-ttu-id="9c5ce-211">Ajoutez l’instruction `using` suivante en haut de *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-211">Add the following `using` statement to the top of *ImageNetData.cs*:</span></span>

    [!code-csharp [ImageNetDataUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L1-L4)]

    <span data-ttu-id="9c5ce-212">Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageNetData` au fichier *ImageNetData.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-212">Remove the existing class definition and add the following code for the `ImageNetData` class to the *ImageNetData.cs* file:</span></span>

    [!code-csharp [ImageNetDataClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetData.cs#L8-L23)]

    <span data-ttu-id="9c5ce-213">`ImageNetData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-213">`ImageNetData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    - <span data-ttu-id="9c5ce-214">`ImagePath` contient le chemin où l’image est stockée.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-214">`ImagePath` contains the path where the image is stored.</span></span>
    - <span data-ttu-id="9c5ce-215">`Label` contient le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-215">`Label` contains the name of the file.</span></span>

    <span data-ttu-id="9c5ce-216">De plus, `ImageNetData` contient une méthode `ReadFromFile` qui charge un grand nombre de fichiers image stockés dans le chemin `imageFolder` spécifié et les retourne sous forme de collection d’objets `ImageNetData`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-216">Additionally, `ImageNetData` contains a method `ReadFromFile` which loads multiple image files stored in the `imageFolder` path specified and returns them as a collection of `ImageNetData` objects.</span></span>

<span data-ttu-id="9c5ce-217">Créez votre classe de prédiction dans le répertoire *DataStructures*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-217">Create your prediction class in the *DataStructures* directory.</span></span>

1. <span data-ttu-id="9c5ce-218">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *DataStructures*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-218">In **Solution Explorer**, right-click the *DataStructures* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9c5ce-219">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageNetPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-219">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageNetPrediction.cs*.</span></span> <span data-ttu-id="9c5ce-220">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-220">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9c5ce-221">Le fichier *ImageNetPrediction.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-221">The *ImageNetPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="9c5ce-222">Ajoutez l’instruction `using` suivante en haut de *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-222">Add the following `using` statement to the top of *ImageNetPrediction.cs*:</span></span>

    [!code-csharp [ImageNetPredictionUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L1)]

    <span data-ttu-id="9c5ce-223">Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageNetPrediction` au fichier *ImageNetPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-223">Remove the existing class definition and add the following code for the `ImageNetPrediction` class to the *ImageNetPrediction.cs* file:</span></span>

    [!code-csharp [ImageNetPredictionClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/DataStructures/ImageNetPrediction.cs#L5-L9)]

    <span data-ttu-id="9c5ce-224">`ImageNetPrediction` est la classe de données de prédiction et présente le champ `float[]` suivant :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-224">`ImageNetPrediction` is the prediction data class and has the following `float[]` field:</span></span>

    - <span data-ttu-id="9c5ce-225">`PredictedLabel` contient les dimensions, le score d’objets et les probabilités de classe pour chacun des rectangles englobants détectés dans une image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-225">`PredictedLabel` contains the dimensions, objectness score and class probabilities for each of the bounding boxes detected in an image.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="9c5ce-226">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="9c5ce-226">Initialize variables in Main</span></span>

<span data-ttu-id="9c5ce-227">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-227">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9c5ce-228">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-228">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="9c5ce-229">Initialisez la variable `mlContext` avec une nouvelle instance de `MLContext` en ajoutant la ligne suivante à la méthode `Main` de *Program.cs* sous le champ `outputFolder`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-229">Initialize the `mlContext` variable with a new instance of `MLContext` by adding the following line to the `Main` method of *Program.cs* below the `outputFolder` field.</span></span>

[!code-csharp [InitMLContext](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L24)]

## <a name="create-a-parser-to-post-process-model-outputs"></a><span data-ttu-id="9c5ce-230">Créer un analyseur pour le post-traitement des sorties du modèle</span><span class="sxs-lookup"><span data-stu-id="9c5ce-230">Create a parser to post-process model outputs</span></span>

<span data-ttu-id="9c5ce-231">Le modèle segmente une image dans une grille `13 x 13`, où chaque cellule de grille est `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-231">The model segments an image into a `13 x 13` grid, where each grid cell is `32px x 32px`.</span></span> <span data-ttu-id="9c5ce-232">Chaque cellule de grille contient 5 rectangles englobants d’objet potentiels.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-232">Each grid cell contains 5 potential object bounding boxes.</span></span> <span data-ttu-id="9c5ce-233">Un rectangle englobant a 25 éléments :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-233">A bounding box has  25 elements:</span></span>

![Exemple de grille à gauche, et exemple de cadre englobant à droite](./media/object-detection-onnx/model-output-description.png)

- <span data-ttu-id="9c5ce-235">`x` position x du centre du rectangle englobant par rapport à la cellule de grille à laquelle il est associé.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-235">`x` the x position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="9c5ce-236">`y` position y du centre du rectangle englobant par rapport à la cellule de grille à laquelle il est associé.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-236">`y` the y position of the bounding box center relative to the grid cell it's associated with.</span></span>
- <span data-ttu-id="9c5ce-237">`w` largeur du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-237">`w` the width of the bounding box.</span></span>
- <span data-ttu-id="9c5ce-238">`h` hauteur du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-238">`h` the height of the bounding box.</span></span>
- <span data-ttu-id="9c5ce-239">`o` valeur de confiance qu’un objet existe dans le rectangle englobant, également connue sous le nom de score d’objet.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-239">`o` the confidence value that an object exists within the bounding box, also known as objectness score.</span></span>
- <span data-ttu-id="9c5ce-240">`p1-p20` probabilités de classe pour chacune des 20 classes prédites par le modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-240">`p1-p20` class probabilities for each of the 20 classes predicted by the model.</span></span>

<span data-ttu-id="9c5ce-241">Au total, les 25 éléments décrivant chacun des 5 rectangles englobants composent les 125 éléments contenus dans chaque cellule de grille.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-241">In total, the 25 elements describing each of the 5 bounding boxes make up the 125 elements contained in each grid cell.</span></span>

<span data-ttu-id="9c5ce-242">La sortie générée par le modèle ONNX préentraîné est un tableau de type float de longueur `21125`, représentant les éléments d’un tenseur avec les dimensions `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-242">The output generated by the pre-trained ONNX model is a float array of length `21125`, representing the elements of a tensor with dimensions `125 x 13 x 13`.</span></span> <span data-ttu-id="9c5ce-243">Pour transformer les prédictions générées par le modèle en tenseur, un travail de post-traitement est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-243">In order to transform the predictions generated by the model into a tensor, some post-processing work is required.</span></span> <span data-ttu-id="9c5ce-244">Pour ce faire, créez un ensemble de classes pour permettre l’analyse de la sortie.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-244">To do so, create a set of classes to help parse the output.</span></span>

<span data-ttu-id="9c5ce-245">Ajoutez un nouveau répertoire à votre projet pour organiser l’ensemble des classes d’analyseur.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-245">Add a new directory to your project to organize the set of parser classes.</span></span>

1. <span data-ttu-id="9c5ce-246">Dans l’**Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-246">In **Solution Explorer**, right-click the project, and then select **Add** > **New Folder**.</span></span> <span data-ttu-id="9c5ce-247">Lorsque le nouveau dossier s’affiche dans l’Explorateur de solutions, nommez-le « YoloParser ».</span><span class="sxs-lookup"><span data-stu-id="9c5ce-247">When the new folder appears in the Solution Explorer, name it "YoloParser".</span></span>

### <a name="create-bounding-boxes-and-dimensions"></a><span data-ttu-id="9c5ce-248">Créer des rectangles englobants et des dimensions</span><span class="sxs-lookup"><span data-stu-id="9c5ce-248">Create bounding boxes and dimensions</span></span>

<span data-ttu-id="9c5ce-249">Les données générées par le modèle contiennent les coordonnées et les dimensions des rectangles englobants des objets dans l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-249">The data output by the model contains coordinates and dimensions of the bounding boxes of objects within the image.</span></span> <span data-ttu-id="9c5ce-250">Créez une classe de base pour les dimensions.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-250">Create a base class for dimensions.</span></span>

1. <span data-ttu-id="9c5ce-251">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-251">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9c5ce-252">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *DimensionsBase.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-252">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *DimensionsBase.cs*.</span></span> <span data-ttu-id="9c5ce-253">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-253">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9c5ce-254">Le fichier *DimensionsBase.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-254">The *DimensionsBase.cs* file opens in the code editor.</span></span> <span data-ttu-id="9c5ce-255">Supprimez toutes les instructions `using` et la définition de classe existante.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-255">Remove all `using` statements and existing class definition.</span></span>

    <span data-ttu-id="9c5ce-256">Ajoutez le code suivant pour la classe `DimensionsBase` au fichier *DimensionsBase.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-256">Add the following code for the `DimensionsBase` class to the *DimensionsBase.cs* file:</span></span>

    [!code-csharp [DimensionsBaseClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/DimensionsBase.cs#L3-L9)]

    <span data-ttu-id="9c5ce-257">`DimensionsBase` présente les champs `float` suivants :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-257">`DimensionsBase` has the following `float` fields:</span></span>

    - <span data-ttu-id="9c5ce-258">`X` contient la position de l’objet sur l’axe x.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-258">`X` contains the position of the object along the x-axis.</span></span>
    - <span data-ttu-id="9c5ce-259">`Y` contient la position de l’objet sur l’axe y.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-259">`Y` contains the position of the object along the y-axis.</span></span>
    - <span data-ttu-id="9c5ce-260">`Height` contient la hauteur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-260">`Height` contains the height of the object.</span></span>
    - <span data-ttu-id="9c5ce-261">`Width` contient la largeur de l’objet.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-261">`Width` contains the width of the object.</span></span>

<span data-ttu-id="9c5ce-262">Ensuite, créez une classe pour vos rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-262">Next, create a class for your bounding boxes.</span></span>

1. <span data-ttu-id="9c5ce-263">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-263">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9c5ce-264">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *YoloBoundingBox.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-264">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloBoundingBox.cs*.</span></span> <span data-ttu-id="9c5ce-265">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-265">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9c5ce-266">Le fichier *YoloBoundingBox.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-266">The *YoloBoundingBox.cs* file opens in the code editor.</span></span> <span data-ttu-id="9c5ce-267">Ajoutez l’instruction `using` suivante en haut de *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-267">Add the following `using` statement to the top of *YoloBoundingBox.cs*:</span></span>

    [!code-csharp [YoloBoundingBoxUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L1)]

    <span data-ttu-id="9c5ce-268">Juste au-dessus de la définition de classe existante, ajoutez une nouvelle définition de classe nommée `BoundingBoxDimensions` qui hérite de la classe `DimensionsBase` pour contenir les dimensions du rectangle englobant respectif.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-268">Just above the existing class definition, add a new class definition called `BoundingBoxDimensions` which inherits from the `DimensionsBase` class to contain the dimensions of the respective bounding box.</span></span>

    [!code-csharp [BoundingBoxDimClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L5)]

    <span data-ttu-id="9c5ce-269">Supprimez la définition de classe `YoloBoundingBox` existante et ajoutez le code suivant pour la classe `YoloBoundingBox` au fichier *YoloBoundingBox.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-269">Remove the existing `YoloBoundingBox` class definition and add the following code for the `YoloBoundingBox` class to the *YoloBoundingBox.cs* file:</span></span>

    [!code-csharp [YoloBoundingBoxClass](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloBoundingBox.cs#L7-L21)]

    <span data-ttu-id="9c5ce-270">`YoloBoundingBox` présente les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-270">`YoloBoundingBox` has the following fields:</span></span>

    - <span data-ttu-id="9c5ce-271">`Dimensions` contient les dimensions du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-271">`Dimensions` contains dimensions of the bounding box.</span></span>
    - <span data-ttu-id="9c5ce-272">`Label` contient la classe de l’objet détecté dans le rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-272">`Label` contains the class of object detected within the bounding box.</span></span>
    - <span data-ttu-id="9c5ce-273">`Confidence` contient la valeur de confiance de la classe.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-273">`Confidence` contains the confidence of the class.</span></span>
    - <span data-ttu-id="9c5ce-274">`Rect` contient la représentation rectangle des dimensions du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-274">`Rect` contains the rectangle representation of the bounding box's dimensions.</span></span>
    - <span data-ttu-id="9c5ce-275">`BoxColor` contient la couleur associée à la classe respective utilisée pour dessiner sur l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-275">`BoxColor` contains the color associated with the respective class used to draw on the image.</span></span>

### <a name="create-the-parser"></a><span data-ttu-id="9c5ce-276">Créer l’analyseur</span><span class="sxs-lookup"><span data-stu-id="9c5ce-276">Create the parser</span></span>

<span data-ttu-id="9c5ce-277">Maintenant que les classes pour les dimensions et les rectangles englobants sont créées, il est temps de créer l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-277">Now that the classes for dimensions and bounding boxes are created, it's time to create the parser.</span></span>

1. <span data-ttu-id="9c5ce-278">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le répertoire *YoloParser*, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-278">In **Solution Explorer**, right-click the *YoloParser* directory, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9c5ce-279">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez le champ **Nom** par *YoloOutputParser.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-279">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *YoloOutputParser.cs*.</span></span> <span data-ttu-id="9c5ce-280">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-280">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9c5ce-281">Le fichier *YoloOutputParser.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-281">The *YoloOutputParser.cs* file opens in the code editor.</span></span> <span data-ttu-id="9c5ce-282">Ajoutez l’instruction `using` suivante en haut du fichier *YoloOutputParser.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-282">Add the following `using` statement to the top of *YoloOutputParser.cs*:</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L1-L4)]

    <span data-ttu-id="9c5ce-283">Dans la définition de la classe `YoloOutputParser` existante, ajoutez une classe imbriquée qui contient les dimensions de chacune des cellules de l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-283">Inside the existing `YoloOutputParser` class definition, add a nested class that contains the dimensions of each of the cells in the image.</span></span> <span data-ttu-id="9c5ce-284">Ajoutez le code suivant pour la classe `CellDimensions` qui hérite de la classe `DimensionsBase` en haut de la définition de la classe `YoloOutputParser`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-284">Add the following code for the `CellDimensions` class which inherits from the `DimensionsBase` class at the top of the `YoloOutputParser` class definition.</span></span>

    [!code-csharp [YoloParserUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L10)]

1. <span data-ttu-id="9c5ce-285">Dans la définition de la classe `YoloOutputParser`, ajoutez la constante et les champs suivants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-285">Inside the `YoloOutputParser` class definition, add the following constant and fields.</span></span>

    [!code-csharp [ParserVarDefinitions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L12-L21)]

    - <span data-ttu-id="9c5ce-286">`ROW_COUNT` est le nombre de lignes dans la grille dans laquelle l’image est divisée.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-286">`ROW_COUNT` is the number of rows in the grid the image is divided into.</span></span>
    - <span data-ttu-id="9c5ce-287">`COL_COUNT` est le nombre de colonnes dans la grille dans laquelle l’image est divisée.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-287">`COL_COUNT` is the number of columns in the grid the image is divided into.</span></span>
    - <span data-ttu-id="9c5ce-288">`CHANNEL_COUNT` est le nombre total de valeurs contenues dans une cellule de la grille.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-288">`CHANNEL_COUNT` is the total number of values contained in one cell of the grid.</span></span>
    - <span data-ttu-id="9c5ce-289">`BOXES_PER_CELL` est le nombre de rectangles englobants dans une cellule.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-289">`BOXES_PER_CELL` is the number of bounding boxes in a cell,</span></span>
    - <span data-ttu-id="9c5ce-290">`BOX_INFO_FEATURE_COUNT` est le nombre de caractéristiques contenues dans un rectangle (x, y, hauteur, largeur, confiance).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-290">`BOX_INFO_FEATURE_COUNT` is the number of features contained within a box (x,y,height,width,confidence).</span></span>
    - <span data-ttu-id="9c5ce-291">`CLASS_COUNT` est le nombre de prédictions de classe contenues dans chaque rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-291">`CLASS_COUNT` is the number of class predictions contained in each bounding box.</span></span>
    - <span data-ttu-id="9c5ce-292">`CELL_WIDTH` est la largeur d’une cellule dans la grille de l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-292">`CELL_WIDTH` is the width of one cell in the image grid.</span></span>
    - <span data-ttu-id="9c5ce-293">`CELL_HEIGHT` est la hauteur d’une cellule dans la grille de l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-293">`CELL_HEIGHT` is the height of one cell in the image grid.</span></span>
    - <span data-ttu-id="9c5ce-294">`channelStride` est la position de départ de la cellule active dans la grille.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-294">`channelStride` is the starting position of the current cell in the grid.</span></span>

    <span data-ttu-id="9c5ce-295">Quand le modèle fait une prédiction (ou « scoring »), il divise l’image d’entrée `416px x 416px` sous forme de grille de cellules d’une taille de `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-295">When the model makes a prediction, also known as scoring, it divides the `416px x 416px` input image into a grid of cells the size of `13 x 13`.</span></span> <span data-ttu-id="9c5ce-296">Chaque cellule contient `32px x 32px`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-296">Each cell contains is `32px x 32px`.</span></span> <span data-ttu-id="9c5ce-297">Dans chaque cellule, il y a 5 rectangles englobants contenant chacun 5 caractéristiques (x, y, largeur, hauteur, confiance).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-297">Within each cell, there are 5 bounding boxes each containing 5 features (x, y, width, height, confidence).</span></span> <span data-ttu-id="9c5ce-298">Chaque rectangle englobant contient aussi la probabilité de chacune des classes qui, dans le cas présent, est de 20.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-298">In addition, each bounding box contains the probability of each of the classes which in this case is 20.</span></span> <span data-ttu-id="9c5ce-299">Par conséquent, chaque cellule contient 125 informations différentes (5 caractéristiques + 20 probabilités de classe).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-299">Therefore, each cell contains 125 pieces of information (5 features + 20 class probabilities).</span></span>

<span data-ttu-id="9c5ce-300">Créez une liste d’ancres sous `channelStride` pour les 5 rectangles englobants :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-300">Create a list of anchors below `channelStride` for all 5 bounding boxes:</span></span>

[!code-csharp [ParserAnchors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L23-L26)]

<span data-ttu-id="9c5ce-301">Les ancres sont des ratios de hauteur et de largeur prédéfinis pour les rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-301">Anchors are pre-defined height and width ratios of bounding boxes.</span></span> <span data-ttu-id="9c5ce-302">La plupart des objets ou classes détectés par un modèle ont des ratios similaires.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-302">Most object or classes detected by a model have similar ratios.</span></span> <span data-ttu-id="9c5ce-303">C’est utile lorsqu’il s’agit de créer des rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-303">This is valuable when it comes to creating bounding boxes.</span></span> <span data-ttu-id="9c5ce-304">Au lieu de prédire les rectangles englobants, le décalage par rapport aux dimensions prédéfinies est calculé, réduisant ainsi le calcul nécessaire pour prédire le rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-304">Instead of predicting the bounding boxes, the offset from the pre-defined dimensions is calculated therefore reducing the computation required to predict the bounding box.</span></span> <span data-ttu-id="9c5ce-305">En général, ces ratios d’ancre sont calculés en fonction du jeu de données utilisé.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-305">Typically these anchor ratios are calculated based on the dataset used.</span></span> <span data-ttu-id="9c5ce-306">Dans ce cas, étant donné que le jeu de données est connu et que les valeurs ont été précalculées, les ancres peuvent être codées en dur.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-306">In this case because the dataset is known and the values have been pre-computed, the anchors can be hard-coded.</span></span>

<span data-ttu-id="9c5ce-307">Ensuite, définissez les étiquettes ou les classes que le modèle va prédire.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-307">Next, define the labels or classes that the model will predict.</span></span> <span data-ttu-id="9c5ce-308">Ce modèle prédit 20 classes, qui est un sous-ensemble du nombre total de classes prédites par le modèle YOLOv2 d’origine.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-308">This model predicts 20 classes which is a subset of the total number of classes predicted by the original YOLOv2 model.</span></span>

<span data-ttu-id="9c5ce-309">Ajoutez votre liste d’étiquettes sous les `anchors`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-309">Add your list of labels below the `anchors`.</span></span>

[!code-csharp [ParserLabels](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L28-L34)]

<span data-ttu-id="9c5ce-310">Des couleurs sont associées à chacune des classes.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-310">There are colors associated with each of the classes.</span></span> <span data-ttu-id="9c5ce-311">Attribuez vos couleurs de classe sous vos `labels` :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-311">Assign your class colors below your `labels`:</span></span>

[!code-csharp [ParserColors](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L36-L59)]

### <a name="create-helper-functions"></a><span data-ttu-id="9c5ce-312">Créer des fonctions d’assistance</span><span class="sxs-lookup"><span data-stu-id="9c5ce-312">Create helper functions</span></span>

<span data-ttu-id="9c5ce-313">Il faut suivre une série d’étapes dans la phase de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-313">There are a series of steps involved in the post-processing phase.</span></span> <span data-ttu-id="9c5ce-314">Pour vous aider, vous pouvez faire appel à plusieurs méthodes d’assistance.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-314">To help with that, several helper methods can be employed.</span></span>

<span data-ttu-id="9c5ce-315">Les méthodes d’assistance utilisées par l’analyseur sont :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-315">The helper methods used in by the parser are:</span></span>

- <span data-ttu-id="9c5ce-316">`Sigmoid` applique la fonction sigmoïde qui génère un nombre entre 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-316">`Sigmoid` applies the sigmoid function that outputs a number between 0 and 1.</span></span>
- <span data-ttu-id="9c5ce-317">`Softmax` normalise un vecteur d’entrée dans une distribution de probabilité.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-317">`Softmax` normalizes an input vector into a probability distribution.</span></span>
- <span data-ttu-id="9c5ce-318">`GetOffset` mappe les éléments de la sortie du modèle unidimensionnelle à la position correspondante dans un tenseur `125 x 13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-318">`GetOffset` maps elements in the one-dimensional model output to the corresponding position in a `125 x 13 x 13` tensor.</span></span>
- <span data-ttu-id="9c5ce-319">`ExtractBoundingBoxes` extrait les dimensions du rectangle englobant en utilisant la méthode `GetOffset` de la sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-319">`ExtractBoundingBoxes` extracts the bounding box dimensions using the `GetOffset` method from the model output.</span></span>
- <span data-ttu-id="9c5ce-320">`GetConfidence` extrait la valeur de confiance qui indique le degré de probabilité que le modèle a détecté un objet et utilise la fonction `Sigmoid` pour la convertir en pourcentage.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-320">`GetConfidence` extracts the confidence value which states how sure the model is that it has detected an object and uses the `Sigmoid` function to turn it into a percentage.</span></span>
- <span data-ttu-id="9c5ce-321">`MapBoundingBoxToCell` utilise les dimensions du rectangle englobant et les mappe à sa cellule respective dans l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-321">`MapBoundingBoxToCell` uses the bounding box dimensions and maps them onto its respective cell within the image.</span></span>
- <span data-ttu-id="9c5ce-322">`ExtractClasses` extrait les prédictions de classe pour le rectangle englobant de la sortie du modèle en utilisant la méthode `GetOffset` et les transforme en distribution de probabilité en utilisant la méthode `Softmax`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-322">`ExtractClasses` extracts the class predictions for the bounding box from the model output using the `GetOffset` method and turns them into a probability distribution using the `Softmax` method.</span></span>
- <span data-ttu-id="9c5ce-323">`GetTopResult` sélectionne la classe dans la liste des classes prédites avec la probabilité la plus forte.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-323">`GetTopResult` selects the class from the list of predicted classes with the highest probability.</span></span>
- <span data-ttu-id="9c5ce-324">`IntersectionOverUnion` filtre les rectangles englobants qui se chevauchent avec des probabilités moins fortes.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-324">`IntersectionOverUnion` filters overlapping bounding boxes with lower probabilities.</span></span>

<span data-ttu-id="9c5ce-325">Ajoutez le code pour toutes les méthodes d’assistance sous votre liste de `classColors`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-325">Add the code for all the helper methods below your list of `classColors`.</span></span>

[!code-csharp [ParserHelperMethods](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L61-L151)]

<span data-ttu-id="9c5ce-326">Une fois que vous avez défini toutes les méthodes d’assistance, il est temps de les utiliser pour traiter la sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-326">Once you have defined all of the helper methods, it's time to use them to process the model output.</span></span>

<span data-ttu-id="9c5ce-327">Sous la méthode `IntersectionOverUnion`, créez la méthode `ParseOutputs` pour traiter la sortie générée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-327">Below the `IntersectionOverUnion` method, create the `ParseOutputs` method to process the output generated by the model.</span></span>

```csharp
public IList<YoloBoundingBox> ParseOutputs(float[] yoloModelOutputs, float threshold = .3F)
{

}
```

<span data-ttu-id="9c5ce-328">Créez une liste pour stocker vos rectangles englobants et définir des variables dans la méthode `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-328">Create a list to store your bounding boxes and define variables inside the `ParseOutputs` method.</span></span>

[!code-csharp [BBoxList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L155)]

<span data-ttu-id="9c5ce-329">Chaque image est divisée en grille de cellules `13 x 13`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-329">Each image is divided into a grid of `13 x 13` cells.</span></span> <span data-ttu-id="9c5ce-330">Chaque cellule contient cinq rectangles englobants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-330">Each cell contains five bounding boxes.</span></span> <span data-ttu-id="9c5ce-331">Sous la variable `boxes`, ajoutez le code pour traiter tous les rectangles de chacune des cellules.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-331">Below the `boxes` variable, add code to process all of the boxes in each of the cells.</span></span>

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

<span data-ttu-id="9c5ce-332">Dans la boucle la plus interne, calculez la position de départ du rectangle actuel au sein de la sortie du modèle unidimensionnelle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-332">Inside the inner-most loop, calculate the starting position of the current box within the one-dimensional model output.</span></span>

[!code-csharp [ChannelDef](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L163)]

<span data-ttu-id="9c5ce-333">Directement en dessous, utilisez la méthode `ExtractBoundingBoxDimensions` pour obtenir les dimensions du rectangle englobant actuel.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-333">Directly below that, use the `ExtractBoundingBoxDimensions` method to get the dimensions of the current bounding box.</span></span>

[!code-csharp [GetBBoxDims](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L165)]

<span data-ttu-id="9c5ce-334">Utilisez ensuite la méthode `GetConfidence` pour obtenir la confiance du rectangle englobant actuel.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-334">Then, use the `GetConfidence` method to get the confidence for the current bounding box.</span></span>

[!code-csharp [GetConfidence](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L167)]

<span data-ttu-id="9c5ce-335">Après, utilisez la méthode `MapBoundingBoxToCell` pour mapper le rectangle englobant actuel à la cellule active en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-335">After that, use the `MapBoundingBoxToCell` method to map the current bounding box to the current cell being processed.</span></span>

[!code-csharp [MapBoundingBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L169)]

<span data-ttu-id="9c5ce-336">Avant d’aller plus loin dans le traitement, vérifiez si votre valeur de confiance est supérieure au seuil fourni.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-336">Before doing any further processing, check whether your confidence value is greater than the threshold provided.</span></span> <span data-ttu-id="9c5ce-337">Si elle ne l’est pas, traitez le rectangle englobant suivant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-337">If not, process the next bounding box.</span></span>

[!code-csharp [CheckThreshold1](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L171-L172)]

<span data-ttu-id="9c5ce-338">Sinon, continuez à traiter la sortie.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-338">Otherwise, continue processing the output.</span></span> <span data-ttu-id="9c5ce-339">L’étape suivante consiste à obtenir la distribution de probabilité des classes prédites pour le rectangle englobant actuel en utilisant la méthode `ExtractClasses`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-339">The next step is to get the probability distribution of the predicted classes for the current bounding box using the `ExtractClasses` method.</span></span>

[!code-csharp [ExtractClasses](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L174)]

<span data-ttu-id="9c5ce-340">Utilisez ensuite la méthode `GetTopResult` pour obtenir la valeur et l’index de la classe avec la probabilité la plus forte pour le rectangle actuel et calculer son score.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-340">Then, use the `GetTopResult` method to get the value and index of the class with the highest probability for the current box and compute its score.</span></span>

[!code-csharp [GetTopResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L176-L177)]

<span data-ttu-id="9c5ce-341">Utilisez `topScore` pour une fois de plus conserver uniquement les rectangles englobants qui se trouvent au-dessus du seuil spécifié.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-341">Use the `topScore` to once again keep only those bounding boxes that are above the specified threshold.</span></span>

[!code-csharp [CheckThreshold2](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L179-L180)]

<span data-ttu-id="9c5ce-342">Enfin, si le rectangle englobant actuel dépasse le seuil, créez un objet `BoundingBox` et ajoutez-le à la liste des `boxes`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-342">Finally, if the current bounding box exceeds the threshold, create a new `BoundingBox` object and add it to the `boxes` list.</span></span>

[!code-csharp [AddBBoxToList](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L182-L194)]

<span data-ttu-id="9c5ce-343">Une fois que toutes les cellules de l’image ont été traitées, retournez la liste des `boxes`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-343">Once all cells in the image have been processed, return the `boxes` list.</span></span> <span data-ttu-id="9c5ce-344">Ajoutez l’instruction return suivante sous la boucle for la plus externe dans la méthode `ParseOutputs`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-344">Add the following return statement below the outer-most for-loop in the `ParseOutputs` method.</span></span>

[!code-csharp [ReturnBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L198)]

### <a name="filter-overlapping-boxes"></a><span data-ttu-id="9c5ce-345">Filtrer les rectangles qui se chevauchent</span><span class="sxs-lookup"><span data-stu-id="9c5ce-345">Filter overlapping boxes</span></span>

<span data-ttu-id="9c5ce-346">Maintenant que tous les rectangles englobants à confiance élevée ont été extraits de la sortie du modèle, il faut procéder à un autre filtrage pour supprimer les images qui se chevauchent.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-346">Now that all of the highly confident bounding boxes have been extracted from the model output, additional filtering needs to be done to remove overlapping images.</span></span> <span data-ttu-id="9c5ce-347">Ajoutez une méthode appelée `FilterBoundingBoxes` sous la méthode `ParseOutputs` :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-347">Add a method called `FilterBoundingBoxes` below the `ParseOutputs` method:</span></span>

```csharp
public IList<YoloBoundingBox> FilterBoundingBoxes(IList<YoloBoundingBox> boxes, int limit, float threshold)
{

}
```

<span data-ttu-id="9c5ce-348">Dans la méthode `FilterBoundingBoxes`, commencez par créer un tableau égal à la taille des rectangles détectés et par marquer tous les emplacements comme actifs ou prêts pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-348">Inside the `FilterBoundingBoxes` method, start off by creating an array equal to the size of detected boxes and marking all slots as active or ready for processing.</span></span>

[!code-csharp [InitActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L203-L207)]

<span data-ttu-id="9c5ce-349">Triez ensuite la liste contenant vos rectangles englobants dans l’ordre décroissant en fonction de la confiance.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-349">Then, sort the list containing your bounding boxes in descending order based on confidence.</span></span>

[!code-csharp [SortBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L209-L211)]

<span data-ttu-id="9c5ce-350">Ensuite, créez une liste pour contenir les résultats filtrés.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-350">After that, create a list to hold the filtered results.</span></span>

[!code-csharp [InitFilterResult](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L213)]

<span data-ttu-id="9c5ce-351">Commencez à traiter chaque rectangle englobant en effectuant une itération sur chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-351">Begin processing each bounding box by iterating over each of the bounding boxes.</span></span>

```csharp
for (int i = 0; i < boxes.Count; i++)
{

}
```

<span data-ttu-id="9c5ce-352">Dans cette boucle for, vérifiez si le rectangle englobant actuel peut être traité.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-352">Inside of this for-loop, check whether the current bounding box can be processed.</span></span>

```csharp
if (isActiveBoxes[i])
{

}
```

<span data-ttu-id="9c5ce-353">Dans ce cas, ajoutez le rectangle englobant à la liste des résultats.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-353">If so, add the bounding box to the list of results.</span></span> <span data-ttu-id="9c5ce-354">Si les résultats dépassent la limite spécifiée des rectangles à extraire, rompez la boucle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-354">If the results exceeds the specified limit of boxes to be extracted, break out of the loop.</span></span> <span data-ttu-id="9c5ce-355">Ajoutez le code suivant dans l’instruction if.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-355">Add the following code inside the if-statement.</span></span>

[!code-csharp [AddFirstBBoxToResults](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L219-L223)]

<span data-ttu-id="9c5ce-356">Sinon, regardez les rectangles englobants adjacents.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-356">Otherwise, look at the adjacent bounding boxes.</span></span> <span data-ttu-id="9c5ce-357">Ajoutez le code suivant sous le contrôle de la limite de rectangle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-357">Add the following code below the box limit check.</span></span>

```csharp
for (var j = i + 1; j < boxes.Count; j++)
{

}
```

<span data-ttu-id="9c5ce-358">Comme pour le premier rectangle, si le rectangle adjacent est actif ou prêt à être traité, utilisez la méthode `IntersectionOverUnion` pour vérifier si le premier rectangle et le deuxième rectangle dépassent le seuil spécifié.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-358">Like the first box, if the adjacent box is active or ready to be processed, use the `IntersectionOverUnion` method to check whether the first box and the second box exceed the specified threshold.</span></span> <span data-ttu-id="9c5ce-359">Ajoutez le code suivant à votre boucle for la plus interne.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-359">Add the following code to your inner-most for-loop.</span></span>

[!code-csharp [IOUBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L227-L239)]

<span data-ttu-id="9c5ce-360">En dehors de la boucle for la plus interne qui vérifie les rectangles englobants adjacents, regardez s’il reste d’éventuels rectangles englobants à traiter.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-360">Outside of the inner-most for-loop that checks adjacent bounding boxes, see whether there are any remaining bounding boxes to be processed.</span></span> <span data-ttu-id="9c5ce-361">Si ce n’est pas le cas, rompez la boucle for externe.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-361">If not, break out of the outer for-loop.</span></span>

[!code-csharp [CheckActiveSlots](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L242-L243)]

<span data-ttu-id="9c5ce-362">Enfin, en dehors de la boucle for initiale de la méthode `FilterBoundingBoxes`, retournez les résultats :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-362">Finally, outside of the initial for-loop of the `FilterBoundingBoxes` method, return the results:</span></span>

[!code-csharp [ReturnFilteredBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/YoloParser/YoloOutputParser.cs#L246)]

<span data-ttu-id="9c5ce-363">Idéaux!</span><span class="sxs-lookup"><span data-stu-id="9c5ce-363">Great!</span></span> <span data-ttu-id="9c5ce-364">Il est maintenant temps d’utiliser ce code avec le modèle de scoring.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-364">Now it's time to use this code along with the model for scoring.</span></span>

## <a name="use-the-model-for-scoring"></a><span data-ttu-id="9c5ce-365">Utiliser le modèle pour le scoring</span><span class="sxs-lookup"><span data-stu-id="9c5ce-365">Use the model for scoring</span></span>

<span data-ttu-id="9c5ce-366">Tout comme le post-traitement, il faut suivre quelques étapes pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-366">Just like with post-processing, there are a few steps in the scoring steps.</span></span> <span data-ttu-id="9c5ce-367">Pour vous y aider, ajoutez une classe qui contiendra la logique de scoring à votre projet.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-367">To help with this, add a class that will contain the scoring logic to your project.</span></span>

1. <span data-ttu-id="9c5ce-368">Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-368">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="9c5ce-369">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *OnnxModelScorer.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-369">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *OnnxModelScorer.cs*.</span></span> <span data-ttu-id="9c5ce-370">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-370">Then, select the **Add** button.</span></span>

    <span data-ttu-id="9c5ce-371">Le fichier *OnnxModelScorer.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-371">The *OnnxModelScorer.cs* file opens in the code editor.</span></span> <span data-ttu-id="9c5ce-372">Ajoutez l’instruction `using` suivante en haut de *OnnxModelScorer.cs* :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-372">Add the following `using` statement to the top of *OnnxModelScorer.cs*:</span></span>

    [!code-csharp [ScorerUsings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L1-L7)]

    <span data-ttu-id="9c5ce-373">Dans la définition de la classe `OnnxModelScorer`, ajoutez les variables suivantes.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-373">Inside the `OnnxModelScorer` class definition, add the following variables.</span></span>

    [!code-csharp [InitScorerVars](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L13-L17)]

    <span data-ttu-id="9c5ce-374">Juste en dessous, créez un constructeur pour la classe `OnnxModelScorer` qui initialisera les variables déjà définies.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-374">Directly below that, create a constructor for the `OnnxModelScorer` class that will initialize the previously defined variables.</span></span>

    [!code-csharp [ScorerCtor](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L19-L24)]

    <span data-ttu-id="9c5ce-375">Une fois que vous avez créé le constructeur, définissez quelques structs qui contiennent les variables relatives aux paramètres de l’image et du modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-375">Once you have created the constructor, define a couple of structs that contain variables related to the image and model settings.</span></span> <span data-ttu-id="9c5ce-376">Créez un struct appelé `ImageNetSettings` pour contenir la hauteur et la largeur attendues comme entrée pour le modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-376">Create a struct called `ImageNetSettings` to contain the height and width expected as input for the model.</span></span>

    [!code-csharp [ImageNetSettingStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L26-L30)]

    <span data-ttu-id="9c5ce-377">Ensuite, créez un autre struct appelé `TinyYoloModelSettings` qui contient les noms des couches d’entrée et de sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-377">After that, create another struct called `TinyYoloModelSettings` which contains the names of the input and output layers of the model.</span></span> <span data-ttu-id="9c5ce-378">Pour visualiser le nom des couches d’entrée et de sortie du modèle, vous pouvez utiliser un outil comme [Netron](https://github.com/lutzroeder/netron).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-378">To visualize the name of the input and output layers of the model, you can use a tool like [Netron](https://github.com/lutzroeder/netron).</span></span>

    [!code-csharp [YoloSettingsStruct](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L32-L43)]

    <span data-ttu-id="9c5ce-379">Après, créez le premier ensemble de méthodes à utiliser pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-379">Next, create the first set of methods use for scoring.</span></span> <span data-ttu-id="9c5ce-380">Créez la méthode `LoadModel` dans votre classe `OnnxModelScorer`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-380">Create the `LoadModel` method inside of your `OnnxModelScorer` class.</span></span>

    ```csharp
    private ITransformer LoadModel(string modelLocation)
    {

    }
    ```

    <span data-ttu-id="9c5ce-381">Dans la méthode `LoadModel`, ajoutez le code suivant pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-381">Inside the `LoadModel` method, add the following code for logging.</span></span>

    [!code-csharp [LoadModelLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L47-L49)]

    <span data-ttu-id="9c5ce-382">Les pipelines ML.NET doivent connaître le schéma de données sur lequel opérer quand la méthode [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) est appelée.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-382">ML.NET pipelines need to know the data schema to operate on when the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method is called.</span></span> <span data-ttu-id="9c5ce-383">Dans ce cas, un processus similaire à l’entraînement sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-383">In this case, a process similar to training will be used.</span></span> <span data-ttu-id="9c5ce-384">Toutefois, étant donné qu’aucun véritable entraînement ne se produit, il est acceptable d’utiliser une [`IDataView`](xref:Microsoft.ML.IDataView) vide.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-384">However, because no actual training is happening, it is acceptable to use an empty [`IDataView`](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="9c5ce-385">Créez une [`IDataView`](xref:Microsoft.ML.IDataView) pour le pipeline à partir d’une liste vide.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-385">Create a new [`IDataView`](xref:Microsoft.ML.IDataView) for the pipeline from an empty list.</span></span>

    [!code-csharp [LoadEmptyIDV](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L52)]

    <span data-ttu-id="9c5ce-386">En dessous, définissez le pipeline.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-386">Below that, define the pipeline.</span></span> <span data-ttu-id="9c5ce-387">Le pipeline se compose de quatre transformations.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-387">The pipeline will consist of four transforms.</span></span>

    - <span data-ttu-id="9c5ce-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) charge l’image en tant que bitmap.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-388">[`LoadImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages*) loads the image as a Bitmap.</span></span>
    - <span data-ttu-id="9c5ce-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) redimensionne l’image à la taille spécifiée (dans le cas présent, `416 x 416`).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-389">[`ResizeImages`](xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages*) rescales the image to the size specified (in this case, `416 x 416`).</span></span>
    - <span data-ttu-id="9c5ce-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) change la représentation en pixels de l’image en passant d’une bitmap à un vecteur numérique.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-390">[`ExtractPixels`](xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels*) changes the pixel representation of the image from a Bitmap to a numerical vector.</span></span>
    - <span data-ttu-id="9c5ce-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) charge le modèle ONNX et l’utilise pour effectuer un scoring sur les données fournies.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-391">[`ApplyOnnxModel`](xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel*) loads the ONNX model and uses it to score on the data provided.</span></span>

    <span data-ttu-id="9c5ce-392">Définissez votre pipeline dans la méthode `LoadModel` sous la variable `data`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-392">Define your pipeline in the `LoadModel` method below the `data` variable.</span></span>

    [!code-csharp [ScoringPipeline](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L55-L58)]

    <span data-ttu-id="9c5ce-393">Il est maintenant temps d’instancier le modèle pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-393">Now it's time to instantiate the model for scoring.</span></span> <span data-ttu-id="9c5ce-394">Appelez la méthode [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) sur le pipeline et retournez-la pour poursuivre le traitement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-394">Call the [`Fit`](xref:Microsoft.ML.IEstimator%601.Fit*) method on the pipeline and return it for further processing.</span></span>

    [!code-csharp [FitReturnModel](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L61-L63)]

<span data-ttu-id="9c5ce-395">Une fois que le modèle est chargé, il peut être utilisé pour faire des prédictions.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-395">Once the model is loaded, it can then be used to make predictions.</span></span> <span data-ttu-id="9c5ce-396">Pour faciliter ce processus, créez une méthode appelée `PredictDataUsingModel` sous la méthode `LoadModel`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-396">To facilitate that process, create a method called `PredictDataUsingModel` below the `LoadModel` method.</span></span>

```csharp
private IEnumerable<float[]> PredictDataUsingModel(IDataView testData, ITransformer model)
{

}
```

<span data-ttu-id="9c5ce-397">Dans `PredictDataUsingModel`, ajoutez le code suivant pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-397">Inside the `PredictDataUsingModel`, add the following code for logging.</span></span>

[!code-csharp [PredictDataLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L68-L71)]

<span data-ttu-id="9c5ce-398">Ensuite, utilisez la méthode [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) pour le scoring des données.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-398">Then, use the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method to score the data.</span></span>

[!code-csharp [ScoreImages](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L73)]

<span data-ttu-id="9c5ce-399">Extrayez les probabilités prédites et retournez-les pour un traitement supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-399">Extract the predicted probabilities and return them for additional processing.</span></span>

[!code-csharp [ReturnModelOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L75-L77)]

<span data-ttu-id="9c5ce-400">Maintenant que les deux étapes sont configurées, fusionnez-les en une seule méthode.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-400">Now that both steps are set up, combine them into a single method.</span></span> <span data-ttu-id="9c5ce-401">Sous la méthode `PredictDataUsingModel`, ajoutez une nouvelle méthode appelée `Score`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-401">Below the `PredictDataUsingModel` method, add a new method called `Score`.</span></span>

[!code-csharp [ScoreMethod](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/OnnxModelScorer.cs#L80-L85)]

<span data-ttu-id="9c5ce-402">Vous avez presque fini !</span><span class="sxs-lookup"><span data-stu-id="9c5ce-402">Almost there!</span></span> <span data-ttu-id="9c5ce-403">À présent, passons à la pratique.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-403">Now it's time to put it all to use.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="9c5ce-404">Détecter des objets</span><span class="sxs-lookup"><span data-stu-id="9c5ce-404">Detect objects</span></span>

<span data-ttu-id="9c5ce-405">Maintenant que la configuration est terminée, il est temps de détecter des objets.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-405">Now that all of the setup is complete, it's time to detect some objects.</span></span> <span data-ttu-id="9c5ce-406">Commencez par ajouter des références au scoreur et à l’analyseur dans votre classe *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-406">Start off by adding references to the scorer and parser in your *Program.cs* class.</span></span>

[!code-csharp [ReferenceScorerParser](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L8-L9)]

### <a name="score-and-parse-model-outputs"></a><span data-ttu-id="9c5ce-407">Scorer et analyser les sorties du modèle</span><span class="sxs-lookup"><span data-stu-id="9c5ce-407">Score and parse model outputs</span></span>

<span data-ttu-id="9c5ce-408">Dans la méthode `Main` de votre classe *Program.cs*, ajoutez une instruction try-catch.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-408">Inside the `Main` method of your *Program.cs* class, add a try-catch statement.</span></span>

```csharp
try
{

}
catch (Exception ex)
{
    Console.WriteLine(ex.ToString());
}
```

<span data-ttu-id="9c5ce-409">Dans le bloc `try`, commencez à implémenter la logique de détection d’objet.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-409">Inside of the `try` block, start implementing the object detection logic.</span></span> <span data-ttu-id="9c5ce-410">Chargez d’abord les données dans une [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-410">First, load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

[!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L29-L30)]

<span data-ttu-id="9c5ce-411">Créez ensuite une instance de `OnnxModelScorer` et utilisez-la pour le scoring des données chargées.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-411">Then, create an instance of `OnnxModelScorer` and use it to score the loaded data.</span></span>

[!code-csharp [ScoreData](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L33-L36)]

<span data-ttu-id="9c5ce-412">À présent, passons à l’étape de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-412">Now it's time for the post-processing step.</span></span> <span data-ttu-id="9c5ce-413">Créez une instance de `YoloOutputParser` et utilisez-la pour traiter la sortie du modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-413">Create an instance of `YoloOutputParser` and use it to process the model output.</span></span>

[!code-csharp [ParsePredictions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L39-L44)]

<span data-ttu-id="9c5ce-414">Une fois que la sortie du modèle a été traitée, il est temps de tracer les rectangles englobants sur les images.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-414">Once the model output has been processed, it's time to draw the bounding boxes on the images.</span></span>

### <a name="visualize-predictions"></a><span data-ttu-id="9c5ce-415">Visualiser des prédictions</span><span class="sxs-lookup"><span data-stu-id="9c5ce-415">Visualize predictions</span></span>

<span data-ttu-id="9c5ce-416">Une fois que le modèle a scoré les images et que les sorties ont été traitées, les rectangles englobants doivent être tracés sur l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-416">After the model has scored the images and the outputs have been processed, the bounding boxes have to be drawn on the image.</span></span> <span data-ttu-id="9c5ce-417">Pour ce faire, ajoutez une méthode appelée `DrawBoundingBox` en dessous de la méthode `GetAbsolutePath` dans *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-417">To do so, add a method called `DrawBoundingBox` below the `GetAbsolutePath` method inside of *Program.cs*.</span></span>

```csharp
private static void DrawBoundingBox(string inputImageLocation, string outputImageLocation, string imageName, IList<YoloBoundingBox> filteredBoundingBoxes)
{

}
```

<span data-ttu-id="9c5ce-418">Tout d’abord, chargez l’image et récupérez les dimensions de hauteur et de largeur dans la méthode `DrawBoundingBox`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-418">First, load the image and get the height and width dimensions in the `DrawBoundingBox` method.</span></span>

[!code-csharp [LoadImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L78-L81)]

<span data-ttu-id="9c5ce-419">Ensuite, créez une boucle for-each pour itérer sur chaque rectangle englobant détecté par le modèle.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-419">Then, create a for-each loop to iterate over each of the bounding boxes detected by the model.</span></span>

```csharp
foreach (var box in filteredBoundingBoxes)
{

}
```

<span data-ttu-id="9c5ce-420">À l’intérieur de la boucle for-each, récupérez les dimensions du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-420">Inside of the for-each loop, get the dimensions of the bounding box.</span></span>

[!code-csharp [GetBBoxDimensions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L86-L89)]

<span data-ttu-id="9c5ce-421">Étant donné que les dimensions du rectangle englobant correspondent à l’entrée de modèle de `416 x 416`, adaptez les dimensions du rectangle englobant pour qu’elles correspondent à la taille réelle de l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-421">Because the dimensions of the bounding box correspond to the model input of `416 x 416`, scale the bounding box dimensions to match the actual size of the image.</span></span>

[!code-csharp [ScaleImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L92-L95)]

<span data-ttu-id="9c5ce-422">Ensuite, définissez un modèle pour le texte qui s’affichera au-dessus de chaque cadre englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-422">Then, define a template for text that will appear above each bounding box.</span></span> <span data-ttu-id="9c5ce-423">Le texte contient la classe de l’objet qui se trouve dans le rectangle englobant respectif, ainsi que l’indice de confiance.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-423">The text will contain the class of the object inside of the respective bounding box as well as the confidence.</span></span>

[!code-csharp [DefineBBoxText](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L98)]

<span data-ttu-id="9c5ce-424">Pour tracer sur l’image, convertissez-la en objet [`Graphics`](xref:System.Drawing.Graphics).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-424">In order to draw on the image, convert it to a [`Graphics`](xref:System.Drawing.Graphics) object.</span></span>

```csharp
using (Graphics thumbnailGraphic = Graphics.FromImage(image))
{

}
```

<span data-ttu-id="9c5ce-425">Dans le bloc de code `using`, réglez les paramètres d’objet [`Graphics`](xref:System.Drawing.Graphics) du graphique.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-425">Inside the `using` code block, tune the graphic's [`Graphics`](xref:System.Drawing.Graphics) object settings.</span></span>

[!code-csharp [TuneGraphicSettings](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L102-L104)]

<span data-ttu-id="9c5ce-426">En dessous, définissez les options de police et de couleur du texte et du rectangle englobant.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-426">Below that, set the font and color options for the text and bounding box.</span></span>

[!code-csharp [SetColorOptions](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L106-L114)]

<span data-ttu-id="9c5ce-427">Créez et renseignez un rectangle au-dessus du rectangle englobant pour contenir le texte à l’aide de la méthode [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-427">Create and fill a rectangle above the bounding box to contain the text using the [`FillRectangle`](xref:System.Drawing.Graphics.FillRectangle*) method.</span></span> <span data-ttu-id="9c5ce-428">Cela permettra de distinguer le texte et d’améliorer la lisibilité.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-428">This will help contrast the text and improve readability.</span></span>

[!code-csharp [DrawTextBackground](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L117)]

<span data-ttu-id="9c5ce-429">Écrivez ensuite le texte et tracez le rectangle englobant sur l’image en utilisant les méthodes [`DrawString`](xref:System.Drawing.Graphics.DrawString*) et [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-429">Then, Draw the text and bounding box on the image using the [`DrawString`](xref:System.Drawing.Graphics.DrawString*) and [`DrawRectangle`](xref:System.Drawing.Graphics.DrawRectangle*) methods.</span></span>

[!code-csharp [DrawClassAndBBox](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L118-L121)]

<span data-ttu-id="9c5ce-430">En dehors de la boucle for-each, ajoutez du code pour enregistrer les images dans `outputDirectory`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-430">Outside of the for-each loop, add code to save the images in the `outputDirectory`.</span></span>

[!code-csharp [SaveImage](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L125-L130)]

<span data-ttu-id="9c5ce-431">Pour obtenir des commentaires supplémentaires indiquant que l’application fait des prédictions comme prévu au moment de l’exécution, ajoutez une méthode appelée `LogDetectedObjects` en dessous de la méthode `DrawBoundingBox` dans le fichier *Program.cs* pour générer les objets détectés dans la console.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-431">For additional feedback that the application is making predictions as expected at runtime, add a method called `LogDetectedObjects` below the `DrawBoundingBox` method in the *Program.cs* file to output the detected objects to the console.</span></span>

[!code-csharp [LogOutputs](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L133-L143)]

<span data-ttu-id="9c5ce-432">Maintenant que vous disposez de méthodes d’assistance pour créer des commentaires visuels à partir des prédictions, ajoutez une boucle For pour itérer sur chacune des images scorées.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-432">Now that you have helper methods to create visual feedback from the predictions, add a for-loop to iterate over each of the scored images.</span></span>

```csharp
for (var i = 0; i < images.Count(); i++)
{

}
```

<span data-ttu-id="9c5ce-433">Dans la boucle for, récupérez le nom du fichier image et les rectangles englobants associés.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-433">Inside of the for-loop, get the name of the image file and the bounding boxes associated with it.</span></span>

[!code-csharp [GetImageFileName](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L49-L50)]

<span data-ttu-id="9c5ce-434">Dessous, utilisez la méthode `DrawBoundingBox` pour tracer les rectangles englobants sur l’image.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-434">Below that, use the `DrawBoundingBox` method to draw the bounding boxes on the image.</span></span>

[!code-csharp [DrawBBoxes](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L52)]

<span data-ttu-id="9c5ce-435">Enfin, utilisez la méthode `LogDetectedObjects` pour sortir des prédictions dans la console.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-435">Lastly, use the `LogDetectedObjects` method to output predictions to the console.</span></span>

[!code-csharp [LogPredictionsOutput](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L54)]

<span data-ttu-id="9c5ce-436">Après l’instruction try-catch, ajoutez une logique supplémentaire pour indiquer que le processus a fini l’exécution.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-436">After the try-catch statement, add additional logic to indicate the process is done running.</span></span>

[!code-csharp [EndProcessLog](~/machinelearning-samples/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx/ObjectDetectionConsoleApp/Program.cs#L62-L63)]

<span data-ttu-id="9c5ce-437">C’est tout !</span><span class="sxs-lookup"><span data-stu-id="9c5ce-437">That's it!</span></span>

## <a name="results"></a><span data-ttu-id="9c5ce-438">Résultats</span><span class="sxs-lookup"><span data-stu-id="9c5ce-438">Results</span></span>

<span data-ttu-id="9c5ce-439">Après avoir suivi les étapes précédentes, exécutez votre application console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="9c5ce-439">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="9c5ce-440">Vous devriez obtenir les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-440">Your results should be similar to the following output.</span></span> <span data-ttu-id="9c5ce-441">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-441">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="9c5ce-442">Pour voir les images avec les rectangles englobants, accédez au répertoire `assets/images/output/`.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-442">To see the images with bounding boxes, navigate to the `assets/images/output/` directory.</span></span> <span data-ttu-id="9c5ce-443">Voici un exemple de l’une des images traitées.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-443">Below is a sample from one of the processed images.</span></span>

![Exemple d’image traitée d’une salle de Dinning](./media/object-detection-onnx/dinning-room-table-chairs.png)

<span data-ttu-id="9c5ce-445">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="9c5ce-445">Congratulations!</span></span> <span data-ttu-id="9c5ce-446">Vous avez créé un modèle Machine Learning pour la détection d’objets en réutilisant un modèle `ONNX` préentraîné dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-446">You've now successfully built a machine learning model for object detection by reusing a pre-trained `ONNX` model in ML.NET.</span></span>

<span data-ttu-id="9c5ce-447">Vous pouvez trouver le code source de ce didacticiel dans le référentiel [dotnet/machinelearning-Samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) .</span><span class="sxs-lookup"><span data-stu-id="9c5ce-447">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx) repository.</span></span>

<span data-ttu-id="9c5ce-448">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="9c5ce-448">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="9c5ce-449">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="9c5ce-449">Understand the problem</span></span>
> - <span data-ttu-id="9c5ce-450">Découvrir ce qu’est ONNX et comment il fonctionne avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="9c5ce-450">Learn what ONNX is and how it works with ML.NET</span></span>
> - <span data-ttu-id="9c5ce-451">Comprendre le modèle</span><span class="sxs-lookup"><span data-stu-id="9c5ce-451">Understand the model</span></span>
> - <span data-ttu-id="9c5ce-452">Réutiliser le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="9c5ce-452">Reuse the pre-trained model</span></span>
> - <span data-ttu-id="9c5ce-453">Détecter les objets avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="9c5ce-453">Detect objects with a loaded model</span></span>

<span data-ttu-id="9c5ce-454">Consultez le dépôt d’exemples Machine Learning GitHub pour voir un exemple détaillé de détection d’objets.</span><span class="sxs-lookup"><span data-stu-id="9c5ce-454">Check out the Machine Learning samples GitHub repository to explore an expanded object detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="9c5ce-455">Référentiel GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="9c5ce-455">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/DeepLearning_ObjectDetection_Onnx)
