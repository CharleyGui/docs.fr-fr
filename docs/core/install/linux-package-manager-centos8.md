---
title: Installer .NET Core sur Linux CentOS 8 Package Manager-.NET Core
description: Utilisez un gestionnaire de package pour installer kit SDK .NET Core et le runtime sur CentOS 8.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: b4cf5975e18aa8dfa8649c0d038caf38d648ad86
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728518"
---
# <a name="centos-8-package-manager---install-net-core"></a><span data-ttu-id="748e2-103">CentOS 8 Package Manager-installer .NET Core</span><span class="sxs-lookup"><span data-stu-id="748e2-103">CentOS 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="748e2-104">Cet article explique comment utiliser un gestionnaire de package pour installer .NET Core sur CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="748e2-104">This article describes how to use a package manager to install .NET Core on CentOS 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="748e2-105">Installer le kit SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="748e2-105">Install the .NET Core SDK</span></span>

<span data-ttu-id="748e2-106">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="748e2-106">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="748e2-107">Installer le runtime ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="748e2-107">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="748e2-108">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="748e2-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="748e2-109">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="748e2-109">Install the .NET Core Runtime</span></span>

<span data-ttu-id="748e2-110">Dans votre terminal, exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="748e2-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="748e2-111">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="748e2-111">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
