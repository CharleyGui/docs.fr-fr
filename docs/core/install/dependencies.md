---
title: Dépendances de kit SDK .NET Core et d’exécution-.NET Core
description: Décrit en détail la configuration requise pour le système d’exploitation et l’architecture de l’UC pour installer le kit SDK .NET Core et le runtime sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 42765d4402dfa17d4e962b2ecaf7a83e91853c76
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140994"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="e8638-103">Dépendances et exigences de .NET Core</span><span class="sxs-lookup"><span data-stu-id="e8638-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="e8638-104">Cet article détaille les systèmes d’exploitation et l’architecture du processeur pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8638-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="e8638-105">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="e8638-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="e8638-106">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e8638-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="e8638-107">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="e8638-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-108">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-109">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-109">OS</span></span>                            | <span data-ttu-id="e8638-110">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-110">Version</span></span>                        | <span data-ttu-id="e8638-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e8638-112">Client Windows</span><span class="sxs-lookup"><span data-stu-id="e8638-112">Windows Client</span></span>                | <span data-ttu-id="e8638-113">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="e8638-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e8638-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-114">x64, x86</span></span>        |
| <span data-ttu-id="e8638-115">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="e8638-115">Windows 10 Client</span></span>             | <span data-ttu-id="e8638-116">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="e8638-116">Version 1607+</span></span>                  | <span data-ttu-id="e8638-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-117">x64, x86</span></span>        |
| <span data-ttu-id="e8638-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e8638-118">Windows Server</span></span>                | <span data-ttu-id="e8638-119">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="e8638-119">2012 R2+</span></span>                       | <span data-ttu-id="e8638-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-120">x64, x86</span></span>        |
| <span data-ttu-id="e8638-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="e8638-121">Nano Server</span></span>                   | <span data-ttu-id="e8638-122">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="e8638-122">Version 1803+</span></span>                  | <span data-ttu-id="e8638-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-123">x64, ARM32</span></span>      |

<span data-ttu-id="e8638-124">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="e8638-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e8638-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="e8638-126">*.NET Core 3,0 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="e8638-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="e8638-127">Les versions de Windows suivantes sont prises en charge avec .NET Core 3,0 :</span><span class="sxs-lookup"><span data-stu-id="e8638-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-128">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-129">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-129">OS</span></span>                            | <span data-ttu-id="e8638-130">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-130">Version</span></span>                        | <span data-ttu-id="e8638-131">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e8638-132">Client Windows</span><span class="sxs-lookup"><span data-stu-id="e8638-132">Windows Client</span></span>                | <span data-ttu-id="e8638-133">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="e8638-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e8638-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-134">x64, x86</span></span>        |
| <span data-ttu-id="e8638-135">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="e8638-135">Windows 10 Client</span></span>             | <span data-ttu-id="e8638-136">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="e8638-136">Version 1607+</span></span>                  | <span data-ttu-id="e8638-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-137">x64, x86</span></span>        |
| <span data-ttu-id="e8638-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e8638-138">Windows Server</span></span>                | <span data-ttu-id="e8638-139">2012 R2 +</span><span class="sxs-lookup"><span data-stu-id="e8638-139">2012 R2+</span></span>                       | <span data-ttu-id="e8638-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-140">x64, x86</span></span>        |
| <span data-ttu-id="e8638-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="e8638-141">Nano Server</span></span>                   | <span data-ttu-id="e8638-142">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="e8638-142">Version 1803+</span></span>                  | <span data-ttu-id="e8638-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-143">x64, ARM32</span></span>      |

<span data-ttu-id="e8638-144">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="e8638-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="e8638-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="e8638-146">*.NET Core 2,2 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="e8638-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="e8638-147">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,2 :</span><span class="sxs-lookup"><span data-stu-id="e8638-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-148">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-149">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-149">OS</span></span>                            | <span data-ttu-id="e8638-150">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-150">Version</span></span>                        | <span data-ttu-id="e8638-151">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e8638-152">Client Windows</span><span class="sxs-lookup"><span data-stu-id="e8638-152">Windows Client</span></span>                | <span data-ttu-id="e8638-153">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="e8638-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e8638-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-154">x64, x86</span></span>        |
| <span data-ttu-id="e8638-155">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="e8638-155">Windows 10 Client</span></span>             | <span data-ttu-id="e8638-156">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="e8638-156">Version 1607+</span></span>                  | <span data-ttu-id="e8638-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-157">x64, x86</span></span>        |
| <span data-ttu-id="e8638-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e8638-158">Windows Server</span></span>                | <span data-ttu-id="e8638-159">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="e8638-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="e8638-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-160">x64, x86</span></span>        |
| <span data-ttu-id="e8638-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="e8638-161">Nano Server</span></span>                   | <span data-ttu-id="e8638-162">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="e8638-162">Version 1803+</span></span>                   | <span data-ttu-id="e8638-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-163">x64, ARM32</span></span>      |

<span data-ttu-id="e8638-164">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="e8638-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e8638-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e8638-166">Les versions de Windows suivantes sont prises en charge avec .NET Core 2,1 :</span><span class="sxs-lookup"><span data-stu-id="e8638-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-167">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-168">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-168">OS</span></span>                            | <span data-ttu-id="e8638-169">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-169">Version</span></span>                        | <span data-ttu-id="e8638-170">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="e8638-171">Client Windows</span><span class="sxs-lookup"><span data-stu-id="e8638-171">Windows Client</span></span>                | <span data-ttu-id="e8638-172">7 SP1 +, 8,1</span><span class="sxs-lookup"><span data-stu-id="e8638-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="e8638-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-173">x64, x86</span></span>        |
| <span data-ttu-id="e8638-174">Client Windows 10</span><span class="sxs-lookup"><span data-stu-id="e8638-174">Windows 10 Client</span></span>             | <span data-ttu-id="e8638-175">Version 1607 +</span><span class="sxs-lookup"><span data-stu-id="e8638-175">Version 1607+</span></span>                  | <span data-ttu-id="e8638-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-176">x64, x86</span></span>        |
| <span data-ttu-id="e8638-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="e8638-177">Windows Server</span></span>                | <span data-ttu-id="e8638-178">2008 R2 SP1 +</span><span class="sxs-lookup"><span data-stu-id="e8638-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="e8638-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="e8638-179">x64, x86</span></span>        |
| <span data-ttu-id="e8638-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="e8638-180">Nano Server</span></span>                   | <span data-ttu-id="e8638-181">Version 1803 +</span><span class="sxs-lookup"><span data-stu-id="e8638-181">Version 1803+</span></span>                  | <span data-ttu-id="e8638-182">64x</span><span class="sxs-lookup"><span data-stu-id="e8638-182">x64,</span></span>            |

<span data-ttu-id="e8638-183">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a><span data-ttu-id="e8638-184">Windows 7/Vista/8,1/Server 2008 R2/Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e8638-184">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="e8638-185">Des dépendances supplémentaires sont requises si vous installez le kit de développement logiciel (SDK) .NET ou le runtime sur les versions suivantes de Windows :</span><span class="sxs-lookup"><span data-stu-id="e8638-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="e8638-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="e8638-186">Windows 7 SP1</span></span>
- <span data-ttu-id="e8638-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="e8638-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="e8638-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="e8638-188">Windows 8.1</span></span>
- <span data-ttu-id="e8638-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="e8638-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="e8638-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="e8638-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="e8638-191">Installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e8638-191">Install the following:</span></span>

- <span data-ttu-id="e8638-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="e8638-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="e8638-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="e8638-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="e8638-194">La configuration requise ci-dessus est également requise si vous rencontrez l’une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="e8638-195">Le programme ne peut pas démarrer, car l' *API-MS-Win-CRT-Runtime-L1-1 1/-0. dll* est absente de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e8638-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="e8638-196">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="e8638-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="e8638-197">\- ou -</span><span class="sxs-lookup"><span data-stu-id="e8638-197">\- or -</span></span>
>
> <span data-ttu-id="e8638-198">Le programme ne peut pas démarrer, car l' *API-MS-Win-cor-TimeZone-L1-1 1/-0. dll* est absente de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e8638-198">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="e8638-199">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="e8638-199">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="e8638-200">\- ou -</span><span class="sxs-lookup"><span data-stu-id="e8638-200">\- or -</span></span>
>
> <span data-ttu-id="e8638-201">La bibliothèque *hostfxr. dll* a été trouvée, mais son chargement à partir de *C :\\\<path_to_app>\\hostfxr. dll* a échoué.</span><span class="sxs-lookup"><span data-stu-id="e8638-201">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="e8638-202">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="e8638-202">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="e8638-203">.NET Core 3,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="e8638-203">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="e8638-204">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e8638-204">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e8638-205">.NET Core 3,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-205">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-206">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-206">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-207">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-207">OS</span></span>                             | <span data-ttu-id="e8638-208">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-208">Version</span></span>               | <span data-ttu-id="e8638-209">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-209">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="e8638-210">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-210">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="e8638-211">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="e8638-211">6, 7, 8</span></span>               | <span data-ttu-id="e8638-212">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-212">x64</span></span> |
| <span data-ttu-id="e8638-213">CentOS</span><span class="sxs-lookup"><span data-stu-id="e8638-213">CentOS</span></span>                         | <span data-ttu-id="e8638-214">7+</span><span class="sxs-lookup"><span data-stu-id="e8638-214">7+</span></span>                    | <span data-ttu-id="e8638-215">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-215">x64</span></span> |
| <span data-ttu-id="e8638-216">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-216">Oracle Linux</span></span>                   | <span data-ttu-id="e8638-217">7+</span><span class="sxs-lookup"><span data-stu-id="e8638-217">7+</span></span>                    | <span data-ttu-id="e8638-218">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-218">x64</span></span> |
| <span data-ttu-id="e8638-219">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8638-219">Fedora</span></span>                         | <span data-ttu-id="e8638-220">plus de 30 ans</span><span class="sxs-lookup"><span data-stu-id="e8638-220">30+</span></span>                   | <span data-ttu-id="e8638-221">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-221">x64</span></span> |
| <span data-ttu-id="e8638-222">Debian</span><span class="sxs-lookup"><span data-stu-id="e8638-222">Debian</span></span>                         | <span data-ttu-id="e8638-223">9+</span><span class="sxs-lookup"><span data-stu-id="e8638-223">9+</span></span>                    | <span data-ttu-id="e8638-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="e8638-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e8638-225">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e8638-225">Ubuntu</span></span>                         | <span data-ttu-id="e8638-226">16.04+</span><span class="sxs-lookup"><span data-stu-id="e8638-226">16.04+</span></span>                | <span data-ttu-id="e8638-227">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="e8638-227">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e8638-228">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e8638-228">Linux Mint</span></span>                     | <span data-ttu-id="e8638-229">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="e8638-229">18+</span></span>                   | <span data-ttu-id="e8638-230">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-230">x64</span></span> |
| <span data-ttu-id="e8638-231">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e8638-231">openSUSE</span></span>                       | <span data-ttu-id="e8638-232">plus de 15</span><span class="sxs-lookup"><span data-stu-id="e8638-232">15+</span></span>                   | <span data-ttu-id="e8638-233">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-233">x64</span></span> |
| <span data-ttu-id="e8638-234">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e8638-234">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="e8638-235">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e8638-235">12 SP2+</span></span>               | <span data-ttu-id="e8638-236">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-236">x64</span></span> |
| <span data-ttu-id="e8638-237">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-237">Alpine Linux</span></span>                   | <span data-ttu-id="e8638-238">3.10 +</span><span class="sxs-lookup"><span data-stu-id="e8638-238">3.10+</span></span>                 | <span data-ttu-id="e8638-239">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="e8638-239">x64, ARM64</span></span> |

<span data-ttu-id="e8638-240">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,1](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-240">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="e8638-241">Pour plus d’informations sur l’installation de .NET Core 3,1 sur ARM64 (kernel 4.14 +), consultez [installation de .net core 3,0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="e8638-241">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8638-242">La prise en charge de ARM64 nécessite Linux kernel 4,14 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="e8638-242">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="e8638-243">Certaines distributions Linux répondent à cette exigence, contrairement à d’autres.</span><span class="sxs-lookup"><span data-stu-id="e8638-243">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="e8638-244">Par exemple, Ubuntu 18,04 est pris en charge, mais Ubuntu 16,04 ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="e8638-244">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="e8638-245">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e8638-245">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="e8638-246">*.NET Core 3,0 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="e8638-246">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="e8638-247">.NET Core 3,0 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="e8638-247">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="e8638-248">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e8638-248">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e8638-249">.NET Core 3,0 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-249">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-250">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-250">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-251">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-251">OS</span></span>                             | <span data-ttu-id="e8638-252">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-252">Version</span></span>               | <span data-ttu-id="e8638-253">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-253">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="e8638-254">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-254">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="e8638-255">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="e8638-255">6, 7, 8</span></span>               | <span data-ttu-id="e8638-256">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-256">x64</span></span> |
| <span data-ttu-id="e8638-257">CentOS</span><span class="sxs-lookup"><span data-stu-id="e8638-257">CentOS</span></span>                         | <span data-ttu-id="e8638-258">7+</span><span class="sxs-lookup"><span data-stu-id="e8638-258">7+</span></span>                    | <span data-ttu-id="e8638-259">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-259">x64</span></span> |
| <span data-ttu-id="e8638-260">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-260">Oracle Linux</span></span>                   | <span data-ttu-id="e8638-261">7+</span><span class="sxs-lookup"><span data-stu-id="e8638-261">7+</span></span>                    | <span data-ttu-id="e8638-262">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-262">x64</span></span> |
| <span data-ttu-id="e8638-263">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8638-263">Fedora</span></span>                         | <span data-ttu-id="e8638-264">29 +</span><span class="sxs-lookup"><span data-stu-id="e8638-264">29+</span></span>                   | <span data-ttu-id="e8638-265">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-265">x64</span></span> |
| <span data-ttu-id="e8638-266">Debian</span><span class="sxs-lookup"><span data-stu-id="e8638-266">Debian</span></span>                         | <span data-ttu-id="e8638-267">9+</span><span class="sxs-lookup"><span data-stu-id="e8638-267">9+</span></span>                    | <span data-ttu-id="e8638-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="e8638-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e8638-269">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e8638-269">Ubuntu</span></span>                         | <span data-ttu-id="e8638-270">16.04+</span><span class="sxs-lookup"><span data-stu-id="e8638-270">16.04+</span></span>                | <span data-ttu-id="e8638-271">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="e8638-271">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="e8638-272">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e8638-272">Linux Mint</span></span>                     | <span data-ttu-id="e8638-273">plus de 18 ans</span><span class="sxs-lookup"><span data-stu-id="e8638-273">18+</span></span>                   | <span data-ttu-id="e8638-274">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-274">x64</span></span> |
| <span data-ttu-id="e8638-275">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e8638-275">openSUSE</span></span>                       | <span data-ttu-id="e8638-276">plus de 15</span><span class="sxs-lookup"><span data-stu-id="e8638-276">15+</span></span>                   | <span data-ttu-id="e8638-277">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-277">x64</span></span> |
| <span data-ttu-id="e8638-278">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e8638-278">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="e8638-279">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e8638-279">12 SP2+</span></span>               | <span data-ttu-id="e8638-280">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-280">x64</span></span> |
| <span data-ttu-id="e8638-281">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-281">Alpine Linux</span></span>                   | <span data-ttu-id="e8638-282">3.8+</span><span class="sxs-lookup"><span data-stu-id="e8638-282">3.8+</span></span>                  | <span data-ttu-id="e8638-283">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="e8638-283">x64, ARM64</span></span> |

<span data-ttu-id="e8638-284">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 3,0 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-284">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="e8638-285">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="e8638-285">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="e8638-286">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="e8638-286">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="e8638-287">*.NET Core 2,2 n’est pas pris en charge pour le moment. Pour plus d’informations, consultez la [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="e8638-287">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="e8638-288">.NET Core 2,2 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="e8638-288">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="e8638-289">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e8638-289">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e8638-290">.NET Core 2,2 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-290">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-291">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-291">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-292">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-292">OS</span></span>                             |  <span data-ttu-id="e8638-293">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-293">Version</span></span>                |  <span data-ttu-id="e8638-294">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-294">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="e8638-295">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-295">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="e8638-296">6, 7</span><span class="sxs-lookup"><span data-stu-id="e8638-296">6, 7</span></span>                   | <span data-ttu-id="e8638-297">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-297">x64</span></span> |
| <span data-ttu-id="e8638-298">CentOS</span><span class="sxs-lookup"><span data-stu-id="e8638-298">CentOS</span></span>                         |  <span data-ttu-id="e8638-299">7</span><span class="sxs-lookup"><span data-stu-id="e8638-299">7</span></span>                      | <span data-ttu-id="e8638-300">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-300">x64</span></span> |
| <span data-ttu-id="e8638-301">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-301">Oracle Linux</span></span>                   |  <span data-ttu-id="e8638-302">7</span><span class="sxs-lookup"><span data-stu-id="e8638-302">7</span></span>                      | <span data-ttu-id="e8638-303">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-303">x64</span></span> |
| <span data-ttu-id="e8638-304">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8638-304">Fedora</span></span>                         |  <span data-ttu-id="e8638-305">29, 30</span><span class="sxs-lookup"><span data-stu-id="e8638-305">29, 30</span></span>                 | <span data-ttu-id="e8638-306">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-306">x64</span></span> |
| <span data-ttu-id="e8638-307">Debian</span><span class="sxs-lookup"><span data-stu-id="e8638-307">Debian</span></span>                         |  <span data-ttu-id="e8638-308">9</span><span class="sxs-lookup"><span data-stu-id="e8638-308">9</span></span>                      | <span data-ttu-id="e8638-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-309">x64, ARM32</span></span> |
| <span data-ttu-id="e8638-310">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e8638-310">Ubuntu</span></span>                         |  <span data-ttu-id="e8638-311">16,04, 18,04, 18,10</span><span class="sxs-lookup"><span data-stu-id="e8638-311">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="e8638-312">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-312">x64, ARM32</span></span> |
| <span data-ttu-id="e8638-313">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e8638-313">Linux Mint</span></span>                     |  <span data-ttu-id="e8638-314">17, 18</span><span class="sxs-lookup"><span data-stu-id="e8638-314">17, 18</span></span>                 | <span data-ttu-id="e8638-315">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-315">x64</span></span> |
| <span data-ttu-id="e8638-316">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e8638-316">openSUSE</span></span>                       |  <span data-ttu-id="e8638-317">plus de 15</span><span class="sxs-lookup"><span data-stu-id="e8638-317">15+</span></span>                    | <span data-ttu-id="e8638-318">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-318">x64</span></span> |
| <span data-ttu-id="e8638-319">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e8638-319">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="e8638-320">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e8638-320">12 SP2+</span></span>                | <span data-ttu-id="e8638-321">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-321">x64</span></span> |
| <span data-ttu-id="e8638-322">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-322">Alpine Linux</span></span>                   |  <span data-ttu-id="e8638-323">3.8+</span><span class="sxs-lookup"><span data-stu-id="e8638-323">3.8+</span></span>                   | <span data-ttu-id="e8638-324">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-324">x64</span></span> |

<span data-ttu-id="e8638-325">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,2 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-325">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="e8638-326">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e8638-326">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="e8638-327">.NET Core 2,1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="e8638-327">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="e8638-328">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="e8638-328">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="e8638-329">.NET Core 2,1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-329">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-330">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-330">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-331">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="e8638-331">OS</span></span>                             |  <span data-ttu-id="e8638-332">Version</span><span class="sxs-lookup"><span data-stu-id="e8638-332">Version</span></span>                |  <span data-ttu-id="e8638-333">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-333">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="e8638-334">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-334">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="e8638-335">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="e8638-335">6, 7, 8</span></span>                | <span data-ttu-id="e8638-336">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-336">x64</span></span> |
| <span data-ttu-id="e8638-337">CentOS</span><span class="sxs-lookup"><span data-stu-id="e8638-337">CentOS</span></span>                         |  <span data-ttu-id="e8638-338">7+</span><span class="sxs-lookup"><span data-stu-id="e8638-338">7+</span></span>                     | <span data-ttu-id="e8638-339">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-339">x64</span></span> |
| <span data-ttu-id="e8638-340">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-340">Oracle Linux</span></span>                   |  <span data-ttu-id="e8638-341">7+</span><span class="sxs-lookup"><span data-stu-id="e8638-341">7+</span></span>                     | <span data-ttu-id="e8638-342">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-342">x64</span></span> |
| <span data-ttu-id="e8638-343">Fedora</span><span class="sxs-lookup"><span data-stu-id="e8638-343">Fedora</span></span>                         |  <span data-ttu-id="e8638-344">plus de 30 ans</span><span class="sxs-lookup"><span data-stu-id="e8638-344">30+</span></span>                    | <span data-ttu-id="e8638-345">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-345">x64</span></span> |
| <span data-ttu-id="e8638-346">Debian</span><span class="sxs-lookup"><span data-stu-id="e8638-346">Debian</span></span>                         |  <span data-ttu-id="e8638-347">9</span><span class="sxs-lookup"><span data-stu-id="e8638-347">9</span></span>                      | <span data-ttu-id="e8638-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-348">x64, ARM32</span></span> |
| <span data-ttu-id="e8638-349">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e8638-349">Ubuntu</span></span>                         |  <span data-ttu-id="e8638-350">16,04, 18,04, 19,04, 19,10</span><span class="sxs-lookup"><span data-stu-id="e8638-350">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="e8638-351">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="e8638-351">x64, ARM32</span></span> |
| <span data-ttu-id="e8638-352">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="e8638-352">Linux Mint</span></span>                     |  <span data-ttu-id="e8638-353">17+</span><span class="sxs-lookup"><span data-stu-id="e8638-353">17+</span></span>                    | <span data-ttu-id="e8638-354">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-354">x64</span></span> |
| <span data-ttu-id="e8638-355">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="e8638-355">openSUSE</span></span>                       |  <span data-ttu-id="e8638-356">plus de 15</span><span class="sxs-lookup"><span data-stu-id="e8638-356">15+</span></span>                    | <span data-ttu-id="e8638-357">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-357">x64</span></span> |
| <span data-ttu-id="e8638-358">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="e8638-358">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="e8638-359">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="e8638-359">12 SP2+</span></span>                | <span data-ttu-id="e8638-360">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-360">x64</span></span> |
| <span data-ttu-id="e8638-361">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-361">Alpine Linux</span></span>                   |  <span data-ttu-id="e8638-362">3.8+</span><span class="sxs-lookup"><span data-stu-id="e8638-362">3.8+</span></span>                   | <span data-ttu-id="e8638-363">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-363">x64</span></span> |

<span data-ttu-id="e8638-364">Pour plus d’informations sur les systèmes d’exploitation, les distributions et la stratégie de cycle de vie de .NET Core 2,1 pris en charge, consultez [versions de système d’exploitation prises en charge pour .net core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-364">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="e8638-365">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="e8638-365">Linux distribution dependencies</span></span>

<span data-ttu-id="e8638-366">En fonction de votre distribution Linux, vous devrez peut-être installer des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e8638-366">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8638-367">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="e8638-367">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="e8638-368">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="e8638-368">Ubuntu</span></span>

<span data-ttu-id="e8638-369">Les distributions Ubuntu requièrent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-369">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="e8638-370">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="e8638-370">liblttng-ust0</span></span>
- <span data-ttu-id="e8638-371">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="e8638-371">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="e8638-372">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="e8638-372">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="e8638-373">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="e8638-373">libssl1.0.0</span></span>
- <span data-ttu-id="e8638-374">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="e8638-374">libkrb5-3</span></span>
- <span data-ttu-id="e8638-375">zlib1g</span><span class="sxs-lookup"><span data-stu-id="e8638-375">zlib1g</span></span>
- <span data-ttu-id="e8638-376">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="e8638-376">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="e8638-377">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="e8638-377">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="e8638-378">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="e8638-378">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="e8638-379">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="e8638-379">libicu60 (for 18.x)</span></span>

<span data-ttu-id="e8638-380">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="e8638-380">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="e8638-381">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="e8638-381">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="e8638-382">La plupart des versions d’Ubuntu incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="e8638-382">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="e8638-383">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="e8638-383">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="e8638-384">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="e8638-384">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="e8638-385">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="e8638-385">CentOS and Fedora</span></span>

<span data-ttu-id="e8638-386">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-386">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="e8638-387">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="e8638-387">lttng-ust</span></span>
- <span data-ttu-id="e8638-388">libcurl</span><span class="sxs-lookup"><span data-stu-id="e8638-388">libcurl</span></span>
- <span data-ttu-id="e8638-389">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="e8638-389">openssl-libs</span></span>
- <span data-ttu-id="e8638-390">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="e8638-390">krb5-libs</span></span>
- <span data-ttu-id="e8638-391">libicu</span><span class="sxs-lookup"><span data-stu-id="e8638-391">libicu</span></span>
- <span data-ttu-id="e8638-392">zlib</span><span class="sxs-lookup"><span data-stu-id="e8638-392">zlib</span></span>

<span data-ttu-id="e8638-393">Utilisateurs Fedora : si la version de votre OpenSSL >= 1,1, vous devez installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="e8638-393">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="e8638-394">Pour .NET Core 2,0, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="e8638-394">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="e8638-395">libunwind</span><span class="sxs-lookup"><span data-stu-id="e8638-395">libunwind</span></span>
- <span data-ttu-id="e8638-396">libuuid</span><span class="sxs-lookup"><span data-stu-id="e8638-396">libuuid</span></span>

<span data-ttu-id="e8638-397">Pour plus d’informations sur les dépendances, consultez [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-397">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="e8638-398">Pour les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* , vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="e8638-398">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="e8638-399">libgdiplus (version 6.0.1 ou ultérieure)</span><span class="sxs-lookup"><span data-stu-id="e8638-399">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="e8638-400">La plupart des versions de CentOS et Fedora incluent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="e8638-400">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="e8638-401">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="e8638-401">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="e8638-402">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="e8638-402">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="e8638-403">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="e8638-403">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="e8638-404">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="e8638-404">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="e8638-405">Version de .NET Core</span><span class="sxs-lookup"><span data-stu-id="e8638-405">.NET Core Version</span></span> | <span data-ttu-id="e8638-406">macOS</span><span class="sxs-lookup"><span data-stu-id="e8638-406">macOS</span></span>                 | <span data-ttu-id="e8638-407">Architectures</span><span class="sxs-lookup"><span data-stu-id="e8638-407">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="e8638-408">3.1</span><span class="sxs-lookup"><span data-stu-id="e8638-408">3.1</span></span>               | <span data-ttu-id="e8638-409">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="e8638-409">High Sierra (10.13+)</span></span>  | <span data-ttu-id="e8638-410">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-410">x64</span></span> | [<span data-ttu-id="e8638-411">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="e8638-411">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="e8638-412">3.0</span><span class="sxs-lookup"><span data-stu-id="e8638-412">3.0</span></span>               | <span data-ttu-id="e8638-413">High Sierra (10.13 +)</span><span class="sxs-lookup"><span data-stu-id="e8638-413">High Sierra (10.13+)</span></span>  | <span data-ttu-id="e8638-414">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-414">x64</span></span> | [<span data-ttu-id="e8638-415">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="e8638-415">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="e8638-416">2.2</span><span class="sxs-lookup"><span data-stu-id="e8638-416">2.2</span></span>               | <span data-ttu-id="e8638-417">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="e8638-417">Sierra (10.12+)</span></span>       | <span data-ttu-id="e8638-418">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-418">x64</span></span> | [<span data-ttu-id="e8638-419">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="e8638-419">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="e8638-420">2.1</span><span class="sxs-lookup"><span data-stu-id="e8638-420">2.1</span></span>               | <span data-ttu-id="e8638-421">Sierra (10.12 +)</span><span class="sxs-lookup"><span data-stu-id="e8638-421">Sierra (10.12+)</span></span>       | <span data-ttu-id="e8638-422">x64</span><span class="sxs-lookup"><span data-stu-id="e8638-422">x64</span></span> | [<span data-ttu-id="e8638-423">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="e8638-423">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="e8638-424">À partir de macOS Catalina (version 10,15), tous les logiciels générés après le 1er juin 2019, qui sont distribués avec l’ID de développeur, doivent être certifiés.</span><span class="sxs-lookup"><span data-stu-id="e8638-424">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="e8638-425">Cette exigence s’applique au Runtime .NET Core, kit SDK .NET Core et aux logiciels créés avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e8638-425">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="e8638-426">Les programmes d’installation de .NET Core (Runtime et SDK) versions 3,1, 3,0 et 2,1 ont été certifiés depuis le 18 février 2020.</span><span class="sxs-lookup"><span data-stu-id="e8638-426">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="e8638-427">Les versions antérieures publiées ne sont pas certifiées.</span><span class="sxs-lookup"><span data-stu-id="e8638-427">Prior released versions aren't notarized.</span></span> <span data-ttu-id="e8638-428">Si vous exécutez une application non authentifiée, une erreur semblable à l’image suivante s’affiche :</span><span class="sxs-lookup"><span data-stu-id="e8638-428">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerte de notaire Catalina macOS](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="e8638-430">Pour plus d’informations sur la façon dont l’application de la notaire affecte .NET Core (et vos applications .NET Core), consultez [utilisation de la méthode de notaire Catalina MacOS](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-430">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="e8638-431">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="e8638-431">libgdiplus</span></span>

<span data-ttu-id="e8638-432">Les applications .NET Core qui utilisent l’assembly *System. Drawing. Common* nécessitent l’installation de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="e8638-432">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="e8638-433">Pour obtenir facilement des libgdiplus, vous pouvez utiliser le gestionnaire de package [Homebrew (« Brass »)](https://brew.sh/) pour MacOS.</span><span class="sxs-lookup"><span data-stu-id="e8638-433">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="e8638-434">Après l’installation de la commande *infuse*, installez libgdiplus en exécutant les commandes suivantes à une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="e8638-434">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="e8638-435">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="e8638-435">Next steps</span></span>

- <span data-ttu-id="e8638-436">Pour développer et exécuter des applications, installez le [Kit SDK .net Core](sdk.md) (y compris le Runtime).</span><span class="sxs-lookup"><span data-stu-id="e8638-436">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="e8638-437">Pour exécuter des applications créées par d’autres utilisateurs, installez le [Runtime .net Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="e8638-437">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
