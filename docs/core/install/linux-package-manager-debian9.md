---
title: Installer .NET Core sur Debian 9 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et exécuter sur Debian 9.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: cfe28d04edfac97938612537986498636c141be0
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134291"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="883a0-103">Debian 9 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="883a0-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="883a0-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Debian 9.</span><span class="sxs-lookup"><span data-stu-id="883a0-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="883a0-105">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="883a0-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="883a0-106">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="883a0-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="883a0-107">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="883a0-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="883a0-108">Enregistrez le référentiel du produit.</span><span class="sxs-lookup"><span data-stu-id="883a0-108">Register the product repository.</span></span>
- <span data-ttu-id="883a0-109">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="883a0-109">Install required dependencies.</span></span>

<span data-ttu-id="883a0-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="883a0-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="883a0-111">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="883a0-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="883a0-112">Installer le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="883a0-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="883a0-113">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="883a0-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="883a0-114">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="883a0-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="883a0-115">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="883a0-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="883a0-116">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="883a0-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="883a0-117">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="883a0-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="883a0-118">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="883a0-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="883a0-119">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="883a0-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="883a0-120">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="883a0-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="883a0-121">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="883a0-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="883a0-122">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="883a0-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="883a0-123">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="883a0-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="883a0-124">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="883a0-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
