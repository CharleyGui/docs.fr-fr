---
title: CLI .NET Core
titleSuffix: ''
description: Un aperçu de l’ERC de base de .NET et de ses caractéristiques.
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110839"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="b5e4b-103">Vue d’ensemble de CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="b5e4b-103">.NET Core CLI overview</span></span>

<span data-ttu-id="b5e4b-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b5e4b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="b5e4b-105">L’interface de ligne de commande .NET Core (CLI) est un toolchain multiplateforme pour développer, construire, exécuter et publier des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="b5e4b-106">Le CLI de base .NET est inclus avec le [.NET Core SDK](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b5e4b-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="b5e4b-107">Pour apprendre à installer le .NET Core SDK, voir [Installer le .NET Core SDK](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="b5e4b-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="b5e4b-108">Commandes CLI</span><span class="sxs-lookup"><span data-stu-id="b5e4b-108">CLI commands</span></span>

<span data-ttu-id="b5e4b-109">Les commandes suivantes sont installées par défaut :</span><span class="sxs-lookup"><span data-stu-id="b5e4b-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="b5e4b-110">Commandes de base</span><span class="sxs-lookup"><span data-stu-id="b5e4b-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="b5e4b-111">Commandes de modification de projet</span><span class="sxs-lookup"><span data-stu-id="b5e4b-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="b5e4b-112">Commandes avancées</span><span class="sxs-lookup"><span data-stu-id="b5e4b-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="b5e4b-113">Commandes de gestion d’outils</span><span class="sxs-lookup"><span data-stu-id="b5e4b-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="b5e4b-114">[`tool restore`](global-tools.md#install-a-local-tool)Disponible depuis .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="b5e4b-115">[`tool run`](global-tools.md#invoke-a-local-tool)Disponible depuis .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="b5e4b-116">Les outils sont des applications de console qui sont installées à partir de paquets NuGet et sont invoquées à partir de l’invite de commande.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="b5e4b-117">Vous pouvez écrire des outils vous-même ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="b5e4b-118">Les outils sont également connus sous le nom d’outils globaux, d’outils de chemin à outils et d’outils locaux.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="b5e4b-119">Pour plus d’informations, voir [.NET Core outils aperçu](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b5e4b-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="b5e4b-120">Structure de commande</span><span class="sxs-lookup"><span data-stu-id="b5e4b-120">Command structure</span></span>

<span data-ttu-id="b5e4b-121">La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="b5e4b-122">Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :</span><span class="sxs-lookup"><span data-stu-id="b5e4b-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="b5e4b-123">Pilote</span><span class="sxs-lookup"><span data-stu-id="b5e4b-123">Driver</span></span>

<span data-ttu-id="b5e4b-124">Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="b5e4b-125">Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="b5e4b-126">Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="b5e4b-127">Si vous souhaitez utiliser une version spécifique de .NET Core Runtime, choisissez l’option `--fx-version <VERSION>` (voir la référence [dotnet command](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="b5e4b-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="b5e4b-128">Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="b5e4b-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b5e4b-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="b5e4b-130">D’abord, le pilote détermine la version du kit SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="b5e4b-131">S’il n’y a pas de fichier [global.json,](global-json.md) la dernière version du SDK disponible est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="b5e4b-132">Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="b5e4b-133">Une fois que la version du SDK est déterminée, elle exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="b5e4b-134">Commande</span><span class="sxs-lookup"><span data-stu-id="b5e4b-134">Command</span></span>

<span data-ttu-id="b5e4b-135">La commande exécute une action.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-135">The command performs an action.</span></span> <span data-ttu-id="b5e4b-136">Par exemple, `dotnet build` génère le code.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="b5e4b-137">`dotnet publish` publie le code.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="b5e4b-138">Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="b5e4b-139">Arguments</span><span class="sxs-lookup"><span data-stu-id="b5e4b-139">Arguments</span></span>

<span data-ttu-id="b5e4b-140">Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="b5e4b-141">Par exemple, lorsque `dotnet publish my_app.csproj`vous `my_app.csproj` exécutez, l’argument indique `publish` le projet à publier et est transmis à la commande.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="b5e4b-142">Options</span><span class="sxs-lookup"><span data-stu-id="b5e4b-142">Options</span></span>

<span data-ttu-id="b5e4b-143">Les options que vous passez sur la ligne de commande sont les options de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="b5e4b-144">Par exemple, lorsque `dotnet publish --output /build_output`vous `--output` exécutez, l’option `publish` et sa valeur sont transmises à la commande.</span><span class="sxs-lookup"><span data-stu-id="b5e4b-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5e4b-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5e4b-145">See also</span></span>

- [<span data-ttu-id="b5e4b-146">dotnet/sdk GitHub référentiel</span><span class="sxs-lookup"><span data-stu-id="b5e4b-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="b5e4b-147">Guide d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="b5e4b-147">.NET Core installation guide</span></span>](../install/sdk.md)
