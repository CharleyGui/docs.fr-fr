---
title: Installer .NET Core sur CentOS-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur CentOS.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9f4de70b4989be1d162f384518a015816a3e75a9
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324896"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-centos"></a><span data-ttu-id="6f255-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur CentOS</span><span class="sxs-lookup"><span data-stu-id="6f255-103">Install .NET Core SDK or .NET Core Runtime on CentOS</span></span>

<span data-ttu-id="6f255-104">.NET Core est pris en charge sur CentOS.</span><span class="sxs-lookup"><span data-stu-id="6f255-104">.NET Core is supported on CentOS.</span></span> <span data-ttu-id="6f255-105">Cet article explique comment installer .NET Core sur CentOS.</span><span class="sxs-lookup"><span data-stu-id="6f255-105">This article describes how to install .NET Core on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="6f255-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="6f255-106">Supported distributions</span></span>

<span data-ttu-id="6f255-107">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur CentOS 7 et CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="6f255-107">The following table is a list of currently supported .NET Core releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="6f255-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de CentOS ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6f255-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="6f255-109">Une ✔️ indique que la version de CentOS ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="6f255-109">A ✔️ indicates that the version of CentOS or .NET Core is still supported.</span></span>
- <span data-ttu-id="6f255-110">Une ❌ indique que la version de CentOS ou de .net Core n’est pas prise en charge sur cette version de CentOS.</span><span class="sxs-lookup"><span data-stu-id="6f255-110">A ❌ indicates that the version of CentOS or .NET Core isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="6f255-111">Quand une version de CentOS et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6f255-111">When both a version of CentOS and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="6f255-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="6f255-112">CentOS</span></span>                   | <span data-ttu-id="6f255-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6f255-113">.NET Core 2.1</span></span> | <span data-ttu-id="6f255-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6f255-114">.NET Core 3.1</span></span> | <span data-ttu-id="6f255-115">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="6f255-115">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="6f255-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="6f255-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="6f255-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6f255-117">✔️ 2.1</span></span>        | <span data-ttu-id="6f255-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6f255-118">✔️ 3.1</span></span>        | <span data-ttu-id="6f255-119">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="6f255-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="6f255-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="6f255-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="6f255-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="6f255-121">✔️ 2.1</span></span>        | <span data-ttu-id="6f255-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="6f255-122">✔️ 3.1</span></span>        | <span data-ttu-id="6f255-123">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="6f255-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="6f255-124">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6f255-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="6f255-125">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="6f255-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="6f255-126">3.0</span><span class="sxs-lookup"><span data-stu-id="6f255-126">3.0</span></span>
- <span data-ttu-id="6f255-127">2.2</span><span class="sxs-lookup"><span data-stu-id="6f255-127">2.2</span></span>
- <span data-ttu-id="6f255-128">2.0</span><span class="sxs-lookup"><span data-stu-id="6f255-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="6f255-129">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="6f255-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="6f255-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="6f255-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="6f255-131">.NET Core 3,1 est disponible dans les référentiels de packages par défaut pour CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="6f255-131">.NET Core 3.1 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="6f255-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="6f255-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-31](includes/linux-install-31-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="6f255-133">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="6f255-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="6f255-134">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f255-134">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="6f255-135">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="6f255-135">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="6f255-136">Snap</span><span class="sxs-lookup"><span data-stu-id="6f255-136">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="6f255-137">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="6f255-137">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="6f255-138">Installation par script</span><span class="sxs-lookup"><span data-stu-id="6f255-138">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="6f255-139">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="6f255-139">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="6f255-140">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6f255-140">Next steps</span></span>

- [<span data-ttu-id="6f255-141">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="6f255-141">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
