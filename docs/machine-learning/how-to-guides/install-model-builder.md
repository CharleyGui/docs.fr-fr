---
title: Guide pratique pour installer Model Builder
description: Découvrir comment installer l’outil Model Builder ML.NET
author: luisquintanilla
ms.author: luquinta
ms.date: 06/21/2019
ms.custom: mvc, how-to
ms.openlocfilehash: a1034d294012b8df5ec778fc40602fe52223961d
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774569"
---
# <a name="how-to-install-mlnet-model-builder"></a><span data-ttu-id="de9a0-103">Guide pratique pour installer Model Builder ML.NET</span><span class="sxs-lookup"><span data-stu-id="de9a0-103">How to install ML.NET Model Builder</span></span>

<span data-ttu-id="de9a0-104">Découvrez comment installer Model Builder ML.NET pour ajouter le machine learning à vos applications .NET.</span><span class="sxs-lookup"><span data-stu-id="de9a0-104">Learn how to install ML.NET Model Builder to add machine learning to your .NET applications.</span></span>

> [!NOTE]
> <span data-ttu-id="de9a0-105">Model Builder est actuellement en préversion.</span><span class="sxs-lookup"><span data-stu-id="de9a0-105">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="de9a0-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="de9a0-106">Pre-requisites</span></span>

- <span data-ttu-id="de9a0-107">Visual Studio 2017 version 15.9.12 ou ultérieure/Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="de9a0-107">Visual Studio 2017 version 15.9.12 or later / Visual Studio 2019</span></span>
- <span data-ttu-id="de9a0-108">SDK .NET Core 2.1 ou ultérieur</span><span class="sxs-lookup"><span data-stu-id="de9a0-108">.NET Core 2.1 or later SDK</span></span>

## <a name="limitations"></a><span data-ttu-id="de9a0-109">Limitations</span><span class="sxs-lookup"><span data-stu-id="de9a0-109">Limitations</span></span>

- <span data-ttu-id="de9a0-110">L’extension Model Builder ML.NET fonctionne actuellement seulement avec Visual Studio sur Windows.</span><span class="sxs-lookup"><span data-stu-id="de9a0-110">ML.NET Model Builder Extension currently only works on Visual Studio on Windows.</span></span>
- <span data-ttu-id="de9a0-111">La limite du jeu de données d’entraînement est de 1 Go</span><span class="sxs-lookup"><span data-stu-id="de9a0-111">Training dataset limit of 1GB</span></span>
- <span data-ttu-id="de9a0-112">SQL Server a une limite de 100 000 lignes pour l’entraînement</span><span class="sxs-lookup"><span data-stu-id="de9a0-112">SQL Server has a limit of 100 thousand rows for training</span></span>
- <span data-ttu-id="de9a0-113">Microsoft SQL Server Data Tools pour Visual Studio 2017 n’est pas pris en charge</span><span class="sxs-lookup"><span data-stu-id="de9a0-113">Microsoft SQL Server Data Tools for Visual Studio 2017 is not supported</span></span>

## <a name="install"></a><span data-ttu-id="de9a0-114">Installez</span><span class="sxs-lookup"><span data-stu-id="de9a0-114">Install</span></span>

<span data-ttu-id="de9a0-115">Model Builder ML.NET peut être installé via Visual Studio Marketplace ou depuis Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="de9a0-115">ML.NET Model builder can be installed either through the Visual Studio Marketplace or from within Visual Studio.</span></span>

### <a name="visual-studio-marketplace"></a><span data-ttu-id="de9a0-116">Visual Studio Marketplace</span><span class="sxs-lookup"><span data-stu-id="de9a0-116">Visual Studio Marketplace</span></span>

1. <span data-ttu-id="de9a0-117">Télécharger depuis [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span><span class="sxs-lookup"><span data-stu-id="de9a0-117">Download from [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=MLNET.07)</span></span>
1. <span data-ttu-id="de9a0-118">Suivre les invites pour installer sur les différentes versions de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="de9a0-118">Follow prompts to install onto respective Visual Studio version</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="de9a0-119">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="de9a0-119">Visual Studio 2017</span></span>

1. <span data-ttu-id="de9a0-120">Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.</span><span class="sxs-lookup"><span data-stu-id="de9a0-120">In the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![Boîte de dialogue VS2017 ouvrir le gestionnaire d’extensions](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="de9a0-122">Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.</span><span class="sxs-lookup"><span data-stu-id="de9a0-122">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="de9a0-123">Dans la barre de recherche, recherchez *Model Builder ML.NET* puis, dans les résultats, sélectionnez « Model Builder ML.NET (Préversion) »</span><span class="sxs-lookup"><span data-stu-id="de9a0-123">In the search bar, search for *ML.NET Model Builder* and from the results, select ML.NET Model Builder (Preview)</span></span>

    ![VS2017 Rechercher et installer l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2017-install-model-builder.png)

1. <span data-ttu-id="de9a0-125">Suivez les invites pour effectuer l’installation</span><span class="sxs-lookup"><span data-stu-id="de9a0-125">Follow the prompts to complete the installation</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="de9a0-126">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="de9a0-126">Visual Studio 2019</span></span>

1. <span data-ttu-id="de9a0-127">Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.</span><span class="sxs-lookup"><span data-stu-id="de9a0-127">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![Boîte de dialogue VS2019 ouvrir le gestionnaire d’extensions](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="de9a0-129">Dans l’invite *Extension et mises à jour*, sélectionnez le nœud *En ligne*.</span><span class="sxs-lookup"><span data-stu-id="de9a0-129">Inside the *Extension and Updates* prompt, select the *Online* node.</span></span>
1. <span data-ttu-id="de9a0-130">Tapez *Model Builder ML.NET* dans la barre de recherche, puis sélectionnez « Model Builder ML.NET (Préversion) »</span><span class="sxs-lookup"><span data-stu-id="de9a0-130">Type *ML.NET Model Builder* into the search bar select ML.NET Model Builder (Preview)</span></span>

    ![VS2019 Rechercher et installer l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2019-install-model-builder.png)

1. <span data-ttu-id="de9a0-132">Suivez les invites pour effectuer l’installation</span><span class="sxs-lookup"><span data-stu-id="de9a0-132">Follow the prompts to complete the installation</span></span>

## <a name="uninstall"></a><span data-ttu-id="de9a0-133">Désinstaller</span><span class="sxs-lookup"><span data-stu-id="de9a0-133">Uninstall</span></span>

### <a name="visual-studio-2017"></a><span data-ttu-id="de9a0-134">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="de9a0-134">Visual Studio 2017</span></span>

1. <span data-ttu-id="de9a0-135">Dans la barre de menus, sélectionnez **Outils** > **Extensions et mises à jour**.</span><span class="sxs-lookup"><span data-stu-id="de9a0-135">On the menu bar, select **Tools** > **Extensions and Updates**</span></span>

    ![VS2017 ouvre la boîte de dialogue gérer les extensions](./media/install-model-builder/vs2017-open-extensions-manager.png)

1. <span data-ttu-id="de9a0-137">Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*</span><span class="sxs-lookup"><span data-stu-id="de9a0-137">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="de9a0-138">Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="de9a0-138">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2017 Rechercher et désinstaller l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2017-uninstall-model-builder.png)

1. <span data-ttu-id="de9a0-140">Suivez les invites pour effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="de9a0-140">Follow the prompts to complete the uninstallation.</span></span>

### <a name="visual-studio-2019"></a><span data-ttu-id="de9a0-141">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="de9a0-141">Visual Studio 2019</span></span>

1. <span data-ttu-id="de9a0-142">Dans la barre de menus, sélectionnez **Extensions** > **Gérer les extensions**.</span><span class="sxs-lookup"><span data-stu-id="de9a0-142">On the menu bar, select **Extensions** > **Manage Extensions**</span></span>

    ![VS2019 ouvre la boîte de dialogue gérer les extensions](./media/install-model-builder/vs2019-open-extensions-manager.png)

1. <span data-ttu-id="de9a0-144">Dans l’invite *Extension et mises à jour*, développez le nœud *Installé* et sélectionnez *Outils*</span><span class="sxs-lookup"><span data-stu-id="de9a0-144">Inside the *Extension and Updates* prompt, expand the *Installed* node and select *Tools*</span></span>
1. <span data-ttu-id="de9a0-145">Sélectionnez Model Builder ML.NET (Préversion) dans la liste des outils, puis sélectionnez *Désinstaller*.</span><span class="sxs-lookup"><span data-stu-id="de9a0-145">Select ML.NET Model Builder (Preview) from the list of tools and then, select *Uninstall*</span></span>

    ![VS2019 Rechercher et désinstaller l’extension du générateur de modèles dans la boîte de dialogue Gestionnaire d’extensions](./media/install-model-builder/vs2019-uninstall-model-builder.png)

1. <span data-ttu-id="de9a0-147">Suivez les invites pour effectuer la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="de9a0-147">Follow the prompts to complete the uninstallation.</span></span>

## <a name="upgrade"></a><span data-ttu-id="de9a0-148">Mettre à niveau</span><span class="sxs-lookup"><span data-stu-id="de9a0-148">Upgrade</span></span>

<span data-ttu-id="de9a0-149">Le processus de mise à niveau est similaire au processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="de9a0-149">The upgrade process is similar to the installation process.</span></span> <span data-ttu-id="de9a0-150">Téléchargez la dernière version à partir de Visual Studio Marketplace ou utilisez le Gestionnaire d’extensions dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="de9a0-150">Either download the latest version from Visual Studio Marketplace or use the Extensions Manager in Visual Studio.</span></span>
