---
title: Dépendances de kit SDK .NET Core et d’exécution-.NET Core
description: Décrit en détail la configuration requise pour le système d’exploitation et l’architecture de l’UC pour installer le kit SDK .NET Core et le runtime sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157806"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="bf2f7-103">Dépendances et exigences de .NET Core</span><span class="sxs-lookup"><span data-stu-id="bf2f7-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="bf2f7-104">Cet article détaille les systèmes d’exploitation et l’architecture du processeur pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="bf2f7-105">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="bf2f7-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="bf2f7-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="bf2f7-107">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-108">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-109">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-109">OS</span></span>                            | <span data-ttu-id="bf2f7-110">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-110">Version</span></span>                        | <span data-ttu-id="bf2f7-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="bf2f7-112">Client Windows</span><span class="sxs-lookup"><span data-stu-id="bf2f7-112">Windows Client</span></span>                | <span data-ttu-id="bf2f7-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="bf2f7-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-114">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-115">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="bf2f7-115">Windows 10 Client</span></span>             | <span data-ttu-id="bf2f7-116">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-116">Version 1607+</span></span>                  | <span data-ttu-id="bf2f7-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-117">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-118">Windows Server</span></span>                | <span data-ttu-id="bf2f7-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-119">2012 R2+</span></span>                       | <span data-ttu-id="bf2f7-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-120">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-121">Nano Server</span></span>                   | <span data-ttu-id="bf2f7-122">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-122">Version 1803+</span></span>                  | <span data-ttu-id="bf2f7-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-123">x64, ARM32</span></span>      |

<span data-ttu-id="bf2f7-124">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="bf2f7-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bf2f7-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="bf2f7-126">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-127">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-128">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-128">OS</span></span>                            | <span data-ttu-id="bf2f7-129">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-129">Version</span></span>                        | <span data-ttu-id="bf2f7-130">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="bf2f7-131">Client Windows</span><span class="sxs-lookup"><span data-stu-id="bf2f7-131">Windows Client</span></span>                | <span data-ttu-id="bf2f7-132">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="bf2f7-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-133">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-134">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="bf2f7-134">Windows 10 Client</span></span>             | <span data-ttu-id="bf2f7-135">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-135">Version 1607+</span></span>                  | <span data-ttu-id="bf2f7-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-136">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-137">Windows Server</span></span>                | <span data-ttu-id="bf2f7-138">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-138">2012 R2+</span></span>                       | <span data-ttu-id="bf2f7-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-139">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-140">Nano Server</span></span>                   | <span data-ttu-id="bf2f7-141">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-141">Version 1803+</span></span>                  | <span data-ttu-id="bf2f7-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-142">x64, ARM32</span></span>      |

<span data-ttu-id="bf2f7-143">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="bf2f7-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="bf2f7-145">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,2 :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-146">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-147">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-147">OS</span></span>                            | <span data-ttu-id="bf2f7-148">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-148">Version</span></span>                        | <span data-ttu-id="bf2f7-149">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="bf2f7-150">Client Windows</span><span class="sxs-lookup"><span data-stu-id="bf2f7-150">Windows Client</span></span>                | <span data-ttu-id="bf2f7-151">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="bf2f7-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-152">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-153">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="bf2f7-153">Windows 10 Client</span></span>             | <span data-ttu-id="bf2f7-154">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-154">Version 1607+</span></span>                  | <span data-ttu-id="bf2f7-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-155">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-156">Windows Server</span></span>                | <span data-ttu-id="bf2f7-157">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="bf2f7-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-158">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-159">Nano Server</span></span>                   | <span data-ttu-id="bf2f7-160">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-160">Version 1803+</span></span>                   | <span data-ttu-id="bf2f7-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-161">x64, ARM32</span></span>      |

<span data-ttu-id="bf2f7-162">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="bf2f7-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="bf2f7-164">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,1 :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-165">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-166">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-166">OS</span></span>                            | <span data-ttu-id="bf2f7-167">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-167">Version</span></span>                        | <span data-ttu-id="bf2f7-168">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="bf2f7-169">Client Windows</span><span class="sxs-lookup"><span data-stu-id="bf2f7-169">Windows Client</span></span>                | <span data-ttu-id="bf2f7-170">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="bf2f7-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-171">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-172">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="bf2f7-172">Windows 10 Client</span></span>             | <span data-ttu-id="bf2f7-173">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-173">Version 1607+</span></span>                  | <span data-ttu-id="bf2f7-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-174">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-175">Windows Server</span></span>                | <span data-ttu-id="bf2f7-176">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="bf2f7-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="bf2f7-177">x64, x86</span></span>        |
| <span data-ttu-id="bf2f7-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="bf2f7-178">Nano Server</span></span>                   | <span data-ttu-id="bf2f7-179">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-179">Version 1803+</span></span>                  | <span data-ttu-id="bf2f7-180">64x</span><span class="sxs-lookup"><span data-stu-id="bf2f7-180">x64,</span></span>            |

<span data-ttu-id="bf2f7-181">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="bf2f7-182">Windows 7/Vista/8,1/Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="bf2f7-183">Des dépendances supplémentaires sont requises si vous installez le kit de développement logiciel (SDK) .NET ou le runtime sur les versions suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="bf2f7-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-184">Windows 7 SP1</span></span>
- <span data-ttu-id="bf2f7-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="bf2f7-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-186">Windows 8.1</span></span>
- <span data-ttu-id="bf2f7-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="bf2f7-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="bf2f7-189">Installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-189">Install the following:</span></span>

- <span data-ttu-id="bf2f7-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="bf2f7-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="bf2f7-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="bf2f7-192">La configuration requise ci-dessus est également requise si vous rencontrez l’une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="bf2f7-193">Le programme ne peut pas démarrer, car l' *API-MS-Win-CRT-Runtime-L1-1 1/-0. dll* est absente de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="bf2f7-194">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="bf2f7-195">\- ou -</span><span class="sxs-lookup"><span data-stu-id="bf2f7-195">\- or -</span></span>
>
> <span data-ttu-id="bf2f7-196">La bibliothèque *hostfxr. dll* a été trouvée, mais son chargement à partir de *C :\\\<path_to_app >\\hostfxr. dll* a échoué.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="bf2f7-197">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="bf2f7-198">.NET Core 3,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="bf2f7-199">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="bf2f7-200">.NET Core 3,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-201">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-202">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-202">OS</span></span>                             | <span data-ttu-id="bf2f7-203">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-203">Version</span></span>               | <span data-ttu-id="bf2f7-204">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="bf2f7-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="bf2f7-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="bf2f7-206">6, 7, 8</span></span>               | <span data-ttu-id="bf2f7-207">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-207">x64</span></span> |
| <span data-ttu-id="bf2f7-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="bf2f7-208">CentOS</span></span>                         | <span data-ttu-id="bf2f7-209">7+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-209">7+</span></span>                    | <span data-ttu-id="bf2f7-210">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-210">x64</span></span> |
| <span data-ttu-id="bf2f7-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-211">Oracle Linux</span></span>                   | <span data-ttu-id="bf2f7-212">7+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-212">7+</span></span>                    | <span data-ttu-id="bf2f7-213">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-213">x64</span></span> |
| <span data-ttu-id="bf2f7-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="bf2f7-214">Fedora</span></span>                         | <span data-ttu-id="bf2f7-215">29 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-215">29+</span></span>                   | <span data-ttu-id="bf2f7-216">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-216">x64</span></span> |
| <span data-ttu-id="bf2f7-217">Debian</span><span class="sxs-lookup"><span data-stu-id="bf2f7-217">Debian</span></span>                         | <span data-ttu-id="bf2f7-218">9+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-218">9+</span></span>                    | <span data-ttu-id="bf2f7-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="bf2f7-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf2f7-220">Ubuntu</span></span>                         | <span data-ttu-id="bf2f7-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-221">16.04+</span></span>                | <span data-ttu-id="bf2f7-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="bf2f7-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="bf2f7-223">Linux Mint</span></span>                     | <span data-ttu-id="bf2f7-224">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="bf2f7-224">18+</span></span>                   | <span data-ttu-id="bf2f7-225">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-225">x64</span></span> |
| <span data-ttu-id="bf2f7-226">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="bf2f7-226">openSUSE</span></span>                       | <span data-ttu-id="bf2f7-227">plus de 15</span><span class="sxs-lookup"><span data-stu-id="bf2f7-227">15+</span></span>                   | <span data-ttu-id="bf2f7-228">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-228">x64</span></span> |
| <span data-ttu-id="bf2f7-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="bf2f7-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-230">12 SP2+</span></span>               | <span data-ttu-id="bf2f7-231">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-231">x64</span></span> |
| <span data-ttu-id="bf2f7-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-232">Alpine Linux</span></span>                   | <span data-ttu-id="bf2f7-233">3.10 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-233">3.10+</span></span>                 | <span data-ttu-id="bf2f7-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-234">x64, ARM64</span></span> |

<span data-ttu-id="bf2f7-235">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="bf2f7-236">Pour plus d’informations sur l’installation de .NET Core 3,1 sur ARM64 (kernel 4.14 +), consultez [installation de .net core 3,0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf2f7-237">La prise en charge de ARM64 nécessite Linux kernel 4,14 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="bf2f7-238">Certaines distributions Linux répondent à cette exigence, contrairement à d’autres.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="bf2f7-239">Par exemple, Ubuntu 18,04 est pris en charge, mais Ubuntu 16,04 ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="bf2f7-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="bf2f7-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="bf2f7-241">.NET Core 3,0 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="bf2f7-242">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="bf2f7-243">.NET Core 3,0 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-244">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-245">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-245">OS</span></span>                             | <span data-ttu-id="bf2f7-246">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-246">Version</span></span>               | <span data-ttu-id="bf2f7-247">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="bf2f7-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="bf2f7-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="bf2f7-249">6, 7, 8</span></span>               | <span data-ttu-id="bf2f7-250">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-250">x64</span></span> |
| <span data-ttu-id="bf2f7-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="bf2f7-251">CentOS</span></span>                         | <span data-ttu-id="bf2f7-252">7+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-252">7+</span></span>                    | <span data-ttu-id="bf2f7-253">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-253">x64</span></span> |
| <span data-ttu-id="bf2f7-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-254">Oracle Linux</span></span>                   | <span data-ttu-id="bf2f7-255">7+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-255">7+</span></span>                    | <span data-ttu-id="bf2f7-256">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-256">x64</span></span> |
| <span data-ttu-id="bf2f7-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="bf2f7-257">Fedora</span></span>                         | <span data-ttu-id="bf2f7-258">29 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-258">29+</span></span>                   | <span data-ttu-id="bf2f7-259">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-259">x64</span></span> |
| <span data-ttu-id="bf2f7-260">Debian</span><span class="sxs-lookup"><span data-stu-id="bf2f7-260">Debian</span></span>                         | <span data-ttu-id="bf2f7-261">9+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-261">9+</span></span>                    | <span data-ttu-id="bf2f7-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="bf2f7-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf2f7-263">Ubuntu</span></span>                         | <span data-ttu-id="bf2f7-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-264">16.04+</span></span>                | <span data-ttu-id="bf2f7-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="bf2f7-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="bf2f7-266">Linux Mint</span></span>                     | <span data-ttu-id="bf2f7-267">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="bf2f7-267">18+</span></span>                   | <span data-ttu-id="bf2f7-268">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-268">x64</span></span> |
| <span data-ttu-id="bf2f7-269">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="bf2f7-269">openSUSE</span></span>                       | <span data-ttu-id="bf2f7-270">plus de 15</span><span class="sxs-lookup"><span data-stu-id="bf2f7-270">15+</span></span>                   | <span data-ttu-id="bf2f7-271">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-271">x64</span></span> |
| <span data-ttu-id="bf2f7-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="bf2f7-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-273">12 SP2+</span></span>               | <span data-ttu-id="bf2f7-274">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-274">x64</span></span> |
| <span data-ttu-id="bf2f7-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-275">Alpine Linux</span></span>                   | <span data-ttu-id="bf2f7-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-276">3.8+</span></span>                  | <span data-ttu-id="bf2f7-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-277">x64, ARM64</span></span> |

<span data-ttu-id="bf2f7-278">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="bf2f7-279">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="bf2f7-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="bf2f7-281">.NET Core 2,2 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="bf2f7-282">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="bf2f7-283">.NET Core 2,2 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-284">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-285">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-285">OS</span></span>                             |  <span data-ttu-id="bf2f7-286">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-286">Version</span></span>                |  <span data-ttu-id="bf2f7-287">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="bf2f7-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="bf2f7-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="bf2f7-289">6, 7</span></span>                   | <span data-ttu-id="bf2f7-290">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-290">x64</span></span> |
| <span data-ttu-id="bf2f7-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="bf2f7-291">CentOS</span></span>                         |  <span data-ttu-id="bf2f7-292">7</span><span class="sxs-lookup"><span data-stu-id="bf2f7-292">7</span></span>                      | <span data-ttu-id="bf2f7-293">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-293">x64</span></span> |
| <span data-ttu-id="bf2f7-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-294">Oracle Linux</span></span>                   |  <span data-ttu-id="bf2f7-295">7</span><span class="sxs-lookup"><span data-stu-id="bf2f7-295">7</span></span>                      | <span data-ttu-id="bf2f7-296">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-296">x64</span></span> |
| <span data-ttu-id="bf2f7-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="bf2f7-297">Fedora</span></span>                         |  <span data-ttu-id="bf2f7-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="bf2f7-298">29, 30</span></span>                 | <span data-ttu-id="bf2f7-299">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-299">x64</span></span> |
| <span data-ttu-id="bf2f7-300">Debian</span><span class="sxs-lookup"><span data-stu-id="bf2f7-300">Debian</span></span>                         |  <span data-ttu-id="bf2f7-301">9</span><span class="sxs-lookup"><span data-stu-id="bf2f7-301">9</span></span>                      | <span data-ttu-id="bf2f7-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-302">x64, ARM32</span></span> |
| <span data-ttu-id="bf2f7-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf2f7-303">Ubuntu</span></span>                         |  <span data-ttu-id="bf2f7-304">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="bf2f7-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="bf2f7-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-305">x64, ARM32</span></span> |
| <span data-ttu-id="bf2f7-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="bf2f7-306">Linux Mint</span></span>                     |  <span data-ttu-id="bf2f7-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="bf2f7-307">17, 18</span></span>                 | <span data-ttu-id="bf2f7-308">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-308">x64</span></span> |
| <span data-ttu-id="bf2f7-309">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="bf2f7-309">openSUSE</span></span>                       |  <span data-ttu-id="bf2f7-310">plus de 15</span><span class="sxs-lookup"><span data-stu-id="bf2f7-310">15+</span></span>                    | <span data-ttu-id="bf2f7-311">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-311">x64</span></span> |
| <span data-ttu-id="bf2f7-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="bf2f7-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-313">12 SP2+</span></span>                | <span data-ttu-id="bf2f7-314">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-314">x64</span></span> |
| <span data-ttu-id="bf2f7-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-315">Alpine Linux</span></span>                   |  <span data-ttu-id="bf2f7-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-316">3.8+</span></span>                   | <span data-ttu-id="bf2f7-317">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-317">x64</span></span> |

<span data-ttu-id="bf2f7-318">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="bf2f7-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="bf2f7-320">.NET Core 2,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="bf2f7-321">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="bf2f7-322">.NET Core 2,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-323">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-324">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="bf2f7-324">OS</span></span>                             |  <span data-ttu-id="bf2f7-325">cible</span><span class="sxs-lookup"><span data-stu-id="bf2f7-325">Version</span></span>                |  <span data-ttu-id="bf2f7-326">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="bf2f7-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="bf2f7-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="bf2f7-328">6, 7, 8</span></span>                | <span data-ttu-id="bf2f7-329">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-329">x64</span></span> |
| <span data-ttu-id="bf2f7-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="bf2f7-330">CentOS</span></span>                         |  <span data-ttu-id="bf2f7-331">7+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-331">7+</span></span>                     | <span data-ttu-id="bf2f7-332">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-332">x64</span></span> |
| <span data-ttu-id="bf2f7-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-333">Oracle Linux</span></span>                   |  <span data-ttu-id="bf2f7-334">7+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-334">7+</span></span>                     | <span data-ttu-id="bf2f7-335">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-335">x64</span></span> |
| <span data-ttu-id="bf2f7-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="bf2f7-336">Fedora</span></span>                         |  <span data-ttu-id="bf2f7-337">29 +</span><span class="sxs-lookup"><span data-stu-id="bf2f7-337">29+</span></span>                    | <span data-ttu-id="bf2f7-338">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-338">x64</span></span> |
| <span data-ttu-id="bf2f7-339">Debian</span><span class="sxs-lookup"><span data-stu-id="bf2f7-339">Debian</span></span>                         |  <span data-ttu-id="bf2f7-340">9</span><span class="sxs-lookup"><span data-stu-id="bf2f7-340">9</span></span>                      | <span data-ttu-id="bf2f7-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-341">x64, ARM32</span></span> |
| <span data-ttu-id="bf2f7-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf2f7-342">Ubuntu</span></span>                         |  <span data-ttu-id="bf2f7-343">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="bf2f7-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="bf2f7-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="bf2f7-344">x64, ARM32</span></span> |
| <span data-ttu-id="bf2f7-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="bf2f7-345">Linux Mint</span></span>                     |  <span data-ttu-id="bf2f7-346">17+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-346">17+</span></span>                    | <span data-ttu-id="bf2f7-347">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-347">x64</span></span> |
| <span data-ttu-id="bf2f7-348">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="bf2f7-348">openSUSE</span></span>                       |  <span data-ttu-id="bf2f7-349">plus de 15</span><span class="sxs-lookup"><span data-stu-id="bf2f7-349">15+</span></span>                    | <span data-ttu-id="bf2f7-350">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-350">x64</span></span> |
| <span data-ttu-id="bf2f7-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="bf2f7-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-352">12 SP2+</span></span>                | <span data-ttu-id="bf2f7-353">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-353">x64</span></span> |
| <span data-ttu-id="bf2f7-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-354">Alpine Linux</span></span>                   |  <span data-ttu-id="bf2f7-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="bf2f7-355">3.8+</span></span>                   | <span data-ttu-id="bf2f7-356">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-356">x64</span></span> |

<span data-ttu-id="bf2f7-357">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="bf2f7-358">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="bf2f7-358">Linux distribution dependencies</span></span>

<span data-ttu-id="bf2f7-359">En fonction de votre distribution Linux, vous devrez peut-être installer des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf2f7-360">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="bf2f7-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="bf2f7-361">Ubuntu</span></span>

<span data-ttu-id="bf2f7-362">Les distributions Ubuntu requièrent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="bf2f7-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="bf2f7-363">liblttng-ust0</span></span>
- <span data-ttu-id="bf2f7-364">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="bf2f7-365">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="bf2f7-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="bf2f7-366">libssl1.0.0</span></span>
- <span data-ttu-id="bf2f7-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="bf2f7-367">libkrb5-3</span></span>
- <span data-ttu-id="bf2f7-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="bf2f7-368">zlib1g</span></span>
- <span data-ttu-id="bf2f7-369">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="bf2f7-370">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="bf2f7-371">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="bf2f7-372">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="bf2f7-373">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="bf2f7-374">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="bf2f7-375">La plupart des versions d’Ubuntu incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="bf2f7-376">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="bf2f7-377">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="bf2f7-378">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="bf2f7-378">CentOS and Fedora</span></span>

<span data-ttu-id="bf2f7-379">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="bf2f7-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="bf2f7-380">lttng-ust</span></span>
- <span data-ttu-id="bf2f7-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="bf2f7-381">libcurl</span></span>
- <span data-ttu-id="bf2f7-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="bf2f7-382">openssl-libs</span></span>
- <span data-ttu-id="bf2f7-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="bf2f7-383">krb5-libs</span></span>
- <span data-ttu-id="bf2f7-384">libicu</span><span class="sxs-lookup"><span data-stu-id="bf2f7-384">libicu</span></span>
- <span data-ttu-id="bf2f7-385">zlib</span><span class="sxs-lookup"><span data-stu-id="bf2f7-385">zlib</span></span>

<span data-ttu-id="bf2f7-386">Utilisateurs Fedora : si la version de votre OpenSSL > = 1,1, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="bf2f7-387">Pour .NET Core 2,0, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="bf2f7-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="bf2f7-388">libunwind</span></span>
- <span data-ttu-id="bf2f7-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="bf2f7-389">libuuid</span></span>

<span data-ttu-id="bf2f7-390">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="bf2f7-391">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="bf2f7-392">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="bf2f7-393">La plupart des versions de CentOS et Fedora incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="bf2f7-394">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="bf2f7-395">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="bf2f7-396">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="bf2f7-397">Un symbole de `+` représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="bf2f7-398">Version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="bf2f7-398">.NET Core Version</span></span> | <span data-ttu-id="bf2f7-399">macOS</span><span class="sxs-lookup"><span data-stu-id="bf2f7-399">macOS</span></span>                 | <span data-ttu-id="bf2f7-400">Architectures</span><span class="sxs-lookup"><span data-stu-id="bf2f7-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="bf2f7-401">3.1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-401">3.1</span></span>               | <span data-ttu-id="bf2f7-402">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="bf2f7-403">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-403">x64</span></span> | [<span data-ttu-id="bf2f7-404">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="bf2f7-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="bf2f7-405">3.0</span><span class="sxs-lookup"><span data-stu-id="bf2f7-405">3.0</span></span>               | <span data-ttu-id="bf2f7-406">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="bf2f7-407">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-407">x64</span></span> | [<span data-ttu-id="bf2f7-408">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="bf2f7-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="bf2f7-409">2.2</span><span class="sxs-lookup"><span data-stu-id="bf2f7-409">2.2</span></span>               | <span data-ttu-id="bf2f7-410">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="bf2f7-411">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-411">x64</span></span> | [<span data-ttu-id="bf2f7-412">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="bf2f7-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="bf2f7-413">2.1</span><span class="sxs-lookup"><span data-stu-id="bf2f7-413">2.1</span></span>               | <span data-ttu-id="bf2f7-414">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="bf2f7-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="bf2f7-415">x64</span><span class="sxs-lookup"><span data-stu-id="bf2f7-415">x64</span></span> | [<span data-ttu-id="bf2f7-416">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="bf2f7-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="bf2f7-417">À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019, qui sont distribués avec l’ID de développeur, doivent être certifiés.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="bf2f7-418">Cette exigence s’applique au Runtime .NET Core, kit SDK .NET Core et aux logiciels créés avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="bf2f7-419">Les programmes d’installation de .NET Core (Runtime et SDK) versions 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="bf2f7-420">Les versions antérieures publiées ne sont pas certifiées.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="bf2f7-421">Si vous exécutez une application non authentifiée, une erreur semblable à l’image suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerte de notaire Catalina macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="bf2f7-423">Pour plus d’informations sur la façon dont l’application de la notaire affecte .NET Core (et vos applications .NET Core), consultez [utilisation de la méthode de notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="bf2f7-424">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="bf2f7-424">libgdiplus</span></span>

<span data-ttu-id="bf2f7-425">Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="bf2f7-426">Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="bf2f7-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="bf2f7-427">Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="bf2f7-428">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf2f7-428">Next steps</span></span>

- <span data-ttu-id="bf2f7-429">Pour développer et exécuter des applications, installez le [Kit SDK .net Core](sdk.md) (y compris le Runtime).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="bf2f7-430">Pour exécuter des applications créées par d’autres utilisateurs, installez le [Runtime .net Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="bf2f7-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
