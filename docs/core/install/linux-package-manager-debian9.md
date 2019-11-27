---
title: Installer .NET Core sur Debian 9-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Debian 9.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: e0aed17a7283a1d032aa8d6da723bc5b115d91a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451037"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="f83a0-103">Gestionnaire de package Debian 9-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="f83a0-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="f83a0-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Debian 9.</span><span class="sxs-lookup"><span data-stu-id="f83a0-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="f83a0-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="f83a0-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="f83a0-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="f83a0-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="f83a0-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="f83a0-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="f83a0-108">Inscrire la clé Microsoft</span><span class="sxs-lookup"><span data-stu-id="f83a0-108">Register the Microsoft key</span></span>
- <span data-ttu-id="f83a0-109">inscrire le dépôt du produit</span><span class="sxs-lookup"><span data-stu-id="f83a0-109">register the product repository</span></span>
- <span data-ttu-id="f83a0-110">Installer les dépendances requises</span><span class="sxs-lookup"><span data-stu-id="f83a0-110">Install required dependencies</span></span>

<span data-ttu-id="f83a0-111">Cette opération ne doit être effectuée qu’une fois par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f83a0-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="f83a0-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f83a0-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="f83a0-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="f83a0-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="f83a0-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f83a0-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="f83a0-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f83a0-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="f83a0-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f83a0-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="f83a0-117">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f83a0-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="f83a0-118">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f83a0-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="f83a0-119">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="f83a0-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="f83a0-120">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f83a0-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="f83a0-121">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f83a0-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f83a0-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="f83a0-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
