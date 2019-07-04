---
title: Guide pratique pour installer Model Builder
description: Découvrir comment installer l’outil Model Builder ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: 54ab595c56f816517180aab48022c7df207fe84d
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410567"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="4ab63-103">Guide pratique pour installer Model Builder ML.NET</span><span class="sxs-lookup"><span data-stu-id="4ab63-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="4ab63-104">Découvrez comment installer Model Builder ML.NET pour ajouter le machine learning à vos applications .NET.</span><span class="sxs-lookup"><span data-stu-id="4ab63-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="4ab63-105">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="4ab63-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="4ab63-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4ab63-106">Pre-requisites</span></span>

- <span data-ttu-id="4ab63-107">Visual Studio 2017 15.9.12 ou ultérieur / Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4ab63-107">Visual Studio 2017 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="4ab63-108">SDK .NET Core 2.1 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="4ab63-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="4ab63-109">Limitations</span><span class="sxs-lookup"><span data-stu-id="4ab63-109">Limitations</span></span>

- <span data-ttu-id="4ab63-110">L’extension Model Builder ML.NET fonctionne actuellement seulement avec Visual Studio sur Windows.</span><span class="sxs-lookup"><span data-stu-id="4ab63-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="4ab63-111">La limite du jeu de données d’entraînement est de 1 Go</span><span class="sxs-lookup"><span data-stu-id="4ab63-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="4ab63-112">SQL Server a une limite de 100 000 lignes pour l’entraînement</span><span class="sxs-lookup"><span data-stu-id="4ab63-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="4ab63-113">Microsoft SQL Server Data Tools pour Visual Studio 2017 n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="4ab63-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="4ab63-114">Installez</span><span class="sxs-lookup"><span data-stu-id="4ab63-114">Install</span></span>

<span data-ttu-id="4ab63-115">Model Builder ML.NET peut être installé via Visual Studio Marketplace ou depuis Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ab63-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span> 

### <a name="visual-studio-marketplace"></a><span data-ttu-id="4ab63-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="4ab63-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="4ab63-117">Télécharger depuis [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="4ab63-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="4ab63-118">Suivre les invites pour installer sur les différentes versions de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ab63-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="4ab63-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4ab63-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="4ab63-120">Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.</span><span class="sxs-lookup"><span data-stu-id="4ab63-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="4ab63-121">Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.</span><span class="sxs-lookup"><span data-stu-id="4ab63-121">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="4ab63-122">Dans la barre de recherche, recherchez *Model Builder ML.NET* puis, dans les résultats, sélectionnez « Model Builder ML.NET (Préversion) »</span><span class="sxs-lookup"><span data-stu-id="4ab63-122">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="4ab63-123">Suivez les invites pour effectuer l’installation</span><span class="sxs-lookup"><span data-stu-id="4ab63-123">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="4ab63-124">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4ab63-124">Visual Studio 2019</span></span>

1. <span data-ttu-id="4ab63-125">Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.</span><span class="sxs-lookup"><span data-stu-id="4ab63-125">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="4ab63-126">Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.</span><span class="sxs-lookup"><span data-stu-id="4ab63-126">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="4ab63-127">Tapez *Model Builder ML.NET* dans la barre de recherche, puis sélectionnez « Model Builder ML.NET (Préversion) »</span><span class="sxs-lookup"><span data-stu-id="4ab63-127">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>
1. <span data-ttu-id="4ab63-128">Suivez les invites pour effectuer l’installation</span><span class="sxs-lookup"><span data-stu-id="4ab63-128">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="4ab63-129">Désinstaller</span><span class="sxs-lookup"><span data-stu-id="4ab63-129">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="4ab63-130">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4ab63-130">Visual Studio 2017</span></span>

1. <span data-ttu-id="4ab63-131">Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.</span><span class="sxs-lookup"><span data-stu-id="4ab63-131">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>
1. <span data-ttu-id="4ab63-132">Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*</span><span class="sxs-lookup"><span data-stu-id="4ab63-132">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="4ab63-133">Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="4ab63-133">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="4ab63-134">Suivez les invites pour effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="4ab63-134">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="4ab63-135">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="4ab63-135">Visual Studio 2019</span></span>

1. <span data-ttu-id="4ab63-136">Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.</span><span class="sxs-lookup"><span data-stu-id="4ab63-136">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>
1. <span data-ttu-id="4ab63-137">Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*</span><span class="sxs-lookup"><span data-stu-id="4ab63-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="4ab63-138">Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="4ab63-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>
1. <span data-ttu-id="4ab63-139">Suivez les invites pour effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="4ab63-139">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="4ab63-140">Mettre à niveau</span><span class="sxs-lookup"><span data-stu-id="4ab63-140">Upgrade</span></span>

<span data-ttu-id="4ab63-141">Le processus de mise à niveau est similaire au processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="4ab63-141">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="4ab63-142">Téléchargez la dernière version à partir de Visual Studio Marketplace ou utilisez le Gestionnaire d’extensions dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ab63-142">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
