---
title: Installer .NET Core sur openSUSE-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 24f0a5b5278d038c2f941b0984efcacd91dcbe31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619466"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-opensuse"></a><span data-ttu-id="47a0b-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur openSUSE</span><span class="sxs-lookup"><span data-stu-id="47a0b-103">Install .NET Core SDK or .NET Core Runtime on openSUSE</span></span>

<span data-ttu-id="47a0b-104">.NET Core est pris en charge sur openSUSE.</span><span class="sxs-lookup"><span data-stu-id="47a0b-104">.NET Core is supported on openSUSE.</span></span> <span data-ttu-id="47a0b-105">Cet article explique comment installer .NET Core sur openSUSE.</span><span class="sxs-lookup"><span data-stu-id="47a0b-105">This article describes how to install .NET Core on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="47a0b-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="47a0b-106">Supported distributions</span></span>

<span data-ttu-id="47a0b-107">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="47a0b-107">The following table is a list of currently supported .NET Core releases on openSUSE 15.</span></span> <span data-ttu-id="47a0b-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de openSUSE ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="47a0b-108">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="47a0b-109">Une ✔️ indique que la version de openSUSE ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="47a0b-109">A ✔️ indicates that the version of openSUSE or .NET Core is still supported.</span></span>
- <span data-ttu-id="47a0b-110">Une ❌ indique que la version de openSUSE ou de .net Core n’est pas prise en charge sur cette version de openSUSE.</span><span class="sxs-lookup"><span data-stu-id="47a0b-110">A ❌ indicates that the version of openSUSE or .NET Core isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="47a0b-111">Quand une version de openSUSE et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="47a0b-111">When both a version of openSUSE and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="47a0b-112">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="47a0b-112">openSUSE</span></span>                   | <span data-ttu-id="47a0b-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="47a0b-113">.NET Core 2.1</span></span> | <span data-ttu-id="47a0b-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="47a0b-114">.NET Core 3.1</span></span> | <span data-ttu-id="47a0b-115">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="47a0b-115">.NET 5 Preview (manual install only)</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="47a0b-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="47a0b-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="47a0b-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="47a0b-117">✔️ 2.1</span></span>        | <span data-ttu-id="47a0b-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="47a0b-118">✔️ 3.1</span></span>        | <span data-ttu-id="47a0b-119">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="47a0b-119">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="47a0b-120">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="47a0b-120">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="47a0b-121">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="47a0b-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="47a0b-122">3.0</span><span class="sxs-lookup"><span data-stu-id="47a0b-122">3.0</span></span>
- <span data-ttu-id="47a0b-123">2.2</span><span class="sxs-lookup"><span data-stu-id="47a0b-123">2.2</span></span>
- <span data-ttu-id="47a0b-124">2.0</span><span class="sxs-lookup"><span data-stu-id="47a0b-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="47a0b-125">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="47a0b-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="47a0b-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="47a0b-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="47a0b-127">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="47a0b-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="47a0b-128">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET Core.</span><span class="sxs-lookup"><span data-stu-id="47a0b-128">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="47a0b-129">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="47a0b-129">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="47a0b-130">Snap</span><span class="sxs-lookup"><span data-stu-id="47a0b-130">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="47a0b-131">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="47a0b-131">Dependencies</span></span>

<span data-ttu-id="47a0b-132">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="47a0b-132">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="47a0b-133">Toutefois, si vous installez manuellement .NET Core ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="47a0b-133">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="47a0b-134">krb5</span><span class="sxs-lookup"><span data-stu-id="47a0b-134">krb5</span></span>
- <span data-ttu-id="47a0b-135">libicu</span><span class="sxs-lookup"><span data-stu-id="47a0b-135">libicu</span></span>
- <span data-ttu-id="47a0b-136">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="47a0b-136">libopenssl1_0_0</span></span>

<span data-ttu-id="47a0b-137">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="47a0b-137">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="47a0b-138">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="47a0b-138">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="47a0b-139">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="47a0b-139">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="47a0b-140">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="47a0b-140">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="47a0b-141">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="47a0b-141">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="47a0b-142">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="47a0b-142">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="47a0b-143">Installation par script</span><span class="sxs-lookup"><span data-stu-id="47a0b-143">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="47a0b-144">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="47a0b-144">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="47a0b-145">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="47a0b-145">Next steps</span></span>

- [<span data-ttu-id="47a0b-146">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="47a0b-146">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
