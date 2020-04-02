---
title: Commande dotnet publish
description: La commande de publication dotnet publie un projet ou une solution .NET Core à un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588269"
---
# <a name="dotnet-publish"></a><span data-ttu-id="9930e-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9930e-103">dotnet publish</span></span>

<span data-ttu-id="9930e-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="9930e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9930e-105">Nom</span><span class="sxs-lookup"><span data-stu-id="9930e-105">Name</span></span>

<span data-ttu-id="9930e-106">`dotnet publish`- Publie l’application et ses dépendances à un dossier pour le déploiement dans un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="9930e-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9930e-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="9930e-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="9930e-108">Description</span><span class="sxs-lookup"><span data-stu-id="9930e-108">Description</span></span>

<span data-ttu-id="9930e-109">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="9930e-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="9930e-110">La sortie inclut les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="9930e-110">The output includes the following assets:</span></span>

- <span data-ttu-id="9930e-111">Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.</span><span class="sxs-lookup"><span data-stu-id="9930e-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="9930e-112">Un fichier *.deps.json* qui comprend toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="9930e-113">Un fichier *.runtimeconfig.json* qui spécifie le temps d’exécution partagé que l’application attend, ainsi que d’autres options de configuration pour le temps d’exécution (par exemple, type de collecte des ordures).</span><span class="sxs-lookup"><span data-stu-id="9930e-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="9930e-114">Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="9930e-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="9930e-115">La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9930e-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="9930e-116">Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement.</span><span class="sxs-lookup"><span data-stu-id="9930e-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="9930e-117">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="9930e-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="9930e-118">Pour plus d’informations, voir [Publier .NET Apps Core avec le CLI .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9930e-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="9930e-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="9930e-119">MSBuild</span></span>

<span data-ttu-id="9930e-120">La commande `dotnet publish` appelle MSBuild, qui appelle la cible de `Publish`.</span><span class="sxs-lookup"><span data-stu-id="9930e-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="9930e-121">Les paramètres passés à `dotnet publish` sont passés à MSBuild.</span><span class="sxs-lookup"><span data-stu-id="9930e-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="9930e-122">Les paramètres `-c` et `-o` correspondent aux propriétés `Configuration` et `OutputPath` de MSBuild, respectivement.</span><span class="sxs-lookup"><span data-stu-id="9930e-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="9930e-123">La `dotnet publish` commande accepte les options MSBuild, telles que `-p` pour définir les propriétés et `-l` définir un bûcheron.</span><span class="sxs-lookup"><span data-stu-id="9930e-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="9930e-124">Par exemple, vous pouvez définir une propriété MSBuild en utilisant le format : `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="9930e-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="9930e-125">Vous pouvez également définir des propriétés liées à la publication en vous référant à un fichier *.pubxml,* par exemple :</span><span class="sxs-lookup"><span data-stu-id="9930e-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="9930e-126">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="9930e-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="9930e-127">Informations de référence sur la ligne de commande MSBuild</span><span class="sxs-lookup"><span data-stu-id="9930e-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="9930e-128">Visual Studio publie des profils (.pubxml) pour ASP.NET déploiement de l’application Core</span><span class="sxs-lookup"><span data-stu-id="9930e-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="9930e-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9930e-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="9930e-130">Arguments</span><span class="sxs-lookup"><span data-stu-id="9930e-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="9930e-131">Le projet ou la solution à publier.</span><span class="sxs-lookup"><span data-stu-id="9930e-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="9930e-132">`PROJECT`est le nom de voie et de fichier [d’un](csproj.md)fichier de projet de C, de F, ou de base visuelle, ou le chemin vers un répertoire qui contient un fichier de projet de C, de F, ou de base visuelle.</span><span class="sxs-lookup"><span data-stu-id="9930e-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="9930e-133">Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="9930e-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="9930e-134">`SOLUTION`est le chemin et le nom de fichier d’un fichier de solution *(extension .sln),* ou le chemin vers un répertoire qui contient un fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="9930e-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="9930e-135">Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="9930e-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="9930e-136">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9930e-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="9930e-137">Options</span><span class="sxs-lookup"><span data-stu-id="9930e-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="9930e-138">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="9930e-138">Defines the build configuration.</span></span> <span data-ttu-id="9930e-139">La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="9930e-140">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="9930e-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="9930e-141">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="9930e-142">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="9930e-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9930e-143">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="9930e-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9930e-144">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="9930e-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="9930e-145">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9930e-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="9930e-146">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="9930e-146">For example, to complete authentication.</span></span> <span data-ttu-id="9930e-147">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9930e-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="9930e-148">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="9930e-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="9930e-149">Le fichier manifeste fait partie [ `dotnet store` ](dotnet-store.md)de la sortie de la commande .</span><span class="sxs-lookup"><span data-stu-id="9930e-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="9930e-150">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="9930e-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="9930e-151">Ne génère pas le projet avant la publication.</span><span class="sxs-lookup"><span data-stu-id="9930e-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="9930e-152">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="9930e-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="9930e-153">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="9930e-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="9930e-154">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="9930e-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="9930e-155">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9930e-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9930e-156">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="9930e-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9930e-157">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="9930e-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="9930e-158">S’il n’est pas précisé, il ne fait pas défaut à *[project_file_folder]./bin/[configuration]/[cadre]/publier/* pour un délai exécutable et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="9930e-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="9930e-159">Il est par défaut à *[project_file_folder]/bin/[configuration]/[cadre]/[runtime]/publish/* pour un exécutable autonome.</span><span class="sxs-lookup"><span data-stu-id="9930e-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  - <span data-ttu-id="9930e-160">.NET Core 3.x SDK et plus tard</span><span class="sxs-lookup"><span data-stu-id="9930e-160">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="9930e-161">Si un chemin relatif est spécifié lors de la publication d’un projet, l’annuaire de sortie généré est relatif à l’annuaire de travail actuel, et non à l’emplacement du fichier du projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-161">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="9930e-162">Si un chemin relatif est spécifié lors de la publication d’une solution, toutes les sorties pour tous les projets entrent dans le dossier spécifié par rapport à l’annuaire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="9930e-162">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="9930e-163">Pour faire publier la sortie aller à des dossiers séparés pour chaque `PublishDir` projet, `--output` spécifier un chemin relatif en utilisant la propriété de msbuild au lieu de l’option.</span><span class="sxs-lookup"><span data-stu-id="9930e-163">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="9930e-164">Par exemple, `dotnet publish -p:PublishDir=.\publish` envoie la sortie `publish` de publication pour chaque projet à un dossier sous le dossier qui contient le fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-164">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="9930e-165">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="9930e-165">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="9930e-166">Si un chemin relatif est spécifié lors de la publication d’un projet, l’annuaire de sortie généré est relatif à l’emplacement du fichier du projet, et non à l’annuaire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="9930e-166">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="9930e-167">Si un chemin relatif est spécifié lors de la publication d’une solution, la sortie de chaque projet est dans un dossier distinct par rapport à l’emplacement du fichier du projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-167">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="9930e-168">Si un chemin absolu est spécifié lors de la publication d’une solution, tous les documents de publication pour tous les projets entrent dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="9930e-168">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="9930e-169">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="9930e-169">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="9930e-170">La `true` valeur par défaut est si un identifiant de temps d’exécution est spécifié et que le projet est un projet exécutable (pas un projet de bibliothèque).</span><span class="sxs-lookup"><span data-stu-id="9930e-170">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="9930e-171">Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9930e-171">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="9930e-172">Si cette option est `true` utilisée `false`sans spécifier ou , la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="9930e-172">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="9930e-173">Dans ce cas, ne mettez pas la `--self-contained`solution `true` ou `false` l’argument du projet immédiatement après , parce que ou est attendu dans cette position.</span><span class="sxs-lookup"><span data-stu-id="9930e-173">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="9930e-174">Équivaut à `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="9930e-174">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="9930e-175">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9930e-175">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9930e-176">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="9930e-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="9930e-177">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9930e-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="9930e-178">Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="9930e-178">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9930e-179">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="9930e-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9930e-180">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9930e-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9930e-181">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="9930e-181">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="9930e-182">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="9930e-183">Exemples</span><span class="sxs-lookup"><span data-stu-id="9930e-183">Examples</span></span>

- <span data-ttu-id="9930e-184">Créez un [binaire multiplateforme dépendant du temps d’exécution](../deploying/index.md#produce-a-cross-platform-binary) pour le projet dans l’annuaire actuel :</span><span class="sxs-lookup"><span data-stu-id="9930e-184">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="9930e-185">En commençant par .NET Core 3.0 SDK, cet exemple crée également un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour la plate-forme actuelle.</span><span class="sxs-lookup"><span data-stu-id="9930e-185">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="9930e-186">Créez un [exécutable autonome](../deploying/index.md#publish-self-contained) pour le projet dans l’annuaire actuel, pour une durée de course spécifique :</span><span class="sxs-lookup"><span data-stu-id="9930e-186">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="9930e-187">Le RID doit être dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-187">The RID must be in the project file.</span></span>

- <span data-ttu-id="9930e-188">Créez un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour le projet dans l’annuaire actuel, pour une plate-forme spécifique :</span><span class="sxs-lookup"><span data-stu-id="9930e-188">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="9930e-189">Le RID doit être dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="9930e-189">The RID must be in the project file.</span></span> <span data-ttu-id="9930e-190">Cet exemple s’applique à .NET Core 3.0 SDK et aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="9930e-190">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="9930e-191">Publier le projet dans l’annuaire actuel, pour un cadre spécifique de temps d’exécution et de cible :</span><span class="sxs-lookup"><span data-stu-id="9930e-191">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="9930e-192">Publier le fichier de projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="9930e-192">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="9930e-193">Publiez l’application actuelle mais ne restaurez pas les références du projet au projet (P2P), juste le projet racine pendant l’opération de restauration :</span><span class="sxs-lookup"><span data-stu-id="9930e-193">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="9930e-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9930e-194">See also</span></span>

- [<span data-ttu-id="9930e-195">.NET Aperçu de publication d’applications de base</span><span class="sxs-lookup"><span data-stu-id="9930e-195">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="9930e-196">Publier des applications .NET Core avec le CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="9930e-196">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="9930e-197">Versions cibles de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9930e-197">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="9930e-198">Catalogue Runtime IDentifier (RID)</span><span class="sxs-lookup"><span data-stu-id="9930e-198">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="9930e-199">Travailler avec macOS Catalina Notarization</span><span class="sxs-lookup"><span data-stu-id="9930e-199">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="9930e-200">Structure d’annuaire d’une application publiée</span><span class="sxs-lookup"><span data-stu-id="9930e-200">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="9930e-201">Informations de référence sur la ligne de commande MSBuild</span><span class="sxs-lookup"><span data-stu-id="9930e-201">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="9930e-202">Visual Studio publie des profils (.pubxml) pour ASP.NET déploiement de l’application Core</span><span class="sxs-lookup"><span data-stu-id="9930e-202">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="9930e-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9930e-203">dotnet msbuild</span></span>](dotnet-msbuild.md)
