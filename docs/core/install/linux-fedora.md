---
title: Installer .NET sur Fedora-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 9e96773e30fb8ee395e37dca7a4794cd42359bb2
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594609"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="8a3fa-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Fedora</span><span class="sxs-lookup"><span data-stu-id="8a3fa-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="8a3fa-104">.NET est pris en charge sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="8a3fa-105">Cet article explique comment installer .NET sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="8a3fa-106">Quand une version de Fedora n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="8a3fa-107">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="8a3fa-108">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="8a3fa-108">Supported distributions</span></span>

<span data-ttu-id="8a3fa-109">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="8a3fa-110">Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Fedora](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="8a3fa-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="8a3fa-111">Une ✔️ indique que la version de Fedora ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="8a3fa-112">Une ❌ indique que la version de Fedora ou .net n’est pas prise en charge sur cette version de Fedora.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="8a3fa-113">Quand une version de Fedora et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="8a3fa-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="8a3fa-114">Fedora</span></span>               | <span data-ttu-id="8a3fa-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-115">.NET Core 2.1</span></span> | <span data-ttu-id="8a3fa-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-116">.NET Core 3.1</span></span> | <span data-ttu-id="8a3fa-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="8a3fa-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="8a3fa-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-119">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-120">✔️ 3.1</span></span>        | <span data-ttu-id="8a3fa-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-121">✔️ 5.0</span></span> |
| <span data-ttu-id="8a3fa-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="8a3fa-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-123">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-124">✔️ 3.1</span></span>        | <span data-ttu-id="8a3fa-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-125">✔️ 5.0</span></span> |
| <span data-ttu-id="8a3fa-126">❌[31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="8a3fa-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-127">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-128">✔️ 3.1</span></span>        | <span data-ttu-id="8a3fa-129">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-129">❌ 5.0</span></span> |
| <span data-ttu-id="8a3fa-130">❌ [30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="8a3fa-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-131">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-132">✔️ 3.1</span></span>        | <span data-ttu-id="8a3fa-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-133">❌ 5.0</span></span> |
| <span data-ttu-id="8a3fa-134">❌[29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="8a3fa-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-135">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-136">✔️ 3.1</span></span>        | <span data-ttu-id="8a3fa-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-137">❌ 5.0</span></span> |
| <span data-ttu-id="8a3fa-138">❌[28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="8a3fa-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-139">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-140">❌ 3.1</span></span>        | <span data-ttu-id="8a3fa-141">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-141">❌ 5.0</span></span> |
| <span data-ttu-id="8a3fa-142">❌[27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="8a3fa-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="8a3fa-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-143">✔️ 2.1</span></span>        | <span data-ttu-id="8a3fa-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="8a3fa-144">❌ 3.1</span></span>        | <span data-ttu-id="8a3fa-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-145">❌ 5.0</span></span> |

<span data-ttu-id="8a3fa-146">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="8a3fa-147">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="8a3fa-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="8a3fa-148">3.0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-148">3.0</span></span>
- <span data-ttu-id="8a3fa-149">2.2</span><span class="sxs-lookup"><span data-stu-id="8a3fa-149">2.2</span></span>
- <span data-ttu-id="8a3fa-150">2.0</span><span class="sxs-lookup"><span data-stu-id="8a3fa-150">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="8a3fa-151">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="8a3fa-151">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="8a3fa-152">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="8a3fa-152">Fedora 33 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="8a3fa-153">.NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 33.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-153">.NET Core 3.1 is available in the default package repositories for Fedora 33.</span></span> <span data-ttu-id="8a3fa-154">Pour installer .NET Core 3,1, utilisez la `dnf install` commande avec le package approprié, tel que `aspnetcore-runtime-3.1` ou `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="8a3fa-154">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="8a3fa-155">.NET 5,0 n’est pas encore disponible dans les référentiels de packages par défaut.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-155">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="8a3fa-156">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="8a3fa-156">Fedora 32 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="8a3fa-157">.NET Core 3,1 est disponible dans les référentiels de packages par défaut pour Fedora 32.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-157">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span> <span data-ttu-id="8a3fa-158">Pour installer .NET Core 3,1, utilisez la `dnf install` commande avec le package approprié, tel que `aspnetcore-runtime-3.1` ou `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="8a3fa-158">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="8a3fa-159">.NET 5,0 n’est pas encore disponible dans les référentiels de packages par défaut.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-159">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="8a3fa-160">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="8a3fa-160">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="8a3fa-161">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="8a3fa-161">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="8a3fa-162">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="8a3fa-162">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="8a3fa-163">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="8a3fa-163">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="8a3fa-164">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="8a3fa-164">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="8a3fa-165">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="8a3fa-165">Troubleshoot the package manager</span></span>

<span data-ttu-id="8a3fa-166">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a3fa-166">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="8a3fa-167">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="8a3fa-167">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="8a3fa-168">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="8a3fa-168">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="8a3fa-169">Snap</span><span class="sxs-lookup"><span data-stu-id="8a3fa-169">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="8a3fa-170">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="8a3fa-170">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="8a3fa-171">Installation par script</span><span class="sxs-lookup"><span data-stu-id="8a3fa-171">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="8a3fa-172">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="8a3fa-172">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="8a3fa-173">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8a3fa-173">Next steps</span></span>

- [<span data-ttu-id="8a3fa-174">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="8a3fa-174">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
