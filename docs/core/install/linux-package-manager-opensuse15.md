---
title: Installer .NET Core sur openSUSE 15-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: aaece5e3554ab567cf82c23265c8fba1656298d8
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920769"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="2d9a9-103">Gestionnaire de package openSUSE 15-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="2d9a9-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="2d9a9-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="2d9a9-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="2d9a9-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="2d9a9-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="2d9a9-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="2d9a9-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="2d9a9-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="2d9a9-109">Enregistrez le dépôt du produit.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-109">Register the product repository.</span></span>
- <span data-ttu-id="2d9a9-110">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-110">Install required dependencies.</span></span>

<span data-ttu-id="2d9a9-111">Cette opération ne doit être effectuée qu’une fois par ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="2d9a9-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="2d9a9-113">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="2d9a9-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="2d9a9-114">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="2d9a9-115">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="2d9a9-116">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2d9a9-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="2d9a9-117">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="2d9a9-118">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="2d9a9-119">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="2d9a9-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="2d9a9-120">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="2d9a9-121">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2d9a9-122">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="2d9a9-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="2d9a9-123">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="2d9a9-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="2d9a9-124">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d9a9-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="2d9a9-125">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="2d9a9-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
