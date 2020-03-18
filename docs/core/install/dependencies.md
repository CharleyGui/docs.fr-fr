---
title: .NET Core SDK et dépendances de temps d’exécution - .NET Core
description: Détaille le système d’exploitation et les conditions préalables à l’architecture CPU pour installer le SDK core .NET et l’heure d’exécution sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157806"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="6528e-103">.NET Dépendances et exigences de base</span><span class="sxs-lookup"><span data-stu-id="6528e-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="6528e-104">Cet article détaille quels systèmes d’exploitation et l’architecture CPU sont pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6528e-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="6528e-105">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="6528e-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="6528e-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6528e-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="6528e-107">Les versions Windows suivantes sont prises en charge avec .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="6528e-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-108">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-109">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-109">OS</span></span>                            | <span data-ttu-id="6528e-110">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-110">Version</span></span>                        | <span data-ttu-id="6528e-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6528e-112">Client Windows</span><span class="sxs-lookup"><span data-stu-id="6528e-112">Windows Client</span></span>                | <span data-ttu-id="6528e-113">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="6528e-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6528e-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-114">x64, x86</span></span>        |
| <span data-ttu-id="6528e-115">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="6528e-115">Windows 10 Client</span></span>             | <span data-ttu-id="6528e-116">Version 1607</span><span class="sxs-lookup"><span data-stu-id="6528e-116">Version 1607+</span></span>                  | <span data-ttu-id="6528e-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-117">x64, x86</span></span>        |
| <span data-ttu-id="6528e-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6528e-118">Windows Server</span></span>                | <span data-ttu-id="6528e-119">R2 2012</span><span class="sxs-lookup"><span data-stu-id="6528e-119">2012 R2+</span></span>                       | <span data-ttu-id="6528e-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-120">x64, x86</span></span>        |
| <span data-ttu-id="6528e-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6528e-121">Nano Server</span></span>                   | <span data-ttu-id="6528e-122">Version 1803</span><span class="sxs-lookup"><span data-stu-id="6528e-122">Version 1803+</span></span>                  | <span data-ttu-id="6528e-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-123">x64, ARM32</span></span>      |

<span data-ttu-id="6528e-124">Pour plus d’informations sur .NET Core 3.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 3.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="6528e-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6528e-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="6528e-126">Les versions Windows suivantes sont prises en charge avec .NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="6528e-126">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-127">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-127">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-128">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-128">OS</span></span>                            | <span data-ttu-id="6528e-129">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-129">Version</span></span>                        | <span data-ttu-id="6528e-130">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-130">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6528e-131">Client Windows</span><span class="sxs-lookup"><span data-stu-id="6528e-131">Windows Client</span></span>                | <span data-ttu-id="6528e-132">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="6528e-132">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6528e-133">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-133">x64, x86</span></span>        |
| <span data-ttu-id="6528e-134">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="6528e-134">Windows 10 Client</span></span>             | <span data-ttu-id="6528e-135">Version 1607</span><span class="sxs-lookup"><span data-stu-id="6528e-135">Version 1607+</span></span>                  | <span data-ttu-id="6528e-136">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-136">x64, x86</span></span>        |
| <span data-ttu-id="6528e-137">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6528e-137">Windows Server</span></span>                | <span data-ttu-id="6528e-138">R2 2012</span><span class="sxs-lookup"><span data-stu-id="6528e-138">2012 R2+</span></span>                       | <span data-ttu-id="6528e-139">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-139">x64, x86</span></span>        |
| <span data-ttu-id="6528e-140">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6528e-140">Nano Server</span></span>                   | <span data-ttu-id="6528e-141">Version 1803</span><span class="sxs-lookup"><span data-stu-id="6528e-141">Version 1803+</span></span>                  | <span data-ttu-id="6528e-142">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-142">x64, ARM32</span></span>      |

<span data-ttu-id="6528e-143">Pour plus d’informations sur les systèmes d’exploitation supportés .NET Core 3.0, les distributions et la politique du cycle de vie, voir [.NET Core 3.0 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-143">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="6528e-144">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6528e-144">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6528e-145">Les versions Windows suivantes sont prises en charge avec .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="6528e-145">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-146">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-146">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-147">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-147">OS</span></span>                            | <span data-ttu-id="6528e-148">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-148">Version</span></span>                        | <span data-ttu-id="6528e-149">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-149">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6528e-150">Client Windows</span><span class="sxs-lookup"><span data-stu-id="6528e-150">Windows Client</span></span>                | <span data-ttu-id="6528e-151">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="6528e-151">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6528e-152">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-152">x64, x86</span></span>        |
| <span data-ttu-id="6528e-153">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="6528e-153">Windows 10 Client</span></span>             | <span data-ttu-id="6528e-154">Version 1607</span><span class="sxs-lookup"><span data-stu-id="6528e-154">Version 1607+</span></span>                  | <span data-ttu-id="6528e-155">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-155">x64, x86</span></span>        |
| <span data-ttu-id="6528e-156">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6528e-156">Windows Server</span></span>                | <span data-ttu-id="6528e-157">R2 SP1 2008</span><span class="sxs-lookup"><span data-stu-id="6528e-157">2008 R2 SP1+</span></span>                   | <span data-ttu-id="6528e-158">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-158">x64, x86</span></span>        |
| <span data-ttu-id="6528e-159">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6528e-159">Nano Server</span></span>                   | <span data-ttu-id="6528e-160">Version 1803</span><span class="sxs-lookup"><span data-stu-id="6528e-160">Version 1803+</span></span>                   | <span data-ttu-id="6528e-161">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-161">x64, ARM32</span></span>      |

<span data-ttu-id="6528e-162">Pour plus d’informations sur .NET Core 2.2 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.2 Versions OS pris en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-162">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="6528e-163">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6528e-163">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6528e-164">Les versions Windows suivantes sont prises en charge avec .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="6528e-164">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-165">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-165">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-166">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-166">OS</span></span>                            | <span data-ttu-id="6528e-167">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-167">Version</span></span>                        | <span data-ttu-id="6528e-168">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-168">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="6528e-169">Client Windows</span><span class="sxs-lookup"><span data-stu-id="6528e-169">Windows Client</span></span>                | <span data-ttu-id="6528e-170">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="6528e-170">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="6528e-171">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-171">x64, x86</span></span>        |
| <span data-ttu-id="6528e-172">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="6528e-172">Windows 10 Client</span></span>             | <span data-ttu-id="6528e-173">Version 1607</span><span class="sxs-lookup"><span data-stu-id="6528e-173">Version 1607+</span></span>                  | <span data-ttu-id="6528e-174">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-174">x64, x86</span></span>        |
| <span data-ttu-id="6528e-175">Windows Server</span><span class="sxs-lookup"><span data-stu-id="6528e-175">Windows Server</span></span>                | <span data-ttu-id="6528e-176">R2 SP1 2008</span><span class="sxs-lookup"><span data-stu-id="6528e-176">2008 R2 SP1+</span></span>                   | <span data-ttu-id="6528e-177">x64, x86</span><span class="sxs-lookup"><span data-stu-id="6528e-177">x64, x86</span></span>        |
| <span data-ttu-id="6528e-178">Nano Server</span><span class="sxs-lookup"><span data-stu-id="6528e-178">Nano Server</span></span>                   | <span data-ttu-id="6528e-179">Version 1803</span><span class="sxs-lookup"><span data-stu-id="6528e-179">Version 1803+</span></span>                  | <span data-ttu-id="6528e-180">x64,</span><span class="sxs-lookup"><span data-stu-id="6528e-180">x64,</span></span>            |

<span data-ttu-id="6528e-181">Pour plus d’informations sur .NET Core 2.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-181">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="6528e-182">Windows 7 / Vista / 8.1 / Serveur 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6528e-182">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="6528e-183">Des dépendances supplémentaires sont nécessaires si vous installez le SDK .NET ou l’heure d’exécution sur les versions Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-183">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="6528e-184">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="6528e-184">Windows 7 SP1</span></span>
- <span data-ttu-id="6528e-185">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="6528e-185">Windows Vista SP 2</span></span>
- <span data-ttu-id="6528e-186">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="6528e-186">Windows 8.1</span></span>
- <span data-ttu-id="6528e-187">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="6528e-187">Windows Server 2008 R2</span></span>
- <span data-ttu-id="6528e-188">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="6528e-188">Windows Server 2012 R2</span></span>

<span data-ttu-id="6528e-189">Installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6528e-189">Install the following:</span></span>

- <span data-ttu-id="6528e-190">[Microsoft Visual C 2015 Red redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="6528e-190">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="6528e-191">KB2533623</span><span class="sxs-lookup"><span data-stu-id="6528e-191">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="6528e-192">Les exigences ci-dessus sont également requises si vous tombez sur l’une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-192">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="6528e-193">Le programme ne peut pas commencer parce que *api-ms-win-crt-runtime-l1-1-0.dll* est absent de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6528e-193">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="6528e-194">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="6528e-194">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="6528e-195">\- ou -</span><span class="sxs-lookup"><span data-stu-id="6528e-195">\- or -</span></span>
>
> <span data-ttu-id="6528e-196">La bibliothèque *hostfxr.dll* a été trouvée, mais le chargement de *C:\\\<path_to_app>\\hostfxr.dll* échoué.</span><span class="sxs-lookup"><span data-stu-id="6528e-196">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="6528e-197">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="6528e-197">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="6528e-198">.NET Core 3.1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="6528e-198">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="6528e-199">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6528e-199">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6528e-200">.NET Core 3.1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-200">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-201">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-201">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-202">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-202">OS</span></span>                             | <span data-ttu-id="6528e-203">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-203">Version</span></span>               | <span data-ttu-id="6528e-204">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-204">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="6528e-205">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-205">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="6528e-206">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="6528e-206">6, 7, 8</span></span>               | <span data-ttu-id="6528e-207">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-207">x64</span></span> |
| <span data-ttu-id="6528e-208">CentOS</span><span class="sxs-lookup"><span data-stu-id="6528e-208">CentOS</span></span>                         | <span data-ttu-id="6528e-209">7+</span><span class="sxs-lookup"><span data-stu-id="6528e-209">7+</span></span>                    | <span data-ttu-id="6528e-210">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-210">x64</span></span> |
| <span data-ttu-id="6528e-211">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-211">Oracle Linux</span></span>                   | <span data-ttu-id="6528e-212">7+</span><span class="sxs-lookup"><span data-stu-id="6528e-212">7+</span></span>                    | <span data-ttu-id="6528e-213">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-213">x64</span></span> |
| <span data-ttu-id="6528e-214">Fedora</span><span class="sxs-lookup"><span data-stu-id="6528e-214">Fedora</span></span>                         | <span data-ttu-id="6528e-215">29 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-215">29+</span></span>                   | <span data-ttu-id="6528e-216">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-216">x64</span></span> |
| <span data-ttu-id="6528e-217">Debian</span><span class="sxs-lookup"><span data-stu-id="6528e-217">Debian</span></span>                         | <span data-ttu-id="6528e-218">9+</span><span class="sxs-lookup"><span data-stu-id="6528e-218">9+</span></span>                    | <span data-ttu-id="6528e-219">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6528e-219">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6528e-220">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6528e-220">Ubuntu</span></span>                         | <span data-ttu-id="6528e-221">16.04+</span><span class="sxs-lookup"><span data-stu-id="6528e-221">16.04+</span></span>                | <span data-ttu-id="6528e-222">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6528e-222">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6528e-223">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6528e-223">Linux Mint</span></span>                     | <span data-ttu-id="6528e-224">18 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-224">18+</span></span>                   | <span data-ttu-id="6528e-225">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-225">x64</span></span> |
| <span data-ttu-id="6528e-226">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="6528e-226">openSUSE</span></span>                       | <span data-ttu-id="6528e-227">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-227">15+</span></span>                   | <span data-ttu-id="6528e-228">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-228">x64</span></span> |
| <span data-ttu-id="6528e-229">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="6528e-229">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="6528e-230">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6528e-230">12 SP2+</span></span>               | <span data-ttu-id="6528e-231">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-231">x64</span></span> |
| <span data-ttu-id="6528e-232">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-232">Alpine Linux</span></span>                   | <span data-ttu-id="6528e-233">3.10</span><span class="sxs-lookup"><span data-stu-id="6528e-233">3.10+</span></span>                 | <span data-ttu-id="6528e-234">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="6528e-234">x64, ARM64</span></span> |

<span data-ttu-id="6528e-235">Pour plus d’informations sur .NET Core 3.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 3.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-235">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="6528e-236">Pour plus d’informations sur la façon d’installer .NET Core 3.1 sur ARM64 (noyau 4.14), voir [Installing .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="6528e-236">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6528e-237">Le support ARM64 nécessite un noyau Linux 4.14 ou plus.</span><span class="sxs-lookup"><span data-stu-id="6528e-237">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="6528e-238">Certaines distributions linux satisfont à cette exigence tandis que d’autres ne le font pas.</span><span class="sxs-lookup"><span data-stu-id="6528e-238">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="6528e-239">Par exemple, Ubuntu 18.04 est pris en charge, mais Ubuntu 16.04 ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="6528e-239">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="6528e-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6528e-240">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="6528e-241">.NET Core 3.0 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="6528e-241">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="6528e-242">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6528e-242">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6528e-243">.NET Core 3.0 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-243">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-244">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-244">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-245">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-245">OS</span></span>                             | <span data-ttu-id="6528e-246">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-246">Version</span></span>               | <span data-ttu-id="6528e-247">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-247">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="6528e-248">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-248">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="6528e-249">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="6528e-249">6, 7, 8</span></span>               | <span data-ttu-id="6528e-250">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-250">x64</span></span> |
| <span data-ttu-id="6528e-251">CentOS</span><span class="sxs-lookup"><span data-stu-id="6528e-251">CentOS</span></span>                         | <span data-ttu-id="6528e-252">7+</span><span class="sxs-lookup"><span data-stu-id="6528e-252">7+</span></span>                    | <span data-ttu-id="6528e-253">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-253">x64</span></span> |
| <span data-ttu-id="6528e-254">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-254">Oracle Linux</span></span>                   | <span data-ttu-id="6528e-255">7+</span><span class="sxs-lookup"><span data-stu-id="6528e-255">7+</span></span>                    | <span data-ttu-id="6528e-256">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-256">x64</span></span> |
| <span data-ttu-id="6528e-257">Fedora</span><span class="sxs-lookup"><span data-stu-id="6528e-257">Fedora</span></span>                         | <span data-ttu-id="6528e-258">29 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-258">29+</span></span>                   | <span data-ttu-id="6528e-259">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-259">x64</span></span> |
| <span data-ttu-id="6528e-260">Debian</span><span class="sxs-lookup"><span data-stu-id="6528e-260">Debian</span></span>                         | <span data-ttu-id="6528e-261">9+</span><span class="sxs-lookup"><span data-stu-id="6528e-261">9+</span></span>                    | <span data-ttu-id="6528e-262">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6528e-262">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6528e-263">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6528e-263">Ubuntu</span></span>                         | <span data-ttu-id="6528e-264">16.04+</span><span class="sxs-lookup"><span data-stu-id="6528e-264">16.04+</span></span>                | <span data-ttu-id="6528e-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="6528e-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="6528e-266">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6528e-266">Linux Mint</span></span>                     | <span data-ttu-id="6528e-267">18 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-267">18+</span></span>                   | <span data-ttu-id="6528e-268">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-268">x64</span></span> |
| <span data-ttu-id="6528e-269">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="6528e-269">openSUSE</span></span>                       | <span data-ttu-id="6528e-270">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-270">15+</span></span>                   | <span data-ttu-id="6528e-271">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-271">x64</span></span> |
| <span data-ttu-id="6528e-272">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="6528e-272">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="6528e-273">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6528e-273">12 SP2+</span></span>               | <span data-ttu-id="6528e-274">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-274">x64</span></span> |
| <span data-ttu-id="6528e-275">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-275">Alpine Linux</span></span>                   | <span data-ttu-id="6528e-276">3.8+</span><span class="sxs-lookup"><span data-stu-id="6528e-276">3.8+</span></span>                  | <span data-ttu-id="6528e-277">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="6528e-277">x64, ARM64</span></span> |

<span data-ttu-id="6528e-278">Pour plus d’informations sur les systèmes d’exploitation supportés .NET Core 3.0, les distributions et la politique du cycle de vie, voir [.NET Core 3.0 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-278">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="6528e-279">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="6528e-279">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="6528e-280">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="6528e-280">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="6528e-281">.NET Core 2.2 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="6528e-281">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="6528e-282">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6528e-282">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6528e-283">.NET Core 2.2 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-283">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-284">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-284">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-285">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-285">OS</span></span>                             |  <span data-ttu-id="6528e-286">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-286">Version</span></span>                |  <span data-ttu-id="6528e-287">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-287">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="6528e-288">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-288">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="6528e-289">6, 7</span><span class="sxs-lookup"><span data-stu-id="6528e-289">6, 7</span></span>                   | <span data-ttu-id="6528e-290">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-290">x64</span></span> |
| <span data-ttu-id="6528e-291">CentOS</span><span class="sxs-lookup"><span data-stu-id="6528e-291">CentOS</span></span>                         |  <span data-ttu-id="6528e-292">7</span><span class="sxs-lookup"><span data-stu-id="6528e-292">7</span></span>                      | <span data-ttu-id="6528e-293">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-293">x64</span></span> |
| <span data-ttu-id="6528e-294">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-294">Oracle Linux</span></span>                   |  <span data-ttu-id="6528e-295">7</span><span class="sxs-lookup"><span data-stu-id="6528e-295">7</span></span>                      | <span data-ttu-id="6528e-296">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-296">x64</span></span> |
| <span data-ttu-id="6528e-297">Fedora</span><span class="sxs-lookup"><span data-stu-id="6528e-297">Fedora</span></span>                         |  <span data-ttu-id="6528e-298">29, 30</span><span class="sxs-lookup"><span data-stu-id="6528e-298">29, 30</span></span>                 | <span data-ttu-id="6528e-299">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-299">x64</span></span> |
| <span data-ttu-id="6528e-300">Debian</span><span class="sxs-lookup"><span data-stu-id="6528e-300">Debian</span></span>                         |  <span data-ttu-id="6528e-301">9</span><span class="sxs-lookup"><span data-stu-id="6528e-301">9</span></span>                      | <span data-ttu-id="6528e-302">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-302">x64, ARM32</span></span> |
| <span data-ttu-id="6528e-303">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6528e-303">Ubuntu</span></span>                         |  <span data-ttu-id="6528e-304">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="6528e-304">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="6528e-305">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-305">x64, ARM32</span></span> |
| <span data-ttu-id="6528e-306">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6528e-306">Linux Mint</span></span>                     |  <span data-ttu-id="6528e-307">17, 18</span><span class="sxs-lookup"><span data-stu-id="6528e-307">17, 18</span></span>                 | <span data-ttu-id="6528e-308">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-308">x64</span></span> |
| <span data-ttu-id="6528e-309">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="6528e-309">openSUSE</span></span>                       |  <span data-ttu-id="6528e-310">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-310">15+</span></span>                    | <span data-ttu-id="6528e-311">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-311">x64</span></span> |
| <span data-ttu-id="6528e-312">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="6528e-312">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="6528e-313">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6528e-313">12 SP2+</span></span>                | <span data-ttu-id="6528e-314">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-314">x64</span></span> |
| <span data-ttu-id="6528e-315">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-315">Alpine Linux</span></span>                   |  <span data-ttu-id="6528e-316">3.8+</span><span class="sxs-lookup"><span data-stu-id="6528e-316">3.8+</span></span>                   | <span data-ttu-id="6528e-317">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-317">x64</span></span> |

<span data-ttu-id="6528e-318">Pour plus d’informations sur .NET Core 2.2 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.2 Versions OS pris en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-318">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="6528e-319">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6528e-319">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="6528e-320">.NET Core 2.1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="6528e-320">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="6528e-321">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="6528e-321">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="6528e-322">.NET Core 2.1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-322">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-323">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-323">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-324">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="6528e-324">OS</span></span>                             |  <span data-ttu-id="6528e-325">Version</span><span class="sxs-lookup"><span data-stu-id="6528e-325">Version</span></span>                |  <span data-ttu-id="6528e-326">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-326">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="6528e-327">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-327">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="6528e-328">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="6528e-328">6, 7, 8</span></span>                | <span data-ttu-id="6528e-329">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-329">x64</span></span> |
| <span data-ttu-id="6528e-330">CentOS</span><span class="sxs-lookup"><span data-stu-id="6528e-330">CentOS</span></span>                         |  <span data-ttu-id="6528e-331">7+</span><span class="sxs-lookup"><span data-stu-id="6528e-331">7+</span></span>                     | <span data-ttu-id="6528e-332">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-332">x64</span></span> |
| <span data-ttu-id="6528e-333">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-333">Oracle Linux</span></span>                   |  <span data-ttu-id="6528e-334">7+</span><span class="sxs-lookup"><span data-stu-id="6528e-334">7+</span></span>                     | <span data-ttu-id="6528e-335">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-335">x64</span></span> |
| <span data-ttu-id="6528e-336">Fedora</span><span class="sxs-lookup"><span data-stu-id="6528e-336">Fedora</span></span>                         |  <span data-ttu-id="6528e-337">29 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-337">29+</span></span>                    | <span data-ttu-id="6528e-338">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-338">x64</span></span> |
| <span data-ttu-id="6528e-339">Debian</span><span class="sxs-lookup"><span data-stu-id="6528e-339">Debian</span></span>                         |  <span data-ttu-id="6528e-340">9</span><span class="sxs-lookup"><span data-stu-id="6528e-340">9</span></span>                      | <span data-ttu-id="6528e-341">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-341">x64, ARM32</span></span> |
| <span data-ttu-id="6528e-342">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6528e-342">Ubuntu</span></span>                         |  <span data-ttu-id="6528e-343">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="6528e-343">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="6528e-344">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="6528e-344">x64, ARM32</span></span> |
| <span data-ttu-id="6528e-345">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="6528e-345">Linux Mint</span></span>                     |  <span data-ttu-id="6528e-346">17+</span><span class="sxs-lookup"><span data-stu-id="6528e-346">17+</span></span>                    | <span data-ttu-id="6528e-347">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-347">x64</span></span> |
| <span data-ttu-id="6528e-348">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="6528e-348">openSUSE</span></span>                       |  <span data-ttu-id="6528e-349">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="6528e-349">15+</span></span>                    | <span data-ttu-id="6528e-350">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-350">x64</span></span> |
| <span data-ttu-id="6528e-351">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="6528e-351">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="6528e-352">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="6528e-352">12 SP2+</span></span>                | <span data-ttu-id="6528e-353">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-353">x64</span></span> |
| <span data-ttu-id="6528e-354">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-354">Alpine Linux</span></span>                   |  <span data-ttu-id="6528e-355">3.8+</span><span class="sxs-lookup"><span data-stu-id="6528e-355">3.8+</span></span>                   | <span data-ttu-id="6528e-356">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-356">x64</span></span> |

<span data-ttu-id="6528e-357">Pour plus d’informations sur .NET Core 2.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-357">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="6528e-358">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="6528e-358">Linux distribution dependencies</span></span>

<span data-ttu-id="6528e-359">En fonction de votre distribution linux, vous devrez peut-être installer des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="6528e-359">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6528e-360">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="6528e-360">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="6528e-361">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="6528e-361">Ubuntu</span></span>

<span data-ttu-id="6528e-362">Les distributions Ubuntu exigent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-362">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="6528e-363">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="6528e-363">liblttng-ust0</span></span>
- <span data-ttu-id="6528e-364">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="6528e-364">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="6528e-365">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="6528e-365">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="6528e-366">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="6528e-366">libssl1.0.0</span></span>
- <span data-ttu-id="6528e-367">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="6528e-367">libkrb5-3</span></span>
- <span data-ttu-id="6528e-368">zlib1g</span><span class="sxs-lookup"><span data-stu-id="6528e-368">zlib1g</span></span>
- <span data-ttu-id="6528e-369">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="6528e-369">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="6528e-370">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="6528e-370">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="6528e-371">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="6528e-371">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="6528e-372">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="6528e-372">libicu60 (for 18.x)</span></span>

<span data-ttu-id="6528e-373">Pour les applications .NET Core qui utilisent l’assemblage *System.Drawing.Common,* vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="6528e-373">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="6528e-374">libgdiplus (version 6.0.1 ou plus tard)</span><span class="sxs-lookup"><span data-stu-id="6528e-374">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="6528e-375">La plupart des versions d’Ubuntu comprennent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="6528e-375">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="6528e-376">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel Mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="6528e-376">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="6528e-377">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="6528e-377">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="6528e-378">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="6528e-378">CentOS and Fedora</span></span>

<span data-ttu-id="6528e-379">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-379">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="6528e-380">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="6528e-380">lttng-ust</span></span>
- <span data-ttu-id="6528e-381">libcurl</span><span class="sxs-lookup"><span data-stu-id="6528e-381">libcurl</span></span>
- <span data-ttu-id="6528e-382">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="6528e-382">openssl-libs</span></span>
- <span data-ttu-id="6528e-383">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="6528e-383">krb5-libs</span></span>
- <span data-ttu-id="6528e-384">libicu</span><span class="sxs-lookup"><span data-stu-id="6528e-384">libicu</span></span>
- <span data-ttu-id="6528e-385">zlib</span><span class="sxs-lookup"><span data-stu-id="6528e-385">zlib</span></span>

<span data-ttu-id="6528e-386">Utilisateurs fedora: Si la version de votre OpenSSL >1,1, vous aurez besoin d’installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="6528e-386">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="6528e-387">Pour .NET Core 2.0, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="6528e-387">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="6528e-388">libunwind</span><span class="sxs-lookup"><span data-stu-id="6528e-388">libunwind</span></span>
- <span data-ttu-id="6528e-389">libuuid</span><span class="sxs-lookup"><span data-stu-id="6528e-389">libuuid</span></span>

<span data-ttu-id="6528e-390">Pour plus d’informations sur les dépendances, voir [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-390">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="6528e-391">Pour les applications .NET Core qui utilisent l’assemblage *System.Drawing.Common,* vous aurez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="6528e-391">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="6528e-392">libgdiplus (version 6.0.1 ou plus tard)</span><span class="sxs-lookup"><span data-stu-id="6528e-392">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="6528e-393">La plupart des versions de CentOS et Fedora comprennent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="6528e-393">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="6528e-394">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel Mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="6528e-394">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="6528e-395">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="6528e-395">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="6528e-396">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="6528e-396">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="6528e-397">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="6528e-397">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="6528e-398">Version de base .NET</span><span class="sxs-lookup"><span data-stu-id="6528e-398">.NET Core Version</span></span> | <span data-ttu-id="6528e-399">macOS</span><span class="sxs-lookup"><span data-stu-id="6528e-399">macOS</span></span>                 | <span data-ttu-id="6528e-400">Architectures</span><span class="sxs-lookup"><span data-stu-id="6528e-400">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="6528e-401">3.1</span><span class="sxs-lookup"><span data-stu-id="6528e-401">3.1</span></span>               | <span data-ttu-id="6528e-402">High Sierra (10.13 ')</span><span class="sxs-lookup"><span data-stu-id="6528e-402">High Sierra (10.13+)</span></span>  | <span data-ttu-id="6528e-403">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-403">x64</span></span> | [<span data-ttu-id="6528e-404">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="6528e-404">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="6528e-405">3.0</span><span class="sxs-lookup"><span data-stu-id="6528e-405">3.0</span></span>               | <span data-ttu-id="6528e-406">High Sierra (10.13 ')</span><span class="sxs-lookup"><span data-stu-id="6528e-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="6528e-407">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-407">x64</span></span> | [<span data-ttu-id="6528e-408">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="6528e-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="6528e-409">2.2</span><span class="sxs-lookup"><span data-stu-id="6528e-409">2.2</span></span>               | <span data-ttu-id="6528e-410">Sierra (10.12 ')</span><span class="sxs-lookup"><span data-stu-id="6528e-410">Sierra (10.12+)</span></span>       | <span data-ttu-id="6528e-411">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-411">x64</span></span> | [<span data-ttu-id="6528e-412">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="6528e-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="6528e-413">2.1</span><span class="sxs-lookup"><span data-stu-id="6528e-413">2.1</span></span>               | <span data-ttu-id="6528e-414">Sierra (10.12 ')</span><span class="sxs-lookup"><span data-stu-id="6528e-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="6528e-415">x64</span><span class="sxs-lookup"><span data-stu-id="6528e-415">x64</span></span> | [<span data-ttu-id="6528e-416">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="6528e-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="6528e-417">À partir de macOS Catalina (version 10.15), tous les logiciels construits après le 1er juin 2019 qui sont distribués avec Developer ID, doivent être notariés.</span><span class="sxs-lookup"><span data-stu-id="6528e-417">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="6528e-418">Cette exigence s’applique au temps d’exécution .NET Core, .NET Core SDK, et au logiciel créé avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6528e-418">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="6528e-419">Les installateurs pour les versions .NET Core (à la fois en runtime et SDK) 3.1, 3.0 et 2.1, ont été notariés depuis le 18 février 2020.</span><span class="sxs-lookup"><span data-stu-id="6528e-419">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="6528e-420">Les versions publiées antérieurement ne sont pas notariées.</span><span class="sxs-lookup"><span data-stu-id="6528e-420">Prior released versions aren't notarized.</span></span> <span data-ttu-id="6528e-421">Si vous exécutez une application non notariée, vous verrez une erreur similaire à l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="6528e-421">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerte de notarisation macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="6528e-423">Pour plus d’informations sur la façon dont la notarisation forcée affecte .NET Core (et vos applications .NET Core), voir [Travailler avec macOS Catalina Notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-423">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="6528e-424">Libgdiplus</span><span class="sxs-lookup"><span data-stu-id="6528e-424">libgdiplus</span></span>

<span data-ttu-id="6528e-425">.NET Applications de base qui utilisent *l’assemblage System.Drawing.Common* nécessitent libgdiplus pour être installé.</span><span class="sxs-lookup"><span data-stu-id="6528e-425">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="6528e-426">Un moyen facile d’obtenir libgdiplus est en utilisant le gestionnaire de paquet [Homebrew ("brew")](https://brew.sh/) pour macOS.</span><span class="sxs-lookup"><span data-stu-id="6528e-426">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="6528e-427">Après l’installation de *l’infusion,* installez libgdiplus en exécutant les commandes suivantes à une invite terminale (commande) :</span><span class="sxs-lookup"><span data-stu-id="6528e-427">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="6528e-428">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6528e-428">Next steps</span></span>

- <span data-ttu-id="6528e-429">Pour développer et exécuter des applications, installez le [SDK core .NET](sdk.md) (inclut le temps d’exécution).</span><span class="sxs-lookup"><span data-stu-id="6528e-429">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="6528e-430">Pour exécuter des applications que d’autres ont créées, installez le [temps d’exécution .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="6528e-430">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
