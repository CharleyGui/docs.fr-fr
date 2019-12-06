---
title: Installer .NET Core sur CentOS 7-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: cb65811d5cae5c747c2660b4b10486f3162b9f33
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836940"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="23c1b-103">Gestionnaire de package CentOS 7-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="23c1b-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="23c1b-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="23c1b-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="23c1b-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="23c1b-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="23c1b-106">Inscrire le flux et la clé Microsoft</span><span class="sxs-lookup"><span data-stu-id="23c1b-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="23c1b-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="23c1b-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="23c1b-108">Inscrire la clé Microsoft</span><span class="sxs-lookup"><span data-stu-id="23c1b-108">Register the Microsoft key</span></span>
- <span data-ttu-id="23c1b-109">inscrire le dépôt du produit</span><span class="sxs-lookup"><span data-stu-id="23c1b-109">register the product repository</span></span>
- <span data-ttu-id="23c1b-110">Installer les dépendances requises</span><span class="sxs-lookup"><span data-stu-id="23c1b-110">Install required dependencies</span></span>

<span data-ttu-id="23c1b-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="23c1b-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="23c1b-112">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="23c1b-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="23c1b-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="23c1b-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="23c1b-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23c1b-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="23c1b-115">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="23c1b-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="23c1b-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="23c1b-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="23c1b-117">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="23c1b-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="23c1b-118">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="23c1b-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="23c1b-119">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="23c1b-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="23c1b-120">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23c1b-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="23c1b-121">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="23c1b-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="23c1b-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="23c1b-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
