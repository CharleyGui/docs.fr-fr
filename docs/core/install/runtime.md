---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: fbe9b9e12dc53d9ab6570299e03f2b0a8868fb53
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567269"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="8cd34-104">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cd34-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="8cd34-105">Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8cd34-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="8cd34-106">Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8cd34-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows,os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="8cd34-107">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="8cd34-107">Install with an installer</span></span>

<span data-ttu-id="8cd34-108">Windows et macOS ont tous deux des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8cd34-108">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 runtime.</span></span>

- <span data-ttu-id="8cd34-109">[UC Windows x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [processeurs x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="8cd34-109">Windows [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0) | [x86 (32-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="8cd34-110">[UC MacOS x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="8cd34-110">macOS [x64 (64-bit) CPUs](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="8cd34-111">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="8cd34-111">Install with a package manager</span></span>

<span data-ttu-id="8cd34-112">Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="8cd34-112">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="8cd34-113">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="8cd34-113">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="8cd34-114">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="8cd34-114">Install with PowerShell automation</span></span>

<span data-ttu-id="8cd34-115">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="8cd34-115">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="8cd34-116">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="8cd34-116">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8cd34-117">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8cd34-117">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="8cd34-118">Pour installer la version actuelle de .NET Core (3,0), exécutez le script avec le commutateur suivant :</span><span class="sxs-lookup"><span data-stu-id="8cd34-118">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```powershell
dotnet-install.ps1 -Channel 3.0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="8cd34-119">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="8cd34-119">Install with bash automation</span></span>

<span data-ttu-id="8cd34-120">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="8cd34-120">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="8cd34-121">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="8cd34-121">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="8cd34-122">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8cd34-122">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="8cd34-123">Pour installer la version actuelle de .NET Core (3,0), exécutez le script avec le commutateur suivant :</span><span class="sxs-lookup"><span data-stu-id="8cd34-123">To install the current release of .NET Core (3.0), run the script with the following switch:</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="8cd34-124">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="8cd34-124">All .NET Core downloads</span></span>

<span data-ttu-id="8cd34-125">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="8cd34-125">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="8cd34-126">Téléchargements .NET Core 3,1 preview</span><span class="sxs-lookup"><span data-stu-id="8cd34-126">.NET Core 3.1 Preview downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="8cd34-127">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="8cd34-127">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="8cd34-128">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="8cd34-128">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="8cd34-129">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="8cd34-129">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="8cd34-130">Docker</span><span class="sxs-lookup"><span data-stu-id="8cd34-130">Docker</span></span>

<span data-ttu-id="8cd34-131">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="8cd34-131">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="8cd34-132">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="8cd34-132">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="8cd34-133">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="8cd34-133">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="8cd34-134">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="8cd34-134">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="8cd34-135">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="8cd34-135">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="8cd34-136">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="8cd34-136">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="8cd34-137">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="8cd34-137">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="8cd34-138">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="8cd34-138">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8cd34-139">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8cd34-139">Next steps</span></span>

- <span data-ttu-id="8cd34-140">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="8cd34-140">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
