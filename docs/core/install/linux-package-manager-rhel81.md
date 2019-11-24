---
title: Install .NET Core on Linux RHEL 8.1 package manager - .NET Core
description: Use a package manager to install .NET Core SDK and runtime on RHEL 8.1.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 5b658fe4c56b945210534872fe3cc502eb31a763
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450974"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="21312-103">RHEL 8.1 Package Manager - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="21312-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="21312-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span><span class="sxs-lookup"><span data-stu-id="21312-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="21312-105">Register your Red Hat subscription</span><span class="sxs-lookup"><span data-stu-id="21312-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="21312-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span><span class="sxs-lookup"><span data-stu-id="21312-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="21312-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="21312-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="21312-108">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="21312-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="21312-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="21312-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="21312-110">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="21312-110">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="21312-111">Install the ASP.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="21312-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="21312-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="21312-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="21312-113">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="21312-113">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="21312-114">Install the .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="21312-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="21312-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span><span class="sxs-lookup"><span data-stu-id="21312-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="21312-116">In your terminal, run the following commands.</span><span class="sxs-lookup"><span data-stu-id="21312-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```
