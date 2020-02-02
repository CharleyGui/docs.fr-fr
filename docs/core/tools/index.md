---
title: CLI .NET Core
titleSuffix: ''
description: Vue d’ensemble de la CLI .NET Core et de ses fonctionnalités.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920476"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="1dd81-103">Présentation de CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="1dd81-103">.NET Core CLI overview</span></span>

<span data-ttu-id="1dd81-104">L’interface de ligne de commande (CLI) .NET Core est un chaîne d’outils multiplateforme pour le développement, la génération, l’exécution et la publication d’applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1dd81-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="1dd81-105">Le CLI .NET Core est inclus dans le [Kit SDK .net Core](../sdk.md).</span><span class="sxs-lookup"><span data-stu-id="1dd81-105">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="1dd81-106">Pour savoir comment installer le kit SDK .NET Core, consultez [install the kit SDK .net Core](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="1dd81-106">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="1dd81-107">Commandes CLI</span><span class="sxs-lookup"><span data-stu-id="1dd81-107">CLI commands</span></span>

<span data-ttu-id="1dd81-108">Les commandes suivantes sont installées par défaut :</span><span class="sxs-lookup"><span data-stu-id="1dd81-108">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1dd81-109">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1dd81-109">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="1dd81-110">**Commandes de base**</span><span class="sxs-lookup"><span data-stu-id="1dd81-110">**Basic commands**</span></span>

- [<span data-ttu-id="1dd81-111">new</span><span class="sxs-lookup"><span data-stu-id="1dd81-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="1dd81-112">restore</span><span class="sxs-lookup"><span data-stu-id="1dd81-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="1dd81-113">build</span><span class="sxs-lookup"><span data-stu-id="1dd81-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="1dd81-114">publish</span><span class="sxs-lookup"><span data-stu-id="1dd81-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="1dd81-115">run</span><span class="sxs-lookup"><span data-stu-id="1dd81-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="1dd81-116">test</span><span class="sxs-lookup"><span data-stu-id="1dd81-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="1dd81-117">vstest</span><span class="sxs-lookup"><span data-stu-id="1dd81-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="1dd81-118">pack</span><span class="sxs-lookup"><span data-stu-id="1dd81-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="1dd81-119">migrate</span><span class="sxs-lookup"><span data-stu-id="1dd81-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="1dd81-120">clean</span><span class="sxs-lookup"><span data-stu-id="1dd81-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="1dd81-121">sln</span><span class="sxs-lookup"><span data-stu-id="1dd81-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="1dd81-122">help</span><span class="sxs-lookup"><span data-stu-id="1dd81-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="1dd81-123">store</span><span class="sxs-lookup"><span data-stu-id="1dd81-123">store</span></span>](dotnet-store.md)

<span data-ttu-id="1dd81-124">**Commandes de modification de projets**</span><span class="sxs-lookup"><span data-stu-id="1dd81-124">**Project modification commands**</span></span>

- [<span data-ttu-id="1dd81-125">add package</span><span class="sxs-lookup"><span data-stu-id="1dd81-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="1dd81-126">add reference</span><span class="sxs-lookup"><span data-stu-id="1dd81-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="1dd81-127">remove package</span><span class="sxs-lookup"><span data-stu-id="1dd81-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="1dd81-128">remove reference</span><span class="sxs-lookup"><span data-stu-id="1dd81-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="1dd81-129">list reference</span><span class="sxs-lookup"><span data-stu-id="1dd81-129">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="1dd81-130">**Commandes avancées**</span><span class="sxs-lookup"><span data-stu-id="1dd81-130">**Advanced commands**</span></span>

- [<span data-ttu-id="1dd81-131">nuget delete</span><span class="sxs-lookup"><span data-stu-id="1dd81-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="1dd81-132">nuget locals</span><span class="sxs-lookup"><span data-stu-id="1dd81-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="1dd81-133">nuget push</span><span class="sxs-lookup"><span data-stu-id="1dd81-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="1dd81-134">msbuild</span><span class="sxs-lookup"><span data-stu-id="1dd81-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="1dd81-135">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="1dd81-135">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1dd81-136">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1dd81-136">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1dd81-137">**Commandes de base**</span><span class="sxs-lookup"><span data-stu-id="1dd81-137">**Basic commands**</span></span>

- [<span data-ttu-id="1dd81-138">new</span><span class="sxs-lookup"><span data-stu-id="1dd81-138">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="1dd81-139">restore</span><span class="sxs-lookup"><span data-stu-id="1dd81-139">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="1dd81-140">build</span><span class="sxs-lookup"><span data-stu-id="1dd81-140">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="1dd81-141">publish</span><span class="sxs-lookup"><span data-stu-id="1dd81-141">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="1dd81-142">run</span><span class="sxs-lookup"><span data-stu-id="1dd81-142">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="1dd81-143">test</span><span class="sxs-lookup"><span data-stu-id="1dd81-143">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="1dd81-144">vstest</span><span class="sxs-lookup"><span data-stu-id="1dd81-144">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="1dd81-145">pack</span><span class="sxs-lookup"><span data-stu-id="1dd81-145">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="1dd81-146">migrate</span><span class="sxs-lookup"><span data-stu-id="1dd81-146">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="1dd81-147">clean</span><span class="sxs-lookup"><span data-stu-id="1dd81-147">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="1dd81-148">sln</span><span class="sxs-lookup"><span data-stu-id="1dd81-148">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="1dd81-149">**Commandes de modification de projets**</span><span class="sxs-lookup"><span data-stu-id="1dd81-149">**Project modification commands**</span></span>

- [<span data-ttu-id="1dd81-150">add package</span><span class="sxs-lookup"><span data-stu-id="1dd81-150">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="1dd81-151">add reference</span><span class="sxs-lookup"><span data-stu-id="1dd81-151">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="1dd81-152">remove package</span><span class="sxs-lookup"><span data-stu-id="1dd81-152">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="1dd81-153">remove reference</span><span class="sxs-lookup"><span data-stu-id="1dd81-153">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="1dd81-154">list reference</span><span class="sxs-lookup"><span data-stu-id="1dd81-154">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="1dd81-155">**Commandes avancées**</span><span class="sxs-lookup"><span data-stu-id="1dd81-155">**Advanced commands**</span></span>

- [<span data-ttu-id="1dd81-156">nuget delete</span><span class="sxs-lookup"><span data-stu-id="1dd81-156">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="1dd81-157">nuget locals</span><span class="sxs-lookup"><span data-stu-id="1dd81-157">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="1dd81-158">nuget push</span><span class="sxs-lookup"><span data-stu-id="1dd81-158">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="1dd81-159">msbuild</span><span class="sxs-lookup"><span data-stu-id="1dd81-159">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="1dd81-160">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="1dd81-160">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="1dd81-161">L’interface CLI adopte un modèle d’extensibilité qui vous permet de spécifier des outils supplémentaires pour vos projets.</span><span class="sxs-lookup"><span data-stu-id="1dd81-161">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="1dd81-162">Pour plus d’informations, consultez la rubrique [Modèle d’extensibilité des outils CLI .NET Core](extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="1dd81-162">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="1dd81-163">Structure de commande</span><span class="sxs-lookup"><span data-stu-id="1dd81-163">Command structure</span></span>

<span data-ttu-id="1dd81-164">La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande.</span><span class="sxs-lookup"><span data-stu-id="1dd81-164">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="1dd81-165">Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :</span><span class="sxs-lookup"><span data-stu-id="1dd81-165">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1dd81-166">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1dd81-166">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1dd81-167">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1dd81-167">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="1dd81-168">Pilote</span><span class="sxs-lookup"><span data-stu-id="1dd81-168">Driver</span></span>

<span data-ttu-id="1dd81-169">Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="1dd81-169">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="1dd81-170">Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="1dd81-170">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="1dd81-171">Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="1dd81-171">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="1dd81-172">Si vous souhaitez utiliser une version spécifique de .NET Core Runtime, choisissez l’option `--fx-version <VERSION>` (voir la référence [dotnet command](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="1dd81-172">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="1dd81-173">Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI.</span><span class="sxs-lookup"><span data-stu-id="1dd81-173">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="1dd81-174">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1dd81-174">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="1dd81-175">D’abord, le pilote détermine la version du kit SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1dd81-175">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="1dd81-176">S’il n’existe pas de ['global.json'](global-json.md), la dernière version du SDK disponible est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1dd81-176">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="1dd81-177">Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1dd81-177">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="1dd81-178">Une fois que la version du SDK est déterminée, elle exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="1dd81-178">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="1dd81-179">Command</span><span class="sxs-lookup"><span data-stu-id="1dd81-179">Command</span></span>

<span data-ttu-id="1dd81-180">La commande exécute une action.</span><span class="sxs-lookup"><span data-stu-id="1dd81-180">The command performs an action.</span></span> <span data-ttu-id="1dd81-181">Par exemple, `dotnet build` génère le code.</span><span class="sxs-lookup"><span data-stu-id="1dd81-181">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="1dd81-182">`dotnet publish` publie le code.</span><span class="sxs-lookup"><span data-stu-id="1dd81-182">`dotnet publish` publishes code.</span></span> <span data-ttu-id="1dd81-183">Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="1dd81-183">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="1dd81-184">Arguments</span><span class="sxs-lookup"><span data-stu-id="1dd81-184">Arguments</span></span>

<span data-ttu-id="1dd81-185">Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="1dd81-185">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="1dd81-186">Par exemple, lorsque vous exécutez `dotnet publish my_app.csproj`, l’argument `my_app.csproj` indique le projet à publier et est transmis à la commande `publish`.</span><span class="sxs-lookup"><span data-stu-id="1dd81-186">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="1dd81-187">Options</span><span class="sxs-lookup"><span data-stu-id="1dd81-187">Options</span></span>

<span data-ttu-id="1dd81-188">Les options que vous passez sur la ligne de commande sont les options de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="1dd81-188">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="1dd81-189">Par exemple, lorsque vous exécutez `dotnet publish --output /build_output`, l’option `--output` et sa valeur sont passés à la commande `publish`.</span><span class="sxs-lookup"><span data-stu-id="1dd81-189">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="1dd81-190">Migration à partir de project.json</span><span class="sxs-lookup"><span data-stu-id="1dd81-190">Migration from project.json</span></span>

<span data-ttu-id="1dd81-191">Si vous avez utilisé les outils Preview 2 pour produire des projets *project.json*, consultez la rubrique [dotnet migrate](dotnet-migrate.md) pour plus d’informations sur la migration de votre projet vers MSBuild/ *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="1dd81-191">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="1dd81-192">Pour les projets .NET Core créés avant la version des outils de Preview 2, mettez à jour manuellement le projet en suivant les instructions dans [Migration de DNX vers l’interface CLI .NET Core (project.json)](../migration/from-dnx.md), puis utilisez `dotnet migrate` ou mettez directement à niveau vos projets.</span><span class="sxs-lookup"><span data-stu-id="1dd81-192">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1dd81-193">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dd81-193">See also</span></span>

- [<span data-ttu-id="1dd81-194">référentiel GitHub dotnet/SDK</span><span class="sxs-lookup"><span data-stu-id="1dd81-194">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="1dd81-195">Guide d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="1dd81-195">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
