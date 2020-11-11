---
title: Installer .NET sur Fedora-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: d5b5886f8b29e0f8e935850686cc84f78c55be02
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507064"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="540c6-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Fedora</span><span class="sxs-lookup"><span data-stu-id="540c6-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="540c6-104">.NET est pris en charge sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="540c6-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="540c6-105">Cet article explique comment installer .NET sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="540c6-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="540c6-106">Quand une version de Fedora n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="540c6-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="540c6-107">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="540c6-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="540c6-108">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="540c6-108">Supported distributions</span></span>

<span data-ttu-id="540c6-109">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="540c6-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="540c6-110">Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Fedora](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="540c6-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="540c6-111">Une ✔️ indique que la version de Fedora ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="540c6-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="540c6-112">Une ❌ indique que la version de Fedora ou .net n’est pas prise en charge sur cette version de Fedora.</span><span class="sxs-lookup"><span data-stu-id="540c6-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="540c6-113">Quand une version de Fedora et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="540c6-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="540c6-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="540c6-114">Fedora</span></span>               | <span data-ttu-id="540c6-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="540c6-115">.NET Core 2.1</span></span> | <span data-ttu-id="540c6-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="540c6-116">.NET Core 3.1</span></span> | <span data-ttu-id="540c6-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="540c6-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="540c6-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="540c6-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-119">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-120">✔️ 3.1</span></span>        | <span data-ttu-id="540c6-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-121">✔️ 5.0</span></span> |
| <span data-ttu-id="540c6-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="540c6-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="540c6-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-123">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-124">✔️ 3.1</span></span>        | <span data-ttu-id="540c6-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-125">✔️ 5.0</span></span> |
| <span data-ttu-id="540c6-126">❌[31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="540c6-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="540c6-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-127">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-128">✔️ 3.1</span></span>        | <span data-ttu-id="540c6-129">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-129">❌ 5.0</span></span> |
| <span data-ttu-id="540c6-130">❌[30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="540c6-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="540c6-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-131">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-132">✔️ 3.1</span></span>        | <span data-ttu-id="540c6-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-133">❌ 5.0</span></span> |
| <span data-ttu-id="540c6-134">❌[29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="540c6-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="540c6-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-135">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-136">✔️ 3.1</span></span>        | <span data-ttu-id="540c6-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-137">❌ 5.0</span></span> |
| <span data-ttu-id="540c6-138">❌[28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="540c6-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="540c6-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-139">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-140">❌ 3.1</span></span>        | <span data-ttu-id="540c6-141">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-141">❌ 5.0</span></span> |
| <span data-ttu-id="540c6-142">❌[27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="540c6-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="540c6-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="540c6-143">✔️ 2.1</span></span>        | <span data-ttu-id="540c6-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="540c6-144">❌ 3.1</span></span>        | <span data-ttu-id="540c6-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="540c6-145">❌ 5.0</span></span> |

<span data-ttu-id="540c6-146">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="540c6-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="540c6-147">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="540c6-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="540c6-148">3.0</span><span class="sxs-lookup"><span data-stu-id="540c6-148">3.0</span></span>
- <span data-ttu-id="540c6-149">2.2</span><span class="sxs-lookup"><span data-stu-id="540c6-149">2.2</span></span>
- <span data-ttu-id="540c6-150">2.0</span><span class="sxs-lookup"><span data-stu-id="540c6-150">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="540c6-151">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="540c6-151">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="540c6-152">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="540c6-152">Fedora 33 ✔️</span></span>

<span data-ttu-id="540c6-153">.NET 5 et .NET Core 3,1 sont disponibles dans les référentiels de packages par défaut pour Fedora 33.</span><span class="sxs-lookup"><span data-stu-id="540c6-153">.NET 5 and .NET Core 3.1 are available in the default package repositories for Fedora 33.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="540c6-154">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="540c6-154">Fedora 32 ✔️</span></span>

<span data-ttu-id="540c6-155">.NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="540c6-155">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="540c6-156">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="540c6-156">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="540c6-157">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="540c6-157">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="540c6-158">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="540c6-158">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="540c6-159">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="540c6-159">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="540c6-160">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="540c6-160">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="540c6-161">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="540c6-161">Troubleshoot the package manager</span></span>

<span data-ttu-id="540c6-162">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="540c6-162">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="540c6-163">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="540c6-163">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="540c6-164">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="540c6-164">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="540c6-165">Snap</span><span class="sxs-lookup"><span data-stu-id="540c6-165">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="540c6-166">Dépendances</span><span class="sxs-lookup"><span data-stu-id="540c6-166">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="540c6-167">Installation par script</span><span class="sxs-lookup"><span data-stu-id="540c6-167">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="540c6-168">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="540c6-168">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="540c6-169">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="540c6-169">Next steps</span></span>

- [<span data-ttu-id="540c6-170">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="540c6-170">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
