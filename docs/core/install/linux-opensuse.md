---
title: Installer .NET sur openSUSE-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 17012f3689e5834fd1629946767e931cb22a2c1b
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506899"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="35406-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur openSUSE</span><span class="sxs-lookup"><span data-stu-id="35406-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="35406-104">.NET est pris en charge sur openSUSE.</span><span class="sxs-lookup"><span data-stu-id="35406-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="35406-105">Cet article explique comment installer .NET sur openSUSE.</span><span class="sxs-lookup"><span data-stu-id="35406-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="35406-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="35406-106">Supported distributions</span></span>

<span data-ttu-id="35406-107">Le tableau suivant répertorie les versions .NET actuellement prises en charge sur openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="35406-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="35406-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de openSUSE ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="35406-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="35406-109">Une ✔️ indique que la version de openSUSE ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="35406-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="35406-110">Une ❌ indique que la version de openSUSE ou .net n’est pas prise en charge sur cette version de openSUSE.</span><span class="sxs-lookup"><span data-stu-id="35406-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="35406-111">Quand une version de openSUSE et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="35406-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="35406-112">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="35406-112">openSUSE</span></span>                   | <span data-ttu-id="35406-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="35406-113">.NET Core 2.1</span></span> | <span data-ttu-id="35406-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="35406-114">.NET Core 3.1</span></span> | <span data-ttu-id="35406-115">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="35406-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="35406-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="35406-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="35406-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="35406-117">✔️ 2.1</span></span>        | <span data-ttu-id="35406-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="35406-118">✔️ 3.1</span></span>        | <span data-ttu-id="35406-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="35406-119">✔️ 5.0</span></span> |

<span data-ttu-id="35406-120">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="35406-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="35406-121">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="35406-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="35406-122">3.0</span><span class="sxs-lookup"><span data-stu-id="35406-122">3.0</span></span>
- <span data-ttu-id="35406-123">2.2</span><span class="sxs-lookup"><span data-stu-id="35406-123">2.2</span></span>
- <span data-ttu-id="35406-124">2.0</span><span class="sxs-lookup"><span data-stu-id="35406-124">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="35406-125">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="35406-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="35406-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="35406-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="35406-127">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="35406-127">Troubleshoot the package manager</span></span>

<span data-ttu-id="35406-128">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="35406-128">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="35406-129">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="35406-129">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="35406-130">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="35406-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="35406-131">Snap</span><span class="sxs-lookup"><span data-stu-id="35406-131">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="35406-132">Dépendances</span><span class="sxs-lookup"><span data-stu-id="35406-132">Dependencies</span></span>

<span data-ttu-id="35406-133">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="35406-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="35406-134">Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="35406-134">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="35406-135">krb5</span><span class="sxs-lookup"><span data-stu-id="35406-135">krb5</span></span>
- <span data-ttu-id="35406-136">libicu</span><span class="sxs-lookup"><span data-stu-id="35406-136">libicu</span></span>
- <span data-ttu-id="35406-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="35406-137">libopenssl1_0_0</span></span>

<span data-ttu-id="35406-138">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="35406-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="35406-139">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="35406-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="35406-140">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="35406-140">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="35406-141">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="35406-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="35406-142">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="35406-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="35406-143">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="35406-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="35406-144">Installation par script</span><span class="sxs-lookup"><span data-stu-id="35406-144">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="35406-145">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="35406-145">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="35406-146">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="35406-146">Next steps</span></span>

- [<span data-ttu-id="35406-147">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="35406-147">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
