---
title: Installer .NET sur Debian-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Debian.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 913d8bffdd6c0b5e88a70dae0ec4c8d732e80cc0
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970835"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="199e3-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Debian</span><span class="sxs-lookup"><span data-stu-id="199e3-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="199e3-104">Cet article explique comment installer .NET sur Debian.</span><span class="sxs-lookup"><span data-stu-id="199e3-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="199e3-105">Quand une version Debian n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="199e3-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="199e3-106">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="199e3-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="199e3-107">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="199e3-107">Supported distributions</span></span>

<span data-ttu-id="199e3-108">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Debian sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="199e3-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="199e3-109">Ces versions restent prises en charge jusqu’à la fin de la [prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Debian](https://wiki.debian.org/DebianReleases).</span><span class="sxs-lookup"><span data-stu-id="199e3-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="199e3-110">Une ✔️ indique que la version de Debian ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="199e3-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="199e3-111">Une ❌ indique que la version de Debian ou de .net n’est pas prise en charge sur cette version Debian.</span><span class="sxs-lookup"><span data-stu-id="199e3-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="199e3-112">Quand une version de Debian et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="199e3-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="199e3-113">Debian</span><span class="sxs-lookup"><span data-stu-id="199e3-113">Debian</span></span>                   | <span data-ttu-id="199e3-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="199e3-114">.NET Core 2.1</span></span> | <span data-ttu-id="199e3-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="199e3-115">.NET Core 3.1</span></span> | <span data-ttu-id="199e3-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="199e3-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="199e3-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="199e3-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="199e3-118">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="199e3-118">✔️ 2.1</span></span>        | <span data-ttu-id="199e3-119">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="199e3-119">✔️ 3.1</span></span>        | <span data-ttu-id="199e3-120">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="199e3-120">✔️ 5.0</span></span> |
| <span data-ttu-id="199e3-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="199e3-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="199e3-122">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="199e3-122">✔️ 2.1</span></span>        | <span data-ttu-id="199e3-123">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="199e3-123">✔️ 3.1</span></span>        | <span data-ttu-id="199e3-124">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="199e3-124">✔️ 5.0</span></span> |
| <span data-ttu-id="199e3-125">❌[8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="199e3-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="199e3-126">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="199e3-126">✔️ 2.1</span></span>        | <span data-ttu-id="199e3-127">❌ 3,1</span><span class="sxs-lookup"><span data-stu-id="199e3-127">❌ 3.1</span></span>        | <span data-ttu-id="199e3-128">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="199e3-128">❌ 5.0</span></span> |

<span data-ttu-id="199e3-129">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="199e3-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="199e3-130">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="199e3-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="199e3-131">3.0</span><span class="sxs-lookup"><span data-stu-id="199e3-131">3.0</span></span>
- <span data-ttu-id="199e3-132">2.2</span><span class="sxs-lookup"><span data-stu-id="199e3-132">2.2</span></span>
- <span data-ttu-id="199e3-133">2.0</span><span class="sxs-lookup"><span data-stu-id="199e3-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="199e3-134">Supprimer les versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="199e3-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="debian-10-"></a><span data-ttu-id="199e3-135">✔️ Debian 10</span><span class="sxs-lookup"><span data-stu-id="199e3-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="199e3-136">✔️ Debian 9</span><span class="sxs-lookup"><span data-stu-id="199e3-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="199e3-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="199e3-137">Debian 8 ❌</span></span>

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

## <a name="how-to-install-other-versions"></a><span data-ttu-id="199e3-138">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="199e3-138">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="199e3-139">Utiliser APT pour mettre à jour .NET</span><span class="sxs-lookup"><span data-stu-id="199e3-139">Use APT to update .NET</span></span>

<span data-ttu-id="199e3-140">Quand une nouvelle version de correctif est disponible pour .NET, vous pouvez simplement la mettre à niveau à l’aide de la commande APT avec les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="199e3-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="199e3-141">Résolution des problèmes de APT</span><span class="sxs-lookup"><span data-stu-id="199e3-141">APT troubleshooting</span></span>

<span data-ttu-id="199e3-142">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation de la fonction APT pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="199e3-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="199e3-143">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="199e3-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="199e3-144">Impossible d' \\ installer certains packages</span><span class="sxs-lookup"><span data-stu-id="199e3-144">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="199e3-145">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="199e3-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="199e3-146">Dépendances</span><span class="sxs-lookup"><span data-stu-id="199e3-146">Dependencies</span></span>

<span data-ttu-id="199e3-147">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="199e3-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="199e3-148">Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="199e3-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="199e3-149">libc6</span><span class="sxs-lookup"><span data-stu-id="199e3-149">libc6</span></span>
- <span data-ttu-id="199e3-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="199e3-150">libgcc1</span></span>
- <span data-ttu-id="199e3-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="199e3-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="199e3-152">libicu52 (pour 8. x)</span><span class="sxs-lookup"><span data-stu-id="199e3-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="199e3-153">libicu57 (9. x)</span><span class="sxs-lookup"><span data-stu-id="199e3-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="199e3-154">libicu63 (pour 10. x)</span><span class="sxs-lookup"><span data-stu-id="199e3-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="199e3-155">libicu67 (pour 11. x)</span><span class="sxs-lookup"><span data-stu-id="199e3-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="199e3-156">libssl 1.0.0 (8. x)</span><span class="sxs-lookup"><span data-stu-id="199e3-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="199e3-157">libssl 1.1 (pour 9. x-11. x)</span><span class="sxs-lookup"><span data-stu-id="199e3-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="199e3-158">libstdc + + 6</span><span class="sxs-lookup"><span data-stu-id="199e3-158">libstdc++6</span></span>
- <span data-ttu-id="199e3-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="199e3-159">zlib1g</span></span>

<span data-ttu-id="199e3-160">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="199e3-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="199e3-161">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="199e3-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="199e3-162">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="199e3-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="199e3-163">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="199e3-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="199e3-164">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="199e3-164">Next steps</span></span>

- [<span data-ttu-id="199e3-165">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="199e3-165">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="199e3-166">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="199e3-166">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
