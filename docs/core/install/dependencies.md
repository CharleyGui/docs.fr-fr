---
title: .NET Core SDK et dépendances de temps d’exécution - .NET Core
description: Détaille le système d’exploitation et les conditions préalables à l’architecture CPU pour installer le SDK core .NET et l’heure d’exécution sur Windows, Linux et macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546560"
---
# <a name="net-core-dependencies-and-requirements"></a><span data-ttu-id="cc924-103">.NET Dépendances et exigences de base</span><span class="sxs-lookup"><span data-stu-id="cc924-103">.NET Core dependencies and requirements</span></span>

<span data-ttu-id="cc924-104">Cet article détaille quels systèmes d’exploitation et l’architecture CPU sont pris en charge par .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc924-104">This article details which operating systems and CPU architecture are supported by .NET Core.</span></span>

## <a name="supported-operating-systems"></a><span data-ttu-id="cc924-105">Systèmes d’exploitation pris en charge</span><span class="sxs-lookup"><span data-stu-id="cc924-105">Supported operating systems</span></span>

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[<span data-ttu-id="cc924-106">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="cc924-106">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="cc924-107">Les versions Windows suivantes sont prises en charge avec .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="cc924-107">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-108">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-108">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-109">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-109">OS</span></span>                            | <span data-ttu-id="cc924-110">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-110">Version</span></span>                        | <span data-ttu-id="cc924-111">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-111">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="cc924-112">Client Windows</span><span class="sxs-lookup"><span data-stu-id="cc924-112">Windows Client</span></span>                | <span data-ttu-id="cc924-113">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="cc924-113">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="cc924-114">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-114">x64, x86</span></span>        |
| <span data-ttu-id="cc924-115">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="cc924-115">Windows 10 Client</span></span>             | <span data-ttu-id="cc924-116">Version 1607</span><span class="sxs-lookup"><span data-stu-id="cc924-116">Version 1607+</span></span>                  | <span data-ttu-id="cc924-117">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-117">x64, x86</span></span>        |
| <span data-ttu-id="cc924-118">Windows Server</span><span class="sxs-lookup"><span data-stu-id="cc924-118">Windows Server</span></span>                | <span data-ttu-id="cc924-119">R2 2012</span><span class="sxs-lookup"><span data-stu-id="cc924-119">2012 R2+</span></span>                       | <span data-ttu-id="cc924-120">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-120">x64, x86</span></span>        |
| <span data-ttu-id="cc924-121">Nano Server</span><span class="sxs-lookup"><span data-stu-id="cc924-121">Nano Server</span></span>                   | <span data-ttu-id="cc924-122">Version 1803</span><span class="sxs-lookup"><span data-stu-id="cc924-122">Version 1803+</span></span>                  | <span data-ttu-id="cc924-123">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-123">x64, ARM32</span></span>      |

<span data-ttu-id="cc924-124">Pour plus d’informations sur .NET Core 3.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 3.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-124">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="cc924-125">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cc924-125">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="cc924-126">*.NET Core 3.0 est actuellement hors de support. Pour plus d’informations, voir la [politique de soutien de base .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="cc924-126">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="cc924-127">Les versions Windows suivantes sont prises en charge avec .NET Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="cc924-127">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-128">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-128">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-129">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-129">OS</span></span>                            | <span data-ttu-id="cc924-130">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-130">Version</span></span>                        | <span data-ttu-id="cc924-131">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-131">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="cc924-132">Client Windows</span><span class="sxs-lookup"><span data-stu-id="cc924-132">Windows Client</span></span>                | <span data-ttu-id="cc924-133">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="cc924-133">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="cc924-134">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-134">x64, x86</span></span>        |
| <span data-ttu-id="cc924-135">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="cc924-135">Windows 10 Client</span></span>             | <span data-ttu-id="cc924-136">Version 1607</span><span class="sxs-lookup"><span data-stu-id="cc924-136">Version 1607+</span></span>                  | <span data-ttu-id="cc924-137">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-137">x64, x86</span></span>        |
| <span data-ttu-id="cc924-138">Windows Server</span><span class="sxs-lookup"><span data-stu-id="cc924-138">Windows Server</span></span>                | <span data-ttu-id="cc924-139">R2 2012</span><span class="sxs-lookup"><span data-stu-id="cc924-139">2012 R2+</span></span>                       | <span data-ttu-id="cc924-140">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-140">x64, x86</span></span>        |
| <span data-ttu-id="cc924-141">Nano Server</span><span class="sxs-lookup"><span data-stu-id="cc924-141">Nano Server</span></span>                   | <span data-ttu-id="cc924-142">Version 1803</span><span class="sxs-lookup"><span data-stu-id="cc924-142">Version 1803+</span></span>                  | <span data-ttu-id="cc924-143">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-143">x64, ARM32</span></span>      |

<span data-ttu-id="cc924-144">Pour plus d’informations sur les systèmes d’exploitation supportés .NET Core 3.0, les distributions et la politique du cycle de vie, voir [.NET Core 3.0 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-144">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="cc924-145">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cc924-145">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="cc924-146">*.NET Core 2.2 est actuellement hors de support. Pour plus d’informations, voir la [politique de soutien de base .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="cc924-146">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="cc924-147">Les versions Windows suivantes sont prises en charge avec .NET Core 2.2:</span><span class="sxs-lookup"><span data-stu-id="cc924-147">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-148">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-148">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-149">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-149">OS</span></span>                            | <span data-ttu-id="cc924-150">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-150">Version</span></span>                        | <span data-ttu-id="cc924-151">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-151">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="cc924-152">Client Windows</span><span class="sxs-lookup"><span data-stu-id="cc924-152">Windows Client</span></span>                | <span data-ttu-id="cc924-153">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="cc924-153">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="cc924-154">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-154">x64, x86</span></span>        |
| <span data-ttu-id="cc924-155">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="cc924-155">Windows 10 Client</span></span>             | <span data-ttu-id="cc924-156">Version 1607</span><span class="sxs-lookup"><span data-stu-id="cc924-156">Version 1607+</span></span>                  | <span data-ttu-id="cc924-157">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-157">x64, x86</span></span>        |
| <span data-ttu-id="cc924-158">Windows Server</span><span class="sxs-lookup"><span data-stu-id="cc924-158">Windows Server</span></span>                | <span data-ttu-id="cc924-159">R2 SP1 2008</span><span class="sxs-lookup"><span data-stu-id="cc924-159">2008 R2 SP1+</span></span>                   | <span data-ttu-id="cc924-160">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-160">x64, x86</span></span>        |
| <span data-ttu-id="cc924-161">Nano Server</span><span class="sxs-lookup"><span data-stu-id="cc924-161">Nano Server</span></span>                   | <span data-ttu-id="cc924-162">Version 1803</span><span class="sxs-lookup"><span data-stu-id="cc924-162">Version 1803+</span></span>                   | <span data-ttu-id="cc924-163">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-163">x64, ARM32</span></span>      |

<span data-ttu-id="cc924-164">Pour plus d’informations sur .NET Core 2.2 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.2 Versions OS pris en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-164">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="cc924-165">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cc924-165">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="cc924-166">Les versions Windows suivantes sont prises en charge avec .NET Core 2.1:</span><span class="sxs-lookup"><span data-stu-id="cc924-166">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-167">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-167">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-168">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-168">OS</span></span>                            | <span data-ttu-id="cc924-169">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-169">Version</span></span>                        | <span data-ttu-id="cc924-170">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-170">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="cc924-171">Client Windows</span><span class="sxs-lookup"><span data-stu-id="cc924-171">Windows Client</span></span>                | <span data-ttu-id="cc924-172">7 SP1, 8,1</span><span class="sxs-lookup"><span data-stu-id="cc924-172">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="cc924-173">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-173">x64, x86</span></span>        |
| <span data-ttu-id="cc924-174">Windows 10 Client</span><span class="sxs-lookup"><span data-stu-id="cc924-174">Windows 10 Client</span></span>             | <span data-ttu-id="cc924-175">Version 1607</span><span class="sxs-lookup"><span data-stu-id="cc924-175">Version 1607+</span></span>                  | <span data-ttu-id="cc924-176">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-176">x64, x86</span></span>        |
| <span data-ttu-id="cc924-177">Windows Server</span><span class="sxs-lookup"><span data-stu-id="cc924-177">Windows Server</span></span>                | <span data-ttu-id="cc924-178">R2 SP1 2008</span><span class="sxs-lookup"><span data-stu-id="cc924-178">2008 R2 SP1+</span></span>                   | <span data-ttu-id="cc924-179">x64, x86</span><span class="sxs-lookup"><span data-stu-id="cc924-179">x64, x86</span></span>        |
| <span data-ttu-id="cc924-180">Nano Server</span><span class="sxs-lookup"><span data-stu-id="cc924-180">Nano Server</span></span>                   | <span data-ttu-id="cc924-181">Version 1803</span><span class="sxs-lookup"><span data-stu-id="cc924-181">Version 1803+</span></span>                  | <span data-ttu-id="cc924-182">x64,</span><span class="sxs-lookup"><span data-stu-id="cc924-182">x64,</span></span>            |

<span data-ttu-id="cc924-183">Pour plus d’informations sur .NET Core 2.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-183">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a><span data-ttu-id="cc924-184">Windows 7 / Vista / 8.1 / Serveur 2008 R2</span><span class="sxs-lookup"><span data-stu-id="cc924-184">Windows 7 / Vista / 8.1 / Server 2008 R2</span></span>

<span data-ttu-id="cc924-185">Des dépendances supplémentaires sont nécessaires si vous installez le SDK .NET ou l’heure d’exécution sur les versions Windows suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-185">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="cc924-186">Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="cc924-186">Windows 7 SP1</span></span>
- <span data-ttu-id="cc924-187">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="cc924-187">Windows Vista SP 2</span></span>
- <span data-ttu-id="cc924-188">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cc924-188">Windows 8.1</span></span>
- <span data-ttu-id="cc924-189">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="cc924-189">Windows Server 2008 R2</span></span>
- <span data-ttu-id="cc924-190">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="cc924-190">Windows Server 2012 R2</span></span>

<span data-ttu-id="cc924-191">Installez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="cc924-191">Install the following:</span></span>

- <span data-ttu-id="cc924-192">[Microsoft Visual C 2015 Red redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span><span class="sxs-lookup"><span data-stu-id="cc924-192">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="cc924-193">KB2533623</span><span class="sxs-lookup"><span data-stu-id="cc924-193">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="cc924-194">Les exigences ci-dessus sont également requises si vous tombez sur l’une des erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-194">The requirements above are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="cc924-195">Le programme ne peut pas commencer parce que *api-ms-win-crt-runtime-l1-1-0.dll* est absent de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cc924-195">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="cc924-196">Essayez de réinstaller le programme pour résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="cc924-196">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="cc924-197">\- ou -</span><span class="sxs-lookup"><span data-stu-id="cc924-197">\- or -</span></span>
>
> <span data-ttu-id="cc924-198">La bibliothèque *hostfxr.dll* a été trouvée, mais le chargement de *C:\\\<path_to_app>\\hostfxr.dll* échoué.</span><span class="sxs-lookup"><span data-stu-id="cc924-198">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[<span data-ttu-id="cc924-199">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="cc924-199">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="cc924-200">.NET Core 3.1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="cc924-200">.NET Core 3.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="cc924-201">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cc924-201">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="cc924-202">.NET Core 3.1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-202">.NET Core 3.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-203">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-203">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-204">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-204">OS</span></span>                             | <span data-ttu-id="cc924-205">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-205">Version</span></span>               | <span data-ttu-id="cc924-206">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-206">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="cc924-207">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-207">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="cc924-208">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="cc924-208">6, 7, 8</span></span>               | <span data-ttu-id="cc924-209">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-209">x64</span></span> |
| <span data-ttu-id="cc924-210">CentOS</span><span class="sxs-lookup"><span data-stu-id="cc924-210">CentOS</span></span>                         | <span data-ttu-id="cc924-211">7+</span><span class="sxs-lookup"><span data-stu-id="cc924-211">7+</span></span>                    | <span data-ttu-id="cc924-212">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-212">x64</span></span> |
| <span data-ttu-id="cc924-213">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-213">Oracle Linux</span></span>                   | <span data-ttu-id="cc924-214">7+</span><span class="sxs-lookup"><span data-stu-id="cc924-214">7+</span></span>                    | <span data-ttu-id="cc924-215">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-215">x64</span></span> |
| <span data-ttu-id="cc924-216">Fedora</span><span class="sxs-lookup"><span data-stu-id="cc924-216">Fedora</span></span>                         | <span data-ttu-id="cc924-217">30 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-217">30+</span></span>                   | <span data-ttu-id="cc924-218">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-218">x64</span></span> |
| <span data-ttu-id="cc924-219">Debian</span><span class="sxs-lookup"><span data-stu-id="cc924-219">Debian</span></span>                         | <span data-ttu-id="cc924-220">9+</span><span class="sxs-lookup"><span data-stu-id="cc924-220">9+</span></span>                    | <span data-ttu-id="cc924-221">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="cc924-221">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="cc924-222">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cc924-222">Ubuntu</span></span>                         | <span data-ttu-id="cc924-223">16.04+</span><span class="sxs-lookup"><span data-stu-id="cc924-223">16.04+</span></span>                | <span data-ttu-id="cc924-224">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="cc924-224">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="cc924-225">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="cc924-225">Linux Mint</span></span>                     | <span data-ttu-id="cc924-226">18 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-226">18+</span></span>                   | <span data-ttu-id="cc924-227">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-227">x64</span></span> |
| <span data-ttu-id="cc924-228">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="cc924-228">openSUSE</span></span>                       | <span data-ttu-id="cc924-229">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-229">15+</span></span>                   | <span data-ttu-id="cc924-230">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-230">x64</span></span> |
| <span data-ttu-id="cc924-231">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="cc924-231">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="cc924-232">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="cc924-232">12 SP2+</span></span>               | <span data-ttu-id="cc924-233">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-233">x64</span></span> |
| <span data-ttu-id="cc924-234">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-234">Alpine Linux</span></span>                   | <span data-ttu-id="cc924-235">3.10</span><span class="sxs-lookup"><span data-stu-id="cc924-235">3.10+</span></span>                 | <span data-ttu-id="cc924-236">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="cc924-236">x64, ARM64</span></span> |

<span data-ttu-id="cc924-237">Pour plus d’informations sur .NET Core 3.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 3.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-237">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

<span data-ttu-id="cc924-238">Pour plus d’informations sur la façon d’installer .NET Core 3.1 sur ARM64 (noyau 4.14), voir [Installing .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="cc924-238">For more information about how to install .NET Core 3.1 on ARM64 (kernel 4.14+), see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc924-239">Le support ARM64 nécessite un noyau Linux 4.14 ou plus.</span><span class="sxs-lookup"><span data-stu-id="cc924-239">ARM64 support requires Linux kernel 4.14 or higher.</span></span> <span data-ttu-id="cc924-240">Certaines distributions linux satisfont à cette exigence tandis que d’autres ne le font pas.</span><span class="sxs-lookup"><span data-stu-id="cc924-240">Some linux distributions satisfy this requirement while others don't.</span></span> <span data-ttu-id="cc924-241">Par exemple, Ubuntu 18.04 est pris en charge, mais Ubuntu 16.04 ne le fait pas.</span><span class="sxs-lookup"><span data-stu-id="cc924-241">For example, Ubuntu 18.04 is supported but Ubuntu 16.04 doesn't.</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="cc924-242">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cc924-242">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="cc924-243">*.NET Core 3.0 est actuellement hors de support. Pour plus d’informations, voir la [politique de soutien de base .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="cc924-243">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="cc924-244">.NET Core 3.0 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="cc924-244">.NET Core 3.0 treats Linux as a single operating system.</span></span> <span data-ttu-id="cc924-245">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cc924-245">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="cc924-246">.NET Core 3.0 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-246">.NET Core 3.0 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-247">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-247">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-248">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-248">OS</span></span>                             | <span data-ttu-id="cc924-249">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-249">Version</span></span>               | <span data-ttu-id="cc924-250">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-250">Architectures</span></span>    |
| ------------------------------ | --------------------- | ---------------- |
| <span data-ttu-id="cc924-251">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-251">Red Hat Enterprise Linux</span></span>       | <span data-ttu-id="cc924-252">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="cc924-252">6, 7, 8</span></span>               | <span data-ttu-id="cc924-253">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-253">x64</span></span> |
| <span data-ttu-id="cc924-254">CentOS</span><span class="sxs-lookup"><span data-stu-id="cc924-254">CentOS</span></span>                         | <span data-ttu-id="cc924-255">7+</span><span class="sxs-lookup"><span data-stu-id="cc924-255">7+</span></span>                    | <span data-ttu-id="cc924-256">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-256">x64</span></span> |
| <span data-ttu-id="cc924-257">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-257">Oracle Linux</span></span>                   | <span data-ttu-id="cc924-258">7+</span><span class="sxs-lookup"><span data-stu-id="cc924-258">7+</span></span>                    | <span data-ttu-id="cc924-259">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-259">x64</span></span> |
| <span data-ttu-id="cc924-260">Fedora</span><span class="sxs-lookup"><span data-stu-id="cc924-260">Fedora</span></span>                         | <span data-ttu-id="cc924-261">29 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-261">29+</span></span>                   | <span data-ttu-id="cc924-262">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-262">x64</span></span> |
| <span data-ttu-id="cc924-263">Debian</span><span class="sxs-lookup"><span data-stu-id="cc924-263">Debian</span></span>                         | <span data-ttu-id="cc924-264">9+</span><span class="sxs-lookup"><span data-stu-id="cc924-264">9+</span></span>                    | <span data-ttu-id="cc924-265">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="cc924-265">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="cc924-266">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cc924-266">Ubuntu</span></span>                         | <span data-ttu-id="cc924-267">16.04+</span><span class="sxs-lookup"><span data-stu-id="cc924-267">16.04+</span></span>                | <span data-ttu-id="cc924-268">x64, ARM32, ARM64</span><span class="sxs-lookup"><span data-stu-id="cc924-268">x64, ARM32, ARM64</span></span> |
| <span data-ttu-id="cc924-269">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="cc924-269">Linux Mint</span></span>                     | <span data-ttu-id="cc924-270">18 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-270">18+</span></span>                   | <span data-ttu-id="cc924-271">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-271">x64</span></span> |
| <span data-ttu-id="cc924-272">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="cc924-272">openSUSE</span></span>                       | <span data-ttu-id="cc924-273">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-273">15+</span></span>                   | <span data-ttu-id="cc924-274">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-274">x64</span></span> |
| <span data-ttu-id="cc924-275">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="cc924-275">SUSE Enterprise Linux (SLES)</span></span>   | <span data-ttu-id="cc924-276">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="cc924-276">12 SP2+</span></span>               | <span data-ttu-id="cc924-277">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-277">x64</span></span> |
| <span data-ttu-id="cc924-278">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-278">Alpine Linux</span></span>                   | <span data-ttu-id="cc924-279">3.8+</span><span class="sxs-lookup"><span data-stu-id="cc924-279">3.8+</span></span>                  | <span data-ttu-id="cc924-280">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="cc924-280">x64, ARM64</span></span> |

<span data-ttu-id="cc924-281">Pour plus d’informations sur les systèmes d’exploitation supportés .NET Core 3.0, les distributions et la politique du cycle de vie, voir [.NET Core 3.0 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-281">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

<span data-ttu-id="cc924-282">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="cc924-282">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="cc924-283">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cc924-283">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="cc924-284">*.NET Core 2.2 est actuellement hors de support. Pour plus d’informations, voir la [politique de soutien de base .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span><span class="sxs-lookup"><span data-stu-id="cc924-284">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="cc924-285">.NET Core 2.2 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="cc924-285">.NET Core 2.2 treats Linux as a single operating system.</span></span> <span data-ttu-id="cc924-286">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cc924-286">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="cc924-287">.NET Core 2.2 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-287">.NET Core 2.2 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-288">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-288">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-289">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-289">OS</span></span>                             |  <span data-ttu-id="cc924-290">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-290">Version</span></span>                |  <span data-ttu-id="cc924-291">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-291">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="cc924-292">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-292">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="cc924-293">6, 7</span><span class="sxs-lookup"><span data-stu-id="cc924-293">6, 7</span></span>                   | <span data-ttu-id="cc924-294">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-294">x64</span></span> |
| <span data-ttu-id="cc924-295">CentOS</span><span class="sxs-lookup"><span data-stu-id="cc924-295">CentOS</span></span>                         |  <span data-ttu-id="cc924-296">7</span><span class="sxs-lookup"><span data-stu-id="cc924-296">7</span></span>                      | <span data-ttu-id="cc924-297">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-297">x64</span></span> |
| <span data-ttu-id="cc924-298">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-298">Oracle Linux</span></span>                   |  <span data-ttu-id="cc924-299">7</span><span class="sxs-lookup"><span data-stu-id="cc924-299">7</span></span>                      | <span data-ttu-id="cc924-300">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-300">x64</span></span> |
| <span data-ttu-id="cc924-301">Fedora</span><span class="sxs-lookup"><span data-stu-id="cc924-301">Fedora</span></span>                         |  <span data-ttu-id="cc924-302">29, 30</span><span class="sxs-lookup"><span data-stu-id="cc924-302">29, 30</span></span>                 | <span data-ttu-id="cc924-303">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-303">x64</span></span> |
| <span data-ttu-id="cc924-304">Debian</span><span class="sxs-lookup"><span data-stu-id="cc924-304">Debian</span></span>                         |  <span data-ttu-id="cc924-305">9</span><span class="sxs-lookup"><span data-stu-id="cc924-305">9</span></span>                      | <span data-ttu-id="cc924-306">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-306">x64, ARM32</span></span> |
| <span data-ttu-id="cc924-307">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cc924-307">Ubuntu</span></span>                         |  <span data-ttu-id="cc924-308">16.04, 18.04, 18.10</span><span class="sxs-lookup"><span data-stu-id="cc924-308">16.04, 18.04, 18.10</span></span>    | <span data-ttu-id="cc924-309">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-309">x64, ARM32</span></span> |
| <span data-ttu-id="cc924-310">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="cc924-310">Linux Mint</span></span>                     |  <span data-ttu-id="cc924-311">17, 18</span><span class="sxs-lookup"><span data-stu-id="cc924-311">17, 18</span></span>                 | <span data-ttu-id="cc924-312">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-312">x64</span></span> |
| <span data-ttu-id="cc924-313">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="cc924-313">openSUSE</span></span>                       |  <span data-ttu-id="cc924-314">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-314">15+</span></span>                    | <span data-ttu-id="cc924-315">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-315">x64</span></span> |
| <span data-ttu-id="cc924-316">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="cc924-316">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="cc924-317">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="cc924-317">12 SP2+</span></span>                | <span data-ttu-id="cc924-318">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-318">x64</span></span> |
| <span data-ttu-id="cc924-319">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-319">Alpine Linux</span></span>                   |  <span data-ttu-id="cc924-320">3.8+</span><span class="sxs-lookup"><span data-stu-id="cc924-320">3.8+</span></span>                   | <span data-ttu-id="cc924-321">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-321">x64</span></span> |

<span data-ttu-id="cc924-322">Pour plus d’informations sur .NET Core 2.2 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.2 Versions OS pris en charge](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-322">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="cc924-323">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cc924-323">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="cc924-324">.NET Core 2.1 traite Linux comme un système d’exploitation unique.</span><span class="sxs-lookup"><span data-stu-id="cc924-324">.NET Core 2.1 treats Linux as a single operating system.</span></span> <span data-ttu-id="cc924-325">Il existe une seule build Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cc924-325">There's a single Linux build (per chip architecture) for supported Linux distributions.</span></span>

<span data-ttu-id="cc924-326">.NET Core 2.1 est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-326">.NET Core 2.1 is supported on the following Linux distributions/versions:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-327">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-327">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-328">Système d''exploitation</span><span class="sxs-lookup"><span data-stu-id="cc924-328">OS</span></span>                             |  <span data-ttu-id="cc924-329">Version</span><span class="sxs-lookup"><span data-stu-id="cc924-329">Version</span></span>                |  <span data-ttu-id="cc924-330">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-330">Architectures</span></span>   |
| ------------------------------ | ----------------------- | ---------------- |
| <span data-ttu-id="cc924-331">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-331">Red Hat Enterprise Linux</span></span>       |  <span data-ttu-id="cc924-332">6, 7, 8</span><span class="sxs-lookup"><span data-stu-id="cc924-332">6, 7, 8</span></span>                | <span data-ttu-id="cc924-333">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-333">x64</span></span> |
| <span data-ttu-id="cc924-334">CentOS</span><span class="sxs-lookup"><span data-stu-id="cc924-334">CentOS</span></span>                         |  <span data-ttu-id="cc924-335">7+</span><span class="sxs-lookup"><span data-stu-id="cc924-335">7+</span></span>                     | <span data-ttu-id="cc924-336">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-336">x64</span></span> |
| <span data-ttu-id="cc924-337">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-337">Oracle Linux</span></span>                   |  <span data-ttu-id="cc924-338">7+</span><span class="sxs-lookup"><span data-stu-id="cc924-338">7+</span></span>                     | <span data-ttu-id="cc924-339">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-339">x64</span></span> |
| <span data-ttu-id="cc924-340">Fedora</span><span class="sxs-lookup"><span data-stu-id="cc924-340">Fedora</span></span>                         |  <span data-ttu-id="cc924-341">30 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-341">30+</span></span>                    | <span data-ttu-id="cc924-342">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-342">x64</span></span> |
| <span data-ttu-id="cc924-343">Debian</span><span class="sxs-lookup"><span data-stu-id="cc924-343">Debian</span></span>                         |  <span data-ttu-id="cc924-344">9</span><span class="sxs-lookup"><span data-stu-id="cc924-344">9</span></span>                      | <span data-ttu-id="cc924-345">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-345">x64, ARM32</span></span> |
| <span data-ttu-id="cc924-346">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cc924-346">Ubuntu</span></span>                         |  <span data-ttu-id="cc924-347">16.04, 18.04, 19.04, 19.10</span><span class="sxs-lookup"><span data-stu-id="cc924-347">16.04, 18.04, 19.04, 19.10</span></span>    | <span data-ttu-id="cc924-348">x64, ARM32</span><span class="sxs-lookup"><span data-stu-id="cc924-348">x64, ARM32</span></span> |
| <span data-ttu-id="cc924-349">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="cc924-349">Linux Mint</span></span>                     |  <span data-ttu-id="cc924-350">17+</span><span class="sxs-lookup"><span data-stu-id="cc924-350">17+</span></span>                    | <span data-ttu-id="cc924-351">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-351">x64</span></span> |
| <span data-ttu-id="cc924-352">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="cc924-352">openSUSE</span></span>                       |  <span data-ttu-id="cc924-353">15 ans et plus</span><span class="sxs-lookup"><span data-stu-id="cc924-353">15+</span></span>                    | <span data-ttu-id="cc924-354">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-354">x64</span></span> |
| <span data-ttu-id="cc924-355">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="cc924-355">SUSE Enterprise Linux (SLES)</span></span>   |  <span data-ttu-id="cc924-356">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="cc924-356">12 SP2+</span></span>                | <span data-ttu-id="cc924-357">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-357">x64</span></span> |
| <span data-ttu-id="cc924-358">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-358">Alpine Linux</span></span>                   |  <span data-ttu-id="cc924-359">3.8+</span><span class="sxs-lookup"><span data-stu-id="cc924-359">3.8+</span></span>                   | <span data-ttu-id="cc924-360">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-360">x64</span></span> |

<span data-ttu-id="cc924-361">Pour plus d’informations sur .NET Core 2.1 systèmes d’exploitation pris en charge, les distributions et la politique du cycle de vie, voir [.NET Core 2.1 Versions OS prises en charge](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-361">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="cc924-362">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="cc924-362">Linux distribution dependencies</span></span>

<span data-ttu-id="cc924-363">En fonction de votre distribution linux, vous devrez peut-être installer des dépendances supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="cc924-363">Based on your linux distribution, you may need to install additional dependencies.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc924-364">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="cc924-364">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="cc924-365">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cc924-365">Ubuntu</span></span>

<span data-ttu-id="cc924-366">Les distributions Ubuntu exigent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-366">Ubuntu distributions require the following libraries to be installed:</span></span>

- <span data-ttu-id="cc924-367">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="cc924-367">liblttng-ust0</span></span>
- <span data-ttu-id="cc924-368">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="cc924-368">libcurl3 (for 14.x and 16.x)</span></span>
- <span data-ttu-id="cc924-369">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="cc924-369">libcurl4 (for 18.x)</span></span>
- <span data-ttu-id="cc924-370">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="cc924-370">libssl1.0.0</span></span>
- <span data-ttu-id="cc924-371">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="cc924-371">libkrb5-3</span></span>
- <span data-ttu-id="cc924-372">zlib1g</span><span class="sxs-lookup"><span data-stu-id="cc924-372">zlib1g</span></span>
- <span data-ttu-id="cc924-373">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="cc924-373">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="cc924-374">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="cc924-374">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="cc924-375">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="cc924-375">libicu57 (for 17.x)</span></span>
- <span data-ttu-id="cc924-376">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="cc924-376">libicu60 (for 18.x)</span></span>

<span data-ttu-id="cc924-377">Pour les applications .NET Core qui utilisent l’assemblage *System.Drawing.Common,* vous avez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="cc924-377">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="cc924-378">libgdiplus (version 6.0.1 ou plus tard)</span><span class="sxs-lookup"><span data-stu-id="cc924-378">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="cc924-379">La plupart des versions d’Ubuntu comprennent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="cc924-379">Most versions of Ubuntu include an earlier version of libgdiplus.</span></span> <span data-ttu-id="cc924-380">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel Mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="cc924-380">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="cc924-381">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="cc924-381">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="cc924-382">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="cc924-382">CentOS and Fedora</span></span>

<span data-ttu-id="cc924-383">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-383">CentOS distributions require the following libraries installed:</span></span>

- <span data-ttu-id="cc924-384">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="cc924-384">lttng-ust</span></span>
- <span data-ttu-id="cc924-385">libcurl</span><span class="sxs-lookup"><span data-stu-id="cc924-385">libcurl</span></span>
- <span data-ttu-id="cc924-386">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="cc924-386">openssl-libs</span></span>
- <span data-ttu-id="cc924-387">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="cc924-387">krb5-libs</span></span>
- <span data-ttu-id="cc924-388">libicu</span><span class="sxs-lookup"><span data-stu-id="cc924-388">libicu</span></span>
- <span data-ttu-id="cc924-389">zlib</span><span class="sxs-lookup"><span data-stu-id="cc924-389">zlib</span></span>

<span data-ttu-id="cc924-390">Utilisateurs fedora: Si la version de votre OpenSSL >1,1, vous aurez besoin d’installer **compat-openssl10**.</span><span class="sxs-lookup"><span data-stu-id="cc924-390">Fedora users: If your OpenSSL's version >= 1.1, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="cc924-391">Pour .NET Core 2.0, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="cc924-391">For .NET Core 2.0, the following dependencies are also required:</span></span>

- <span data-ttu-id="cc924-392">libunwind</span><span class="sxs-lookup"><span data-stu-id="cc924-392">libunwind</span></span>
- <span data-ttu-id="cc924-393">libuuid</span><span class="sxs-lookup"><span data-stu-id="cc924-393">libuuid</span></span>

<span data-ttu-id="cc924-394">Pour plus d’informations sur les dépendances, voir [applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-394">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="cc924-395">Pour les applications .NET Core qui utilisent l’assemblage *System.Drawing.Common,* vous aurez également besoin de la dépendance suivante :</span><span class="sxs-lookup"><span data-stu-id="cc924-395">For .NET Core apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- <span data-ttu-id="cc924-396">libgdiplus (version 6.0.1 ou plus tard)</span><span class="sxs-lookup"><span data-stu-id="cc924-396">libgdiplus (version 6.0.1 or later)</span></span>

> [!WARNING]
> <span data-ttu-id="cc924-397">La plupart des versions de CentOS et Fedora comprennent une version antérieure de libgdiplus.</span><span class="sxs-lookup"><span data-stu-id="cc924-397">Most versions of CentOS and Fedora include an earlier version of libgdiplus.</span></span> <span data-ttu-id="cc924-398">Vous pouvez installer une version récente de libgdiplus en ajoutant le référentiel Mono à votre système.</span><span class="sxs-lookup"><span data-stu-id="cc924-398">You can install a recent version of libgdiplus by adding the Mono repository to your system.</span></span> <span data-ttu-id="cc924-399">Pour plus d’informations, consultez <https://www.mono-project.com/download/stable/>.</span><span class="sxs-lookup"><span data-stu-id="cc924-399">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

::: zone-end

::: zone pivot="os-macos"

<span data-ttu-id="cc924-400">.NET Core est pris en charge sur les versions macOS suivantes :</span><span class="sxs-lookup"><span data-stu-id="cc924-400">.NET Core is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="cc924-401">Un `+` symbole représente la version minimale.</span><span class="sxs-lookup"><span data-stu-id="cc924-401">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="cc924-402">Version de base .NET</span><span class="sxs-lookup"><span data-stu-id="cc924-402">.NET Core Version</span></span> | <span data-ttu-id="cc924-403">macOS</span><span class="sxs-lookup"><span data-stu-id="cc924-403">macOS</span></span>                 | <span data-ttu-id="cc924-404">Architectures</span><span class="sxs-lookup"><span data-stu-id="cc924-404">Architectures</span></span> |     |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="cc924-405">3.1</span><span class="sxs-lookup"><span data-stu-id="cc924-405">3.1</span></span>               | <span data-ttu-id="cc924-406">High Sierra (10.13 ')</span><span class="sxs-lookup"><span data-stu-id="cc924-406">High Sierra (10.13+)</span></span>  | <span data-ttu-id="cc924-407">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-407">x64</span></span> | [<span data-ttu-id="cc924-408">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="cc924-408">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="cc924-409">3.0</span><span class="sxs-lookup"><span data-stu-id="cc924-409">3.0</span></span>               | <span data-ttu-id="cc924-410">High Sierra (10.13 ')</span><span class="sxs-lookup"><span data-stu-id="cc924-410">High Sierra (10.13+)</span></span>  | <span data-ttu-id="cc924-411">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-411">x64</span></span> | [<span data-ttu-id="cc924-412">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="cc924-412">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="cc924-413">2.2</span><span class="sxs-lookup"><span data-stu-id="cc924-413">2.2</span></span>               | <span data-ttu-id="cc924-414">Sierra (10.12 ')</span><span class="sxs-lookup"><span data-stu-id="cc924-414">Sierra (10.12+)</span></span>       | <span data-ttu-id="cc924-415">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-415">x64</span></span> | [<span data-ttu-id="cc924-416">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="cc924-416">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="cc924-417">2.1</span><span class="sxs-lookup"><span data-stu-id="cc924-417">2.1</span></span>               | <span data-ttu-id="cc924-418">Sierra (10.12 ')</span><span class="sxs-lookup"><span data-stu-id="cc924-418">Sierra (10.12+)</span></span>       | <span data-ttu-id="cc924-419">x64</span><span class="sxs-lookup"><span data-stu-id="cc924-419">x64</span></span> | [<span data-ttu-id="cc924-420">Plus d’informations</span><span class="sxs-lookup"><span data-stu-id="cc924-420">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="cc924-421">À partir de macOS Catalina (version 10.15), tous les logiciels construits après le 1er juin 2019 qui sont distribués avec Developer ID, doivent être notariés.</span><span class="sxs-lookup"><span data-stu-id="cc924-421">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="cc924-422">Cette exigence s’applique au temps d’exécution .NET Core, .NET Core SDK, et au logiciel créé avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc924-422">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span>

<span data-ttu-id="cc924-423">Les installateurs pour les versions .NET Core (à la fois en runtime et SDK) 3.1, 3.0 et 2.1, ont été notariés depuis le 18 février 2020.</span><span class="sxs-lookup"><span data-stu-id="cc924-423">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="cc924-424">Les versions publiées antérieurement ne sont pas notariées.</span><span class="sxs-lookup"><span data-stu-id="cc924-424">Prior released versions aren't notarized.</span></span> <span data-ttu-id="cc924-425">Si vous exécutez une application non notariée, vous verrez une erreur similaire à l’image suivante :</span><span class="sxs-lookup"><span data-stu-id="cc924-425">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![alerte de notarisation macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="cc924-427">Pour plus d’informations sur la façon dont la notarisation forcée affecte .NET Core (et vos applications .NET Core), voir [Travailler avec macOS Catalina Notarization](macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-427">For more information about how enforced-notarization affects .NET Core (and your .NET Core apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="cc924-428">Libgdiplus</span><span class="sxs-lookup"><span data-stu-id="cc924-428">libgdiplus</span></span>

<span data-ttu-id="cc924-429">.NET Applications de base qui utilisent *l’assemblage System.Drawing.Common* nécessitent libgdiplus pour être installé.</span><span class="sxs-lookup"><span data-stu-id="cc924-429">.NET Core applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="cc924-430">Un moyen facile d’obtenir libgdiplus est en utilisant le gestionnaire de paquet [Homebrew ("brew")](https://brew.sh/) pour macOS.</span><span class="sxs-lookup"><span data-stu-id="cc924-430">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="cc924-431">Après l’installation de *l’infusion,* installez libgdiplus en exécutant les commandes suivantes à une invite terminale (commande) :</span><span class="sxs-lookup"><span data-stu-id="cc924-431">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a><span data-ttu-id="cc924-432">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="cc924-432">Next steps</span></span>

- <span data-ttu-id="cc924-433">Pour développer et exécuter des applications, installez le [SDK core .NET](sdk.md) (inclut le temps d’exécution).</span><span class="sxs-lookup"><span data-stu-id="cc924-433">To develop and run apps, install the [.NET Core SDK](sdk.md) (includes the runtime).</span></span>
- <span data-ttu-id="cc924-434">Pour exécuter des applications que d’autres ont créées, installez le [temps d’exécution .NET Core](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="cc924-434">To run apps others have created, install the [.NET Core runtime](runtime.md).</span></span>
