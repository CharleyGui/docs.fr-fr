---
title: Prérequis pour .NET Core sur Linux
description: Versions Linux et dépendances .NET Core prises en charge pour développer, déployer et exécuter des applications .NET Core sur des ordinateurs Linux.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 5fcf931572f3c7e9b9857d2e91e9d620c7aad0bd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969867"
---
# <a name="prerequisites-for-net-core-on-linux"></a><span data-ttu-id="cb722-103">Prérequis pour .NET Core sur Linux</span><span class="sxs-lookup"><span data-stu-id="cb722-103">Prerequisites for .NET Core on Linux</span></span>

<span data-ttu-id="cb722-104">Cet article montre les dépendances nécessaires pour développer des applications .NET Core sur Linux.</span><span class="sxs-lookup"><span data-stu-id="cb722-104">This article shows the dependencies needed to develop .NET Core applications on Linux.</span></span> <span data-ttu-id="cb722-105">Les distributions/versions Linux et les dépendances prises en charge ci-après s’appliquent aux deux façons de développer des applications .NET Core sur Linux :</span><span class="sxs-lookup"><span data-stu-id="cb722-105">The supported Linux distributions/versions, and dependencies that follow apply to the two ways of developing .NET Core apps on Linux:</span></span>

* [<span data-ttu-id="cb722-106">Ligne de commande avec votre éditeur favori</span><span class="sxs-lookup"><span data-stu-id="cb722-106">Command-line with your favorite editor</span></span>](tutorials/using-with-xplat-cli.md)
* [<span data-ttu-id="cb722-107">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="cb722-107">Visual Studio Code</span></span>](https://code.visualstudio.com/)

> [!NOTE]
> <span data-ttu-id="cb722-108">Le kit SDK .NET Core n’est pas nécessaire pour les environnements/serveurs de production.</span><span class="sxs-lookup"><span data-stu-id="cb722-108">The .NET Core SDK package is not required for production servers/environments.</span></span> <span data-ttu-id="cb722-109">Seul le package du Runtime .NET Core est nécessaire pour les applications déployées dans des environnements de production.</span><span class="sxs-lookup"><span data-stu-id="cb722-109">Only the .NET Core runtime package is needed for apps deployed to production environments.</span></span> <span data-ttu-id="cb722-110">Le Runtime .NET Core est déployé avec les applications dans le cadre d’un déploiement autonome, mais il doit être déployé séparément pour des applications déployées qui dépendent du framework.</span><span class="sxs-lookup"><span data-stu-id="cb722-110">The .NET Core runtime is deployed with apps as part of a self-contained deployment, however, it must be deployed for Framework-dependent deployed apps separately.</span></span> <span data-ttu-id="cb722-111">Pour plus d’informations sur les types de déploiements autonomes et dépendants du framework, consultez [Déploiement d’applications .NET Core](./deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb722-111">For more information about framework-dependent and self-contained deployment types, see [.NET Core application deployment](./deploying/index.md).</span></span> <span data-ttu-id="cb722-112">Consultez également [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) pour obtenir des instructions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="cb722-112">Also see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) for specific guidelines.</span></span>

## <a name="supported-linux-versions"></a><span data-ttu-id="cb722-113">Versions de Linux prises en charge</span><span class="sxs-lookup"><span data-stu-id="cb722-113">Supported Linux versions</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cb722-114">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="cb722-114">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="cb722-115">.NET Core 2.x traite Linux comme un seul système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cb722-115">.NET Core 2.x treats Linux as a single operating system.</span></span> <span data-ttu-id="cb722-116">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb722-116">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="cb722-117">Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 2.2](https://dotnet.microsoft.com/download/dotnet-core/2.2) ou [Téléchargements .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="cb722-117">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="cb722-118">.NET Core 2.x est pris en charge sur les distributions/versions Linux suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb722-118">.NET Core 2.x is supported on the following Linux distributions/versions:</span></span>

* <span data-ttu-id="cb722-119">Red Hat Enterprise Linux 7, 6 - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-119">Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="cb722-120">CentOS 7 - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-120">CentOS 7  - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="cb722-121">Oracle Linux 7 - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-121">Oracle Linux 7 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="cb722-122">Fedora 28, 27 - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-122">Fedora 28, 27 - 64-bit (`x86_64` or `amd64`)</span></span> 
* <span data-ttu-id="cb722-123">Debian 9 (64 bits, `amd64`), 8.7 ou une version ultérieure – 64 bits (`arm32` ou `x86_64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-123">Debian 9 (64-bit, `arm32`), 8.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="cb722-124">Ubuntu 18.04 (64 bits, `arm32`), 16.04, 14.04 – 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-124">Ubuntu 18.04 (64-bit, `arm32`), 16.04, 14.04 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="cb722-125">Linux Mint 18, 17 - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-125">Linux Mint 18, 17 - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="cb722-126">openSUSE 42.3 ou version ultérieure - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-126">openSUSE 42.3 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="cb722-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 ou version ultérieure - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-127">SUSE Enterprise Linux (SLES) 12 Service Pack 2 or later - 64-bit (`x86_64` or `amd64`)</span></span>
* <span data-ttu-id="cb722-128">Alpine Linux 3.7 ou version ultérieure - 64 bits (`x86_64` ou `amd64`)</span><span class="sxs-lookup"><span data-stu-id="cb722-128">Alpine Linux 3.7 or later versions - 64-bit (`x86_64` or `amd64`)</span></span>

<span data-ttu-id="cb722-129">Pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 2.1 et .NET Core 2.2, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie, voir [Versions des systèmes d’exploitation prises en charge par .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) et [Versions des systèmes d’exploitation prises en charge par .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span><span class="sxs-lookup"><span data-stu-id="cb722-129">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cb722-130">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cb722-130">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="cb722-131">Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 1.1](https://dotnet.microsoft.com/download/dotnet-core/1.1) ou [Téléchargements .NET Core 1.0](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="cb722-131">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

<span data-ttu-id="cb722-132">.NET Core 1.x est pris en charge sur les distributions/versions Linux 64 bits suivantes (`x86_64` ou `amd64`) :</span><span class="sxs-lookup"><span data-stu-id="cb722-132">.NET Core 1.x is supported on the following Linux 64-bit (`x86_64` or `amd64`) distributions/versions:</span></span>

* <span data-ttu-id="cb722-133">Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="cb722-133">Red Hat Enterprise Linux 7</span></span>
* <span data-ttu-id="cb722-134">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cb722-134">CentOS 7</span></span>
* <span data-ttu-id="cb722-135">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="cb722-135">Oracle Linux 7</span></span>
* <span data-ttu-id="cb722-136">Fedora 28 (.NET Core 1.1), 27</span><span class="sxs-lookup"><span data-stu-id="cb722-136">Fedora 28 (.NET Core 1.1), 27</span></span>
* <span data-ttu-id="cb722-137">Debian 8.2 ou versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="cb722-137">Debian 8.2 or later versions</span></span>
* <span data-ttu-id="cb722-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span><span class="sxs-lookup"><span data-stu-id="cb722-138">Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04</span></span>
* <span data-ttu-id="cb722-139">Linux Mint 17</span><span class="sxs-lookup"><span data-stu-id="cb722-139">Linux Mint 17</span></span>
* <span data-ttu-id="cb722-140">openSUSE 42.3 ou versions ultérieures (.NET Core 1.1)</span><span class="sxs-lookup"><span data-stu-id="cb722-140">openSUSE 42.3 or later versions (.NET Core 1.1)</span></span>

<span data-ttu-id="cb722-141">Consultez [.NET Core 1.x - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation pris en charge par .NET Core 1.x, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="cb722-141">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="cb722-142">.NET Core 3.0 préversion 1</span><span class="sxs-lookup"><span data-stu-id="cb722-142">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="cb722-143">.NET Core 3.0 préversion 1 traite Linux comme un seul système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="cb722-143">.NET Core 3.0 Preview 1 treats Linux as a single operating system.</span></span> <span data-ttu-id="cb722-144">Il existe une seule version Linux (par architecture de puce) pour les distributions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb722-144">There is a single Linux build (per chip architecture) for supported Linux distributions.</span></span> 

<span data-ttu-id="cb722-145">Pour obtenir des liens de téléchargement et plus d’informations, voir [Téléchargements .NET Core 3.0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="cb722-145">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

<span data-ttu-id="cb722-146">NET Core 3.0 préversion 1 est pris en charge sur les distributions/versions Linux suivantes.</span><span class="sxs-lookup"><span data-stu-id="cb722-146">.NET Core 3.0 Preview 1 is supported on the following Linux distributions/versions.</span></span> 

<span data-ttu-id="cb722-147">SE</span><span class="sxs-lookup"><span data-stu-id="cb722-147">OS</span></span>                            | <span data-ttu-id="cb722-148">Version</span><span class="sxs-lookup"><span data-stu-id="cb722-148">Version</span></span>               | <span data-ttu-id="cb722-149">Architectures</span><span class="sxs-lookup"><span data-stu-id="cb722-149">Architectures</span></span>  
------------------------------|-----------------------|----------------
<span data-ttu-id="cb722-150">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="cb722-150">Red Hat Enterprise Linux</span></span>      | <span data-ttu-id="cb722-151">6\.</span><span class="sxs-lookup"><span data-stu-id="cb722-151">6</span></span>                     | <span data-ttu-id="cb722-152">X64</span><span class="sxs-lookup"><span data-stu-id="cb722-152">x64</span></span>
<span data-ttu-id="cb722-153">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="cb722-153">Red Hat Enterprise Linux</span></span><br><span data-ttu-id="cb722-154">CentOS</span><span class="sxs-lookup"><span data-stu-id="cb722-154">CentOS</span></span><br><span data-ttu-id="cb722-155">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="cb722-155">Oracle Linux</span></span>  | <span data-ttu-id="cb722-156">7</span><span class="sxs-lookup"><span data-stu-id="cb722-156">7</span></span>                     | <span data-ttu-id="cb722-157">X64</span><span class="sxs-lookup"><span data-stu-id="cb722-157">x64</span></span>
<span data-ttu-id="cb722-158">Fedora</span><span class="sxs-lookup"><span data-stu-id="cb722-158">Fedora</span></span>                        | <span data-ttu-id="cb722-159">28</span><span class="sxs-lookup"><span data-stu-id="cb722-159">28</span></span>                    | <span data-ttu-id="cb722-160">X64</span><span class="sxs-lookup"><span data-stu-id="cb722-160">x64</span></span>
<span data-ttu-id="cb722-161">Debian</span><span class="sxs-lookup"><span data-stu-id="cb722-161">Debian</span></span>                        | <span data-ttu-id="cb722-162">9</span><span class="sxs-lookup"><span data-stu-id="cb722-162">9</span></span>                     | <span data-ttu-id="cb722-163">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="cb722-163">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="cb722-164">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cb722-164">Ubuntu</span></span>                        | <span data-ttu-id="cb722-165">16.04+, 18.04+</span><span class="sxs-lookup"><span data-stu-id="cb722-165">16.04+, 18.04+</span></span>        | <span data-ttu-id="cb722-166">x64, ARM32\*, ARM64\*</span><span class="sxs-lookup"><span data-stu-id="cb722-166">x64, ARM32\*, ARM64\*</span></span>
<span data-ttu-id="cb722-167">Linux Mint</span><span class="sxs-lookup"><span data-stu-id="cb722-167">Linux Mint</span></span>                    | <span data-ttu-id="cb722-168">18</span><span class="sxs-lookup"><span data-stu-id="cb722-168">18</span></span>                    | <span data-ttu-id="cb722-169">X64</span><span class="sxs-lookup"><span data-stu-id="cb722-169">x64</span></span>
<span data-ttu-id="cb722-170">openSUSE</span><span class="sxs-lookup"><span data-stu-id="cb722-170">openSUSE</span></span>                      | <span data-ttu-id="cb722-171">42.3+</span><span class="sxs-lookup"><span data-stu-id="cb722-171">42.3+</span></span>                 | <span data-ttu-id="cb722-172">X64</span><span class="sxs-lookup"><span data-stu-id="cb722-172">x64</span></span>
<span data-ttu-id="cb722-173">SUSE Enterprise Linux (SLES)</span><span class="sxs-lookup"><span data-stu-id="cb722-173">SUSE Enterprise Linux (SLES)</span></span>  | <span data-ttu-id="cb722-174">12 SP2+</span><span class="sxs-lookup"><span data-stu-id="cb722-174">12 SP2+</span></span>               | <span data-ttu-id="cb722-175">X64</span><span class="sxs-lookup"><span data-stu-id="cb722-175">x64</span></span>
<span data-ttu-id="cb722-176">Alpine Linux</span><span class="sxs-lookup"><span data-stu-id="cb722-176">Alpine Linux</span></span>                  | <span data-ttu-id="cb722-177">3.8+</span><span class="sxs-lookup"><span data-stu-id="cb722-177">3.8+</span></span>                  | <span data-ttu-id="cb722-178">x64, ARM64</span><span class="sxs-lookup"><span data-stu-id="cb722-178">x64, ARM64</span></span>

<span data-ttu-id="cb722-179">\* La prise en charge ARM32 et ARM64 commence par 9 Debian et Ubuntu 16.04.</span><span class="sxs-lookup"><span data-stu-id="cb722-179">\* ARM32 and ARM64 support starts with Debian 9 and Ubuntu 16.04.</span></span> <span data-ttu-id="cb722-180">Les versions antérieures de ces distributions ne sont pas prises en charge sur les processeurs ARM.</span><span class="sxs-lookup"><span data-stu-id="cb722-180">Earlier versions of those distros are not supported on ARM chips.</span></span>

<span data-ttu-id="cb722-181">Consultez [.NET Core 3.0 - Versions des systèmes d’exploitation prises en charge](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) pour obtenir la liste complète des systèmes d’exploitation, distributions et versions pris en charge par .NET Core 3.0, les systèmes d’exploitation non pris en charge et des liens sur la politique concernant le cycle de vie.</span><span class="sxs-lookup"><span data-stu-id="cb722-181">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="cb722-182">Pour plus d’informations sur l’installation de .NET Core 3.0 sur ARM64, consultez [Installation de .NET Core 3.0 sur Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span><span class="sxs-lookup"><span data-stu-id="cb722-182">For more information about how to install .NET Core 3.0 on ARM64, see [Installing .NET Core 3.0 on Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).</span></span>

---

## <a name="linux-distribution-dependencies"></a><span data-ttu-id="cb722-183">Dépendances des distributions Linux</span><span class="sxs-lookup"><span data-stu-id="cb722-183">Linux distribution dependencies</span></span>

<span data-ttu-id="cb722-184">Les éléments suivants sont destinés à être des exemples.</span><span class="sxs-lookup"><span data-stu-id="cb722-184">The following are intended to be examples.</span></span> <span data-ttu-id="cb722-185">Les versions et les noms exacts peuvent varier légèrement sur la distribution Linux que vous choisissez.</span><span class="sxs-lookup"><span data-stu-id="cb722-185">The exact versions and names may vary slightly on your Linux distribution of choice.</span></span>

### <a name="ubuntu"></a><span data-ttu-id="cb722-186">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="cb722-186">Ubuntu</span></span>

<span data-ttu-id="cb722-187">Les distributions Ubuntu nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb722-187">Ubuntu distributions require the following libraries installed:</span></span>

* <span data-ttu-id="cb722-188">liblttng-ust0</span><span class="sxs-lookup"><span data-stu-id="cb722-188">liblttng-ust0</span></span>
* <span data-ttu-id="cb722-189">libcurl3 (pour 14.x et 16.x)</span><span class="sxs-lookup"><span data-stu-id="cb722-189">libcurl3 (for 14.x and 16.x)</span></span>
* <span data-ttu-id="cb722-190">libcurl4 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="cb722-190">libcurl4 (for 18.x)</span></span>
* <span data-ttu-id="cb722-191">libssl1.0.0</span><span class="sxs-lookup"><span data-stu-id="cb722-191">libssl1.0.0</span></span>
* <span data-ttu-id="cb722-192">libkrb5-3</span><span class="sxs-lookup"><span data-stu-id="cb722-192">libkrb5-3</span></span>
* <span data-ttu-id="cb722-193">zlib1g</span><span class="sxs-lookup"><span data-stu-id="cb722-193">zlib1g</span></span>
* <span data-ttu-id="cb722-194">libicu52 (pour 14.x)</span><span class="sxs-lookup"><span data-stu-id="cb722-194">libicu52 (for 14.x)</span></span>
* <span data-ttu-id="cb722-195">libicu55 (pour 16.x)</span><span class="sxs-lookup"><span data-stu-id="cb722-195">libicu55 (for 16.x)</span></span>
* <span data-ttu-id="cb722-196">libicu57 (pour 17.x)</span><span class="sxs-lookup"><span data-stu-id="cb722-196">libicu57 (for 17.x)</span></span>
* <span data-ttu-id="cb722-197">libicu60 (pour 18.x)</span><span class="sxs-lookup"><span data-stu-id="cb722-197">libicu60 (for 18.x)</span></span>

<span data-ttu-id="cb722-198">Pour les versions antérieures à .NET Core 2.1, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="cb722-198">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="cb722-199">libunwind8</span><span class="sxs-lookup"><span data-stu-id="cb722-199">libunwind8</span></span>
* <span data-ttu-id="cb722-200">libuuid1</span><span class="sxs-lookup"><span data-stu-id="cb722-200">libuuid1</span></span>

### <a name="centos-and-fedora"></a><span data-ttu-id="cb722-201">CentOS et Fedora</span><span class="sxs-lookup"><span data-stu-id="cb722-201">CentOS and Fedora</span></span>

<span data-ttu-id="cb722-202">Les distributions CentOS nécessitent l’installation des bibliothèques suivantes :</span><span class="sxs-lookup"><span data-stu-id="cb722-202">CentOS distributions require the following libraries installed:</span></span>

* <span data-ttu-id="cb722-203">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="cb722-203">lttng-ust</span></span>
* <span data-ttu-id="cb722-204">libcurl</span><span class="sxs-lookup"><span data-stu-id="cb722-204">libcurl</span></span>
* <span data-ttu-id="cb722-205">openssl-libs</span><span class="sxs-lookup"><span data-stu-id="cb722-205">openssl-libs</span></span>
* <span data-ttu-id="cb722-206">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="cb722-206">krb5-libs</span></span>
* <span data-ttu-id="cb722-207">libicu</span><span class="sxs-lookup"><span data-stu-id="cb722-207">libicu</span></span>
* <span data-ttu-id="cb722-208">zlib</span><span class="sxs-lookup"><span data-stu-id="cb722-208">zlib</span></span>

<span data-ttu-id="cb722-209">Utilisateurs de Fedora : si votre version d’openssl >= 1.1, vous devez installer compat-openssl10.</span><span class="sxs-lookup"><span data-stu-id="cb722-209">Fedora users: If your openssl's version >= 1.1, you'll need to install compat-openssl10.</span></span>

<span data-ttu-id="cb722-210">Pour les versions antérieures à .NET Core 2.1, les dépendances suivantes sont également requises :</span><span class="sxs-lookup"><span data-stu-id="cb722-210">For versions earlier than .NET Core 2.1, following dependencies are also required:</span></span>

* <span data-ttu-id="cb722-211">libunwind</span><span class="sxs-lookup"><span data-stu-id="cb722-211">libunwind</span></span>
* <span data-ttu-id="cb722-212">libuuid</span><span class="sxs-lookup"><span data-stu-id="cb722-212">libuuid</span></span>

<span data-ttu-id="cb722-213">Pour plus d’informations sur les dépendances, consultez [Applications Linux autonomes](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) (en anglais).</span><span class="sxs-lookup"><span data-stu-id="cb722-213">For more information about the dependencies, see [Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

## <a name="installing-net-core-dependencies-with-the-native-installers"></a><span data-ttu-id="cb722-214">Installation des dépendances .NET Core avec les programmes d’installation natifs</span><span class="sxs-lookup"><span data-stu-id="cb722-214">Installing .NET Core dependencies with the native installers</span></span>

<span data-ttu-id="cb722-215">Les programmes d’installation natifs .NET Core sont disponibles pour les distributions/versions Linux prises en charge.</span><span class="sxs-lookup"><span data-stu-id="cb722-215">.NET Core native installers are available for supported Linux distributions/versions.</span></span> <span data-ttu-id="cb722-216">Les programmes d’installation natifs requièrent un accès administrateur (sudo) au serveur.</span><span class="sxs-lookup"><span data-stu-id="cb722-216">The native installers require admin (sudo) access to the server.</span></span> <span data-ttu-id="cb722-217">L’avantage d’utiliser un programme d’installation natif est que toutes les dépendances natives .NET Core sont installées.</span><span class="sxs-lookup"><span data-stu-id="cb722-217">The advantage of using a native installer is that all of the .NET Core native dependencies are installed.</span></span> <span data-ttu-id="cb722-218">En outre, les programmes d’installation natifs installent le SDK .NET Core à l’échelle du système.</span><span class="sxs-lookup"><span data-stu-id="cb722-218">Native installers also install the .NET Core SDK system-wide.</span></span>

<span data-ttu-id="cb722-219">Sur Linux, il existe deux choix pour le package de programme d’installation :</span><span class="sxs-lookup"><span data-stu-id="cb722-219">On Linux, there are two installer package choices:</span></span>

* <span data-ttu-id="cb722-220">Utilisation d’un gestionnaire de package basé sur le flux, tel qu’apt-get pour Ubuntu, ou yum pour CentOS/RHEL.</span><span class="sxs-lookup"><span data-stu-id="cb722-220">Using a feed-based package manager, such as apt-get for Ubuntu, or yum for CentOS/RHEL.</span></span>
* <span data-ttu-id="cb722-221">Utilisation des packages eux-mêmes, DEB ou RPM</span><span class="sxs-lookup"><span data-stu-id="cb722-221">Using the packages themselves, DEB or RPM.</span></span>

### <a name="scripting-installs-with-the-net-core-installer-script"></a><span data-ttu-id="cb722-222">Script d’installation avec le script de programme d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="cb722-222">Scripting Installs with the .NET Core installer script</span></span>

<span data-ttu-id="cb722-223">Les [scripts dotnet-install](./tools/dotnet-install-script.md) sont utilisés pour effectuer une installation non administrateur de la chaîne d’outils CLI et du runtime partagé.</span><span class="sxs-lookup"><span data-stu-id="cb722-223">The [dotnet-install scripts](./tools/dotnet-install-script.md) are used to perform a non-admin install of the CLI toolchain and the shared runtime.</span></span> <span data-ttu-id="cb722-224">Vous pouvez télécharger le script depuis <https://dot.net/v1/dotnet-install.sh>.</span><span class="sxs-lookup"><span data-stu-id="cb722-224">You can download the script from <https://dot.net/v1/dotnet-install.sh>.</span></span>

<span data-ttu-id="cb722-225">Le script installe par défaut la dernière version de « LTS », qui correspond à .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="cb722-225">The script defaults to installing the latest "LTS" version, which is currently .NET Core 1.1.</span></span> <span data-ttu-id="cb722-226">Pour installer .NET Core 2.1.x, exécutez le script avec le commutateur suivant :</span><span class="sxs-lookup"><span data-stu-id="cb722-226">To install .NET Core 2.1, run the script with the following switch:</span></span>

```console
./dotnet-install.sh -c Current
```

<span data-ttu-id="cb722-227">Le script bash du programme d’installation est utilisé dans les scénarios d’automatisation et dans les installations non administratives.</span><span class="sxs-lookup"><span data-stu-id="cb722-227">The installer bash script is used in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="cb722-228">Comme ce script lit également les commutateurs PowerShell, ces derniers peuvent être utilisés avec le script sur les systèmes Linux/OS X.</span><span class="sxs-lookup"><span data-stu-id="cb722-228">This script also reads PowerShell switches, so they can be used with the script on Linux/OS X systems.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="cb722-229">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="cb722-229">Troubleshoot</span></span>

<span data-ttu-id="cb722-230">En cas de problème avec une installation de .NET Core sur une distribution/version de Linux prise en charge, consultez les rubriques suivantes correspondant à vos distributions/versions installées :</span><span class="sxs-lookup"><span data-stu-id="cb722-230">If you have problems with a .NET Core installation on a supported Linux distribution/version, consult the following topics for your installed distributions/versions:</span></span>

* [<span data-ttu-id="cb722-231">Problèmes connus avec .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="cb722-231">.NET Core 3.0 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [<span data-ttu-id="cb722-232">Problèmes connus avec .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="cb722-232">.NET Core 2.2 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [<span data-ttu-id="cb722-233">Problèmes connus avec .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="cb722-233">.NET Core 2.1 known issues</span></span>](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [<span data-ttu-id="cb722-234">Problèmes connus avec .NET Core 1.1</span><span class="sxs-lookup"><span data-stu-id="cb722-234">.NET Core 1.1 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [<span data-ttu-id="cb722-235">Problèmes connus avec .NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="cb722-235">.NET Core 1.0 known issues</span></span>](https://github.com/dotnet/core/blob/master/release-notes/1.0)
