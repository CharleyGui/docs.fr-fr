---
title: Installer .NET Core sur Fedora 31 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur Fedora 31.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 28bda3676f99037e565080e1ff3f9d89a67d0d69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920781"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="5c567-103">Fedora 31 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="5c567-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="5c567-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Fedora 31.</span><span class="sxs-lookup"><span data-stu-id="5c567-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="5c567-105">Si vous installez le temps d’exécution, nous vous suggérons d’installer le [ASP.NET’arrêt Core,](#install-the-aspnet-core-runtime)car il comprend à la fois .NET Core et ASP.NET les temps d’exécution Core.</span><span class="sxs-lookup"><span data-stu-id="5c567-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="5c567-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="5c567-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="5c567-107">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="5c567-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="5c567-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c567-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="5c567-109">Enregistrez le référentiel du produit.</span><span class="sxs-lookup"><span data-stu-id="5c567-109">Register the product repository.</span></span>
- <span data-ttu-id="5c567-110">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="5c567-110">Install required dependencies.</span></span>

<span data-ttu-id="5c567-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="5c567-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="5c567-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="5c567-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="5c567-113">Installer le kit de développement logiciel (SDK) .NET Core</span><span class="sxs-lookup"><span data-stu-id="5c567-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="5c567-114">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5c567-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="5c567-115">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="5c567-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="5c567-116">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c567-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="5c567-117">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5c567-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="5c567-118">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="5c567-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="5c567-119">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="5c567-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="5c567-120">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c567-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="5c567-121">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="5c567-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5c567-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="5c567-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="5c567-123">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="5c567-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="5c567-124">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c567-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="5c567-125">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="5c567-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
