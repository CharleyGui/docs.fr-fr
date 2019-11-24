---
title: Install .NET Core on CentOS 7 - package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on CentOS 7.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 62b07342197addaa5c7d962c08c4ff1d7121eff8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451079"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="d5a20-103">CentOS 7 Package Manager - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="d5a20-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="d5a20-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span><span class="sxs-lookup"><span data-stu-id="d5a20-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="d5a20-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span><span class="sxs-lookup"><span data-stu-id="d5a20-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="d5a20-106">Register Microsoft key and feed</span><span class="sxs-lookup"><span data-stu-id="d5a20-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="d5a20-107">Before installing .NET, you'll need to:</span><span class="sxs-lookup"><span data-stu-id="d5a20-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="d5a20-108">Register the Microsoft key</span><span class="sxs-lookup"><span data-stu-id="d5a20-108">Register the Microsoft key</span></span>
- <span data-ttu-id="d5a20-109">register the product repository</span><span class="sxs-lookup"><span data-stu-id="d5a20-109">register the product repository</span></span>
- <span data-ttu-id="d5a20-110">Install required dependencies</span><span class="sxs-lookup"><span data-stu-id="d5a20-110">Install required dependencies</span></span>

<span data-ttu-id="d5a20-111">This only needs to be done once per machine.</span><span class="sxs-lookup"><span data-stu-id="d5a20-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="d5a20-112">Open a terminal and run the following command.</span><span class="sxs-lookup"><span data-stu-id="d5a20-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="d5a20-113">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="d5a20-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="d5a20-114">Update the products available for installation, then install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d5a20-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="d5a20-115">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="d5a20-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="d5a20-116">Install the ASP.NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="d5a20-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="d5a20-117">Update the products available for installation, then install the ASP.NET runtime.</span><span class="sxs-lookup"><span data-stu-id="d5a20-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="d5a20-118">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="d5a20-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="d5a20-119">Install the .NET Core runtime</span><span class="sxs-lookup"><span data-stu-id="d5a20-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="d5a20-120">Update the products available for installation, then install the .NET Core runtime.</span><span class="sxs-lookup"><span data-stu-id="d5a20-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="d5a20-121">In your terminal, run the following command.</span><span class="sxs-lookup"><span data-stu-id="d5a20-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="d5a20-122">How to install other versions</span><span class="sxs-lookup"><span data-stu-id="d5a20-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
