---
title: Installer .NET Core sur Fedora 29 - gestionnaire de paquets - .NET Core
description: Utilisez un gestionnaire de paquets pour installer .NET Core SDK et l’exécution sur Fedora 29.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1cbe38f4f104a8e178d8bcfd1fa1bd6d7645261
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645316"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="3aeea-103">Fedora 29 Package Manager - Installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="3aeea-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="3aeea-104">Cet article décrit comment utiliser un gestionnaire de paquets pour installer .NET Core sur Fedora 29.</span><span class="sxs-lookup"><span data-stu-id="3aeea-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="3aeea-105">Ajouter la clé de dépôt Microsoft et les flux</span><span class="sxs-lookup"><span data-stu-id="3aeea-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="3aeea-106">Avant d’installer .NET, vous devrez :</span><span class="sxs-lookup"><span data-stu-id="3aeea-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="3aeea-107">Ajoutez la clé de signature du forfait Microsoft à la liste des clés de confiance.</span><span class="sxs-lookup"><span data-stu-id="3aeea-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="3aeea-108">Ajoutez le référentiel au gestionnaire du paquet.</span><span class="sxs-lookup"><span data-stu-id="3aeea-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="3aeea-109">Installer les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="3aeea-109">Install required dependencies.</span></span>

<span data-ttu-id="3aeea-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="3aeea-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="3aeea-111">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="3aeea-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="3aeea-112">Installer le SDK core .NET</span><span class="sxs-lookup"><span data-stu-id="3aeea-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="3aeea-113">Mettre à jour les produits disponibles pour l’installation, puis installer le .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="3aeea-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="3aeea-114">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="3aeea-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="3aeea-115">Installer le temps d’exécution ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3aeea-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="3aeea-116">Mettre à jour les produits disponibles pour l’installation, puis installer le ASP.NET’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3aeea-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="3aeea-117">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="3aeea-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="3aeea-118">Installer le temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="3aeea-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="3aeea-119">Mettre à jour les produits disponibles pour l’installation, puis installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3aeea-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="3aeea-120">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="3aeea-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="3aeea-121">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="3aeea-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="3aeea-122">Dépanner le gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="3aeea-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="3aeea-123">Cette section fournit des informations sur les erreurs courantes que vous pouvez obtenir lors de l’utilisation du gestionnaire de paquet pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3aeea-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="3aeea-124">N’est pas allé chercher</span><span class="sxs-lookup"><span data-stu-id="3aeea-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
