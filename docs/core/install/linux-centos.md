---
title: Installer .NET sur CentOS-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur CentOS.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: d0f5d38de0f505d62f2a35c5d1c3f7161c91a96b
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507093"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="97984-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur CentOS</span><span class="sxs-lookup"><span data-stu-id="97984-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="97984-104">.NET est pris en charge sur CentOS.</span><span class="sxs-lookup"><span data-stu-id="97984-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="97984-105">Cet article explique comment installer .NET sur CentOS.</span><span class="sxs-lookup"><span data-stu-id="97984-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="97984-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="97984-106">Supported distributions</span></span>

<span data-ttu-id="97984-107">Le tableau suivant répertorie les versions .NET actuellement prises en charge sur CentOS 7 et CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="97984-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="97984-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de CentOS ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="97984-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="97984-109">Une ✔️ indique que la version de CentOS ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="97984-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="97984-110">Une ❌ indique que la version de CentOS ou .net n’est pas prise en charge sur cette version de CentOS.</span><span class="sxs-lookup"><span data-stu-id="97984-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="97984-111">Quand une version de CentOS et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="97984-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="97984-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="97984-112">CentOS</span></span>                   | <span data-ttu-id="97984-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="97984-113">.NET Core 2.1</span></span> | <span data-ttu-id="97984-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="97984-114">.NET Core 3.1</span></span> | <span data-ttu-id="97984-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="97984-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="97984-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="97984-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="97984-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="97984-117">✔️ 2.1</span></span>        | <span data-ttu-id="97984-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="97984-118">✔️ 3.1</span></span>        | <span data-ttu-id="97984-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="97984-119">✔️ 5.0</span></span> |
| <span data-ttu-id="97984-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="97984-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="97984-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="97984-121">✔️ 2.1</span></span>        | <span data-ttu-id="97984-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="97984-122">✔️ 3.1</span></span>        | <span data-ttu-id="97984-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="97984-123">✔️ 5.0</span></span> |

<span data-ttu-id="97984-124">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="97984-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="97984-125">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="97984-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="97984-126">3.0</span><span class="sxs-lookup"><span data-stu-id="97984-126">3.0</span></span>
- <span data-ttu-id="97984-127">2.2</span><span class="sxs-lookup"><span data-stu-id="97984-127">2.2</span></span>
- <span data-ttu-id="97984-128">2.0</span><span class="sxs-lookup"><span data-stu-id="97984-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="97984-129">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="97984-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="97984-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="97984-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="97984-131">.NET 5,0 est disponible dans les référentiels de packages par défaut pour CentOS 8.</span><span class="sxs-lookup"><span data-stu-id="97984-131">.NET 5.0 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="97984-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="97984-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="97984-133">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="97984-133">Troubleshoot the package manager</span></span>

<span data-ttu-id="97984-134">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="97984-134">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="97984-135">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="97984-135">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="97984-136">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="97984-136">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="97984-137">Snap</span><span class="sxs-lookup"><span data-stu-id="97984-137">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="97984-138">Dépendances</span><span class="sxs-lookup"><span data-stu-id="97984-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="97984-139">Installation par script</span><span class="sxs-lookup"><span data-stu-id="97984-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="97984-140">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="97984-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="97984-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="97984-141">Next steps</span></span>

- [<span data-ttu-id="97984-142">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="97984-142">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
