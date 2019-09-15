---
title: Commande dotnet run
description: La commande dotnet run fournit une option pratique pour exécuter votre application à partir du code source.
ms.date: 05/29/2018
ms.openlocfilehash: b21987ef9ee4dd7d8fdb93d0853b7faa93001688
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969749"
---
# <a name="dotnet-run"></a><span data-ttu-id="2560e-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2560e-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2560e-104">Nom</span><span class="sxs-lookup"><span data-stu-id="2560e-104">Name</span></span>

<span data-ttu-id="2560e-105">`dotnet run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.</span><span class="sxs-lookup"><span data-stu-id="2560e-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2560e-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="2560e-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2560e-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2560e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2560e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2560e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2560e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2560e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="2560e-110">Description</span><span class="sxs-lookup"><span data-stu-id="2560e-110">Description</span></span>

<span data-ttu-id="2560e-111">La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="2560e-112">Elle est utile pour le développement itératif rapide en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="2560e-113">Elle dépend de la commande [`dotnet build`](dotnet-build.md) pour générer le code.</span><span class="sxs-lookup"><span data-stu-id="2560e-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="2560e-114">Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="2560e-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="2560e-115">Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="2560e-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="2560e-116">Par exemple, si vous avez une application `netcoreapp2.1` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="2560e-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="2560e-117">Les fichiers sont remplacés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2560e-117">Files are overwritten as needed.</span></span> <span data-ttu-id="2560e-118">Les fichiers temporaires sont placés dans le répertoire `obj`.</span><span class="sxs-lookup"><span data-stu-id="2560e-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="2560e-119">Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.</span><span class="sxs-lookup"><span data-stu-id="2560e-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="2560e-120">La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="2560e-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="2560e-121">Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="2560e-122">Par exemple, pour exécuter `myapp.dll`, utilisez :</span><span class="sxs-lookup"><span data-stu-id="2560e-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="2560e-123">Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande (CLI) .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="2560e-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="2560e-124">Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="2560e-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="2560e-125">Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production.</span><span class="sxs-lookup"><span data-stu-id="2560e-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="2560e-126">[Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié.</span><span class="sxs-lookup"><span data-stu-id="2560e-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="2560e-127">Options</span><span class="sxs-lookup"><span data-stu-id="2560e-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="2560e-128">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="2560e-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="2560e-129">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2560e-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="2560e-130">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="2560e-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2560e-131">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="2560e-131">Defines the build configuration.</span></span> <span data-ttu-id="2560e-132">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="2560e-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2560e-133">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="2560e-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2560e-134">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2560e-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="2560e-135">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="2560e-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2560e-136">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="2560e-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="2560e-137">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="2560e-138">Nom du profil de lancement éventuel à utiliser au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="2560e-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="2560e-139">Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`.</span><span class="sxs-lookup"><span data-stu-id="2560e-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="2560e-140">Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="2560e-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="2560e-141">Ne génère pas le projet avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2560e-141">Doesn't build the project before running.</span></span> <span data-ttu-id="2560e-142">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="2560e-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="2560e-143">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="2560e-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="2560e-144">N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="2560e-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="2560e-145">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="2560e-146">Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet).</span><span class="sxs-lookup"><span data-stu-id="2560e-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="2560e-147">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="2560e-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2560e-148">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="2560e-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="2560e-149">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2560e-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2560e-150">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2560e-151">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2560e-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="2560e-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2560e-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="2560e-153">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2560e-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="2560e-154">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="2560e-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2560e-155">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="2560e-155">Defines the build configuration.</span></span> <span data-ttu-id="2560e-156">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="2560e-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2560e-157">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="2560e-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2560e-158">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2560e-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="2560e-159">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="2560e-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="2560e-160">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="2560e-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="2560e-161">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="2560e-162">Nom du profil de lancement éventuel à utiliser au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="2560e-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="2560e-163">Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`.</span><span class="sxs-lookup"><span data-stu-id="2560e-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="2560e-164">Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="2560e-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="2560e-165">Ne génère pas le projet avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2560e-165">Doesn't build the project before running.</span></span> <span data-ttu-id="2560e-166">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="2560e-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="2560e-167">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="2560e-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="2560e-168">N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="2560e-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="2560e-169">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="2560e-170">Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet).</span><span class="sxs-lookup"><span data-stu-id="2560e-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="2560e-171">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="2560e-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="2560e-172">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="2560e-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="2560e-173">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="2560e-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="2560e-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="2560e-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="2560e-175">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2560e-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="2560e-176">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="2560e-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="2560e-177">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="2560e-177">Defines the build configuration.</span></span> <span data-ttu-id="2560e-178">La valeur par défaut est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="2560e-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="2560e-179">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="2560e-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="2560e-180">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2560e-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="2560e-181">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2560e-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="2560e-182">Spécifie le chemin d’accès et le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="2560e-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="2560e-183">(Voir la REMARQUE.) Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="2560e-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="2560e-184">Utilisez le chemin d’accès et le nom du fichier projet avec l’option `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="2560e-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="2560e-185">Une régression dans l’interface CLI empêche de fournir un chemin de dossier avec le SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="2560e-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="2560e-186">Pour plus d’informations sur ce problème, consultez la page [dotnet run -p, impossible de démarrer un projet (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="2560e-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="2560e-187">Exemples</span><span class="sxs-lookup"><span data-stu-id="2560e-187">Examples</span></span>

<span data-ttu-id="2560e-188">Exécutez le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="2560e-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="2560e-189">Exécutez le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="2560e-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="2560e-190">Exécutez le projet dans le répertoire actuel (l’argument `--help` de cet exemple est passé à l’application, puisque l’option `--` vide est utilisée) :</span><span class="sxs-lookup"><span data-stu-id="2560e-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="2560e-191">Restaurer des dépendances et des outils pour le projet dans le répertoire actuel en montrant uniquement une sortie minimale, puis exécuter le projet : (SDK .NET Core 2.0 et ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="2560e-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
