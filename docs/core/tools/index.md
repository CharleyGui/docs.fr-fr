---
title: Outils de l’interface de ligne de commande (CLI) de .NET Core
description: Présentation des outils et fonctionnalités de l’interface de ligne de commande (CLI) de .NET Core.
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: ff96023dd0b161271e146f7a7e69924c9db9e769
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569518"
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="1f717-103">Outils de l’interface de ligne de commande (CLI) de .NET Core</span><span class="sxs-lookup"><span data-stu-id="1f717-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="1f717-104">L’interface de ligne de commande (CLI) de .NET Core est une nouvelle chaîne d’outils multiplateforme pour le développement d’applications .NET.</span><span class="sxs-lookup"><span data-stu-id="1f717-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="1f717-105">CLI est une fondation sur laquelle les autres outils de niveau supérieur, tels que les environnements de développement intégré (IDE), les éditeurs et les orchestrateurs de builds, peuvent se baser.</span><span class="sxs-lookup"><span data-stu-id="1f717-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="1f717-106">Installation</span><span class="sxs-lookup"><span data-stu-id="1f717-106">Installation</span></span>

<span data-ttu-id="1f717-107">Utilisez les programmes d’installation natifs ou les scripts shell d’installation :</span><span class="sxs-lookup"><span data-stu-id="1f717-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="1f717-108">Les programmes d’installation natifs sont principalement utilisés sur les ordinateurs des développeurs et s’appuient sur le mécanisme d’installation natif de chaque plateforme prise en charge, par exemple des packages DEB sur Ubuntu ou des ensembles MSI sur Windows.</span><span class="sxs-lookup"><span data-stu-id="1f717-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="1f717-109">Ces programmes d’installation installent et configurent l’environnement pour une utilisation immédiate par le développeur, mais requièrent des privilèges d’administrateur sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1f717-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="1f717-110">Vous pouvez consulter les instructions d’installation dans le [guide d’installation de .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="1f717-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="1f717-111">Les scripts de shell servent principalement à configurer les serveurs de builds et permettent d’installer les outils sans privilèges d’administration.</span><span class="sxs-lookup"><span data-stu-id="1f717-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="1f717-112">Les scripts d’installation n’installent pas les composants requis sur l’ordinateur, qui doivent être installés manuellement.</span><span class="sxs-lookup"><span data-stu-id="1f717-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="1f717-113">Pour plus d’informations, consultez la [rubrique de référence sur les scripts d’installation](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="1f717-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="1f717-114">Pour plus d’informations sur la configuration de l’interface CLI sur votre serveur de builds avec intégration continue (CI), consultez [Utilisation du SDK et des outils .NET Core avec l’intégration continue](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1f717-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="1f717-115">Par défaut, l’interface CLI s’installe en parallèle (SxS) et plusieurs versions des outils CLI peuvent donc coexister sur un même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1f717-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="1f717-116">La méthode permettant d’identifier la version utilisée sur un ordinateur sur lequel plusieurs versions sont installées est expliquée plus en détail dans la section [Pilote](#driver).</span><span class="sxs-lookup"><span data-stu-id="1f717-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="1f717-117">Commandes CLI</span><span class="sxs-lookup"><span data-stu-id="1f717-117">CLI commands</span></span>

<span data-ttu-id="1f717-118">Les commandes suivantes sont installées par défaut :</span><span class="sxs-lookup"><span data-stu-id="1f717-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1f717-119">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1f717-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="1f717-120">**Commandes de base**</span><span class="sxs-lookup"><span data-stu-id="1f717-120">**Basic commands**</span></span>

* [<span data-ttu-id="1f717-121">new</span><span class="sxs-lookup"><span data-stu-id="1f717-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="1f717-122">restore</span><span class="sxs-lookup"><span data-stu-id="1f717-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="1f717-123">build</span><span class="sxs-lookup"><span data-stu-id="1f717-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="1f717-124">publish</span><span class="sxs-lookup"><span data-stu-id="1f717-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="1f717-125">run</span><span class="sxs-lookup"><span data-stu-id="1f717-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="1f717-126">test</span><span class="sxs-lookup"><span data-stu-id="1f717-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="1f717-127">vstest</span><span class="sxs-lookup"><span data-stu-id="1f717-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="1f717-128">pack</span><span class="sxs-lookup"><span data-stu-id="1f717-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="1f717-129">migrate</span><span class="sxs-lookup"><span data-stu-id="1f717-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="1f717-130">clean</span><span class="sxs-lookup"><span data-stu-id="1f717-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="1f717-131">sln</span><span class="sxs-lookup"><span data-stu-id="1f717-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="1f717-132">help</span><span class="sxs-lookup"><span data-stu-id="1f717-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="1f717-133">store</span><span class="sxs-lookup"><span data-stu-id="1f717-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="1f717-134">**Commandes de modification de projets**</span><span class="sxs-lookup"><span data-stu-id="1f717-134">**Project modification commands**</span></span>

* [<span data-ttu-id="1f717-135">add package</span><span class="sxs-lookup"><span data-stu-id="1f717-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="1f717-136">add reference</span><span class="sxs-lookup"><span data-stu-id="1f717-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="1f717-137">remove package</span><span class="sxs-lookup"><span data-stu-id="1f717-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="1f717-138">remove reference</span><span class="sxs-lookup"><span data-stu-id="1f717-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="1f717-139">list reference</span><span class="sxs-lookup"><span data-stu-id="1f717-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="1f717-140">**Commandes avancées**</span><span class="sxs-lookup"><span data-stu-id="1f717-140">**Advanced commands**</span></span>

* [<span data-ttu-id="1f717-141">nuget delete</span><span class="sxs-lookup"><span data-stu-id="1f717-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="1f717-142">nuget locals</span><span class="sxs-lookup"><span data-stu-id="1f717-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="1f717-143">nuget push</span><span class="sxs-lookup"><span data-stu-id="1f717-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="1f717-144">msbuild</span><span class="sxs-lookup"><span data-stu-id="1f717-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="1f717-145">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="1f717-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1f717-146">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1f717-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="1f717-147">**Commandes de base**</span><span class="sxs-lookup"><span data-stu-id="1f717-147">**Basic commands**</span></span>

* [<span data-ttu-id="1f717-148">new</span><span class="sxs-lookup"><span data-stu-id="1f717-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="1f717-149">restore</span><span class="sxs-lookup"><span data-stu-id="1f717-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="1f717-150">build</span><span class="sxs-lookup"><span data-stu-id="1f717-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="1f717-151">publish</span><span class="sxs-lookup"><span data-stu-id="1f717-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="1f717-152">run</span><span class="sxs-lookup"><span data-stu-id="1f717-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="1f717-153">test</span><span class="sxs-lookup"><span data-stu-id="1f717-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="1f717-154">vstest</span><span class="sxs-lookup"><span data-stu-id="1f717-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="1f717-155">pack</span><span class="sxs-lookup"><span data-stu-id="1f717-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="1f717-156">migrate</span><span class="sxs-lookup"><span data-stu-id="1f717-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="1f717-157">clean</span><span class="sxs-lookup"><span data-stu-id="1f717-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="1f717-158">sln</span><span class="sxs-lookup"><span data-stu-id="1f717-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="1f717-159">**Commandes de modification de projets**</span><span class="sxs-lookup"><span data-stu-id="1f717-159">**Project modification commands**</span></span>

* [<span data-ttu-id="1f717-160">add package</span><span class="sxs-lookup"><span data-stu-id="1f717-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="1f717-161">add reference</span><span class="sxs-lookup"><span data-stu-id="1f717-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="1f717-162">remove package</span><span class="sxs-lookup"><span data-stu-id="1f717-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="1f717-163">remove reference</span><span class="sxs-lookup"><span data-stu-id="1f717-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="1f717-164">list reference</span><span class="sxs-lookup"><span data-stu-id="1f717-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="1f717-165">**Commandes avancées**</span><span class="sxs-lookup"><span data-stu-id="1f717-165">**Advanced commands**</span></span>

* [<span data-ttu-id="1f717-166">nuget delete</span><span class="sxs-lookup"><span data-stu-id="1f717-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="1f717-167">nuget locals</span><span class="sxs-lookup"><span data-stu-id="1f717-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="1f717-168">nuget push</span><span class="sxs-lookup"><span data-stu-id="1f717-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="1f717-169">msbuild</span><span class="sxs-lookup"><span data-stu-id="1f717-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="1f717-170">dotnet install script</span><span class="sxs-lookup"><span data-stu-id="1f717-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="1f717-171">L’interface CLI adopte un modèle d’extensibilité qui vous permet de spécifier des outils supplémentaires pour vos projets.</span><span class="sxs-lookup"><span data-stu-id="1f717-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="1f717-172">Pour plus d’informations, consultez la rubrique [Modèle d’extensibilité des outils CLI .NET Core](extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="1f717-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="1f717-173">Structure de commande</span><span class="sxs-lookup"><span data-stu-id="1f717-173">Command structure</span></span>

<span data-ttu-id="1f717-174">La structure de commande CLI se compose du [pilote (« dotnet »)](#driver), de la [commande](#command) et éventuellement des [arguments](#arguments) et [options](#options) de la commande.</span><span class="sxs-lookup"><span data-stu-id="1f717-174">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="1f717-175">Ce modèle apparaît dans la plupart des opérations de l’interface CLI, notamment la création d’une application console et son exécution à partir de la ligne de commande, comme le montrent les commandes suivantes, exécutées à partir d’un répertoire nommé *my_app* :</span><span class="sxs-lookup"><span data-stu-id="1f717-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="1f717-176">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="1f717-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1f717-177">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="1f717-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="1f717-178">Pilote</span><span class="sxs-lookup"><span data-stu-id="1f717-178">Driver</span></span>

<span data-ttu-id="1f717-179">Le pilote s’intitule [dotnet](dotnet.md) et gère deux tâches : l’exécution d’une [application dépendant du framework](../deploying/index.md) ou l’exécution d’une commande.</span><span class="sxs-lookup"><span data-stu-id="1f717-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="1f717-180">Pour exécuter une application dépendant du framework, spécifiez l’application après le pilote, par exemple `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="1f717-180">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="1f717-181">Lors de l’exécution de la commande à partir du dossier où se trouve la DLL de l’application, vous devez simplement exécuter `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="1f717-181">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="1f717-182">Si vous souhaitez utiliser une version spécifique de .NET Core Runtime, choisissez l’option `--fx-version <VERSION>` (voir la référence [dotnet command](dotnet.md)).</span><span class="sxs-lookup"><span data-stu-id="1f717-182">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="1f717-183">Lorsque vous fournissez une commande au pilote, `dotnet.exe` démarre le processus d’exécution de la commande CLI.</span><span class="sxs-lookup"><span data-stu-id="1f717-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="1f717-184">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="1f717-184">For example:</span></span>

```bash
> dotnet build
```

<span data-ttu-id="1f717-185">D’abord, le pilote détermine la version du kit SDK à utiliser.</span><span class="sxs-lookup"><span data-stu-id="1f717-185">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="1f717-186">S’il n’existe pas de ['global.json'](global-json.md), la dernière version du SDK disponible est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1f717-186">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="1f717-187">Il s’agit peut-être d’une préversion ou d’une version stable, selon la plus récente qui se trouve sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1f717-187">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="1f717-188">Une fois que la version du SDK est déterminée, elle exécute la commande.</span><span class="sxs-lookup"><span data-stu-id="1f717-188">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="1f717-189">Commande</span><span class="sxs-lookup"><span data-stu-id="1f717-189">Command</span></span>

<span data-ttu-id="1f717-190">La commande exécute une action.</span><span class="sxs-lookup"><span data-stu-id="1f717-190">The command performs an action.</span></span> <span data-ttu-id="1f717-191">Par exemple, `dotnet build` génère le code.</span><span class="sxs-lookup"><span data-stu-id="1f717-191">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="1f717-192">`dotnet publish` publie le code.</span><span class="sxs-lookup"><span data-stu-id="1f717-192">`dotnet publish` publishes code.</span></span> <span data-ttu-id="1f717-193">Les commandes sont implémentées comme une application console à l’aide d’une convention `dotnet {command}`.</span><span class="sxs-lookup"><span data-stu-id="1f717-193">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="1f717-194">Arguments</span><span class="sxs-lookup"><span data-stu-id="1f717-194">Arguments</span></span>

<span data-ttu-id="1f717-195">Les arguments que vous passez sur la ligne de commande sont les arguments de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="1f717-195">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="1f717-196">Par exemple, lorsque vous exécutez `dotnet publish my_app.csproj`, l’argument `my_app.csproj` indique le projet à publier et est transmis à la commande `publish`.</span><span class="sxs-lookup"><span data-stu-id="1f717-196">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="1f717-197">Options</span><span class="sxs-lookup"><span data-stu-id="1f717-197">Options</span></span>

<span data-ttu-id="1f717-198">Les options que vous passez sur la ligne de commande sont les options de la commande appelée.</span><span class="sxs-lookup"><span data-stu-id="1f717-198">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="1f717-199">Par exemple, lorsque vous exécutez `dotnet publish --output /build_output`, l’option `--output` et sa valeur sont passés à la commande `publish`.</span><span class="sxs-lookup"><span data-stu-id="1f717-199">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="1f717-200">Migration à partir de project.json</span><span class="sxs-lookup"><span data-stu-id="1f717-200">Migration from project.json</span></span>

<span data-ttu-id="1f717-201">Si vous avez utilisé les outils Preview 2 pour produire des projets *project.json*, consultez la rubrique [dotnet migrate](dotnet-migrate.md) pour plus d’informations sur la migration de votre projet vers MSBuild/ *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="1f717-201">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="1f717-202">Pour les projets .NET Core créés avant la version des outils de Preview 2, mettez à jour manuellement le projet en suivant les instructions dans [Migration de DNX vers l’interface CLI .NET Core (project.json)](../migration/from-dnx.md), puis utilisez `dotnet migrate` ou mettez directement à niveau vos projets.</span><span class="sxs-lookup"><span data-stu-id="1f717-202">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f717-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f717-203">See also</span></span>

- [<span data-ttu-id="1f717-204">Référentiel GitHub dotnet/CLI</span><span class="sxs-lookup"><span data-stu-id="1f717-204">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)
- [<span data-ttu-id="1f717-205">Guide d’installation de .NET Core</span><span class="sxs-lookup"><span data-stu-id="1f717-205">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
