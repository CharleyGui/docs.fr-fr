---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451166"
---
# <a name="dotnet-command"></a><span data-ttu-id="f34ce-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="f34ce-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f34ce-104">Name</span><span class="sxs-lookup"><span data-stu-id="f34ce-104">Name</span></span>

<span data-ttu-id="f34ce-105">`dotnet` - Outil de gestion du code source et des ressources binaires .NET.</span><span class="sxs-lookup"><span data-stu-id="f34ce-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f34ce-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="f34ce-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="f34ce-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f34ce-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[<span data-ttu-id="f34ce-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f34ce-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="f34ce-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f34ce-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="f34ce-110">Description</span><span class="sxs-lookup"><span data-stu-id="f34ce-110">Description</span></span>

<span data-ttu-id="f34ce-111">`dotnet` est un outil de gestion du code source et des ressources binaires .NET.</span><span class="sxs-lookup"><span data-stu-id="f34ce-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="f34ce-112">Il expose les commandes qui permettent d’effectuer des tâches spécifiques, par exemple [`dotnet build`](dotnet-build.md) et [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="f34ce-113">Chaque commande définit ses propres arguments.</span><span class="sxs-lookup"><span data-stu-id="f34ce-113">Each command defines its own arguments.</span></span> <span data-ttu-id="f34ce-114">Tapez `--help` après chaque commande pour accéder à une brève documentation d’aide.</span><span class="sxs-lookup"><span data-stu-id="f34ce-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="f34ce-115">Vous pouvez utiliser `dotnet` pour exécuter des applications en spécifiant une DLL d’application, par exemple `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="f34ce-116">Pour plus d’informations sur les options de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="f34ce-117">Options</span><span class="sxs-lookup"><span data-stu-id="f34ce-117">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="f34ce-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f34ce-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="f34ce-119">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="f34ce-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="f34ce-120">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="f34ce-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="f34ce-121">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="f34ce-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="f34ce-122">Un fichier *DEPS. JSON* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour traiter les conflits d’assembly.</span><span class="sxs-lookup"><span data-stu-id="f34ce-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="f34ce-123">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="f34ce-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="f34ce-124">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="f34ce-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="f34ce-125">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="f34ce-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="f34ce-126">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="f34ce-127">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="f34ce-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="f34ce-128">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="f34ce-129">Affiche les runtimes .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="f34ce-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="f34ce-130">Affiche les kits de développement logiciel .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="f34ce-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="f34ce-131">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="f34ce-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="f34ce-132">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="f34ce-132">`N` can be:</span></span>

- <span data-ttu-id="f34ce-133">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="f34ce-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="f34ce-134">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="f34ce-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="f34ce-135">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="f34ce-135">This is the default behavior.</span></span>
- <span data-ttu-id="f34ce-136">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="f34ce-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="f34ce-137">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f34ce-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="f34ce-138">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="f34ce-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="f34ce-139">Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="f34ce-140">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f34ce-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f34ce-141">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="f34ce-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f34ce-142">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f34ce-143">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="f34ce-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="f34ce-144">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="f34ce-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="f34ce-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f34ce-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="f34ce-146">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="f34ce-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="f34ce-147">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="f34ce-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="f34ce-148">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="f34ce-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="f34ce-149">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="f34ce-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="f34ce-150">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="f34ce-151">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="f34ce-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="f34ce-152">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="f34ce-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="f34ce-153">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="f34ce-154">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="f34ce-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="f34ce-155">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="f34ce-156">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="f34ce-157">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f34ce-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="f34ce-158">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="f34ce-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="f34ce-159">Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="f34ce-160">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f34ce-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f34ce-161">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="f34ce-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f34ce-162">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f34ce-163">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="f34ce-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="f34ce-164">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="f34ce-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="f34ce-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f34ce-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="f34ce-166">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="f34ce-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="f34ce-167">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="f34ce-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="f34ce-168">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="f34ce-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="f34ce-169">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="f34ce-170">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="f34ce-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="f34ce-171">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="f34ce-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="f34ce-172">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="f34ce-173">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="f34ce-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="f34ce-174">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="f34ce-175">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="f34ce-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="f34ce-176">Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="f34ce-177">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="f34ce-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="f34ce-178">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="f34ce-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f34ce-179">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f34ce-180">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="f34ce-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="f34ce-181">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="f34ce-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="f34ce-182">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="f34ce-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="f34ce-183">Général</span><span class="sxs-lookup"><span data-stu-id="f34ce-183">General</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="f34ce-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f34ce-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="f34ce-185">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-185">Command</span></span>                                       | <span data-ttu-id="f34ce-186">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="f34ce-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="f34ce-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="f34ce-188">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="f34ce-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="f34ce-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="f34ce-190">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="f34ce-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="f34ce-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="f34ce-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="f34ce-192">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="f34ce-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="f34ce-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="f34ce-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="f34ce-194">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f34ce-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="f34ce-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="f34ce-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="f34ce-196">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f34ce-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="f34ce-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f34ce-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="f34ce-198">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f34ce-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="f34ce-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f34ce-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="f34ce-200">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="f34ce-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="f34ce-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="f34ce-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="f34ce-202">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="f34ce-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="f34ce-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="f34ce-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="f34ce-204">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="f34ce-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="f34ce-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="f34ce-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="f34ce-206">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="f34ce-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="f34ce-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="f34ce-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="f34ce-208">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="f34ce-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="f34ce-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="f34ce-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="f34ce-210">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="f34ce-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="f34ce-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="f34ce-212">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="f34ce-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="f34ce-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f34ce-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="f34ce-214">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="f34ce-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20"></a>[<span data-ttu-id="f34ce-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f34ce-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="f34ce-216">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-216">Command</span></span>                             | <span data-ttu-id="f34ce-217">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="f34ce-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="f34ce-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="f34ce-219">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="f34ce-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="f34ce-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="f34ce-221">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="f34ce-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="f34ce-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="f34ce-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="f34ce-223">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="f34ce-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="f34ce-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="f34ce-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="f34ce-225">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f34ce-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="f34ce-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f34ce-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="f34ce-227">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f34ce-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="f34ce-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f34ce-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="f34ce-229">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="f34ce-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="f34ce-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="f34ce-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="f34ce-231">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="f34ce-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="f34ce-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="f34ce-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="f34ce-233">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="f34ce-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="f34ce-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="f34ce-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="f34ce-235">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="f34ce-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="f34ce-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="f34ce-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="f34ce-237">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="f34ce-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="f34ce-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="f34ce-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="f34ce-239">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="f34ce-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="f34ce-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="f34ce-241">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="f34ce-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="f34ce-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f34ce-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="f34ce-243">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="f34ce-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1x"></a>[<span data-ttu-id="f34ce-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f34ce-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="f34ce-245">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-245">Command</span></span>                             | <span data-ttu-id="f34ce-246">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="f34ce-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="f34ce-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="f34ce-248">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="f34ce-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="f34ce-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="f34ce-250">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="f34ce-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="f34ce-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="f34ce-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="f34ce-252">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="f34ce-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="f34ce-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="f34ce-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="f34ce-254">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="f34ce-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="f34ce-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="f34ce-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="f34ce-256">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="f34ce-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="f34ce-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="f34ce-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="f34ce-258">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="f34ce-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="f34ce-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="f34ce-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="f34ce-260">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="f34ce-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="f34ce-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="f34ce-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="f34ce-262">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="f34ce-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="f34ce-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="f34ce-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="f34ce-264">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="f34ce-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="f34ce-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="f34ce-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="f34ce-266">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="f34ce-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="f34ce-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="f34ce-268">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="f34ce-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="f34ce-269">Références de projets</span><span class="sxs-lookup"><span data-stu-id="f34ce-269">Project references</span></span>

<span data-ttu-id="f34ce-270">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-270">Command</span></span> | <span data-ttu-id="f34ce-271">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-271">Function</span></span>
--- | ---
[<span data-ttu-id="f34ce-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="f34ce-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="f34ce-273">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="f34ce-273">Adds a project reference.</span></span>
[<span data-ttu-id="f34ce-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="f34ce-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="f34ce-275">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="f34ce-275">Lists project references.</span></span>
[<span data-ttu-id="f34ce-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="f34ce-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="f34ce-277">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="f34ce-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="f34ce-278">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="f34ce-278">NuGet packages</span></span>

<span data-ttu-id="f34ce-279">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-279">Command</span></span> | <span data-ttu-id="f34ce-280">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-280">Function</span></span>
--- | ---
[<span data-ttu-id="f34ce-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="f34ce-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="f34ce-282">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="f34ce-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="f34ce-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="f34ce-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="f34ce-284">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="f34ce-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="f34ce-285">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="f34ce-285">NuGet commands</span></span>

<span data-ttu-id="f34ce-286">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-286">Command</span></span> | <span data-ttu-id="f34ce-287">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-287">Function</span></span>
--- | ---
[<span data-ttu-id="f34ce-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="f34ce-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="f34ce-289">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="f34ce-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="f34ce-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="f34ce-291">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="f34ce-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="f34ce-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="f34ce-293">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="f34ce-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="f34ce-294">Commandes globales, de chemin d’accès d’outil et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="f34ce-294">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="f34ce-295">Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="f34ce-295">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="f34ce-296">Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="f34ce-296">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="f34ce-297">Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux.</span><span class="sxs-lookup"><span data-stu-id="f34ce-297">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="f34ce-298">Pour plus d’informations, consultez [vue d’ensemble des outils .net Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-298">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="f34ce-299">Les outils globaux et de chemin d’accès aux outils sont disponibles à partir de kit SDK .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="f34ce-299">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="f34ce-300">Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="f34ce-300">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="f34ce-301">Commande</span><span class="sxs-lookup"><span data-stu-id="f34ce-301">Command</span></span> | <span data-ttu-id="f34ce-302">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-302">Function</span></span>
--- | ---
[<span data-ttu-id="f34ce-303">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="f34ce-303">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="f34ce-304">Installe un outil sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-304">Installs a tool on your machine.</span></span>
[<span data-ttu-id="f34ce-305">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="f34ce-305">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="f34ce-306">Répertorie tous les outils globaux, de chemin d’accès d’outil ou locaux actuellement installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-306">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="f34ce-307">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="f34ce-307">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="f34ce-308">Désinstalle un outil de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-308">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="f34ce-309">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f34ce-309">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="f34ce-310">Met à jour un outil qui est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-310">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="f34ce-311">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="f34ce-311">Additional tools</span></span>

<span data-ttu-id="f34ce-312">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-312">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="f34ce-313">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="f34ce-313">These tools are listed in the following table:</span></span>

| <span data-ttu-id="f34ce-314">Outil</span><span class="sxs-lookup"><span data-stu-id="f34ce-314">Tool</span></span>                                              | <span data-ttu-id="f34ce-315">Fonction</span><span class="sxs-lookup"><span data-stu-id="f34ce-315">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="f34ce-316">dev-certs</span><span class="sxs-lookup"><span data-stu-id="f34ce-316">dev-certs</span></span>                                         | <span data-ttu-id="f34ce-317">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="f34ce-317">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="f34ce-318">ef</span><span class="sxs-lookup"><span data-stu-id="f34ce-318">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="f34ce-319">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="f34ce-319">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="f34ce-320">sql-cache</span><span class="sxs-lookup"><span data-stu-id="f34ce-320">sql-cache</span></span>                                         | <span data-ttu-id="f34ce-321">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f34ce-321">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="f34ce-322">user-secrets</span><span class="sxs-lookup"><span data-stu-id="f34ce-322">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="f34ce-323">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f34ce-323">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="f34ce-324">watch</span><span class="sxs-lookup"><span data-stu-id="f34ce-324">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="f34ce-325">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="f34ce-325">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="f34ce-326">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-326">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="f34ce-327">Exemples</span><span class="sxs-lookup"><span data-stu-id="f34ce-327">Examples</span></span>

<span data-ttu-id="f34ce-328">Crée une application console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="f34ce-328">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="f34ce-329">Restaurez les dépendances d’une application donnée :</span><span class="sxs-lookup"><span data-stu-id="f34ce-329">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="f34ce-330">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="f34ce-330">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="f34ce-331">Exécutez une DLL d’application, par exemple `myapp.dll` :</span><span class="sxs-lookup"><span data-stu-id="f34ce-331">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="f34ce-332">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="f34ce-332">Environment variables</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="f34ce-333">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f34ce-333">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="f34ce-334">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="f34ce-334">The global packages folder.</span></span> <span data-ttu-id="f34ce-335">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="f34ce-335">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="f34ce-336">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-336">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="f34ce-337">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f34ce-337">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="f34ce-338">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="f34ce-338">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="f34ce-339">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="f34ce-339">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="f34ce-340">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="f34ce-340">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="f34ce-341">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="f34ce-341">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="f34ce-342">Si elle n’est pas définie, la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-342">If not set, it defaults to `true`.</span></span> <span data-ttu-id="f34ce-343">Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées).</span><span class="sxs-lookup"><span data-stu-id="f34ce-343">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="f34ce-344">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-344">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="f34ce-345">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-345">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="f34ce-346">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="f34ce-346">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="f34ce-347">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="f34ce-347">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="f34ce-348">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="f34ce-348">The primary package cache.</span></span> <span data-ttu-id="f34ce-349">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="f34ce-349">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="f34ce-350">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-350">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="f34ce-351">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f34ce-351">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="f34ce-352">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="f34ce-352">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="f34ce-353">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="f34ce-353">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="f34ce-354">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="f34ce-354">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="f34ce-355">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="f34ce-355">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="f34ce-356">Si elle n’est pas définie, la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="f34ce-356">If not set, it defaults to `true`.</span></span> <span data-ttu-id="f34ce-357">Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées).</span><span class="sxs-lookup"><span data-stu-id="f34ce-357">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="f34ce-358">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="f34ce-358">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="f34ce-359">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="f34ce-359">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="f34ce-360">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="f34ce-360">The primary package cache.</span></span> <span data-ttu-id="f34ce-361">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="f34ce-361">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="f34ce-362">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f34ce-362">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="f34ce-363">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f34ce-363">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="f34ce-364">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="f34ce-364">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="f34ce-365">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="f34ce-365">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="f34ce-366">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="f34ce-366">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="f34ce-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f34ce-367">See also</span></span>

- [<span data-ttu-id="f34ce-368">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="f34ce-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="f34ce-369">Paramètres de configuration du Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="f34ce-369">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
