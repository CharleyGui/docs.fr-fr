---
title: Install .NET Core on Ubuntu 18.04 package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on Ubuntu 18.04.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 6929c7a91c131abb1170938fee010b077b1dbdc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450862"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="4eea0-103">Ubuntu 18.04 Package Manager - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="4eea0-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4eea0-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span><span class="sxs-lookup"><span data-stu-id="4eea0-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="4eea0-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span><span class="sxs-lookup"><span data-stu-id="4eea0-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="4eea0-106">Register Microsoft key and feed</span><span class="sxs-lookup"><span data-stu-id="4eea0-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="4eea0-107">Before installing .NET, you'll need to:</span><span class="sxs-lookup"><span data-stu-id="4eea0-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4eea0-108">Register the Microsoft key</span><span class="sxs-lookup"><span data-stu-id="4eea0-108">Register the Microsoft key</span></span>
- <span data-ttu-id="4eea0-109">register the product repository</span><span class="sxs-lookup"><span data-stu-id="4eea0-109">register the product repository</span></span>
- <span data-ttu-id="4eea0-110">Install required dependencies</span><span class="sxs-lookup"><span data-stu-id="4eea0-110">Install required dependencies</span></span>

<span data-ttu-id="4eea0-111">This only needs to be done once per machine.</span><span class="sxs-lookup"><span data-stu-id="4eea0-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4eea0-112">Open a terminal and run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4eea0-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4eea0-113">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="4eea0-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="4eea0-114">Update the products available for installation, then install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4eea0-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4eea0-115">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4eea0-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="4eea0-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span><span class="sxs-lookup"><span data-stu-id="4eea0-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4eea0-117">Install the ASP.NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="4eea0-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4eea0-118">Update the products available for installation, then install the ASP.NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="4eea0-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="4eea0-119">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4eea0-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="4eea0-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span><span class="sxs-lookup"><span data-stu-id="4eea0-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4eea0-121">Install the .NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="4eea0-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="4eea0-122">Update the products available for installation, then install the .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="4eea0-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4eea0-123">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4eea0-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

> [!IMPORTANT]
> <span data-ttu-id="4eea0-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span><span class="sxs-lookup"><span data-stu-id="4eea0-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.0**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4eea0-125">How to install other versions</span><span class="sxs-lookup"><span data-stu-id="4eea0-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="4eea0-126">Troubleshoot the package manager</span><span class="sxs-lookup"><span data-stu-id="4eea0-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="4eea0-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}** , run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4eea0-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="4eea0-128">If that doesn't work, you can run a manual install with the following commands.</span><span class="sxs-lookup"><span data-stu-id="4eea0-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
