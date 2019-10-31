---
title: 'Didacticiel : générer un modèle de classification d’images ML.NET à partir d’un modèle TensorFlow pré-formé'
description: Découvrez comment transférer les connaissances d’un modèle TensorFlow existant dans un nouveau modèle de classification d’image ML.NET. Le modèle TensorFlow a été formé pour classifier les images en milliers de catégories. Le modèle ML.NET utilise l’apprentissage de transfert pour classer les images en moins de catégories plus larges.
ms.date: 10/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
author: natke
ms.author: nakersha
ms.openlocfilehash: bd25a24e467148c46958b6e7ce7b18e181dab5fd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129600"
---
# <a name="tutorial-generate-an-mlnet-image-classification-model-from-a-pre-trained-tensorflow-model"></a><span data-ttu-id="2ed0a-105">Didacticiel : générer un modèle de classification d’images ML.NET à partir d’un modèle TensorFlow pré-formé</span><span class="sxs-lookup"><span data-stu-id="2ed0a-105">Tutorial: Generate an ML.NET image classification model from a pre-trained TensorFlow model</span></span>

<span data-ttu-id="2ed0a-106">Découvrez comment transférer les connaissances d’un modèle TensorFlow existant dans un nouveau modèle de classification d’image ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-106">Learn how to transfer the knowledge from an existing TensorFlow model into a new ML.NET image classification model.</span></span>

<span data-ttu-id="2ed0a-107">Le modèle TensorFlow a été formé pour classifier les images en milliers de catégories.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-107">The TensorFlow model was trained to classify images into a thousand categories.</span></span> <span data-ttu-id="2ed0a-108">Le modèle ML.NET utilise une partie du modèle TensorFlow dans son pipeline pour former un modèle afin de classer les images en 3 catégories.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-108">The ML.NET model makes use of part of the TensorFlow model in its pipeline to train a model to classify images into 3 categories.</span></span>

<span data-ttu-id="2ed0a-109">Pour entraîner un modèle de [Classification d’images](https://en.wikipedia.org/wiki/Outline_of_object_recognition) à partir de zéro, il faut définir des millions de paramètres, disposer d’une multitude de données d’apprentissage étiquetées et posséder une grande quantité de ressources de calcul (des centaines d’heures GPU).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="2ed0a-110">S’il n’est pas aussi efficace que l’apprentissage d’un modèle personnalisé à partir de zéro, l’apprentissage par transfert permet de raccourcir ce processus : il s’agit de travailler avec des milliers (et non des millions) d’images étiquetées et de créer assez vite un modèle personnalisé (en une heure sur un ordinateur sans GPU).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span> <span data-ttu-id="2ed0a-111">Ce didacticiel met à l’échelle ce processus plus en détail, en utilisant seulement une douzaine d’images de formation.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-111">This tutorial scales that process down even further, using only a dozen training images.</span></span>

<span data-ttu-id="2ed0a-112">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2ed0a-113">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="2ed0a-113">Understand the problem</span></span>
> * <span data-ttu-id="2ed0a-114">Incorporer le modèle TensorFlow pré-formé dans le pipeline ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ed0a-114">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="2ed0a-115">Former et évaluer le modèle ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ed0a-115">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="2ed0a-116">Classer une image de test</span><span class="sxs-lookup"><span data-stu-id="2ed0a-116">Classify a test image</span></span>

<span data-ttu-id="2ed0a-117">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-117">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="2ed0a-118">Notez que, par défaut, la configuration de projet .NET pour ce tutoriel cible .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-118">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="2ed0a-119">Qu’est-ce que l’apprentissage par transfert ?</span><span class="sxs-lookup"><span data-stu-id="2ed0a-119">What is transfer learning?</span></span>

<span data-ttu-id="2ed0a-120">Le transfert d’apprentissage est le processus qui consiste à utiliser les connaissances acquises tout en résolvant un problème et en l’appliquant à un problème différent mais lié.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-120">Transfer learning is the process of using knowledge gained while solving one problem and applying it to a different but related problem.</span></span>

<span data-ttu-id="2ed0a-121">Pour ce didacticiel, vous utilisez une partie d’un modèle TensorFlow, formé pour classifier les images en mille catégories, dans un modèle ML.NET qui classe les images en trois catégories.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-121">For this tutorial, you use part of a TensorFlow model - trained to classify images into a thousand categories - in an ML.NET model that classifies images into 3 categories.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ed0a-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ed0a-122">Prerequisites</span></span>

* <span data-ttu-id="2ed0a-123">[Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-123">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="2ed0a-124">Package NuGet Microsoft.ML 1.3.1</span><span class="sxs-lookup"><span data-stu-id="2ed0a-124">Microsoft.ML 1.3.1 Nuget package</span></span>
* <span data-ttu-id="2ed0a-125">Package NuGet Microsoft. ML. ImageAnalytics 1.3.1</span><span class="sxs-lookup"><span data-stu-id="2ed0a-125">Microsoft.ML.ImageAnalytics 1.3.1 Nuget package</span></span>
* <span data-ttu-id="2ed0a-126">Package NuGet Microsoft. ML. TensorFlow 1.3.1</span><span class="sxs-lookup"><span data-stu-id="2ed0a-126">Microsoft.ML.TensorFlow 1.3.1 Nuget package</span></span>

* [<span data-ttu-id="2ed0a-127">Le fichier .zip du répertoire de ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="2ed0a-127">The tutorial assets directory .ZIP file</span></span>](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip)

* [<span data-ttu-id="2ed0a-128">Le modèle Machine Learning InceptionV1</span><span class="sxs-lookup"><span data-stu-id="2ed0a-128">The InceptionV1 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-right-machine-learning-task"></a><span data-ttu-id="2ed0a-129">Sélectionner la tâche de Machine Learning appropriée</span><span class="sxs-lookup"><span data-stu-id="2ed0a-129">Select the right machine learning task</span></span>

### <a name="deep-learning"></a><span data-ttu-id="2ed0a-130">Deep Learning</span><span class="sxs-lookup"><span data-stu-id="2ed0a-130">Deep learning</span></span>

<span data-ttu-id="2ed0a-131">Le [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) est un sous-ensemble du Machine Learning, qui révolutionne des domaines comme la Vision par ordinateur et la Reconnaissance vocale.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-131">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="2ed0a-132">L’entraînement des modèles Deep Learning s’effectue à l’aide de grands ensembles de [données étiquetées](https://en.wikipedia.org/wiki/Labeled_data) et de [réseaux neuronaux](https://en.wikipedia.org/wiki/Artificial_neural_network) comportant plusieurs couches d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-132">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="2ed0a-133">Le Deep Learning présente différentes caractéristiques :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-133">Deep learning:</span></span>

* <span data-ttu-id="2ed0a-134">Il fonctionne mieux sur certaines tâches comme la Vision par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-134">Performs better on some tasks like Computer Vision.</span></span>
* <span data-ttu-id="2ed0a-135">Nécessite d’énormes quantités de données d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-135">Requires huge amounts of training data.</span></span>

<span data-ttu-id="2ed0a-136">La classification d’images est une tâche Machine Learning commune qui nous permet de classer automatiquement les images en catégories telles que :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-136">Image Classification is a common Machine Learning task that allows us to automatically classify images into categories such as:</span></span>

* <span data-ttu-id="2ed0a-137">détecter ou non la présence d’un visage dans une image ;</span><span class="sxs-lookup"><span data-stu-id="2ed0a-137">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="2ed0a-138">Détection des chats et des chiens.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-138">Detecting cats vs. dogs.</span></span>

 <span data-ttu-id="2ed0a-139">Ou comme dans les images suivantes, en déterminant si une image est un (n) aliment, jouet ou appareil :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-139">Or as in the following images, determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="2ed0a-140">![image de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![image de nounours](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![image de grille-pain](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="2ed0a-140">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="2ed0a-141">Les images précédentes appartiennent à Wikimedia Commons et sont attribuées ainsi :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-141">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="2ed0a-142">« 220px-Pepperoni_pizza.jpg », domaine public, https://commons.wikimedia.org/w/index.php?curid=79505 ;</span><span class="sxs-lookup"><span data-stu-id="2ed0a-142">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="2ed0a-143">« 119px-Nalle_-_a_small_brown_teddy_bear.jpg », de [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) (photographie personnelle), CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166 ;</span><span class="sxs-lookup"><span data-stu-id="2ed0a-143">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="2ed0a-144">« 193px Broodrooster.jpg », de [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) (travail personnel), CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-144">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="2ed0a-145">Le `Inception model` est formé pour classer les images en milliers de catégories, mais pour ce didacticiel, vous devez classer les images dans un ensemble de catégories plus petit, et uniquement ces catégories.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-145">The `Inception model` is trained to classify images into a thousand categories, but for this tutorial, you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="2ed0a-146">Entrez la partie `transfer` de `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-146">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="2ed0a-147">Vous pouvez transposer la capacité de `Inception model` à identifier et à classer des images aux nouvelles catégories, en nombre limité, de votre classifieur d’images personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-147">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>

* <span data-ttu-id="2ed0a-148">Aliment</span><span class="sxs-lookup"><span data-stu-id="2ed0a-148">Food</span></span>
* <span data-ttu-id="2ed0a-149">Jouet</span><span class="sxs-lookup"><span data-stu-id="2ed0a-149">Toy</span></span>
* <span data-ttu-id="2ed0a-150">Appareil</span><span class="sxs-lookup"><span data-stu-id="2ed0a-150">Appliance</span></span>

<span data-ttu-id="2ed0a-151">Ce didacticiel utilise le modèle d’apprentissage profond du [modèle](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) TensorFlow, un modèle de reconnaissance d’image populaire formé sur le jeu de données `ImageNet`.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-151">This tutorial uses the TensorFlow [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) deep learning model, a popular image recognition model trained on the `ImageNet` dataset.</span></span> <span data-ttu-id="2ed0a-152">Le modèle TensorFlow classifie les images entières en mille classes, telles que « parapluie », « Jersey » et « lave-vaisselle ».</span><span class="sxs-lookup"><span data-stu-id="2ed0a-152">The TensorFlow model classifies entire images into a thousand classes, such as “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="2ed0a-153">Étant donné que le `Inception model` a déjà été formé sur des milliers d’images différentes, en interne, il contient les [fonctionnalités d’image](https://en.wikipedia.org/wiki/Feature_(computer_vision)) nécessaires à l’identification de l’image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-153">Because the `Inception model` has already been pre trained on thousands of different images, internally it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="2ed0a-154">Nous pouvons utiliser ces fonctionnalités d’image interne dans le modèle pour effectuer l’apprentissage d’un nouveau modèle avec beaucoup moins de classes.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-154">We can make use of these internal image features in the model to train a new model with far fewer classes.</span></span>

<span data-ttu-id="2ed0a-155">Comme le montre le diagramme suivant, vous ajoutez une référence aux packages NuGet ML.NET dans vos applications .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-155">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="2ed0a-156">En coulisses, ML.NET inclut et référence la bibliothèque `TensorFlow` native qui vous permet d’écrire du code qui charge un fichier de modèle de `TensorFlow` formé existant.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-156">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file.</span></span>

![Diagramme ML.NET de transformation TensorFlow](./media/image-classification/tensorflow-mlnet.png)

### <a name="multiclass-classification"></a><span data-ttu-id="2ed0a-158">Classification multiclasse</span><span class="sxs-lookup"><span data-stu-id="2ed0a-158">Multiclass classification</span></span>

<span data-ttu-id="2ed0a-159">Après avoir utilisé le modèle d’Inception TensorFlow pour extraire les fonctionnalités qui conviennent comme entrée pour un algorithme de Machine Learning classique, nous ajoutons un [classifieur multiclasse](../resources/tasks.md#multiclass-classification)ml.net.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-159">After using the TensorFlow inception model to extract features suitable as input for a classical machine learning algorithm, we add an ML.NET [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span>

<span data-ttu-id="2ed0a-160">Le formateur spécifique utilisé dans ce cas est l' [algorithme de régression logistique multimultinomiale](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-160">The specific trainer used in this case is the [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression).</span></span>

<span data-ttu-id="2ed0a-161">L’algorithme implémenté par ce formateur fonctionne bien sur les problèmes liés à un grand nombre de fonctionnalités, ce qui est le cas pour un modèle d’apprentissage profond fonctionnant sur des données d’image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-161">The algorithm implemented by this trainer performs well on problems with a large number of features, which is the case for a deep learning model operating on image data.</span></span>

### <a name="data"></a><span data-ttu-id="2ed0a-162">Données</span><span class="sxs-lookup"><span data-stu-id="2ed0a-162">Data</span></span>

<span data-ttu-id="2ed0a-163">Il y a deux sources de données : le fichier `.tsv` et les fichiers image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-163">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="2ed0a-164">Le fichier `tags.tsv` comporte deux colonnes : la première est définie comme `ImagePath` et la deuxième est le `Label` correspondant à l’image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-164">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="2ed0a-165">L’exemple de fichier suivant ne possède pas de ligne d’en-tête :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-165">The following example file doesn't have a header row, and looks like this:</span></span>

<!-- markdownlint-disable MD010 -->
```tsv
broccoli.jpg    food
pizza.jpg   food
pizza2.jpg  food
teddy2.jpg  toy
teddy3.jpg  toy
teddy4.jpg  toy
toaster.jpg appliance
toaster2.png    appliance
```
<!-- markdownlint-enable MD010 -->

<span data-ttu-id="2ed0a-166">Les images d’apprentissage et de test se trouvent dans les dossiers de ressources que vous allez télécharger dans un fichier zip.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-166">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="2ed0a-167">Elles appartiennent à Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-167">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="2ed0a-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), le dépôt de fichiers multimédias sous licence libre.*</span><span class="sxs-lookup"><span data-stu-id="2ed0a-168">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="2ed0a-169">Extrait le 10:48, le 17 octobre 2018 de : https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span><span class="sxs-lookup"><span data-stu-id="2ed0a-169">Retrieved 10:48, October 17, 2018 from: https://commons.wikimedia.org/wiki/Pizza https://commons.wikimedia.org/wiki/Toaster https://commons.wikimedia.org/wiki/Teddy_bear</span></span>

## <a name="setup"></a><span data-ttu-id="2ed0a-170">Installation</span><span class="sxs-lookup"><span data-stu-id="2ed0a-170">Setup</span></span>

### <a name="create-a-project"></a><span data-ttu-id="2ed0a-171">Créer un projet</span><span class="sxs-lookup"><span data-stu-id="2ed0a-171">Create a project</span></span>

1. <span data-ttu-id="2ed0a-172">Créer une **application console .NET Core** appelée « TransferLearningTF ».</span><span class="sxs-lookup"><span data-stu-id="2ed0a-172">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

1. <span data-ttu-id="2ed0a-173">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    * <span data-ttu-id="2ed0a-174">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    * <span data-ttu-id="2ed0a-175">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span>
    * <span data-ttu-id="2ed0a-176">Cliquez sur la liste déroulante **version** , sélectionnez le package **1.3.1** dans la liste, puis cliquez sur le bouton **installer** .</span><span class="sxs-lookup"><span data-stu-id="2ed0a-176">Click on the **Version** drop-down, select the **1.3.1** package in the list, and select the **Install** button.</span></span>
    * <span data-ttu-id="2ed0a-177">Sélectionnez le bouton **OK** dans la boîte de dialogue **aperçu des modifications** .</span><span class="sxs-lookup"><span data-stu-id="2ed0a-177">Select the **OK** button on the **Preview Changes** dialog.</span></span>
    * <span data-ttu-id="2ed0a-178">Sélectionnez le bouton **J’accepte** dans la boîte de dialogue acceptation de la **licence** si vous acceptez les termes du contrat de licence pour les packages listés.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-178">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>
    * <span data-ttu-id="2ed0a-179">Répétez ces étapes pour **Microsoft. ml. ImageAnalytics v 1.3.1** et **Microsoft. ml. TensorFlow v 1.3.1**.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-179">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.3.1** and **Microsoft.ML.TensorFlow v1.3.1**.</span></span>

### <a name="download-assets"></a><span data-ttu-id="2ed0a-180">Télécharger les ressources</span><span class="sxs-lookup"><span data-stu-id="2ed0a-180">Download assets</span></span>

1. <span data-ttu-id="2ed0a-181">Téléchargez le [fichier zip du répertoire de ressources du projet ](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-181">Download [The project assets directory zip file](https://github.com/dotnet/samples/blob/master/machine-learning/tutorials/TransferLearningTF/image-classifier-assets.zip), and unzip.</span></span>

1. <span data-ttu-id="2ed0a-182">Copiez le répertoire `assets` dans votre répertoire de projet *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-182">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="2ed0a-183">Ce répertoire et ses sous-répertoires contiennent les fichiers de données et d’aide nécessaires à ce tutoriel (sauf pour le modèle Inception, que vous allez télécharger et ajouter à l’étape suivante).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-183">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

1. <span data-ttu-id="2ed0a-184">Téléchargez le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-184">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

1. <span data-ttu-id="2ed0a-185">Copiez le contenu décompressé du répertoire `inception5h` dans le répertoire `assets/inception` de votre projet *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-185">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets/inception` directory.</span></span> <span data-ttu-id="2ed0a-186">Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-186">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Contenu du répertoire Inception](./media/image-classification/inception-files.png)

1. <span data-ttu-id="2ed0a-188">Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-188">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="2ed0a-189">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-189">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="2ed0a-190">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="2ed0a-190">Create classes and define paths</span></span>

1. <span data-ttu-id="2ed0a-191">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-191">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

1. <span data-ttu-id="2ed0a-192">Ajoutez le code suivant à la ligne située juste au-dessus de la méthode `Main` pour spécifier les chemins d’accès aux éléments multimédias :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-192">Add the following code to the line right above the `Main` method to specify the asset paths:</span></span>

    [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

1. <span data-ttu-id="2ed0a-193">Créez des classes pour vos données d’entrée et prédictions.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-193">Create classes for your input data, and predictions.</span></span>

    [!code-csharp[DeclareImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImageData)]

    <span data-ttu-id="2ed0a-194">`ImageData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-194">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

    * <span data-ttu-id="2ed0a-195">`ImagePath` contient le nom du fichier image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-195">`ImagePath` contains the image file name.</span></span>
    * <span data-ttu-id="2ed0a-196">`Label` contient la valeur de l’étiquette d’image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-196">`Label` contains a value for the image label.</span></span>

1. <span data-ttu-id="2ed0a-197">Ajoutez une nouvelle classe à votre projet pour `ImagePrediction` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-197">Add a new class to your project for `ImagePrediction`:</span></span>

    [!code-csharp[DeclareImagePrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareImagePrediction)]

    <span data-ttu-id="2ed0a-198">`ImagePrediction` est la classe de prédiction des images, qui comprend les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-198">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

    * <span data-ttu-id="2ed0a-199">`Score` contient le pourcentage de confiance d’une classification d’image donnée.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-199">`Score` contains the confidence percentage for a given image classification.</span></span>
    * <span data-ttu-id="2ed0a-200">`PredictedLabelValue` contient la valeur de l’étiquette de classification d’image prédite.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-200">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

    <span data-ttu-id="2ed0a-201">`ImagePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-201">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="2ed0a-202">Elle comporte une `string` (`ImagePath`) correspondant au chemin de l’image.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-202">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="2ed0a-203">Le `Label` permet de réutiliser et d’effectuer l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-203">The `Label` is used to reuse and train the model.</span></span> <span data-ttu-id="2ed0a-204">L’attribut `PredictedLabelValue` est utilisé pendant la prédiction et l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-204">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="2ed0a-205">L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-205">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="2ed0a-206">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="2ed0a-206">Initialize variables in Main</span></span>

1. <span data-ttu-id="2ed0a-207">Initialiser la variable `mlContext` avec une nouvelle instance de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-207">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="2ed0a-208">Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-208">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

    [!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

    <span data-ttu-id="2ed0a-209">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-209">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2ed0a-210">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-210">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="create-a-struct-for-inception-model-parameters"></a><span data-ttu-id="2ed0a-211">Créer un struct pour les paramètres de modèle d’Inception</span><span class="sxs-lookup"><span data-stu-id="2ed0a-211">Create a struct for Inception model parameters</span></span>

1. <span data-ttu-id="2ed0a-212">Le modèle d’Inception a plusieurs paramètres que vous devez passer.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-212">The Inception model has several parameters you need to pass in.</span></span> <span data-ttu-id="2ed0a-213">Créez un struct pour mapper les valeurs de paramètre à des noms conviviaux avec le code suivant, juste après la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-213">Create a struct to map the parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

    [!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="2ed0a-214">Créer une méthode d’utilitaire d’affichage</span><span class="sxs-lookup"><span data-stu-id="2ed0a-214">Create a display utility method</span></span>

<span data-ttu-id="2ed0a-215">Étant donné que vous allez afficher les données d’image et les prédictions associées plusieurs fois, créez une méthode d’utilitaire d’affichage qui gère l’affichage des données d’image et des résultats de prédiction.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-215">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

1. <span data-ttu-id="2ed0a-216">Créez la méthode `DisplayResults()` juste après le struct `InceptionSettings` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-216">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

    ```csharp
    private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
    {

    }
    ```

1. <span data-ttu-id="2ed0a-217">Renseignez le corps de la méthode `DisplayResults` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-217">Fill in the body of the `DisplayResults` method:</span></span>

    [!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="2ed0a-218">Créez une méthode d’utilitaire de fichier .tsv</span><span class="sxs-lookup"><span data-stu-id="2ed0a-218">Create a .tsv file utility method</span></span>

1. <span data-ttu-id="2ed0a-219">Créez la méthode `ReadFromTsv()` juste après la méthode `DisplayResults()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-219">Create the `ReadFromTsv()` method, just after the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
    {

    }
    ```

1. <span data-ttu-id="2ed0a-220">Renseignez le corps de la méthode `ReadFromTsv` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-220">Fill in the body of the `ReadFromTsv` method:</span></span>

    [!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]

    <span data-ttu-id="2ed0a-221">Le code analyse le fichier `tags.tsv` pour ajouter le chemin d’accès au fichier image pour la propriété `ImagePath` et le charger et le `Label` dans un objet `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-221">The code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span>

### <a name="create-a-method-to-make-a-prediction"></a><span data-ttu-id="2ed0a-222">Créer une méthode pour effectuer une prédiction</span><span class="sxs-lookup"><span data-stu-id="2ed0a-222">Create a method to make a prediction</span></span>

1. <span data-ttu-id="2ed0a-223">Créez la méthode `ClassifySingleImage()` juste avant la méthode `DisplayResults()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-223">Create the `ClassifySingleImage()` method, just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static void ClassifySingleImage(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="2ed0a-224">Créez un objet `ImageData` qui contient le chemin d’accès qualifié complet et le nom du fichier image pour le `ImagePath`unique.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-224">Create an `ImageData` object that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="2ed0a-225">Ajoutez le code suivant à la fin de la méthode `ClassifySingleImage()` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-225">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

    [!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

1. <span data-ttu-id="2ed0a-226">Effectuez une seule prédiction en ajoutant le code suivant comme ligne suivante dans la méthode `ClassifySingleImage` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-226">Make a single prediction, by adding the following code as the next line in the `ClassifySingleImage` method:</span></span>

    [!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

    <span data-ttu-id="2ed0a-227">Pour récupérer la prédiction, utilisez la méthode [Predict ()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) .</span><span class="sxs-lookup"><span data-stu-id="2ed0a-227">To get the prediction, use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) method.</span></span> <span data-ttu-id="2ed0a-228">Le [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API pratique, qui vous permet d’effectuer une prédiction sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-228">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2ed0a-229">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-229">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2ed0a-230">Il est acceptable d’utiliser dans des environnements à thread unique ou prototype.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-230">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2ed0a-231">Pour améliorer les performances et la sécurité des threads dans les environnements de production, utilisez le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-231">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2ed0a-232">Consultez ce guide sur l' [utilisation de `PredictionEnginePool` dans une API Web ASP.net Core](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-232">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2ed0a-233">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-233">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="2ed0a-234">Affichez le résultat de la prédiction à la fin de la méthode `ClassifySingleImage()` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-234">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

   [!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="construct-the-mlnet-model-pipeline"></a><span data-ttu-id="2ed0a-235">Construire le pipeline de modèle ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ed0a-235">Construct the ML.NET model pipeline</span></span>

<span data-ttu-id="2ed0a-236">Un pipeline de modèle ML.NET est une chaîne d’estimateurs.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-236">An ML.NET model pipeline is a chain of estimators.</span></span> <span data-ttu-id="2ed0a-237">Notez qu’aucune exécution ne se produit pendant la construction du pipeline.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-237">Note that no execution happens during pipeline construction.</span></span> <span data-ttu-id="2ed0a-238">Les objets estimateur sont créés, mais ils ne sont pas exécutés.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-238">The estimator objects are created but not executed.</span></span>

1. <span data-ttu-id="2ed0a-239">Ajouter une méthode pour générer le modèle</span><span class="sxs-lookup"><span data-stu-id="2ed0a-239">Add a method to generate the model</span></span>

    <span data-ttu-id="2ed0a-240">Cette méthode est le cœur du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-240">This method is the heart of the tutorial.</span></span> <span data-ttu-id="2ed0a-241">Il crée un pipeline pour le modèle et forme le pipeline pour produire le modèle ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-241">It creates a pipeline for the model, and trains the pipeline to produce the ML.NET model.</span></span> <span data-ttu-id="2ed0a-242">Il évalue également le modèle par rapport à certaines données de test précédemment invisibles.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-242">It also evaluates the model against some previously unseen test data.</span></span>

    <span data-ttu-id="2ed0a-243">Créez la méthode `GenerateModel()`, juste après le struct `InceptionSettings` et juste avant la méthode `DisplayResults()`, avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-243">Create the `GenerateModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer GenerateModel(MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="2ed0a-244">Ajoutez les estimateurs pour charger, redimensionner et extraire les pixels à partir des données de l’image :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-244">Add the estimators to load, resize and extract the pixels from the image data:</span></span>

    [!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

    <span data-ttu-id="2ed0a-245">Les données de l’image doivent être traitées dans le format attendu par le modèle TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-245">The image data needs to be processed into the format that the TensorFlow model expects.</span></span> <span data-ttu-id="2ed0a-246">Dans ce cas, les images sont chargées en mémoire, redimensionnées à une taille cohérente et les pixels sont extraits dans un vecteur numérique.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-246">In this case, the images are loaded into memory, resized to a consistent size, and the pixels are extracted into a numeric vector.</span></span>

1. <span data-ttu-id="2ed0a-247">Ajoutez l’estimateur pour charger le modèle TensorFlow et le noter :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-247">Add the estimator to load the TensorFlow model, and score it:</span></span>

    [!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="2ed0a-248">Cette étape du pipeline charge le modèle TensorFlow en mémoire, puis traite le vecteur de valeurs de pixel via le réseau de modèles TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-248">This stage in the pipeline loads the TensorFlow model into memory, then processes the vector of pixel values through the TensorFlow model network.</span></span> <span data-ttu-id="2ed0a-249">L’application d’entrées à un modèle d’apprentissage profond et la génération d’une sortie à l’aide du modèle sont appelées **notation**.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-249">Applying inputs to a deep learning model, and generating an output using the model, is referred to as **Scoring**.</span></span> <span data-ttu-id="2ed0a-250">Lorsque vous utilisez le modèle dans son intégralité, la notation effectue une inférence ou une prédiction.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-250">When using the model in its entirety, scoring makes an inference, or prediction.</span></span>

    <span data-ttu-id="2ed0a-251">Dans ce cas, vous utilisez tout le modèle TensorFlow, à l’exception de la dernière couche, qui est la couche qui effectue l’inférence.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-251">In this case, you use all of the TensorFlow model except the last layer, which is the layer that makes the inference.</span></span> <span data-ttu-id="2ed0a-252">La sortie de la couche avant est étiquetée `softmax_2_preactivation`.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-252">The output of the penultimate layer is labeled `softmax_2_preactivation`.</span></span> <span data-ttu-id="2ed0a-253">La sortie de cette couche est effectivement un vecteur de fonctionnalités qui caractérisent les images d’entrée d’origine.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-253">The output of this layer is effectively a vector of features that characterize the original input images.</span></span>

    <span data-ttu-id="2ed0a-254">Ce vecteur de fonctionnalité généré par le modèle TensorFlow sera utilisé comme entrée pour un algorithme d’apprentissage ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-254">This feature vector generated by the TensorFlow model will be used as input to an ML.NET training algorithm.</span></span>

1. <span data-ttu-id="2ed0a-255">Ajoutez l’estimateur pour mapper les étiquettes de chaîne dans les données d’apprentissage aux valeurs de clés entières :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-255">Add the estimator to map the string labels in the training data to integer key values:</span></span>

    [!code-csharp[MapValueToKey](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey)]

    <span data-ttu-id="2ed0a-256">Le formateur ML.NET qui est ajouté ensuite requiert que ses étiquettes soient au format `key` plutôt qu’à des chaînes arbitraires.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-256">The ML.NET trainer that is appended next requires its labels to be in `key` format rather than arbitrary strings.</span></span> <span data-ttu-id="2ed0a-257">Une clé est un nombre qui a un mappage un-à-un à une valeur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-257">A key is a number that has a one to one mapping to a string value.</span></span>

1. <span data-ttu-id="2ed0a-258">Ajoutez l’algorithme d’apprentissage ML.NET :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-258">Add the ML.NET training algorithm:</span></span>

    [!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

1. <span data-ttu-id="2ed0a-259">Ajoutez l’estimateur pour mapper la valeur de clé prédite dans une chaîne :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-259">Add the estimator to map the predicted key value back into a string:</span></span>

    [!code-csharp[MapKeyToValue](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapKeyToValue)]

## <a name="train-the-model"></a><span data-ttu-id="2ed0a-260">Effectuer l’apprentissage du modèle</span><span class="sxs-lookup"><span data-stu-id="2ed0a-260">Train the model</span></span>

1. <span data-ttu-id="2ed0a-261">Charger les données d’apprentissage à l’aide du wrapper [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) .</span><span class="sxs-lookup"><span data-stu-id="2ed0a-261">Load the training data using the [LoadFromTextFile](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile(Microsoft.ML.DataOperationsCatalog,System.String,Microsoft.ML.Data.TextLoader.Options)) wrapper.</span></span> <span data-ttu-id="2ed0a-262">Ajoutez le code suivant comme première ligne de la méthode `GenerateModel()` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-262">Add the following code as the next line in the `GenerateModel()` method:</span></span>

    [!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

    <span data-ttu-id="2ed0a-263">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-263">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="2ed0a-264">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-264">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="2ed0a-265">Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-265">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="2ed0a-266">Effectuer l’apprentissage du modèle avec les données chargées ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-266">Train the model with the data loaded above:</span></span>

    [!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

    <span data-ttu-id="2ed0a-267">La méthode `Fit()` forme votre modèle en appliquant le jeu de données d’apprentissage au pipeline.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-267">The `Fit()` method trains your model by applying the training dataset to the pipeline.</span></span>

## <a name="evaluate-the-accuracy-of-the-model"></a><span data-ttu-id="2ed0a-268">Évaluer la précision du modèle</span><span class="sxs-lookup"><span data-stu-id="2ed0a-268">Evaluate the accuracy of the model</span></span>

1. <span data-ttu-id="2ed0a-269">Chargez et transformez les données de test en ajoutant le code suivant à la ligne suivante de la méthode `GenerateModel` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-269">Load and transform the test data, by adding the following code to the next line of the `GenerateModel` method:</span></span>

    [!code-csharp[LoadAndTransformTestData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadAndTransformTestData "Load and transform test data")]

    <span data-ttu-id="2ed0a-270">Voici quelques exemples d’images que vous pouvez utiliser pour évaluer le modèle.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-270">There are a few sample images that you can use to evaluate the model.</span></span> <span data-ttu-id="2ed0a-271">Comme les données d’apprentissage, celles-ci doivent être chargées dans un `IDataView`, afin de pouvoir être transformées par le modèle.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-271">Like the training data, these need to be loaded into an `IDataView`, so that they can be transformed by the model.</span></span>

1. <span data-ttu-id="2ed0a-272">Ajoutez le code suivant à la méthode `GenerateModel()` pour évaluer le modèle :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-272">Add the following code to the `GenerateModel()` method to evaluate the model:</span></span>

    [!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

    <span data-ttu-id="2ed0a-273">Une fois la prédiction définie, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-273">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

    * <span data-ttu-id="2ed0a-274">Évalue le modèle (compare les valeurs prédites avec le jeu de données de test `labels`).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-274">Assesses the model (compares the predicted values with the test dataset `labels`).</span></span>
    * <span data-ttu-id="2ed0a-275">Retourne les indicateurs de performances du modèle.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-275">Returns the model performance metrics.</span></span>

1. <span data-ttu-id="2ed0a-276">Afficher les métriques de précision du modèle</span><span class="sxs-lookup"><span data-stu-id="2ed0a-276">Display the model accuracy metrics</span></span>

    <span data-ttu-id="2ed0a-277">Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-277">Use the following code to display the metrics, share the results, and then act on them:</span></span>

    [!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

    <span data-ttu-id="2ed0a-278">Les indicateurs suivants sont évalués pour la classification d’images :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-278">The following metrics are evaluated for image classification:</span></span>

    * <span data-ttu-id="2ed0a-279">`Log-loss` (voir [Perte logarithmique](../resources/glossary.md#log-loss)).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-279">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="2ed0a-280">Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-280">You want Log-loss to be as close to zero as possible.</span></span>
    * <span data-ttu-id="2ed0a-281">`Per class Log-loss`.,</span><span class="sxs-lookup"><span data-stu-id="2ed0a-281">`Per class Log-loss`.</span></span> <span data-ttu-id="2ed0a-282">La perte logarithmique doit être aussi proche de zéro que possible.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-282">You want per class Log-loss to be as close to zero as possible.</span></span>

1. <span data-ttu-id="2ed0a-283">Ajoutez le code suivant pour retourner le modèle entraîné à la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-283">Add the following code to return the trained model as the next line:</span></span>

    [!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="run-the-application"></a><span data-ttu-id="2ed0a-284">Exécutez l’application !</span><span class="sxs-lookup"><span data-stu-id="2ed0a-284">Run the application!</span></span>

1. <span data-ttu-id="2ed0a-285">Ajoutez l’appel à `GenerateModel` dans la méthode `Main` après la création de la classe MLContext :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-285">Add the call to `GenerateModel` in the `Main` method after the creation of the MLContext class:</span></span>

    [!code-csharp[CallGenerateModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallGenerateModel)]

1. <span data-ttu-id="2ed0a-286">Ajoutez l’appel à la méthode `ClassifySingleImage()` en tant que ligne de code suivante dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-286">Add the call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

    [!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

1. <span data-ttu-id="2ed0a-287">Exécutez votre application console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-287">Run your console app (Ctrl + F5).</span></span> <span data-ttu-id="2ed0a-288">Vous devriez obtenir les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-288">Your results should be similar to the following output.</span></span>  <span data-ttu-id="2ed0a-289">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-289">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

    ```console
    =============== Training classification model ===============
    Image: broccoli2.jpg predicted as: food with score: 0.8955513
    Image: pizza3.jpg predicted as: food with score: 0.9667718
    Image: teddy6.jpg predicted as: toy with score: 0.9797683
    =============== Classification metrics ===============
    LogLoss is: 0.0653774699265059
    PerClassLogLoss is: 0.110315812569315 , 0.0204391272836966 , 0
    =============== Making single image classification ===============
    Image: toaster3.jpg predicted as: appliance with score: 0.9646884
    ```

<span data-ttu-id="2ed0a-290">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="2ed0a-290">Congratulations!</span></span> <span data-ttu-id="2ed0a-291">Vous avez maintenant correctement créé un modèle de Machine Learning pour la classification d’images en appliquant l’apprentissage de transfert à un modèle de `TensorFlow` dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-291">You've now successfully built a machine learning model for image classification by applying transfer learning to a `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="2ed0a-292">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="2ed0a-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="2ed0a-293">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="2ed0a-293">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2ed0a-294">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="2ed0a-294">Understand the problem</span></span>
> * <span data-ttu-id="2ed0a-295">Incorporer le modèle TensorFlow pré-formé dans le pipeline ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ed0a-295">Incorporate the pre-trained TensorFlow model into the ML.NET pipeline</span></span>
> * <span data-ttu-id="2ed0a-296">Former et évaluer le modèle ML.NET</span><span class="sxs-lookup"><span data-stu-id="2ed0a-296">Train and evaluate the ML.NET model</span></span>
> * <span data-ttu-id="2ed0a-297">Classer une image de test</span><span class="sxs-lookup"><span data-stu-id="2ed0a-297">Classify a test image</span></span>

<span data-ttu-id="2ed0a-298">Consultez le référentiel GitHub d’exemples Machine Learning pour voir un exemple développé de classification d’images.</span><span class="sxs-lookup"><span data-stu-id="2ed0a-298">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2ed0a-299">Référentiel GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="2ed0a-299">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
