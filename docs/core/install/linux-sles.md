---
title: Installer .NET Core sur SLES-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur SLES.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: b2eab6a0305d492e37e1b33d02be43ca41d42b6f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603033"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="a4977-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur SLES</span><span class="sxs-lookup"><span data-stu-id="a4977-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="a4977-104">.NET Core est pris en charge sur SLES.</span><span class="sxs-lookup"><span data-stu-id="a4977-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="a4977-105">Cet article explique comment installer .NET Core sur SLES.</span><span class="sxs-lookup"><span data-stu-id="a4977-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="a4977-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="a4977-106">Supported distributions</span></span>

<span data-ttu-id="a4977-107">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur SLES 12 SP2 et SLES 15.</span><span class="sxs-lookup"><span data-stu-id="a4977-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="a4977-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de SLES ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="a4977-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="a4977-109">Une ✔️ indique que la version de SLES ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="a4977-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="a4977-110">Une ❌ indique que la version de SLES ou de .net Core n’est pas prise en charge sur cette version SLES.</span><span class="sxs-lookup"><span data-stu-id="a4977-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="a4977-111">Quand une version de SLES et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="a4977-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="a4977-112">SLES</span><span class="sxs-lookup"><span data-stu-id="a4977-112">SLES</span></span>                   | <span data-ttu-id="a4977-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a4977-113">.NET Core 2.1</span></span> | <span data-ttu-id="a4977-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a4977-114">.NET Core 3.1</span></span> | <span data-ttu-id="a4977-115">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="a4977-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="a4977-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="a4977-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="a4977-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="a4977-117">✔️ 2.1</span></span>        | <span data-ttu-id="a4977-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="a4977-118">✔️ 3.1</span></span>        | <span data-ttu-id="a4977-119">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="a4977-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="a4977-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="a4977-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="a4977-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="a4977-121">✔️ 2.1</span></span>        | <span data-ttu-id="a4977-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="a4977-122">✔️ 3.1</span></span>        | <span data-ttu-id="a4977-123">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="a4977-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="a4977-124">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="a4977-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="a4977-125">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="a4977-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="a4977-126">3.0</span><span class="sxs-lookup"><span data-stu-id="a4977-126">3.0</span></span>
- <span data-ttu-id="a4977-127">2.2</span><span class="sxs-lookup"><span data-stu-id="a4977-127">2.2</span></span>
- <span data-ttu-id="a4977-128">2.0</span><span class="sxs-lookup"><span data-stu-id="a4977-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a4977-129">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="a4977-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="a4977-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="a4977-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="a4977-131">Actuellement, le package d’installation du référentiel SLES 15 Microsoft installe le fichier *Microsoft-prod. référentiel* dans le répertoire incorrect, empêchant ainsi zypper de trouver les packages .net core.</span><span class="sxs-lookup"><span data-stu-id="a4977-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="a4977-132">Pour résoudre ce problème, créez un lien symbolique dans le répertoire approprié.</span><span class="sxs-lookup"><span data-stu-id="a4977-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="a4977-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="a4977-133">SLES 12 ✔️</span></span>

<span data-ttu-id="a4977-134">.NET Core requiert SP2 au minimum pour la famille SLES 12.</span><span class="sxs-lookup"><span data-stu-id="a4977-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a4977-135">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="a4977-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="a4977-136">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a4977-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="a4977-137">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="a4977-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="a4977-138">Snap</span><span class="sxs-lookup"><span data-stu-id="a4977-138">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="a4977-139">Dépendances</span><span class="sxs-lookup"><span data-stu-id="a4977-139">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="a4977-140">Installation par script</span><span class="sxs-lookup"><span data-stu-id="a4977-140">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="a4977-141">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="a4977-141">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="a4977-142">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a4977-142">Next steps</span></span>

- [<span data-ttu-id="a4977-143">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a4977-143">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
