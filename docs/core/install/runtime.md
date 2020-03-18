---
title: Installer .NET Core runtime sur Windows, Linux et macOS - .NET Core
description: Apprenez à installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399013"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="551af-104">Installer le .NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="551af-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="551af-105">Dans cet article, vous apprendrez à télécharger et installer le temps d’exécution .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="551af-106">Le temps d’exécution .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="551af-107">Installer avec un installateur</span><span class="sxs-lookup"><span data-stu-id="551af-107">Install with an installer</span></span>

<span data-ttu-id="551af-108">Windows a des installateurs autonomes qui peuvent être utilisés pour installer le point d’exécution .NET Core 3.1:</span><span class="sxs-lookup"><span data-stu-id="551af-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="551af-109">x64 (64 bits) DPC</span><span class="sxs-lookup"><span data-stu-id="551af-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="551af-110">x86 (32 bits) CPU</span><span class="sxs-lookup"><span data-stu-id="551af-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="551af-111">Installer avec un installateur</span><span class="sxs-lookup"><span data-stu-id="551af-111">Install with an installer</span></span>

<span data-ttu-id="551af-112">macOS a des installateurs autonomes qui peuvent être utilisés pour installer le temps d’exécution .NET Core 3.1 :</span><span class="sxs-lookup"><span data-stu-id="551af-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="551af-113">x64 (64 bits) DPC</span><span class="sxs-lookup"><span data-stu-id="551af-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a><span data-ttu-id="551af-114">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="551af-114">Download and manually install</span></span>

<span data-ttu-id="551af-115">Comme alternative aux installateurs macOS pour .NET Core, vous pouvez télécharger et installer manuellement l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="551af-115">As an alternative to the macOS installers for .NET Core, you can download and manually install the runtime.</span></span>

<span data-ttu-id="551af-116">Pour installer l’heure d’exécution et activer les commandes CLI .NET Core disponibles au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-116">To install the runtime and enable the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="551af-117">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="551af-117">Then, open a terminal and run the following commands.</span></span> <span data-ttu-id="551af-118">On suppose que le temps d’exécution est téléchargé sur le `~/Downloads/dotnet-runtime.pkg` fichier.</span><span class="sxs-lookup"><span data-stu-id="551af-118">It's assumed the runtime is downloaded to the `~/Downloads/dotnet-runtime.pkg` file.</span></span>

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="551af-119">Installer avec un gestionnaire de paquets</span><span class="sxs-lookup"><span data-stu-id="551af-119">Install with a package manager</span></span>

<span data-ttu-id="551af-120">Vous pouvez installer le .NET Core Runtime avec de nombreux gestionnaires de paquets Linux communs.</span><span class="sxs-lookup"><span data-stu-id="551af-120">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="551af-121">Pour plus d’informations, voir [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="551af-121">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="551af-122">L’installer avec un gestionnaire de paquets n’est pris en charge que sur l’architecture x64.</span><span class="sxs-lookup"><span data-stu-id="551af-122">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="551af-123">Si vous installez le .NET Core Runtime avec une architecture différente, comme ARM, suivez les instructions sur la section [Télécharger et installer manuellement.](#download-and-manually-install)</span><span class="sxs-lookup"><span data-stu-id="551af-123">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="551af-124">Pour plus d’informations sur les architectures qui sont prises en charge, voir [.NET Core dépendances et les exigences](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="551af-124">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="551af-125">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="551af-125">Download and manually install</span></span>

<span data-ttu-id="551af-126">Pour extraire l’heure d’exécution et rendre disponibles les commandes CLI de base .NET au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-126">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="551af-127">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="551af-127">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="551af-128">Les `export` commandes précédentes ne rendent disponibles que les commandes CLI de base .NET pour la session terminale au cours de laquelle il a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="551af-128">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="551af-129">Vous pouvez modifier votre profil shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="551af-129">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="551af-130">Il ya un certain nombre de coquilles différentes disponibles pour Linux et chacun a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="551af-130">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="551af-131">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="551af-131">For example:</span></span>
>
> - <span data-ttu-id="551af-132">**Bash Shell**: *'/.bash_profile*, *'/.bashrc'*</span><span class="sxs-lookup"><span data-stu-id="551af-132">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="551af-133">**Korn Shell**: *'/.kshrc* ou *.profil*</span><span class="sxs-lookup"><span data-stu-id="551af-133">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="551af-134">**Z Shell**: *'/.zshrc* ou *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="551af-134">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="551af-135">Modifiez le fichier source approprié `:$HOME/dotnet` pour votre coque `PATH` et ajoutez à la fin de l’instruction existante.</span><span class="sxs-lookup"><span data-stu-id="551af-135">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="551af-136">Si `PATH` aucune déclaration n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="551af-136">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="551af-137">En outre, ajouter `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="551af-137">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="551af-138">Cette approche vous permet d’installer différentes versions dans des endroits distincts et de choisir explicitement celle à utiliser par quelle application.</span><span class="sxs-lookup"><span data-stu-id="551af-138">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="551af-139">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="551af-139">Install with PowerShell automation</span></span>

<span data-ttu-id="551af-140">Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin de l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="551af-140">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="551af-141">Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="551af-141">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="551af-142">Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="551af-142">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="551af-143">Vous pouvez choisir une version `Channel` spécifique en spécifiant le commutateur.</span><span class="sxs-lookup"><span data-stu-id="551af-143">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="551af-144">Inclure `Runtime` le commutateur pour installer un temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="551af-144">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="551af-145">Sinon, le script installe le [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="551af-145">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="551af-146">La commande ci-dessus installe le temps de course ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="551af-146">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="551af-147">Le temps d’exécution ASP.NET Core comprend également le temps d’exécution standard .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-147">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="551af-148">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="551af-148">Download and manually install</span></span>

<span data-ttu-id="551af-149">Pour extraire l’heure d’exécution et rendre disponibles les commandes CLI de base .NET au terminal, [téléchargez](#all-net-core-downloads) d’abord une version binaire .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-149">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="551af-150">Ensuite, créez un répertoire à installer, par exemple. `%USERPROFILE%\dotnet`</span><span class="sxs-lookup"><span data-stu-id="551af-150">Then, create a directory to install to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="551af-151">Enfin, extraire le fichier zip téléchargé dans ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="551af-151">Finally, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="551af-152">Par défaut, les commandes et les applications CLI de base .NET n’utiliseront pas le noyau .NET installé de cette façon.</span><span class="sxs-lookup"><span data-stu-id="551af-152">By default, .NET Core CLI commands and apps will not use .NET Core installed in this way.</span></span> <span data-ttu-id="551af-153">Vous devez choisir explicitement de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="551af-153">You have to explicitly choose to use it.</span></span> <span data-ttu-id="551af-154">Pour ce faire, modifiez les variables de l’environnement avec lesquelles une application est lancée :</span><span class="sxs-lookup"><span data-stu-id="551af-154">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

<span data-ttu-id="551af-155">Cette approche vous permet d’installer plusieurs versions dans des endroits distincts, puis de choisir explicitement l’emplacement d’installation qu’une application doit utiliser en exécutant l’application avec des variables d’environnement pointant vers cet endroit.</span><span class="sxs-lookup"><span data-stu-id="551af-155">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="551af-156">Même lorsque ces variables d’environnement sont définies, .NET Core tient toujours compte de l’emplacement d’installation global par défaut lors de la sélection du meilleur cadre pour l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="551af-156">Even when these environment variables are set, .NET Core still considers the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="551af-157">La valeur `C:\Program Files\dotnet`par défaut est généralement, que les installateurs utilisent.</span><span class="sxs-lookup"><span data-stu-id="551af-157">The default is typically `C:\Program Files\dotnet`, which the installers use.</span></span> <span data-ttu-id="551af-158">Vous pouvez demander à l’heure d’exécution d’utiliser uniquement l’emplacement d’installation personnalisé en définissant cette variable d’environnement ainsi:</span><span class="sxs-lookup"><span data-stu-id="551af-158">You can instruct the runtime to only use the custom install location by setting this environment variable as well:</span></span>

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="551af-159">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="551af-159">Install with bash automation</span></span>

<span data-ttu-id="551af-160">Les [scripts d’installation de dotnet](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non admin de l’heure d’exécution.</span><span class="sxs-lookup"><span data-stu-id="551af-160">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="551af-161">Vous pouvez télécharger le script à partir de la page de [référence de script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="551af-161">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="551af-162">Le script par défaut à l’installation de la dernière [version de support à long terme (LTS),](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) qui est .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="551af-162">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="551af-163">Vous pouvez choisir une version `current` spécifique en spécifiant le commutateur.</span><span class="sxs-lookup"><span data-stu-id="551af-163">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="551af-164">Inclure `runtime` le commutateur pour installer un temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="551af-164">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="551af-165">Sinon, le script installe le [SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="551af-165">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="551af-166">La commande ci-dessus installe le temps de course ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="551af-166">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="551af-167">Le temps d’exécution ASP.NET Core comprend également le temps d’exécution standard .NET Core.</span><span class="sxs-lookup"><span data-stu-id="551af-167">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="551af-168">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="551af-168">All .NET Core downloads</span></span>

<span data-ttu-id="551af-169">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants:</span><span class="sxs-lookup"><span data-stu-id="551af-169">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="551af-170">.NET Core 3.1 téléchargements</span><span class="sxs-lookup"><span data-stu-id="551af-170">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="551af-171">.NET Core 2.1 téléchargements</span><span class="sxs-lookup"><span data-stu-id="551af-171">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="551af-172">Docker</span><span class="sxs-lookup"><span data-stu-id="551af-172">Docker</span></span>

<span data-ttu-id="551af-173">Les conteneurs fournissent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="551af-173">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="551af-174">Les conteneurs de la même machine ne partagent que le noyau et utilisent les ressources données à votre application.</span><span class="sxs-lookup"><span data-stu-id="551af-174">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="551af-175">.NET Core peut fonctionner dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="551af-175">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="551af-176">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="551af-176">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="551af-177">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="551af-177">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="551af-178">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="551af-178">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="551af-179">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="551af-179">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="551af-180">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur Docker, voir [Introduction à .NET et Docker](../docker/introduction.md) et [Échantillons](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="551af-180">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="551af-181">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="551af-181">Next steps</span></span>

- <span data-ttu-id="551af-182">[Comment vérifier si .NET Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="551af-182">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
