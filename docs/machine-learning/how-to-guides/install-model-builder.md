---
title: Guide pratique pour installer Model Builder
description: Découvrir comment installer l’outil Model Builder ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: b87f712ad7a8b2229c1d42db4bad1fe511475ac7
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552940"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="16eb4-103">Guide pratique pour installer Model Builder ML.NET</span><span class="sxs-lookup"><span data-stu-id="16eb4-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="16eb4-104">Découvrez comment installer Model Builder ML.NET pour ajouter le machine learning à vos applications .NET.</span><span class="sxs-lookup"><span data-stu-id="16eb4-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="16eb4-105">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="16eb4-105">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="16eb4-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="16eb4-106">Prerequisites</span></span>

- <span data-ttu-id="16eb4-107">Visual Studio 2017 version 15.9.12 ou ultérieure/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="16eb4-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="16eb4-108">.NET Core 2,1 SDK ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="16eb4-108">.NET Core 2.1 SDK or later.</span></span>

> [!NOTE]
> <span data-ttu-id="16eb4-109">Le kit de développement logiciel (SDK) .NET Core 3,0 n’est pas pris en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="16eb4-109">.NET Core 3.0 SDK is not currently supported.</span></span>

## <a name="limitations"></a><span data-ttu-id="16eb4-110">Limitations</span><span class="sxs-lookup"><span data-stu-id="16eb4-110">Limitations</span></span>

- <span data-ttu-id="16eb4-111">L’extension Model Builder ML.NET fonctionne actuellement seulement avec Visual Studio sur Windows.</span><span class="sxs-lookup"><span data-stu-id="16eb4-111">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="16eb4-112">La limite du jeu de données d’entraînement est de 1 Go</span><span class="sxs-lookup"><span data-stu-id="16eb4-112">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="16eb4-113">SQL Server a une limite de 100 000 lignes pour l’entraînement</span><span class="sxs-lookup"><span data-stu-id="16eb4-113">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="16eb4-114">Microsoft SQL Server Data Tools pour Visual Studio 2017 n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="16eb4-114">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="16eb4-115">Installez .</span><span class="sxs-lookup"><span data-stu-id="16eb4-115">Install</span></span>

<span data-ttu-id="16eb4-116">Model Builder ML.NET peut être installé via Visual Studio Marketplace ou depuis Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16eb4-116">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="16eb4-117">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="16eb4-117">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="16eb4-118">Télécharger depuis [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="16eb4-118">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="16eb4-119">Suivre les invites pour installer sur les différentes versions de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="16eb4-119">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="16eb4-120">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="16eb4-120">Visual Studio 2017</span></span>

1. <span data-ttu-id="16eb4-121">Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.</span><span class="sxs-lookup"><span data-stu-id="16eb4-121">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Boîte de dialogue VS2017 ouvrir le gestionnaire d’extensions](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="16eb4-123">Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.</span><span class="sxs-lookup"><span data-stu-id="16eb4-123">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="16eb4-124">Dans la barre de recherche, recherchez *Model Builder ML.NET* puis, dans les résultats, sélectionnez « Model Builder ML.NET (Préversion) »</span><span class="sxs-lookup"><span data-stu-id="16eb4-124">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 Rechercher et installer l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="16eb4-126">Suivez les invites pour effectuer l’installation</span><span class="sxs-lookup"><span data-stu-id="16eb4-126">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="16eb4-127">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="16eb4-127">Visual Studio 2019</span></span>

1. <span data-ttu-id="16eb4-128">Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.</span><span class="sxs-lookup"><span data-stu-id="16eb4-128">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Boîte de dialogue VS2019 ouvrir le gestionnaire d’extensions](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="16eb4-130">Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.</span><span class="sxs-lookup"><span data-stu-id="16eb4-130">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="16eb4-131">Tapez *Model Builder ML.NET* dans la barre de recherche, puis sélectionnez « Model Builder ML.NET (Préversion) »</span><span class="sxs-lookup"><span data-stu-id="16eb4-131">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 Rechercher et installer l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="16eb4-133">Suivez les invites pour effectuer l’installation</span><span class="sxs-lookup"><span data-stu-id="16eb4-133">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="16eb4-134">Désinstaller</span><span class="sxs-lookup"><span data-stu-id="16eb4-134">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="16eb4-135">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="16eb4-135">Visual Studio 2017</span></span>

1. <span data-ttu-id="16eb4-136">Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.</span><span class="sxs-lookup"><span data-stu-id="16eb4-136">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 ouvre la boîte de dialogue gérer les extensions](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="16eb4-138">Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*</span><span class="sxs-lookup"><span data-stu-id="16eb4-138">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="16eb4-139">Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="16eb4-139">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 Rechercher et désinstaller l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="16eb4-141">Suivez les invites pour effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="16eb4-141">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="16eb4-142">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="16eb4-142">Visual Studio 2019</span></span>

1. <span data-ttu-id="16eb4-143">Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.</span><span class="sxs-lookup"><span data-stu-id="16eb4-143">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 ouvre la boîte de dialogue gérer les extensions](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="16eb4-145">Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*</span><span class="sxs-lookup"><span data-stu-id="16eb4-145">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="16eb4-146">Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="16eb4-146">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 Rechercher et désinstaller l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="16eb4-148">Suivez les invites pour effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="16eb4-148">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="16eb4-149">Mettre à niveau</span><span class="sxs-lookup"><span data-stu-id="16eb4-149">Upgrade</span></span>

<span data-ttu-id="16eb4-150">Le processus de mise à niveau est similaire au processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="16eb4-150">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="16eb4-151">Téléchargez la dernière version à partir de Visual Studio Marketplace ou utilisez le Gestionnaire d’extensions dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="16eb4-151">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
