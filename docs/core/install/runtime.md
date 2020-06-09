---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: c079e1856cdd370a278efc6fdfb4953059b6f2ba
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596291"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="b849b-104">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="b849b-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="b849b-105">Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b849b-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="b849b-106">Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b849b-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="b849b-107">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="b849b-107">Install with an installer</span></span>

<span data-ttu-id="b849b-108">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="b849b-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="b849b-109">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b849b-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b849b-110">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="b849b-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="b849b-111">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="b849b-111">Install with an installer</span></span>

<span data-ttu-id="b849b-112">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="b849b-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="b849b-113">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="b849b-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="b849b-114">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="b849b-114">Download and manually install</span></span>

<span data-ttu-id="b849b-115">Comme alternative aux programmes d’installation macOS pour .NET Core, vous pouvez télécharger et installer manuellement le Runtime.</span><span class="sxs-lookup"><span data-stu-id="b849b-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="b849b-116">Pour installer le runtime et activer les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire de .net core.</span><span class="sxs-lookup"><span data-stu-id="b849b-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b849b-117">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="b849b-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="b849b-118">Il est supposé que le runtime est téléchargé dans le `~/Downloads/dotnet-runtime.pkg` fichier.</span><span class="sxs-lookup"><span data-stu-id="b849b-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a><span data-ttu-id="b849b-119">Installer sur Linux</span><span class="sxs-lookup"><span data-stu-id="b849b-119">Install on Linux</span></span>

<span data-ttu-id="b849b-120">Cet article sera bientôt supprimé.</span><span class="sxs-lookup"><span data-stu-id="b849b-120">This article will be removed soon.</span></span> <span data-ttu-id="b849b-121">Il est actuellement remplacé par [install .net Core sur Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-121">It is currently replaced by [Install .NET Core on Linux](linux.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="b849b-122">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="b849b-122">Install with PowerShell automation</span></span>

<span data-ttu-id="b849b-123">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="b849b-123">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="b849b-124">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-124">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b849b-125">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="b849b-125">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b849b-126">Vous pouvez choisir une version spécifique en spécifiant le `Channel` commutateur.</span><span class="sxs-lookup"><span data-stu-id="b849b-126">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="b849b-127">Incluez le `Runtime` commutateur pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="b849b-127">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="b849b-128">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-128">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="b849b-129">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="b849b-129">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="b849b-130">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="b849b-130">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="b849b-131">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="b849b-131">Download and manually install</span></span>

<span data-ttu-id="b849b-132">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core.</span><span class="sxs-lookup"><span data-stu-id="b849b-132">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="b849b-133">Ensuite, créez un répertoire dans lequel installer, par exemple `%USERPROFILE%\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="b849b-133">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="b849b-134">Enfin, extrayez le fichier zip téléchargé dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="b849b-134">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="b849b-135">Par défaut, les commandes et les applications CLI .NET Core n’utilisent pas .NET Core de cette manière et vous devez choisir explicitement de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="b849b-135">By default, .NET Core CLI commands and apps won't use .NET Core installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="b849b-136">Pour ce faire, modifiez les variables d’environnement à l’aide desquelles une application est démarrée :</span><span class="sxs-lookup"><span data-stu-id="b849b-136">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="b849b-137">Cette approche vous permet d’installer plusieurs versions dans des emplacements distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement qui pointent à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="b849b-137">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="b849b-138">Même lorsque ces variables d’environnement sont définies, .NET Core prend toujours en compte l’emplacement d’installation globale par défaut lors de la sélection du meilleur Framework pour l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="b849b-138">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="b849b-139">La valeur par défaut est généralement `C:\Program Files\dotnet` , que les programmes d’installation utilisent.</span><span class="sxs-lookup"><span data-stu-id="b849b-139">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="b849b-140">Vous pouvez indiquer à l’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant également cette variable d’environnement :</span><span class="sxs-lookup"><span data-stu-id="b849b-140">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="b849b-141">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="b849b-141">Install with bash automation</span></span>

<span data-ttu-id="b849b-142">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="b849b-142">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="b849b-143">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-143">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b849b-144">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="b849b-144">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="b849b-145">Vous pouvez choisir une version spécifique en spécifiant le `current` commutateur.</span><span class="sxs-lookup"><span data-stu-id="b849b-145">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="b849b-146">Incluez le `runtime` commutateur pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="b849b-146">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="b849b-147">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-147">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="b849b-148">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="b849b-148">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="b849b-149">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="b849b-149">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="b849b-150">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="b849b-150">All .NET Core downloads</span></span>

<span data-ttu-id="b849b-151">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="b849b-151">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="b849b-152">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b849b-152">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b849b-153">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="b849b-153">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="b849b-154">Docker</span><span class="sxs-lookup"><span data-stu-id="b849b-154">Docker</span></span>

<span data-ttu-id="b849b-155">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="b849b-155">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="b849b-156">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="b849b-156">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="b849b-157">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="b849b-157">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="b849b-158">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="b849b-158">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="b849b-159">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="b849b-159">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="b849b-160">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="b849b-160">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="b849b-161">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="b849b-161">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="b849b-162">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-162">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b849b-163">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b849b-163">Next steps</span></span>

- <span data-ttu-id="b849b-164">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="b849b-164">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
