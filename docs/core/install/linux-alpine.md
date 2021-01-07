---
title: Installer .NET sur Alpine-.NET
description: Montre les différentes façons d’installer le kit de développement logiciel (SDK) .NET et le Runtime .NET sur Alpine.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 6adaa905c400b45526ebbc3d8e2606522863eec3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970848"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="00b7d-103">Installer le kit de développement logiciel (SDK) .NET ou le Runtime .NET sur Alpine</span><span class="sxs-lookup"><span data-stu-id="00b7d-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="00b7d-104">Cet article explique comment installer .NET sur Alpine.</span><span class="sxs-lookup"><span data-stu-id="00b7d-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="00b7d-105">Quand une version Alpine n’est plus prise en charge, .NET n’est plus pris en charge avec cette version.</span><span class="sxs-lookup"><span data-stu-id="00b7d-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="00b7d-106">Toutefois, ces instructions peuvent vous aider à faire fonctionner .NET sur ces versions, même si elles ne sont pas prises en charge.</span><span class="sxs-lookup"><span data-stu-id="00b7d-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="install"></a><span data-ttu-id="00b7d-107">Installer</span><span class="sxs-lookup"><span data-stu-id="00b7d-107">Install</span></span>

<span data-ttu-id="00b7d-108">Les programmes d’installation ne sont pas disponibles pour Alpine Linux.</span><span class="sxs-lookup"><span data-stu-id="00b7d-108">Installers aren't available for Alpine Linux.</span></span> <span data-ttu-id="00b7d-109">Vous devez installer .NET de l’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="00b7d-109">You must install .NET in one of the following ways:</span></span>

- [<span data-ttu-id="00b7d-110">Package d’alignement</span><span class="sxs-lookup"><span data-stu-id="00b7d-110">Snap package</span></span>](linux-snap.md)
- [<span data-ttu-id="00b7d-111">Installation par script avec _install-dotnet.sh_</span><span class="sxs-lookup"><span data-stu-id="00b7d-111">Scripted install with _install-dotnet.sh_</span></span>](linux-scripted-manual.md#scripted-install)
- [<span data-ttu-id="00b7d-112">Extraction binaire manuelle</span><span class="sxs-lookup"><span data-stu-id="00b7d-112">Manual binary extraction</span></span>](linux-scripted-manual.md#manual-install)

## <a name="supported-distributions"></a><span data-ttu-id="00b7d-113">Distributions prises en charge</span><span class="sxs-lookup"><span data-stu-id="00b7d-113">Supported distributions</span></span>

<span data-ttu-id="00b7d-114">Le tableau suivant répertorie les versions de .NET actuellement prises en charge et les versions de Alpine sur lesquelles elles sont prises en charge.</span><span class="sxs-lookup"><span data-stu-id="00b7d-114">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="00b7d-115">Ces versions restent prises en charge jusqu’à la [fin de la prise en charge](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) de la version de .net ou de la version de [Alpine](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="00b7d-115">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="00b7d-116">Une ✔️ indique que la version de Alpine ou .NET est toujours prise en charge.</span><span class="sxs-lookup"><span data-stu-id="00b7d-116">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="00b7d-117">Une ❌ indique que la version de Alpine ou .net n’est pas prise en charge sur cette version alpine.</span><span class="sxs-lookup"><span data-stu-id="00b7d-117">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="00b7d-118">Quand une version de .NET alpine et une version de .NET sont ✔️, cette combinaison de système d’exploitation et .NET est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="00b7d-118">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="00b7d-119">Alpine</span><span class="sxs-lookup"><span data-stu-id="00b7d-119">Alpine</span></span>  | <span data-ttu-id="00b7d-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="00b7d-120">.NET Core 2.1</span></span> | <span data-ttu-id="00b7d-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="00b7d-121">.NET Core 3.1</span></span> | <span data-ttu-id="00b7d-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="00b7d-122">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="00b7d-123">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="00b7d-123">✔️ 3.12</span></span> | <span data-ttu-id="00b7d-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-124">✔️ 2.1</span></span>        | <span data-ttu-id="00b7d-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-125">✔️ 3.1</span></span>        | <span data-ttu-id="00b7d-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="00b7d-126">✔️ 5.0</span></span> |
| <span data-ttu-id="00b7d-127">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="00b7d-127">✔️ 3.11</span></span> | <span data-ttu-id="00b7d-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-128">✔️ 2.1</span></span>        | <span data-ttu-id="00b7d-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-129">✔️ 3.1</span></span>        | <span data-ttu-id="00b7d-130">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="00b7d-130">✔️ 5.0</span></span> |
| <span data-ttu-id="00b7d-131">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="00b7d-131">✔️ 3.10</span></span> | <span data-ttu-id="00b7d-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-132">✔️ 2.1</span></span>        | <span data-ttu-id="00b7d-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-133">✔️ 3.1</span></span>        | <span data-ttu-id="00b7d-134">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="00b7d-134">❌ 5.0</span></span> |
| <span data-ttu-id="00b7d-135">❌ 3,9</span><span class="sxs-lookup"><span data-stu-id="00b7d-135">❌ 3.9</span></span>  | <span data-ttu-id="00b7d-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-136">✔️ 2.1</span></span>        | <span data-ttu-id="00b7d-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-137">✔️ 3.1</span></span>        | <span data-ttu-id="00b7d-138">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="00b7d-138">❌ 5.0</span></span> |
| <span data-ttu-id="00b7d-139">❌ 3,8</span><span class="sxs-lookup"><span data-stu-id="00b7d-139">❌ 3.8</span></span>  | <span data-ttu-id="00b7d-140">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-140">✔️ 2.1</span></span>        | <span data-ttu-id="00b7d-141">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="00b7d-141">✔️ 3.1</span></span>        | <span data-ttu-id="00b7d-142">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="00b7d-142">❌ 5.0</span></span> |

<span data-ttu-id="00b7d-143">Les versions suivantes de .NET ne sont plus prises en charge.</span><span class="sxs-lookup"><span data-stu-id="00b7d-143">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="00b7d-144">Les téléchargements sont toujours publiés :</span><span class="sxs-lookup"><span data-stu-id="00b7d-144">The downloads for these still remain published:</span></span>

- <span data-ttu-id="00b7d-145">3.0</span><span class="sxs-lookup"><span data-stu-id="00b7d-145">3.0</span></span>
- <span data-ttu-id="00b7d-146">2.2</span><span class="sxs-lookup"><span data-stu-id="00b7d-146">2.2</span></span>
- <span data-ttu-id="00b7d-147">2.0</span><span class="sxs-lookup"><span data-stu-id="00b7d-147">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="00b7d-148">Dépendances</span><span class="sxs-lookup"><span data-stu-id="00b7d-148">Dependencies</span></span>

<span data-ttu-id="00b7d-149">.NET sur Alpine Linux nécessite l’installation des dépendances suivantes :</span><span class="sxs-lookup"><span data-stu-id="00b7d-149">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="00b7d-150">ICU-libs</span><span class="sxs-lookup"><span data-stu-id="00b7d-150">icu-libs</span></span>
- <span data-ttu-id="00b7d-151">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="00b7d-151">krb5-libs</span></span>
- <span data-ttu-id="00b7d-152">libgcc</span><span class="sxs-lookup"><span data-stu-id="00b7d-152">libgcc</span></span>
- <span data-ttu-id="00b7d-153">libintl</span><span class="sxs-lookup"><span data-stu-id="00b7d-153">libintl</span></span>
- <span data-ttu-id="00b7d-154">libssl 1.1 (Alpine v 3.9 ou supérieur)</span><span class="sxs-lookup"><span data-stu-id="00b7d-154">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="00b7d-155">libssl 1.0 (Alpine v 3.8 ou version antérieure)</span><span class="sxs-lookup"><span data-stu-id="00b7d-155">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="00b7d-156">libstdc++</span><span class="sxs-lookup"><span data-stu-id="00b7d-156">libstdc++</span></span>
- <span data-ttu-id="00b7d-157">zlib</span><span class="sxs-lookup"><span data-stu-id="00b7d-157">zlib</span></span>

## <a name="next-steps"></a><span data-ttu-id="00b7d-158">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="00b7d-158">Next steps</span></span>

- [<span data-ttu-id="00b7d-159">Comment activer la saisie semi-automatique via la touche TAB pour .NET CLI</span><span class="sxs-lookup"><span data-stu-id="00b7d-159">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="00b7d-160">Didacticiel : créer une application console avec le kit de développement logiciel (SDK) .NET à l’aide de Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="00b7d-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
