---
title: Installer .NET Core sur SLES-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: e1a2490c1d653eb07aebdd51e34e1bf462906482
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324699"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="06b7d-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur SLES</span><span class="sxs-lookup"><span data-stu-id="06b7d-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="06b7d-104">.NET Core est pris en charge sur SLES.</span><span class="sxs-lookup"><span data-stu-id="06b7d-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="06b7d-105">Cet article explique comment installer .NET Core sur SLES.</span><span class="sxs-lookup"><span data-stu-id="06b7d-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="06b7d-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="06b7d-106">Supported distributions</span></span>

<span data-ttu-id="06b7d-107">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur SLES 12 SP2 et SLES 15.</span><span class="sxs-lookup"><span data-stu-id="06b7d-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="06b7d-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de SLES ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="06b7d-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="06b7d-109">Une ✔️ indique que la version de SLES ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="06b7d-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="06b7d-110">Une ❌ indique que la version de SLES ou de .net Core n’est pas prise en charge sur cette version SLES.</span><span class="sxs-lookup"><span data-stu-id="06b7d-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="06b7d-111">Quand une version de SLES et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="06b7d-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="06b7d-112">SLES</span><span class="sxs-lookup"><span data-stu-id="06b7d-112">SLES</span></span>                   | <span data-ttu-id="06b7d-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="06b7d-113">.NET Core 2.1</span></span> | <span data-ttu-id="06b7d-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="06b7d-114">.NET Core 3.1</span></span> | <span data-ttu-id="06b7d-115">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="06b7d-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="06b7d-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="06b7d-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="06b7d-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="06b7d-117">✔️ 2.1</span></span>        | <span data-ttu-id="06b7d-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="06b7d-118">✔️ 3.1</span></span>        | <span data-ttu-id="06b7d-119">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="06b7d-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="06b7d-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="06b7d-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="06b7d-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="06b7d-121">✔️ 2.1</span></span>        | <span data-ttu-id="06b7d-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="06b7d-122">✔️ 3.1</span></span>        | <span data-ttu-id="06b7d-123">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="06b7d-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="06b7d-124">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="06b7d-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="06b7d-125">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="06b7d-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="06b7d-126">3.0</span><span class="sxs-lookup"><span data-stu-id="06b7d-126">3.0</span></span>
- <span data-ttu-id="06b7d-127">2.2</span><span class="sxs-lookup"><span data-stu-id="06b7d-127">2.2</span></span>
- <span data-ttu-id="06b7d-128">2.0</span><span class="sxs-lookup"><span data-stu-id="06b7d-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="06b7d-129">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="06b7d-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="06b7d-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="06b7d-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="06b7d-131">Actuellement, le package d’installation du référentiel SLES 15 Microsoft installe le fichier *Microsoft-prod. référentiel* dans le répertoire incorrect, empêchant ainsi zypper de trouver les packages .net core.</span><span class="sxs-lookup"><span data-stu-id="06b7d-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="06b7d-132">Pour résoudre ce problème, créez un lien symbolique dans le répertoire approprié.</span><span class="sxs-lookup"><span data-stu-id="06b7d-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="06b7d-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="06b7d-133">SLES 12 ✔️</span></span>

<span data-ttu-id="06b7d-134">.NET Core requiert SP2 au minimum pour la famille SLES 12.</span><span class="sxs-lookup"><span data-stu-id="06b7d-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="06b7d-135">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="06b7d-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="06b7d-136">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06b7d-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="06b7d-137">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="06b7d-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="06b7d-138">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="06b7d-138">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="06b7d-139">Installation par script</span><span class="sxs-lookup"><span data-stu-id="06b7d-139">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="06b7d-140">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="06b7d-140">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="06b7d-141">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="06b7d-141">Next steps</span></span>

- [<span data-ttu-id="06b7d-142">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="06b7d-142">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
