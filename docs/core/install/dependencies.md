---
title: Dépendances de kit SDK .NET Core et d’exécution-.NET Core
description: Décrit en détail la configuration requise pour le système d’exploitation et l’architecture de l’UC pour installer le kit SDK .NET Core et le runtime sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 11/06/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: b79ec6a9723cbd44717d5f187213278556c0b6ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451100"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="2ee5b-103">Dépendances et exigences de .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ee5b-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="2ee5b-104">Cet article détaille les systèmes d’exploitation et l’architecture du processeur pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="2ee5b-105">Systèmes d'exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="2ee5b-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="2ee5b-106">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ee5b-106">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="2ee5b-107">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-107">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-108">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-109">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ee5b-109">OS</span></span>                            | <span data-ttu-id="2ee5b-110">Version</span><span class="sxs-lookup"><span data-stu-id="2ee5b-110">Version</span></span>                        | <span data-ttu-id="2ee5b-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="2ee5b-112">Client Windows</span><span class="sxs-lookup"><span data-stu-id="2ee5b-112">Windows Client</span></span>                | <span data-ttu-id="2ee5b-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="2ee5b-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-114">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-115">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="2ee5b-115">Windows 10 Client</span></span>             | <span data-ttu-id="2ee5b-116">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-116">Version 1607+</span></span>                  | <span data-ttu-id="2ee5b-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-117">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="2ee5b-118">Windows Server</span></span>                | <span data-ttu-id="2ee5b-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-119">2012 R2+</span></span>                       | <span data-ttu-id="2ee5b-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-120">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="2ee5b-121">Nano Server</span></span>                   | <span data-ttu-id="2ee5b-122">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-122">Version 1803+</span></span>                  | <span data-ttu-id="2ee5b-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="2ee5b-123">x64, ARM32</span></span>      |

<span data-ttu-id="2ee5b-124">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-124">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="2ee5b-125">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-125">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="2ee5b-126">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,2 :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-126">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-127">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-128">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ee5b-128">OS</span></span>                            | <span data-ttu-id="2ee5b-129">Version</span><span class="sxs-lookup"><span data-stu-id="2ee5b-129">Version</span></span>                        | <span data-ttu-id="2ee5b-130">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="2ee5b-131">Client Windows</span><span class="sxs-lookup"><span data-stu-id="2ee5b-131">Windows Client</span></span>                | <span data-ttu-id="2ee5b-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="2ee5b-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-133">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-134">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="2ee5b-134">Windows 10 Client</span></span>             | <span data-ttu-id="2ee5b-135">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-135">Version 1607+</span></span>                  | <span data-ttu-id="2ee5b-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-136">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="2ee5b-137">Windows Server</span></span>                | <span data-ttu-id="2ee5b-138">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-138">2008 R2 SP1+</span></span>                   | <span data-ttu-id="2ee5b-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-139">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="2ee5b-140">Nano Server</span></span>                   | <span data-ttu-id="2ee5b-141">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-141">Version 1803+</span></span>                   | <span data-ttu-id="2ee5b-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="2ee5b-142">x64, ARM32</span></span>      |

<span data-ttu-id="2ee5b-143">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-143">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2ee5b-144">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-144">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="2ee5b-145">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,1 :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-145">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-146">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-147">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ee5b-147">OS</span></span>                            | <span data-ttu-id="2ee5b-148">Version</span><span class="sxs-lookup"><span data-stu-id="2ee5b-148">Version</span></span>                        | <span data-ttu-id="2ee5b-149">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="2ee5b-150">Client Windows</span><span class="sxs-lookup"><span data-stu-id="2ee5b-150">Windows Client</span></span>                | <span data-ttu-id="2ee5b-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="2ee5b-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-152">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-153">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="2ee5b-153">Windows 10 Client</span></span>             | <span data-ttu-id="2ee5b-154">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-154">Version 1607+</span></span>                  | <span data-ttu-id="2ee5b-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-155">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="2ee5b-156">Windows Server</span></span>                | <span data-ttu-id="2ee5b-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="2ee5b-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="2ee5b-158">x64, x86</span></span>        |
| <span data-ttu-id="2ee5b-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="2ee5b-159">Nano Server</span></span>                   | <span data-ttu-id="2ee5b-160">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-160">Version 1803+</span></span>                  | <span data-ttu-id="2ee5b-161">64x</span><span class="sxs-lookup"><span data-stu-id="2ee5b-161">x64,</span></span>            |

<span data-ttu-id="2ee5b-162">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-162">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="2ee5b-163">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-163">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="2ee5b-164">Des dépendances supplémentaires sont requises si vous installez le kit de développement logiciel (SDK) .NET ou le runtime sur les versions suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-164">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="2ee5b-165">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-165">Windows 7 SP1</span></span>
- <span data-ttu-id="2ee5b-166">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-166">Windows Vista SP 2</span></span>
- <span data-ttu-id="2ee5b-167">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-167">Windows 8.1</span></span>
- <span data-ttu-id="2ee5b-168">Windows Server 2008 R2 SP2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-168">Windows Server 2008 R2</span></span>
- <span data-ttu-id="2ee5b-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-169">Windows Server 2012 R2</span></span>

<span data-ttu-id="2ee5b-170">Installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-170">Install the following:</span></span>

- <span data-ttu-id="2ee5b-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-171">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="2ee5b-172">KB2533623</span><span class="sxs-lookup"><span data-stu-id="2ee5b-172">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="2ee5b-173">La configuration requise ci-dessus est également requise si vous rencontrez l’une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-173">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="2ee5b-174">Le programme ne peut pas démarrer, car l' *API-MS-Win-CRT-Runtime-L1-1 1/-0. dll* est absente de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-174">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="2ee5b-175">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-175">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="2ee5b-176">\- ou -</span><span class="sxs-lookup"><span data-stu-id="2ee5b-176">\- or -</span></span>
>
> <span data-ttu-id="2ee5b-177">La bibliothèque *hostfxr. dll* a été trouvée, mais son chargement à partir de *C :\\\<path_to_app >\\hostfxr. dll* a échoué.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-177">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="2ee5b-178">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2ee5b-178">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="2ee5b-179">.NET Core 3,0 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-179">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="2ee5b-180">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-180">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="2ee5b-181">.NET Core 3,0 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-181">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-182">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-182">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-183">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ee5b-183">OS</span></span>                             | <span data-ttu-id="2ee5b-184">Version</span><span class="sxs-lookup"><span data-stu-id="2ee5b-184">Version</span></span>               | <span data-ttu-id="2ee5b-185">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-185">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="2ee5b-186">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-186">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="2ee5b-187">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="2ee5b-187">6, 7, 8</span></span>               | <span data-ttu-id="2ee5b-188">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-188">x64</span></span> |
| <span data-ttu-id="2ee5b-189">CentOS</span><span class="sxs-lookup"><span data-stu-id="2ee5b-189">CentOS</span></span>                         | <span data-ttu-id="2ee5b-190">plus de 7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-190">7+</span></span>                    | <span data-ttu-id="2ee5b-191">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-191">x64</span></span> |
| <span data-ttu-id="2ee5b-192">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-192">Oracle Linux</span></span>                   | <span data-ttu-id="2ee5b-193">plus de 7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-193">7+</span></span>                    | <span data-ttu-id="2ee5b-194">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-194">x64</span></span> |
| <span data-ttu-id="2ee5b-195">Fedora</span><span class="sxs-lookup"><span data-stu-id="2ee5b-195">Fedora</span></span>                         | <span data-ttu-id="2ee5b-196">29 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-196">29+</span></span>                   | <span data-ttu-id="2ee5b-197">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-197">x64</span></span> |
| <span data-ttu-id="2ee5b-198">Debian</span><span class="sxs-lookup"><span data-stu-id="2ee5b-198">Debian</span></span>                         | <span data-ttu-id="2ee5b-199">9+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-199">9+</span></span>                    | <span data-ttu-id="2ee5b-200">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-200">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="2ee5b-201">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2ee5b-201">Ubuntu</span></span>                         | <span data-ttu-id="2ee5b-202">16.04+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-202">16.04+</span></span>                | <span data-ttu-id="2ee5b-203">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-203">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="2ee5b-204">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="2ee5b-204">Linux Mint</span></span>                     | <span data-ttu-id="2ee5b-205">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="2ee5b-205">18+</span></span>                   | <span data-ttu-id="2ee5b-206">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-206">x64</span></span> |
| <span data-ttu-id="2ee5b-207">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2ee5b-207">openSUSE</span></span>                       | <span data-ttu-id="2ee5b-208">plus de 15</span><span class="sxs-lookup"><span data-stu-id="2ee5b-208">15+</span></span>                   | <span data-ttu-id="2ee5b-209">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-209">x64</span></span> |
| <span data-ttu-id="2ee5b-210">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-210">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="2ee5b-211">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-211">12 SP2+</span></span>               | <span data-ttu-id="2ee5b-212">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-212">x64</span></span> |
| <span data-ttu-id="2ee5b-213">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-213">Alpine Linux</span></span>                   | <span data-ttu-id="2ee5b-214">3.8+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-214">3.8+</span></span>                  | <span data-ttu-id="2ee5b-215">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-215">x64, ARM64</span></span> |

<span data-ttu-id="2ee5b-216">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-216">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="2ee5b-217">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-217">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22tabnetcore22"></a>[<span data-ttu-id="2ee5b-218">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-218">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="2ee5b-219">.NET Core 2,2 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-219">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="2ee5b-220">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-220">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="2ee5b-221">.NET Core 2,2 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-221">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-222">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-222">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-223">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ee5b-223">OS</span></span>                             |  <span data-ttu-id="2ee5b-224">Version</span><span class="sxs-lookup"><span data-stu-id="2ee5b-224">Version</span></span>                |  <span data-ttu-id="2ee5b-225">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-225">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="2ee5b-226">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-226">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="2ee5b-227">6, 7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-227">6, 7</span></span>                   | <span data-ttu-id="2ee5b-228">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-228">x64</span></span> |
| <span data-ttu-id="2ee5b-229">CentOS</span><span class="sxs-lookup"><span data-stu-id="2ee5b-229">CentOS</span></span>                         |  <span data-ttu-id="2ee5b-230">7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-230">7</span></span>                      | <span data-ttu-id="2ee5b-231">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-231">x64</span></span> |
| <span data-ttu-id="2ee5b-232">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-232">Oracle Linux</span></span>                   |  <span data-ttu-id="2ee5b-233">7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-233">7</span></span>                      | <span data-ttu-id="2ee5b-234">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-234">x64</span></span> |
| <span data-ttu-id="2ee5b-235">Fedora</span><span class="sxs-lookup"><span data-stu-id="2ee5b-235">Fedora</span></span>                         |  <span data-ttu-id="2ee5b-236">29, 30</span><span class="sxs-lookup"><span data-stu-id="2ee5b-236">29, 30</span></span>                 | <span data-ttu-id="2ee5b-237">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-237">x64</span></span> |
| <span data-ttu-id="2ee5b-238">Debian</span><span class="sxs-lookup"><span data-stu-id="2ee5b-238">Debian</span></span>                         |  <span data-ttu-id="2ee5b-239">9</span><span class="sxs-lookup"><span data-stu-id="2ee5b-239">9</span></span>                      | <span data-ttu-id="2ee5b-240">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="2ee5b-240">x64, ARM32</span></span> |
| <span data-ttu-id="2ee5b-241">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2ee5b-241">Ubuntu</span></span>                         |  <span data-ttu-id="2ee5b-242">16,04, 18,04, 18,10, 19,04</span><span class="sxs-lookup"><span data-stu-id="2ee5b-242">16.04, 18.04, 18.10, 19.04</span></span>    | <span data-ttu-id="2ee5b-243">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="2ee5b-243">x64, ARM32</span></span> |
| <span data-ttu-id="2ee5b-244">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="2ee5b-244">Linux Mint</span></span>                     |  <span data-ttu-id="2ee5b-245">17, 18</span><span class="sxs-lookup"><span data-stu-id="2ee5b-245">17, 18</span></span>                 | <span data-ttu-id="2ee5b-246">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-246">x64</span></span> |
| <span data-ttu-id="2ee5b-247">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2ee5b-247">openSUSE</span></span>                       |  <span data-ttu-id="2ee5b-248">plus de 15</span><span class="sxs-lookup"><span data-stu-id="2ee5b-248">15+</span></span>                    | <span data-ttu-id="2ee5b-249">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-249">x64</span></span> |
| <span data-ttu-id="2ee5b-250">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-250">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="2ee5b-251">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-251">12 SP2+</span></span>                | <span data-ttu-id="2ee5b-252">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-252">x64</span></span> |
| <span data-ttu-id="2ee5b-253">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-253">Alpine Linux</span></span>                   |  <span data-ttu-id="2ee5b-254">3.8+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-254">3.8+</span></span>                   | <span data-ttu-id="2ee5b-255">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-255">x64</span></span> |

<span data-ttu-id="2ee5b-256">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-256">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2ee5b-257">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-257">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="2ee5b-258">.NET Core 2,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-258">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="2ee5b-259">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-259">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="2ee5b-260">.NET Core 2,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-260">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-261">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-261">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-262">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="2ee5b-262">OS</span></span>                             |  <span data-ttu-id="2ee5b-263">Version</span><span class="sxs-lookup"><span data-stu-id="2ee5b-263">Version</span></span>                |  <span data-ttu-id="2ee5b-264">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-264">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="2ee5b-265">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-265">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="2ee5b-266">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="2ee5b-266">6, 7, 8</span></span>                | <span data-ttu-id="2ee5b-267">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-267">x64</span></span> |
| <span data-ttu-id="2ee5b-268">CentOS</span><span class="sxs-lookup"><span data-stu-id="2ee5b-268">CentOS</span></span>                         |  <span data-ttu-id="2ee5b-269">plus de 7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-269">7+</span></span>                     | <span data-ttu-id="2ee5b-270">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-270">x64</span></span> |
| <span data-ttu-id="2ee5b-271">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-271">Oracle Linux</span></span>                   |  <span data-ttu-id="2ee5b-272">plus de 7</span><span class="sxs-lookup"><span data-stu-id="2ee5b-272">7+</span></span>                     | <span data-ttu-id="2ee5b-273">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-273">x64</span></span> |
| <span data-ttu-id="2ee5b-274">Fedora</span><span class="sxs-lookup"><span data-stu-id="2ee5b-274">Fedora</span></span>                         |  <span data-ttu-id="2ee5b-275">29 +</span><span class="sxs-lookup"><span data-stu-id="2ee5b-275">29+</span></span>                    | <span data-ttu-id="2ee5b-276">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-276">x64</span></span> |
| <span data-ttu-id="2ee5b-277">Debian</span><span class="sxs-lookup"><span data-stu-id="2ee5b-277">Debian</span></span>                         |  <span data-ttu-id="2ee5b-278">9</span><span class="sxs-lookup"><span data-stu-id="2ee5b-278">9</span></span>                      | <span data-ttu-id="2ee5b-279">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="2ee5b-279">x64, ARM32</span></span> |
| <span data-ttu-id="2ee5b-280">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2ee5b-280">Ubuntu</span></span>                         |  <span data-ttu-id="2ee5b-281">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="2ee5b-281">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="2ee5b-282">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="2ee5b-282">x64, ARM32</span></span> |
| <span data-ttu-id="2ee5b-283">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="2ee5b-283">Linux Mint</span></span>                     |  <span data-ttu-id="2ee5b-284">plus de 17</span><span class="sxs-lookup"><span data-stu-id="2ee5b-284">17+</span></span>                    | <span data-ttu-id="2ee5b-285">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-285">x64</span></span> |
| <span data-ttu-id="2ee5b-286">openSUSE</span><span class="sxs-lookup"><span data-stu-id="2ee5b-286">openSUSE</span></span>                       |  <span data-ttu-id="2ee5b-287">plus de 15</span><span class="sxs-lookup"><span data-stu-id="2ee5b-287">15+</span></span>                    | <span data-ttu-id="2ee5b-288">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-288">x64</span></span> |
| <span data-ttu-id="2ee5b-289">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-289">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="2ee5b-290">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-290">12 SP2+</span></span>                | <span data-ttu-id="2ee5b-291">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-291">x64</span></span> |
| <span data-ttu-id="2ee5b-292">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-292">Alpine Linux</span></span>                   |  <span data-ttu-id="2ee5b-293">3.8+</span><span class="sxs-lookup"><span data-stu-id="2ee5b-293">3.8+</span></span>                   | <span data-ttu-id="2ee5b-294">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-294">x64</span></span> |

<span data-ttu-id="2ee5b-295">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-295">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="2ee5b-296">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="2ee5b-296">Linux distribution dependencies</span></span>

<span data-ttu-id="2ee5b-297">En fonction de votre distribution Linux, vous devrez peut-être installer des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-297">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ee5b-298">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-298">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="2ee5b-299">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="2ee5b-299">Ubuntu</span></span>

<span data-ttu-id="2ee5b-300">Les distributions Ubuntu requièrent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-300">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="2ee5b-301">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="2ee5b-301">liblttng-ust0</span></span>
- <span data-ttu-id="2ee5b-302">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-302">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="2ee5b-303">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-303">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="2ee5b-304">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="2ee5b-304">libssl1.0.0</span></span>
- <span data-ttu-id="2ee5b-305">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="2ee5b-305">libkrb5-3</span></span>
- <span data-ttu-id="2ee5b-306">zlib1g</span><span class="sxs-lookup"><span data-stu-id="2ee5b-306">zlib1g</span></span>
- <span data-ttu-id="2ee5b-307">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-307">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="2ee5b-308">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-308">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="2ee5b-309">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-309">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="2ee5b-310">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-310">libicu60 (for 18.x)</span></span>

<span data-ttu-id="2ee5b-311">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-311">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="2ee5b-312">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-312">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="2ee5b-313">La plupart des versions d’Ubuntu incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-313">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="2ee5b-314">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-314">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="2ee5b-315">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-315">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="2ee5b-316">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="2ee5b-316">CentOS and Fedora</span></span>

<span data-ttu-id="2ee5b-317">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-317">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="2ee5b-318">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="2ee5b-318">lttng-ust</span></span>
- <span data-ttu-id="2ee5b-319">libcurl</span><span class="sxs-lookup"><span data-stu-id="2ee5b-319">libcurl</span></span>
- <span data-ttu-id="2ee5b-320">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="2ee5b-320">openssl-libs</span></span>
- <span data-ttu-id="2ee5b-321">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="2ee5b-321">krb5-libs</span></span>
- <span data-ttu-id="2ee5b-322">libicu</span><span class="sxs-lookup"><span data-stu-id="2ee5b-322">libicu</span></span>
- <span data-ttu-id="2ee5b-323">zlib</span><span class="sxs-lookup"><span data-stu-id="2ee5b-323">zlib</span></span>

<span data-ttu-id="2ee5b-324">Utilisateurs Fedora : si la version de votre OpenSSL > = 1,1, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-324">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="2ee5b-325">Pour .NET Core 2,0, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-325">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="2ee5b-326">libunwind</span><span class="sxs-lookup"><span data-stu-id="2ee5b-326">libunwind</span></span>
- <span data-ttu-id="2ee5b-327">libuuid</span><span class="sxs-lookup"><span data-stu-id="2ee5b-327">libuuid</span></span>

<span data-ttu-id="2ee5b-328">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-328">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="2ee5b-329">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-329">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="2ee5b-330">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-330">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="2ee5b-331">La plupart des versions de CentOS et Fedora incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-331">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="2ee5b-332">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-332">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="2ee5b-333">Pour plus d'informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-333">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="2ee5b-334">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-334">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="2ee5b-335">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-335">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="2ee5b-336">Version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ee5b-336">.NET Core Version</span></span> | <span data-ttu-id="2ee5b-337">macOS</span><span class="sxs-lookup"><span data-stu-id="2ee5b-337">macOS</span></span>                 | <span data-ttu-id="2ee5b-338">Architectures</span><span class="sxs-lookup"><span data-stu-id="2ee5b-338">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="2ee5b-339">3,0</span><span class="sxs-lookup"><span data-stu-id="2ee5b-339">3.0</span></span>               | <span data-ttu-id="2ee5b-340">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-340">High Sierra (10.13+)</span></span>  | <span data-ttu-id="2ee5b-341">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-341">x64</span></span> | [<span data-ttu-id="2ee5b-342">Complément d’information</span><span class="sxs-lookup"><span data-stu-id="2ee5b-342">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="2ee5b-343">2.2</span><span class="sxs-lookup"><span data-stu-id="2ee5b-343">2.2</span></span>               | <span data-ttu-id="2ee5b-344">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-344">Sierra (10.12+)</span></span>       | <span data-ttu-id="2ee5b-345">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-345">x64</span></span> | [<span data-ttu-id="2ee5b-346">Complément d’information</span><span class="sxs-lookup"><span data-stu-id="2ee5b-346">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="2ee5b-347">2.1</span><span class="sxs-lookup"><span data-stu-id="2ee5b-347">2.1</span></span>               | <span data-ttu-id="2ee5b-348">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="2ee5b-348">Sierra (10.12+)</span></span>       | <span data-ttu-id="2ee5b-349">x64</span><span class="sxs-lookup"><span data-stu-id="2ee5b-349">x64</span></span> | [<span data-ttu-id="2ee5b-350">Complément d’information</span><span class="sxs-lookup"><span data-stu-id="2ee5b-350">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="2ee5b-351">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="2ee5b-351">libgdiplus</span></span>

<span data-ttu-id="2ee5b-352">Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-352">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="2ee5b-353">Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="2ee5b-353">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="2ee5b-354">Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-354">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="2ee5b-355">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ee5b-355">Next steps</span></span>

- <span data-ttu-id="2ee5b-356">Pour développer et exécuter des applications, installez le [Kit SDK .net Core](sdk.md) (y compris le Runtime).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-356">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="2ee5b-357">Pour exécuter des applications créées par d’autres utilisateurs, installez le [Runtime .net Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="2ee5b-357">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
