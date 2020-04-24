---
title: Installer .NET Core sur CentOS 7 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: f8c4115b9d85edc36809f0daed5f6825149c8411
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645404"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="2a3ea-103">CentOS 7 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="2a3ea-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="2a3ea-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="2a3ea-105">Ajouter la clé de dépôt Microsoft et les flux</span><span class="sxs-lookup"><span data-stu-id="2a3ea-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="2a3ea-106">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="2a3ea-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="2a3ea-107">Ajoutez la clé de signature du forfait Microsoft à la liste des clés de confiance.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="2a3ea-108">Ajoutez le référentiel au gestionnaire du paquet.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="2a3ea-109">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-109">Install required dependencies.</span></span>

<span data-ttu-id="2a3ea-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="2a3ea-111">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="2a3ea-112">Installer le SDK core .NET</span><span class="sxs-lookup"><span data-stu-id="2a3ea-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="2a3ea-113">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="2a3ea-114">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-114">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="2a3ea-115">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2a3ea-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="2a3ea-116">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="2a3ea-117">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-117">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="2a3ea-118">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="2a3ea-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="2a3ea-119">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="2a3ea-120">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-120">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="2a3ea-121">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="2a3ea-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="2a3ea-122">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="2a3ea-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="2a3ea-123">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2a3ea-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="2a3ea-124">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="2a3ea-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
