---
title: Commande dotnet publish
description: La commande de publication dotnet publie un projet ou une solution .NET Core à un répertoire.
ms.date: 02/24/2020
ms.openlocfilehash: c34618409c9a539043c84c7e03daa8aa249d64f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146553"
---
# <a name="dotnet-publish"></a><span data-ttu-id="bc30d-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="bc30d-103">dotnet publish</span></span>

<span data-ttu-id="bc30d-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bc30d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bc30d-105">Nom</span><span class="sxs-lookup"><span data-stu-id="bc30d-105">Name</span></span>

<span data-ttu-id="bc30d-106">`dotnet publish`- Publie l’application et ses dépendances à un dossier pour le déploiement dans un système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="bc30d-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bc30d-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bc30d-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="bc30d-108">Description</span><span class="sxs-lookup"><span data-stu-id="bc30d-108">Description</span></span>

<span data-ttu-id="bc30d-109">`dotnet publish` compile l’application, parcourt ses dépendances spécifiées dans le fichier projet et publie l’ensemble de fichiers obtenus dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="bc30d-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="bc30d-110">La sortie inclut les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="bc30d-110">The output includes the following assets:</span></span>

- <span data-ttu-id="bc30d-111">Le code de langage intermédiaire (IL) dans un assembly avec l’extension *dll*.</span><span class="sxs-lookup"><span data-stu-id="bc30d-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="bc30d-112">Un fichier *.deps.json* qui comprend toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="bc30d-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="bc30d-113">Un fichier *.runtimeconfig.json* qui spécifie le temps d’exécution partagé que l’application attend, ainsi que d’autres options de configuration pour le temps d’exécution (par exemple, type de collecte des ordures).</span><span class="sxs-lookup"><span data-stu-id="bc30d-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="bc30d-114">Les dépendances de l’application, qui sont copiées à partir du cache NuGet dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="bc30d-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="bc30d-115">La sortie de la commande `dotnet publish` est prête pour le déploiement sur un système d’hébergement (par exemple, un serveur, PC, Mac, ordinateur portable) à des fins d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bc30d-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="bc30d-116">Il s’agit de la seule façon officiellement prise en charge pour préparer l’application au déploiement.</span><span class="sxs-lookup"><span data-stu-id="bc30d-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="bc30d-117">En fonction du type de déploiement que spécifie le projet, le runtime .NET Core partagé peut ou non être installé sur le système d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="bc30d-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="bc30d-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="bc30d-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="bc30d-119">Le projet ou la solution à publier.</span><span class="sxs-lookup"><span data-stu-id="bc30d-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="bc30d-120">`PROJECT`est le nom de voie et de fichier [d’un](csproj.md)fichier de projet de C, de F, ou de base visuelle, ou le chemin vers un répertoire qui contient un fichier de projet de C, de F, ou de base visuelle.</span><span class="sxs-lookup"><span data-stu-id="bc30d-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="bc30d-121">Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="bc30d-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="bc30d-122">`SOLUTION`est le chemin et le nom de fichier d’un fichier de solution *(extension .sln),* ou le chemin vers un répertoire qui contient un fichier de solution.</span><span class="sxs-lookup"><span data-stu-id="bc30d-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="bc30d-123">Si l’annuaire n’est pas spécifié, il est par défaut à l’annuaire actuel.</span><span class="sxs-lookup"><span data-stu-id="bc30d-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="bc30d-124">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc30d-124">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="bc30d-125">Options</span><span class="sxs-lookup"><span data-stu-id="bc30d-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="bc30d-126">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="bc30d-126">Defines the build configuration.</span></span> <span data-ttu-id="bc30d-127">La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="bc30d-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bc30d-128">Publie l’application pour le [framework cible](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="bc30d-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="bc30d-129">Le framework cible doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="bc30d-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="bc30d-130">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="bc30d-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="bc30d-131">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="bc30d-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bc30d-132">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="bc30d-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="bc30d-133">Permet à la commande de s’arrêter et d’attendre une action ou une entrée utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bc30d-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="bc30d-134">Par exemple, pour effectuer une authentification.</span><span class="sxs-lookup"><span data-stu-id="bc30d-134">For example, to complete authentication.</span></span> <span data-ttu-id="bc30d-135">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc30d-135">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="bc30d-136">Spécifie un ou plusieurs [manifestes cibles](../deploying/runtime-store.md) à utiliser pour épurer l’ensemble des packages publiés avec l’application.</span><span class="sxs-lookup"><span data-stu-id="bc30d-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="bc30d-137">Le fichier manifeste fait partie [ `dotnet store` ](dotnet-store.md)de la sortie de la commande .</span><span class="sxs-lookup"><span data-stu-id="bc30d-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="bc30d-138">Pour spécifier plusieurs manifestes, ajoutez une option `--manifest` pour chaque manifeste.</span><span class="sxs-lookup"><span data-stu-id="bc30d-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="bc30d-139">Ne génère pas le projet avant la publication.</span><span class="sxs-lookup"><span data-stu-id="bc30d-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="bc30d-140">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="bc30d-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="bc30d-141">Ignore les références entre projets et restaure uniquement le projet racine.</span><span class="sxs-lookup"><span data-stu-id="bc30d-141">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="bc30d-142">N’affiche pas la bannière de démarrage ni le message de copyright.</span><span class="sxs-lookup"><span data-stu-id="bc30d-142">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="bc30d-143">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc30d-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bc30d-144">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="bc30d-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bc30d-145">Spécifie le chemin d’accès du répertoire de sortie.</span><span class="sxs-lookup"><span data-stu-id="bc30d-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="bc30d-146">S’il n’est pas précisé, il ne fait pas défaut à *./bin/[configuration]/[cadre]/publier/* pour un délai exécutable et multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="bc30d-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="bc30d-147">Il ne fait pas défaut à *./bin/[configuration]/[cadre]/[runtime]/publish/* pour un exécutable autonome.</span><span class="sxs-lookup"><span data-stu-id="bc30d-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="bc30d-148">Si le chemin est relatif, le répertoire de sortie généré est relatif à l’emplacement du fichier projet, et non au répertoire de travail actuel.</span><span class="sxs-lookup"><span data-stu-id="bc30d-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="bc30d-149">Publie le runtime .NET Core avec votre application ; ainsi, vous n’avez pas besoin d’installer le runtime sur l’ordinateur cible.</span><span class="sxs-lookup"><span data-stu-id="bc30d-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="bc30d-150">Par `true` défaut, si un identifiant de temps d’exécution est spécifié.</span><span class="sxs-lookup"><span data-stu-id="bc30d-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="bc30d-151">Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="bc30d-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="bc30d-152">Équivaut à `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="bc30d-152">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="bc30d-153">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bc30d-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="bc30d-154">Publie l’application pour un runtime donné.</span><span class="sxs-lookup"><span data-stu-id="bc30d-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="bc30d-155">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="bc30d-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="bc30d-156">Pour plus d’informations, voir [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="bc30d-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bc30d-157">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="bc30d-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bc30d-158">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bc30d-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="bc30d-159">La valeur par défaut est `minimal`.</span><span class="sxs-lookup"><span data-stu-id="bc30d-159">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="bc30d-160">Définit le suffixe de version qui remplace l’astérisque (`*`) dans le champ de version du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="bc30d-160">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="bc30d-161">Exemples</span><span class="sxs-lookup"><span data-stu-id="bc30d-161">Examples</span></span>

- <span data-ttu-id="bc30d-162">Créez un [binaire multiplateforme dépendant du temps d’exécution](../deploying/index.md#produce-a-cross-platform-binary) pour le projet dans l’annuaire actuel :</span><span class="sxs-lookup"><span data-stu-id="bc30d-162">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="bc30d-163">En commençant par .NET Core 3.0 SDK, cet exemple crée également un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour la plate-forme actuelle.</span><span class="sxs-lookup"><span data-stu-id="bc30d-163">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="bc30d-164">Créez un [exécutable autonome](../deploying/index.md#publish-self-contained) pour le projet dans l’annuaire actuel, pour une durée de course spécifique :</span><span class="sxs-lookup"><span data-stu-id="bc30d-164">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="bc30d-165">Le RID doit être dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="bc30d-165">The RID must be in the project file.</span></span>

- <span data-ttu-id="bc30d-166">Créez un [runtime-dépendant exécutable](../deploying/index.md#publish-runtime-dependent) pour le projet dans l’annuaire actuel, pour une plate-forme spécifique :</span><span class="sxs-lookup"><span data-stu-id="bc30d-166">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="bc30d-167">Le RID doit être dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="bc30d-167">The RID must be in the project file.</span></span> <span data-ttu-id="bc30d-168">Cet exemple s’applique à .NET Core 3.0 SDK et aux versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="bc30d-168">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="bc30d-169">Publier le projet dans l’annuaire actuel, pour un cadre spécifique de temps d’exécution et de cible :</span><span class="sxs-lookup"><span data-stu-id="bc30d-169">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="bc30d-170">Publier le fichier de projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="bc30d-170">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="bc30d-171">Publiez l’application actuelle mais ne restaurez pas les références du projet au projet (P2P), juste le projet racine pendant l’opération de restauration :</span><span class="sxs-lookup"><span data-stu-id="bc30d-171">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="bc30d-172">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc30d-172">See also</span></span>

- [<span data-ttu-id="bc30d-173">.NET Aperçu de publication d’applications de base</span><span class="sxs-lookup"><span data-stu-id="bc30d-173">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="bc30d-174">Publier des applications .NET Core avec le CLI core .NET</span><span class="sxs-lookup"><span data-stu-id="bc30d-174">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="bc30d-175">Cadres cibles</span><span class="sxs-lookup"><span data-stu-id="bc30d-175">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="bc30d-176">Catalogue Runtime IDentifier (RID)</span><span class="sxs-lookup"><span data-stu-id="bc30d-176">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="bc30d-177">[Travailler avec macOS Catalina Notarization](../install/macos-notarization-issues.md) Pour plus d’informations, voir qu’il suit les ressources :</span><span class="sxs-lookup"><span data-stu-id="bc30d-177">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="bc30d-178">Structure d’annuaire d’une application publiée</span><span class="sxs-lookup"><span data-stu-id="bc30d-178">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
