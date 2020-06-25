---
title: Installer .NET Core sur RHEL-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur RHEL.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 4a406fe1834c16bab9a5548b69206b51270b33fa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324710"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="1fde5-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur RHEL</span><span class="sxs-lookup"><span data-stu-id="1fde5-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="1fde5-104">.NET Core est pris en charge sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="1fde5-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="1fde5-105">Cet article explique comment installer .NET Core sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="1fde5-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1fde5-106">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="1fde5-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="1fde5-107">Pour installer .NET Core à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="1fde5-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1fde5-108">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="1fde5-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="1fde5-109">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="1fde5-109">Supported distributions</span></span>

<span data-ttu-id="1fde5-110">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge sur RHEL 7 et RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="1fde5-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="1fde5-111">Ces versions restent prises en charge jusqu’à ce que la version de [.net Core ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de RHEL ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1fde5-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="1fde5-112">Une ✔️ indique que la version de RHEL ou de .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="1fde5-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="1fde5-113">Une ❌ indique que la version de RHEL ou de .net Core n’est pas prise en charge sur cette version de RHEL.</span><span class="sxs-lookup"><span data-stu-id="1fde5-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="1fde5-114">Quand une version de RHEL et une version de .NET Core ont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1fde5-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="1fde5-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="1fde5-115">RHEL</span></span>                   | <span data-ttu-id="1fde5-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1fde5-116">.NET Core 2.1</span></span> | <span data-ttu-id="1fde5-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1fde5-117">.NET Core 3.1</span></span> | <span data-ttu-id="1fde5-118">.NET 5 Preview (installation manuelle uniquement)</span><span class="sxs-lookup"><span data-stu-id="1fde5-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1fde5-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="1fde5-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="1fde5-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1fde5-120">✔️ 2.1</span></span>        | <span data-ttu-id="1fde5-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1fde5-121">✔️ 3.1</span></span>        | <span data-ttu-id="1fde5-122">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="1fde5-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="1fde5-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="1fde5-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="1fde5-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1fde5-124">✔️ 2.1</span></span>        | <span data-ttu-id="1fde5-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1fde5-125">✔️ 3.1</span></span>        | <span data-ttu-id="1fde5-126">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="1fde5-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="1fde5-127">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="1fde5-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="1fde5-128">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="1fde5-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1fde5-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1fde5-129">3.0</span></span>
- <span data-ttu-id="1fde5-130">2.2</span><span class="sxs-lookup"><span data-stu-id="1fde5-130">2.2</span></span>
- <span data-ttu-id="1fde5-131">2.0</span><span class="sxs-lookup"><span data-stu-id="1fde5-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1fde5-132">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="1fde5-132">How to install other versions</span></span>

<span data-ttu-id="1fde5-133">Consultez la [documentation de Red Hat pour .net Core](https://access.redhat.com/documentation/net_core/) sur les étapes requises pour installer d’autres versions de .net core.</span><span class="sxs-lookup"><span data-stu-id="1fde5-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="1fde5-134">✔️ RHEL 8</span><span class="sxs-lookup"><span data-stu-id="1fde5-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="1fde5-135">.NET Core est inclus dans les dépôts FluxApp pour RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="1fde5-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="1fde5-136">✔️ RHEL 7</span><span class="sxs-lookup"><span data-stu-id="1fde5-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="1fde5-137">La commande suivante installe le `scl-utils` Package :</span><span class="sxs-lookup"><span data-stu-id="1fde5-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="1fde5-138">Installer le Kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="1fde5-138">Install the SDK</span></span>

<span data-ttu-id="1fde5-139">Kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1fde5-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="1fde5-140">Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="1fde5-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1fde5-141">Pour installer kit SDK .NET Core, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1fde5-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="1fde5-142">Red Hat ne recommande pas l’activation permanente `rh-dotnet31` , car cela peut affecter d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="1fde5-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="1fde5-143">Par exemple, `rh-dotnet31` comprend une version de `libcurl` qui diffère de la version de base de RHEL.</span><span class="sxs-lookup"><span data-stu-id="1fde5-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1fde5-144">Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="1fde5-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1fde5-145">Si vous souhaitez activer `rh-dotnet` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="1fde5-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="1fde5-146">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="1fde5-146">Install the runtime</span></span>

<span data-ttu-id="1fde5-147">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="1fde5-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="1fde5-148">Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1fde5-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="1fde5-149">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="1fde5-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="1fde5-150">Red Hat ne recommande pas l’activation permanente `rh-dotnet31-aspnetcore-runtime-3.1` , car cela peut affecter d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="1fde5-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="1fde5-151">Par exemple, `rh-dotnet31-aspnetcore-runtime-3.1` comprend une version de `libcurl` qui diffère de la version de base de RHEL.</span><span class="sxs-lookup"><span data-stu-id="1fde5-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1fde5-152">Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="1fde5-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1fde5-153">Si vous souhaitez activer `rh-dotnet31-aspnetcore-runtime-3.1` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="1fde5-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="1fde5-154">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas la prise en charge de ASP.NET Core : remplacez `rh-dotnet31-aspnetcore-runtime-3.1` dans les commandes ci-dessus par `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="1fde5-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="1fde5-155">Snap</span><span class="sxs-lookup"><span data-stu-id="1fde5-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="1fde5-156">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="1fde5-156">Dependencies</span></span>

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="1fde5-157">Installation par script</span><span class="sxs-lookup"><span data-stu-id="1fde5-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="1fde5-158">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="1fde5-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="1fde5-159">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="1fde5-159">Next steps</span></span>

- [<span data-ttu-id="1fde5-160">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1fde5-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
