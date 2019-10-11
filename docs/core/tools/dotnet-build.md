---
title: Commande dotnet build
description: La commande dotnet build permet de générer un projet et l’ensemble de ses dépendances.
ms.date: 08/08/2019
ms.openlocfilehash: 6194d70a8a14e63adbcad39c7dabbbd220ca329d
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179983"
---
# <a name="dotnet-build"></a><span data-ttu-id="7ebc7-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="7ebc7-103">dotnet build</span></span>

<span data-ttu-id="7ebc7-104">**Cet article s’applique à : ✓** SDK .NET Core 1.x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="7ebc7-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="7ebc7-105">Name</span><span class="sxs-lookup"><span data-stu-id="7ebc7-105">Name</span></span>

<span data-ttu-id="7ebc7-106">`dotnet build` : Génère un projet et l’ensemble de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7ebc7-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="7ebc7-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="7ebc7-108">Description</span><span class="sxs-lookup"><span data-stu-id="7ebc7-108">Description</span></span>

<span data-ttu-id="7ebc7-109">La commande `dotnet build` génère le projet et ses dépendances dans un ensemble de fichiers binaires.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="7ebc7-110">Les fichiers binaires incluent le code du projet dans des fichiers en langage intermédiaire (IL) avec une extension *.dll* et les fichiers de symboles utilisés pour le débogage avec une extension *.pdb*.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="7ebc7-111">Un fichier JSON de dépendances ( *.deps.json*) est généré. Il répertorie les dépendances de l’application.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="7ebc7-112">Un fichier *.runtimeconfig.json* est généré. Il spécifie le runtime partagé et sa version pour l’application.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="7ebc7-113">Si le projet a des dépendances tierces, comme des bibliothèques NuGet, elles sont résolues à partir du cache NuGet et ne sont pas disponibles avec la sortie générée du projet.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="7ebc7-114">Par conséquent, le produit de `dotnet build` ne peut pas être transféré en l’état vers un autre ordinateur pour exécution.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="7ebc7-115">Ce comportement contraste avec celui du .NET Framework dans lequel la génération d’un projet exécutable (une application) produit une sortie exécutable sur n’importe quel ordinateur où le .NET Framework est installé.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="7ebc7-116">Pour obtenir un résultat similaire dans .NET Core, vous devez utiliser la commande [dotnet publish](dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="7ebc7-117">Pour plus d’informations, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="7ebc7-118">La génération requiert le fichier *project.assets.json* qui répertorie les dépendances de votre application.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="7ebc7-119">Le fichier est créé quand la commande [`dotnet restore`](dotnet-restore.md) est exécutée.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="7ebc7-120">Si le fichier de ressources est absent, les outils ne peuvent pas résoudre les assemblys de référence, ce qui entraîne des erreurs.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="7ebc7-121">Avec le kit de développement logiciel (SDK) .NET Core 1. x, vous deviez exécuter explicitement `dotnet restore` avant d’exécuter `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-121">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="7ebc7-122">À compter du SDK .NET Core 2.0, `dotnet restore` s’exécute implicitement quand vous exécutez `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="7ebc7-123">Si vous souhaitez désactiver la restauration implicite au moment d’exécuter la commande de génération, vous pouvez passer l’option `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="7ebc7-124">La possibilité d’exécuter le projet ou non est déterminée par la propriété `<OutputType>` dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="7ebc7-125">L’exemple suivant illustre un projet qui génère du code exécutable :</span><span class="sxs-lookup"><span data-stu-id="7ebc7-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="7ebc7-126">Pour générer une bibliothèque, omettez la propriété `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="7ebc7-127">La principale différence dans la sortie générée est que la DLL de langage intermédiaire pour une bibliothèque ne contient pas de points d’entrée et ne peut pas être exécutée.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="7ebc7-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="7ebc7-128">MSBuild</span></span>

<span data-ttu-id="7ebc7-129">La commande `dotnet build` utilise MSBuild pour générer le projet. Elle prend donc en charge les builds parallèles et les builds incrémentielles.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="7ebc7-130">Pour plus d’informations, consultez l’article [Incremental Builds (Générations incrémentielles)](/visualstudio/msbuild/incremental-builds) .</span><span class="sxs-lookup"><span data-stu-id="7ebc7-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="7ebc7-131">En plus de ses options, la commande `dotnet build` accepte des options MSBuild, comme `-p` pour définir des propriétés ou `-l` pour définir un enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="7ebc7-132">Pour plus d’informations sur ces options, consultez [Informations de référence sur la ligne de commande MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="7ebc7-133">Ou vous pouvez également utiliser la commande [dotnet msbuild](dotnet-msbuild.md).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="7ebc7-134">L’exécution de `dotnet msbuild -restore -target:Build` équivaut à `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="7ebc7-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="7ebc7-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="7ebc7-136">Le fichier projet ou solution à générer.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-136">The project or solution file to build.</span></span> <span data-ttu-id="7ebc7-137">Si vous ne spécifiez pas de fichier projet ou solution, MSBuild recherche dans le répertoire de travail actif un fichier dont l’extension se termine par *proj* ou *sln* et l’utilise.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="7ebc7-138">Options</span><span class="sxs-lookup"><span data-stu-id="7ebc7-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="7ebc7-139">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-139">Defines the build configuration.</span></span> <span data-ttu-id="7ebc7-140">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="7ebc7-141">Compile pour un [framework](../../standard/frameworks.md) spécifique.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="7ebc7-142">Le framework doit être défini dans le [fichier projet](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="7ebc7-143">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7ebc7-144">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="7ebc7-145">Disponible à partir du kit SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="7ebc7-146">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="7ebc7-147">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="7ebc7-148">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-148">For example, to complete authentication.</span></span> <span data-ttu-id="7ebc7-149">Disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="7ebc7-150">Ignore les références entre projets (P2P) et génère uniquement le projet racine spécifié.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="7ebc7-151">Marque la build comme unsafe pour la génération incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="7ebc7-152">Cet indicateur désactive la compilation incrémentielle et force une regénération du graphique de dépendance du projet.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="7ebc7-153">N’exécute pas de restauration implicite pendant la génération.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-153">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="7ebc7-154">Disponible à partir du kit SDK .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-154">Available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="7ebc7-155">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="7ebc7-156">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-156">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="7ebc7-157">Répertoire dans lequel placer les fichiers binaires générés.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="7ebc7-158">Vous devez également définir `--framework` lorsque vous spécifiez cette option.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="7ebc7-159">S’il n’est pas spécifié, le chemin d'accès par défaut est `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="7ebc7-160">Spécifie le runtime cible.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-160">Specifies the target runtime.</span></span> <span data-ttu-id="7ebc7-161">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7ebc7-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7ebc7-162">Définit le niveau de détail MSBuild.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="7ebc7-163">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="7ebc7-164">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="7ebc7-165">Définit la valeur de la propriété `$(VersionSuffix)` à utiliser lors de la génération du projet.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="7ebc7-166">Cela fonctionne uniquement si la propriété `$(Version)` n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="7ebc7-167">Ensuite, `$(Version)` est défini sur `$(VersionPrefix)` combiné avec `$(VersionSuffix)`, séparés par un tiret.</span><span class="sxs-lookup"><span data-stu-id="7ebc7-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="7ebc7-168">Exemples</span><span class="sxs-lookup"><span data-stu-id="7ebc7-168">Examples</span></span>

* <span data-ttu-id="7ebc7-169">Générer un projet et ses dépendances :</span><span class="sxs-lookup"><span data-stu-id="7ebc7-169">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

* <span data-ttu-id="7ebc7-170">Générer un projet et ses dépendances à l’aide de la configuration Release :</span><span class="sxs-lookup"><span data-stu-id="7ebc7-170">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

* <span data-ttu-id="7ebc7-171">Générer un projet et ses dépendances pour un runtime spécifique (dans cet exemple, Ubuntu 18.04) :</span><span class="sxs-lookup"><span data-stu-id="7ebc7-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="7ebc7-172">Générer le projet et utiliser la source de package NuGet spécifiée pendant l’opération de restauration (SDK .NET Core 2.0 et versions ultérieures) :</span><span class="sxs-lookup"><span data-stu-id="7ebc7-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="7ebc7-173">Générer le projet et définissez la version 1.2.3.4 comme un paramètre de build à l’aide de l’`-p` [option MSBuild](#msbuild) :</span><span class="sxs-lookup"><span data-stu-id="7ebc7-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
