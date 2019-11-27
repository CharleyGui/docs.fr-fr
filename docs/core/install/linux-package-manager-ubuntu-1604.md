---
title: Installer .NET Core sur Ubuntu 16,04 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Ubuntu 16,04.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 2409dc9f5e480b309bf7c9aa09b733ded01d772f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450953"
---
# <a name="ubuntu-1604-package-manager---install-net-core"></a><span data-ttu-id="586dd-103">Gestionnaire de package Ubuntu 16,04-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="586dd-103">Ubuntu 16.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="586dd-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Ubuntu 16,04.</span><span class="sxs-lookup"><span data-stu-id="586dd-104">This article describes how to use a package manager to install .NET Core on Ubuntu 16.04.</span></span> <span data-ttu-id="586dd-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="586dd-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="586dd-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="586dd-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="586dd-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="586dd-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="586dd-108">Inscrire la clé Microsoft</span><span class="sxs-lookup"><span data-stu-id="586dd-108">Register the Microsoft key</span></span>
- <span data-ttu-id="586dd-109">inscrire le dépôt du produit</span><span class="sxs-lookup"><span data-stu-id="586dd-109">register the product repository</span></span>
- <span data-ttu-id="586dd-110">Installer les dépendances requises</span><span class="sxs-lookup"><span data-stu-id="586dd-110">Install required dependencies</span></span>

<span data-ttu-id="586dd-111">Cette opération ne doit être effectuée qu’une fois par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="586dd-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="586dd-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="586dd-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="586dd-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="586dd-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="586dd-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="586dd-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="586dd-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="586dd-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="586dd-116">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-SDK-3,0**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="586dd-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="586dd-117">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="586dd-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="586dd-118">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="586dd-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="586dd-119">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="586dd-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="586dd-120">Si vous recevez un message d’erreur semblable à **incapable de localiser le package aspnetcore-Runtime-3,0**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="586dd-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="586dd-121">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="586dd-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="586dd-122">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="586dd-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="586dd-123">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="586dd-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="586dd-124">Si vous recevez un message d’erreur semblable à **incapable de localiser le package dotnet-Runtime-3,0**, consultez la section [résoudre les problèmes liés au gestionnaire de package](#troubleshoot-the-package-manager) .</span><span class="sxs-lookup"><span data-stu-id="586dd-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="586dd-125">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="586dd-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="586dd-126">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="586dd-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="586dd-127">Si vous recevez un message d’erreur semblable à **incapable de localiser le package {le package .net Core}** , exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="586dd-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="586dd-128">Si cela ne fonctionne pas, vous pouvez exécuter une installation manuelle avec les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="586dd-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/16.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
