---
title: Installer .NET Core sur Fedora 31-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Fedora 31.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 25c670694ed2d9e89fe37cedf0b06efd8bc93293
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116965"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="f50b3-103">Fedora 31 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="f50b3-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="f50b3-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Fedora 31.</span><span class="sxs-lookup"><span data-stu-id="f50b3-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="f50b3-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="f50b3-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="f50b3-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="f50b3-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="f50b3-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="f50b3-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="f50b3-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f50b3-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="f50b3-109">Enregistrez le dépôt du produit.</span><span class="sxs-lookup"><span data-stu-id="f50b3-109">Register the product repository.</span></span>
- <span data-ttu-id="f50b3-110">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="f50b3-110">Install required dependencies.</span></span>

<span data-ttu-id="f50b3-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="f50b3-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="f50b3-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="f50b3-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="f50b3-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="f50b3-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="f50b3-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f50b3-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="f50b3-115">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f50b3-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="f50b3-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f50b3-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="f50b3-117">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f50b3-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="f50b3-118">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f50b3-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="f50b3-119">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="f50b3-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="f50b3-120">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f50b3-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="f50b3-121">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f50b3-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f50b3-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="f50b3-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
