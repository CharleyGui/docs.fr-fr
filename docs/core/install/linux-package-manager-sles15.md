---
title: Installer .NET Core sur SLES 15-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur SLES 15.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 5551ce8cffa92d4efb6bbe9db2a4887f4b26cd6e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836912"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="b7f58-103">SLES 15 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7f58-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="b7f58-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur SLES 15.</span><span class="sxs-lookup"><span data-stu-id="b7f58-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span> <span data-ttu-id="b7f58-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="b7f58-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="b7f58-106">Inscrire le flux et la clé Microsoft</span><span class="sxs-lookup"><span data-stu-id="b7f58-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="b7f58-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="b7f58-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="b7f58-108">Inscrire la clé Microsoft</span><span class="sxs-lookup"><span data-stu-id="b7f58-108">Register the Microsoft key</span></span>
- <span data-ttu-id="b7f58-109">inscrire le dépôt du produit</span><span class="sxs-lookup"><span data-stu-id="b7f58-109">register the product repository</span></span>
- <span data-ttu-id="b7f58-110">Installer les dépendances requises</span><span class="sxs-lookup"><span data-stu-id="b7f58-110">Install required dependencies</span></span>

<span data-ttu-id="b7f58-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="b7f58-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="b7f58-112">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b7f58-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="b7f58-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7f58-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="b7f58-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7f58-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="b7f58-115">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b7f58-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="b7f58-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b7f58-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="b7f58-117">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b7f58-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="b7f58-118">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b7f58-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="b7f58-119">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="b7f58-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="b7f58-120">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b7f58-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="b7f58-121">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="b7f58-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b7f58-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="b7f58-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
