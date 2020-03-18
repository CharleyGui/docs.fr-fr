---
title: Installer .NET Core sur Ubuntu 18.04 package manager - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur Ubuntu 18.04.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: e36116d357b8fcd5ced328a574e12c558dd9e2f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920689"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="b06fc-103">Ubuntu 18.04 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="b06fc-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="b06fc-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Ubuntu 18.04.</span><span class="sxs-lookup"><span data-stu-id="b06fc-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="b06fc-105">Si vous installez le temps d’exécution, nous vous suggérons d’installer le [ASP.NET’arrêt Core,](#install-the-aspnet-core-runtime)car il comprend à la fois .NET Core et ASP.NET les temps d’exécution Core.</span><span class="sxs-lookup"><span data-stu-id="b06fc-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="b06fc-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="b06fc-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="b06fc-107">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="b06fc-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="b06fc-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b06fc-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="b06fc-109">Enregistrez le référentiel du produit.</span><span class="sxs-lookup"><span data-stu-id="b06fc-109">Register the product repository.</span></span>
- <span data-ttu-id="b06fc-110">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="b06fc-110">Install required dependencies.</span></span>

<span data-ttu-id="b06fc-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="b06fc-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="b06fc-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b06fc-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="b06fc-113">Installer le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="b06fc-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="b06fc-114">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b06fc-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="b06fc-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b06fc-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="b06fc-116">Si vous recevez un message d’erreur similaire **à Unable pour localiser le paquet dotnet-sdk-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquet.</span><span class="sxs-lookup"><span data-stu-id="b06fc-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="b06fc-117">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b06fc-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="b06fc-118">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’arrêt Core.</span><span class="sxs-lookup"><span data-stu-id="b06fc-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="b06fc-119">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b06fc-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="b06fc-120">Si vous recevez un message d’erreur similaire **à Unable pour localiser le package aspnetcore-runtime-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquets.</span><span class="sxs-lookup"><span data-stu-id="b06fc-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="b06fc-121">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="b06fc-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="b06fc-122">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b06fc-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="b06fc-123">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b06fc-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="b06fc-124">Si vous recevez un message d’erreur similaire **à Unable pour localiser le package dotnet-runtime-3.1**, consultez le [Dépannage de la](#troubleshoot-the-package-manager) section gestionnaire de paquet.</span><span class="sxs-lookup"><span data-stu-id="b06fc-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b06fc-125">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="b06fc-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="b06fc-126">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="b06fc-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="b06fc-127">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b06fc-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="b06fc-128">Incapable de localiser</span><span class="sxs-lookup"><span data-stu-id="b06fc-128">Unable to locate</span></span>

<span data-ttu-id="b06fc-129">Si vous recevez un message d’erreur similaire **à Unable pour localiser le paquet «le paquet .NET Core»,** exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b06fc-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="b06fc-130">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b06fc-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="b06fc-131">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="b06fc-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
