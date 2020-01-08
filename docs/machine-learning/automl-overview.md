---
title: Machine learning automatisé avec ML.NET
description: Vue d’ensemble de la sélection et de l’entraînement automatiques d’un modèle
author: natke
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc
ms.author: nakersha
ms.openlocfilehash: 251ca50f062f415ac4dfeda243eb746e9744b6f4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345186"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="57f66-103">Machine learning automatisé avec ML.NET</span><span class="sxs-lookup"><span data-stu-id="57f66-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="57f66-104">Le machine learning automatisé est une fonctionnalité de ML.NET qui sélectionne et entraîne un modèle automatiquement.</span><span class="sxs-lookup"><span data-stu-id="57f66-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="57f66-105">Vous spécifiez la tâche de machine learning et fournissez un jeu de données, après quoi le machine learning automatisé choisit pour vous le modèle présentant les meilleures métriques.</span><span class="sxs-lookup"><span data-stu-id="57f66-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="57f66-106">Il génère :</span><span class="sxs-lookup"><span data-stu-id="57f66-106">It outputs:</span></span>

- <span data-ttu-id="57f66-107">un fichier de modèle qui peut être chargé dans votre application de prédiction</span><span class="sxs-lookup"><span data-stu-id="57f66-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="57f66-108">le code d’application nécessaire pour effectuer des prédictions</span><span class="sxs-lookup"><span data-stu-id="57f66-108">application code to make predictions</span></span>
- <span data-ttu-id="57f66-109">le code source utilisé pour la sélection des caractéristiques et l’entraînement du modèle (pour comprendre le modèle)</span><span class="sxs-lookup"><span data-stu-id="57f66-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="57f66-110">Cette fonctionnalité étant en préversion, elle est susceptible d’être modifiée.</span><span class="sxs-lookup"><span data-stu-id="57f66-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="57f66-111">Le ML automatisé est actuellement disponible uniquement pour les [tâches](resources/tasks.md) de machine learning de classification binaire, de classification multiclasse et de régression.</span><span class="sxs-lookup"><span data-stu-id="57f66-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="57f66-112">Les autres tâches de machine learning seront prises en charge dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="57f66-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="57f66-113">Il y a trois manières d’utiliser le ML automatisé :</span><span class="sxs-lookup"><span data-stu-id="57f66-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="57f66-114">Avec une interface graphique utilisateur, avec le [Générateur de modèles ML.NET](automate-training-with-model-builder.md)</span><span class="sxs-lookup"><span data-stu-id="57f66-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="57f66-115">À partir de la ligne de commande, avec l’interface [CLI ML.NET](automate-training-with-cli.md)</span><span class="sxs-lookup"><span data-stu-id="57f66-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="57f66-116">Par le biais d’une application, avec l’[API de ML automatisé](how-to-guides/how-to-use-the-automl-api.md)</span><span class="sxs-lookup"><span data-stu-id="57f66-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
