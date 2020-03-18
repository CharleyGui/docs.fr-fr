---
title: Installer .NET Core sur Debian 9 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et exécuter sur Debian 9.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 32b152ff9be5135cf0ca7f8914bc9ee4f78000be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920849"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="874d2-103">Debian 9 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="874d2-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="874d2-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Debian 9.</span><span class="sxs-lookup"><span data-stu-id="874d2-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="874d2-105">Si vous installez le temps d’exécution, nous vous suggérons d’installer le [ASP.NET’arrêt Core,](#install-the-aspnet-core-runtime)car il comprend à la fois .NET Core et ASP.NET les temps d’exécution Core.</span><span class="sxs-lookup"><span data-stu-id="874d2-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="874d2-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="874d2-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="874d2-107">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="874d2-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="874d2-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="874d2-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="874d2-109">Enregistrez le référentiel du produit.</span><span class="sxs-lookup"><span data-stu-id="874d2-109">Register the product repository.</span></span>
- <span data-ttu-id="874d2-110">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="874d2-110">Install required dependencies.</span></span>

<span data-ttu-id="874d2-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="874d2-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="874d2-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="874d2-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="874d2-113">Installer le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="874d2-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="874d2-114">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="874d2-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="874d2-115">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="874d2-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="874d2-116">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="874d2-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="874d2-117">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="874d2-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="874d2-118">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="874d2-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="874d2-119">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="874d2-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="874d2-120">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="874d2-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="874d2-121">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="874d2-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="874d2-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="874d2-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="874d2-123">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="874d2-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="874d2-124">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="874d2-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="874d2-125">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="874d2-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
