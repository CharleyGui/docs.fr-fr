---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 395978a2e471260254caf3da8421adf2413c132c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450855"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="a846f-104">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="a846f-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="a846f-105">Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a846f-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="a846f-106">Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a846f-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

<span data-ttu-id="a846f-107">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="a846f-107">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="a846f-108">Téléchargements .NET Core 3,1 Preview 3</span><span class="sxs-lookup"><span data-stu-id="a846f-108">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="a846f-109">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="a846f-109">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="a846f-110">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="a846f-110">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="a846f-111">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="a846f-111">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="install-with-an-installer"></a><span data-ttu-id="a846f-112">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="a846f-112">Install with an installer</span></span>

<span data-ttu-id="a846f-113">Windows et macOS ont tous deux des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="a846f-113">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="a846f-114">UC Windows [x64](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x64-installer) | [UC x32](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="a846f-114">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-windows-x86-installer)</span></span>
- <span data-ttu-id="a846f-115">[processeurs MacOS x64](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="a846f-115">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-runtime-3.0.0-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="a846f-116">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="a846f-116">Install with a package manager</span></span>

<span data-ttu-id="a846f-117">Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="a846f-117">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="a846f-118">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="a846f-118">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="a846f-119">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="a846f-119">Install with PowerShell automation</span></span>

<span data-ttu-id="a846f-120">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="a846f-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="a846f-121">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a846f-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="a846f-122">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="a846f-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="a846f-123">Pour installer la version actuelle de .NET Core (3,0), exécutez le script avec le commutateur suivant :</span><span class="sxs-lookup"><span data-stu-id="a846f-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="a846f-124">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="a846f-124">Install with bash automation</span></span>

<span data-ttu-id="a846f-125">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="a846f-125">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="a846f-126">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a846f-126">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="a846f-127">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="a846f-127">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="a846f-128">Pour installer la version actuelle de .NET Core (3,0), exécutez le script avec le commutateur suivant :</span><span class="sxs-lookup"><span data-stu-id="a846f-128">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="a846f-129">Docker</span><span class="sxs-lookup"><span data-stu-id="a846f-129">Docker</span></span>

<span data-ttu-id="a846f-130">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="a846f-130">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="a846f-131">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="a846f-131">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="a846f-132">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="a846f-132">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="a846f-133">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="a846f-133">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="a846f-134">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="a846f-134">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="a846f-135">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="a846f-135">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="a846f-136">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="a846f-136">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="a846f-137">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="a846f-137">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a846f-138">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="a846f-138">Next steps</span></span>

- <span data-ttu-id="a846f-139">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a846f-139">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
