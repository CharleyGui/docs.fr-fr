---
title: Installer .NET Core sur SLES 15-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur SLES 15.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: be5a21db8c3942bfe8827dfbce41bcf88aec342a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595610"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="1792b-103">SLES 15 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="1792b-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="1792b-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur SLES 15.</span><span class="sxs-lookup"><span data-stu-id="1792b-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="1792b-105">Ajouter la clé et le flux du référentiel Microsoft</span><span class="sxs-lookup"><span data-stu-id="1792b-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="1792b-106">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="1792b-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="1792b-107">Ajoutez la clé de signature de package Microsoft à la liste des clés approuvées.</span><span class="sxs-lookup"><span data-stu-id="1792b-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="1792b-108">Ajoutez le référentiel au gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="1792b-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="1792b-109">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="1792b-109">Install required dependencies.</span></span>

<span data-ttu-id="1792b-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="1792b-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="1792b-111">Ouvrez un terminal et exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="1792b-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="1792b-112">Actuellement, le package d’installation du référentiel SLES 15 Microsoft installe le fichier *Microsoft-prod. référentiel* dans le répertoire incorrect, empêchant ainsi zypper de trouver les packages .net core.</span><span class="sxs-lookup"><span data-stu-id="1792b-112">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="1792b-113">Pour résoudre ce problème, créez un lien symbolique dans le répertoire approprié.</span><span class="sxs-lookup"><span data-stu-id="1792b-113">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="1792b-114">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="1792b-114">Install the .NET Core SDK</span></span>

<span data-ttu-id="1792b-115">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1792b-115">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="1792b-116">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="1792b-116">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="1792b-117">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1792b-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="1792b-118">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1792b-118">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="1792b-119">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="1792b-119">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="1792b-120">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="1792b-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="1792b-121">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1792b-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="1792b-122">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="1792b-122">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1792b-123">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="1792b-123">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="1792b-124">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="1792b-124">Troubleshoot the package manager</span></span>

<span data-ttu-id="1792b-125">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1792b-125">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="1792b-126">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="1792b-126">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
