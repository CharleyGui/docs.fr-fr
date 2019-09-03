---
title: Commande dotnet
description: Découvrez la commande dotnet (le pilote générique des outils .NET Core CLI) et comment l’utiliser.
ms.date: 06/04/2018
ms.openlocfilehash: 61542a3fff8bba6e2c3e55a4db5a746620d79ca1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202513"
---
# <a name="dotnet-command"></a><span data-ttu-id="011d7-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="011d7-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="011d7-104">Name</span><span class="sxs-lookup"><span data-stu-id="011d7-104">Name</span></span>

<span data-ttu-id="011d7-105">`dotnet` - Outil de gestion du code source et des ressources binaires .NET.</span><span class="sxs-lookup"><span data-stu-id="011d7-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="011d7-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="011d7-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="011d7-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="011d7-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="011d7-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="011d7-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="011d7-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="011d7-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="011d7-110">Description</span><span class="sxs-lookup"><span data-stu-id="011d7-110">Description</span></span>

<span data-ttu-id="011d7-111">`dotnet` est un outil de gestion du code source et des ressources binaires .NET.</span><span class="sxs-lookup"><span data-stu-id="011d7-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="011d7-112">Il expose les commandes qui permettent d’effectuer des tâches spécifiques, par exemple [`dotnet build`](dotnet-build.md) et [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="011d7-113">Chaque commande définit ses propres arguments.</span><span class="sxs-lookup"><span data-stu-id="011d7-113">Each command defines its own arguments.</span></span> <span data-ttu-id="011d7-114">Tapez `--help` après chaque commande pour accéder à une brève documentation d’aide.</span><span class="sxs-lookup"><span data-stu-id="011d7-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="011d7-115">Vous pouvez utiliser `dotnet` pour exécuter des applications en spécifiant une DLL d’application, par exemple `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="011d7-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="011d7-116">Pour plus d’informations sur les options de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="011d7-117">Options</span><span class="sxs-lookup"><span data-stu-id="011d7-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="011d7-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="011d7-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="011d7-119">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="011d7-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="011d7-120">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="011d7-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="011d7-121">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="011d7-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="011d7-122">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="011d7-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="011d7-123">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="011d7-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="011d7-124">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="011d7-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="011d7-125">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="011d7-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="011d7-126">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="011d7-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="011d7-127">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="011d7-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="011d7-128">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="011d7-129">Affiche les runtimes .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="011d7-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="011d7-130">Affiche les kits de développement logiciel .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="011d7-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="011d7-131">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="011d7-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="011d7-132">`N` peut être :</span><span class="sxs-lookup"><span data-stu-id="011d7-132">`N` can be:</span></span>
* <span data-ttu-id="011d7-133">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="011d7-133">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="011d7-134">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="011d7-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="011d7-135">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="011d7-135">This is the default behavior.</span></span>
* <span data-ttu-id="011d7-136">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="011d7-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="011d7-137">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="011d7-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="011d7-138">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="011d7-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="011d7-139">Un fichier *runtimeconfig.json* est un fichier de configuration contenant des paramètres de configuration de runtime.</span><span class="sxs-lookup"><span data-stu-id="011d7-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="011d7-140">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="011d7-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="011d7-141">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="011d7-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="011d7-142">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="011d7-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="011d7-143">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="011d7-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="011d7-144">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="011d7-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="011d7-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="011d7-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="011d7-146">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="011d7-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="011d7-147">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="011d7-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="011d7-148">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="011d7-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="011d7-149">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="011d7-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="011d7-150">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="011d7-151">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="011d7-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="011d7-152">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="011d7-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="011d7-153">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="011d7-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="011d7-154">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="011d7-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="011d7-155">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="011d7-156">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="011d7-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="011d7-157">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="011d7-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="011d7-158">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="011d7-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="011d7-159">Un fichier *runtimeconfig.json* est un fichier de configuration contenant des paramètres de configuration de runtime.</span><span class="sxs-lookup"><span data-stu-id="011d7-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="011d7-160">Pour plus d’informations, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="011d7-161">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="011d7-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="011d7-162">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="011d7-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="011d7-163">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="011d7-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="011d7-164">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="011d7-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="011d7-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="011d7-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="011d7-166">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="011d7-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="011d7-167">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="011d7-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="011d7-168">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="011d7-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="011d7-169">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="011d7-170">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="011d7-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="011d7-171">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="011d7-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="011d7-172">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="011d7-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="011d7-173">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="011d7-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="011d7-174">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="011d7-175">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="011d7-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="011d7-176">Un fichier *runtimeconfig.json* est un fichier de configuration contenant des paramètres de configuration de runtime.</span><span class="sxs-lookup"><span data-stu-id="011d7-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="011d7-177">Pour plus d’informations, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="011d7-178">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="011d7-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="011d7-179">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="011d7-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="011d7-180">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="011d7-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="011d7-181">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="011d7-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="011d7-182">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="011d7-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="011d7-183">Général</span><span class="sxs-lookup"><span data-stu-id="011d7-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="011d7-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="011d7-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="011d7-185">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-185">Command</span></span>                                       | <span data-ttu-id="011d7-186">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="011d7-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="011d7-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="011d7-188">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="011d7-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="011d7-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="011d7-190">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="011d7-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="011d7-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="011d7-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="011d7-192">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="011d7-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="011d7-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="011d7-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="011d7-194">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="011d7-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="011d7-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="011d7-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="011d7-196">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="011d7-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="011d7-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="011d7-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="011d7-198">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="011d7-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="011d7-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="011d7-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="011d7-200">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="011d7-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="011d7-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="011d7-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="011d7-202">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="011d7-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="011d7-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="011d7-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="011d7-204">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="011d7-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="011d7-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="011d7-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="011d7-206">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="011d7-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="011d7-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="011d7-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="011d7-208">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="011d7-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="011d7-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="011d7-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="011d7-210">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="011d7-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="011d7-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="011d7-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="011d7-212">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="011d7-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="011d7-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="011d7-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="011d7-214">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="011d7-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="011d7-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="011d7-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="011d7-216">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-216">Command</span></span>                             | <span data-ttu-id="011d7-217">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="011d7-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="011d7-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="011d7-219">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="011d7-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="011d7-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="011d7-221">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="011d7-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="011d7-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="011d7-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="011d7-223">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="011d7-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="011d7-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="011d7-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="011d7-225">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="011d7-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="011d7-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="011d7-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="011d7-227">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="011d7-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="011d7-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="011d7-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="011d7-229">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="011d7-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="011d7-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="011d7-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="011d7-231">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="011d7-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="011d7-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="011d7-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="011d7-233">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="011d7-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="011d7-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="011d7-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="011d7-235">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="011d7-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="011d7-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="011d7-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="011d7-237">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="011d7-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="011d7-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="011d7-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="011d7-239">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="011d7-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="011d7-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="011d7-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="011d7-241">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="011d7-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="011d7-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="011d7-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="011d7-243">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="011d7-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="011d7-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="011d7-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="011d7-245">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-245">Command</span></span>                             | <span data-ttu-id="011d7-246">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="011d7-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="011d7-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="011d7-248">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="011d7-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="011d7-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="011d7-250">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="011d7-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="011d7-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="011d7-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="011d7-252">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="011d7-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="011d7-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="011d7-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="011d7-254">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="011d7-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="011d7-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="011d7-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="011d7-256">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="011d7-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="011d7-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="011d7-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="011d7-258">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="011d7-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="011d7-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="011d7-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="011d7-260">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="011d7-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="011d7-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="011d7-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="011d7-262">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="011d7-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="011d7-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="011d7-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="011d7-264">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="011d7-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="011d7-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="011d7-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="011d7-266">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="011d7-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="011d7-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="011d7-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="011d7-268">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="011d7-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="011d7-269">Références de projets</span><span class="sxs-lookup"><span data-stu-id="011d7-269">Project references</span></span>

<span data-ttu-id="011d7-270">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-270">Command</span></span> | <span data-ttu-id="011d7-271">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-271">Function</span></span>
--- | ---
[<span data-ttu-id="011d7-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="011d7-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="011d7-273">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="011d7-273">Adds a project reference.</span></span>
[<span data-ttu-id="011d7-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="011d7-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="011d7-275">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="011d7-275">Lists project references.</span></span>
[<span data-ttu-id="011d7-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="011d7-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="011d7-277">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="011d7-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="011d7-278">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="011d7-278">NuGet packages</span></span>

<span data-ttu-id="011d7-279">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-279">Command</span></span> | <span data-ttu-id="011d7-280">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-280">Function</span></span>
--- | ---
[<span data-ttu-id="011d7-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="011d7-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="011d7-282">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="011d7-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="011d7-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="011d7-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="011d7-284">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="011d7-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="011d7-285">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="011d7-285">NuGet commands</span></span>

<span data-ttu-id="011d7-286">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-286">Command</span></span> | <span data-ttu-id="011d7-287">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-287">Function</span></span>
--- | ---
[<span data-ttu-id="011d7-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="011d7-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="011d7-289">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="011d7-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="011d7-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="011d7-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="011d7-291">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="011d7-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="011d7-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="011d7-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="011d7-293">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="011d7-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="011d7-294">Outils et commandes globaux</span><span class="sxs-lookup"><span data-stu-id="011d7-294">Global Tools commands</span></span>

<span data-ttu-id="011d7-295">Les [outils globaux .NET Core](global-tools.md) sont disponibles à partir de .NET Core SDK 2.1.300 :</span><span class="sxs-lookup"><span data-stu-id="011d7-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="011d7-296">Commande</span><span class="sxs-lookup"><span data-stu-id="011d7-296">Command</span></span> | <span data-ttu-id="011d7-297">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-297">Function</span></span>
--- | ---
[<span data-ttu-id="011d7-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="011d7-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="011d7-299">Installe un outil global sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="011d7-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="011d7-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="011d7-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="011d7-301">Répertorie tous les outils globaux actuellement installés dans le répertoire par défaut de votre machine ou à l’emplacement du chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="011d7-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="011d7-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="011d7-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="011d7-303">Désinstalle un outil global de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="011d7-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="011d7-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="011d7-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="011d7-305">Met à jour un outil global sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="011d7-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="011d7-306">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="011d7-306">Additional tools</span></span>

<span data-ttu-id="011d7-307">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="011d7-308">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="011d7-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="011d7-309">Outil</span><span class="sxs-lookup"><span data-stu-id="011d7-309">Tool</span></span>                                              | <span data-ttu-id="011d7-310">Fonction</span><span class="sxs-lookup"><span data-stu-id="011d7-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="011d7-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="011d7-311">dev-certs</span></span>                                         | <span data-ttu-id="011d7-312">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="011d7-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="011d7-313">ef</span><span class="sxs-lookup"><span data-stu-id="011d7-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="011d7-314">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="011d7-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="011d7-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="011d7-315">sql-cache</span></span>                                         | <span data-ttu-id="011d7-316">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="011d7-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="011d7-317">user-secrets</span><span class="sxs-lookup"><span data-stu-id="011d7-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="011d7-318">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="011d7-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="011d7-319">watch</span><span class="sxs-lookup"><span data-stu-id="011d7-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="011d7-320">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="011d7-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="011d7-321">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="011d7-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="011d7-322">Exemples</span><span class="sxs-lookup"><span data-stu-id="011d7-322">Examples</span></span>

<span data-ttu-id="011d7-323">Crée une application console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="011d7-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="011d7-324">Restaurez les dépendances d’une application donnée :</span><span class="sxs-lookup"><span data-stu-id="011d7-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="011d7-325">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="011d7-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="011d7-326">Exécutez une DLL d’application, par exemple `myapp.dll` :</span><span class="sxs-lookup"><span data-stu-id="011d7-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="011d7-327">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="011d7-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="011d7-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="011d7-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="011d7-329">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="011d7-329">The global packages folder.</span></span> <span data-ttu-id="011d7-330">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="011d7-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="011d7-331">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="011d7-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="011d7-332">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="011d7-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="011d7-333">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="011d7-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="011d7-334">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="011d7-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="011d7-335">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="011d7-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="011d7-336">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="011d7-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="011d7-337">Si elle n’est pas définie, la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="011d7-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="011d7-338">Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées).</span><span class="sxs-lookup"><span data-stu-id="011d7-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="011d7-339">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="011d7-340">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="011d7-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="011d7-341">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="011d7-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="011d7-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="011d7-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="011d7-343">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="011d7-343">The primary package cache.</span></span> <span data-ttu-id="011d7-344">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="011d7-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="011d7-345">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="011d7-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="011d7-346">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="011d7-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="011d7-347">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="011d7-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="011d7-348">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="011d7-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="011d7-349">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="011d7-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="011d7-350">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="011d7-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="011d7-351">Si elle n’est pas définie, la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="011d7-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="011d7-352">Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées).</span><span class="sxs-lookup"><span data-stu-id="011d7-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="011d7-353">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="011d7-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="011d7-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="011d7-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="011d7-355">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="011d7-355">The primary package cache.</span></span> <span data-ttu-id="011d7-356">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="011d7-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="011d7-357">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="011d7-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="011d7-358">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="011d7-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="011d7-359">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="011d7-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="011d7-360">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="011d7-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="011d7-361">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="011d7-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="011d7-362">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="011d7-362">See also</span></span>

- [<span data-ttu-id="011d7-363">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="011d7-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
