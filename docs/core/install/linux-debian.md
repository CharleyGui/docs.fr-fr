---
title: Installer .NET Core sur Debian-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Debian.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: c66d8e1daad4e59a766781b7117600352879b724
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603054"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-debian"></a><span data-ttu-id="5d1b5-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur Debian</span><span class="sxs-lookup"><span data-stu-id="5d1b5-103">Install .NET Core SDK or .NET Core Runtime on Debian</span></span>

<span data-ttu-id="5d1b5-104">Cet article explique comment installer .NET Core sur Debian.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-104">This article describes how to install .NET Core on Debian.</span></span> <span data-ttu-id="5d1b5-105">Quand une version Debian n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-105">When a Debian version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="5d1b5-106">Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="5d1b5-107">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="5d1b5-107">Supported distributions</span></span>

<span data-ttu-id="5d1b5-108">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Debian sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-108">The following table is a list of currently supported .NET Core releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="5d1b5-109">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Debian](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="5d1b5-109">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="5d1b5-110">Une ✔️ indique que la version de Debian ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-110">A ✔️ indicates that the version of Debian or .NET Core is still supported.</span></span>
- <span data-ttu-id="5d1b5-111">Une ❌ indique que la version de Debian ou de .net Core n’est pas prise en charge sur cette version Debian.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-111">A ❌ indicates that the version of Debian or .NET Core isn't supported on that Debian release.</span></span>
- <span data-ttu-id="5d1b5-112">Quand une version de Debian et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-112">When both a version of Debian and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="5d1b5-113">Debian</span><span class="sxs-lookup"><span data-stu-id="5d1b5-113">Debian</span></span>                   | <span data-ttu-id="5d1b5-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-114">.NET Core 2.1</span></span> | <span data-ttu-id="5d1b5-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-115">.NET Core 3.1</span></span> | <span data-ttu-id="5d1b5-116">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="5d1b5-116">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="5d1b5-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="5d1b5-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="5d1b5-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-118">✔️ 2.1</span></span>        | <span data-ttu-id="5d1b5-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-119">✔️ 3.1</span></span>        | <span data-ttu-id="5d1b5-120">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="5d1b5-120">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="5d1b5-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="5d1b5-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="5d1b5-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-122">✔️ 2.1</span></span>        | <span data-ttu-id="5d1b5-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-123">✔️ 3.1</span></span>        | <span data-ttu-id="5d1b5-124">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="5d1b5-124">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="5d1b5-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="5d1b5-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="5d1b5-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-126">✔️ 2.1</span></span>        | <span data-ttu-id="5d1b5-127">❌3,1</span><span class="sxs-lookup"><span data-stu-id="5d1b5-127">❌ 3.1</span></span>        | <span data-ttu-id="5d1b5-128">❌version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="5d1b5-128">❌ 5.0 Preview</span></span> |

<span data-ttu-id="5d1b5-129">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-129">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="5d1b5-130">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="5d1b5-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="5d1b5-131">3.0</span><span class="sxs-lookup"><span data-stu-id="5d1b5-131">3.0</span></span>
- <span data-ttu-id="5d1b5-132">2.2</span><span class="sxs-lookup"><span data-stu-id="5d1b5-132">2.2</span></span>
- <span data-ttu-id="5d1b5-133">2.0</span><span class="sxs-lookup"><span data-stu-id="5d1b5-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5d1b5-134">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="5d1b5-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="5d1b5-135">✔️ Debian 10</span><span class="sxs-lookup"><span data-stu-id="5d1b5-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="5d1b5-136">✔️ Debian 9</span><span class="sxs-lookup"><span data-stu-id="5d1b5-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="5d1b5-137">Debian 8❌</span><span class="sxs-lookup"><span data-stu-id="5d1b5-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="5d1b5-138">Kit de développement logiciel (SDK) APT Update ou Runtime</span><span class="sxs-lookup"><span data-stu-id="5d1b5-138">APT update SDK or runtime</span></span>

<span data-ttu-id="5d1b5-139">Quand une nouvelle version de correctif est disponible pour .NET Core, vous pouvez simplement la mettre à niveau via la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d1b5-139">When a new patch release is available for .NET Core, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="5d1b5-140">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="5d1b5-140">APT troubleshooting</span></span>

<span data-ttu-id="5d1b5-141">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d1b5-141">This section provides information on common errors you may get while using APT to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="5d1b5-142">Impossible de localiser</span><span class="sxs-lookup"><span data-stu-id="5d1b5-142">Unable to locate</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="5d1b5-143">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="5d1b5-143">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="5d1b5-144">Snap</span><span class="sxs-lookup"><span data-stu-id="5d1b5-144">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="5d1b5-145">Dépendances</span><span class="sxs-lookup"><span data-stu-id="5d1b5-145">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="5d1b5-146">Installation par script</span><span class="sxs-lookup"><span data-stu-id="5d1b5-146">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="5d1b5-147">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="5d1b5-147">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="5d1b5-148">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5d1b5-148">Next steps</span></span>

- [<span data-ttu-id="5d1b5-149">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5d1b5-149">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
