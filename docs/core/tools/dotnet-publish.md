---
title: Commande dotnet publish
description: La commande dotnet publish publie un projet ou une solution .NET Core dans un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: 59fdbfa875dad13963ae198acc6a31b537279dfe
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251177"
---
# <a name="dotnet-publish"></a><span data-ttu-id="6483a-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6483a-103">dotnet publish</span></span>

<span data-ttu-id="6483a-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6483a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6483a-105">Nom</span><span class="sxs-lookup"><span data-stu-id="6483a-105">Name</span></span>

<span data-ttu-id="6483a-106">`dotnet publish`-Publie l’application et ses dépendances dans un dossier pour le déploiement sur un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="6483a-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6483a-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="6483a-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="6483a-108">Description</span><span class="sxs-lookup"><span data-stu-id="6483a-108">Description</span></span>

<span data-ttu-id="6483a-109">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="6483a-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="6483a-110">La sortie inclut les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="6483a-110">The output includes the following assets:</span></span>

- <span data-ttu-id="6483a-111">Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.</span><span class="sxs-lookup"><span data-stu-id="6483a-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="6483a-112">*.deps.jssur* un fichier qui comprend toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="6483a-113">*.runtimeconfig.jssur* un fichier qui spécifie le runtime partagé attendu par l’application, ainsi que d’autres options de configuration pour le runtime (par exemple, garbage collection type).</span><span class="sxs-lookup"><span data-stu-id="6483a-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="6483a-114">Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="6483a-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="6483a-115">La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6483a-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="6483a-116">Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement.</span><span class="sxs-lookup"><span data-stu-id="6483a-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="6483a-117">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="6483a-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="6483a-118">Pour plus d’informations, consultez [publier des applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="6483a-119">Restauration implicite</span><span class="sxs-lookup"><span data-stu-id="6483a-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="6483a-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="6483a-120">MSBuild</span></span>

<span data-ttu-id="6483a-121">La commande `dotnet publish` appelle MSBuild, qui appelle la cible de `Publish`.</span><span class="sxs-lookup"><span data-stu-id="6483a-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="6483a-122">Les paramètres passés à `dotnet publish` sont passés à MSBuild.</span><span class="sxs-lookup"><span data-stu-id="6483a-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="6483a-123">Les paramètres `-c` et `-o` correspondent aux propriétés `Configuration` et `PublishDir` de MSBuild, respectivement.</span><span class="sxs-lookup"><span data-stu-id="6483a-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="6483a-124">La `dotnet publish` commande accepte les options MSBuild, comme `-p` pour définir des propriétés et `-l` pour définir un enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="6483a-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="6483a-125">Par exemple, vous pouvez définir une propriété MSBuild en utilisant le format : `-p:<NAME>=<VALUE>` .</span><span class="sxs-lookup"><span data-stu-id="6483a-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="6483a-126">Vous pouvez également définir des propriétés relatives à la publication en faisant référence à un fichier *. pubxml* , par exemple :</span><span class="sxs-lookup"><span data-stu-id="6483a-126">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="6483a-127">L’exemple précédent utilise le fichier *FolderProfile. pubxml* qui se trouve dans le dossier \* \<project_folder> /Properties/PublishProfiles\* .</span><span class="sxs-lookup"><span data-stu-id="6483a-127">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="6483a-128">Si vous spécifiez un chemin d’accès et une extension de fichier lors de la définition de la `PublishProfile` propriété, ils sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="6483a-128">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="6483a-129">MSBuild par défaut examine le dossier *Properties/PublishProfiles* et suppose l’extension de fichier *pubxml* .</span><span class="sxs-lookup"><span data-stu-id="6483a-129">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="6483a-130">Pour spécifier le chemin d’accès et le nom de fichier, y compris l’extension, définissez la propriété à la `PublishProfileFullPath` place de la `PublishProfile` propriété.</span><span class="sxs-lookup"><span data-stu-id="6483a-130">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="6483a-131">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="6483a-131">For more information, see the following resources:</span></span>

- [<span data-ttu-id="6483a-132">Informations de référence sur la ligne de commande MSBuild</span><span class="sxs-lookup"><span data-stu-id="6483a-132">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="6483a-133">Profils de publication Visual Studio (. pubxml) pour le déploiement d’applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6483a-133">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="6483a-134">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="6483a-134">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="6483a-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="6483a-135">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="6483a-136">Projet ou solution à publier.</span><span class="sxs-lookup"><span data-stu-id="6483a-136">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="6483a-137">`PROJECT`est le chemin d’accès et le nom de fichier d’un fichier projet [c#](csproj.md), f # ou Visual Basic, ou le chemin d’accès à un répertoire qui contient un fichier projet C#, f # ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6483a-137">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="6483a-138">Si le répertoire n’est pas spécifié, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="6483a-138">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="6483a-139">`SOLUTION`est le chemin d’accès et le nom de fichier d’un fichier solution (extension *. sln* ), ou le chemin d’accès à un répertoire qui contient un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="6483a-139">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="6483a-140">Si le répertoire n’est pas spécifié, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="6483a-140">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="6483a-141">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-141">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="6483a-142">Options</span><span class="sxs-lookup"><span data-stu-id="6483a-142">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="6483a-143">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="6483a-143">Defines the build configuration.</span></span> <span data-ttu-id="6483a-144">La valeur par défaut pour la plupart des projets est `Debug` , mais vous pouvez remplacer les paramètres de configuration de build dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-144">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="6483a-145">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="6483a-145">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6483a-146">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-146">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="6483a-147">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="6483a-147">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6483a-148">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="6483a-148">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6483a-149">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="6483a-149">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="6483a-150">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6483a-150">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="6483a-151">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="6483a-151">For example, to complete authentication.</span></span> <span data-ttu-id="6483a-152">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-152">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="6483a-153">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="6483a-153">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="6483a-154">Le fichier manifeste fait partie de la sortie de la [ `dotnet store` commande](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-154">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="6483a-155">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="6483a-155">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="6483a-156">Ne génère pas le projet avant la publication.</span><span class="sxs-lookup"><span data-stu-id="6483a-156">Doesn't build the project before publishing.</span></span> <span data-ttu-id="6483a-157">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="6483a-157">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="6483a-158">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="6483a-158">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="6483a-159">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="6483a-159">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="6483a-160">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-160">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="6483a-161">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="6483a-161">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="6483a-162">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="6483a-162">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="6483a-163">S’il n’est pas spécifié, la valeur par défaut est *[project_file_folder]./bin/[Configuration]/[Framework]/Publish/* pour un exécutable dépendant du runtime et des binaires multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="6483a-163">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="6483a-164">La valeur par défaut est *[project_file_folder]/bin/[Configuration]/[Framework]/[Runtime]/Publish/* pour un exécutable autonome.</span><span class="sxs-lookup"><span data-stu-id="6483a-164">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="6483a-165">Dans un projet Web, si le dossier de sortie se trouve dans le dossier du projet, les commandes successives `dotnet publish` génèrent des dossiers de sortie imbriqués.</span><span class="sxs-lookup"><span data-stu-id="6483a-165">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="6483a-166">Par exemple, si le dossier du projet est *MyProject*et que le dossier de sortie de publication est *MyProject/Publish*, et que vous exécutez `dotnet publish` deux fois, la deuxième exécution place les fichiers de contenu, tels que les fichiers *. config* et *. JSON* dans *MyProject/Publish/Publish*.</span><span class="sxs-lookup"><span data-stu-id="6483a-166">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="6483a-167">Pour éviter d’imbriquer des dossiers de publication, spécifiez un dossier de publication qui ne se trouve pas **directement** sous le dossier du projet, ou excluez le dossier de publication du projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-167">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="6483a-168">Pour exclure un dossier de publication nommé *publishoutput*, ajoutez l’élément suivant à un `PropertyGroup` élément dans le fichier *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="6483a-168">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="6483a-169">Kit de développement logiciel (SDK) .NET Core 3. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="6483a-169">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="6483a-170">Si un chemin d’accès relatif est spécifié lors de la publication d’un projet, le répertoire de sortie généré est relatif au répertoire de travail actuel, et non à l’emplacement du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-170">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="6483a-171">Si un chemin d’accès relatif est spécifié lors de la publication d’une solution, toutes les sorties de tous les projets sont placées dans le dossier spécifié par rapport au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="6483a-171">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="6483a-172">Pour que la sortie de publication passe à des dossiers distincts pour chaque projet, spécifiez un chemin d’accès relatif à l’aide `PublishDir` de la propriété MSBuild au lieu de l' `--output` option.</span><span class="sxs-lookup"><span data-stu-id="6483a-172">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="6483a-173">Par exemple, `dotnet publish -p:PublishDir=.\publish` envoie la sortie de publication pour chaque projet dans un `publish` dossier sous le dossier qui contient le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-173">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="6483a-174">Kit de développement logiciel (SDK) .NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="6483a-174">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="6483a-175">Si un chemin d’accès relatif est spécifié lors de la publication d’un projet, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="6483a-175">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="6483a-176">Si un chemin d’accès relatif est spécifié lors de la publication d’une solution, la sortie de chaque projet passe dans un dossier distinct relatif à l’emplacement du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-176">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="6483a-177">Si un chemin d’accès absolu est spécifié lors de la publication d’une solution, toutes les sorties de publication de tous les projets sont placées dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="6483a-177">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="6483a-178">Compile les assemblys d’application au format ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="6483a-178">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="6483a-179">R2R est une forme de compilation ahead-of-time (AOT).</span><span class="sxs-lookup"><span data-stu-id="6483a-179">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="6483a-180">Pour plus d’informations, consultez [images ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="6483a-180">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="6483a-181">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-181">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6483a-182">Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="6483a-182">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="6483a-183">Pour plus d’informations, consultez [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="6483a-183">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="6483a-184">Empaquette l’application dans un exécutable à fichier unique spécifique à la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6483a-184">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="6483a-185">L’exécutable est auto-extractible et contient toutes les dépendances (y compris native) requises pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="6483a-185">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="6483a-186">Lors de la première exécution de l’application, celle-ci est extraite d’un répertoire basé sur le nom de l’application et l’identificateur de la build.</span><span class="sxs-lookup"><span data-stu-id="6483a-186">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="6483a-187">Le démarrage est plus rapide quand l’application est réexécutée.</span><span class="sxs-lookup"><span data-stu-id="6483a-187">Startup is faster when the application is run again.</span></span> <span data-ttu-id="6483a-188">L’application n’a pas besoin de s’extraire elle-même une deuxième fois, sauf si une nouvelle version est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6483a-188">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="6483a-189">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-189">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6483a-190">Pour plus d’informations sur la publication monofichier, consultez le [document conceptuel sur l’outil de regroupement monofichier](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-190">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="6483a-191">Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="6483a-191">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="6483a-192">Pour plus d’informations, consultez [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="6483a-192">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="6483a-193">Supprime les bibliothèques inutilisées pour réduire la taille du déploiement d’une application lors de la publication d’un fichier exécutable autonome.</span><span class="sxs-lookup"><span data-stu-id="6483a-193">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="6483a-194">Pour plus d’informations, consultez [Trim self-contained Deployments and executed](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-194">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="6483a-195">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-195">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="6483a-196">Nous vous recommandons de spécifier cette option dans un profil de publication plutôt que sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="6483a-196">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="6483a-197">Pour plus d’informations, consultez [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="6483a-197">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="6483a-198">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="6483a-198">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="6483a-199">La valeur par défaut est `true` si un identificateur de Runtime est spécifié et que le projet est un projet exécutable (pas un projet de bibliothèque).</span><span class="sxs-lookup"><span data-stu-id="6483a-199">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="6483a-200">Pour plus d’informations, consultez [publication d’applications .net Core](../deploying/index.md) et [publication d’applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-200">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="6483a-201">Si cette option est utilisée sans spécifier `true` ou `false` , la valeur par défaut est `true` .</span><span class="sxs-lookup"><span data-stu-id="6483a-201">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="6483a-202">Dans ce cas, ne placez pas l’argument solution ou Project immédiatement après `--self-contained` , car `true` ou `false` est attendu dans cette position.</span><span class="sxs-lookup"><span data-stu-id="6483a-202">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="6483a-203">Équivaut à `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="6483a-203">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="6483a-204">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="6483a-204">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="6483a-205">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="6483a-205">Publishes the application for a given runtime.</span></span> <span data-ttu-id="6483a-206">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-206">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="6483a-207">Pour plus d’informations, consultez [publication d’applications .net Core](../deploying/index.md) et [publication d’applications .net core avec le CLI .net Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="6483a-207">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6483a-208">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="6483a-208">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6483a-209">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6483a-209">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="6483a-210">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="6483a-210">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="6483a-211">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-211">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="6483a-212">Exemples</span><span class="sxs-lookup"><span data-stu-id="6483a-212">Examples</span></span>

- <span data-ttu-id="6483a-213">Créez un [binaire multiplateforme dépendant du runtime](../deploying/index.md#produce-a-cross-platform-binary) pour le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="6483a-213">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="6483a-214">À compter du kit de développement logiciel (SDK) .NET Core 3,0, cet exemple crée également un [exécutable dépendant du runtime](../deploying/index.md#publish-runtime-dependent) pour la plateforme actuelle.</span><span class="sxs-lookup"><span data-stu-id="6483a-214">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="6483a-215">Créer un [exécutable autonome](../deploying/index.md#publish-self-contained) pour le projet dans le répertoire actif, pour un Runtime spécifique :</span><span class="sxs-lookup"><span data-stu-id="6483a-215">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="6483a-216">Le RID doit se trouver dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-216">The RID must be in the project file.</span></span>

- <span data-ttu-id="6483a-217">Créez un [exécutable dépendant du runtime](../deploying/index.md#publish-runtime-dependent) pour le projet dans le répertoire actif, pour une plateforme spécifique :</span><span class="sxs-lookup"><span data-stu-id="6483a-217">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="6483a-218">Le RID doit se trouver dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="6483a-218">The RID must be in the project file.</span></span> <span data-ttu-id="6483a-219">Cet exemple s’applique au kit de développement logiciel (SDK) .NET Core 3,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="6483a-219">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="6483a-220">Publiez le projet dans le répertoire actif, pour un Runtime spécifique et une version cible du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="6483a-220">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="6483a-221">Publier le fichier projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="6483a-221">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="6483a-222">Publier l’application actuelle, mais ne pas restaurer les références entre projets (P2P), uniquement le projet racine pendant l’opération de restauration :</span><span class="sxs-lookup"><span data-stu-id="6483a-222">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="6483a-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6483a-223">See also</span></span>

- [<span data-ttu-id="6483a-224">Vue d’ensemble de la publication d’applications .NET Core</span><span class="sxs-lookup"><span data-stu-id="6483a-224">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="6483a-225">Publier des applications .NET Core avec le CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="6483a-225">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="6483a-226">Frameworks cibles</span><span class="sxs-lookup"><span data-stu-id="6483a-226">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="6483a-227">Catalogue des identificateurs de Runtime (RID)</span><span class="sxs-lookup"><span data-stu-id="6483a-227">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="6483a-228">Utilisation de la notaire Catalina macOS</span><span class="sxs-lookup"><span data-stu-id="6483a-228">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="6483a-229">Structure de répertoires d’une application publiée</span><span class="sxs-lookup"><span data-stu-id="6483a-229">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="6483a-230">Informations de référence sur la ligne de commande MSBuild</span><span class="sxs-lookup"><span data-stu-id="6483a-230">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="6483a-231">Profils de publication Visual Studio (. pubxml) pour le déploiement d’applications ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6483a-231">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="6483a-232">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="6483a-232">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="6483a-233">ILLInk. Tasks</span><span class="sxs-lookup"><span data-stu-id="6483a-233">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
