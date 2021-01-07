---
title: Installer .NET sur Fedora-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Fedora.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9dd8c6264831e2a9382960be505639f1eba95151
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970822"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="0193c-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Fedora</span><span class="sxs-lookup"><span data-stu-id="0193c-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="0193c-104">.NET est pris en charge sur Fedora et cet article explique comment installer .NET sur Fedora.</span><span class="sxs-lookup"><span data-stu-id="0193c-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="0193c-105">Quand une version de Fedora n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="0193c-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="install-net-50"></a><span data-ttu-id="0193c-106">Installer .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="0193c-106">Install .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="0193c-107">**Fedora 32**</span><span class="sxs-lookup"><span data-stu-id="0193c-107">**Fedora 32**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

<span data-ttu-id="0193c-108">**Fedora 33**</span><span class="sxs-lookup"><span data-stu-id="0193c-108">**Fedora 33**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="0193c-109">Installer .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0193c-109">Install .NET Core 3.1</span></span>

<span data-ttu-id="0193c-110">La dernière version de .NET disponible dans les référentiels de packages par défaut pour Fedora est .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="0193c-110">The latest version of .NET available in the default package repositories for Fedora is .NET Core 3.1.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="0193c-111">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="0193c-111">Supported distributions</span></span>

<span data-ttu-id="0193c-112">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Fedora sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0193c-112">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="0193c-113">Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Fedora](https://fedoraproject.org/wiki/End_of_life).</span><span class="sxs-lookup"><span data-stu-id="0193c-113">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="0193c-114">Une ✔️ indique que la version de Fedora ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="0193c-114">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="0193c-115">Une ❌ indique que la version de Fedora ou .net n’est pas prise en charge sur cette version de Fedora.</span><span class="sxs-lookup"><span data-stu-id="0193c-115">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="0193c-116">Quand une version de Fedora et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="0193c-116">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="0193c-117">Version .NET</span><span class="sxs-lookup"><span data-stu-id="0193c-117">.NET Version</span></span>  | <span data-ttu-id="0193c-118">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-118">Fedora 33 ✔️</span></span> | <span data-ttu-id="0193c-119">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-119">32 ✔️</span></span> | <span data-ttu-id="0193c-120">31 ❌</span><span class="sxs-lookup"><span data-stu-id="0193c-120">31 ❌</span></span> | <span data-ttu-id="0193c-121">30 ❌</span><span class="sxs-lookup"><span data-stu-id="0193c-121">30 ❌</span></span> | <span data-ttu-id="0193c-122">28 ❌</span><span class="sxs-lookup"><span data-stu-id="0193c-122">29 ❌</span></span> | <span data-ttu-id="0193c-123">28/08/03 ❌</span><span class="sxs-lookup"><span data-stu-id="0193c-123">28 ❌</span></span> | <span data-ttu-id="0193c-124">26 ❌</span><span class="sxs-lookup"><span data-stu-id="0193c-124">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="0193c-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0193c-125">.NET 5.0</span></span>      | <span data-ttu-id="0193c-126">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-126">✔️</span></span>        | <span data-ttu-id="0193c-127">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-127">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="0193c-128">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0193c-128">.NET Core 3.1</span></span> | <span data-ttu-id="0193c-129">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-129">✔️</span></span>        | <span data-ttu-id="0193c-130">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-130">✔️</span></span> | <span data-ttu-id="0193c-131">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-131">✔️</span></span>|<span data-ttu-id="0193c-132">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-132">✔️</span></span> |<span data-ttu-id="0193c-133">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-133">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="0193c-134">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0193c-134">.NET Core 2.1</span></span> | <span data-ttu-id="0193c-135">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-135">✔️</span></span>        | <span data-ttu-id="0193c-136">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-136">✔️</span></span> | <span data-ttu-id="0193c-137">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-137">✔️</span></span>|<span data-ttu-id="0193c-138">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-138">✔️</span></span> |<span data-ttu-id="0193c-139">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-139">✔️</span></span> |<span data-ttu-id="0193c-140">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-140">✔️</span></span>  |<span data-ttu-id="0193c-141">✔️</span><span class="sxs-lookup"><span data-stu-id="0193c-141">✔️</span></span> |

<span data-ttu-id="0193c-142">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="0193c-142">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="0193c-143">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="0193c-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0193c-144">3.0</span><span class="sxs-lookup"><span data-stu-id="0193c-144">3.0</span></span>
- <span data-ttu-id="0193c-145">2.2</span><span class="sxs-lookup"><span data-stu-id="0193c-145">2.2</span></span>
- <span data-ttu-id="0193c-146">2.0</span><span class="sxs-lookup"><span data-stu-id="0193c-146">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="0193c-147">Supprimer les versions préliminaires</span><span class="sxs-lookup"><span data-stu-id="0193c-147">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="0193c-148">Dépendances</span><span class="sxs-lookup"><span data-stu-id="0193c-148">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="0193c-149">Installer sur des distributions plus anciennes</span><span class="sxs-lookup"><span data-stu-id="0193c-149">Install on older distributions</span></span>

<span data-ttu-id="0193c-150">Les versions antérieures de Fedora ne contiennent pas .NET Core dans les référentiels de packages par défaut.</span><span class="sxs-lookup"><span data-stu-id="0193c-150">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="0193c-151">Vous pouvez installer .NET avec le [composant logiciel enfichable](linux-snap.md), via le [script _dotnet-install.sh_](linux-scripted-manual.md#scripted-install), ou utiliser le référentiel Microsoft pour installer .net :</span><span class="sxs-lookup"><span data-stu-id="0193c-151">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="0193c-152">Tout d’abord, ajoutez la clé de signature Microsoft à votre liste de clés approuvées.</span><span class="sxs-lookup"><span data-stu-id="0193c-152">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="0193c-153">Ensuite, ajoutez le dépôt de packages Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0193c-153">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="0193c-154">La source du référentiel est basée sur votre version de Fedora.</span><span class="sxs-lookup"><span data-stu-id="0193c-154">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="0193c-155">Version de Fedora</span><span class="sxs-lookup"><span data-stu-id="0193c-155">Fedora Version</span></span> | <span data-ttu-id="0193c-156">Référentiel de packages</span><span class="sxs-lookup"><span data-stu-id="0193c-156">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="0193c-157">31</span><span class="sxs-lookup"><span data-stu-id="0193c-157">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="0193c-158">30</span><span class="sxs-lookup"><span data-stu-id="0193c-158">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="0193c-159">29</span><span class="sxs-lookup"><span data-stu-id="0193c-159">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="0193c-160">28</span><span class="sxs-lookup"><span data-stu-id="0193c-160">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="0193c-161">27</span><span class="sxs-lookup"><span data-stu-id="0193c-161">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0193c-162">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="0193c-162">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0193c-163">Résoudre les problèmes liés au gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="0193c-163">Troubleshoot the package manager</span></span>

<span data-ttu-id="0193c-164">Cette section fournit des informations sur les erreurs courantes que vous pouvez être amené à effectuer lors de l’utilisation du gestionnaire de package pour installer .NET ou .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0193c-164">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="0193c-165">Impossible de trouver le package</span><span class="sxs-lookup"><span data-stu-id="0193c-165">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="0193c-166">Échec de la récupération</span><span class="sxs-lookup"><span data-stu-id="0193c-166">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="0193c-167">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0193c-167">Next steps</span></span>

- [<span data-ttu-id="0193c-168">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="0193c-168">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="0193c-169">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="0193c-169">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
