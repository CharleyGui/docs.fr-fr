---
title: Installer .NET sur RHEL-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: a742497bba3459a4d8772f5c9e3d915b5b18e62e
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506924"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="bd761-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur RHEL</span><span class="sxs-lookup"><span data-stu-id="bd761-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="bd761-104">.NET est pris en charge sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="bd761-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="bd761-105">Cet article explique comment installer .NET sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="bd761-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="bd761-106">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="bd761-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="bd761-107">Pour installer .NET à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="bd761-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="bd761-108">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="bd761-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="bd761-109">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="bd761-109">Supported distributions</span></span>

<span data-ttu-id="bd761-110">Le tableau suivant répertorie les versions .NET actuellement prises en charge sur RHEL 7 et RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="bd761-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="bd761-111">Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de RHEL ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bd761-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="bd761-112">Une ✔️ indique que la version de RHEL ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bd761-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="bd761-113">Une ❌ indique que la version de RHEL ou de .net n’est pas prise en charge sur cette version de RHEL.</span><span class="sxs-lookup"><span data-stu-id="bd761-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="bd761-114">Quand une version de RHEL et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bd761-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="bd761-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="bd761-115">RHEL</span></span>                   | <span data-ttu-id="bd761-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bd761-116">.NET Core 2.1</span></span> | <span data-ttu-id="bd761-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="bd761-117">.NET Core 3.1</span></span> | <span data-ttu-id="bd761-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="bd761-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="bd761-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="bd761-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="bd761-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="bd761-120">✔️ 2.1</span></span>        | <span data-ttu-id="bd761-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="bd761-121">✔️ 3.1</span></span>        | <span data-ttu-id="bd761-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="bd761-122">✔️ 5.0</span></span> |
| <span data-ttu-id="bd761-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="bd761-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="bd761-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="bd761-124">✔️ 2.1</span></span>        | <span data-ttu-id="bd761-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="bd761-125">✔️ 3.1</span></span>        | <span data-ttu-id="bd761-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="bd761-126">✔️ 5.0</span></span> |

<span data-ttu-id="bd761-127">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bd761-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="bd761-128">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="bd761-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="bd761-129">3.0</span><span class="sxs-lookup"><span data-stu-id="bd761-129">3.0</span></span>
- <span data-ttu-id="bd761-130">2.2</span><span class="sxs-lookup"><span data-stu-id="bd761-130">2.2</span></span>
- <span data-ttu-id="bd761-131">2.0</span><span class="sxs-lookup"><span data-stu-id="bd761-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="bd761-132">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="bd761-132">How to install other versions</span></span>

<span data-ttu-id="bd761-133">Consultez la [documentation de Red Hat pour .net](https://access.redhat.com/documentation/net/5.0/) sur les étapes requises pour installer d’autres versions de .net.</span><span class="sxs-lookup"><span data-stu-id="bd761-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="bd761-134">✔️ RHEL 8</span><span class="sxs-lookup"><span data-stu-id="bd761-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="bd761-135">.NET est inclus dans les dépôts FluxApp pour RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="bd761-135">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="bd761-136">✔️ RHEL 7</span><span class="sxs-lookup"><span data-stu-id="bd761-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="bd761-137">La commande suivante installe le `scl-utils` Package :</span><span class="sxs-lookup"><span data-stu-id="bd761-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="bd761-138">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="bd761-138">Install the SDK</span></span>

<span data-ttu-id="bd761-139">Le kit de développement logiciel (SDK) .NET vous permet de développer des applications avec .NET.</span><span class="sxs-lookup"><span data-stu-id="bd761-139">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="bd761-140">Si vous installez le kit de développement logiciel (SDK) .NET, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="bd761-140">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="bd761-141">Pour installer le kit de développement logiciel (SDK) .NET, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bd761-141">To install the .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="bd761-142">Red Hat ne recommande pas l’activation permanente `rh-dotnet50` , car cela peut affecter d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="bd761-142">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="bd761-143">Par exemple, `rh-dotnet50` comprend une version de `libcurl` qui diffère de la version de base de RHEL.</span><span class="sxs-lookup"><span data-stu-id="bd761-143">For example, `rh-dotnet50` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="bd761-144">Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="bd761-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="bd761-145">Si vous souhaitez activer `rh-dotnet` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="bd761-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="bd761-146">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="bd761-146">Install the runtime</span></span>

<span data-ttu-id="bd761-147">Le runtime ASP.NET Core vous permet d’exécuter des applications qui ont été créées avec .NET et qui n’ont pas fourni le Runtime.</span><span class="sxs-lookup"><span data-stu-id="bd761-147">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="bd761-148">Les commandes suivantes installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET.</span><span class="sxs-lookup"><span data-stu-id="bd761-148">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="bd761-149">Sur votre terminal, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bd761-149">In your terminal, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50-aspnetcore-runtime-5.0 bash
```

<span data-ttu-id="bd761-150">Red Hat ne recommande pas l’activation permanente `rh-dotnet50-aspnetcore-runtime-5.0` , car cela peut affecter d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="bd761-150">Red Hat doesn't recommend permanently enabling `rh-dotnet50-aspnetcore-runtime-5.0` because it may affect other programs.</span></span> <span data-ttu-id="bd761-151">Par exemple, `rh-dotnet50-aspnetcore-runtime-5.0` comprend une version de `libcurl` qui diffère de la version de base de RHEL.</span><span class="sxs-lookup"><span data-stu-id="bd761-151">For example, `rh-dotnet50-aspnetcore-runtime-5.0` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="bd761-152">Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="bd761-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="bd761-153">Si vous souhaitez activer `rh-dotnet50-aspnetcore-runtime-5.0` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="bd761-153">If you want to enable `rh-dotnet50-aspnetcore-runtime-5.0` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50-aspnetcore-runtime-5.0
```

<span data-ttu-id="bd761-154">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET, qui n’inclut pas ASP.NET Core prise en charge : remplacez `rh-dotnet50-aspnetcore-runtime-5.0` dans les commandes précédentes par `rh-dotnet50-dotnet-runtime-5.0` .</span><span class="sxs-lookup"><span data-stu-id="bd761-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the previous commands with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="snap"></a><span data-ttu-id="bd761-155">Snap</span><span class="sxs-lookup"><span data-stu-id="bd761-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="bd761-156">Dépendances</span><span class="sxs-lookup"><span data-stu-id="bd761-156">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="bd761-157">Installation par script</span><span class="sxs-lookup"><span data-stu-id="bd761-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="bd761-158">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="bd761-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="bd761-159">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bd761-159">Next steps</span></span>

- [<span data-ttu-id="bd761-160">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bd761-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
