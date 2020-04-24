---
title: Installer .NET Core sur Ubuntu 19.10 package manager - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur Ubuntu 19.10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3a1e6a184fbe2d20b3a4580049b64c735d860b5f
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645530"
---
# <a name="ubuntu-1910-package-manager---install-net-core"></a><span data-ttu-id="ba3c9-103">Ubuntu 19.10 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="ba3c9-103">Ubuntu 19.10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="ba3c9-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Ubuntu 19.10.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="ba3c9-105">Ajouter la clé de dépôt Microsoft et les flux</span><span class="sxs-lookup"><span data-stu-id="ba3c9-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="ba3c9-106">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="ba3c9-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="ba3c9-107">Ajoutez la clé de signature du forfait Microsoft à la liste des clés de confiance.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="ba3c9-108">Ajoutez le référentiel au gestionnaire du paquet.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="ba3c9-109">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-109">Install required dependencies.</span></span>

<span data-ttu-id="ba3c9-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="ba3c9-111">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="ba3c9-112">Installer le SDK core .NET</span><span class="sxs-lookup"><span data-stu-id="ba3c9-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="ba3c9-113">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="ba3c9-114">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ba3c9-115">Si vous recevez un message d’erreur similaire **à Unable pour localiser le paquet dotnet-sdk-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquet.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="ba3c9-116">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba3c9-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="ba3c9-117">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’arrêt Core.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="ba3c9-118">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ba3c9-119">Si vous recevez un message d’erreur similaire **à Unable pour localiser le package aspnetcore-runtime-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquets.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="ba3c9-120">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="ba3c9-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="ba3c9-121">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="ba3c9-122">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="ba3c9-123">Si vous recevez un message d’erreur similaire **à Unable pour localiser le package dotnet-runtime-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquet.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ba3c9-124">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="ba3c9-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="ba3c9-125">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="ba3c9-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="ba3c9-126">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="ba3c9-127">Incapable de localiser</span><span class="sxs-lookup"><span data-stu-id="ba3c9-127">Unable to locate</span></span>

<span data-ttu-id="ba3c9-128">Si vous recevez un message d’erreur similaire **à Unable pour localiser le paquet «le paquet .NET Core»,** exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="ba3c9-129">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ba3c9-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="ba3c9-130">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="ba3c9-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
