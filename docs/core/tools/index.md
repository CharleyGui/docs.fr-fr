---
title: CLI .NET Core
titleSuffix: ''
description: Vue d’ensemble de la CLI .NET Core et de ses fonctionnalités.
ms.date: 02/13/2020
ms.openlocfilehash: d84f96889cabc3fb4521e39db25050aacdd11546
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156710"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="588dd-103">Présentation de CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="588dd-103">.NET Core CLI overview</span></span>

<span data-ttu-id="588dd-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="588dd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="588dd-105">L’interface de ligne de commande (CLI) .NET Core est un chaîne d’outils multiplateforme pour le développement, la génération, l’exécution et la publication d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="588dd-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="588dd-106">Le CLI .NET Core est inclus dans le [Kit SDK .net Core](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="588dd-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="588dd-107">Pour savoir comment installer le kit SDK .NET Core, consultez [install the kit SDK .net Core](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="588dd-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="588dd-108">Commandes CLI</span><span class="sxs-lookup"><span data-stu-id="588dd-108">CLI commands</span></span>

<span data-ttu-id="588dd-109">Les commandes suivantes sont installées par défaut :</span><span class="sxs-lookup"><span data-stu-id="588dd-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="588dd-110">Commandes de base</span><span class="sxs-lookup"><span data-stu-id="588dd-110">Basic commands</span></span>

- [<span data-ttu-id="588dd-111">nouveau</span><span class="sxs-lookup"><span data-stu-id="588dd-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="588dd-112">restore</span><span class="sxs-lookup"><span data-stu-id="588dd-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="588dd-113">build</span><span class="sxs-lookup"><span data-stu-id="588dd-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="588dd-114">publish</span><span class="sxs-lookup"><span data-stu-id="588dd-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="588dd-115">run</span><span class="sxs-lookup"><span data-stu-id="588dd-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="588dd-116">test</span><span class="sxs-lookup"><span data-stu-id="588dd-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="588dd-117">vstest</span><span class="sxs-lookup"><span data-stu-id="588dd-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="588dd-118">pack</span><span class="sxs-lookup"><span data-stu-id="588dd-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="588dd-119">migrer</span><span class="sxs-lookup"><span data-stu-id="588dd-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="588dd-120">clean</span><span class="sxs-lookup"><span data-stu-id="588dd-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="588dd-121">sln</span><span class="sxs-lookup"><span data-stu-id="588dd-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="588dd-122">help</span><span class="sxs-lookup"><span data-stu-id="588dd-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="588dd-123">store</span><span class="sxs-lookup"><span data-stu-id="588dd-123">store</span></span>](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="588dd-124">Commandes de modification de projet</span><span class="sxs-lookup"><span data-stu-id="588dd-124">Project modification commands</span></span>

- [<span data-ttu-id="588dd-125">add package</span><span class="sxs-lookup"><span data-stu-id="588dd-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="588dd-126">add reference</span><span class="sxs-lookup"><span data-stu-id="588dd-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="588dd-127">remove package</span><span class="sxs-lookup"><span data-stu-id="588dd-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="588dd-128">remove reference</span><span class="sxs-lookup"><span data-stu-id="588dd-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="588dd-129">list reference</span><span class="sxs-lookup"><span data-stu-id="588dd-129">list reference</span></span>](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="588dd-130">Commandes avancées</span><span class="sxs-lookup"><span data-stu-id="588dd-130">Advanced commands</span></span>

- [<span data-ttu-id="588dd-131">nuget delete</span><span class="sxs-lookup"><span data-stu-id="588dd-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="588dd-132">nuget locals</span><span class="sxs-lookup"><span data-stu-id="588dd-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="588dd-133">nuget push</span><span class="sxs-lookup"><span data-stu-id="588dd-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="588dd-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="588dd-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="588dd-135">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="588dd-135">dotnet install script</span></span>](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="588dd-136">Commandes de gestion des outils</span><span class="sxs-lookup"><span data-stu-id="588dd-136">Tool management commands</span></span>

- [<span data-ttu-id="588dd-137">installation de l’outil</span><span class="sxs-lookup"><span data-stu-id="588dd-137">tool install</span></span>](dotnet-tool-install.md)
- [<span data-ttu-id="588dd-138">liste d’outils</span><span class="sxs-lookup"><span data-stu-id="588dd-138">tool list</span></span>](dotnet-tool-list.md)
- [<span data-ttu-id="588dd-139">mise à jour de l’outil</span><span class="sxs-lookup"><span data-stu-id="588dd-139">tool update</span></span>](dotnet-tool-update.md)
- <span data-ttu-id="588dd-140">[restauration](global-tools.md#install-a-local-tool) **de l’outil disponible à partir de kit SDK .net Core 3,0**</span><span class="sxs-lookup"><span data-stu-id="588dd-140">[tool restore](global-tools.md#install-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- <span data-ttu-id="588dd-141">[exécution](global-tools.md#invoke-a-local-tool) **de l’outil disponible à partir de kit SDK .net Core 3,0**</span><span class="sxs-lookup"><span data-stu-id="588dd-141">[tool run](global-tools.md#invoke-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- [<span data-ttu-id="588dd-142">désinstallation de l’outil</span><span class="sxs-lookup"><span data-stu-id="588dd-142">tool uninstall</span></span>](dotnet-tool-uninstall.md)

<span data-ttu-id="588dd-143">Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="588dd-143">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="588dd-144">Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="588dd-144">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="588dd-145">Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux.</span><span class="sxs-lookup"><span data-stu-id="588dd-145">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="588dd-146">Pour plus d’informations, consultez [vue d’ensemble des outils .net Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="588dd-146">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="588dd-147">Structure de commande</span><span class="sxs-lookup"><span data-stu-id="588dd-147">Command structure</span></span>

<span data-ttu-id="588dd-148">La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande.</span><span class="sxs-lookup"><span data-stu-id="588dd-148">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="588dd-149">Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :</span><span class="sxs-lookup"><span data-stu-id="588dd-149">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="588dd-150">Pilote</span><span class="sxs-lookup"><span data-stu-id="588dd-150">Driver</span></span>

<span data-ttu-id="588dd-151">Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="588dd-151">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="588dd-152">Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="588dd-152">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="588dd-153">Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="588dd-153">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="588dd-154">Si vous souhaitez utiliser une version spécifique de .NET Core Runtime, choisissez l’option `--fx-version <VERSION>` (voir la référence [dotnet command](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="588dd-154">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="588dd-155">Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI.</span><span class="sxs-lookup"><span data-stu-id="588dd-155">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="588dd-156">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="588dd-156">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="588dd-157">D’abord, le pilote détermine la version du kit SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="588dd-157">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="588dd-158">S’il n’existe aucun fichier [global. JSON](global-json.md) , la version la plus récente du kit de développement logiciel (SDK) disponible est utilisée.</span><span class="sxs-lookup"><span data-stu-id="588dd-158">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="588dd-159">Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="588dd-159">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="588dd-160">Une fois que la version du SDK est déterminée, elle exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="588dd-160">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="588dd-161">Commande</span><span class="sxs-lookup"><span data-stu-id="588dd-161">Command</span></span>

<span data-ttu-id="588dd-162">La commande exécute une action.</span><span class="sxs-lookup"><span data-stu-id="588dd-162">The command performs an action.</span></span> <span data-ttu-id="588dd-163">Par exemple, `dotnet build` génère le code.</span><span class="sxs-lookup"><span data-stu-id="588dd-163">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="588dd-164">`dotnet publish` publie le code.</span><span class="sxs-lookup"><span data-stu-id="588dd-164">`dotnet publish` publishes code.</span></span> <span data-ttu-id="588dd-165">Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="588dd-165">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="588dd-166">Arguments</span><span class="sxs-lookup"><span data-stu-id="588dd-166">Arguments</span></span>

<span data-ttu-id="588dd-167">Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="588dd-167">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="588dd-168">Par exemple, lorsque vous exécutez `dotnet publish my_app.csproj`, l’argument `my_app.csproj` indique le projet à publier et est transmis à la commande `publish`.</span><span class="sxs-lookup"><span data-stu-id="588dd-168">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="588dd-169">Options</span><span class="sxs-lookup"><span data-stu-id="588dd-169">Options</span></span>

<span data-ttu-id="588dd-170">Les options que vous passez sur la ligne de commande sont les options de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="588dd-170">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="588dd-171">Par exemple, lorsque vous exécutez `dotnet publish --output /build_output`, l’option `--output` et sa valeur sont passés à la commande `publish`.</span><span class="sxs-lookup"><span data-stu-id="588dd-171">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="588dd-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="588dd-172">See also</span></span>

- [<span data-ttu-id="588dd-173">référentiel GitHub dotnet/SDK</span><span class="sxs-lookup"><span data-stu-id="588dd-173">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="588dd-174">Guide d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="588dd-174">.NET Core installation guide</span></span>](../install/sdk.md)
