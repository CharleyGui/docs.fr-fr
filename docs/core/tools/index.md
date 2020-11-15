---
title: CLI .NET
titleSuffix: ''
description: Vue d’ensemble de l’interface de commande .NET et de ses fonctionnalités.
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633854"
---
# <a name="net-cli-overview"></a><span data-ttu-id="6157a-103">Vue d’ensemble de l’interface CLI .NET</span><span class="sxs-lookup"><span data-stu-id="6157a-103">.NET CLI overview</span></span>

<span data-ttu-id="6157a-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6157a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="6157a-105">L’interface de ligne de commande (CLI) .NET est un chaîne d’outils multiplateforme pour le développement, la génération, l’exécution et la publication d’applications .NET.</span><span class="sxs-lookup"><span data-stu-id="6157a-105">The .NET command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span>

<span data-ttu-id="6157a-106">L’interface CLI .NET est incluse avec le [Kit de développement logiciel (SDK) .net](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="6157a-106">The .NET CLI is included with the [.NET SDK](../sdk.md).</span></span> <span data-ttu-id="6157a-107">Pour savoir comment installer le kit de développement logiciel (SDK) .NET, consultez [installer .net Core](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="6157a-107">To learn how to install the .NET SDK, see [Install .NET Core](../install/windows.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="6157a-108">Commandes CLI</span><span class="sxs-lookup"><span data-stu-id="6157a-108">CLI commands</span></span>

<span data-ttu-id="6157a-109">Les commandes suivantes sont installées par défaut :</span><span class="sxs-lookup"><span data-stu-id="6157a-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="6157a-110">Commandes de base</span><span class="sxs-lookup"><span data-stu-id="6157a-110">Basic commands</span></span>

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

### <a name="project-modification-commands"></a><span data-ttu-id="6157a-111">Commandes de modification de projet</span><span class="sxs-lookup"><span data-stu-id="6157a-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="6157a-112">Commandes avancées</span><span class="sxs-lookup"><span data-stu-id="6157a-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="6157a-113">Commandes de gestion des outils</span><span class="sxs-lookup"><span data-stu-id="6157a-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="6157a-114">[`tool restore`](global-tools.md#install-a-local-tool) Disponible depuis kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6157a-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="6157a-115">[`tool run`](global-tools.md#invoke-a-local-tool) Disponible depuis kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6157a-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="6157a-116">Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6157a-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="6157a-117">Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="6157a-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="6157a-118">Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux.</span><span class="sxs-lookup"><span data-stu-id="6157a-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="6157a-119">Pour plus d’informations, consultez [vue d’ensemble des outils .net](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6157a-119">For more information, see [.NET tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="6157a-120">Structure de commande</span><span class="sxs-lookup"><span data-stu-id="6157a-120">Command structure</span></span>

<span data-ttu-id="6157a-121">La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande.</span><span class="sxs-lookup"><span data-stu-id="6157a-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="6157a-122">Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :</span><span class="sxs-lookup"><span data-stu-id="6157a-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app* :</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="6157a-123">Pilote</span><span class="sxs-lookup"><span data-stu-id="6157a-123">Driver</span></span>

<span data-ttu-id="6157a-124">Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="6157a-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="6157a-125">Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="6157a-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="6157a-126">Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="6157a-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="6157a-127">Si vous souhaitez utiliser une version spécifique du Runtime .NET, utilisez l' `--fx-version <VERSION>` option (consultez la référence de la [commande dotnet](dotnet.md) ).</span><span class="sxs-lookup"><span data-stu-id="6157a-127">If you want to use a specific version of the .NET Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="6157a-128">Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI.</span><span class="sxs-lookup"><span data-stu-id="6157a-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="6157a-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6157a-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="6157a-130">D’abord, le pilote détermine la version du kit SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6157a-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="6157a-131">Si aucunglobal.jsn’est présent [ dans](global-json.md) le fichier, la version la plus récente du kit de développement logiciel (SDK) disponible est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6157a-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="6157a-132">Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6157a-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="6157a-133">Une fois que la version du SDK est déterminée, elle exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="6157a-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="6157a-134">Commande</span><span class="sxs-lookup"><span data-stu-id="6157a-134">Command</span></span>

<span data-ttu-id="6157a-135">La commande exécute une action.</span><span class="sxs-lookup"><span data-stu-id="6157a-135">The command performs an action.</span></span> <span data-ttu-id="6157a-136">Par exemple, `dotnet build` génère le code.</span><span class="sxs-lookup"><span data-stu-id="6157a-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="6157a-137">`dotnet publish` publie le code.</span><span class="sxs-lookup"><span data-stu-id="6157a-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="6157a-138">Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="6157a-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="6157a-139">Arguments</span><span class="sxs-lookup"><span data-stu-id="6157a-139">Arguments</span></span>

<span data-ttu-id="6157a-140">Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="6157a-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="6157a-141">Par exemple, lorsque vous exécutez `dotnet publish my_app.csproj` , l' `my_app.csproj` argument indique le projet à publier et est passé à la `publish` commande.</span><span class="sxs-lookup"><span data-stu-id="6157a-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="6157a-142">Options</span><span class="sxs-lookup"><span data-stu-id="6157a-142">Options</span></span>

<span data-ttu-id="6157a-143">Les options que vous passez sur la ligne de commande sont les options de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="6157a-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="6157a-144">Par exemple, lorsque vous exécutez `dotnet publish --output /build_output` , l' `--output` option et sa valeur sont passées à la `publish` commande.</span><span class="sxs-lookup"><span data-stu-id="6157a-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="6157a-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6157a-145">See also</span></span>

- [<span data-ttu-id="6157a-146">référentiel GitHub dotnet/SDK</span><span class="sxs-lookup"><span data-stu-id="6157a-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="6157a-147">Guide d’installation de .NET</span><span class="sxs-lookup"><span data-stu-id="6157a-147">.NET installation guide</span></span>](../install/windows.md)
