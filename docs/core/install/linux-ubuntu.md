---
title: Installer .NET sur Ubuntu-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 14e5e9548d4aa09a586e2038f3e35a489ee65cd2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970762"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="d83a1-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d83a1-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="d83a1-104">.NET est pris en charge sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d83a1-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="d83a1-105">Cet article explique comment installer .NET sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d83a1-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="d83a1-106">Quand une version d’Ubuntu n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="d83a1-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="d83a1-107">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="d83a1-107">Supported distributions</span></span>

<span data-ttu-id="d83a1-108">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions d’Ubuntu sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="d83a1-108">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="d83a1-109">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Ubuntu](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="d83a1-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="d83a1-110">Une ✔️ indique que la version d’Ubuntu ou de .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="d83a1-110">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="d83a1-111">Une ❌ indique que la version d’Ubuntu ou de .net n’est pas prise en charge sur cette version d’Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d83a1-111">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="d83a1-112">Quand une version d’Ubuntu et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="d83a1-112">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="d83a1-113">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="d83a1-113">Ubuntu</span></span>                   | <span data-ttu-id="d83a1-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d83a1-114">.NET Core 2.1</span></span> | <span data-ttu-id="d83a1-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="d83a1-115">.NET Core 3.1</span></span> | <span data-ttu-id="d83a1-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="d83a1-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="d83a1-117">✔️ [20,10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-117">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="d83a1-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-118">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-119">✔️ 3.1</span></span>        | <span data-ttu-id="d83a1-120">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-120">✔️ 5.0</span></span> |
| <span data-ttu-id="d83a1-121">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-121">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="d83a1-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-122">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-123">✔️ 3.1</span></span>        | <span data-ttu-id="d83a1-124">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-124">✔️ 5.0</span></span> |
| <span data-ttu-id="d83a1-125">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-125">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="d83a1-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-126">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-127">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-127">✔️ 3.1</span></span>        | <span data-ttu-id="d83a1-128">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-128">✔️ 5.0</span></span> |
| <span data-ttu-id="d83a1-129">❌[19,04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-129">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="d83a1-130">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-130">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-131">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-131">✔️ 3.1</span></span>        | <span data-ttu-id="d83a1-132">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-132">❌ 5.0</span></span> |
| <span data-ttu-id="d83a1-133">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-133">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="d83a1-134">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-134">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-135">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-135">❌ 3.1</span></span>        | <span data-ttu-id="d83a1-136">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-136">❌ 5.0</span></span> |
| <span data-ttu-id="d83a1-137">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-137">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="d83a1-138">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-138">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-139">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-139">✔️ 3.1</span></span>        | <span data-ttu-id="d83a1-140">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-140">✔️ 5.0</span></span> |
| <span data-ttu-id="d83a1-141">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-141">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="d83a1-142">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-142">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-143">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-143">❌ 3.1</span></span>        | <span data-ttu-id="d83a1-144">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-144">❌ 5.0</span></span> |
| <span data-ttu-id="d83a1-145">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-145">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="d83a1-146">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-146">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-147">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-147">❌ 3.1</span></span>        | <span data-ttu-id="d83a1-148">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-148">❌ 5.0</span></span> |
| <span data-ttu-id="d83a1-149">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-149">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="d83a1-150">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-150">❌ 2.1</span></span>        | <span data-ttu-id="d83a1-151">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-151">❌ 3.1</span></span>        | <span data-ttu-id="d83a1-152">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-152">❌ 5.0</span></span> |
| <span data-ttu-id="d83a1-153">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="d83a1-153">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="d83a1-154">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-154">✔️ 2.1</span></span>        | <span data-ttu-id="d83a1-155">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="d83a1-155">✔️ 3.1</span></span>        | <span data-ttu-id="d83a1-156">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="d83a1-156">✔️ 5.0</span></span> |

<span data-ttu-id="d83a1-157">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="d83a1-157">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="d83a1-158">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="d83a1-158">The downloads for these still remain published:</span></span>

- <span data-ttu-id="d83a1-159">3.0</span><span class="sxs-lookup"><span data-stu-id="d83a1-159">3.0</span></span>
- <span data-ttu-id="d83a1-160">2.2</span><span class="sxs-lookup"><span data-stu-id="d83a1-160">2.2</span></span>
- <span data-ttu-id="d83a1-161">2.0</span><span class="sxs-lookup"><span data-stu-id="d83a1-161">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="d83a1-162">Supprimer les versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="d83a1-162">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="2010-"></a><span data-ttu-id="d83a1-163">20,10 ✔️</span><span class="sxs-lookup"><span data-stu-id="d83a1-163">20.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="d83a1-164">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="d83a1-164">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="d83a1-165">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="d83a1-165">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="d83a1-166">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="d83a1-166">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="d83a1-167">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="d83a1-167">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="d83a1-168">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="d83a1-168">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="d83a1-169">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="d83a1-169">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="d83a1-170">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="d83a1-170">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="d83a1-171">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="d83a1-171">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="d83a1-172">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="d83a1-172">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="d83a1-173">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="d83a1-173">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="d83a1-174">Utiliser APT pour mettre à jour .NET</span><span class="sxs-lookup"><span data-stu-id="d83a1-174">Use APT to update .NET</span></span>

<span data-ttu-id="d83a1-175">Quand une nouvelle version de correctif est disponible pour .NET, vous pouvez simplement la mettre à niveau à l’aide de la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="d83a1-175">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="d83a1-176">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="d83a1-176">APT troubleshooting</span></span>

<span data-ttu-id="d83a1-177">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="d83a1-177">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="d83a1-178">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="d83a1-178">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="d83a1-179">Impossible d' \\ installer certains packages</span><span class="sxs-lookup"><span data-stu-id="d83a1-179">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="d83a1-180">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="d83a1-180">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="d83a1-181">Dépendances</span><span class="sxs-lookup"><span data-stu-id="d83a1-181">Dependencies</span></span>

<span data-ttu-id="d83a1-182">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="d83a1-182">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="d83a1-183">Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="d83a1-183">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="d83a1-184">libc6</span><span class="sxs-lookup"><span data-stu-id="d83a1-184">libc6</span></span>
- <span data-ttu-id="d83a1-185">libgcc1</span><span class="sxs-lookup"><span data-stu-id="d83a1-185">libgcc1</span></span>
- <span data-ttu-id="d83a1-186">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="d83a1-186">libgssapi-krb5-2</span></span>
- <span data-ttu-id="d83a1-187">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="d83a1-187">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="d83a1-188">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="d83a1-188">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="d83a1-189">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="d83a1-189">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="d83a1-190">libicu66 (pour 20. x)</span><span class="sxs-lookup"><span data-stu-id="d83a1-190">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="d83a1-191">libssl 1.0.0 (pour 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="d83a1-191">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="d83a1-192">libssl 1.1 (pour 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="d83a1-192">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="d83a1-193">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="d83a1-193">libstdc++6</span></span>
- <span data-ttu-id="d83a1-194">zlib1g</span><span class="sxs-lookup"><span data-stu-id="d83a1-194">zlib1g</span></span>

<span data-ttu-id="d83a1-195">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="d83a1-195">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="d83a1-196">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="d83a1-196">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="d83a1-197">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="d83a1-197">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="d83a1-198">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="d83a1-198">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="d83a1-199">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d83a1-199">Next steps</span></span>

- [<span data-ttu-id="d83a1-200">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="d83a1-200">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="d83a1-201">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d83a1-201">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
