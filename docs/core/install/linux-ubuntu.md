---
title: Installer .NET Core sur Ubuntu-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Ubuntu.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9694dac719024264edee849044f048970b63b7b7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132939"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-ubuntu"></a><span data-ttu-id="48a54-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur Ubuntu</span><span class="sxs-lookup"><span data-stu-id="48a54-103">Install .NET Core SDK or .NET Core Runtime on Ubuntu</span></span>

<span data-ttu-id="48a54-104">.NET Core est pris en charge sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="48a54-104">.NET Core is supported on Ubuntu.</span></span> <span data-ttu-id="48a54-105">Cet article explique comment installer .NET Core sur Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="48a54-105">This article describes how to install .NET Core on Ubuntu.</span></span> <span data-ttu-id="48a54-106">Quand une version d’Ubuntu n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="48a54-106">When an Ubuntu version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="48a54-107">Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="48a54-107">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="48a54-108">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="48a54-108">Supported distributions</span></span>

<span data-ttu-id="48a54-109">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions d’Ubuntu sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="48a54-109">The following table is a list of currently supported .NET Core releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="48a54-110">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version d' [Ubuntu](https://wiki.ubuntu.com/Releases).</span><span class="sxs-lookup"><span data-stu-id="48a54-110">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="48a54-111">Une ✔️ indique que la version d’Ubuntu ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="48a54-111">A ✔️ indicates that the version of Ubuntu or .NET Core is still supported.</span></span>
- <span data-ttu-id="48a54-112">Une ❌ indique que la version d’Ubuntu ou de .net Core n’est pas prise en charge sur cette version d’Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="48a54-112">A ❌ indicates that the version of Ubuntu or .NET Core isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="48a54-113">Quand une version d’Ubuntu et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="48a54-113">When both a version of Ubuntu and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="48a54-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="48a54-114">Ubuntu</span></span>                   | <span data-ttu-id="48a54-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="48a54-115">.NET Core 2.1</span></span> | <span data-ttu-id="48a54-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="48a54-116">.NET Core 3.1</span></span> | <span data-ttu-id="48a54-117">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="48a54-117">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="48a54-118">✔️ [20,04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="48a54-118">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="48a54-119">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-119">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-120">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-120">✔️ 3.1</span></span>        | <span data-ttu-id="48a54-121">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-121">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-122">❌[19,10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="48a54-122">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="48a54-123">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-123">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-124">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-124">✔️ 3.1</span></span>        | <span data-ttu-id="48a54-125">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-125">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-126">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="48a54-126">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="48a54-127">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-127">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-128">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-128">✔️ 3.1</span></span>        | <span data-ttu-id="48a54-129">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-129">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-130">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="48a54-130">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="48a54-131">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-131">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-132">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-132">❌ 3.1</span></span>        | <span data-ttu-id="48a54-133">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-133">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-134">✔️ [18,04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="48a54-134">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="48a54-135">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-135">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-136">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-136">✔️ 3.1</span></span>        | <span data-ttu-id="48a54-137">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-137">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-138">❌[17,10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="48a54-138">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="48a54-139">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-139">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-140">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-140">❌ 3.1</span></span>        | <span data-ttu-id="48a54-141">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-141">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-142">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="48a54-142">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="48a54-143">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-143">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-144">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-144">❌ 3.1</span></span>        | <span data-ttu-id="48a54-145">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-145">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-146">❌ [16,10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="48a54-146">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="48a54-147">❌ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-147">❌ 2.1</span></span>        | <span data-ttu-id="48a54-148">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-148">❌ 3.1</span></span>        | <span data-ttu-id="48a54-149">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-149">❌ 5.0 Preview</span></span> |
| <span data-ttu-id="48a54-150">✔️ [16,04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="48a54-150">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="48a54-151">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="48a54-151">✔️ 2.1</span></span>        | <span data-ttu-id="48a54-152">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="48a54-152">✔️ 3.1</span></span>        | <span data-ttu-id="48a54-153">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="48a54-153">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="48a54-154">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="48a54-154">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="48a54-155">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="48a54-155">The downloads for these still remain published:</span></span>

- <span data-ttu-id="48a54-156">3.0</span><span class="sxs-lookup"><span data-stu-id="48a54-156">3.0</span></span>
- <span data-ttu-id="48a54-157">2,2</span><span class="sxs-lookup"><span data-stu-id="48a54-157">2.2</span></span>
- <span data-ttu-id="48a54-158">2,0</span><span class="sxs-lookup"><span data-stu-id="48a54-158">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="48a54-159">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="48a54-159">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2004-"></a><span data-ttu-id="48a54-160">20,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="48a54-160">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1910-"></a><span data-ttu-id="48a54-161">19,10 ❌</span><span class="sxs-lookup"><span data-stu-id="48a54-161">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="48a54-162">19,04 ❌</span><span class="sxs-lookup"><span data-stu-id="48a54-162">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="48a54-163">18,10 ❌</span><span class="sxs-lookup"><span data-stu-id="48a54-163">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="48a54-164">18,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="48a54-164">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1710-"></a><span data-ttu-id="48a54-165">17,10 ❌</span><span class="sxs-lookup"><span data-stu-id="48a54-165">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="48a54-166">17,04 ❌</span><span class="sxs-lookup"><span data-stu-id="48a54-166">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="48a54-167">16,10 ❌</span><span class="sxs-lookup"><span data-stu-id="48a54-167">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="48a54-168">16,04 ✔️</span><span class="sxs-lookup"><span data-stu-id="48a54-168">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="48a54-169">Kit de développement logiciel (SDK) APT Update ou Runtime</span><span class="sxs-lookup"><span data-stu-id="48a54-169">APT update SDK or runtime</span></span>

<span data-ttu-id="48a54-170">Quand une nouvelle version de correctif est disponible pour .NET Core, vous pouvez simplement la mettre à niveau via la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="48a54-170">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="48a54-171">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="48a54-171">APT troubleshooting</span></span>

<span data-ttu-id="48a54-172">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="48a54-172">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="48a54-173">Impossible d' \\ installer certains packages</span><span class="sxs-lookup"><span data-stu-id="48a54-173">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="48a54-174">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="48a54-174">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="48a54-175">Snap</span><span class="sxs-lookup"><span data-stu-id="48a54-175">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="48a54-176">Dépendances</span><span class="sxs-lookup"><span data-stu-id="48a54-176">Dependencies</span></span>

<span data-ttu-id="48a54-177">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="48a54-177">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="48a54-178">Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="48a54-178">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="48a54-179">libc6</span><span class="sxs-lookup"><span data-stu-id="48a54-179">libc6</span></span>
- <span data-ttu-id="48a54-180">libgcc1</span><span class="sxs-lookup"><span data-stu-id="48a54-180">libgcc1</span></span>
- <span data-ttu-id="48a54-181">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="48a54-181">libgssapi-krb5-2</span></span>
- <span data-ttu-id="48a54-182">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="48a54-182">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="48a54-183">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="48a54-183">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="48a54-184">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="48a54-184">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="48a54-185">libicu66 (pour 20. x)</span><span class="sxs-lookup"><span data-stu-id="48a54-185">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="48a54-186">libssl 1.0.0 (pour 14. x, 16. x)</span><span class="sxs-lookup"><span data-stu-id="48a54-186">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="48a54-187">libssl 1.1 (pour 18. x, 20. x)</span><span class="sxs-lookup"><span data-stu-id="48a54-187">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="48a54-188">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="48a54-188">libstdc++6</span></span>
- <span data-ttu-id="48a54-189">zlib1g</span><span class="sxs-lookup"><span data-stu-id="48a54-189">zlib1g</span></span>

<span data-ttu-id="48a54-190">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="48a54-190">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="48a54-191">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="48a54-191">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="48a54-192">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="48a54-192">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="48a54-193">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="48a54-193">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="48a54-194">Installation par script</span><span class="sxs-lookup"><span data-stu-id="48a54-194">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="48a54-195">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="48a54-195">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="48a54-196">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="48a54-196">Next steps</span></span>

- [<span data-ttu-id="48a54-197">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="48a54-197">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
