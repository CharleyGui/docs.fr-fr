---
title: Installer .NET Core sur Alpine-.NET Core
description: Montre les différentes façons d’installer kit SDK .NET Core et le Runtime .NET Core sur Alpine.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 0efe3bbacbe573b77eae8818ea29b5a3867e4570
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619518"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="944e0-103">Installer kit SDK .NET Core ou le Runtime .NET Core sur Alpine</span><span class="sxs-lookup"><span data-stu-id="944e0-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="944e0-104">Cet article explique comment installer .NET Core sur Alpine.</span><span class="sxs-lookup"><span data-stu-id="944e0-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="944e0-105">Quand une version Alpine n’est plus prise en charge, .NET Core n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="944e0-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="944e0-106">Toutefois, ces instructions peuvent vous aider à obtenir .NET Core s’exécutant sur ces versions, même s’il n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="944e0-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="944e0-107">Il n’y a aucun installeur pour Alpine.</span><span class="sxs-lookup"><span data-stu-id="944e0-107">There are no installers for Alpine.</span></span> <span data-ttu-id="944e0-108">Vous devez utiliser le [script d’installation](#scripted-install) ou suivre les instructions d' [installation manuelle](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="944e0-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="944e0-109">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="944e0-109">Supported distributions</span></span>

<span data-ttu-id="944e0-110">Le tableau suivant répertorie les versions de .NET Core actuellement prises en charge et les versions de Alpine sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="944e0-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="944e0-111">Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net Core ou de la version de [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="944e0-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="944e0-112">Une ✔️ indique que la version de Alpine ou .NET Core est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="944e0-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="944e0-113">Une ❌ indique que la version de Alpine ou .net Core n’est pas prise en charge sur cette version alpine.</span><span class="sxs-lookup"><span data-stu-id="944e0-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="944e0-114">Quand une version de .NET Core et une version de .NET Core sont ✔️, cette combinaison de système d’exploitation et .NET sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="944e0-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="944e0-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="944e0-115">Alpine</span></span>                   | <span data-ttu-id="944e0-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="944e0-116">.NET Core 2.1</span></span> | <span data-ttu-id="944e0-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="944e0-117">.NET Core 3.1</span></span> | <span data-ttu-id="944e0-118">Version préliminaire de .NET 5</span><span class="sxs-lookup"><span data-stu-id="944e0-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="944e0-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="944e0-119">✔️ 3.12</span></span>  | <span data-ttu-id="944e0-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="944e0-120">✔️ 2.1</span></span>        | <span data-ttu-id="944e0-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="944e0-121">✔️ 3.1</span></span>        | <span data-ttu-id="944e0-122">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="944e0-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="944e0-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="944e0-123">✔️ 3.11</span></span>  | <span data-ttu-id="944e0-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="944e0-124">✔️ 2.1</span></span>        | <span data-ttu-id="944e0-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="944e0-125">✔️ 3.1</span></span>        | <span data-ttu-id="944e0-126">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="944e0-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="944e0-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="944e0-127">✔️ 3.10</span></span>  | <span data-ttu-id="944e0-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="944e0-128">✔️ 2.1</span></span>        | <span data-ttu-id="944e0-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="944e0-129">✔️ 3.1</span></span>        | <span data-ttu-id="944e0-130">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="944e0-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="944e0-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="944e0-131">✔️ 3.9</span></span>   | <span data-ttu-id="944e0-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="944e0-132">✔️ 2.1</span></span>        | <span data-ttu-id="944e0-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="944e0-133">✔️ 3.1</span></span>        | <span data-ttu-id="944e0-134">✔️ version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="944e0-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="944e0-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="944e0-135">❌ 3.8</span></span>   | <span data-ttu-id="944e0-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="944e0-136">✔️ 2.1</span></span>        | <span data-ttu-id="944e0-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="944e0-137">❌ 3.1</span></span>        | <span data-ttu-id="944e0-138">❌version préliminaire 5,0</span><span class="sxs-lookup"><span data-stu-id="944e0-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="944e0-139">Les versions suivantes de .NET Core ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="944e0-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="944e0-140">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="944e0-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="944e0-141">3.0</span><span class="sxs-lookup"><span data-stu-id="944e0-141">3.0</span></span>
- <span data-ttu-id="944e0-142">2.2</span><span class="sxs-lookup"><span data-stu-id="944e0-142">2.2</span></span>
- <span data-ttu-id="944e0-143">2.0</span><span class="sxs-lookup"><span data-stu-id="944e0-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="944e0-144">Les dépendances</span><span class="sxs-lookup"><span data-stu-id="944e0-144">Dependencies</span></span>

<span data-ttu-id="944e0-145">.NET Core sur Alpine Linux nécessite l’installation des dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="944e0-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="944e0-146">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="944e0-146">icu-libs</span></span>
- <span data-ttu-id="944e0-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="944e0-147">krb5-libs</span></span>
- <span data-ttu-id="944e0-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="944e0-148">libgcc</span></span>
- <span data-ttu-id="944e0-149">libintl</span><span class="sxs-lookup"><span data-stu-id="944e0-149">libintl</span></span>
- <span data-ttu-id="944e0-150">libssl 1.1 (Alpine v 3.9 ou supérieur)</span><span class="sxs-lookup"><span data-stu-id="944e0-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="944e0-151">libssl 1.0 (Alpine v 3.8 ou version antérieure)</span><span class="sxs-lookup"><span data-stu-id="944e0-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="944e0-152">libstdc++</span><span class="sxs-lookup"><span data-stu-id="944e0-152">libstdc++</span></span>
- <span data-ttu-id="944e0-153">zlib</span><span class="sxs-lookup"><span data-stu-id="944e0-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="944e0-154">Installation par script</span><span class="sxs-lookup"><span data-stu-id="944e0-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="944e0-155">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="944e0-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="944e0-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="944e0-156">Next steps</span></span>

- [<span data-ttu-id="944e0-157">Didacticiel : créer une application console avec kit SDK .NET Core à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="944e0-157">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
