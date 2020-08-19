---
title: Comment installer la prise en charge des GPU dans le générateur de modèles
description: Découvrez comment installer la prise en charge des GPU dans le générateur de modèles
ms.date: 08/18/2020
author: luisquintanilla
ms.author: luquinta
ms.topic: how-to
ms.openlocfilehash: ce629efa4c12a69f87196de35ebfe4331dc0800f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608567"
---
# <a name="how-to-install-gpu-support-in-model-builder"></a><span data-ttu-id="6dd7d-103">Comment installer la prise en charge des GPU dans le générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="6dd7d-103">How to install GPU support in Model Builder</span></span>

<span data-ttu-id="6dd7d-104">Découvrez comment installer les pilotes GPU pour utiliser votre GPU avec le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-104">Learn how to install the GPU drivers to use your GPU with Model Builder.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6dd7d-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="6dd7d-105">Prerequisites</span></span>

- <span data-ttu-id="6dd7d-106">Extension Visual Studio du générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-106">Model Builder Visual Studio extension.</span></span> <span data-ttu-id="6dd7d-107">L’extension est intégrée à Visual Studio à partir de la version 16.6.1.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-107">The extension is built into Visual Studio as of version 16.6.1.</span></span>
- <span data-ttu-id="6dd7d-108">[Extension de prise en charge du GPU Visual Studio](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU)pour le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-108">[Model Builder Visual Studio GPU support extension](https://marketplace.visualstudio.com/items?itemName=MLNET.ModelBuilderGPU).</span></span>
- <span data-ttu-id="6dd7d-109">Au moins un GPU compatible CUDA.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-109">At least one CUDA compatible GPU.</span></span> <span data-ttu-id="6dd7d-110">Pour obtenir la liste des GPU compatibles, consultez le [Guide NVIDIA](https://developer.nvidia.com/cuda-gpus).</span><span class="sxs-lookup"><span data-stu-id="6dd7d-110">For a list of compatible GPUs, see [NVIDIA's guide](https://developer.nvidia.com/cuda-gpus).</span></span>
- <span data-ttu-id="6dd7d-111">Compte de développeur NVIDIA.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-111">NVIDIA developer account.</span></span> <span data-ttu-id="6dd7d-112">Si vous n’en avez pas, [créez un compte gratuit](https://developer.nvidia.com/developer-program).</span><span class="sxs-lookup"><span data-stu-id="6dd7d-112">If you don't have one, [create a free account](https://developer.nvidia.com/developer-program).</span></span>

## <a name="install-dependencies"></a><span data-ttu-id="6dd7d-113">Installer des dépendances</span><span class="sxs-lookup"><span data-stu-id="6dd7d-113">Install dependencies</span></span>

1. <span data-ttu-id="6dd7d-114">Installez [CUDA v 10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span><span class="sxs-lookup"><span data-stu-id="6dd7d-114">Install [CUDA v10.0](https://developer.nvidia.com/cuda-10.0-download-archive).</span></span> <span data-ttu-id="6dd7d-115">Veillez à installer CUDA v 10.0, et non une autre version plus récente.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-115">Make sure you install CUDA v10.0, not any other newer version.</span></span> <span data-ttu-id="6dd7d-116">Plusieurs versions de CUDA ne peuvent pas être installées.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-116">You cannot have multiple versions of CUDA installed.</span></span>
1. <span data-ttu-id="6dd7d-117">Installez [cuDNN v 7.6.4 pour CUDA 10,0](https://developer.nvidia.com/rdp/cudnn-download).</span><span class="sxs-lookup"><span data-stu-id="6dd7d-117">Install [cuDNN v7.6.4 for CUDA 10.0](https://developer.nvidia.com/rdp/cudnn-download).</span></span> <span data-ttu-id="6dd7d-118">Plusieurs versions de cuDNN ne peuvent pas être installées.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-118">You cannot have multiple versions of cuDNN installed.</span></span> <span data-ttu-id="6dd7d-119">Après avoir téléchargé le fichier zip cuDNN v 7.6.4 et l’avoir décompressé, copiez-le `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` dans `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin` .</span><span class="sxs-lookup"><span data-stu-id="6dd7d-119">After downloading cuDNN v7.6.4 zip file and unpacking it, copy `<CUDNN_zip_files_path>\cuda\bin\cudnn64_7.dll` to `<YOUR_DRIVE>\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.0\bin`.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="6dd7d-120">Dépannage</span><span class="sxs-lookup"><span data-stu-id="6dd7d-120">Troubleshooting</span></span>

<span data-ttu-id="6dd7d-121">**Comment faire savez-vous du GPU que je possède ?**</span><span class="sxs-lookup"><span data-stu-id="6dd7d-121">**How do I know what GPU I have?**</span></span>

<span data-ttu-id="6dd7d-122">Suivez les instructions fournies :</span><span class="sxs-lookup"><span data-stu-id="6dd7d-122">Follow instructions provided:</span></span>

1. <span data-ttu-id="6dd7d-123">Cliquer avec le bouton droit sur le Bureau</span><span class="sxs-lookup"><span data-stu-id="6dd7d-123">Right-click on desktop</span></span>
1. <span data-ttu-id="6dd7d-124">Si vous voyez « panneau de configuration NVIDIA » ou « affichage NVIDIA » dans la fenêtre contextuelle, vous disposez d’un GPU NVIDIA</span><span class="sxs-lookup"><span data-stu-id="6dd7d-124">If you see "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window, you have an NVIDIA GPU</span></span>
1. <span data-ttu-id="6dd7d-125">Cliquez sur le « panneau de configuration NVIDIA » ou sur « Affichage NVIDIA » dans la fenêtre contextuelle.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-125">Click on "NVIDIA Control Panel" or "NVIDIA Display" in the pop-up window</span></span>
1. <span data-ttu-id="6dd7d-126">Regarder « informations sur les cartes graphiques »</span><span class="sxs-lookup"><span data-stu-id="6dd7d-126">Look at "Graphics Card Information"</span></span>
1. <span data-ttu-id="6dd7d-127">Vous verrez le nom de votre GPU NVIDIA</span><span class="sxs-lookup"><span data-stu-id="6dd7d-127">You will see the name of your NVIDIA GPU</span></span>

<span data-ttu-id="6dd7d-128">**Je ne vois pas le panneau de configuration NVIDIA (ou il ne parvient pas à s’ouvrir), mais je sais que j’ai un GPU NVIDIA.**</span><span class="sxs-lookup"><span data-stu-id="6dd7d-128">**I don't see NVIDIA Control Panel (or it fails to open) but I know I have an NVIDIA GPU.**</span></span>

1. <span data-ttu-id="6dd7d-129">Ouvrez le Gestionnaire de périphériques.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-129">Open Device Manager</span></span>
1. <span data-ttu-id="6dd7d-130">Examiner les adaptateurs d’affichage</span><span class="sxs-lookup"><span data-stu-id="6dd7d-130">Look at Display adapters</span></span>
1. <span data-ttu-id="6dd7d-131">Installez le [pilote](https://www.nvidia.com/drivers) approprié pour votre GPU.</span><span class="sxs-lookup"><span data-stu-id="6dd7d-131">Install appropriate [driver](https://www.nvidia.com/drivers) for your GPU.</span></span>
