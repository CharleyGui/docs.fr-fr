---
title: Installer .NET Core sur Debian 10-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur Debian 10.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 038f5579f99f700ce47dc67be2fd344f01cf800c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595615"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="ce861-103">Debian 10 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce861-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="ce861-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur Debian 10.</span><span class="sxs-lookup"><span data-stu-id="ce861-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="ce861-105">Ajouter la clé et le flux du référentiel Microsoft</span><span class="sxs-lookup"><span data-stu-id="ce861-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="ce861-106">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="ce861-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="ce861-107">Ajoutez la clé de signature de package Microsoft à la liste des clés approuvées.</span><span class="sxs-lookup"><span data-stu-id="ce861-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="ce861-108">Ajoutez le référentiel au gestionnaire de package.</span><span class="sxs-lookup"><span data-stu-id="ce861-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="ce861-109">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="ce861-109">Install required dependencies.</span></span>

<span data-ttu-id="ce861-110">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="ce861-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="ce861-111">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce861-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="ce861-112">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce861-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="ce861-113">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce861-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="ce861-114">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce861-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="ce861-115">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce861-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="ce861-116">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce861-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="ce861-117">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce861-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="ce861-118">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="ce861-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="ce861-119">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce861-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="ce861-120">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce861-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ce861-121">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="ce861-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="ce861-122">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="ce861-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="ce861-123">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce861-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="ce861-124">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="ce861-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
