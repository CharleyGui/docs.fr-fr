---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 8f4a895ad66dea3063a32f785e4c521196266978
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74835727"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="c7b7c-104">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7b7c-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="c7b7c-105">Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="c7b7c-106">Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="c7b7c-107">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="c7b7c-107">Install with an installer</span></span>

<span data-ttu-id="c7b7c-108">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="c7b7c-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="c7b7c-109">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="c7b7c-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="c7b7c-110">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="c7b7c-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="c7b7c-111">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="c7b7c-111">Install with an installer</span></span>

<span data-ttu-id="c7b7c-112">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="c7b7c-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="c7b7c-113">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="c7b7c-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="c7b7c-114">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="c7b7c-114">Install with a package manager</span></span>

<span data-ttu-id="c7b7c-115">Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="c7b7c-116">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="c7b7c-117">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7b7c-117">Install with PowerShell automation</span></span>

<span data-ttu-id="c7b7c-118">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-118">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c7b7c-119">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-119">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c7b7c-120">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-120">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="c7b7c-121">Vous pouvez choisir une version spécifique en spécifiant le commutateur `Channel`.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-121">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="c7b7c-122">Incluez le commutateur `Runtime` pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-122">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="c7b7c-123">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-123">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="c7b7c-124">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-124">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="c7b7c-125">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-125">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="c7b7c-126">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="c7b7c-126">Install with bash automation</span></span>

<span data-ttu-id="c7b7c-127">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-127">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="c7b7c-128">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-128">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="c7b7c-129">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-129">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="c7b7c-130">Vous pouvez choisir une version spécifique en spécifiant le commutateur `current`.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-130">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="c7b7c-131">Incluez le commutateur `runtime` pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-131">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="c7b7c-132">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-132">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="c7b7c-133">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-133">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="c7b7c-134">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-134">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="c7b7c-135">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="c7b7c-135">All .NET Core downloads</span></span>

<span data-ttu-id="c7b7c-136">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="c7b7c-136">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="c7b7c-137">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c7b7c-137">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="c7b7c-138">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="c7b7c-138">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="c7b7c-139">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="c7b7c-139">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="c7b7c-140">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="c7b7c-140">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="c7b7c-141">Docker</span><span class="sxs-lookup"><span data-stu-id="c7b7c-141">Docker</span></span>

<span data-ttu-id="c7b7c-142">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-142">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="c7b7c-143">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-143">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="c7b7c-144">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-144">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="c7b7c-145">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-145">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="c7b7c-146">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-146">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="c7b7c-147">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-147">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="c7b7c-148">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="c7b7c-148">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="c7b7c-149">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-149">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c7b7c-150">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c7b7c-150">Next steps</span></span>

- <span data-ttu-id="c7b7c-151">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="c7b7c-151">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
