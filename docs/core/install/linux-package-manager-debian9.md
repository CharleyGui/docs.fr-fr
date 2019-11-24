---
title: Install .NET Core on Debian 9 - package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on Debian 9.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: e0aed17a7283a1d032aa8d6da723bc5b115d91a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451037"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="4f220-103">Debian 9 Package Manager - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="4f220-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4f220-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span><span class="sxs-lookup"><span data-stu-id="4f220-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="4f220-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span><span class="sxs-lookup"><span data-stu-id="4f220-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="4f220-106">Register Microsoft key and feed</span><span class="sxs-lookup"><span data-stu-id="4f220-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="4f220-107">Before installing .NET, you'll need to:</span><span class="sxs-lookup"><span data-stu-id="4f220-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4f220-108">Register the Microsoft key</span><span class="sxs-lookup"><span data-stu-id="4f220-108">Register the Microsoft key</span></span>
- <span data-ttu-id="4f220-109">register the product repository</span><span class="sxs-lookup"><span data-stu-id="4f220-109">register the product repository</span></span>
- <span data-ttu-id="4f220-110">Install required dependencies</span><span class="sxs-lookup"><span data-stu-id="4f220-110">Install required dependencies</span></span>

<span data-ttu-id="4f220-111">This only needs to be done once per machine.</span><span class="sxs-lookup"><span data-stu-id="4f220-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4f220-112">Open a terminal and run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4f220-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4f220-113">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="4f220-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="4f220-114">Update the products available for installation, then install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="4f220-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4f220-115">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4f220-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4f220-116">Install the ASP.NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="4f220-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4f220-117">Update the products available for installation, then install the ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="4f220-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="4f220-118">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4f220-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4f220-119">Install the .NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="4f220-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="4f220-120">Update the products available for installation, then install the .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="4f220-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4f220-121">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="4f220-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4f220-122">How to install other versions</span><span class="sxs-lookup"><span data-stu-id="4f220-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
