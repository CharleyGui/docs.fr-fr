---
title: Commande dotnet run
description: La commande dotnet run fournit une option pratique pour exécuter votre application à partir du code source.
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734103"
---
# <a name="dotnet-run"></a><span data-ttu-id="80610-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="80610-103">dotnet run</span></span>

<span data-ttu-id="80610-104">**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="80610-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="80610-105">Nom</span><span class="sxs-lookup"><span data-stu-id="80610-105">Name</span></span>

<span data-ttu-id="80610-106">`dotnet run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.</span><span class="sxs-lookup"><span data-stu-id="80610-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="80610-107">Résumé</span><span class="sxs-lookup"><span data-stu-id="80610-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="80610-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="80610-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="80610-109">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="80610-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="80610-110">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="80610-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="80610-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="80610-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="80610-112">Description</span><span class="sxs-lookup"><span data-stu-id="80610-112">Description</span></span>

<span data-ttu-id="80610-113">La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande.</span><span class="sxs-lookup"><span data-stu-id="80610-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="80610-114">Elle est utile pour le développement itératif rapide en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="80610-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="80610-115">Elle dépend de la commande [`dotnet build`](dotnet-build.md) pour générer le code.</span><span class="sxs-lookup"><span data-stu-id="80610-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="80610-116">Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="80610-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="80610-117">Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="80610-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="80610-118">Par exemple, si vous avez une application `netcoreapp2.1` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="80610-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="80610-119">Les fichiers sont remplacés, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="80610-119">Files are overwritten as needed.</span></span> <span data-ttu-id="80610-120">Les fichiers temporaires sont placés dans le répertoire `obj`.</span><span class="sxs-lookup"><span data-stu-id="80610-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="80610-121">Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.</span><span class="sxs-lookup"><span data-stu-id="80610-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="80610-122">La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés.</span><span class="sxs-lookup"><span data-stu-id="80610-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="80610-123">Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande.</span><span class="sxs-lookup"><span data-stu-id="80610-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="80610-124">Par exemple, pour exécuter `myapp.dll`, utilisez :</span><span class="sxs-lookup"><span data-stu-id="80610-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="80610-125">Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande (CLI) .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="80610-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="80610-126">Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet.</span><span class="sxs-lookup"><span data-stu-id="80610-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="80610-127">Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production.</span><span class="sxs-lookup"><span data-stu-id="80610-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="80610-128">[Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié.</span><span class="sxs-lookup"><span data-stu-id="80610-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="80610-129">Options</span><span class="sxs-lookup"><span data-stu-id="80610-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="80610-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="80610-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="80610-131">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="80610-132">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="80610-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="80610-133">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="80610-133">Defines the build configuration.</span></span> <span data-ttu-id="80610-134">La valeur par défaut de la plupart des projets est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="80610-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="80610-135">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="80610-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="80610-136">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="80610-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="80610-137">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="80610-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="80610-138">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="80610-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="80610-139">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="80610-140">Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).</span><span class="sxs-lookup"><span data-stu-id="80610-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="80610-141">Nom du profil de lancement éventuel à utiliser au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="80610-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="80610-142">Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`.</span><span class="sxs-lookup"><span data-stu-id="80610-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="80610-143">Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="80610-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="80610-144">Ne génère pas le projet avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-144">Doesn't build the project before running.</span></span> <span data-ttu-id="80610-145">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="80610-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="80610-146">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="80610-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="80610-147">N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="80610-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="80610-148">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="80610-149">Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet).</span><span class="sxs-lookup"><span data-stu-id="80610-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="80610-150">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="80610-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="80610-151">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="80610-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="80610-152">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="80610-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="80610-153">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="80610-154">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="80610-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="80610-155">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="80610-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="80610-156">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="80610-157">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="80610-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="80610-158">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="80610-158">Defines the build configuration.</span></span> <span data-ttu-id="80610-159">La valeur par défaut de la plupart des projets est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="80610-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="80610-160">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="80610-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="80610-161">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="80610-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="80610-162">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="80610-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="80610-163">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="80610-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="80610-164">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="80610-165">Nom du profil de lancement éventuel à utiliser au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="80610-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="80610-166">Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`.</span><span class="sxs-lookup"><span data-stu-id="80610-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="80610-167">Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="80610-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="80610-168">Ne génère pas le projet avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-168">Doesn't build the project before running.</span></span> <span data-ttu-id="80610-169">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="80610-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="80610-170">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="80610-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="80610-171">N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="80610-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="80610-172">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="80610-173">Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet).</span><span class="sxs-lookup"><span data-stu-id="80610-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="80610-174">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="80610-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="80610-175">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="80610-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="80610-176">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="80610-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="80610-177">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="80610-178">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="80610-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="80610-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="80610-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="80610-180">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="80610-181">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="80610-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="80610-182">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="80610-182">Defines the build configuration.</span></span> <span data-ttu-id="80610-183">La valeur par défaut de la plupart des projets est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="80610-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="80610-184">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="80610-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="80610-185">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="80610-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="80610-186">Force la résolution de toutes les dépendances même si la dernière restauration a réussi.</span><span class="sxs-lookup"><span data-stu-id="80610-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="80610-187">Définir cet indicateur revient à supprimer le fichier *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="80610-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="80610-188">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="80610-189">Nom du profil de lancement éventuel à utiliser au lancement de l’application.</span><span class="sxs-lookup"><span data-stu-id="80610-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="80610-190">Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`.</span><span class="sxs-lookup"><span data-stu-id="80610-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="80610-191">Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="80610-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="80610-192">Ne génère pas le projet avant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-192">Doesn't build the project before running.</span></span> <span data-ttu-id="80610-193">L’indicateur `--no-restore` est également défini implicitement.</span><span class="sxs-lookup"><span data-stu-id="80610-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="80610-194">En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.</span><span class="sxs-lookup"><span data-stu-id="80610-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="80610-195">N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.</span><span class="sxs-lookup"><span data-stu-id="80610-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="80610-196">N’effectue pas de restauration implicite à l’exécution de la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="80610-197">Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet).</span><span class="sxs-lookup"><span data-stu-id="80610-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="80610-198">Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="80610-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="80610-199">Spécifie le runtime cible pour lequel restaurer les packages.</span><span class="sxs-lookup"><span data-stu-id="80610-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="80610-200">Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="80610-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="80610-201">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="80610-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="80610-202">Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="80610-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="80610-203">Tous les arguments après ce délimiteur sont passés à l’application exécutée.</span><span class="sxs-lookup"><span data-stu-id="80610-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="80610-204">Définit la configuration de build.</span><span class="sxs-lookup"><span data-stu-id="80610-204">Defines the build configuration.</span></span> <span data-ttu-id="80610-205">La valeur par défaut de la plupart des projets est `Debug`.</span><span class="sxs-lookup"><span data-stu-id="80610-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="80610-206">Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié.</span><span class="sxs-lookup"><span data-stu-id="80610-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="80610-207">Le framework doit être spécifié dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="80610-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="80610-208">Affiche une aide brève pour la commande.</span><span class="sxs-lookup"><span data-stu-id="80610-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="80610-209">Spécifie le chemin d’accès et le nom du fichier projet.</span><span class="sxs-lookup"><span data-stu-id="80610-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="80610-210">(Voir la remarque.) S’il n’est pas spécifié, le répertoire actif est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="80610-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="80610-211">Utilisez le chemin d’accès et le nom du fichier projet avec l’option `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="80610-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="80610-212">Une régression dans l’interface CLI empêche de fournir un chemin de dossier avec le SDK .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="80610-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="80610-213">Pour plus d’informations sur ce problème, consultez la page [dotnet run -p, impossible de démarrer un projet (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="80610-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="80610-214">Exemples</span><span class="sxs-lookup"><span data-stu-id="80610-214">Examples</span></span>

<span data-ttu-id="80610-215">Exécutez le projet dans le répertoire actif :</span><span class="sxs-lookup"><span data-stu-id="80610-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="80610-216">Exécutez le projet spécifié :</span><span class="sxs-lookup"><span data-stu-id="80610-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="80610-217">Exécutez le projet dans le répertoire actuel (l’argument `--help` de cet exemple est passé à l’application, puisque l’option `--` vide est utilisée) :</span><span class="sxs-lookup"><span data-stu-id="80610-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="80610-218">Restaurer des dépendances et des outils pour le projet dans le répertoire actuel en montrant uniquement une sortie minimale, puis exécuter le projet : (SDK .NET Core 2.0 et ultérieur) :</span><span class="sxs-lookup"><span data-stu-id="80610-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
