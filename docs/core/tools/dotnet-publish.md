---
title: Commande dotnet publish
description: La commande de publication dotnet publie un projet ou une solution .NET Core à un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: ca6b6bd0151674a81e0beee7798dc6bde9c088f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463469"
---
# <a name="dotnet-publish"></a><span data-ttu-id="a7beb-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a7beb-103">dotnet publish</span></span>

<span data-ttu-id="a7beb-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="a7beb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a7beb-105">Nom</span><span class="sxs-lookup"><span data-stu-id="a7beb-105">Name</span></span>

<span data-ttu-id="a7beb-106">`dotnet publish`- Publie l’application et ses dépendances à un dossier pour le déploiement dans un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="a7beb-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a7beb-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="a7beb-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun] [-p:PublishSingleFile] [-p:PublishTrimmed]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="a7beb-108">Description</span><span class="sxs-lookup"><span data-stu-id="a7beb-108">Description</span></span>

<span data-ttu-id="a7beb-109">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="a7beb-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="a7beb-110">La sortie inclut les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="a7beb-110">The output includes the following assets:</span></span>

- <span data-ttu-id="a7beb-111">Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.</span><span class="sxs-lookup"><span data-stu-id="a7beb-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="a7beb-112">Un fichier *.deps.json* qui comprend toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="a7beb-113">Un fichier *.runtimeconfig.json* qui spécifie le temps d’exécution partagé que l’application attend, ainsi que d’autres options de configuration pour le temps d’exécution (par exemple, type de collecte des ordures).</span><span class="sxs-lookup"><span data-stu-id="a7beb-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="a7beb-114">Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="a7beb-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="a7beb-115">La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a7beb-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="a7beb-116">Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement.</span><span class="sxs-lookup"><span data-stu-id="a7beb-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="a7beb-117">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="a7beb-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="a7beb-118">Pour plus d’informations, voir [Publier .NET Apps Core avec le CLI .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="a7beb-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="a7beb-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="a7beb-119">MSBuild</span></span>

<span data-ttu-id="a7beb-120">La commande `dotnet publish` appelle MSBuild, qui appelle la cible de `Publish`.</span><span class="sxs-lookup"><span data-stu-id="a7beb-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="a7beb-121">Les paramètres passés à `dotnet publish` sont passés à MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a7beb-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="a7beb-122">Les paramètres `-c` et `-o` correspondent aux propriétés `Configuration` et `OutputPath` de MSBuild, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a7beb-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="a7beb-123">La `dotnet publish` commande accepte les options MSBuild, telles que `-p` pour définir les propriétés et `-l` définir un bûcheron.</span><span class="sxs-lookup"><span data-stu-id="a7beb-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="a7beb-124">Par exemple, vous pouvez définir une propriété MSBuild en utilisant le format : `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="a7beb-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="a7beb-125">Vous pouvez également définir des propriétés liées à la publication en vous référant à un fichier *.pubxml,* par exemple :</span><span class="sxs-lookup"><span data-stu-id="a7beb-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="a7beb-126">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="a7beb-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="a7beb-127">Informations de référence sur la ligne de commande MSBuild</span><span class="sxs-lookup"><span data-stu-id="a7beb-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="a7beb-128">Visual Studio publie des profils (.pubxml) pour ASP.NET déploiement de l’application Core</span><span class="sxs-lookup"><span data-stu-id="a7beb-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="a7beb-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a7beb-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="a7beb-130">Arguments</span><span class="sxs-lookup"><span data-stu-id="a7beb-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="a7beb-131">Le projet ou la solution à publier.</span><span class="sxs-lookup"><span data-stu-id="a7beb-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="a7beb-132">`PROJECT`est le nom de voie et de fichier [d’un](csproj.md)fichier de projet de C, de F, ou de base visuelle, ou le chemin vers un répertoire qui contient un fichier de projet de C, de F, ou de base visuelle.</span><span class="sxs-lookup"><span data-stu-id="a7beb-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="a7beb-133">Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="a7beb-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="a7beb-134">`SOLUTION`est le chemin et le nom de fichier d’un fichier de solution *(extension .sln),* ou le chemin vers un répertoire qui contient un fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="a7beb-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="a7beb-135">Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="a7beb-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="a7beb-136">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="a7beb-137">Options</span><span class="sxs-lookup"><span data-stu-id="a7beb-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="a7beb-138">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="a7beb-138">Defines the build configuration.</span></span> <span data-ttu-id="a7beb-139">La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="a7beb-140">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="a7beb-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="a7beb-141">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="a7beb-142">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="a7beb-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a7beb-143">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="a7beb-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a7beb-144">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="a7beb-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="a7beb-145">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a7beb-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="a7beb-146">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="a7beb-146">For example, to complete authentication.</span></span> <span data-ttu-id="a7beb-147">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="a7beb-148">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="a7beb-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="a7beb-149">Le fichier manifeste fait partie [ `dotnet store` ](dotnet-store.md)de la sortie de la commande .</span><span class="sxs-lookup"><span data-stu-id="a7beb-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="a7beb-150">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="a7beb-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="a7beb-151">Ne génère pas le projet avant la publication.</span><span class="sxs-lookup"><span data-stu-id="a7beb-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="a7beb-152">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="a7beb-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="a7beb-153">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="a7beb-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="a7beb-154">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="a7beb-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="a7beb-155">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="a7beb-156">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="a7beb-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="a7beb-157">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="a7beb-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="a7beb-158">S’il n’est pas précisé, il ne fait pas défaut à *[project_file_folder]./bin/[configuration]/[cadre]/publier/* pour un délai exécutable et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="a7beb-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="a7beb-159">Il est par défaut à *[project_file_folder]/bin/[configuration]/[cadre]/[runtime]/publish/* pour un exécutable autonome.</span><span class="sxs-lookup"><span data-stu-id="a7beb-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="a7beb-160">Dans un projet Web, si le dossier de sortie `dotnet publish` se trouve dans le dossier du projet, les commandes successives entraînent des dossiers de sortie imbriqués.</span><span class="sxs-lookup"><span data-stu-id="a7beb-160">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="a7beb-161">Par exemple, si le dossier de projet est *monproject*, et le dossier `dotnet publish` de sortie de publication est *monproject/publier*, et vous exécutez deux fois, la deuxième exécution met des fichiers de contenu tels que *.config* et *.json* fichiers dans *monproject/ publier / publier*.</span><span class="sxs-lookup"><span data-stu-id="a7beb-161">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="a7beb-162">Pour éviter de nichant les dossiers de publication, spécifiez un dossier de publication qui n’est pas directement sous le dossier du projet, ou excluez le dossier de publication du projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-162">To avoid nesting publish folders, specify a publish folder that is not directly under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="a7beb-163">Pour exclure un dossier de publication nommé *publieurputput*, ajoutez l’élément suivant à un `PropertyGroup` élément dans le fichier *.csproj:*</span><span class="sxs-lookup"><span data-stu-id="a7beb-163">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="a7beb-164">.NET Core 3.x SDK et plus tard</span><span class="sxs-lookup"><span data-stu-id="a7beb-164">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="a7beb-165">Si un chemin relatif est spécifié lors de la publication d’un projet, l’annuaire de sortie généré est relatif à l’annuaire de travail actuel, et non à l’emplacement du fichier du projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-165">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="a7beb-166">Si un chemin relatif est spécifié lors de la publication d’une solution, toutes les sorties pour tous les projets entrent dans le dossier spécifié par rapport à l’annuaire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="a7beb-166">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="a7beb-167">Pour faire publier la sortie aller à des dossiers séparés pour chaque `PublishDir` projet, `--output` spécifier un chemin relatif en utilisant la propriété de msbuild au lieu de l’option.</span><span class="sxs-lookup"><span data-stu-id="a7beb-167">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="a7beb-168">Par exemple, `dotnet publish -p:PublishDir=.\publish` envoie la sortie `publish` de publication pour chaque projet à un dossier sous le dossier qui contient le fichier de projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-168">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="a7beb-169">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="a7beb-169">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="a7beb-170">Si un chemin relatif est spécifié lors de la publication d’un projet, l’annuaire de sortie généré est relatif à l’emplacement du fichier du projet, et non à l’annuaire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="a7beb-170">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="a7beb-171">Si un chemin relatif est spécifié lors de la publication d’une solution, la sortie de chaque projet est dans un dossier distinct par rapport à l’emplacement du fichier du projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-171">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="a7beb-172">Si un chemin absolu est spécifié lors de la publication d’une solution, tous les documents de publication pour tous les projets entrent dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="a7beb-172">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun`**

  <span data-ttu-id="a7beb-173">Compile les assemblages d’applications sous forme de format ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="a7beb-173">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="a7beb-174">R2R est une forme de compilation ahead-of-time (AOT).</span><span class="sxs-lookup"><span data-stu-id="a7beb-174">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="a7beb-175">Pour plus d’informations, voir [les images ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="a7beb-175">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="a7beb-176">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-176">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a7beb-177">Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a7beb-177">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="a7beb-178">Pour plus d’informations, consultez [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="a7beb-178">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile`**

  <span data-ttu-id="a7beb-179">Emballe l’application dans un fichier unique spécifique à une plate-forme exécutable.</span><span class="sxs-lookup"><span data-stu-id="a7beb-179">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="a7beb-180">L’exécutable est auto-extraction et contient toutes les dépendances (y compris indigène) qui sont nécessaires pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="a7beb-180">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="a7beb-181">Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build.</span><span class="sxs-lookup"><span data-stu-id="a7beb-181">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="a7beb-182">Le démarrage est plus rapide quand l’application est réexécutée.</span><span class="sxs-lookup"><span data-stu-id="a7beb-182">Startup is faster when the application is run again.</span></span> <span data-ttu-id="a7beb-183">L’application n’a pas besoin de s’extraire une deuxième fois à moins qu’une nouvelle version ne soit utilisée.</span><span class="sxs-lookup"><span data-stu-id="a7beb-183">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="a7beb-184">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-184">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a7beb-185">Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="a7beb-185">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="a7beb-186">Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a7beb-186">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="a7beb-187">Pour plus d’informations, consultez [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="a7beb-187">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed`**

  <span data-ttu-id="a7beb-188">Coupe les bibliothèques inutilisées pour réduire la taille du déploiement d’une application lors de la publication d’un exécutable autonome.</span><span class="sxs-lookup"><span data-stu-id="a7beb-188">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="a7beb-189">Pour plus d’informations, voir [Trim déploiements autonomes et exécutables](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="a7beb-189">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="a7beb-190">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-190">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="a7beb-191">Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a7beb-191">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="a7beb-192">Pour plus d’informations, consultez [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="a7beb-192">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="a7beb-193">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="a7beb-193">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="a7beb-194">La `true` valeur par défaut est si un identifiant de temps d’exécution est spécifié et que le projet est un projet exécutable (pas un projet de bibliothèque).</span><span class="sxs-lookup"><span data-stu-id="a7beb-194">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="a7beb-195">Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="a7beb-195">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="a7beb-196">Si cette option est `true` utilisée `false`sans spécifier ou , la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="a7beb-196">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="a7beb-197">Dans ce cas, ne mettez pas la `--self-contained`solution `true` ou `false` l’argument du projet immédiatement après , parce que ou est attendu dans cette position.</span><span class="sxs-lookup"><span data-stu-id="a7beb-197">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="a7beb-198">Équivaut à `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="a7beb-198">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="a7beb-199">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="a7beb-199">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="a7beb-200">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="a7beb-200">Publishes the application for a given runtime.</span></span> <span data-ttu-id="a7beb-201">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a7beb-201">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="a7beb-202">Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="a7beb-202">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a7beb-203">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="a7beb-203">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a7beb-204">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a7beb-204">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a7beb-205">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="a7beb-205">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="a7beb-206">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-206">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="a7beb-207">Exemples</span><span class="sxs-lookup"><span data-stu-id="a7beb-207">Examples</span></span>

- <span data-ttu-id="a7beb-208">Créez un [binaire multiplateforme dépendant du temps d’exécution](../deploying/index.md#produce-a-cross-platform-binary) pour le projet dans l’annuaire actuel :</span><span class="sxs-lookup"><span data-stu-id="a7beb-208">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="a7beb-209">En commençant par .NET Core 3.0 SDK, cet exemple crée également un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour la plate-forme actuelle.</span><span class="sxs-lookup"><span data-stu-id="a7beb-209">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="a7beb-210">Créez un [exécutable autonome](../deploying/index.md#publish-self-contained) pour le projet dans l’annuaire actuel, pour une durée de course spécifique :</span><span class="sxs-lookup"><span data-stu-id="a7beb-210">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="a7beb-211">Le RID doit être dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-211">The RID must be in the project file.</span></span>

- <span data-ttu-id="a7beb-212">Créez un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour le projet dans l’annuaire actuel, pour une plate-forme spécifique :</span><span class="sxs-lookup"><span data-stu-id="a7beb-212">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="a7beb-213">Le RID doit être dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="a7beb-213">The RID must be in the project file.</span></span> <span data-ttu-id="a7beb-214">Cet exemple s’applique à .NET Core 3.0 SDK et aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="a7beb-214">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="a7beb-215">Publier le projet dans l’annuaire actuel, pour un cadre spécifique de temps d’exécution et de cible :</span><span class="sxs-lookup"><span data-stu-id="a7beb-215">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="a7beb-216">Publier le fichier de projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="a7beb-216">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="a7beb-217">Publiez l’application actuelle mais ne restaurez pas les références du projet au projet (P2P), juste le projet racine pendant l’opération de restauration :</span><span class="sxs-lookup"><span data-stu-id="a7beb-217">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="a7beb-218">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7beb-218">See also</span></span>

- [<span data-ttu-id="a7beb-219">.NET Aperçu de publication d’applications de base</span><span class="sxs-lookup"><span data-stu-id="a7beb-219">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="a7beb-220">Publier des applications .NET Core avec le CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="a7beb-220">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="a7beb-221">Versions cibles de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a7beb-221">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="a7beb-222">Catalogue Runtime IDentifier (RID)</span><span class="sxs-lookup"><span data-stu-id="a7beb-222">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="a7beb-223">Travailler avec macOS Catalina Notarization</span><span class="sxs-lookup"><span data-stu-id="a7beb-223">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="a7beb-224">Structure d’annuaire d’une application publiée</span><span class="sxs-lookup"><span data-stu-id="a7beb-224">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="a7beb-225">Informations de référence sur la ligne de commande MSBuild</span><span class="sxs-lookup"><span data-stu-id="a7beb-225">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="a7beb-226">Visual Studio publie des profils (.pubxml) pour ASP.NET déploiement de l’application Core</span><span class="sxs-lookup"><span data-stu-id="a7beb-226">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="a7beb-227">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a7beb-227">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="a7beb-228">ILLInk.Tâches</span><span class="sxs-lookup"><span data-stu-id="a7beb-228">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
