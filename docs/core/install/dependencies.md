---
title: Dépendances de kit SDK .NET Core et d’exécution-.NET Core
description: Décrit en détail la configuration requise pour le système d’exploitation et l’architecture de l’UC pour installer le kit SDK .NET Core et le runtime sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 4164ea5a04d80ab20109168a225b793b02ee616a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448891"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="ad6fb-103">Dépendances et exigences de .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad6fb-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="ad6fb-104">Cet article détaille les systèmes d’exploitation et l’architecture du processeur pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="ad6fb-105">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="ad6fb-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="ad6fb-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="ad6fb-107">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-108">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-109">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-109">OS</span></span>                            | <span data-ttu-id="ad6fb-110">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-110">Version</span></span>                        | <span data-ttu-id="ad6fb-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ad6fb-112">Client Windows</span><span class="sxs-lookup"><span data-stu-id="ad6fb-112">Windows Client</span></span>                | <span data-ttu-id="ad6fb-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ad6fb-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-114">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-115">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="ad6fb-115">Windows 10 Client</span></span>             | <span data-ttu-id="ad6fb-116">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-116">Version 1607+</span></span>                  | <span data-ttu-id="ad6fb-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-117">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-118">Windows Server</span></span>                | <span data-ttu-id="ad6fb-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-119">2012 R2+</span></span>                       | <span data-ttu-id="ad6fb-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-120">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-121">Nano Server</span></span>                   | <span data-ttu-id="ad6fb-122">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-122">Version 1803+</span></span>                  | <span data-ttu-id="ad6fb-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-123">x64, ARM32</span></span>      |

<span data-ttu-id="ad6fb-124">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="ad6fb-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ad6fb-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="ad6fb-126">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-127">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-128">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-128">OS</span></span>                            | <span data-ttu-id="ad6fb-129">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-129">Version</span></span>                        | <span data-ttu-id="ad6fb-130">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ad6fb-131">Client Windows</span><span class="sxs-lookup"><span data-stu-id="ad6fb-131">Windows Client</span></span>                | <span data-ttu-id="ad6fb-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ad6fb-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-133">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-134">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="ad6fb-134">Windows 10 Client</span></span>             | <span data-ttu-id="ad6fb-135">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-135">Version 1607+</span></span>                  | <span data-ttu-id="ad6fb-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-136">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-137">Windows Server</span></span>                | <span data-ttu-id="ad6fb-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-138">2012 R2+</span></span>                       | <span data-ttu-id="ad6fb-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-139">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-140">Nano Server</span></span>                   | <span data-ttu-id="ad6fb-141">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-141">Version 1803+</span></span>                  | <span data-ttu-id="ad6fb-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-142">x64, ARM32</span></span>      |

<span data-ttu-id="ad6fb-143">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="ad6fb-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ad6fb-145">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,2 :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-146">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-147">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-147">OS</span></span>                            | <span data-ttu-id="ad6fb-148">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-148">Version</span></span>                        | <span data-ttu-id="ad6fb-149">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ad6fb-150">Client Windows</span><span class="sxs-lookup"><span data-stu-id="ad6fb-150">Windows Client</span></span>                | <span data-ttu-id="ad6fb-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ad6fb-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-152">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-153">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="ad6fb-153">Windows 10 Client</span></span>             | <span data-ttu-id="ad6fb-154">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-154">Version 1607+</span></span>                  | <span data-ttu-id="ad6fb-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-155">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-156">Windows Server</span></span>                | <span data-ttu-id="ad6fb-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="ad6fb-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-158">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-159">Nano Server</span></span>                   | <span data-ttu-id="ad6fb-160">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-160">Version 1803+</span></span>                   | <span data-ttu-id="ad6fb-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-161">x64, ARM32</span></span>      |

<span data-ttu-id="ad6fb-162">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="ad6fb-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ad6fb-164">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,1 :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-165">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-166">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-166">OS</span></span>                            | <span data-ttu-id="ad6fb-167">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-167">Version</span></span>                        | <span data-ttu-id="ad6fb-168">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ad6fb-169">Client Windows</span><span class="sxs-lookup"><span data-stu-id="ad6fb-169">Windows Client</span></span>                | <span data-ttu-id="ad6fb-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ad6fb-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-171">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-172">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="ad6fb-172">Windows 10 Client</span></span>             | <span data-ttu-id="ad6fb-173">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-173">Version 1607+</span></span>                  | <span data-ttu-id="ad6fb-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-174">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-175">Windows Server</span></span>                | <span data-ttu-id="ad6fb-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="ad6fb-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="ad6fb-177">x64, x86</span></span>        |
| <span data-ttu-id="ad6fb-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ad6fb-178">Nano Server</span></span>                   | <span data-ttu-id="ad6fb-179">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-179">Version 1803+</span></span>                  | <span data-ttu-id="ad6fb-180">64x</span><span class="sxs-lookup"><span data-stu-id="ad6fb-180">x64,</span></span>            |

<span data-ttu-id="ad6fb-181">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="ad6fb-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="ad6fb-183">Des dépendances supplémentaires sont requises si vous installez le kit de développement logiciel (SDK) .NET ou le runtime sur les versions suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="ad6fb-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-184">Windows 7 SP1</span></span>
- <span data-ttu-id="ad6fb-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="ad6fb-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-186">Windows 8.1</span></span>
- <span data-ttu-id="ad6fb-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="ad6fb-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="ad6fb-189">Installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-189">Install the following:</span></span>

- <span data-ttu-id="ad6fb-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="ad6fb-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="ad6fb-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="ad6fb-192">La configuration requise ci-dessus est également requise si vous rencontrez l’une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="ad6fb-193">Le programme ne peut pas démarrer, car l' *API-MS-Win-CRT-Runtime-L1-1 1/-0. dll* est absente de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="ad6fb-194">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="ad6fb-195">\- ou -</span><span class="sxs-lookup"><span data-stu-id="ad6fb-195">\- or -</span></span>
>
> <span data-ttu-id="ad6fb-196">La bibliothèque *hostfxr. dll* a été trouvée, mais son chargement à partir de *C :\\\<path_to_app >\\hostfxr. dll* a échoué.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="ad6fb-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="ad6fb-198">.NET Core 3,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="ad6fb-199">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ad6fb-200">.NET Core 3,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-201">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-202">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-202">OS</span></span>                             | <span data-ttu-id="ad6fb-203">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-203">Version</span></span>               | <span data-ttu-id="ad6fb-204">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="ad6fb-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="ad6fb-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="ad6fb-206">6, 7, 8</span></span>               | <span data-ttu-id="ad6fb-207">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-207">x64</span></span> |
| <span data-ttu-id="ad6fb-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="ad6fb-208">CentOS</span></span>                         | <span data-ttu-id="ad6fb-209">7+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-209">7+</span></span>                    | <span data-ttu-id="ad6fb-210">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-210">x64</span></span> |
| <span data-ttu-id="ad6fb-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-211">Oracle Linux</span></span>                   | <span data-ttu-id="ad6fb-212">7+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-212">7+</span></span>                    | <span data-ttu-id="ad6fb-213">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-213">x64</span></span> |
| <span data-ttu-id="ad6fb-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad6fb-214">Fedora</span></span>                         | <span data-ttu-id="ad6fb-215">29 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-215">29+</span></span>                   | <span data-ttu-id="ad6fb-216">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-216">x64</span></span> |
| <span data-ttu-id="ad6fb-217">Debian</span><span class="sxs-lookup"><span data-stu-id="ad6fb-217">Debian</span></span>                         | <span data-ttu-id="ad6fb-218">9+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-218">9+</span></span>                    | <span data-ttu-id="ad6fb-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ad6fb-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad6fb-220">Ubuntu</span></span>                         | <span data-ttu-id="ad6fb-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-221">16.04+</span></span>                | <span data-ttu-id="ad6fb-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ad6fb-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="ad6fb-223">Linux Mint</span></span>                     | <span data-ttu-id="ad6fb-224">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="ad6fb-224">18+</span></span>                   | <span data-ttu-id="ad6fb-225">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-225">x64</span></span> |
| <span data-ttu-id="ad6fb-226">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ad6fb-226">openSUSE</span></span>                       | <span data-ttu-id="ad6fb-227">plus de 15</span><span class="sxs-lookup"><span data-stu-id="ad6fb-227">15+</span></span>                   | <span data-ttu-id="ad6fb-228">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-228">x64</span></span> |
| <span data-ttu-id="ad6fb-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="ad6fb-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-230">12 SP2+</span></span>               | <span data-ttu-id="ad6fb-231">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-231">x64</span></span> |
| <span data-ttu-id="ad6fb-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-232">Alpine Linux</span></span>                   | <span data-ttu-id="ad6fb-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-233">3.10+</span></span>                 | <span data-ttu-id="ad6fb-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-234">x64, ARM64</span></span> |

<span data-ttu-id="ad6fb-235">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="ad6fb-236">Pour plus d’informations sur l’installation de .NET Core 3,1 sur ARM64 (kernel 4.14 +), consultez [installation de .net core 3,0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad6fb-237">La prise en charge de ARM64 nécessite Linux kernel 4,14 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="ad6fb-238">Certaines distributions Linux répondent à cette exigence, contrairement à d’autres.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="ad6fb-239">Par exemple, Ubuntu 18,04 est pris en charge, mais Ubuntu 16,04 ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="ad6fb-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ad6fb-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="ad6fb-241">.NET Core 3,0 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="ad6fb-242">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ad6fb-243">.NET Core 3,0 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-244">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-245">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-245">OS</span></span>                             | <span data-ttu-id="ad6fb-246">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-246">Version</span></span>               | <span data-ttu-id="ad6fb-247">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="ad6fb-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="ad6fb-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="ad6fb-249">6, 7, 8</span></span>               | <span data-ttu-id="ad6fb-250">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-250">x64</span></span> |
| <span data-ttu-id="ad6fb-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="ad6fb-251">CentOS</span></span>                         | <span data-ttu-id="ad6fb-252">7+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-252">7+</span></span>                    | <span data-ttu-id="ad6fb-253">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-253">x64</span></span> |
| <span data-ttu-id="ad6fb-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-254">Oracle Linux</span></span>                   | <span data-ttu-id="ad6fb-255">7+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-255">7+</span></span>                    | <span data-ttu-id="ad6fb-256">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-256">x64</span></span> |
| <span data-ttu-id="ad6fb-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad6fb-257">Fedora</span></span>                         | <span data-ttu-id="ad6fb-258">29 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-258">29+</span></span>                   | <span data-ttu-id="ad6fb-259">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-259">x64</span></span> |
| <span data-ttu-id="ad6fb-260">Debian</span><span class="sxs-lookup"><span data-stu-id="ad6fb-260">Debian</span></span>                         | <span data-ttu-id="ad6fb-261">9+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-261">9+</span></span>                    | <span data-ttu-id="ad6fb-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ad6fb-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad6fb-263">Ubuntu</span></span>                         | <span data-ttu-id="ad6fb-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-264">16.04+</span></span>                | <span data-ttu-id="ad6fb-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="ad6fb-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="ad6fb-266">Linux Mint</span></span>                     | <span data-ttu-id="ad6fb-267">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="ad6fb-267">18+</span></span>                   | <span data-ttu-id="ad6fb-268">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-268">x64</span></span> |
| <span data-ttu-id="ad6fb-269">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ad6fb-269">openSUSE</span></span>                       | <span data-ttu-id="ad6fb-270">plus de 15</span><span class="sxs-lookup"><span data-stu-id="ad6fb-270">15+</span></span>                   | <span data-ttu-id="ad6fb-271">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-271">x64</span></span> |
| <span data-ttu-id="ad6fb-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="ad6fb-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-273">12 SP2+</span></span>               | <span data-ttu-id="ad6fb-274">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-274">x64</span></span> |
| <span data-ttu-id="ad6fb-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-275">Alpine Linux</span></span>                   | <span data-ttu-id="ad6fb-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-276">3.8+</span></span>                  | <span data-ttu-id="ad6fb-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-277">x64, ARM64</span></span> |

<span data-ttu-id="ad6fb-278">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="ad6fb-279">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="ad6fb-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ad6fb-281">.NET Core 2,2 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="ad6fb-282">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ad6fb-283">.NET Core 2,2 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-284">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-285">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-285">OS</span></span>                             |  <span data-ttu-id="ad6fb-286">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-286">Version</span></span>                |  <span data-ttu-id="ad6fb-287">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="ad6fb-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="ad6fb-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="ad6fb-289">6, 7</span></span>                   | <span data-ttu-id="ad6fb-290">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-290">x64</span></span> |
| <span data-ttu-id="ad6fb-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="ad6fb-291">CentOS</span></span>                         |  <span data-ttu-id="ad6fb-292">7</span><span class="sxs-lookup"><span data-stu-id="ad6fb-292">7</span></span>                      | <span data-ttu-id="ad6fb-293">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-293">x64</span></span> |
| <span data-ttu-id="ad6fb-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-294">Oracle Linux</span></span>                   |  <span data-ttu-id="ad6fb-295">7</span><span class="sxs-lookup"><span data-stu-id="ad6fb-295">7</span></span>                      | <span data-ttu-id="ad6fb-296">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-296">x64</span></span> |
| <span data-ttu-id="ad6fb-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad6fb-297">Fedora</span></span>                         |  <span data-ttu-id="ad6fb-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="ad6fb-298">29, 30</span></span>                 | <span data-ttu-id="ad6fb-299">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-299">x64</span></span> |
| <span data-ttu-id="ad6fb-300">Debian</span><span class="sxs-lookup"><span data-stu-id="ad6fb-300">Debian</span></span>                         |  <span data-ttu-id="ad6fb-301">9</span><span class="sxs-lookup"><span data-stu-id="ad6fb-301">9</span></span>                      | <span data-ttu-id="ad6fb-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-302">x64, ARM32</span></span> |
| <span data-ttu-id="ad6fb-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad6fb-303">Ubuntu</span></span>                         |  <span data-ttu-id="ad6fb-304">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="ad6fb-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="ad6fb-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-305">x64, ARM32</span></span> |
| <span data-ttu-id="ad6fb-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="ad6fb-306">Linux Mint</span></span>                     |  <span data-ttu-id="ad6fb-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="ad6fb-307">17, 18</span></span>                 | <span data-ttu-id="ad6fb-308">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-308">x64</span></span> |
| <span data-ttu-id="ad6fb-309">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ad6fb-309">openSUSE</span></span>                       |  <span data-ttu-id="ad6fb-310">plus de 15</span><span class="sxs-lookup"><span data-stu-id="ad6fb-310">15+</span></span>                    | <span data-ttu-id="ad6fb-311">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-311">x64</span></span> |
| <span data-ttu-id="ad6fb-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="ad6fb-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-313">12 SP2+</span></span>                | <span data-ttu-id="ad6fb-314">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-314">x64</span></span> |
| <span data-ttu-id="ad6fb-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-315">Alpine Linux</span></span>                   |  <span data-ttu-id="ad6fb-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-316">3.8+</span></span>                   | <span data-ttu-id="ad6fb-317">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-317">x64</span></span> |

<span data-ttu-id="ad6fb-318">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="ad6fb-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ad6fb-320">.NET Core 2,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="ad6fb-321">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="ad6fb-322">.NET Core 2,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-323">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-324">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="ad6fb-324">OS</span></span>                             |  <span data-ttu-id="ad6fb-325">Version</span><span class="sxs-lookup"><span data-stu-id="ad6fb-325">Version</span></span>                |  <span data-ttu-id="ad6fb-326">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="ad6fb-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="ad6fb-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="ad6fb-328">6, 7, 8</span></span>                | <span data-ttu-id="ad6fb-329">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-329">x64</span></span> |
| <span data-ttu-id="ad6fb-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="ad6fb-330">CentOS</span></span>                         |  <span data-ttu-id="ad6fb-331">7+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-331">7+</span></span>                     | <span data-ttu-id="ad6fb-332">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-332">x64</span></span> |
| <span data-ttu-id="ad6fb-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-333">Oracle Linux</span></span>                   |  <span data-ttu-id="ad6fb-334">7+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-334">7+</span></span>                     | <span data-ttu-id="ad6fb-335">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-335">x64</span></span> |
| <span data-ttu-id="ad6fb-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="ad6fb-336">Fedora</span></span>                         |  <span data-ttu-id="ad6fb-337">29 +</span><span class="sxs-lookup"><span data-stu-id="ad6fb-337">29+</span></span>                    | <span data-ttu-id="ad6fb-338">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-338">x64</span></span> |
| <span data-ttu-id="ad6fb-339">Debian</span><span class="sxs-lookup"><span data-stu-id="ad6fb-339">Debian</span></span>                         |  <span data-ttu-id="ad6fb-340">9</span><span class="sxs-lookup"><span data-stu-id="ad6fb-340">9</span></span>                      | <span data-ttu-id="ad6fb-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-341">x64, ARM32</span></span> |
| <span data-ttu-id="ad6fb-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad6fb-342">Ubuntu</span></span>                         |  <span data-ttu-id="ad6fb-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="ad6fb-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="ad6fb-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="ad6fb-344">x64, ARM32</span></span> |
| <span data-ttu-id="ad6fb-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="ad6fb-345">Linux Mint</span></span>                     |  <span data-ttu-id="ad6fb-346">plus de 17</span><span class="sxs-lookup"><span data-stu-id="ad6fb-346">17+</span></span>                    | <span data-ttu-id="ad6fb-347">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-347">x64</span></span> |
| <span data-ttu-id="ad6fb-348">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="ad6fb-348">openSUSE</span></span>                       |  <span data-ttu-id="ad6fb-349">plus de 15</span><span class="sxs-lookup"><span data-stu-id="ad6fb-349">15+</span></span>                    | <span data-ttu-id="ad6fb-350">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-350">x64</span></span> |
| <span data-ttu-id="ad6fb-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="ad6fb-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-352">12 SP2+</span></span>                | <span data-ttu-id="ad6fb-353">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-353">x64</span></span> |
| <span data-ttu-id="ad6fb-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-354">Alpine Linux</span></span>                   |  <span data-ttu-id="ad6fb-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="ad6fb-355">3.8+</span></span>                   | <span data-ttu-id="ad6fb-356">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-356">x64</span></span> |

<span data-ttu-id="ad6fb-357">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="ad6fb-358">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="ad6fb-358">Linux distribution dependencies</span></span>

<span data-ttu-id="ad6fb-359">En fonction de votre distribution Linux, vous devrez peut-être installer des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad6fb-360">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="ad6fb-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ad6fb-361">Ubuntu</span></span>

<span data-ttu-id="ad6fb-362">Les distributions Ubuntu requièrent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="ad6fb-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="ad6fb-363">liblttng-ust0</span></span>
- <span data-ttu-id="ad6fb-364">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="ad6fb-365">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="ad6fb-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="ad6fb-366">libssl1.0.0</span></span>
- <span data-ttu-id="ad6fb-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="ad6fb-367">libkrb5-3</span></span>
- <span data-ttu-id="ad6fb-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="ad6fb-368">zlib1g</span></span>
- <span data-ttu-id="ad6fb-369">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="ad6fb-370">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="ad6fb-371">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="ad6fb-372">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="ad6fb-373">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="ad6fb-374">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="ad6fb-375">La plupart des versions d’Ubuntu incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="ad6fb-376">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="ad6fb-377">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="ad6fb-378">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="ad6fb-378">CentOS and Fedora</span></span>

<span data-ttu-id="ad6fb-379">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="ad6fb-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="ad6fb-380">lttng-ust</span></span>
- <span data-ttu-id="ad6fb-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="ad6fb-381">libcurl</span></span>
- <span data-ttu-id="ad6fb-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="ad6fb-382">openssl-libs</span></span>
- <span data-ttu-id="ad6fb-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="ad6fb-383">krb5-libs</span></span>
- <span data-ttu-id="ad6fb-384">libicu</span><span class="sxs-lookup"><span data-stu-id="ad6fb-384">libicu</span></span>
- <span data-ttu-id="ad6fb-385">zlib</span><span class="sxs-lookup"><span data-stu-id="ad6fb-385">zlib</span></span>

<span data-ttu-id="ad6fb-386">Utilisateurs Fedora : si la version de votre OpenSSL > = 1,1, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="ad6fb-387">Pour .NET Core 2,0, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="ad6fb-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="ad6fb-388">libunwind</span></span>
- <span data-ttu-id="ad6fb-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="ad6fb-389">libuuid</span></span>

<span data-ttu-id="ad6fb-390">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="ad6fb-391">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="ad6fb-392">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="ad6fb-393">La plupart des versions de CentOS et Fedora incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="ad6fb-394">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="ad6fb-395">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="ad6fb-396">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="ad6fb-397">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ad6fb-398">Version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="ad6fb-398">.NET Core Version</span></span> | <span data-ttu-id="ad6fb-399">macOS</span><span class="sxs-lookup"><span data-stu-id="ad6fb-399">macOS</span></span>                 | <span data-ttu-id="ad6fb-400">Architectures</span><span class="sxs-lookup"><span data-stu-id="ad6fb-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="ad6fb-401">3.1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-401">3.1</span></span>               | <span data-ttu-id="ad6fb-402">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="ad6fb-403">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-403">x64</span></span> | [<span data-ttu-id="ad6fb-404">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="ad6fb-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="ad6fb-405">3.0</span><span class="sxs-lookup"><span data-stu-id="ad6fb-405">3.0</span></span>               | <span data-ttu-id="ad6fb-406">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="ad6fb-407">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-407">x64</span></span> | [<span data-ttu-id="ad6fb-408">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="ad6fb-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="ad6fb-409">2.2</span><span class="sxs-lookup"><span data-stu-id="ad6fb-409">2.2</span></span>               | <span data-ttu-id="ad6fb-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="ad6fb-411">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-411">x64</span></span> | [<span data-ttu-id="ad6fb-412">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="ad6fb-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="ad6fb-413">2.1</span><span class="sxs-lookup"><span data-stu-id="ad6fb-413">2.1</span></span>               | <span data-ttu-id="ad6fb-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="ad6fb-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="ad6fb-415">x64</span><span class="sxs-lookup"><span data-stu-id="ad6fb-415">x64</span></span> | [<span data-ttu-id="ad6fb-416">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="ad6fb-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a><span data-ttu-id="ad6fb-417">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="ad6fb-417">libgdiplus</span></span>

<span data-ttu-id="ad6fb-418">Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-418">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="ad6fb-419">Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="ad6fb-419">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="ad6fb-420">Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="ad6fb-420">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="ad6fb-421">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ad6fb-421">Next steps</span></span>

- <span data-ttu-id="ad6fb-422">Pour développer et exécuter des applications, installez le [Kit SDK .net Core](sdk.md) (y compris le Runtime).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-422">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="ad6fb-423">Pour exécuter des applications créées par d’autres utilisateurs, installez le [Runtime .net Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="ad6fb-423">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
