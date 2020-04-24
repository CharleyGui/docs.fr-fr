---
title: Installer .NET Core sur Debian 9 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et exécuter sur Debian 9.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 2e45698d6b87499a54a25b6779ec1a767a2ece6b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645377"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="91ca4-103">Debian 9 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="91ca4-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="91ca4-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Debian 9.</span><span class="sxs-lookup"><span data-stu-id="91ca4-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="91ca4-105">Ajouter la clé de dépôt Microsoft et les flux</span><span class="sxs-lookup"><span data-stu-id="91ca4-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="91ca4-106">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="91ca4-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="91ca4-107">Ajoutez la clé de signature du forfait Microsoft à la liste des clés de confiance.</span><span class="sxs-lookup"><span data-stu-id="91ca4-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="91ca4-108">Ajoutez le référentiel au gestionnaire du paquet.</span><span class="sxs-lookup"><span data-stu-id="91ca4-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="91ca4-109">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="91ca4-109">Install required dependencies.</span></span>

<span data-ttu-id="91ca4-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="91ca4-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="91ca4-111">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="91ca4-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="91ca4-112">Installer le SDK core .NET</span><span class="sxs-lookup"><span data-stu-id="91ca4-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="91ca4-113">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="91ca4-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="91ca4-114">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="91ca4-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="91ca4-115">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="91ca4-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="91ca4-116">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="91ca4-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="91ca4-117">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="91ca4-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="91ca4-118">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="91ca4-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="91ca4-119">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91ca4-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="91ca4-120">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="91ca4-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="91ca4-121">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="91ca4-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="91ca4-122">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="91ca4-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="91ca4-123">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91ca4-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="91ca4-124">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="91ca4-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
