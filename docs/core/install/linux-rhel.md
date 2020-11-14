---
title: Installer .NET sur RHEL-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: cb03f84cf84557d467f0a067b8d5629a843ec7e3
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594570"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="eb84f-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur RHEL</span><span class="sxs-lookup"><span data-stu-id="eb84f-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="eb84f-104">.NET est pris en charge sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="eb84f-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="eb84f-105">Cet article explique comment installer .NET sur RHEL.</span><span class="sxs-lookup"><span data-stu-id="eb84f-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="eb84f-106">Inscrire votre abonnement Red Hat</span><span class="sxs-lookup"><span data-stu-id="eb84f-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="eb84f-107">Pour installer .NET à partir de Red Hat sur RHEL, vous devez d’abord vous inscrire à l’aide du gestionnaire d’abonnements Red Hat.</span><span class="sxs-lookup"><span data-stu-id="eb84f-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="eb84f-108">Si cela n’a pas été fait sur votre système ou si vous n’en êtes pas sûr, consultez la [documentation du produit Red Hat pour .net](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="eb84f-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="eb84f-109">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="eb84f-109">Supported distributions</span></span>

<span data-ttu-id="eb84f-110">Le tableau suivant répertorie les versions .NET actuellement prises en charge sur RHEL 7 et RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="eb84f-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="eb84f-111">Ces versions restent prises en charge jusqu’à ce que la version de [.net ait atteint la fin du support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou que la version de RHEL ne soit plus prise en charge.</span><span class="sxs-lookup"><span data-stu-id="eb84f-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="eb84f-112">Une ✔️ indique que la version de RHEL ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="eb84f-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="eb84f-113">Une ❌ indique que la version de RHEL ou de .net n’est pas prise en charge sur cette version de RHEL.</span><span class="sxs-lookup"><span data-stu-id="eb84f-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="eb84f-114">Quand une version de RHEL et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="eb84f-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="eb84f-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="eb84f-115">RHEL</span></span>                     | <span data-ttu-id="eb84f-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eb84f-116">.NET Core 2.1</span></span> | <span data-ttu-id="eb84f-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="eb84f-117">.NET Core 3.1</span></span> | <span data-ttu-id="eb84f-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="eb84f-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="eb84f-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="eb84f-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="eb84f-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="eb84f-120">✔️ 2.1</span></span>        | <span data-ttu-id="eb84f-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="eb84f-121">✔️ 3.1</span></span>        | <span data-ttu-id="eb84f-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="eb84f-122">✔️ 5.0</span></span> |
| <span data-ttu-id="eb84f-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="eb84f-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="eb84f-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="eb84f-124">✔️ 2.1</span></span>        | <span data-ttu-id="eb84f-125">✔️ [3,1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="eb84f-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="eb84f-126">✔️ [5,0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="eb84f-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="eb84f-127">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="eb84f-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="eb84f-128">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="eb84f-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="eb84f-129">3.0</span><span class="sxs-lookup"><span data-stu-id="eb84f-129">3.0</span></span>
- <span data-ttu-id="eb84f-130">2.2</span><span class="sxs-lookup"><span data-stu-id="eb84f-130">2.2</span></span>
- <span data-ttu-id="eb84f-131">2.0</span><span class="sxs-lookup"><span data-stu-id="eb84f-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="eb84f-132">Comment installer d’autres versions</span><span class="sxs-lookup"><span data-stu-id="eb84f-132">How to install other versions</span></span>

<span data-ttu-id="eb84f-133">Consultez la [documentation de Red Hat pour .net](https://access.redhat.com/documentation/net/5.0/) sur les étapes requises pour installer d’autres versions de .net.</span><span class="sxs-lookup"><span data-stu-id="eb84f-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="eb84f-134">✔️ RHEL 8</span><span class="sxs-lookup"><span data-stu-id="eb84f-134">RHEL 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="eb84f-135">.NET 5,0 n’est pas encore disponible dans les dépôts FluxApp, mais .NET Core 3,1 est.</span><span class="sxs-lookup"><span data-stu-id="eb84f-135">.NET 5.0 isn't yet available in the AppStream repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="eb84f-136">Pour installer .NET Core 3,1, utilisez la `dnf install` commande avec le package approprié, tel que `aspnetcore-runtime-3.1` ou `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="eb84f-136">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="eb84f-137">Les instructions suivantes concernent .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="eb84f-137">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="eb84f-138">RHEL 7 ✔️ .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="eb84f-138">RHEL 7 ✔️ .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-yum.md)]

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="eb84f-139">RHEL 7 ✔️ .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="eb84f-139">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="eb84f-140">La commande suivante installe le `scl-utils` Package :</span><span class="sxs-lookup"><span data-stu-id="eb84f-140">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="eb84f-141">Installer le SDK</span><span class="sxs-lookup"><span data-stu-id="eb84f-141">Install the SDK</span></span>

<span data-ttu-id="eb84f-142">Kit SDK .NET Core vous permet de développer des applications avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb84f-142">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="eb84f-143">Si vous installez kit SDK .NET Core, vous n’avez pas besoin d’installer le runtime correspondant.</span><span class="sxs-lookup"><span data-stu-id="eb84f-143">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="eb84f-144">Pour installer kit SDK .NET Core, exécutez les commandes suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb84f-144">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="eb84f-145">Red Hat ne recommande pas l’activation permanente `rh-dotnet31` , car cela peut affecter d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="eb84f-145">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="eb84f-146">Par exemple, `rh-dotnet31` comprend une version de `libcurl` qui diffère de la version de base de RHEL.</span><span class="sxs-lookup"><span data-stu-id="eb84f-146">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="eb84f-147">Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="eb84f-147">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="eb84f-148">Si vous souhaitez activer `rh-dotnet` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="eb84f-148">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="eb84f-149">Installer le runtime</span><span class="sxs-lookup"><span data-stu-id="eb84f-149">Install the runtime</span></span>

<span data-ttu-id="eb84f-150">Le Runtime .NET Core vous permet d’exécuter des applications qui ont été créées avec .NET Core et qui ne comportent pas le Runtime.</span><span class="sxs-lookup"><span data-stu-id="eb84f-150">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="eb84f-151">Les commandes ci-dessous installent le runtime ASP.NET Core, qui est le runtime le plus compatible pour .NET Core.</span><span class="sxs-lookup"><span data-stu-id="eb84f-151">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="eb84f-152">Dans votre terminal, exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="eb84f-152">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="eb84f-153">Red Hat ne recommande pas l’activation permanente `rh-dotnet31-aspnetcore-runtime-3.1` , car cela peut affecter d’autres programmes.</span><span class="sxs-lookup"><span data-stu-id="eb84f-153">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="eb84f-154">Par exemple, `rh-dotnet31-aspnetcore-runtime-3.1` comprend une version de `libcurl` qui diffère de la version de base de RHEL.</span><span class="sxs-lookup"><span data-stu-id="eb84f-154">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="eb84f-155">Cela peut entraîner des problèmes dans les programmes qui n’attendent pas une version différente de `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="eb84f-155">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="eb84f-156">Si vous souhaitez activer `rh-dotnet31-aspnetcore-runtime-3.1` définitivement, ajoutez la ligne suivante à votre fichier _~ fichier/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="eb84f-156">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="eb84f-157">Comme alternative au runtime ASP.NET Core, vous pouvez installer le Runtime .NET Core qui n’inclut pas la prise en charge de ASP.NET Core : remplacez `rh-dotnet31-aspnetcore-runtime-3.1` dans les commandes ci-dessus par `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="eb84f-157">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="eb84f-158">Snap</span><span class="sxs-lookup"><span data-stu-id="eb84f-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="eb84f-159">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="eb84f-159">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="eb84f-160">Installation par script</span><span class="sxs-lookup"><span data-stu-id="eb84f-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="eb84f-161">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="eb84f-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="eb84f-162">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="eb84f-162">Next steps</span></span>

- [<span data-ttu-id="eb84f-163">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="eb84f-163">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
