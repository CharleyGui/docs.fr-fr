---
title: 'Tutoriel : Reformer le classifieur d’images TensorFlow - Apprentissage par transfert'
description: Apprenez à reformer un modèle de classification des images TensorFlow avec apprentissage par transfert et ML.NET. Le modèle d’origine a été formé pour classer des images individuelles. Après reformation, le nouveau modèle organise les images en grandes catégories.
ms.date: 06/12/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: 9344d0757e140995dfd9ce7d1a355910a81c6d31
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539851"
---
# <a name="tutorial-retrain-a-tensorflow-image-classifier-with-transfer-learning-and-mlnet"></a><span data-ttu-id="d8f50-105">Tutoriel : Reformer un classifieur d’images TensorFlow avec apprentissage par transfert et ML.NET</span><span class="sxs-lookup"><span data-stu-id="d8f50-105">Tutorial: Retrain a TensorFlow image classifier with transfer learning and ML.NET</span></span>

<span data-ttu-id="d8f50-106">Apprenez à reformer un modèle de classification des images TensorFlow avec apprentissage par transfert et ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d8f50-106">Learn how to retrain an image classification TensorFlow model with transfer learning and ML.NET.</span></span> <span data-ttu-id="d8f50-107">Le modèle d’origine a été formé pour classer des images individuelles.</span><span class="sxs-lookup"><span data-stu-id="d8f50-107">The original model was trained to classify individual images.</span></span> <span data-ttu-id="d8f50-108">Après reformation, le nouveau modèle organise les images en grandes catégories.</span><span class="sxs-lookup"><span data-stu-id="d8f50-108">After retraining, the new model organizes the images into broad categories.</span></span> 

<span data-ttu-id="d8f50-109">Pour entraîner un modèle de [Classification d’images](https://en.wikipedia.org/wiki/Outline_of_object_recognition) à partir de zéro, il faut définir des millions de paramètres, disposer d’une multitude de données d’apprentissage étiquetées et posséder une grande quantité de ressources de calcul (des centaines d’heures GPU).</span><span class="sxs-lookup"><span data-stu-id="d8f50-109">Training an [Image Classification](https://en.wikipedia.org/wiki/Outline_of_object_recognition) model from scratch requires setting millions of parameters, a ton of labeled training data and a vast amount of compute resources (hundreds of GPU hours).</span></span> <span data-ttu-id="d8f50-110">S’il n’est pas aussi efficace que l’apprentissage d’un modèle personnalisé à partir de zéro, l’apprentissage par transfert permet de raccourcir ce processus : il s’agit de travailler avec des milliers (et non des millions) d’images étiquetées et de créer assez vite un modèle personnalisé (en une heure sur un ordinateur sans GPU).</span><span class="sxs-lookup"><span data-stu-id="d8f50-110">While not as effective as training a custom model from scratch, transfer learning allows you to shortcut this process by working with thousands of images vs. millions of labeled images and build a customized model fairly quickly (within an hour on a machine without a GPU).</span></span>

<span data-ttu-id="d8f50-111">Dans ce didacticiel, vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="d8f50-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d8f50-112">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="d8f50-112">Understand the problem</span></span>
> * <span data-ttu-id="d8f50-113">Réutiliser et paramétrer le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="d8f50-113">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="d8f50-114">Classer des images</span><span class="sxs-lookup"><span data-stu-id="d8f50-114">Classify Images</span></span>

## <a name="what-is-transfer-learning"></a><span data-ttu-id="d8f50-115">Qu’est-ce que l’apprentissage par transfert ?</span><span class="sxs-lookup"><span data-stu-id="d8f50-115">What is transfer learning?</span></span>

<span data-ttu-id="d8f50-116">Et si vous pouviez réutiliser un modèle déjà entraîné pour résoudre un problème et réentraîner une partie ou la totalité de ses couches de sorte qu’il résolve un problème similaire ?</span><span class="sxs-lookup"><span data-stu-id="d8f50-116">What if you could reuse a model that's already been pre trained to solve a similar problem and retrain either all or some of the layers of that model to make it solve your problem?</span></span> <span data-ttu-id="d8f50-117">Cette technique se nomme [apprentissage par transfert](https://en.wikipedia.org/wiki/Transfer_learning).</span><span class="sxs-lookup"><span data-stu-id="d8f50-117">This technique of reusing part of an already trained model to build a new model is known as [transfer learning](https://en.wikipedia.org/wiki/Transfer_learning).</span></span>

## <a name="image-classification-sample-overview"></a><span data-ttu-id="d8f50-118">Vue d’ensemble de l’exemple de classification d’images</span><span class="sxs-lookup"><span data-stu-id="d8f50-118">Image classification sample overview</span></span>

<span data-ttu-id="d8f50-119">L’exemple est une application console qui s’appuie sur ML.NET pour créer un classifieur d’images en réutilisant un modèle préentraîné avec un petit volume de données d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="d8f50-119">The sample is a console application that uses ML.NET to build an image classifier by reusing a pre-trained model to classify images with a small amount of training data.</span></span>

<span data-ttu-id="d8f50-120">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="d8f50-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span> <span data-ttu-id="d8f50-121">Notez que, par défaut, la configuration de projet .NET pour ce tutoriel cible .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="d8f50-121">Note that by default, the .NET project configuration for this tutorial targets .NET core 2.2.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d8f50-122">Prérequis</span><span class="sxs-lookup"><span data-stu-id="d8f50-122">Prerequisites</span></span>

* <span data-ttu-id="d8f50-123">[Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="d8f50-123">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span> 

* <span data-ttu-id="d8f50-124">Package NuGet Microsoft.ML 1.0.0</span><span class="sxs-lookup"><span data-stu-id="d8f50-124">Microsoft.ML 1.0.0 Nuget package</span></span>
* <span data-ttu-id="d8f50-125">Package NuGet Microsoft.ML.ImageAnalytics 1.0.0</span><span class="sxs-lookup"><span data-stu-id="d8f50-125">Microsoft.ML.ImageAnalytics 1.0.0 Nuget package</span></span>
* <span data-ttu-id="d8f50-126">Package NuGet Microsoft.ML.TensorFlow 0.12.0</span><span class="sxs-lookup"><span data-stu-id="d8f50-126">Microsoft.ML.TensorFlow 0.12.0 Nuget package</span></span>

* [<span data-ttu-id="d8f50-127">Le fichier .zip du répertoire de ressources du tutoriel</span><span class="sxs-lookup"><span data-stu-id="d8f50-127">The tutorial assets directory .ZIP file</span></span>](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip)

* [<span data-ttu-id="d8f50-128">Le modèle Machine Learning InceptionV3</span><span class="sxs-lookup"><span data-stu-id="d8f50-128">The InceptionV3 machine learning model</span></span>](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip)

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="d8f50-129">Sélectionner la tâche d’apprentissage automatique appropriée</span><span class="sxs-lookup"><span data-stu-id="d8f50-129">Select the appropriate machine learning task</span></span>

<span data-ttu-id="d8f50-130">Le [Deep Learning](https://en.wikipedia.org/wiki/Deep_learning) est un sous-ensemble du Machine Learning, qui révolutionne des domaines comme la Vision par ordinateur et la Reconnaissance vocale.</span><span class="sxs-lookup"><span data-stu-id="d8f50-130">[Deep learning](https://en.wikipedia.org/wiki/Deep_learning) is a subset of Machine Learning, which is revolutionizing areas like Computer Vision and Speech Recognition.</span></span>

<span data-ttu-id="d8f50-131">L’entraînement des modèles Deep Learning s’effectue à l’aide de grands ensembles de [données étiquetées](https://en.wikipedia.org/wiki/Labeled_data) et de [réseaux neuronaux](https://en.wikipedia.org/wiki/Artificial_neural_network) comportant plusieurs couches d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="d8f50-131">Deep learning models are trained by using large sets of [labeled data](https://en.wikipedia.org/wiki/Labeled_data) and [neural networks](https://en.wikipedia.org/wiki/Artificial_neural_network) that contain multiple learning layers.</span></span> <span data-ttu-id="d8f50-132">Le Deep Learning présente différentes caractéristiques :</span><span class="sxs-lookup"><span data-stu-id="d8f50-132">Deep learning:</span></span>

* <span data-ttu-id="d8f50-133">Il fonctionne mieux sur certaines tâches comme la Vision par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d8f50-133">Performs better on some tasks like Computer Vision.</span></span>

* <span data-ttu-id="d8f50-134">Il marche bien avec d’énormes volumes de données.</span><span class="sxs-lookup"><span data-stu-id="d8f50-134">Performs well on huge data amounts.</span></span>

<span data-ttu-id="d8f50-135">La classification d’images est une tâche courante de Machine Learning qui permet de classer automatiquement des images dans plusieurs catégories, par exemple :</span><span class="sxs-lookup"><span data-stu-id="d8f50-135">Image Classification is a common Machine Learning task that allows us to automatically classify images into multiple categories such as:</span></span>

* <span data-ttu-id="d8f50-136">détecter ou non la présence d’un visage dans une image ;</span><span class="sxs-lookup"><span data-stu-id="d8f50-136">Detecting a human face in an image or not.</span></span>
* <span data-ttu-id="d8f50-137">détecter des chats ou des chiens.</span><span class="sxs-lookup"><span data-stu-id="d8f50-137">Detecting Cats vs. dogs.</span></span>

 <span data-ttu-id="d8f50-138">On peut également, comme dans les images suivantes, déterminer si une image représente un aliment, un jouet ou un appareil :</span><span class="sxs-lookup"><span data-stu-id="d8f50-138">Or as in the following images determining if an image is a(n)  food, toy, or appliance:</span></span>

<span data-ttu-id="d8f50-139">![image de pizza](./media/image-classification/220px-Pepperoni_pizza.jpg)
![image de nounours](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![image de grille-pain](./media/image-classification/193px-Broodrooster.jpg)</span><span class="sxs-lookup"><span data-stu-id="d8f50-139">![pizza image](./media/image-classification/220px-Pepperoni_pizza.jpg)
![teddy bear image](./media/image-classification/119px-Nalle_-_a_small_brown_teddy_bear.jpg)
![toaster image](./media/image-classification/193px-Broodrooster.jpg)</span></span>

>[!Note]
> <span data-ttu-id="d8f50-140">Les images précédentes appartiennent à Wikimedia Commons et sont attribuées ainsi :</span><span class="sxs-lookup"><span data-stu-id="d8f50-140">The preceding images belong to Wikimedia Commons and are attributed as follows:</span></span>
>
> * <span data-ttu-id="d8f50-141">« 220px-Pepperoni_pizza.jpg », domaine public, https://commons.wikimedia.org/w/index.php?curid=79505 ;</span><span class="sxs-lookup"><span data-stu-id="d8f50-141">"220px-Pepperoni_pizza.jpg" Public Domain, https://commons.wikimedia.org/w/index.php?curid=79505,</span></span>
> * <span data-ttu-id="d8f50-142">« 119px-Nalle_-_a_small_brown_teddy_bear.jpg », de [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) (photographie personnelle), CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166 ;</span><span class="sxs-lookup"><span data-stu-id="d8f50-142">"119px-Nalle_-_a_small_brown_teddy_bear.jpg" By [Jonik](https://commons.wikimedia.org/wiki/User:Jonik) - Self-photographed, CC BY-SA 2.0, https://commons.wikimedia.org/w/index.php?curid=48166.</span></span>
> * <span data-ttu-id="d8f50-143">« 193px Broodrooster.jpg », de [M. Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) (travail personnel), CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403.</span><span class="sxs-lookup"><span data-stu-id="d8f50-143">"193px-Broodrooster.jpg" By [M.Minderhoud](https://nl.wikipedia.org/wiki/Gebruiker:Michiel1972) - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=27403</span></span>

<span data-ttu-id="d8f50-144">L’apprentissage par transfert comporte quelques stratégies, comme *réentraîner toutes les couches* et *avant-dernière couche*.</span><span class="sxs-lookup"><span data-stu-id="d8f50-144">Transfer learning includes a few strategies, such as *retrain all layers* and *penultimate layer*.</span></span> <span data-ttu-id="d8f50-145">Ce tutoriel explique et montre comment utiliser la *stratégie de l’avant-dernière couche*.</span><span class="sxs-lookup"><span data-stu-id="d8f50-145">This tutorial will explain and show how to use the *penultimate layer strategy*.</span></span> <span data-ttu-id="d8f50-146">Cette *stratégie* réutilise un modèle déjà entraîné pour résoudre un problème spécifique.</span><span class="sxs-lookup"><span data-stu-id="d8f50-146">The *penultimate layer strategy* reuses a model that's already been pre-trained to solve a specific problem.</span></span> <span data-ttu-id="d8f50-147">Elle réentraîne la couche finale de ce modèle de sorte qu’il résolve un nouveau problème.</span><span class="sxs-lookup"><span data-stu-id="d8f50-147">The strategy then retrains the final layer of that model to make it solve a new problem.</span></span> <span data-ttu-id="d8f50-148">Le fait de réutiliser le modèle préentraîné dans le nouveau modèle permet de gagner beaucoup de temps et d’économiser de nombreuses ressources.</span><span class="sxs-lookup"><span data-stu-id="d8f50-148">Reusing the pre-trained model as part of your new model will save significant time and resources.</span></span>

<span data-ttu-id="d8f50-149">Le modèle de classification d’images réutilise le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), un modèle TensorFlow classique de reconnaissance d’images, entraîné sur le jeu de données `ImageNet`, qui tente de classer des images entières en un millier de classes, comme « Parapluie », « Pull » et « Lave-vaisselle ».</span><span class="sxs-lookup"><span data-stu-id="d8f50-149">Your image classification model reuses the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), a popular image recognition model trained on the `ImageNet` dataset where the TensorFlow model tries to classify entire images into a thousand classes, like “Umbrella”, “Jersey”, and “Dishwasher”.</span></span>

<span data-ttu-id="d8f50-150">`Inception v3 model`, que l’on peut considérer comme un [réseau neuronal convolutif profond](https://en.wikipedia.org/wiki/Convolutional_neural_network), peut atteindre sur des tâches de reconnaissance visuelle dure des performances raisonnables, au moins égales à l’efficacité humaine dans certains domaines.</span><span class="sxs-lookup"><span data-stu-id="d8f50-150">The `Inception v3 model` can be classified as a [deep convolutional neural network](https://en.wikipedia.org/wiki/Convolutional_neural_network) and can achieve reasonable performance on hard visual recognition tasks, matching or exceeding human performance in some domains.</span></span> <span data-ttu-id="d8f50-151">Le modèle/algorithme, développé par de nombreux chercheurs, s’appuie sur le document d’origine [« Rethinking the Inception Architecture for Computer Vision », Szegedy et al.](https://arxiv.org/abs/1512.00567)</span><span class="sxs-lookup"><span data-stu-id="d8f50-151">The model/algorithm was developed by multiple researchers and based on the original paper: ["Rethinking the Inception Architecture for Computer Vision” by Szegedy, et. al.](https://arxiv.org/abs/1512.00567)</span></span>

<span data-ttu-id="d8f50-152">Étant donné que `Inception model` a déjà été préentraîné sur des milliers d’images différentes, il contient les [caractéristiques des images](https://en.wikipedia.org/wiki/Feature_(computer_vision)) nécessaires à leur identification.</span><span class="sxs-lookup"><span data-stu-id="d8f50-152">Because the `Inception model` has already been pre trained on thousands of different images, it contains the [image features](https://en.wikipedia.org/wiki/Feature_(computer_vision)) needed for image identification.</span></span> <span data-ttu-id="d8f50-153">Les couches inférieures reconnaissent des caractéristiques simples (comme les bords) et les couches supérieures des caractéristiques plus complexes (comme les formes).</span><span class="sxs-lookup"><span data-stu-id="d8f50-153">The lower image feature layers recognize simple features (such as edges) and the higher layers recognize more complex features (such as shapes).</span></span> <span data-ttu-id="d8f50-154">La dernière couche est entraînée sur un ensemble de données beaucoup plus petit, car elle part d’un modèle préentraîné qui sait déjà classer des images.</span><span class="sxs-lookup"><span data-stu-id="d8f50-154">The final layer is trained against a much smaller set of data because you're starting with a pre trained model that already understands how to classify images.</span></span> <span data-ttu-id="d8f50-155">Comme le modèle permet de classer les images dans plus de deux catégories, il s’agit d’un exemple de [classifieur en classes multiples](../resources/tasks.md#multiclass-classification).</span><span class="sxs-lookup"><span data-stu-id="d8f50-155">As your model allows you to classify more than two categories, this is an example of a [multi-class classifier](../resources/tasks.md#multiclass-classification).</span></span> 

<span data-ttu-id="d8f50-156">`TensorFlow` est un kit de ressources de Deep Learning et de Machine Learning très répandu qui permet d’entraîner des réseaux neuronaux profonds (et des calculs numériques généraux) et est implémenté comme un `transformer` dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d8f50-156">`TensorFlow` is a popular deep learning and machine learning toolkit that enables training deep neural networks (and general numeric computations), and is implemented as a `transformer` in ML.NET.</span></span> <span data-ttu-id="d8f50-157">Dans ce tutoriel, il sert à réutiliser `Inception model`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-157">For this tutorial, it's used to reuse the `Inception model`.</span></span>

<span data-ttu-id="d8f50-158">Comme le montre le diagramme suivant, vous ajoutez une référence aux packages NuGet ML.NET dans vos applications .NET Core ou .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d8f50-158">As shown in the following diagram, you add a reference to the ML.NET NuGet packages in your .NET Core or .NET Framework applications.</span></span> <span data-ttu-id="d8f50-159">En coulisses, ML.NET inclut la bibliothèque native `TensorFlow` qui permet d’écrire du code afin de charger un fichier de modèle `TensorFlow` existant pour le scoring.</span><span class="sxs-lookup"><span data-stu-id="d8f50-159">Under the covers, ML.NET includes and references the native `TensorFlow` library that allows you to write code that loads an existing trained `TensorFlow` model file for scoring.</span></span>  

![Diagramme ML.NET de transformation TensorFlow](./media/image-classification/tensorflow-mlnet.png)

<span data-ttu-id="d8f50-161">`Inception model` est entraîné pour classer des images dans un millier de catégories, mais nous devons les classer exclusivement dans un plus petit jeu de catégories.</span><span class="sxs-lookup"><span data-stu-id="d8f50-161">The `Inception model` is trained to classify images into a thousand categories, but you need to classify images in a smaller category set, and only those categories.</span></span> <span data-ttu-id="d8f50-162">Entrez la partie `transfer` de `transfer learning`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-162">Enter the `transfer` part of `transfer learning`.</span></span> <span data-ttu-id="d8f50-163">Vous pouvez transposer la capacité de `Inception model` à identifier et à classer des images aux nouvelles catégories, en nombre limité, de votre classifieur d’images personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d8f50-163">You can transfer the `Inception model`'s ability to recognize and classify images to the new limited categories of your custom image classifier.</span></span>  

 <span data-ttu-id="d8f50-164">Il s’agit de réentraîner la couche finale de ce modèle selon trois catégories :</span><span class="sxs-lookup"><span data-stu-id="d8f50-164">You're going to retrain the final layer of that model using a set of three categories:</span></span>

* <span data-ttu-id="d8f50-165">Aliment</span><span class="sxs-lookup"><span data-stu-id="d8f50-165">Food</span></span>
* <span data-ttu-id="d8f50-166">Jouet</span><span class="sxs-lookup"><span data-stu-id="d8f50-166">Toy</span></span>
* <span data-ttu-id="d8f50-167">Appareil</span><span class="sxs-lookup"><span data-stu-id="d8f50-167">Appliance</span></span>

<span data-ttu-id="d8f50-168">La couche utilise un [algorithme de régression logistique multinomiale](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) afin de trouver la bonne catégorie aussi vite que possible.</span><span class="sxs-lookup"><span data-stu-id="d8f50-168">Your layer uses a [multinomial logistic regression algorithm](https://en.wikipedia.org/wiki/Multinomial_logistic_regression) to find the correct category as quickly as possible.</span></span> <span data-ttu-id="d8f50-169">Cet algorithme se sert des probabilités pour déterminer la réponse, donnant la valeur un à la bonne catégorie et la valeur zéro aux autres.</span><span class="sxs-lookup"><span data-stu-id="d8f50-169">This algorithm classifies using probabilities to determine the answer, giving a one value to the correct category and a zero value to the others.</span></span>  

### <a name="dataset"></a><span data-ttu-id="d8f50-170">DataSet</span><span class="sxs-lookup"><span data-stu-id="d8f50-170">DataSet</span></span>

<span data-ttu-id="d8f50-171">Il y a deux sources de données : le fichier `.tsv` et les fichiers image.</span><span class="sxs-lookup"><span data-stu-id="d8f50-171">There are two data sources: the `.tsv` file, and the image files.</span></span>  <span data-ttu-id="d8f50-172">Le fichier `tags.tsv` comporte deux colonnes : la première est définie comme `ImagePath` et la deuxième est le `Label` correspondant à l’image.</span><span class="sxs-lookup"><span data-stu-id="d8f50-172">The `tags.tsv` file contains two columns: the first one is defined as `ImagePath` and the second one is the `Label` corresponding to the image.</span></span> <span data-ttu-id="d8f50-173">L’exemple de fichier suivant ne possède pas de ligne d’en-tête :</span><span class="sxs-lookup"><span data-stu-id="d8f50-173">The following example file doesn't have a header row, and looks like this:</span></span>

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

<span data-ttu-id="d8f50-174">Les images d’apprentissage et de test se trouvent dans les dossiers de ressources que vous allez télécharger dans un fichier zip.</span><span class="sxs-lookup"><span data-stu-id="d8f50-174">The training and testing images are located in the assets folders that you'll download in a zip file.</span></span> <span data-ttu-id="d8f50-175">Elles appartiennent à Wikimedia Commons.</span><span class="sxs-lookup"><span data-stu-id="d8f50-175">These images belong to Wikimedia Commons.</span></span>
> <span data-ttu-id="d8f50-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), le dépôt de fichiers multimédias sous licence libre.*</span><span class="sxs-lookup"><span data-stu-id="d8f50-176">*[Wikimedia Commons](https://commons.wikimedia.org/w/index.php?title=Main_Page&oldid=313158208), the free media repository.*</span></span> <span data-ttu-id="d8f50-177">Récupéré le 17 octobre 2018 à 10 h 48 aux adresses :</span><span class="sxs-lookup"><span data-stu-id="d8f50-177">Retrieved 10:48, October 17, 2018 from:</span></span>  
> https://commons.wikimedia.org/wiki/Pizza  
> https://commons.wikimedia.org/wiki/Toaster  
> https://commons.wikimedia.org/wiki/Teddy_bear  

## <a name="create-a-console-application"></a><span data-ttu-id="d8f50-178">Créer une application console</span><span class="sxs-lookup"><span data-stu-id="d8f50-178">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="d8f50-179">Créer un projet</span><span class="sxs-lookup"><span data-stu-id="d8f50-179">Create a project</span></span>

1. <span data-ttu-id="d8f50-180">Créer une **application console .NET Core** appelée « TransferLearningTF ».</span><span class="sxs-lookup"><span data-stu-id="d8f50-180">Create a **.NET Core Console Application** called "TransferLearningTF".</span></span>

2. <span data-ttu-id="d8f50-181">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="d8f50-181">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="d8f50-182">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-182">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="d8f50-183">Choisissez « nuget.org » comme source du package, sélectionnez l’onglet Parcourir et recherchez **Microsoft.ML**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-183">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**.</span></span> <span data-ttu-id="d8f50-184">Cliquez sur la liste déroulante **Version** et sélectionnez le package **1.0.0** dans la liste, puis sélectionnez le bouton **Installer**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-184">Click on the **Version** drop-down, select the **1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="d8f50-185">Cliquez sur le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis sur le bouton **J’accepte** dans la boîte de dialogue **Acceptation de la licence** si vous acceptez les termes du contrat de licence pour les packages répertoriés.</span><span class="sxs-lookup"><span data-stu-id="d8f50-185">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="d8f50-186">Répétez ces étapes pour **Microsoft.ML.ImageAnalytics v1.0.0** et **Microsoft.ML.TensorFlow v0.12.0**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-186">Repeat these steps for **Microsoft.ML.ImageAnalytics v1.0.0** and **Microsoft.ML.TensorFlow v0.12.0**.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="d8f50-187">Préparer vos données</span><span class="sxs-lookup"><span data-stu-id="d8f50-187">Prepare your data</span></span>

1. <span data-ttu-id="d8f50-188">Téléchargez le [fichier zip du répertoire de ressources du projet ](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="d8f50-188">Download [The project assets directory zip file](https://download.microsoft.com/download/0/E/5/0E5E0136-21CE-4C66-AC18-9917DED8A4AD/image-classifier-assets.zip), and unzip.</span></span>

2. <span data-ttu-id="d8f50-189">Copiez le répertoire `assets` dans votre répertoire de projet *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="d8f50-189">Copy the `assets` directory into your *TransferLearningTF* project directory.</span></span> <span data-ttu-id="d8f50-190">Ce répertoire et ses sous-répertoires contiennent les fichiers de données et d’aide nécessaires à ce tutoriel (sauf pour le modèle Inception, que vous allez télécharger et ajouter à l’étape suivante).</span><span class="sxs-lookup"><span data-stu-id="d8f50-190">This directory and its subdirectories contain the data and support files (except for the Inception model, which you'll download and add in the next step) needed for this tutorial.</span></span>

3. <span data-ttu-id="d8f50-191">Téléchargez le [modèle Inception](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip) et décompressez-le.</span><span class="sxs-lookup"><span data-stu-id="d8f50-191">Download the [Inception model](https://storage.googleapis.com/download.tensorflow.org/models/inception5h.zip), and unzip.</span></span>

4. <span data-ttu-id="d8f50-192">Copiez le contenu décompressé du répertoire `inception5h` dans le répertoire `assets\inputs-train\inception` de votre projet *TransferLearningTF*.</span><span class="sxs-lookup"><span data-stu-id="d8f50-192">Copy the contents of the `inception5h` directory just unzipped into your *TransferLearningTF* project `assets\inputs-train\inception` directory.</span></span> <span data-ttu-id="d8f50-193">Ce répertoire contient le modèle et les fichiers d’aide supplémentaires nécessaires à ce tutoriel, comme le montre l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="d8f50-193">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![Contenu du répertoire Inception](./media/image-classification/inception-files.png)

5. <span data-ttu-id="d8f50-195">Dans l’Explorateur de solutions, cliquez sur chacun des fichiers du répertoire et des sous-répertoires de ressources et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-195">In Solution Explorer, right-click each of the files in the asset directory and subdirectories and select **Properties**.</span></span> <span data-ttu-id="d8f50-196">Sous **Avancé**, définissez la valeur **Copier dans le répertoire de sortie** sur **Copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-196">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="d8f50-197">Créer des classes et définir des chemins</span><span class="sxs-lookup"><span data-stu-id="d8f50-197">Create classes and define paths</span></span>

<span data-ttu-id="d8f50-198">Ajoutez les instructions `using` supplémentaires suivantes en haut du fichier *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="d8f50-198">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddUsings)]

<span data-ttu-id="d8f50-199">Créez des champs globaux qui représenteront les chemins des différentes ressources, puis des variables globales pour `LabelTokey`, `ImageReal` et `PredictedLabelValue` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-199">Create global fields to hold the paths to the various assets, and global variables for the `LabelTokey`,`ImageReal`, and  `PredictedLabelValue`:</span></span>

* <span data-ttu-id="d8f50-200">`_assetsPath` comporte le chemin des ressources.</span><span class="sxs-lookup"><span data-stu-id="d8f50-200">`_assetsPath` has the path to the assets.</span></span>
* <span data-ttu-id="d8f50-201">`_trainTagsTsv` comporte le chemin du fichier .tsv des balises des données d’images d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="d8f50-201">`_trainTagsTsv` has the path to the training image data tags tsv file.</span></span>
* <span data-ttu-id="d8f50-202">`_predictTagsTsv` comporte le chemin du fichier .tsv des balises des données d’images de prédiction.</span><span class="sxs-lookup"><span data-stu-id="d8f50-202">`_predictTagsTsv` has the path to the prediction image data tags tsv file.</span></span>
* <span data-ttu-id="d8f50-203">`_trainImagesFolder` comporte le chemin des images servant à l’apprentissage du modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-203">`_trainImagesFolder` has the path to the images used to train the model.</span></span>
* <span data-ttu-id="d8f50-204">`_predictImagesFolder` comporte le chemin des images que le modèle entraîné devra classer.</span><span class="sxs-lookup"><span data-stu-id="d8f50-204">`_predictImagesFolder` has the path to the images to be classified by the trained model.</span></span>
* <span data-ttu-id="d8f50-205">`_inceptionPb` comporte le chemin du modèle Inception préentraîné à réutiliser pour réentraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-205">`_inceptionPb` has the path to the pre-trained Inception model to be reused to retrain your model.</span></span>
* <span data-ttu-id="d8f50-206">`_inputImageClassifierZip` comporte le chemin où sera chargé le modèle entraîné.</span><span class="sxs-lookup"><span data-stu-id="d8f50-206">`_inputImageClassifierZip` has the path where the trained model is loaded from.</span></span>
* <span data-ttu-id="d8f50-207">`_outputImageClassifierZip` contient le chemin d’accès où le modèle formé est enregistré.</span><span class="sxs-lookup"><span data-stu-id="d8f50-207">`_outputImageClassifierZip` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="d8f50-208">`LabelTokey` est la valeur `Label` mappée à une clé.</span><span class="sxs-lookup"><span data-stu-id="d8f50-208">`LabelTokey` is the `Label` value mapped to a key.</span></span>
* <span data-ttu-id="d8f50-209">`ImageReal` est la colonne contenant la valeur d’image prédite.</span><span class="sxs-lookup"><span data-stu-id="d8f50-209">`ImageReal`  is the column containing the predicted image value.</span></span>
* <span data-ttu-id="d8f50-210">`PredictedLabelValue` est la colonne contenant la valeur d’étiquette prédite.</span><span class="sxs-lookup"><span data-stu-id="d8f50-210">`PredictedLabelValue` is the column containing the predicted label value.</span></span>

<span data-ttu-id="d8f50-211">Ajoutez le code suivant à la ligne juste au-dessus de la méthode `Main` pour spécifier ces chemins et les autres variables :</span><span class="sxs-lookup"><span data-stu-id="d8f50-211">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="d8f50-212">Créez des classes pour vos données d’entrée et vos prédictions.</span><span class="sxs-lookup"><span data-stu-id="d8f50-212">Create some classes for your input data, and predictions.</span></span> <span data-ttu-id="d8f50-213">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="d8f50-213">Add a new class to your project:</span></span>

1. <span data-ttu-id="d8f50-214">Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-214">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d8f50-215">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImageData.cs*.</span><span class="sxs-lookup"><span data-stu-id="d8f50-215">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImageData.cs*.</span></span> <span data-ttu-id="d8f50-216">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-216">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d8f50-217">Le fichier *ImageData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="d8f50-217">The *ImageData.cs* file opens in the code editor.</span></span> <span data-ttu-id="d8f50-218">Ajoutez l’instruction `using` suivante en haut de *ImageData.cs* :</span><span class="sxs-lookup"><span data-stu-id="d8f50-218">Add the following `using` statement to the top of *ImageData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#AddUsings)]

<span data-ttu-id="d8f50-219">Supprimez la définition de classe existante et ajoutez le code suivant pour la classe `ImageData` au fichier *ImageData.cs* :</span><span class="sxs-lookup"><span data-stu-id="d8f50-219">Remove the existing class definition and add the following code for the `ImageData` class to the *ImageData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/TransferLearningTF/ImageData.cs#DeclareTypes)]

<span data-ttu-id="d8f50-220">`ImageData` est la classe de données d’images d’entrée, qui comprend les champs <xref:System.String> suivants :</span><span class="sxs-lookup"><span data-stu-id="d8f50-220">`ImageData` is the input image data class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="d8f50-221">`ImagePath` contient le nom du fichier image.</span><span class="sxs-lookup"><span data-stu-id="d8f50-221">`ImagePath` contains the image file name.</span></span>
* <span data-ttu-id="d8f50-222">`Label` contient la valeur de l’étiquette d’image.</span><span class="sxs-lookup"><span data-stu-id="d8f50-222">`Label` contains a value for the image label.</span></span>

<span data-ttu-id="d8f50-223">Ajoutez une nouvelle classe à votre projet pour `ImagePrediction` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-223">Add a new class to your project for `ImagePrediction`:</span></span>

1. <span data-ttu-id="d8f50-224">Dans l **’Explorateur de solutions**, cliquez avec le bouton de droite sur le projet, puis sélectionnez **Ajouter** > **Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-224">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="d8f50-225">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *ImagePrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="d8f50-225">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *ImagePrediction.cs*.</span></span> <span data-ttu-id="d8f50-226">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-226">Then, select the **Add** button.</span></span>

    <span data-ttu-id="d8f50-227">Le fichier *ImagePrediction.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="d8f50-227">The *ImagePrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="d8f50-228">Supprimez les instructions `System.Collections.Generic` et `System.Text` `using` en haut de *ImagePrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="d8f50-228">Remove both the `System.Collections.Generic` and the `System.Text` `using` statements at the top of *ImagePrediction.cs*:</span></span>

<span data-ttu-id="d8f50-229">Supprimez la définition de classe existante et ajoutez le code suivant, qui contient la classe `ImagePrediction`, au fichier *ImagePrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="d8f50-229">Remove the existing class definition and add the following code, which has the `ImagePrediction` class, to the *ImagePrediction.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TransferLearningTF/ImagePrediction.cs#DeclareTypes)]

<span data-ttu-id="d8f50-230">`ImagePrediction` est la classe de prédiction des images, qui comprend les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="d8f50-230">`ImagePrediction` is the image prediction class and has the following fields:</span></span>

* <span data-ttu-id="d8f50-231">`Score` contient le pourcentage de confiance d’une classification d’image donnée.</span><span class="sxs-lookup"><span data-stu-id="d8f50-231">`Score` contains the confidence percentage for a given image classification.</span></span>
* <span data-ttu-id="d8f50-232">`PredictedLabelValue` contient la valeur de l’étiquette de classification d’image prédite.</span><span class="sxs-lookup"><span data-stu-id="d8f50-232">`PredictedLabelValue` contains a value for the predicted image classification label.</span></span>

<span data-ttu-id="d8f50-233">`ImagePrediction` représente la classe utilisée pour la prédiction, une fois le modèle formé.</span><span class="sxs-lookup"><span data-stu-id="d8f50-233">`ImagePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="d8f50-234">Elle comporte une `string` (`ImagePath`) correspondant au chemin de l’image.</span><span class="sxs-lookup"><span data-stu-id="d8f50-234">It has a `string` (`ImagePath`) for the image path.</span></span> <span data-ttu-id="d8f50-235">`Label` sert à réutiliser et à réentraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-235">The `Label` is used to reuse and retrain the model.</span></span> <span data-ttu-id="d8f50-236">L’attribut `PredictedLabelValue` est utilisé pendant la prédiction et l’évaluation.</span><span class="sxs-lookup"><span data-stu-id="d8f50-236">The `PredictedLabelValue` is used during prediction and evaluation.</span></span> <span data-ttu-id="d8f50-237">L’évaluation utilise une entrée avec les données d’apprentissage, les valeurs prédites et le modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-237">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="d8f50-238">La [classe MLContext](xref:Microsoft.ML.MLContext) est un point de départ pour toutes les opérations ML.NET, et l’initialisation de `mlContext` crée un environnement ML.NET qui peut être partagé par les objets de flux de travail de création de modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-238">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="d8f50-239">Sur le plan conceptuel, elle est similaire à `DBContext` dans Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d8f50-239">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="d8f50-240">Initialiser les variables dans Principal</span><span class="sxs-lookup"><span data-stu-id="d8f50-240">Initialize variables in Main</span></span>

<span data-ttu-id="d8f50-241">Initialiser la variable `mlContext` avec une nouvelle instance de `MLContext`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-241">Initialize the `mlContext` variable with a new instance of `MLContext`.</span></span>  <span data-ttu-id="d8f50-242">Remplacez la ligne `Console.WriteLine("Hello World!")` par le code suivant dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-242">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CreateMLContext)]

### <a name="create-a-struct-for-default-parameters"></a><span data-ttu-id="d8f50-243">Créer un struct pour les paramètres par défaut</span><span class="sxs-lookup"><span data-stu-id="d8f50-243">Create a struct for default parameters</span></span>

<span data-ttu-id="d8f50-244">Le modèle Inception comporte plusieurs paramètres par défaut qu’il faut passer.</span><span class="sxs-lookup"><span data-stu-id="d8f50-244">The Inception model has several default parameters you need to pass in.</span></span> <span data-ttu-id="d8f50-245">Créez un struct permettant de mapper les valeurs de paramètre par défaut sur les noms conviviaux avec le code suivant, juste après la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-245">Create a struct to map the default parameter values to friendly names with the following code, just after the `Main()` method:</span></span>

[!code-csharp[InceptionSettings](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#InceptionSettings)]

### <a name="create-a-display-utility-method"></a><span data-ttu-id="d8f50-246">Créer une méthode d’utilitaire d’affichage</span><span class="sxs-lookup"><span data-stu-id="d8f50-246">Create a display utility method</span></span>

<span data-ttu-id="d8f50-247">Étant donné que vous allez afficher les données d’image et les prédictions associées plusieurs fois, créez une méthode d’utilitaire d’affichage qui gère l’affichage des données d’image et des résultats de prédiction.</span><span class="sxs-lookup"><span data-stu-id="d8f50-247">Since you'll display the image data and the related predictions more than once, create a display utility method to handle displaying the image and prediction results.</span></span>

<span data-ttu-id="d8f50-248">La méthode `DisplayResults()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8f50-248">The `DisplayResults()` method executes the following tasks:</span></span>

* <span data-ttu-id="d8f50-249">Affiche les résultats prédits.</span><span class="sxs-lookup"><span data-stu-id="d8f50-249">Displays the predicted results.</span></span>

<span data-ttu-id="d8f50-250">Créez la méthode `DisplayResults()` juste après le struct `InceptionSettings` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-250">Create the `DisplayResults()` method, just after the `InceptionSettings` struct, using the following code:</span></span>

```csharp
private static void DisplayResults(IEnumerable<ImagePrediction> imagePredictionData)
{

}
```

<span data-ttu-id="d8f50-251">La méthode `Transform()` a rempli `ImagePath` dans `ImagePrediction` avec les champs prédits.</span><span class="sxs-lookup"><span data-stu-id="d8f50-251">The `Transform()` method populated `ImagePath` in `ImagePrediction` along with the predicted fields.</span></span> <span data-ttu-id="d8f50-252">À mesure que le processus ML.NET progresse, chaque composant ajoute des colonnes, ce qui rend l’affichage des résultats plus facile :</span><span class="sxs-lookup"><span data-stu-id="d8f50-252">As the ML.NET process progresses, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPredictions)]

<span data-ttu-id="d8f50-253">Vous devez appeler la méthode `DisplayResults()` dans les deux méthodes de classification des images.</span><span class="sxs-lookup"><span data-stu-id="d8f50-253">You'll call the `DisplayResults()` method in the two image classification methods.</span></span>

### <a name="create-a-tsv-file-utility-method"></a><span data-ttu-id="d8f50-254">Créez une méthode d’utilitaire de fichier .tsv</span><span class="sxs-lookup"><span data-stu-id="d8f50-254">Create a .tsv file utility method</span></span>

<span data-ttu-id="d8f50-255">La méthode `ReadFromTsv()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8f50-255">The `ReadFromTsv()` method executes the following tasks:</span></span>

* <span data-ttu-id="d8f50-256">Lit le fichier `tags.tsv` de données d’images.</span><span class="sxs-lookup"><span data-stu-id="d8f50-256">Reads the image data `tags.tsv` file.</span></span>
* <span data-ttu-id="d8f50-257">Ajoute le chemin de fichier au nom de fichier image.</span><span class="sxs-lookup"><span data-stu-id="d8f50-257">Adds the file path to the image file name.</span></span>
* <span data-ttu-id="d8f50-258">Charge les données du fichier dans un objet `ImageData` IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="d8f50-258">Loads the file data into an IEnumerable`ImageData` object.</span></span>

<span data-ttu-id="d8f50-259">Créez la méthode `ReadFromTsv()` juste après la méthode `PairAndDisplayResults()`, en utilisant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-259">Create the `ReadFromTsv()` method, just after the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static IEnumerable<ImageData> ReadFromTsv(string file, string folder)
{

}
```

<span data-ttu-id="d8f50-260">Le code suivant analyse le fichier `tags.tsv` afin d’ajouter le chemin de fichier au nom de fichier image pour la propriété `ImagePath` et de le charger ainsi que le `Label` dans un objet `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-260">The following code parses through the `tags.tsv` file to add the file path to the image file name for the `ImagePath` property and load it and the `Label` into an `ImageData` object.</span></span> <span data-ttu-id="d8f50-261">Ajoutez-le en première ligne de la méthode `ReadFromTsv()`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-261">Add it as the first line of the `ReadFromTsv()` method.</span></span>  <span data-ttu-id="d8f50-262">Le chemin de fichier complet est nécessaire pour afficher les résultats de prédiction.</span><span class="sxs-lookup"><span data-stu-id="d8f50-262">You need the fully qualified file path to display the prediction results.</span></span>

[!code-csharp[ReadFromTsv](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReadFromTsv)]
<span data-ttu-id="d8f50-263">Il existe trois principaux concepts dans ML.NET : les [données](../resources/glossary.md#data), les [transformateurs](../resources/glossary.md#transformer) et les [estimateurs](../resources/glossary.md#estimator).</span><span class="sxs-lookup"><span data-stu-id="d8f50-263">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

## <a name="reuse-and-tune-pre-trained-model"></a><span data-ttu-id="d8f50-264">Réutiliser et paramétrer le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="d8f50-264">Reuse and tune pre-trained model</span></span>

<span data-ttu-id="d8f50-265">Ajoutez l’appel suivant à la méthode `ReuseAndTuneInceptionModel()` comme prochaine ligne de code dans la méthode `Main()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-265">Add the following call to the `ReuseAndTuneInceptionModel()`method as the next line of code in the `Main()` method:</span></span>

[!code-csharp[CallReuseAndTuneInceptionModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReuseAndTuneInceptionModel)]

<span data-ttu-id="d8f50-266">La méthode `ReuseAndTuneInceptionModel()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8f50-266">The `ReuseAndTuneInceptionModel()` method executes the following tasks:</span></span>

* <span data-ttu-id="d8f50-267">Charge les données.</span><span class="sxs-lookup"><span data-stu-id="d8f50-267">Loads the data</span></span>
* <span data-ttu-id="d8f50-268">Extrait et transforme les données.</span><span class="sxs-lookup"><span data-stu-id="d8f50-268">Extracts and transforms the data.</span></span>
* <span data-ttu-id="d8f50-269">Évalue le modèle TensorFlow.</span><span class="sxs-lookup"><span data-stu-id="d8f50-269">Scores the TensorFlow model.</span></span>
* <span data-ttu-id="d8f50-270">Paramètre (réentraîne) le modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-270">Tunes (retrains) the model.</span></span>
* <span data-ttu-id="d8f50-271">Affiche les résultats du modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-271">Displays model results.</span></span>
* <span data-ttu-id="d8f50-272">Évalue le modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-272">Evaluates the model.</span></span>
* <span data-ttu-id="d8f50-273">Retourne le modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-273">Returns the model.</span></span>

<span data-ttu-id="d8f50-274">Créez la méthode `ReuseAndTuneInceptionModel()`, juste après le struct `InceptionSettings` et juste avant la méthode `DisplayResults()`, avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-274">Create the `ReuseAndTuneInceptionModel()` method, just after the `InceptionSettings` struct and just before the `DisplayResults()` method, using the following code:</span></span>

```csharp
public static ITransformer ReuseAndTuneInceptionModel(MLContext mlContext, string dataLocation, string imagesFolder, string inputModelLocation, string outputModelLocation)
{

}
```

### <a name="load-the-data"></a><span data-ttu-id="d8f50-275">Charger les données</span><span class="sxs-lookup"><span data-stu-id="d8f50-275">Load the data</span></span>

<span data-ttu-id="d8f50-276">Les données dans ML.NET sont représentées en tant que [classe IDataView](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="d8f50-276">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="d8f50-277">`IDataView` est un moyen flexible et efficace de décrire des données tabulaires (numériques et texte).</span><span class="sxs-lookup"><span data-stu-id="d8f50-277">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="d8f50-278">Les données peuvent être chargées à partir d’un fichier texte ou en temps réel (par exemple, fichiers journaux ou de base de données SQL) dans un objet `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-278">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="d8f50-279">Chargez les données avec le wrapper `MLContext.Data.LoadFromTextFile`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-279">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="d8f50-280">Ajoutez le code suivant comme première ligne de la méthode `ReuseAndTuneInceptionModel()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-280">Add the following code as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadData "Load the data")]

### <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="d8f50-281">Extraire des caractéristiques et transformer les données</span><span class="sxs-lookup"><span data-stu-id="d8f50-281">Extract Features and transform the data</span></span>

<span data-ttu-id="d8f50-282">Le prétraitement et le nettoyage des données constituent des tâches importantes qui se produisent avant qu’un jeu de données puisse être utilisé efficacement pour l’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="d8f50-282">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span>  <span data-ttu-id="d8f50-283">L’utilisation de données sans effectuer ces tâches de modélisation peut produire des résultats trompeurs.</span><span class="sxs-lookup"><span data-stu-id="d8f50-283">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="d8f50-284">Les algorithmes de Machine Learning prennent des données [caractérisées](../resources/glossary.md#feature) ; pour utiliser un réseau neuronal profond, il faut adapter les images au format qu’il attend.</span><span class="sxs-lookup"><span data-stu-id="d8f50-284">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, and when dealing with deep neural networks you must adapt the images to the format expected by the network.</span></span> <span data-ttu-id="d8f50-285">Ce format est un [vecteur numérique](../resources/glossary.md#numerical-feature-vector).</span><span class="sxs-lookup"><span data-stu-id="d8f50-285">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="d8f50-286">Après l’apprentissage et l’évaluation, passez à la prédiction avec les valeurs de la colonne **Label**.</span><span class="sxs-lookup"><span data-stu-id="d8f50-286">After training and evaluation, predict with the **Label** column values.</span></span> <span data-ttu-id="d8f50-287">Comme vous utilisez un modèle préentraîné, mappez les champs sur le nouveau modèle avec la méthode [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A).</span><span class="sxs-lookup"><span data-stu-id="d8f50-287">As you're using a pre-trained model, map fields to the new model with the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method.</span></span> <span data-ttu-id="d8f50-288">Elle transforme le `Label` en une colonne de type de clé numérique (`LabelTokey`) qu’elle ajoute aux colonnes du jeu de données :  Nommez cela `estimator`, car vous y ajouterez également le processus d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="d8f50-288">This method transforms the `Label` into a numeric key type (`LabelTokey`) column and add it as new dataset column:  Name this `estimator` as you'll also add the trainer to it.</span></span> <span data-ttu-id="d8f50-289">Ajoutez la ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="d8f50-289">Add the next line of code:</span></span>

[!code-csharp[MapValueToKey1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey1)]

<span data-ttu-id="d8f50-290">L’estimateur de traitement d’images utilise des extracteurs de caractéristiques de type [réseau neuronal profond](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) préentraînés.</span><span class="sxs-lookup"><span data-stu-id="d8f50-290">Your image processing estimator uses pre-trained [Deep Neural Network(DNN)](https://en.wikipedia.org/wiki/Deep_learning#Deep_neural_networks) featurizers for feature extraction.</span></span> <span data-ttu-id="d8f50-291">Il faut adapter les images au format attendu par des réseaux neuronaux profonds.</span><span class="sxs-lookup"><span data-stu-id="d8f50-291">When dealing with deep neural networks, you  adapt the images to the expected network format.</span></span> <span data-ttu-id="d8f50-292">C’est la raison pour laquelle on utilise plusieurs transformations d’images afin d’obtenir les données d’images au format nécessaire au modèle :</span><span class="sxs-lookup"><span data-stu-id="d8f50-292">This is the reason you use several image transforms to get the image data into the model's expected form:</span></span>

1. <span data-ttu-id="d8f50-293">La transformation `LoadImages` charge les images en mémoire au type bitmap.</span><span class="sxs-lookup"><span data-stu-id="d8f50-293">The `LoadImages`transform images are loaded in memory as a Bitmap type.</span></span>
2. <span data-ttu-id="d8f50-294">La transformation `ResizeImages` redimensionne les images, car le modèle préentraîné définit une largeur et une hauteur d’image d’entrée.</span><span class="sxs-lookup"><span data-stu-id="d8f50-294">The `ResizeImages` transform resizes the images as the pre-trained model has a defined input image width and height.</span></span>
3. <span data-ttu-id="d8f50-295">La transformation `ExtractPixels` extrait les pixels des images d’entrée et les convertit en un vecteur numérique.</span><span class="sxs-lookup"><span data-stu-id="d8f50-295">The `ExtractPixels` transform extracts the pixels from the input images and converts them into a numeric vector.</span></span>

<span data-ttu-id="d8f50-296">Ajoutez ces transformations d’images à la suite du code :</span><span class="sxs-lookup"><span data-stu-id="d8f50-296">Add these image transforms as the next lines of code:</span></span>

[!code-csharp[ImageTransforms](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ImageTransforms)]

<span data-ttu-id="d8f50-297">`LoadTensorFlowModel` est une méthode pratique qui permet de charger le modèle `TensorFlow` une seule fois, puis de créer `TensorFlowEstimator` à l’aide de `ScoreTensorFlowModel`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-297">The `LoadTensorFlowModel` is a convenience method that allows the `TensorFlow` model to be loaded once and then creates the `TensorFlowEstimator` using `ScoreTensorFlowModel`.</span></span> <span data-ttu-id="d8f50-298">`ScoreTensorFlowModel` extrait des sorties spécifiées (les caractéristiques des images de `Inception model` `softmax2_pre_activation`) et évalue un jeu de données avec le modèle `TensorFlow` préentraîné.</span><span class="sxs-lookup"><span data-stu-id="d8f50-298">The `ScoreTensorFlowModel` extracts specified outputs (the `Inception model`'s image features `softmax2_pre_activation`), and scores a dataset using the pre-trained `TensorFlow` model.</span></span>

<span data-ttu-id="d8f50-299">`softmax2_pre_activation` aide à le modèle à déterminer à quelle classe appartiennent les images.</span><span class="sxs-lookup"><span data-stu-id="d8f50-299">`softmax2_pre_activation` assists the model with determining which class the images belongs to.</span></span> <span data-ttu-id="d8f50-300">`softmax2_pre_activation` retourne la probabilité de chacune des catégories pour une image donnée ; la somme de toutes ces probabilités doit être égale à 1.</span><span class="sxs-lookup"><span data-stu-id="d8f50-300">`softmax2_pre_activation` returns a probability for each of the categories for an image, and all of those probabilities must add up to 1.</span></span> <span data-ttu-id="d8f50-301">Il suppose qu’une image appartient à une seule catégorie, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-301">It assumes that an image will belong to only one category, as shown in the following example:</span></span>

| <span data-ttu-id="d8f50-302">Classe</span><span class="sxs-lookup"><span data-stu-id="d8f50-302">Class</span></span>         | <span data-ttu-id="d8f50-303">Probabilité</span><span class="sxs-lookup"><span data-stu-id="d8f50-303">Probability</span></span>   |
| ------------- | ------------- |
| `Food`        |  <span data-ttu-id="d8f50-304">0,001</span><span class="sxs-lookup"><span data-stu-id="d8f50-304">0.001</span></span>        |
| `Toy`         |  <span data-ttu-id="d8f50-305">0,95</span><span class="sxs-lookup"><span data-stu-id="d8f50-305">0.95</span></span>         |
| `Appliance`   |  <span data-ttu-id="d8f50-306">0,06</span><span class="sxs-lookup"><span data-stu-id="d8f50-306">0.06</span></span>         |

<span data-ttu-id="d8f50-307">Ajoutez `TensorFlowTransform` à `estimator` avec la ligne de code suivante :</span><span class="sxs-lookup"><span data-stu-id="d8f50-307">Append the `TensorFlowTransform` to the `estimator` with the following line of code:</span></span>

[!code-csharp[ScoreTensorFlowModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ScoreTensorFlowModel)]

### <a name="choose-a-training-algorithm"></a><span data-ttu-id="d8f50-308">Choisir un algorithme d’apprentissage</span><span class="sxs-lookup"><span data-stu-id="d8f50-308">Choose a training algorithm</span></span>

<span data-ttu-id="d8f50-309">Pour ajouter l’algorithme d’apprentissage, appelez la méthode de wrapper `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-309">To add the training algorithm, call the `mlContext.MulticlassClassification.Trainers.LbfgsMaximumEntropy()` wrapper method.</span></span>  <span data-ttu-id="d8f50-310">[LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) est ajouté à `estimator` et accepte les caractéristiques d’images Inception (`softmax2_pre_activation`) et les paramètres d’entrée `Label` pour apprendre à partir des données d’historique.</span><span class="sxs-lookup"><span data-stu-id="d8f50-310">The [LbfgsMaximumEntropy](xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer) is appended to the `estimator` and accepts the Inception image features (`softmax2_pre_activation`) and the `Label` input parameters to learn from the historic data.</span></span>  <span data-ttu-id="d8f50-311">Ajoutez le processus d’apprentissage avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-311">Add the trainer with the following code:</span></span>

[!code-csharp[AddTrainer](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#AddTrainer)]

<span data-ttu-id="d8f50-312">Il faut également mapper `predictedlabel` sur `predictedlabelvalue` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-312">You also need to map the `predictedlabel` to the `predictedlabelvalue`:</span></span>

[!code-csharp[MapValueToKey2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#MapValueToKey2)]

<span data-ttu-id="d8f50-313">La méthode `Fit()` entraîne votre modèle en transformant le jeu de données et en appliquant l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="d8f50-313">The `Fit()` method trains your model by transforming the dataset and applying the training.</span></span> <span data-ttu-id="d8f50-314">Ajustez le modèle au jeu de données d’entraînement et retournez le modèle entraîné en ajoutant la ligne de code suivante dans la méthode `ReuseAndTuneInceptionModel()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-314">Fit the model to the training dataset and return the trained model by adding the following as the next line of code in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TrainModel)]

<span data-ttu-id="d8f50-315">La méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) établit des prédictions pour plusieurs lignes d’entrée fournies d’un jeu de données de test.</span><span class="sxs-lookup"><span data-stu-id="d8f50-315">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>  <span data-ttu-id="d8f50-316">Transformez les données `Training` en ajoutant le code suivant à `ReuseAndTuneInceptionModel()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-316">Transform the `Training` data by adding the following code to `ReuseAndTuneInceptionModel()`:</span></span>

[!code-csharp[TransformData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#TransformData)]

<span data-ttu-id="d8f50-317">Convertissez vos données d’images et `DataViews` de prédiction en `IEnumerables` fortement typés à associer pour faciliter l’affichage.</span><span class="sxs-lookup"><span data-stu-id="d8f50-317">Convert your image data and prediction `DataViews` into strongly-typed `IEnumerables` to pair for easier display.</span></span> <span data-ttu-id="d8f50-318">Utilisez pour cela la méthode `MLContext.CreateEnumerable()` avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-318">Use the `MLContext.CreateEnumerable()` method to do that, using the following code:</span></span>

[!code-csharp[EnumerateDataViews](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#EnumerateDataViews)]

<span data-ttu-id="d8f50-319">Appelez la méthode `DisplayResults()` pour afficher vos données et prédictions à la fin de la méthode `ReuseAndTuneInceptionModel()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-319">Call the `DisplayResults()` method to display your data and predictions as the next line in the `ReuseAndTuneInceptionModel()` method:</span></span>

[!code-csharp[CallDisplayResults1](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults1)]

<span data-ttu-id="d8f50-320">Une fois la prédiction définie, la méthode [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) :</span><span class="sxs-lookup"><span data-stu-id="d8f50-320">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method:</span></span>

* <span data-ttu-id="d8f50-321">Évalue le modèle (compare les valeurs prédites avec le jeu de données réel `Labels`).</span><span class="sxs-lookup"><span data-stu-id="d8f50-321">Assesses the model (compares the predicted values with the actual dataset `Labels`).</span></span>

* <span data-ttu-id="d8f50-322">Retourne les indicateurs de performances du modèle.</span><span class="sxs-lookup"><span data-stu-id="d8f50-322">Returns the model performance metrics.</span></span>

<span data-ttu-id="d8f50-323">Ajoutez comme nouvelle ligne le code suivant à la méthode `ReuseAndTuneInceptionModel()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-323">Add the following code to the `ReuseAndTuneInceptionModel()` method as the next line:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Evaluate)]

<span data-ttu-id="d8f50-324">Les indicateurs suivants sont évalués pour la classification d’images :</span><span class="sxs-lookup"><span data-stu-id="d8f50-324">The following metrics are evaluated for image classification:</span></span>

* <span data-ttu-id="d8f50-325">`Log-loss` (voir [Perte logarithmique](../resources/glossary.md#log-loss)).</span><span class="sxs-lookup"><span data-stu-id="d8f50-325">`Log-loss` - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="d8f50-326">Vous voulez que la perte logarithmique soit aussi proche de zéro que possible.</span><span class="sxs-lookup"><span data-stu-id="d8f50-326">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="d8f50-327">`Per class Log-loss`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-327">`Per class Log-loss`.</span></span> <span data-ttu-id="d8f50-328">La perte logarithmique doit être aussi proche de zéro que possible.</span><span class="sxs-lookup"><span data-stu-id="d8f50-328">You want per class Log-loss to be as close to zero as possible.</span></span>

<span data-ttu-id="d8f50-329">Utilisez le code suivant pour afficher les métriques, partager les résultats et agir dessus :</span><span class="sxs-lookup"><span data-stu-id="d8f50-329">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayMetrics)]

 <span data-ttu-id="d8f50-330">Ajoutez le code suivant pour retourner le modèle entraîné à la ligne suivante :</span><span class="sxs-lookup"><span data-stu-id="d8f50-330">Add the following code to return the trained model as the next line:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#ReturnModel)]

## <a name="classify-images-with-a-loaded-model"></a><span data-ttu-id="d8f50-331">Classer des images avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="d8f50-331">Classify images with a loaded model</span></span>

<span data-ttu-id="d8f50-332">Ajoutez l’appel suivant à la méthode `ClassifyImages()` à la fin de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-332">Add the following call to the `ClassifyImages()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifyImages](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifyImages)]

<span data-ttu-id="d8f50-333">La méthode `ClassifyImages()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8f50-333">The `ClassifyImages()` method executes the following tasks:</span></span>

* <span data-ttu-id="d8f50-334">Lit le fichier .tsv en `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-334">Reads .TSV file into `IEnumerable`.</span></span>
* <span data-ttu-id="d8f50-335">Prédit les classifications d’images en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="d8f50-335">Predicts image classifications based on test data.</span></span>

<span data-ttu-id="d8f50-336">Créez la méthode `ClassifyImages()`, juste après la méthode `ReuseAndTuneInceptionModel()` et juste avant la méthode `PairAndDisplayResults()`, avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-336">Create the `ClassifyImages()` method, just after the `ReuseAndTuneInceptionModel()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifyImages(MLContext mlContext, string dataLocation, string imagesFolder, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="d8f50-337">Appelez d’abord la méthode `ReadFromTsv()` pour créer une classe `IEnumerable<ImageData>` contenant le chemin complet de chaque `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-337">First, call the `ReadFromTsv()` method to create an `IEnumerable<ImageData>` class that contains the fully qualified path for each `ImagePath`.</span></span> <span data-ttu-id="d8f50-338">Il faut que ce chemin de fichier soit associé à vos données et résultats de prédiction.</span><span class="sxs-lookup"><span data-stu-id="d8f50-338">You need that file path to pair your data and prediction results.</span></span> <span data-ttu-id="d8f50-339">Vous devez également convertir la classe `IEnumerable<ImageData>` en une `IDataView` servant aux prédictions.</span><span class="sxs-lookup"><span data-stu-id="d8f50-339">You also need to convert the `IEnumerable<ImageData>` class to an `IDataView` that you will use to predict.</span></span> <span data-ttu-id="d8f50-340">Ajoutez le code suivant à la fin de la méthode `ClassifyImages()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-340">Add the following code as the next two lines in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallReadFromTSV](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallReadFromTSV)]

<span data-ttu-id="d8f50-341">Comme vous l’avez fait avec les données d’images d’entraînement, prédisez la catégorie des données d’images de test en utilisant la méthode [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) du modèle passé.</span><span class="sxs-lookup"><span data-stu-id="d8f50-341">As you did previously with the training image data, predict the category of the test image data using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the model passed in.</span></span> <span data-ttu-id="d8f50-342">Ajoutez le code suivant à la méthode `ClassifyImages()` pour les prédictions et la conversion de la `IDataView` `predictions` en `IEnumerable` à des fins d’association et d’affichage :</span><span class="sxs-lookup"><span data-stu-id="d8f50-342">Add the following code to the `ClassifyImages()` method for the predictions and to convert the `predictions` `IDataView` into an `IEnumerable` for pairing and display:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#Predict)]

<span data-ttu-id="d8f50-343">Pour associer et afficher vos données d’images de test et vos prédictions, ajoutez le code suivant, qui appelle la méthode `DisplayResults()` déjà créée, à la fin de la méthode `ClassifyImages()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-343">To pair and display your test image data and predictions, add the following code to call the `DisplayResults()` method previously created as the next line in the `ClassifyImages()` method:</span></span>

[!code-csharp[CallDisplayResults2](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallDisplayResults2)]

## <a name="classify-a-single-image-with-a-loaded-model"></a><span data-ttu-id="d8f50-344">Classer une seule image avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="d8f50-344">Classify a single image with a loaded model</span></span>

<span data-ttu-id="d8f50-345">Ajoutez l’appel suivant à la méthode `ClassifySingleImage()` à la fin de la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-345">Add the following call to the `ClassifySingleImage()` method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallClassifySingleImage](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#CallClassifySingleImage)]

<span data-ttu-id="d8f50-346">La méthode `ClassifySingleImage()` exécute les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d8f50-346">The `ClassifySingleImage()` method executes the following tasks:</span></span>

* <span data-ttu-id="d8f50-347">Charge une instance `ImageData`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-347">Loads an `ImageData` instance.</span></span>
* <span data-ttu-id="d8f50-348">Prédit la classification d’image en fonction des données de test.</span><span class="sxs-lookup"><span data-stu-id="d8f50-348">Predicts image classification based on test data.</span></span>

<span data-ttu-id="d8f50-349">Créez la méthode `ClassifySingleImage()`, juste après la méthode `ClassifyImages()` et juste avant la méthode `PairAndDisplayResults()`, avec le code suivant :</span><span class="sxs-lookup"><span data-stu-id="d8f50-349">Create the `ClassifySingleImage()` method, just after the `ClassifyImages()` method and just before the `PairAndDisplayResults()` method, using the following code:</span></span>

```csharp
public static void ClassifySingleImage(MLContext mlContext, string imagePath, string outputModelLocation, ITransformer model)
{

}
```

<span data-ttu-id="d8f50-350">Créez d’abord une classe `ImageData` contenant le chemin complet et le nom de fichier d’image de l’unique `ImagePath`.</span><span class="sxs-lookup"><span data-stu-id="d8f50-350">First, create an `ImageData` class that contains the fully qualified path and image file name for the single `ImagePath`.</span></span> <span data-ttu-id="d8f50-351">Ajoutez le code suivant à la fin de la méthode `ClassifySingleImage()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-351">Add the following code as the next  lines in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[LoadImageData](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#LoadImageData)]

<span data-ttu-id="d8f50-352">La [classe PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) est une API utile qui effectue une prévision sur une seule instance de données.</span><span class="sxs-lookup"><span data-stu-id="d8f50-352">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API that performs a prediction on a single instance of data.</span></span> <span data-ttu-id="d8f50-353">La fonction [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) établit une prédiction sur une seule colonne de données.</span><span class="sxs-lookup"><span data-stu-id="d8f50-353">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span> <span data-ttu-id="d8f50-354">Passez `imageData` à `PredictionEngine` pour prédire la catégorie d’image en ajoutant le code suivant à `ClassifySingleImage()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-354">Pass `imageData` to the `PredictionEngine` to predict the image category by adding the following code to `ClassifySingleImage()`:</span></span>

[!code-csharp[PredictSingle](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#PredictSingle)]

<span data-ttu-id="d8f50-355">Affichez le résultat de la prédiction à la fin de la méthode `ClassifySingleImage()` :</span><span class="sxs-lookup"><span data-stu-id="d8f50-355">Display the prediction result as the next line of code in the `ClassifySingleImage()` method:</span></span>

[!code-csharp[DisplayPrediction](../../../samples/machine-learning/tutorials/TransferLearningTF/Program.cs#DisplayPrediction)]

## <a name="results"></a><span data-ttu-id="d8f50-356">Résultats</span><span class="sxs-lookup"><span data-stu-id="d8f50-356">Results</span></span>

<span data-ttu-id="d8f50-357">Après avoir suivi les étapes précédentes, exécutez votre application console (Ctrl + F5).</span><span class="sxs-lookup"><span data-stu-id="d8f50-357">After following the previous steps, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="d8f50-358">Vous devriez obtenir les résultats suivants.</span><span class="sxs-lookup"><span data-stu-id="d8f50-358">Your results should be similar to the following output.</span></span>  <span data-ttu-id="d8f50-359">Des messages d’avertissement ou de traitement peuvent s’afficher, mais nous les avons supprimés dans les résultats suivants pour plus de clarté.</span><span class="sxs-lookup"><span data-stu-id="d8f50-359">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training classification model ===============
Image: broccoli.jpg predicted as: food with score: 0.976743
Image: pizza.jpg predicted as: food with score: 0.9751652
Image: pizza2.jpg predicted as: food with score: 0.9660203
Image: teddy2.jpg predicted as: toy with score: 0.9748783
Image: teddy3.jpg predicted as: toy with score: 0.9829691
Image: teddy4.jpg predicted as: toy with score: 0.9868168
Image: toaster.jpg predicted as: appliance with score: 0.9769174
Image: toaster2.png predicted as: appliance with score: 0.9800823
=============== Classification metrics ===============
LogLoss is: 0.0228266745633507
PerClassLogLoss is: 0.0277501705149937 , 0.0186303530571291 , 0.0217359128952187
=============== Making classifications ===============
Image: broccoli.png predicted as: food with score: 0.905548
Image: pizza3.jpg predicted as: food with score: 0.9709008
Image: teddy6.jpg predicted as: toy with score: 0.9750155
=============== Making single image classification ===============
Image: toaster3.jpg predicted as: appliance with score: 0.9625379

C:\Program Files\dotnet\dotnet.exe (process 4304) exited with code 0.
Press any key to close this window . . .
```

<span data-ttu-id="d8f50-360">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="d8f50-360">Congratulations!</span></span> <span data-ttu-id="d8f50-361">Vous avez créé un modèle Machine Learning de classification d’images en réutilisant un modèle `TensorFlow` préentraîné dans ML.NET.</span><span class="sxs-lookup"><span data-stu-id="d8f50-361">You've now successfully built a machine learning model for image classification by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="d8f50-362">Vous trouverez le code source de ce tutoriel dans le référentiel [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF).</span><span class="sxs-lookup"><span data-stu-id="d8f50-362">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TransferLearningTF) repository.</span></span>

<span data-ttu-id="d8f50-363">Dans ce didacticiel, vous avez appris à :</span><span class="sxs-lookup"><span data-stu-id="d8f50-363">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d8f50-364">Comprendre le problème</span><span class="sxs-lookup"><span data-stu-id="d8f50-364">Understand the problem</span></span>
> * <span data-ttu-id="d8f50-365">Réutiliser et paramétrer le modèle préentraîné</span><span class="sxs-lookup"><span data-stu-id="d8f50-365">Reuse and tune the pre-trained model</span></span>
> * <span data-ttu-id="d8f50-366">Classer des images avec un modèle chargé</span><span class="sxs-lookup"><span data-stu-id="d8f50-366">Classify images with a loaded model</span></span>

<span data-ttu-id="d8f50-367">Consultez le référentiel GitHub d’exemples Machine Learning pour voir un exemple développé de classification d’images.</span><span class="sxs-lookup"><span data-stu-id="d8f50-367">Check out the Machine Learning samples GitHub repository to explore an expanded image classification sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d8f50-368">Référentiel GitHub dotnet/machinelearning-samples</span><span class="sxs-lookup"><span data-stu-id="d8f50-368">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/)
