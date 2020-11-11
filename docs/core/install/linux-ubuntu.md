---
title: Installer .NET sur Ubuntu-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 419bcf3ccd011cadba8f8c64e195d7dbdbf7e241
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507016"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="cb8c2-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cb8c2-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="cb8c2-104">.NET est pris en charge sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="cb8c2-105">Cet article explique comment installer .NET sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="cb8c2-106">Quand une version d’Ubuntu n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="cb8c2-107">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="cb8c2-108">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="cb8c2-108">Supported distributions</span></span>

<span data-ttu-id="cb8c2-109">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions d’Ubuntu sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="cb8c2-110">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Ubuntu](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="cb8c2-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="cb8c2-111">Une ✔️ indique que la version d’Ubuntu ou de .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="cb8c2-112">Une ❌ indique que la version d’Ubuntu ou de .net n’est pas prise en charge sur cette version d’Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="cb8c2-113">Quand une version d’Ubuntu et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="cb8c2-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cb8c2-114">Ubuntu</span></span>                   | <span data-ttu-id="cb8c2-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-115">.NET Core 2.1</span></span> | <span data-ttu-id="cb8c2-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-116">.NET Core 3.1</span></span> | <span data-ttu-id="cb8c2-117">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="cb8c2-118">✔️ [20,10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="cb8c2-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-119">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-120">✔️ 3.1</span></span>        | <span data-ttu-id="cb8c2-121">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-121">✔️ 5.0</span></span> |
| <span data-ttu-id="cb8c2-122">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="cb8c2-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-123">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-124">✔️ 3.1</span></span>        | <span data-ttu-id="cb8c2-125">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-125">✔️ 5.0</span></span> |
| <span data-ttu-id="cb8c2-126">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="cb8c2-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-127">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-128">✔️ 3.1</span></span>        | <span data-ttu-id="cb8c2-129">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-129">✔️ 5.0</span></span> |
| <span data-ttu-id="cb8c2-130">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="cb8c2-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-131">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-132">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-132">✔️ 3.1</span></span>        | <span data-ttu-id="cb8c2-133">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-133">❌ 5.0</span></span> |
| <span data-ttu-id="cb8c2-134">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="cb8c2-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-135">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-136">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-136">❌ 3.1</span></span>        | <span data-ttu-id="cb8c2-137">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-137">❌ 5.0</span></span> |
| <span data-ttu-id="cb8c2-138">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="cb8c2-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-139">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-140">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-140">✔️ 3.1</span></span>        | <span data-ttu-id="cb8c2-141">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-141">✔️ 5.0</span></span> |
| <span data-ttu-id="cb8c2-142">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="cb8c2-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-143">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-144">❌ 3.1</span></span>        | <span data-ttu-id="cb8c2-145">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-145">❌ 5.0</span></span> |
| <span data-ttu-id="cb8c2-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="cb8c2-147">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-147">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-148">❌ 3.1</span></span>        | <span data-ttu-id="cb8c2-149">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-149">❌ 5.0</span></span> |
| <span data-ttu-id="cb8c2-150">❌[16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="cb8c2-151">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-151">❌ 2.1</span></span>        | <span data-ttu-id="cb8c2-152">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-152">❌ 3.1</span></span>        | <span data-ttu-id="cb8c2-153">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-153">❌ 5.0</span></span> |
| <span data-ttu-id="cb8c2-154">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="cb8c2-155">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-155">✔️ 2.1</span></span>        | <span data-ttu-id="cb8c2-156">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-156">✔️ 3.1</span></span>        | <span data-ttu-id="cb8c2-157">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-157">✔️ 5.0</span></span> |

<span data-ttu-id="cb8c2-158">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="cb8c2-159">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="cb8c2-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="cb8c2-160">3.0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-160">3.0</span></span>
- <span data-ttu-id="cb8c2-161">2.2</span><span class="sxs-lookup"><span data-stu-id="cb8c2-161">2.2</span></span>
- <span data-ttu-id="cb8c2-162">2.0</span><span class="sxs-lookup"><span data-stu-id="cb8c2-162">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cb8c2-163">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="cb8c2-163">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="cb8c2-164">20,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="cb8c2-164">20.10 ✔️</span></span>

<span data-ttu-id="cb8c2-165">Les flux de packages .NET 5 et .NET Core 3,1 pour Ubuntu 20,10 présentent actuellement un problème.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-165">.NET 5 and .NET Core 3.1 package feeds for Ubuntu 20.10 currently have an issue.</span></span> <span data-ttu-id="cb8c2-166">Pour plus d’informations sur le problème, consultez [GitHub issue dotnet/Core # 5549](https://github.com/dotnet/core/issues/5549).</span><span class="sxs-lookup"><span data-stu-id="cb8c2-166">For more information about the issue, see [GitHub issue dotnet/core#5549](https://github.com/dotnet/core/issues/5549).</span></span> <span data-ttu-id="cb8c2-167">Cet article sera mis à jour lorsque le problème est résolu.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-167">This article will be updated when the issue is resolved.</span></span>

<span data-ttu-id="cb8c2-168">Pour installer .NET 5 ou .NET Core 3,1 sur Ubuntu 20,10, suivez les instructions pour [20,04](#2004-).</span><span class="sxs-lookup"><span data-stu-id="cb8c2-168">To install .NET 5 or .NET Core 3.1 on Ubuntu 20.10, follow the instructions for [20.04](#2004-).</span></span>

## <a name="2004-"></a><span data-ttu-id="cb8c2-169">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cb8c2-169">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="cb8c2-170">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="cb8c2-170">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="cb8c2-171">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="cb8c2-171">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="cb8c2-172">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="cb8c2-172">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="cb8c2-173">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cb8c2-173">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="cb8c2-174">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="cb8c2-174">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="cb8c2-175">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="cb8c2-175">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="cb8c2-176">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="cb8c2-176">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="cb8c2-177">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="cb8c2-177">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="cb8c2-178">Kit de développement logiciel (SDK) APT Update ou Runtime</span><span class="sxs-lookup"><span data-stu-id="cb8c2-178">APT update SDK or runtime</span></span>

<span data-ttu-id="cb8c2-179">Quand une nouvelle version de correctif est disponible pour .NET, vous pouvez simplement la mettre à niveau à l’aide de la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb8c2-179">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="cb8c2-180">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="cb8c2-180">APT troubleshooting</span></span>

<span data-ttu-id="cb8c2-181">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-181">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="cb8c2-182">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="cb8c2-182">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="cb8c2-183">Impossible d' \\ installer certains packages</span><span class="sxs-lookup"><span data-stu-id="cb8c2-183">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="cb8c2-184">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="cb8c2-184">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="cb8c2-185">Snap</span><span class="sxs-lookup"><span data-stu-id="cb8c2-185">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="cb8c2-186">Dépendances</span><span class="sxs-lookup"><span data-stu-id="cb8c2-186">Dependencies</span></span>

<span data-ttu-id="cb8c2-187">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-187">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="cb8c2-188">Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="cb8c2-188">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="cb8c2-189">libc6</span><span class="sxs-lookup"><span data-stu-id="cb8c2-189">libc6</span></span>
- <span data-ttu-id="cb8c2-190">libgcc1</span><span class="sxs-lookup"><span data-stu-id="cb8c2-190">libgcc1</span></span>
- <span data-ttu-id="cb8c2-191">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="cb8c2-191">libgssapi-krb5-2</span></span>
- <span data-ttu-id="cb8c2-192">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-192">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="cb8c2-193">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-193">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="cb8c2-194">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-194">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="cb8c2-195">libicu66 (pour 20. x)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-195">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="cb8c2-196">libssl 1.0.0 (pour 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-196">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="cb8c2-197">libssl 1.1 (pour 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-197">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="cb8c2-198">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="cb8c2-198">libstdc++6</span></span>
- <span data-ttu-id="cb8c2-199">zlib1g</span><span class="sxs-lookup"><span data-stu-id="cb8c2-199">zlib1g</span></span>

<span data-ttu-id="cb8c2-200">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="cb8c2-200">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="cb8c2-201">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="cb8c2-201">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="cb8c2-202">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-202">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="cb8c2-203">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="cb8c2-203">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="cb8c2-204">Installation par script</span><span class="sxs-lookup"><span data-stu-id="cb8c2-204">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="cb8c2-205">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="cb8c2-205">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="cb8c2-206">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cb8c2-206">Next steps</span></span>

- [<span data-ttu-id="cb8c2-207">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cb8c2-207">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
