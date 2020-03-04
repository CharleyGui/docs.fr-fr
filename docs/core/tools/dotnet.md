---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240868"
---
# <a name="dotnet-command"></a><span data-ttu-id="5bb2c-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="5bb2c-103">dotnet command</span></span>

<span data-ttu-id="5bb2c-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="5bb2c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5bb2c-105">Nom</span><span class="sxs-lookup"><span data-stu-id="5bb2c-105">Name</span></span>

<span data-ttu-id="5bb2c-106">`dotnet`-pilote générique du CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5bb2c-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5bb2c-107">Synopsis</span></span>

<span data-ttu-id="5bb2c-108">Pour obtenir des informations sur les commandes disponibles et l’environnement :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="5bb2c-109">Pour exécuter une commande (installation du kit de développement logiciel (SDK) requise) :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="5bb2c-110">Pour exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="5bb2c-111">`--roll-forward` est disponible depuis .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="5bb2c-112">Utilisez `--roll-forward-on-no-candidate-fx` pour .NET Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="5bb2c-113">Description</span><span class="sxs-lookup"><span data-stu-id="5bb2c-113">Description</span></span>

<span data-ttu-id="5bb2c-114">La commande `dotnet` a deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="5bb2c-115">Il fournit des commandes pour travailler avec les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="5bb2c-116">Par exemple, [`dotnet build`](dotnet-build.md) génère un projet.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="5bb2c-117">Chaque commande définit ses propres options et arguments.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="5bb2c-118">Toutes les commandes prennent en charge l’option `--help` pour imprimer une brève documentation sur la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="5bb2c-119">Il exécute des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="5bb2c-120">Vous spécifiez le chemin d’accès à un fichier d' `.dll` d’application pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="5bb2c-121">Par exemple, `dotnet myapp.dll` exécute l’application `myapp`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="5bb2c-122">Consultez [déploiement d’applications .net Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="5bb2c-123">Options</span><span class="sxs-lookup"><span data-stu-id="5bb2c-123">Options</span></span>

<span data-ttu-id="5bb2c-124">Différentes options sont disponibles pour la `dotnet` seule, pour exécuter une commande et pour exécuter une application.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="5bb2c-125">Options de dotnet par lui-même</span><span class="sxs-lookup"><span data-stu-id="5bb2c-125">Options for dotnet by itself</span></span>

<span data-ttu-id="5bb2c-126">Les options suivantes sont destinées à `dotnet` par elle-même.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="5bb2c-127">Par exemple : `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="5bb2c-128">Ils affichent des informations sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="5bb2c-129">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="5bb2c-130">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="5bb2c-131">Imprime une liste des runtimes .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="5bb2c-132">Affiche la liste des kits de développement logiciel (SDK) .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5bb2c-133">Imprime une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="5bb2c-134">Options du kit de développement logiciel pour exécuter une commande</span><span class="sxs-lookup"><span data-stu-id="5bb2c-134">SDK options for running a command</span></span>

<span data-ttu-id="5bb2c-135">Les options suivantes concernent `dotnet` avec une commande.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="5bb2c-136">Par exemple : `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="5bb2c-137">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5bb2c-138">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5bb2c-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5bb2c-140">Non pris en charge dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-140">Not supported in every command.</span></span> <span data-ttu-id="5bb2c-141">Consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5bb2c-142">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="5bb2c-143">Chaque commande définit des options spécifiques à cette commande.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="5bb2c-144">Pour obtenir la liste des options disponibles, consultez la page de commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="5bb2c-145">Options d’exécution</span><span class="sxs-lookup"><span data-stu-id="5bb2c-145">Runtime options</span></span>

<span data-ttu-id="5bb2c-146">Les options suivantes sont disponibles lorsque `dotnet` exécute une application.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="5bb2c-147">Par exemple : `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="5bb2c-148">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="5bb2c-149">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="5bb2c-150">Un fichier *DEPS. JSON* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour traiter les conflits d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="5bb2c-151">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="5bb2c-152">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="5bb2c-153">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="5bb2c-154">Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="5bb2c-155">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="5bb2c-156">**`--roll-forward-on-no-candidate-fx <N>`** **disponibles dans le kit de développement logiciel (SDK) .net Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="5bb2c-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="5bb2c-157">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="5bb2c-158">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-158">`N` can be:</span></span>

  - <span data-ttu-id="5bb2c-159">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="5bb2c-160">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="5bb2c-161">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-161">This is the default behavior.</span></span>
  - <span data-ttu-id="5bb2c-162">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="5bb2c-163">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="5bb2c-164">**`--roll-forward <SETTING>`** **disponibles à partir de kit SDK .net Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="5bb2c-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="5bb2c-165">Contrôle la façon dont la restauration par progression est appliquée à l’application.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="5bb2c-166">L' `SETTING` peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="5bb2c-167">S’il n’est pas spécifié, `Minor` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="5bb2c-168">`LatestPatch` : restauration par progression vers la version de correctif la plus récente.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="5bb2c-169">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="5bb2c-170">`Minor`-restaurer à la version mineure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="5bb2c-171">Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="5bb2c-172">`Major`-restaurer la version principale la plus basse, et la version mineure la plus faible, si la version principale demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="5bb2c-173">Si la version principale demandée est présente, la stratégie mineure est utilisée.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="5bb2c-174">`LatestMinor` : restauration par progression vers la version mineure la plus élevée, même si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="5bb2c-175">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="5bb2c-176">`LatestMajor` : restauration par progression vers la version mineure la plus élevée et la plus élevée, même si la version principale demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="5bb2c-177">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="5bb2c-178">`Disable`-ne pas restaurer par progression.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="5bb2c-179">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-179">Only bind to specified version.</span></span> <span data-ttu-id="5bb2c-180">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="5bb2c-181">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="5bb2c-182">À l’exception de `Disable`, tous les paramètres utilisent la version de correctif la plus élevée disponible.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="5bb2c-183">Le comportement de restauration par progression peut également être configuré dans une propriété de fichier projet, une propriété de fichier de configuration au moment de l’exécution et une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="5bb2c-184">Pour plus d’informations, consultez [restauration par progression du runtime de version principale](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="5bb2c-185">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="5bb2c-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="5bb2c-186">Général</span><span class="sxs-lookup"><span data-stu-id="5bb2c-186">General</span></span>

| <span data-ttu-id="5bb2c-187">Commande</span><span class="sxs-lookup"><span data-stu-id="5bb2c-187">Command</span></span>                                       | <span data-ttu-id="5bb2c-188">Fonction</span><span class="sxs-lookup"><span data-stu-id="5bb2c-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="5bb2c-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5bb2c-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="5bb2c-190">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="5bb2c-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="5bb2c-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="5bb2c-192">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="5bb2c-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="5bb2c-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="5bb2c-194">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="5bb2c-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="5bb2c-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="5bb2c-196">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="5bb2c-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="5bb2c-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="5bb2c-198">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="5bb2c-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="5bb2c-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="5bb2c-200">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="5bb2c-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="5bb2c-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="5bb2c-202">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="5bb2c-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="5bb2c-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="5bb2c-204">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="5bb2c-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="5bb2c-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="5bb2c-206">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="5bb2c-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="5bb2c-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="5bb2c-208">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="5bb2c-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="5bb2c-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="5bb2c-210">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="5bb2c-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="5bb2c-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="5bb2c-212">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="5bb2c-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5bb2c-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="5bb2c-214">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="5bb2c-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="5bb2c-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="5bb2c-216">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="5bb2c-217">Références de projets</span><span class="sxs-lookup"><span data-stu-id="5bb2c-217">Project references</span></span>

<span data-ttu-id="5bb2c-218">Commande</span><span class="sxs-lookup"><span data-stu-id="5bb2c-218">Command</span></span> | <span data-ttu-id="5bb2c-219">Fonction</span><span class="sxs-lookup"><span data-stu-id="5bb2c-219">Function</span></span>
--- | ---
[<span data-ttu-id="5bb2c-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="5bb2c-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="5bb2c-221">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-221">Adds a project reference.</span></span>
[<span data-ttu-id="5bb2c-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="5bb2c-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="5bb2c-223">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-223">Lists project references.</span></span>
[<span data-ttu-id="5bb2c-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="5bb2c-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="5bb2c-225">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="5bb2c-226">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="5bb2c-226">NuGet packages</span></span>

<span data-ttu-id="5bb2c-227">Commande</span><span class="sxs-lookup"><span data-stu-id="5bb2c-227">Command</span></span> | <span data-ttu-id="5bb2c-228">Fonction</span><span class="sxs-lookup"><span data-stu-id="5bb2c-228">Function</span></span>
--- | ---
[<span data-ttu-id="5bb2c-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="5bb2c-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="5bb2c-230">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="5bb2c-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="5bb2c-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="5bb2c-232">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="5bb2c-233">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="5bb2c-233">NuGet commands</span></span>

<span data-ttu-id="5bb2c-234">Commande</span><span class="sxs-lookup"><span data-stu-id="5bb2c-234">Command</span></span> | <span data-ttu-id="5bb2c-235">Fonction</span><span class="sxs-lookup"><span data-stu-id="5bb2c-235">Function</span></span>
--- | ---
[<span data-ttu-id="5bb2c-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="5bb2c-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="5bb2c-237">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="5bb2c-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="5bb2c-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="5bb2c-239">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="5bb2c-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="5bb2c-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="5bb2c-241">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="5bb2c-242">Commandes globales, de chemin d’accès d’outil et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="5bb2c-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="5bb2c-243">Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="5bb2c-244">Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="5bb2c-245">Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="5bb2c-246">Pour plus d’informations, consultez [vue d’ensemble des outils .net Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="5bb2c-247">Les outils globaux et de chemin d’accès aux outils sont disponibles à partir de kit SDK .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="5bb2c-248">Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="5bb2c-249">Commande</span><span class="sxs-lookup"><span data-stu-id="5bb2c-249">Command</span></span> | <span data-ttu-id="5bb2c-250">Fonction</span><span class="sxs-lookup"><span data-stu-id="5bb2c-250">Function</span></span>
--- | ---
[<span data-ttu-id="5bb2c-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="5bb2c-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="5bb2c-252">Installe un outil sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="5bb2c-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="5bb2c-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="5bb2c-254">Répertorie tous les outils globaux, de chemin d’accès d’outil ou locaux actuellement installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="5bb2c-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="5bb2c-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="5bb2c-256">Désinstalle un outil de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="5bb2c-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="5bb2c-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="5bb2c-258">Met à jour un outil qui est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="5bb2c-259">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5bb2c-259">Additional tools</span></span>

<span data-ttu-id="5bb2c-260">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="5bb2c-261">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="5bb2c-262">Outil</span><span class="sxs-lookup"><span data-stu-id="5bb2c-262">Tool</span></span>                                              | <span data-ttu-id="5bb2c-263">Fonction</span><span class="sxs-lookup"><span data-stu-id="5bb2c-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="5bb2c-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="5bb2c-264">dev-certs</span></span>                                         | <span data-ttu-id="5bb2c-265">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="5bb2c-266">ef</span><span class="sxs-lookup"><span data-stu-id="5bb2c-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="5bb2c-267">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="5bb2c-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="5bb2c-268">sql-cache</span></span>                                         | <span data-ttu-id="5bb2c-269">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="5bb2c-270">user-secrets</span><span class="sxs-lookup"><span data-stu-id="5bb2c-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="5bb2c-271">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="5bb2c-272">watch</span><span class="sxs-lookup"><span data-stu-id="5bb2c-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="5bb2c-273">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="5bb2c-274">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="5bb2c-275">Exemples</span><span class="sxs-lookup"><span data-stu-id="5bb2c-275">Examples</span></span>

<span data-ttu-id="5bb2c-276">Créez une application de console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="5bb2c-277">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="5bb2c-278">Exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="5bb2c-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="5bb2c-279">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="5bb2c-279">Environment variables</span></span>

- <span data-ttu-id="5bb2c-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="5bb2c-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="5bb2c-281">Spécifie l’emplacement des runtimes .NET Core, s’ils ne sont pas installés à l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="5bb2c-282">L’emplacement par défaut sur Windows est `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="5bb2c-283">L’emplacement par défaut sur Linux et macOS est `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="5bb2c-284">Cette variable d’environnement est utilisée uniquement lors de l’exécution d’applications via des exécutables générés (apphosts).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="5bb2c-285">`DOTNET_ROOT(x86)` est utilisé à la place lors de l’exécution d’un fichier exécutable 32 bits sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="5bb2c-286">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-286">The global packages folder.</span></span> <span data-ttu-id="5bb2c-287">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="5bb2c-288">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="5bb2c-289">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="5bb2c-290">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="5bb2c-291">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="5bb2c-292">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="5bb2c-293">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="5bb2c-294">S’il n’est pas défini, la valeur par défaut est 1 (`true`logique).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="5bb2c-295">Affectez la valeur 0 (`false`logique) pour ne pas résoudre à partir de l’emplacement global et disposer d’installations .NET Core isolées.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="5bb2c-296">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="5bb2c-297">`DOTNET_ROLL_FORWARD` **disponibles à partir du kit de développement logiciel (SDK) .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="5bb2c-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="5bb2c-298">Détermine le comportement de restauration par progression.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-298">Determines roll forward behavior.</span></span> <span data-ttu-id="5bb2c-299">Pour plus d’informations, consultez l’option `--roll-forward` plus haut dans cet article.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="5bb2c-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **disponibles dans le kit de développement logiciel (SDK) .net Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="5bb2c-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="5bb2c-301">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="5bb2c-302">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="5bb2c-303">Définit la langue de l’interface utilisateur CLI à l’aide d’une valeur de paramètres régionaux telle que `en-us`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="5bb2c-304">Les valeurs prises en charge sont les mêmes que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="5bb2c-305">Pour plus d’informations, consultez la section relative à la modification du langage d’installation dans la [documentation d’installation de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="5bb2c-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="5bb2c-306">Les règles .NET Resource Manager s’appliquent. vous n’avez donc pas besoin de choisir une correspondance exacte&mdash;vous pouvez également choisir des descendants dans l’arborescence des `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="5bb2c-307">Par exemple, si vous affectez la valeur `fr-CA`, l’interface CLI trouvera et utilisera les traductions `fr`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="5bb2c-308">Si vous définissez une langue qui n’est pas prise en charge, l’interface CLI revient à l’anglais.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="5bb2c-309">Pour les exécutables générés par l’interface utilisateur graphique : désactive la boîte de dialogue qui apparaît normalement pour certaines classes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="5bb2c-310">Il écrit uniquement dans `stderr` et se termine dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="5bb2c-311">Équivalent de l’option `--additional-deps`de l’interface CLI.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="5bb2c-312">Remplace le RID détecté.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="5bb2c-313">Emplacement du « magasin partagé » dans lequel la résolution de l’assembly revient dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="5bb2c-314">Liste des assemblys à partir desquels charger et exécuter des raccordements de démarrage.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="5bb2c-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="5bb2c-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="5bb2c-316">Contrôle le suivi des diagnostics à partir des composants d’hébergement, tels que `dotnet.exe`, `hostfxr`et `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="5bb2c-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5bb2c-317">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bb2c-317">See also</span></span>

- [<span data-ttu-id="5bb2c-318">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="5bb2c-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="5bb2c-319">Paramètres de configuration du Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="5bb2c-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
