---
title: Commande dotnet
description: Découvrez la commande dotnet (le pilote générique des outils .NET Core CLI) et comment l’utiliser.
ms.date: 06/04/2018
ms.openlocfilehash: 8de6a6f7e584dc472dc23d60f113b03610abb3ef
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926224"
---
# <a name="dotnet-command"></a><span data-ttu-id="5c612-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="5c612-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="5c612-104">Nom</span><span class="sxs-lookup"><span data-stu-id="5c612-104">Name</span></span>

<span data-ttu-id="5c612-105">`dotnet` - Outil de gestion du code source et des ressources binaires .NET.</span><span class="sxs-lookup"><span data-stu-id="5c612-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5c612-106">Résumé</span><span class="sxs-lookup"><span data-stu-id="5c612-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c612-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c612-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c612-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c612-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c612-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c612-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="5c612-110">Description</span><span class="sxs-lookup"><span data-stu-id="5c612-110">Description</span></span>

<span data-ttu-id="5c612-111">`dotnet` est un outil de gestion du code source et des ressources binaires .NET.</span><span class="sxs-lookup"><span data-stu-id="5c612-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="5c612-112">Il expose les commandes qui permettent d’effectuer des tâches spécifiques, par exemple [`dotnet build`](dotnet-build.md) et [`dotnet run`](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="5c612-113">Chaque commande définit ses propres arguments.</span><span class="sxs-lookup"><span data-stu-id="5c612-113">Each command defines its own arguments.</span></span> <span data-ttu-id="5c612-114">Tapez `--help` après chaque commande pour accéder à une brève documentation d’aide.</span><span class="sxs-lookup"><span data-stu-id="5c612-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="5c612-115">Vous pouvez utiliser `dotnet` pour exécuter des applications en spécifiant une DLL d’application, par exemple `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="5c612-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="5c612-116">Pour plus d’informations sur les options de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="5c612-117">Options</span><span class="sxs-lookup"><span data-stu-id="5c612-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c612-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c612-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="5c612-119">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5c612-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="5c612-120">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="5c612-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="5c612-121">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="5c612-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="5c612-122">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="5c612-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5c612-123">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c612-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="5c612-124">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="5c612-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5c612-125">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="5c612-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5c612-126">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5c612-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="5c612-127">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="5c612-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="5c612-128">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="5c612-129">Affiche les runtimes .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="5c612-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="5c612-130">Affiche les kits de développement logiciel .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="5c612-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="5c612-131">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="5c612-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="5c612-132">`N` peut être :</span><span class="sxs-lookup"><span data-stu-id="5c612-132">`N` can be:</span></span>

- <span data-ttu-id="5c612-133">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="5c612-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="5c612-134">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="5c612-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="5c612-135">Il s’agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="5c612-135">This is the default behavior.</span></span>
- <span data-ttu-id="5c612-136">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="5c612-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="5c612-137">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5c612-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="5c612-138">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5c612-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="5c612-139">Un fichier *runtimeconfig.json* est un fichier de configuration contenant des paramètres de configuration de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c612-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="5c612-140">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5c612-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5c612-141">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="5c612-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5c612-142">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5c612-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5c612-143">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="5c612-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="5c612-144">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5c612-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c612-145">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c612-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="5c612-146">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5c612-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="5c612-147">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="5c612-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="5c612-148">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="5c612-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="5c612-149">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="5c612-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5c612-150">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="5c612-151">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="5c612-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5c612-152">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="5c612-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5c612-153">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5c612-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="5c612-154">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="5c612-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="5c612-155">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="5c612-156">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="5c612-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="5c612-157">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5c612-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="5c612-158">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5c612-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="5c612-159">Un fichier *runtimeconfig.json* est un fichier de configuration contenant des paramètres de configuration de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c612-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="5c612-160">Pour plus d’informations, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5c612-161">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="5c612-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5c612-162">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5c612-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5c612-163">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="5c612-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="5c612-164">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5c612-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c612-165">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c612-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="5c612-166">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="5c612-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="5c612-167">Chemin d’un fichier *deps.json*.</span><span class="sxs-lookup"><span data-stu-id="5c612-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="5c612-168">Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys.</span><span class="sxs-lookup"><span data-stu-id="5c612-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5c612-169">Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="5c612-170">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="5c612-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="5c612-171">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="5c612-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="5c612-172">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5c612-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="5c612-173">`dotnet --help` affiche une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="5c612-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="5c612-174">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="5c612-175">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5c612-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="5c612-176">Un fichier *runtimeconfig.json* est un fichier de configuration contenant des paramètres de configuration de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c612-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="5c612-177">Pour plus d’informations, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5c612-178">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="5c612-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5c612-179">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5c612-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5c612-180">Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="5c612-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="5c612-181">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5c612-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="5c612-182">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="5c612-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="5c612-183">Généralités</span><span class="sxs-lookup"><span data-stu-id="5c612-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c612-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c612-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="5c612-185">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-185">Command</span></span>                                       | <span data-ttu-id="5c612-186">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5c612-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5c612-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="5c612-188">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5c612-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="5c612-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="5c612-190">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="5c612-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="5c612-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5c612-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="5c612-192">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="5c612-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="5c612-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="5c612-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="5c612-194">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5c612-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="5c612-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5c612-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="5c612-196">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c612-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5c612-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5c612-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="5c612-198">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5c612-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5c612-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5c612-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="5c612-200">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="5c612-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5c612-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5c612-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="5c612-202">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="5c612-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5c612-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5c612-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="5c612-204">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="5c612-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5c612-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5c612-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="5c612-206">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="5c612-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5c612-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5c612-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="5c612-208">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="5c612-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5c612-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5c612-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="5c612-210">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="5c612-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5c612-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5c612-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="5c612-212">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c612-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="5c612-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5c612-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="5c612-214">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="5c612-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c612-215">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c612-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="5c612-216">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-216">Command</span></span>                             | <span data-ttu-id="5c612-217">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5c612-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5c612-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="5c612-219">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5c612-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5c612-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="5c612-221">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="5c612-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="5c612-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="5c612-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="5c612-223">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5c612-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="5c612-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5c612-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="5c612-225">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c612-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5c612-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5c612-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="5c612-227">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5c612-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5c612-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5c612-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="5c612-229">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="5c612-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5c612-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5c612-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="5c612-231">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="5c612-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5c612-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5c612-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="5c612-233">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="5c612-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5c612-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5c612-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="5c612-235">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="5c612-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5c612-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5c612-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="5c612-237">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="5c612-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5c612-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5c612-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="5c612-239">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="5c612-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5c612-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5c612-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="5c612-241">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="5c612-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="5c612-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5c612-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="5c612-243">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="5c612-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c612-244">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c612-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="5c612-245">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-245">Command</span></span>                             | <span data-ttu-id="5c612-246">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5c612-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5c612-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="5c612-248">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5c612-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5c612-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="5c612-250">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="5c612-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="5c612-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5c612-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="5c612-252">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5c612-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5c612-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5c612-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="5c612-254">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5c612-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5c612-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5c612-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="5c612-256">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="5c612-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5c612-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5c612-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="5c612-258">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="5c612-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5c612-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5c612-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="5c612-260">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="5c612-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5c612-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5c612-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="5c612-262">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="5c612-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5c612-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5c612-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="5c612-264">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="5c612-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5c612-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5c612-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="5c612-266">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="5c612-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5c612-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5c612-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="5c612-268">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="5c612-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="5c612-269">Références de projets</span><span class="sxs-lookup"><span data-stu-id="5c612-269">Project references</span></span>

<span data-ttu-id="5c612-270">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-270">Command</span></span> | <span data-ttu-id="5c612-271">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-271">Function</span></span>
--- | ---
[<span data-ttu-id="5c612-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="5c612-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="5c612-273">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="5c612-273">Adds a project reference.</span></span>
[<span data-ttu-id="5c612-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5c612-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="5c612-275">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="5c612-275">Lists project references.</span></span>
[<span data-ttu-id="5c612-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="5c612-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="5c612-277">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="5c612-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="5c612-278">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="5c612-278">NuGet packages</span></span>

<span data-ttu-id="5c612-279">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-279">Command</span></span> | <span data-ttu-id="5c612-280">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-280">Function</span></span>
--- | ---
[<span data-ttu-id="5c612-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="5c612-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="5c612-282">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c612-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="5c612-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="5c612-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="5c612-284">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c612-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="5c612-285">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="5c612-285">NuGet commands</span></span>

<span data-ttu-id="5c612-286">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-286">Command</span></span> | <span data-ttu-id="5c612-287">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-287">Function</span></span>
--- | ---
[<span data-ttu-id="5c612-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="5c612-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="5c612-289">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="5c612-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="5c612-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="5c612-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="5c612-291">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5c612-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="5c612-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="5c612-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="5c612-293">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="5c612-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="5c612-294">Outils et commandes globaux</span><span class="sxs-lookup"><span data-stu-id="5c612-294">Global Tools commands</span></span>

<span data-ttu-id="5c612-295">Les [outils globaux .NET Core](global-tools.md) sont disponibles à partir de .NET Core SDK 2.1.300 :</span><span class="sxs-lookup"><span data-stu-id="5c612-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="5c612-296">Commande</span><span class="sxs-lookup"><span data-stu-id="5c612-296">Command</span></span> | <span data-ttu-id="5c612-297">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-297">Function</span></span>
--- | ---
[<span data-ttu-id="5c612-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="5c612-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="5c612-299">Installe un outil global sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5c612-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="5c612-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="5c612-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="5c612-301">Répertorie tous les outils globaux actuellement installés dans le répertoire par défaut de votre machine ou à l’emplacement du chemin spécifié.</span><span class="sxs-lookup"><span data-stu-id="5c612-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="5c612-302">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="5c612-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="5c612-303">Désinstalle un outil global de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5c612-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="5c612-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="5c612-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="5c612-305">Met à jour un outil global sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5c612-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="5c612-306">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5c612-306">Additional tools</span></span>

<span data-ttu-id="5c612-307">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="5c612-308">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="5c612-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="5c612-309">Tool</span><span class="sxs-lookup"><span data-stu-id="5c612-309">Tool</span></span>                                              | <span data-ttu-id="5c612-310">Fonction</span><span class="sxs-lookup"><span data-stu-id="5c612-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="5c612-311">dev-certs</span><span class="sxs-lookup"><span data-stu-id="5c612-311">dev-certs</span></span>                                         | <span data-ttu-id="5c612-312">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="5c612-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="5c612-313">ef</span><span class="sxs-lookup"><span data-stu-id="5c612-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="5c612-314">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="5c612-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="5c612-315">sql-cache</span><span class="sxs-lookup"><span data-stu-id="5c612-315">sql-cache</span></span>                                         | <span data-ttu-id="5c612-316">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5c612-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="5c612-317">user-secrets</span><span class="sxs-lookup"><span data-stu-id="5c612-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="5c612-318">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5c612-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="5c612-319">watch</span><span class="sxs-lookup"><span data-stu-id="5c612-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="5c612-320">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="5c612-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="5c612-321">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="5c612-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="5c612-322">Exemples</span><span class="sxs-lookup"><span data-stu-id="5c612-322">Examples</span></span>

<span data-ttu-id="5c612-323">Crée une application console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="5c612-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="5c612-324">Restaurez les dépendances d’une application donnée :</span><span class="sxs-lookup"><span data-stu-id="5c612-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="5c612-325">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="5c612-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="5c612-326">Exécutez une DLL d’application, par exemple `myapp.dll` :</span><span class="sxs-lookup"><span data-stu-id="5c612-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="5c612-327">Variables d’environnement</span><span class="sxs-lookup"><span data-stu-id="5c612-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="5c612-328">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="5c612-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="5c612-329">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="5c612-329">The global packages folder.</span></span> <span data-ttu-id="5c612-330">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="5c612-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5c612-331">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5c612-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5c612-332">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c612-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5c612-333">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="5c612-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5c612-334">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="5c612-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5c612-335">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="5c612-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="5c612-336">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="5c612-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="5c612-337">Si elle n’est pas définie, la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="5c612-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="5c612-338">Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées).</span><span class="sxs-lookup"><span data-stu-id="5c612-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="5c612-339">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="5c612-340">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="5c612-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="5c612-341">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5c612-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="5c612-342">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="5c612-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="5c612-343">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="5c612-343">The primary package cache.</span></span> <span data-ttu-id="5c612-344">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="5c612-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5c612-345">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5c612-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5c612-346">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c612-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5c612-347">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="5c612-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5c612-348">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="5c612-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5c612-349">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="5c612-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="5c612-350">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="5c612-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="5c612-351">Si elle n’est pas définie, la valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="5c612-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="5c612-352">Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées).</span><span class="sxs-lookup"><span data-stu-id="5c612-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="5c612-353">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="5c612-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5c612-354">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="5c612-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="5c612-355">Cache du package principal.</span><span class="sxs-lookup"><span data-stu-id="5c612-355">The primary package cache.</span></span> <span data-ttu-id="5c612-356">S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="5c612-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="5c612-357">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5c612-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="5c612-358">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5c612-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5c612-359">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="5c612-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5c612-360">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="5c612-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5c612-361">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="5c612-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="5c612-362">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c612-362">See also</span></span>

- [<span data-ttu-id="5c612-363">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="5c612-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
