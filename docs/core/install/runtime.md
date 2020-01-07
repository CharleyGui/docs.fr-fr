---
title: Installer le Runtime .NET Core sur Windows, Linux et macOS-.NET Core
description: Découvrez comment installer .NET Core sur Windows, Linux et macOS. Découvrez les dépendances requises pour exécuter des applications .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a45cb570ccf572a699359598319fd3867fb5e5dd
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340958"
---
# <a name="install-the-net-core-runtime"></a><span data-ttu-id="63e6c-104">Installer le Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="63e6c-104">Install the .NET Core Runtime</span></span>

<span data-ttu-id="63e6c-105">Dans cet article, vous allez apprendre à télécharger et à installer le Runtime .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63e6c-105">In this article, you'll learn how to download and install the .NET Core runtime.</span></span> <span data-ttu-id="63e6c-106">Le Runtime .NET Core est utilisé pour exécuter des applications créées avec .NET Core.</span><span class="sxs-lookup"><span data-stu-id="63e6c-106">The .NET Core runtime is used to run apps created with .NET Core.</span></span>

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a><span data-ttu-id="63e6c-107">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="63e6c-107">Install with an installer</span></span>

<span data-ttu-id="63e6c-108">Windows possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="63e6c-108">Windows has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="63e6c-109">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="63e6c-109">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="63e6c-110">Processeurs x86 (32 bits)</span><span class="sxs-lookup"><span data-stu-id="63e6c-110">x86 (32-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a><span data-ttu-id="63e6c-111">Installer avec un programme d’installation</span><span class="sxs-lookup"><span data-stu-id="63e6c-111">Install with an installer</span></span>

<span data-ttu-id="63e6c-112">macOS possède des programmes d’installation autonomes qui peuvent être utilisés pour installer le Runtime .NET Core 3,1 :</span><span class="sxs-lookup"><span data-stu-id="63e6c-112">macOS has standalone installers that can be used to install the .NET Core 3.1 runtime:</span></span>

- [<span data-ttu-id="63e6c-113">Processeurs x64 (64 bits)</span><span class="sxs-lookup"><span data-stu-id="63e6c-113">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="63e6c-114">Installer avec un gestionnaire de package</span><span class="sxs-lookup"><span data-stu-id="63e6c-114">Install with a package manager</span></span>

<span data-ttu-id="63e6c-115">Vous pouvez installer le Runtime .NET Core avec un grand nombre de gestionnaires de packages Linux courants.</span><span class="sxs-lookup"><span data-stu-id="63e6c-115">You can install the .NET Core Runtime with many of the common Linux package managers.</span></span> <span data-ttu-id="63e6c-116">Pour plus d’informations, consultez [Linux Package Manager-install .net Core](linux-package-managers.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-116">For more information, see [Linux Package Manager - Install .NET Core](linux-package-managers.md).</span></span>

<span data-ttu-id="63e6c-117">Son installation avec un gestionnaire de package est uniquement prise en charge sur l’architecture x64.</span><span class="sxs-lookup"><span data-stu-id="63e6c-117">Installing it with a package manager is only supported on the x64 architecture.</span></span> <span data-ttu-id="63e6c-118">Si vous installez le Runtime .NET Core avec une architecture différente, par exemple ARM, suivez les instructions de la section [téléchargement et installation manuelle](#download-and-manually-install) .</span><span class="sxs-lookup"><span data-stu-id="63e6c-118">If you're installing the .NET Core Runtime with a different architecture, such as ARM, follow the instructions on the [Download and manually install](#download-and-manually-install) section.</span></span> <span data-ttu-id="63e6c-119">Pour plus d’informations sur les architectures prises en charge, consultez [.net Core Dependencies and Requirements](dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-119">For more information about what architectures are supported, see [.NET Core dependencies and requirements](dependencies.md).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="63e6c-120">Télécharger et installer manuellement</span><span class="sxs-lookup"><span data-stu-id="63e6c-120">Download and manually install</span></span>

<span data-ttu-id="63e6c-121">Pour extraire le runtime et rendre les commandes CLI .NET Core disponibles sur le terminal, commencez par [Télécharger](#all-net-core-downloads) une version binaire .net core.</span><span class="sxs-lookup"><span data-stu-id="63e6c-121">To extract the runtime and make the .NET Core CLI commands available at the terminal, first [download](#all-net-core-downloads) a .NET Core binary release.</span></span> <span data-ttu-id="63e6c-122">Ensuite, ouvrez un terminal et exécutez les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="63e6c-122">Then, open a terminal and run the following commands.</span></span>

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="63e6c-123">Les commandes `export` précédentes rendent uniquement les commandes CLI .NET Core disponibles pour la session Terminal dans laquelle elles ont été exécutées.</span><span class="sxs-lookup"><span data-stu-id="63e6c-123">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="63e6c-124">Vous pouvez modifier votre profil de Shell pour ajouter définitivement les commandes.</span><span class="sxs-lookup"><span data-stu-id="63e6c-124">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="63e6c-125">Un certain nombre de shells différents sont disponibles pour Linux et chacun d’eux a un profil différent.</span><span class="sxs-lookup"><span data-stu-id="63e6c-125">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="63e6c-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="63e6c-126">For example:</span></span>
>
> - <span data-ttu-id="63e6c-127">**Interpréteur**de commandes bash : *~/. bash_profile*, *~ fichier/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="63e6c-127">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="63e6c-128">**Shell Korn**: *~/.kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="63e6c-128">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="63e6c-129">**Z Shell**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="63e6c-129">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
> 
> <span data-ttu-id="63e6c-130">Modifiez le fichier source approprié pour votre shell et ajoutez `:$HOME/dotnet` à la fin de l’instruction `PATH` existante.</span><span class="sxs-lookup"><span data-stu-id="63e6c-130">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="63e6c-131">Si aucune instruction `PATH` n’est incluse, ajoutez une nouvelle ligne avec `export PATH=$PATH:$HOME/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="63e6c-131">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="63e6c-132">En outre, ajoutez `export DOTNET_ROOT=$HOME/dotnet` à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="63e6c-132">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="63e6c-133">Installer avec l’automatisation PowerShell</span><span class="sxs-lookup"><span data-stu-id="63e6c-133">Install with PowerShell automation</span></span>

<span data-ttu-id="63e6c-134">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="63e6c-134">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="63e6c-135">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-135">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="63e6c-136">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="63e6c-136">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="63e6c-137">Vous pouvez choisir une version spécifique en spécifiant le commutateur `Channel`.</span><span class="sxs-lookup"><span data-stu-id="63e6c-137">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="63e6c-138">Incluez le commutateur `Runtime` pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="63e6c-138">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="63e6c-139">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-139">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="63e6c-140">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="63e6c-140">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="63e6c-141">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="63e6c-141">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="63e6c-142">Installer avec l’automatisation bash</span><span class="sxs-lookup"><span data-stu-id="63e6c-142">Install with bash automation</span></span>

<span data-ttu-id="63e6c-143">Les [scripts dotnet-install](../tools/dotnet-install-script.md) sont utilisés pour l’automatisation et les installations non administratives du Runtime.</span><span class="sxs-lookup"><span data-stu-id="63e6c-143">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="63e6c-144">Vous pouvez télécharger le script à partir de la [page de référence du script dotnet-install](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-144">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="63e6c-145">Par défaut, le script installe la dernière version de [support à long terme (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , qui est .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="63e6c-145">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="63e6c-146">Vous pouvez choisir une version spécifique en spécifiant le commutateur `current`.</span><span class="sxs-lookup"><span data-stu-id="63e6c-146">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="63e6c-147">Incluez le commutateur `runtime` pour installer un Runtime.</span><span class="sxs-lookup"><span data-stu-id="63e6c-147">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="63e6c-148">Dans le cas contraire, le script installe le [Kit de développement logiciel (SDK)](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-148">Otherwise, the script installs the [SDK](sdk.md).</span></span>

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="63e6c-149">La commande ci-dessus installe le runtime ASP.NET Core pour une compatibilité maximale.</span><span class="sxs-lookup"><span data-stu-id="63e6c-149">The command above installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="63e6c-150">Le runtime ASP.NET Core comprend également le Runtime .NET Core standard.</span><span class="sxs-lookup"><span data-stu-id="63e6c-150">The ASP.NET Core runtime also includes the standard .NET Core runtime.</span></span>

::: zone-end

## <a name="all-net-core-downloads"></a><span data-ttu-id="63e6c-151">Tous les téléchargements .NET Core</span><span class="sxs-lookup"><span data-stu-id="63e6c-151">All .NET Core downloads</span></span>

<span data-ttu-id="63e6c-152">Vous pouvez télécharger et installer .NET Core directement avec l’un des liens suivants :</span><span class="sxs-lookup"><span data-stu-id="63e6c-152">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="63e6c-153">Téléchargements .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="63e6c-153">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="63e6c-154">Téléchargements .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="63e6c-154">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="63e6c-155">Téléchargements .NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="63e6c-155">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="63e6c-156">Téléchargements .NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="63e6c-156">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a><span data-ttu-id="63e6c-157">Docker</span><span class="sxs-lookup"><span data-stu-id="63e6c-157">Docker</span></span>

<span data-ttu-id="63e6c-158">Les conteneurs offrent un moyen léger d’isoler votre application du reste du système hôte.</span><span class="sxs-lookup"><span data-stu-id="63e6c-158">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="63e6c-159">Les conteneurs sur le même ordinateur partagent simplement le noyau et utilisent les ressources fournies à votre application.</span><span class="sxs-lookup"><span data-stu-id="63e6c-159">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="63e6c-160">.NET Core peut s’exécuter dans un conteneur d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="63e6c-160">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="63e6c-161">Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="63e6c-161">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="63e6c-162">Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="63e6c-162">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="63e6c-163">Microsoft fournit des images adaptées à des scénarios particuliers.</span><span class="sxs-lookup"><span data-stu-id="63e6c-163">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="63e6c-164">Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.</span><span class="sxs-lookup"><span data-stu-id="63e6c-164">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="63e6c-165">Pour plus d’informations sur l’utilisation de .NET Core dans un conteneur d’ancrage, consultez [Introduction à .net et à l’ancreur](../docker/introduction.md) et aux [exemples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-165">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="63e6c-166">Étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="63e6c-166">Next steps</span></span>

- <span data-ttu-id="63e6c-167">[Comment vérifier si .net Core est déjà installé](how-to-detect-installed-versions.md).</span><span class="sxs-lookup"><span data-stu-id="63e6c-167">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md).</span></span>
