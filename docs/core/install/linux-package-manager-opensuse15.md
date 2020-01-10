---
title: Installer .NET Core sur openSUSE 15-gestionnaire de package-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur openSUSE 15.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740668"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="7f2ee-103">Gestionnaire de package openSUSE 15-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f2ee-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7f2ee-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="7f2ee-105">Si vous installez le runtime, nous vous suggérons d’installer le [runtime ASP.net Core](#install-the-aspnet-core-runtime), car il comprend des runtimes .net Core et ASP.net core.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="7f2ee-106">Inscrire la clé et le flux Microsoft</span><span class="sxs-lookup"><span data-stu-id="7f2ee-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="7f2ee-107">Avant d’installer .NET, vous devez :</span><span class="sxs-lookup"><span data-stu-id="7f2ee-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7f2ee-108">Enregistrez la clé Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="7f2ee-109">Enregistrez le dépôt du produit.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-109">Register the product repository.</span></span>
- <span data-ttu-id="7f2ee-110">Installez les dépendances requises.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-110">Install required dependencies.</span></span>

<span data-ttu-id="7f2ee-111">Vous ne devez faire ces opérations qu’une seule fois par machine.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7f2ee-112">Ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a><span data-ttu-id="7f2ee-113">Erreur de dépendance avec .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="7f2ee-113">Dependency error with .NET Core 3.1</span></span>

<span data-ttu-id="7f2ee-114">Le flux du package .NET Core 3,1 pour openSUSE présente un problème avec la dépendance **krb5** .</span><span class="sxs-lookup"><span data-stu-id="7f2ee-114">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="7f2ee-115">Utilisez la commande suivante pour installer les dépendances appropriées avant d’installer .NET Core 3,1 ou ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-115">Use the following command to install the correct dependencies prior to installing .NET Core 3.1 or ASP.NET Core 3.1.</span></span>

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7f2ee-116">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f2ee-116">Install the .NET Core SDK</span></span>

<span data-ttu-id="7f2ee-117">Mettez à jour les produits disponibles pour l’installation, puis installez le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-117">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7f2ee-118">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7f2ee-119">Le flux du package .NET Core 3,1 pour openSUSE présente un problème avec la dépendance **krb5** .</span><span class="sxs-lookup"><span data-stu-id="7f2ee-119">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="7f2ee-120">Utilisez la commande suivante pour installer les dépendances appropriées, puis installez le kit de développement logiciel (SDK) .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-120">Use the following command to install the correct dependencies, then install the .NET Core 3.1 SDK.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7f2ee-121">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7f2ee-121">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7f2ee-122">Mettez à jour les produits disponibles pour l’installation, puis installez le runtime ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-122">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="7f2ee-123">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-123">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7f2ee-124">Le flux du package .NET Core 3,1 pour openSUSE présente un problème avec la dépendance **krb5** .</span><span class="sxs-lookup"><span data-stu-id="7f2ee-124">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="7f2ee-125">Utilisez la commande suivante pour installer les dépendances appropriées, puis installez le runtime ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-125">Use the following command to install the correct dependencies, then install the ASP.NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7f2ee-126">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f2ee-126">Install the .NET Core runtime</span></span>

<span data-ttu-id="7f2ee-127">Mettez à jour les produits disponibles pour l’installation, puis installez le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-127">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7f2ee-128">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-128">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7f2ee-129">Le flux du package .NET Core 3,1 pour openSUSE présente un problème avec la dépendance **krb5** .</span><span class="sxs-lookup"><span data-stu-id="7f2ee-129">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="7f2ee-130">Utilisez la commande suivante pour installer les dépendances appropriées, puis installez le Runtime .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7f2ee-130">Use the following command to install the correct dependencies, then install the .NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7f2ee-131">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="7f2ee-131">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
