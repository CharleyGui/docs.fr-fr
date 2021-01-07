---
title: Installer .NET sur openSUSE-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur openSUSE.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7a519f19f708e1f12af1e9715bad4f38a607f9c3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970809"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="dea03-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur openSUSE</span><span class="sxs-lookup"><span data-stu-id="dea03-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="dea03-104">.NET est pris en charge sur openSUSE.</span><span class="sxs-lookup"><span data-stu-id="dea03-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="dea03-105">Cet article explique comment installer .NET sur openSUSE.</span><span class="sxs-lookup"><span data-stu-id="dea03-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="dea03-106">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="dea03-106">Supported distributions</span></span>

<span data-ttu-id="dea03-107">Le tableau suivant répertorie les versions .NET actuellement prises en charge sur openSUSE 15.</span><span class="sxs-lookup"><span data-stu-id="dea03-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="dea03-108">Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de openSUSE ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="dea03-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="dea03-109">Une ✔️ indique que la version de openSUSE ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="dea03-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="dea03-110">Une ❌ indique que la version de openSUSE ou .net n’est pas prise en charge sur cette version de openSUSE.</span><span class="sxs-lookup"><span data-stu-id="dea03-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="dea03-111">Quand une version de openSUSE et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="dea03-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="dea03-112">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="dea03-112">openSUSE</span></span>                   | <span data-ttu-id="dea03-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dea03-113">.NET Core 2.1</span></span> | <span data-ttu-id="dea03-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="dea03-114">.NET Core 3.1</span></span> | <span data-ttu-id="dea03-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="dea03-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="dea03-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="dea03-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="dea03-117">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="dea03-117">✔️ 2.1</span></span>        | <span data-ttu-id="dea03-118">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="dea03-118">✔️ 3.1</span></span>        | <span data-ttu-id="dea03-119">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="dea03-119">✔️ 5.0</span></span> |

<span data-ttu-id="dea03-120">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="dea03-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="dea03-121">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="dea03-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="dea03-122">3.0</span><span class="sxs-lookup"><span data-stu-id="dea03-122">3.0</span></span>
- <span data-ttu-id="dea03-123">2.2</span><span class="sxs-lookup"><span data-stu-id="dea03-123">2.2</span></span>
- <span data-ttu-id="dea03-124">2.0</span><span class="sxs-lookup"><span data-stu-id="dea03-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="dea03-125">Supprimer les versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="dea03-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="dea03-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="dea03-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="dea03-127">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="dea03-127">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="dea03-128">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="dea03-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="dea03-129">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET.</span><span class="sxs-lookup"><span data-stu-id="dea03-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="dea03-130">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="dea03-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="dea03-131">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="dea03-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="dea03-132">Dépendances</span><span class="sxs-lookup"><span data-stu-id="dea03-132">Dependencies</span></span>

<span data-ttu-id="dea03-133">Lorsque vous installez avec un gestionnaire de package, ces bibliothèques sont installées pour vous.</span><span class="sxs-lookup"><span data-stu-id="dea03-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="dea03-134">Toutefois, si vous installez manuellement .NET ou si vous publiez une application autonome, vous devez vous assurer que ces bibliothèques sont installées :</span><span class="sxs-lookup"><span data-stu-id="dea03-134">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="dea03-135">krb5</span><span class="sxs-lookup"><span data-stu-id="dea03-135">krb5</span></span>
- <span data-ttu-id="dea03-136">libicu</span><span class="sxs-lookup"><span data-stu-id="dea03-136">libicu</span></span>
- <span data-ttu-id="dea03-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="dea03-137">libopenssl1_0_0</span></span>

<span data-ttu-id="dea03-138">Si la version OpenSSL de l’environnement d’exécution cible est 1,1 ou une version plus récente, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="dea03-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="dea03-139">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="dea03-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="dea03-140">Pour les applications .NET qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="dea03-140">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="dea03-141">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="dea03-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="dea03-142">Vous pouvez installer une version récente de *libgdiplus* en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="dea03-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="dea03-143">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="dea03-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dea03-144">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="dea03-144">Next steps</span></span>

- [<span data-ttu-id="dea03-145">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="dea03-145">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="dea03-146">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dea03-146">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
