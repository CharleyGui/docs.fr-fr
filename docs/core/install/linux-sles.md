---
title: Installer .NET Core sur SLES-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 8f64efcc8206b47855871104e5b6914570c06da0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619414"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a><span data-ttu-id="9f28f-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur SLES</span><span class="sxs-lookup"><span data-stu-id="9f28f-103">Install .NET Core SDK or .NET Core Runtime on SLES</span></span>

<span data-ttu-id="9f28f-104">.NET Core est pris en charge sur SLES.</span><span class="sxs-lookup"><span data-stu-id="9f28f-104">.NET Core is supported on SLES.</span></span> <span data-ttu-id="9f28f-105">Cet article explique comment installer .NET Core sur SLES.</span><span class="sxs-lookup"><span data-stu-id="9f28f-105">This article describes how to install .NET Core on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="9f28f-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="9f28f-106">Supported distributions</span></span>

<span data-ttu-id="9f28f-107">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur SLES 12 SP2 et SLES 15.</span><span class="sxs-lookup"><span data-stu-id="9f28f-107">The following table is a list of currently supported .NET Core releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="9f28f-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de SLES ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="9f28f-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="9f28f-109">Une ✔️ indique que la version de SLES ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="9f28f-109">A ✔️ indicates that the version of SLES or .NET Core is still supported.</span></span>
- <span data-ttu-id="9f28f-110">Une ❌ indique que la version de SLES ou de .net Core n’est pas prise en charge sur cette version SLES.</span><span class="sxs-lookup"><span data-stu-id="9f28f-110">A ❌ indicates that the version of SLES or .NET Core isn't supported on that SLES release.</span></span>
- <span data-ttu-id="9f28f-111">Quand une version de SLES et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="9f28f-111">When both a version of SLES and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="9f28f-112">SLES</span><span class="sxs-lookup"><span data-stu-id="9f28f-112">SLES</span></span>                   | <span data-ttu-id="9f28f-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9f28f-113">.NET Core 2.1</span></span> | <span data-ttu-id="9f28f-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="9f28f-114">.NET Core 3.1</span></span> | <span data-ttu-id="9f28f-115">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="9f28f-115">.NET 5 Preview (manual install only)</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="9f28f-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="9f28f-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="9f28f-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9f28f-117">✔️ 2.1</span></span>        | <span data-ttu-id="9f28f-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="9f28f-118">✔️ 3.1</span></span>        | <span data-ttu-id="9f28f-119">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="9f28f-119">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="9f28f-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="9f28f-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="9f28f-121">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="9f28f-121">✔️ 2.1</span></span>        | <span data-ttu-id="9f28f-122">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="9f28f-122">✔️ 3.1</span></span>        | <span data-ttu-id="9f28f-123">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="9f28f-123">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="9f28f-124">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="9f28f-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="9f28f-125">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="9f28f-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="9f28f-126">3.0</span><span class="sxs-lookup"><span data-stu-id="9f28f-126">3.0</span></span>
- <span data-ttu-id="9f28f-127">2.2</span><span class="sxs-lookup"><span data-stu-id="9f28f-127">2.2</span></span>
- <span data-ttu-id="9f28f-128">2.0</span><span class="sxs-lookup"><span data-stu-id="9f28f-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="9f28f-129">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="9f28f-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="9f28f-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="9f28f-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="9f28f-131">Actuellement, le package d’installation du référentiel SLES 15 Microsoft installe le fichier *Microsoft-prod. référentiel* dans le répertoire incorrect, empêchant ainsi zypper de trouver les packages .net core.</span><span class="sxs-lookup"><span data-stu-id="9f28f-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="9f28f-132">Pour résoudre ce problème, créez un lien symbolique dans le répertoire approprié.</span><span class="sxs-lookup"><span data-stu-id="9f28f-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="9f28f-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="9f28f-133">SLES 12 ✔️</span></span>

<span data-ttu-id="9f28f-134">.NET Core requiert SP2 au minimum pour la famille SLES 12.</span><span class="sxs-lookup"><span data-stu-id="9f28f-134">.NET Core requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="9f28f-135">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="9f28f-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="9f28f-136">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9f28f-136">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="9f28f-137">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="9f28f-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="9f28f-138">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="9f28f-138">Dependencies</span></span>

<span data-ttu-id="9f28f-139">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="9f28f-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="9f28f-140">Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="9f28f-140">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="9f28f-141">krb5</span><span class="sxs-lookup"><span data-stu-id="9f28f-141">krb5</span></span>
- <span data-ttu-id="9f28f-142">libicu</span><span class="sxs-lookup"><span data-stu-id="9f28f-142">libicu</span></span>
- <span data-ttu-id="9f28f-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="9f28f-143">libopenssl1_1</span></span>

<span data-ttu-id="9f28f-144">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="9f28f-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="9f28f-145">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="9f28f-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="9f28f-146">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="9f28f-146">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="9f28f-147">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="9f28f-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="9f28f-148">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="9f28f-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="9f28f-149">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="9f28f-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="9f28f-150">Installation par script</span><span class="sxs-lookup"><span data-stu-id="9f28f-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="9f28f-151">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="9f28f-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="9f28f-152">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9f28f-152">Next steps</span></span>

- [<span data-ttu-id="9f28f-153">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="9f28f-153">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
