---
title: Installer .NET Core sur Fedora-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 89a55ad2e9fd66d277d0c3eb6a07bd402574bd0a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538512"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-fedora"></a><span data-ttu-id="0d7a6-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur Fedora</span><span class="sxs-lookup"><span data-stu-id="0d7a6-103">Install .NET Core SDK or .NET Core Runtime on Fedora</span></span>

<span data-ttu-id="0d7a6-104">.NET Core est pris en charge sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-104">.NET Core is supported on Fedora.</span></span> <span data-ttu-id="0d7a6-105">Cet article explique comment installer .NET Core sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-105">This article describes how to install .NET Core on Fedora.</span></span> <span data-ttu-id="0d7a6-106">Quand une version de Fedora n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-106">When a Fedora version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="0d7a6-107">Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="0d7a6-108">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="0d7a6-108">Supported distributions</span></span>

<span data-ttu-id="0d7a6-109">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-109">The following table is a list of currently supported .NET Core releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="0d7a6-110">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core, ou la version de [Fedora atteint la fin de vie](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="0d7a6-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="0d7a6-111">Une ✔️ indique que la version de Fedora ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-111">A ✔️ indicates that the version of Fedora or .NET Core is still supported.</span></span>
- <span data-ttu-id="0d7a6-112">Une ❌ indique que la version de Fedora ou de .net Core n’est pas prise en charge sur cette version de Fedora.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-112">A ❌ indicates that the version of Fedora or .NET Core isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="0d7a6-113">Quand une version de Fedora et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-113">When both a version of Fedora and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="0d7a6-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="0d7a6-114">Fedora</span></span>                   | <span data-ttu-id="0d7a6-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-115">.NET Core 2.1</span></span> | <span data-ttu-id="0d7a6-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-116">.NET Core 3.1</span></span> | <span data-ttu-id="0d7a6-117">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="0d7a6-118">✔️ [32](linux-fedora.md#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-118">✔️ [32](linux-fedora.md#fedora-32-)</span></span> | <span data-ttu-id="0d7a6-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-119">✔️ 2.1</span></span>        | <span data-ttu-id="0d7a6-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-120">✔️ 3.1</span></span>        | <span data-ttu-id="0d7a6-121">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="0d7a6-122">✔️ [31](linux-fedora.md#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-122">✔️ [31](linux-fedora.md#fedora-31-)</span></span> | <span data-ttu-id="0d7a6-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-123">✔️ 2.1</span></span>        | <span data-ttu-id="0d7a6-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-124">✔️ 3.1</span></span>        | <span data-ttu-id="0d7a6-125">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="0d7a6-126">❌[30](linux-fedora.md#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-126">❌ [30](linux-fedora.md#fedora-30-)</span></span> | <span data-ttu-id="0d7a6-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-127">✔️ 2.1</span></span>        | <span data-ttu-id="0d7a6-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-128">✔️ 3.1</span></span>        | <span data-ttu-id="0d7a6-129">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="0d7a6-130">❌[29](linux-fedora.md#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-130">❌ [29](linux-fedora.md#fedora-29-)</span></span> | <span data-ttu-id="0d7a6-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-131">✔️ 2.1</span></span>        | <span data-ttu-id="0d7a6-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-132">✔️ 3.1</span></span>        | <span data-ttu-id="0d7a6-133">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="0d7a6-134">❌[28](linux-fedora.md#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-134">❌ [28](linux-fedora.md#fedora-28-)</span></span> | <span data-ttu-id="0d7a6-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-135">✔️ 2.1</span></span>        | <span data-ttu-id="0d7a6-136">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-136">❌ 3.1</span></span>        | <span data-ttu-id="0d7a6-137">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-137">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="0d7a6-138">❌[27](linux-fedora.md#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="0d7a6-138">❌ [27](linux-fedora.md#fedora-27-)</span></span> | <span data-ttu-id="0d7a6-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-139">✔️ 2.1</span></span>        | <span data-ttu-id="0d7a6-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="0d7a6-140">❌ 3.1</span></span>        | <span data-ttu-id="0d7a6-141">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-141">❌ 5.0 Preview</span></span> |

<span data-ttu-id="0d7a6-142">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-142">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="0d7a6-143">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="0d7a6-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0d7a6-144">3.0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-144">3.0</span></span>
- <span data-ttu-id="0d7a6-145">2.2</span><span class="sxs-lookup"><span data-stu-id="0d7a6-145">2.2</span></span>
- <span data-ttu-id="0d7a6-146">2.0</span><span class="sxs-lookup"><span data-stu-id="0d7a6-146">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0d7a6-147">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="0d7a6-147">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-32-"></a><span data-ttu-id="0d7a6-148">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="0d7a6-148">Fedora 32 ✔️</span></span>

<span data-ttu-id="0d7a6-149">.NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-149">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="0d7a6-150">Fedora 31 ✔️</span><span class="sxs-lookup"><span data-stu-id="0d7a6-150">Fedora 31 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="0d7a6-151">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="0d7a6-151">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="0d7a6-152">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="0d7a6-152">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="0d7a6-153">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="0d7a6-153">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="0d7a6-154">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="0d7a6-154">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0d7a6-155">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="0d7a6-155">Troubleshoot the package manager</span></span>

<span data-ttu-id="0d7a6-156">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0d7a6-156">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="0d7a6-157">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="0d7a6-157">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="0d7a6-158">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="0d7a6-158">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="0d7a6-159">Snap</span><span class="sxs-lookup"><span data-stu-id="0d7a6-159">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="0d7a6-160">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="0d7a6-160">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="0d7a6-161">Installation par script</span><span class="sxs-lookup"><span data-stu-id="0d7a6-161">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="0d7a6-162">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="0d7a6-162">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="0d7a6-163">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0d7a6-163">Next steps</span></span>

- [<span data-ttu-id="0d7a6-164">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0d7a6-164">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
