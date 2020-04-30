---
title: Installer .NET Core sur Ubuntu 19,04 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Ubuntu 19,04.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: df7f2b093c91a0056f612f167450b5244ebd451c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595646"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="885cb-103">Gestionnaire de package Ubuntu 19,04-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="885cb-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="885cb-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Ubuntu 19,04.</span><span class="sxs-lookup"><span data-stu-id="885cb-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="885cb-105">Ajouter la clé et le flux du référentiel Microsoft</span><span class="sxs-lookup"><span data-stu-id="885cb-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="885cb-106">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="885cb-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="885cb-107">Ajoutez la clé de signature de package Microsoft à la liste des clés approuvées.</span><span class="sxs-lookup"><span data-stu-id="885cb-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="885cb-108">Ajoutez le référentiel au gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="885cb-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="885cb-109">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="885cb-109">Install required dependencies.</span></span>

<span data-ttu-id="885cb-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="885cb-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="885cb-111">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="885cb-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="885cb-112">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="885cb-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="885cb-113">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="885cb-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="885cb-114">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="885cb-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="885cb-115">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-SDK-3,1**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="885cb-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="885cb-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="885cb-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="885cb-117">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="885cb-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="885cb-118">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="885cb-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="885cb-119">Si vous recevez un message d’erreur semblable à **incapable de localiser le package aspnetcore-Runtime-3,1**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="885cb-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="885cb-120">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="885cb-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="885cb-121">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="885cb-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="885cb-122">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="885cb-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="885cb-123">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-Runtime-3,1**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="885cb-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="885cb-124">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="885cb-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="885cb-125">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="885cb-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="885cb-126">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="885cb-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="885cb-127">Impossible de localiser</span><span class="sxs-lookup"><span data-stu-id="885cb-127">Unable to locate</span></span>

<span data-ttu-id="885cb-128">Si vous recevez un message d’erreur semblable à **incapable de localiser le package {le package .net Core}**, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="885cb-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="885cb-129">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="885cb-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="885cb-130">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="885cb-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
