---
title: Installer .NET sur Ubuntu-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 22ce3379e028f065528e1f507a2d8c1ae598f0e8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031842"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="f82b8-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f82b8-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="f82b8-104">.NET est pris en charge sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f82b8-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="f82b8-105">Cet article explique comment installer .NET sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f82b8-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="f82b8-106">Quand une version d’Ubuntu n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="f82b8-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="f82b8-107">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="f82b8-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="f82b8-108">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="f82b8-108">Supported distributions</span></span>

<span data-ttu-id="f82b8-109">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions d’Ubuntu sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="f82b8-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="f82b8-110">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Ubuntu](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="f82b8-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="f82b8-111">Une ✔️ indique que la version d’Ubuntu ou de .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f82b8-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="f82b8-112">Une ❌ indique que la version d’Ubuntu ou de .net n’est pas prise en charge sur cette version d’Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f82b8-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="f82b8-113">Quand une version d’Ubuntu et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="f82b8-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="f82b8-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f82b8-114">Ubuntu</span></span>                   | <span data-ttu-id="f82b8-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f82b8-115">.NET Core 2.1</span></span> | <span data-ttu-id="f82b8-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f82b8-116">.NET Core 3.1</span></span> | <span data-ttu-id="f82b8-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="f82b8-118">✔️ [20,10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="f82b8-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-119">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-120">✔️ 3.1</span></span>        | <span data-ttu-id="f82b8-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-121">✔️ 5.0</span></span> |
| <span data-ttu-id="f82b8-122">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="f82b8-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-123">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-124">✔️ 3.1</span></span>        | <span data-ttu-id="f82b8-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-125">✔️ 5.0</span></span> |
| <span data-ttu-id="f82b8-126">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="f82b8-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-127">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-128">✔️ 3.1</span></span>        | <span data-ttu-id="f82b8-129">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-129">✔️ 5.0</span></span> |
| <span data-ttu-id="f82b8-130">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="f82b8-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-131">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-132">✔️ 3.1</span></span>        | <span data-ttu-id="f82b8-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-133">❌ 5.0</span></span> |
| <span data-ttu-id="f82b8-134">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="f82b8-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-135">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-136">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-136">❌ 3.1</span></span>        | <span data-ttu-id="f82b8-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-137">❌ 5.0</span></span> |
| <span data-ttu-id="f82b8-138">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="f82b8-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-139">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-140">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-140">✔️ 3.1</span></span>        | <span data-ttu-id="f82b8-141">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-141">✔️ 5.0</span></span> |
| <span data-ttu-id="f82b8-142">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="f82b8-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-143">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-144">❌ 3.1</span></span>        | <span data-ttu-id="f82b8-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-145">❌ 5.0</span></span> |
| <span data-ttu-id="f82b8-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="f82b8-147">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-147">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-148">❌ 3.1</span></span>        | <span data-ttu-id="f82b8-149">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-149">❌ 5.0</span></span> |
| <span data-ttu-id="f82b8-150">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="f82b8-151">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-151">❌ 2.1</span></span>        | <span data-ttu-id="f82b8-152">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-152">❌ 3.1</span></span>        | <span data-ttu-id="f82b8-153">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-153">❌ 5.0</span></span> |
| <span data-ttu-id="f82b8-154">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="f82b8-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="f82b8-155">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-155">✔️ 2.1</span></span>        | <span data-ttu-id="f82b8-156">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="f82b8-156">✔️ 3.1</span></span>        | <span data-ttu-id="f82b8-157">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="f82b8-157">✔️ 5.0</span></span> |

<span data-ttu-id="f82b8-158">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="f82b8-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="f82b8-159">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="f82b8-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f82b8-160">3.0</span><span class="sxs-lookup"><span data-stu-id="f82b8-160">3.0</span></span>
- <span data-ttu-id="f82b8-161">2.2</span><span class="sxs-lookup"><span data-stu-id="f82b8-161">2.2</span></span>
- <span data-ttu-id="f82b8-162">2.0</span><span class="sxs-lookup"><span data-stu-id="f82b8-162">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="f82b8-163">Supprimer les versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="f82b8-163">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f82b8-164">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="f82b8-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="f82b8-165">20,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="f82b8-165">20.10 ✔️</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f82b8-166">.NET Core 2,1 n’est pas encore disponible dans le flux de package.</span><span class="sxs-lookup"><span data-stu-id="f82b8-166">.NET Core 2.1 isn't yet available in the package feed.</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="f82b8-167">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="f82b8-167">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="f82b8-168">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="f82b8-168">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="f82b8-169">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="f82b8-169">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="f82b8-170">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="f82b8-170">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="f82b8-171">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="f82b8-171">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="f82b8-172">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="f82b8-172">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="f82b8-173">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="f82b8-173">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="f82b8-174">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="f82b8-174">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="f82b8-175">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="f82b8-175">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="f82b8-176">Kit de développement logiciel (SDK) APT Update ou Runtime</span><span class="sxs-lookup"><span data-stu-id="f82b8-176">APT update SDK or runtime</span></span>

<span data-ttu-id="f82b8-177">Quand une nouvelle version de correctif est disponible pour .NET, vous pouvez simplement la mettre à niveau à l’aide de la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f82b8-177">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="f82b8-178">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="f82b8-178">APT troubleshooting</span></span>

<span data-ttu-id="f82b8-179">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="f82b8-179">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="f82b8-180">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="f82b8-180">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="f82b8-181">Impossible d' \\ installer certains packages</span><span class="sxs-lookup"><span data-stu-id="f82b8-181">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="f82b8-182">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="f82b8-182">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="f82b8-183">Snap</span><span class="sxs-lookup"><span data-stu-id="f82b8-183">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="f82b8-184">Dépendances</span><span class="sxs-lookup"><span data-stu-id="f82b8-184">Dependencies</span></span>

<span data-ttu-id="f82b8-185">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="f82b8-185">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="f82b8-186">Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="f82b8-186">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="f82b8-187">libc6</span><span class="sxs-lookup"><span data-stu-id="f82b8-187">libc6</span></span>
- <span data-ttu-id="f82b8-188">libgcc1</span><span class="sxs-lookup"><span data-stu-id="f82b8-188">libgcc1</span></span>
- <span data-ttu-id="f82b8-189">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="f82b8-189">libgssapi-krb5-2</span></span>
- <span data-ttu-id="f82b8-190">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="f82b8-190">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="f82b8-191">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="f82b8-191">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="f82b8-192">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="f82b8-192">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="f82b8-193">libicu66 (pour 20. x)</span><span class="sxs-lookup"><span data-stu-id="f82b8-193">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="f82b8-194">libssl 1.0.0 (pour 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="f82b8-194">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="f82b8-195">libssl 1.1 (pour 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="f82b8-195">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="f82b8-196">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="f82b8-196">libstdc++6</span></span>
- <span data-ttu-id="f82b8-197">zlib1g</span><span class="sxs-lookup"><span data-stu-id="f82b8-197">zlib1g</span></span>

<span data-ttu-id="f82b8-198">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="f82b8-198">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="f82b8-199">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="f82b8-199">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="f82b8-200">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="f82b8-200">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="f82b8-201">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="f82b8-201">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="f82b8-202">Installation par script</span><span class="sxs-lookup"><span data-stu-id="f82b8-202">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f82b8-203">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="f82b8-203">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f82b8-204">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f82b8-204">Next steps</span></span>

- [<span data-ttu-id="f82b8-205">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f82b8-205">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
