---
title: Installer .NET sur Alpine-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Alpine.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506817"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="22367-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Alpine</span><span class="sxs-lookup"><span data-stu-id="22367-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="22367-104">Cet article explique comment installer .NET sur Alpine.</span><span class="sxs-lookup"><span data-stu-id="22367-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="22367-105">Quand une version Alpine n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="22367-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="22367-106">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="22367-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="22367-107">Il n’y a aucun installeur pour Alpine.</span><span class="sxs-lookup"><span data-stu-id="22367-107">There are no installers for Alpine.</span></span> <span data-ttu-id="22367-108">Vous devez utiliser le [script d’installation](#scripted-install) ou suivre les instructions d' [installation manuelle](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="22367-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="22367-109">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="22367-109">Supported distributions</span></span>

<span data-ttu-id="22367-110">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Alpine sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="22367-110">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="22367-111">Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="22367-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="22367-112">Une ✔️ indique que la version de Alpine ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="22367-112">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="22367-113">Une ❌ indique que la version de Alpine ou .net n’est pas prise en charge sur cette version alpine.</span><span class="sxs-lookup"><span data-stu-id="22367-113">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="22367-114">Quand une version de .NET alpine et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="22367-114">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="22367-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="22367-115">Alpine</span></span>  | <span data-ttu-id="22367-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="22367-116">.NET Core 2.1</span></span> | <span data-ttu-id="22367-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="22367-117">.NET Core 3.1</span></span> | <span data-ttu-id="22367-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="22367-118">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="22367-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="22367-119">✔️ 3.12</span></span> | <span data-ttu-id="22367-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="22367-120">✔️ 2.1</span></span>        | <span data-ttu-id="22367-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="22367-121">✔️ 3.1</span></span>        | <span data-ttu-id="22367-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="22367-122">✔️ 5.0</span></span> |
| <span data-ttu-id="22367-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="22367-123">✔️ 3.11</span></span> | <span data-ttu-id="22367-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="22367-124">✔️ 2.1</span></span>        | <span data-ttu-id="22367-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="22367-125">✔️ 3.1</span></span>        | <span data-ttu-id="22367-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="22367-126">✔️ 5.0</span></span> |
| <span data-ttu-id="22367-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="22367-127">✔️ 3.10</span></span> | <span data-ttu-id="22367-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="22367-128">✔️ 2.1</span></span>        | <span data-ttu-id="22367-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="22367-129">✔️ 3.1</span></span>        | <span data-ttu-id="22367-130">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="22367-130">❌ 5.0</span></span> |
| <span data-ttu-id="22367-131">❌ 3,9</span><span class="sxs-lookup"><span data-stu-id="22367-131">❌ 3.9</span></span>  | <span data-ttu-id="22367-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="22367-132">✔️ 2.1</span></span>        | <span data-ttu-id="22367-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="22367-133">✔️ 3.1</span></span>        | <span data-ttu-id="22367-134">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="22367-134">❌ 5.0</span></span> |
| <span data-ttu-id="22367-135">❌ 3,8</span><span class="sxs-lookup"><span data-stu-id="22367-135">❌ 3.8</span></span>  | <span data-ttu-id="22367-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="22367-136">✔️ 2.1</span></span>        | <span data-ttu-id="22367-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="22367-137">✔️ 3.1</span></span>        | <span data-ttu-id="22367-138">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="22367-138">❌ 5.0</span></span> |

<span data-ttu-id="22367-139">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="22367-139">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="22367-140">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="22367-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="22367-141">3.0</span><span class="sxs-lookup"><span data-stu-id="22367-141">3.0</span></span>
- <span data-ttu-id="22367-142">2.2</span><span class="sxs-lookup"><span data-stu-id="22367-142">2.2</span></span>
- <span data-ttu-id="22367-143">2.0</span><span class="sxs-lookup"><span data-stu-id="22367-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="22367-144">Dépendances</span><span class="sxs-lookup"><span data-stu-id="22367-144">Dependencies</span></span>

<span data-ttu-id="22367-145">.NET sur Alpine Linux nécessite l’installation des dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="22367-145">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="22367-146">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="22367-146">icu-libs</span></span>
- <span data-ttu-id="22367-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="22367-147">krb5-libs</span></span>
- <span data-ttu-id="22367-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="22367-148">libgcc</span></span>
- <span data-ttu-id="22367-149">libintl</span><span class="sxs-lookup"><span data-stu-id="22367-149">libintl</span></span>
- <span data-ttu-id="22367-150">libssl 1.1 (Alpine v 3.9 ou supérieur)</span><span class="sxs-lookup"><span data-stu-id="22367-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="22367-151">libssl 1.0 (Alpine v 3.8 ou version antérieure)</span><span class="sxs-lookup"><span data-stu-id="22367-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="22367-152">libstdc++</span><span class="sxs-lookup"><span data-stu-id="22367-152">libstdc++</span></span>
- <span data-ttu-id="22367-153">zlib</span><span class="sxs-lookup"><span data-stu-id="22367-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="22367-154">Installation par script</span><span class="sxs-lookup"><span data-stu-id="22367-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="22367-155">Installation manuelle</span><span class="sxs-lookup"><span data-stu-id="22367-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="22367-156">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="22367-156">Next steps</span></span>

- [<span data-ttu-id="22367-157">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="22367-157">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
