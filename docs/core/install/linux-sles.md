---
title: Installer .NET sur SLES-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur SLES.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f351a9b11ab16910963a1db88d88b6949b56ae11
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031798"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="bed25-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur SLES</span><span class="sxs-lookup"><span data-stu-id="bed25-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="bed25-104">.NET est pris en charge sur SLES.</span><span class="sxs-lookup"><span data-stu-id="bed25-104">.NET is supported on SLES.</span></span> <span data-ttu-id="bed25-105">Cet article explique comment installer .NET sur SLES.</span><span class="sxs-lookup"><span data-stu-id="bed25-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="bed25-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="bed25-106">Supported distributions</span></span>

<span data-ttu-id="bed25-107">Le tableau suivant répertorie les versions .NET actuellement prises en charge sur SLES 12 SP2 et SLES 15.</span><span class="sxs-lookup"><span data-stu-id="bed25-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="bed25-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de SLES ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bed25-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="bed25-109">Une ✔️ indique que la version de SLES ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bed25-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="bed25-110">Une ❌ indique que la version de SLES ou de .net n’est pas prise en charge sur cette version SLES.</span><span class="sxs-lookup"><span data-stu-id="bed25-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="bed25-111">Quand une version de SLES et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bed25-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="bed25-112">SLES</span><span class="sxs-lookup"><span data-stu-id="bed25-112">SLES</span></span>                   | <span data-ttu-id="bed25-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bed25-113">.NET Core 2.1</span></span> | <span data-ttu-id="bed25-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="bed25-114">.NET Core 3.1</span></span> | <span data-ttu-id="bed25-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="bed25-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="bed25-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="bed25-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="bed25-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="bed25-117">✔️ 2.1</span></span>        | <span data-ttu-id="bed25-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="bed25-118">✔️ 3.1</span></span>        | <span data-ttu-id="bed25-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="bed25-119">✔️ 5.0</span></span> |
| <span data-ttu-id="bed25-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="bed25-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="bed25-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="bed25-121">✔️ 2.1</span></span>        | <span data-ttu-id="bed25-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="bed25-122">✔️ 3.1</span></span>        | <span data-ttu-id="bed25-123">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="bed25-123">✔️ 5.0</span></span> |

<span data-ttu-id="bed25-124">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bed25-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="bed25-125">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="bed25-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="bed25-126">3.0</span><span class="sxs-lookup"><span data-stu-id="bed25-126">3.0</span></span>
- <span data-ttu-id="bed25-127">2.2</span><span class="sxs-lookup"><span data-stu-id="bed25-127">2.2</span></span>
- <span data-ttu-id="bed25-128">2.0</span><span class="sxs-lookup"><span data-stu-id="bed25-128">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="bed25-129">Supprimer les versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="bed25-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="bed25-130">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="bed25-130">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="bed25-131">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="bed25-131">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="bed25-132">Actuellement, le package d’installation du référentiel SLES 15 Microsoft installe le fichier *Microsoft-prod. référentiel* dans le répertoire incorrect, empêchant ainsi zypper de trouver les packages .net.</span><span class="sxs-lookup"><span data-stu-id="bed25-132">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="bed25-133">Pour résoudre ce problème, créez un lien symbolique dans le répertoire approprié.</span><span class="sxs-lookup"><span data-stu-id="bed25-133">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="bed25-134">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="bed25-134">SLES 12 ✔️</span></span>

<span data-ttu-id="bed25-135">.NET requiert SP2 au minimum pour la famille SLES 12.</span><span class="sxs-lookup"><span data-stu-id="bed25-135">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="bed25-136">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="bed25-136">Troubleshoot the package manager</span></span>

<span data-ttu-id="bed25-137">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="bed25-137">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="bed25-138">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="bed25-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="bed25-139">Dépendances</span><span class="sxs-lookup"><span data-stu-id="bed25-139">Dependencies</span></span>

<span data-ttu-id="bed25-140">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="bed25-140">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="bed25-141">Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="bed25-141">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="bed25-142">krb5</span><span class="sxs-lookup"><span data-stu-id="bed25-142">krb5</span></span>
- <span data-ttu-id="bed25-143">libicu</span><span class="sxs-lookup"><span data-stu-id="bed25-143">libicu</span></span>
- <span data-ttu-id="bed25-144">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="bed25-144">libopenssl1_1</span></span>

<span data-ttu-id="bed25-145">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="bed25-145">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="bed25-146">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="bed25-146">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="bed25-147">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="bed25-147">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="bed25-148">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="bed25-148">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="bed25-149">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="bed25-149">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="bed25-150">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="bed25-150">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="bed25-151">Installation par script</span><span class="sxs-lookup"><span data-stu-id="bed25-151">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="bed25-152">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="bed25-152">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="bed25-153">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bed25-153">Next steps</span></span>

- [<span data-ttu-id="bed25-154">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bed25-154">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
