---
title: Commande dotnet run
description: La commande dotnet run fournit une option pratique pour exécuter votre application à partir du code source.
ms.date: 02/19/2020
ms.openlocfilehash: e442ed56d676ffd189ef6d394d840cea671c2dc6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157074"
---
# <a name="dotnet-run"></a><span data-ttu-id="21213-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="21213-103">dotnet run</span></span>

<span data-ttu-id="21213-104">**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="21213-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="21213-105">Nom</span><span class="sxs-lookup"><span data-stu-id="21213-105">Name</span></span>

<span data-ttu-id="21213-106">`dotnet run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.</span><span class="sxs-lookup"><span data-stu-id="21213-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="21213-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="21213-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile]
    [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project]
    [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

## <a name="description"></a><span data-ttu-id="21213-108">Description</span><span class="sxs-lookup"><span data-stu-id="21213-108">Description</span></span>

<span data-ttu-id="21213-109">La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="21213-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="21213-110">Elle est utile pour le développement itératif rapide en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="21213-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="21213-111">La commande dépend [`dotnet build`](dotnet-build.md) de la commande pour construire le code.</span><span class="sxs-lookup"><span data-stu-id="21213-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="21213-112">Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="21213-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="21213-113">Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="21213-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="21213-114">Par exemple, si vous avez une application `netcoreapp2.1` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="21213-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="21213-115">Les fichiers sont remplacés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="21213-115">Files are overwritten as needed.</span></span> <span data-ttu-id="21213-116">Les fichiers temporaires sont placés dans le répertoire `obj`.</span><span class="sxs-lookup"><span data-stu-id="21213-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="21213-117">Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.</span><span class="sxs-lookup"><span data-stu-id="21213-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="21213-118">La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="21213-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="21213-119">Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande.</span><span class="sxs-lookup"><span data-stu-id="21213-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="21213-120">Par exemple, pour exécuter `myapp.dll`, utilisez :</span><span class="sxs-lookup"><span data-stu-id="21213-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="21213-121">Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande (CLI) .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="21213-121">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="21213-122">Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="21213-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="21213-123">Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production.</span><span class="sxs-lookup"><span data-stu-id="21213-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="21213-124">[Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié.</span><span class="sxs-lookup"><span data-stu-id="21213-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="21213-125">Options</span><span class="sxs-lookup"><span data-stu-id="21213-125">Options</span></span>

- **`--`**

  <span data-ttu-id="21213-126">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="21213-126">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="21213-127">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="21213-127">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="21213-128">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="21213-128">Defines the build configuration.</span></span> <span data-ttu-id="21213-129">La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="21213-129">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="21213-130">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="21213-130">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="21213-131">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="21213-131">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="21213-132">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="21213-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="21213-133">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="21213-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="21213-134">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="21213-134">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="21213-135">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="21213-135">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="21213-136">Option disponible à partir du kit SDK .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="21213-136">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="21213-137">Nom du profil de lancement éventuel à utiliser au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="21213-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="21213-138">Les profils de lancement sont définis dans le fichier `Development` *launchSettings.json* et sont généralement appelés , `Staging`, et `Production`.</span><span class="sxs-lookup"><span data-stu-id="21213-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="21213-139">Pour plus d’informations, voir [Travailler avec plusieurs environnements](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="21213-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="21213-140">Ne génère pas le projet avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="21213-140">Doesn't build the project before running.</span></span> <span data-ttu-id="21213-141">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="21213-141">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="21213-142">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="21213-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="21213-143">N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="21213-143">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="21213-144">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="21213-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="21213-145">Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet).</span><span class="sxs-lookup"><span data-stu-id="21213-145">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="21213-146">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="21213-146">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="21213-147">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="21213-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="21213-148">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="21213-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="21213-149">`-r`option courte disponible depuis .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="21213-149">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="21213-150">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="21213-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="21213-151">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="21213-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="21213-152">La valeur par défaut est `m`.</span><span class="sxs-lookup"><span data-stu-id="21213-152">The default value is `m`.</span></span> <span data-ttu-id="21213-153">Disponible depuis .NET Core 2.1 SDK.</span><span class="sxs-lookup"><span data-stu-id="21213-153">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="21213-154">Exemples</span><span class="sxs-lookup"><span data-stu-id="21213-154">Examples</span></span>

- <span data-ttu-id="21213-155">Exécutez le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="21213-155">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="21213-156">Exécutez le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="21213-156">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="21213-157">Exécutez le projet dans le répertoire actuel (l’argument `--help` de cet exemple est passé à l’application, puisque l’option `--` vide est utilisée) :</span><span class="sxs-lookup"><span data-stu-id="21213-157">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="21213-158">Restaurer des dépendances et des outils pour le projet dans le répertoire actuel en montrant uniquement une sortie minimale, puis exécuter le projet : (SDK .NET Core 2.0 et ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="21213-158">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
