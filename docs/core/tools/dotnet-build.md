---
title: Commande dotnet build
description: La commande dotnet build permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 10/14/2019
ms.openlocfilehash: fe2135c150be46997699f756f7f0c9bc18bbb529
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846826"
---
# <a name="dotnet-build"></a><span data-ttu-id="22d56-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="22d56-103">dotnet build</span></span>

<span data-ttu-id="22d56-104">**Cet article s’applique à : ✓** SDK .NET Core 1.x et ultérieur</span><span class="sxs-lookup"><span data-stu-id="22d56-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="22d56-105">Name</span><span class="sxs-lookup"><span data-stu-id="22d56-105">Name</span></span>

<span data-ttu-id="22d56-106">`dotnet build` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="22d56-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="22d56-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="22d56-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="22d56-108">Description</span><span class="sxs-lookup"><span data-stu-id="22d56-108">Description</span></span>

<span data-ttu-id="22d56-109">La commande `dotnet build` génère le projet et ses dépendances dans un ensemble de fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="22d56-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="22d56-110">Les binaires incluent le code du projet dans des fichiers de langage intermédiaire (IL) avec une extension *. dll* .</span><span class="sxs-lookup"><span data-stu-id="22d56-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="22d56-111">En fonction du type de projet et des paramètres, d’autres fichiers peuvent être inclus, par exemple :</span><span class="sxs-lookup"><span data-stu-id="22d56-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="22d56-112">Exécutable qui peut être utilisé pour exécuter l’application, si le type de projet est un exécutable ciblant .NET Core 3,0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="22d56-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="22d56-113">Fichiers de symboles utilisés pour le débogage avec une extension *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="22d56-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="22d56-114">Un fichier *. DEPS. JSON* , qui répertorie les dépendances de l’application ou de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="22d56-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="22d56-115">Un fichier *. runtimeconfig. JSON* , qui spécifie le runtime partagé et sa version pour une application.</span><span class="sxs-lookup"><span data-stu-id="22d56-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="22d56-116">Les autres bibliothèques dont le projet dépend (par le biais de références de projet ou de références de package NuGet).</span><span class="sxs-lookup"><span data-stu-id="22d56-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="22d56-117">Pour les projets exécutables ciblant des versions antérieures à .NET Core 3,0, les dépendances de bibliothèque de NuGet ne sont généralement pas copiées dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="22d56-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="22d56-118">Ils sont résolus à partir du dossier des packages globaux NuGet au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="22d56-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="22d56-119">Par conséquent, le produit de `dotnet build` ne peut pas être transféré en l’état vers un autre ordinateur pour exécution.</span><span class="sxs-lookup"><span data-stu-id="22d56-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="22d56-120">Pour créer une version de l’application qui peut être déployée, vous devez la publier (par exemple, à l’aide de la commande [dotnet Publish](dotnet-publish.md) ).</span><span class="sxs-lookup"><span data-stu-id="22d56-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="22d56-121">Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="22d56-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="22d56-122">Pour les projets exécutables ciblant .NET Core 3,0 et versions ultérieures, les dépendances de bibliothèque sont copiées dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="22d56-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="22d56-123">Cela signifie que s’il n’existe aucune autre logique spécifique à la publication (telle que les projets Web), la sortie de la génération doit être déployée.</span><span class="sxs-lookup"><span data-stu-id="22d56-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="22d56-124">La génération requiert le fichier *project.assets.json* qui répertorie les dépendances de votre application.</span><span class="sxs-lookup"><span data-stu-id="22d56-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="22d56-125">Le fichier est créé quand la commande [`dotnet restore`](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="22d56-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="22d56-126">Si le fichier de ressources est absent, les outils ne peuvent pas résoudre les assemblys de référence, ce qui entraîne des erreurs.</span><span class="sxs-lookup"><span data-stu-id="22d56-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="22d56-127">Avec le kit de développement logiciel (SDK) .NET Core 1. x, vous deviez exécuter explicitement `dotnet restore` avant d’exécuter `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="22d56-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="22d56-128">À compter du SDK .NET Core 2.0, `dotnet restore` s’exécute implicitement quand vous exécutez `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="22d56-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="22d56-129">Si vous souhaitez désactiver la restauration implicite au moment d’exécuter la commande de génération, vous pouvez passer l’option `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="22d56-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="22d56-130">La possibilité d’exécuter le projet ou non est déterminée par la propriété `<OutputType>` dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="22d56-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="22d56-131">L’exemple suivant illustre un projet qui génère du code exécutable :</span><span class="sxs-lookup"><span data-stu-id="22d56-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="22d56-132">Pour produire une bibliothèque, omettez la propriété `<OutputType>` ou remplacez sa valeur par `Library`.</span><span class="sxs-lookup"><span data-stu-id="22d56-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="22d56-133">La DLL IL d’une bibliothèque ne contient pas de points d’entrée et ne peut pas être exécutée.</span><span class="sxs-lookup"><span data-stu-id="22d56-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="22d56-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="22d56-134">MSBuild</span></span>

<span data-ttu-id="22d56-135">La commande `dotnet build` utilise MSBuild pour générer le projet. Elle prend donc en charge les builds parallèles et les builds incrémentielles.</span><span class="sxs-lookup"><span data-stu-id="22d56-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="22d56-136">Pour plus d’informations, consultez l’article [Incremental Builds (Générations incrémentielles)](/visualstudio/msbuild/incremental-builds) .</span><span class="sxs-lookup"><span data-stu-id="22d56-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="22d56-137">En plus de ses options, la commande `dotnet build` accepte des options MSBuild, comme `-p` pour définir des propriétés ou `-l` pour définir un enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="22d56-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="22d56-138">Pour plus d’informations sur ces options, consultez [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="22d56-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="22d56-139">Ou vous pouvez également utiliser la commande [dotnet msbuild](dotnet-msbuild.md).</span><span class="sxs-lookup"><span data-stu-id="22d56-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="22d56-140">L’exécution de `dotnet build` est équivalente à l’exécution de `dotnet msbuild -restore`; Toutefois, le niveau de détail par défaut de la sortie est différent.</span><span class="sxs-lookup"><span data-stu-id="22d56-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="22d56-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="22d56-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="22d56-142">Le fichier projet ou solution à générer.</span><span class="sxs-lookup"><span data-stu-id="22d56-142">The project or solution file to build.</span></span> <span data-ttu-id="22d56-143">Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.</span><span class="sxs-lookup"><span data-stu-id="22d56-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="22d56-144">Options</span><span class="sxs-lookup"><span data-stu-id="22d56-144">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="22d56-145">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="22d56-145">Defines the build configuration.</span></span> <span data-ttu-id="22d56-146">La valeur par défaut pour la plupart des projets est `Debug`, mais vous pouvez remplacer les paramètres de configuration de build dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="22d56-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="22d56-147">Compile pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="22d56-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="22d56-148">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="22d56-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="22d56-149">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="22d56-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="22d56-150">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="22d56-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="22d56-151">Disponible à partir du kit SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="22d56-151">Available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="22d56-152">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="22d56-152">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="22d56-153">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="22d56-153">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="22d56-154">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="22d56-154">For example, to complete authentication.</span></span> <span data-ttu-id="22d56-155">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="22d56-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="22d56-156">Ignore les références entre projets (P2P) et génère uniquement le projet racine spécifié.</span><span class="sxs-lookup"><span data-stu-id="22d56-156">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="22d56-157">Marque la build comme unsafe pour la génération incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="22d56-157">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="22d56-158">Cet indicateur désactive la compilation incrémentielle et force une regénération du graphique de dépendance du projet.</span><span class="sxs-lookup"><span data-stu-id="22d56-158">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="22d56-159">N’exécute pas de restauration implicite pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="22d56-159">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="22d56-160">Disponible à partir du kit SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="22d56-160">Available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="22d56-161">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="22d56-161">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="22d56-162">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="22d56-162">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="22d56-163">Répertoire dans lequel placer les fichiers binaires générés.</span><span class="sxs-lookup"><span data-stu-id="22d56-163">Directory in which to place the built binaries.</span></span> <span data-ttu-id="22d56-164">S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="22d56-164">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="22d56-165">Pour les projets avec plusieurs frameworks cibles (via la propriété `TargetFrameworks`), vous devez également définir des `--framework` lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="22d56-165">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="22d56-166">Spécifie le runtime cible.</span><span class="sxs-lookup"><span data-stu-id="22d56-166">Specifies the target runtime.</span></span> <span data-ttu-id="22d56-167">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="22d56-167">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="22d56-168">Définit le niveau de détail MSBuild.</span><span class="sxs-lookup"><span data-stu-id="22d56-168">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="22d56-169">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="22d56-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="22d56-170">La valeur par défaut est `minimal`,</span><span class="sxs-lookup"><span data-stu-id="22d56-170">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="22d56-171">Définit la valeur de la propriété `$(VersionSuffix)` à utiliser lors de la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="22d56-171">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="22d56-172">Cela fonctionne uniquement si la propriété `$(Version)` n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="22d56-172">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="22d56-173">Ensuite, `$(Version)` est défini sur `$(VersionPrefix)` combiné avec `$(VersionSuffix)`, séparés par un tiret.</span><span class="sxs-lookup"><span data-stu-id="22d56-173">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="22d56-174">Exemples</span><span class="sxs-lookup"><span data-stu-id="22d56-174">Examples</span></span>

- <span data-ttu-id="22d56-175">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="22d56-175">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="22d56-176">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="22d56-176">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="22d56-177">Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 18.04) :</span><span class="sxs-lookup"><span data-stu-id="22d56-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="22d56-178">Générer le projet et utiliser la source de package NuGet spécifiée pendant l’opération de restauration (SDK .NET Core 2.0 et versions ultérieures) :</span><span class="sxs-lookup"><span data-stu-id="22d56-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="22d56-179">Générer le projet et définissez la version 1.2.3.4 comme un paramètre de build à l’aide de l’`-p` [option MSBuild](#msbuild) :</span><span class="sxs-lookup"><span data-stu-id="22d56-179">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
