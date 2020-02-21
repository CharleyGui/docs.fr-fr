---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ba50eb222d9eab6bffbb8ebfdf0ecf47951ce719
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543519"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="a2c9c-104">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="a2c9c-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="a2c9c-105">Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="a2c9c-106">Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="a2c9c-107">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="a2c9c-107">Install with an installer</span></span>

<span data-ttu-id="a2c9c-108">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="a2c9c-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="a2c9c-109">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="a2c9c-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="a2c9c-110">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="a2c9c-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="a2c9c-111">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="a2c9c-111">Install with an installer</span></span>

<span data-ttu-id="a2c9c-112">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="a2c9c-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="a2c9c-113">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="a2c9c-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="a2c9c-114">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="a2c9c-114">Install with a package manager</span></span>

<span data-ttu-id="a2c9c-115">Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="a2c9c-116">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="a2c9c-117">Son installation avec un gestionnaire de package est uniquement prise en charge sur l’architecture x64.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="a2c9c-118">Si vous installez le Runtime .NET Core avec une architecture différente, par exemple ARM, suivez les instructions de la section [téléchargement et installation manuelle](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="a2c9c-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="a2c9c-119">Pour plus d’informations sur les architectures prises en charge, consultez [.net Core Dependencies and Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="a2c9c-120">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="a2c9c-120">Download and manually install</span></span>

<span data-ttu-id="a2c9c-121">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="a2c9c-122">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="a2c9c-123">Les commandes `export` précédentes rendent uniquement les commandes CLI .NET Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="a2c9c-124">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="a2c9c-125">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="a2c9c-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="a2c9c-126">For example:</span></span>
>
> - <span data-ttu-id="a2c9c-127">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="a2c9c-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="a2c9c-128">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="a2c9c-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="a2c9c-129">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="a2c9c-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="a2c9c-130">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l’instruction `PATH` existante.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="a2c9c-131">Si aucune instruction `PATH` n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="a2c9c-132">En outre, ajoutez `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="a2c9c-133">Cette approche vous permet d’installer différentes versions dans des emplacements distincts et de choisir explicitement celle qui doit être utilisée par l’application.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-133">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="a2c9c-134">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="a2c9c-134">Install with PowerShell automation</span></span>

<span data-ttu-id="a2c9c-135">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-135">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="a2c9c-136">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-136">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="a2c9c-137">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-137">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="a2c9c-138">Vous pouvez choisir une version spécifique en spécifiant le commutateur `Channel`.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-138">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="a2c9c-139">Incluez le commutateur `Runtime` pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-139">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="a2c9c-140">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-140">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="a2c9c-141">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-141">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="a2c9c-142">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-142">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="a2c9c-143">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="a2c9c-143">Download and manually install</span></span>

<span data-ttu-id="a2c9c-144">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-144">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="a2c9c-145">Ensuite, créez un répertoire dans lequel effectuer l’installation, par exemple `%USERPROFILE%\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-145">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="a2c9c-146">Enfin, extrayez le fichier zip téléchargé dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-146">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="a2c9c-147">Par défaut, les commandes et applications CLI .NET Core n’utilisent pas .NET Core de cette manière.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-147">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="a2c9c-148">Vous devez choisir explicitement de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-148">You have to explicitly choose to use it.</span></span> <span data-ttu-id="a2c9c-149">Pour ce faire, modifiez les variables d’environnement à l’aide desquelles une application est démarrée :</span><span class="sxs-lookup"><span data-stu-id="a2c9c-149">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="a2c9c-150">Cette approche vous permet d’installer plusieurs versions dans des emplacements distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement qui pointent à cet emplacement.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-150">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="a2c9c-151">Même lorsque ces variables d’environnement sont définies, .NET Core prend toujours en compte l’emplacement d’installation globale par défaut lors de la sélection du meilleur Framework pour l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-151">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="a2c9c-152">La valeur par défaut est généralement `C:\Program Files\dotnet`, que les programmes d’installation utilisent.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-152">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="a2c9c-153">Vous pouvez indiquer à l’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant également cette variable d’environnement :</span><span class="sxs-lookup"><span data-stu-id="a2c9c-153">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="a2c9c-154">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="a2c9c-154">Install with bash automation</span></span>

<span data-ttu-id="a2c9c-155">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-155">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="a2c9c-156">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-156">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="a2c9c-157">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-157">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="a2c9c-158">Vous pouvez choisir une version spécifique en spécifiant le commutateur `current`.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-158">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="a2c9c-159">Incluez le commutateur `runtime` pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-159">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="a2c9c-160">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-160">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="a2c9c-161">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-161">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="a2c9c-162">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-162">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="a2c9c-163">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="a2c9c-163">All .NET Core downloads</span></span>

<span data-ttu-id="a2c9c-164">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="a2c9c-164">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="a2c9c-165">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="a2c9c-165">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="a2c9c-166">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="a2c9c-166">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="a2c9c-167">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="a2c9c-167">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="a2c9c-168">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="a2c9c-168">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="a2c9c-169">Docker</span><span class="sxs-lookup"><span data-stu-id="a2c9c-169">Docker</span></span>

<span data-ttu-id="a2c9c-170">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-170">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="a2c9c-171">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-171">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="a2c9c-172">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-172">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="a2c9c-173">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-173">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="a2c9c-174">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-174">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="a2c9c-175">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-175">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="a2c9c-176">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="a2c9c-176">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="a2c9c-177">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-177">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a2c9c-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="a2c9c-178">Next steps</span></span>

- <span data-ttu-id="a2c9c-179">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="a2c9c-179">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
