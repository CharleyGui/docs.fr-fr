---
title: Installer .NET Core sur Debian-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Debian.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: d0f7d4092ec420d031d0874a56b9e2148afdb865
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538538"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="653d6-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur Debian</span><span class="sxs-lookup"><span data-stu-id="653d6-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="653d6-104">Cet article explique comment installer .NET Core sur Debian.</span><span class="sxs-lookup"><span data-stu-id="653d6-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="653d6-105">Quand une version Debian n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="653d6-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="653d6-106">Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="653d6-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="653d6-107">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="653d6-107">Supported distributions</span></span>

<span data-ttu-id="653d6-108">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Debian sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="653d6-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="653d6-109">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Debian](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="653d6-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="653d6-110">Une ✔️ indique que la version de Debian ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="653d6-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="653d6-111">Une ❌ indique que la version de Debian ou de .net Core n’est pas prise en charge sur cette version Debian.</span><span class="sxs-lookup"><span data-stu-id="653d6-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="653d6-112">Quand une version de Debian et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="653d6-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="653d6-113">Debian</span><span class="sxs-lookup"><span data-stu-id="653d6-113">Debian</span></span>                   | <span data-ttu-id="653d6-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="653d6-114">.NET Core 2.1</span></span> | <span data-ttu-id="653d6-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="653d6-115">.NET Core 3.1</span></span> | <span data-ttu-id="653d6-116">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="653d6-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="653d6-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="653d6-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="653d6-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="653d6-118">✔️ 2.1</span></span>        | <span data-ttu-id="653d6-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="653d6-119">✔️ 3.1</span></span>        | <span data-ttu-id="653d6-120">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="653d6-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="653d6-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="653d6-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="653d6-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="653d6-122">✔️ 2.1</span></span>        | <span data-ttu-id="653d6-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="653d6-123">✔️ 3.1</span></span>        | <span data-ttu-id="653d6-124">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="653d6-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="653d6-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="653d6-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="653d6-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="653d6-126">✔️ 2.1</span></span>        | <span data-ttu-id="653d6-127">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="653d6-127">❌ 3.1</span></span>        | <span data-ttu-id="653d6-128">❌ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="653d6-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="653d6-129">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="653d6-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="653d6-130">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="653d6-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="653d6-131">3.0</span><span class="sxs-lookup"><span data-stu-id="653d6-131">3.0</span></span>
- <span data-ttu-id="653d6-132">2.2</span><span class="sxs-lookup"><span data-stu-id="653d6-132">2.2</span></span>
- <span data-ttu-id="653d6-133">2.0</span><span class="sxs-lookup"><span data-stu-id="653d6-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="653d6-134">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="653d6-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="653d6-135">✔️ Debian 10</span><span class="sxs-lookup"><span data-stu-id="653d6-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="653d6-136">✔️ Debian 9</span><span class="sxs-lookup"><span data-stu-id="653d6-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="653d6-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="653d6-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="653d6-138">Kit de développement logiciel (SDK) APT Update ou Runtime</span><span class="sxs-lookup"><span data-stu-id="653d6-138">APT update SDK or runtime</span></span>

<span data-ttu-id="653d6-139">Quand une nouvelle version de correctif est disponible pour .NET Core, vous pouvez simplement la mettre à niveau via la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="653d6-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="653d6-140">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="653d6-140">APT troubleshooting</span></span>

<span data-ttu-id="653d6-141">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="653d6-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="653d6-142">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="653d6-142">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="653d6-143">Impossible d' \\ installer certains packages</span><span class="sxs-lookup"><span data-stu-id="653d6-143">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="653d6-144">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="653d6-144">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="653d6-145">Snap</span><span class="sxs-lookup"><span data-stu-id="653d6-145">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="653d6-146">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="653d6-146">Dependencies</span></span>

<span data-ttu-id="653d6-147">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="653d6-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="653d6-148">Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="653d6-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="653d6-149">libc6</span><span class="sxs-lookup"><span data-stu-id="653d6-149">libc6</span></span>
- <span data-ttu-id="653d6-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="653d6-150">libgcc1</span></span>
- <span data-ttu-id="653d6-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="653d6-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="653d6-152">libicu52 (pour 8. x)</span><span class="sxs-lookup"><span data-stu-id="653d6-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="653d6-153">libicu57 (9. x)</span><span class="sxs-lookup"><span data-stu-id="653d6-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="653d6-154">libicu63 (pour 10. x)</span><span class="sxs-lookup"><span data-stu-id="653d6-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="653d6-155">libicu67 (pour 11. x)</span><span class="sxs-lookup"><span data-stu-id="653d6-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="653d6-156">libssl 1.0.0 (8. x)</span><span class="sxs-lookup"><span data-stu-id="653d6-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="653d6-157">libssl 1.1 (pour 9. x-11. x)</span><span class="sxs-lookup"><span data-stu-id="653d6-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="653d6-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="653d6-158">libstdc++6</span></span>
- <span data-ttu-id="653d6-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="653d6-159">zlib1g</span></span>

<span data-ttu-id="653d6-160">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="653d6-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="653d6-161">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="653d6-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="653d6-162">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="653d6-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="653d6-163">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="653d6-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="653d6-164">Installation par script</span><span class="sxs-lookup"><span data-stu-id="653d6-164">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="653d6-165">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="653d6-165">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="653d6-166">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="653d6-166">Next steps</span></span>

- [<span data-ttu-id="653d6-167">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="653d6-167">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
