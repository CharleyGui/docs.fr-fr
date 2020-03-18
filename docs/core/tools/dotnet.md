---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398894"
---
# <a name="dotnet-command"></a><span data-ttu-id="a2575-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="a2575-103">dotnet command</span></span>

<span data-ttu-id="a2575-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="a2575-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a2575-105">Nom</span><span class="sxs-lookup"><span data-stu-id="a2575-105">Name</span></span>

<span data-ttu-id="a2575-106">`dotnet`- Le pilote générique pour le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2575-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="a2575-107">Synopsis</span></span>

<span data-ttu-id="a2575-108">Pour obtenir des informations sur les commandes disponibles et l’environnement :</span><span class="sxs-lookup"><span data-stu-id="a2575-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="a2575-109">Pour exécuter une commande (nécessite l’installation SDK):</span><span class="sxs-lookup"><span data-stu-id="a2575-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="a2575-110">Pour exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="a2575-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="a2575-111">`--roll-forward`est disponible depuis .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="a2575-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="a2575-112">Utilisation `--roll-forward-on-no-candidate-fx` pour .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="a2575-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="a2575-113">Description</span><span class="sxs-lookup"><span data-stu-id="a2575-113">Description</span></span>

<span data-ttu-id="a2575-114">La `dotnet` commande a deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="a2575-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="a2575-115">Il fournit des commandes pour travailler avec des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="a2575-116">Par exemple, [`dotnet build`](dotnet-build.md) construit un projet.</span><span class="sxs-lookup"><span data-stu-id="a2575-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="a2575-117">Chaque commande définit ses propres options et arguments.</span><span class="sxs-lookup"><span data-stu-id="a2575-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="a2575-118">Toutes les commandes `--help` prennent en charge l’option d’imprimer de la documentation brève sur la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="a2575-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="a2575-119">Il exécute des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="a2575-120">Vous spécifiez `.dll` le chemin vers un fichier de demande pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="a2575-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="a2575-121">Par exemple, `dotnet myapp.dll` `myapp` exécute l’application.</span><span class="sxs-lookup"><span data-stu-id="a2575-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="a2575-122">Voir [le déploiement de l’application .NET Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.</span><span class="sxs-lookup"><span data-stu-id="a2575-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="a2575-123">Options</span><span class="sxs-lookup"><span data-stu-id="a2575-123">Options</span></span>

<span data-ttu-id="a2575-124">Différentes options sont `dotnet` disponibles pour lui-même, pour l’exécution d’une commande, et pour l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="a2575-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="a2575-125">Options pour dotnet par lui-même</span><span class="sxs-lookup"><span data-stu-id="a2575-125">Options for dotnet by itself</span></span>

<span data-ttu-id="a2575-126">Les options suivantes `dotnet` sont pour lui-même.</span><span class="sxs-lookup"><span data-stu-id="a2575-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="a2575-127">Par exemple : `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="a2575-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="a2575-128">Ils impriment des informations sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="a2575-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="a2575-129">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="a2575-130">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="a2575-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="a2575-131">Imprime une liste des temps d’exécution .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="a2575-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="a2575-132">Imprime une liste des SDKs .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="a2575-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a2575-133">Imprime une liste de commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="a2575-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="a2575-134">Options SDK pour l’exécution d’une commande</span><span class="sxs-lookup"><span data-stu-id="a2575-134">SDK options for running a command</span></span>

<span data-ttu-id="a2575-135">Les options suivantes `dotnet` sont pour avec une commande.</span><span class="sxs-lookup"><span data-stu-id="a2575-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="a2575-136">Par exemple : `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a2575-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="a2575-137">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="a2575-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="a2575-138">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="a2575-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a2575-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a2575-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="a2575-140">Pas pris en charge dans tous les commandements.</span><span class="sxs-lookup"><span data-stu-id="a2575-140">Not supported in every command.</span></span> <span data-ttu-id="a2575-141">Voir la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="a2575-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a2575-142">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="a2575-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="a2575-143">Chaque commande définit les options spécifiques à cette commande.</span><span class="sxs-lookup"><span data-stu-id="a2575-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="a2575-144">Voir la page de commande spécifique pour une liste d’options disponibles.</span><span class="sxs-lookup"><span data-stu-id="a2575-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="a2575-145">Options d’exécution</span><span class="sxs-lookup"><span data-stu-id="a2575-145">Runtime options</span></span>

<span data-ttu-id="a2575-146">Les options suivantes `dotnet` sont disponibles lors de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="a2575-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="a2575-147">Par exemple : `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="a2575-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="a2575-148">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="a2575-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="a2575-149">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="a2575-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="a2575-150">Un fichier *deps.json* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour résoudre les conflits d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="a2575-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="a2575-151">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="a2575-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="a2575-152">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="a2575-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="a2575-153">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="a2575-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="a2575-154">Un fichier *runtimeconfig.json* est un fichier de configuration qui contient des paramètres de temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="a2575-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="a2575-155">Pour plus d’informations, voir [paramètres de configuration .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="a2575-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="a2575-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponible en .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="a2575-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="a2575-157">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="a2575-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="a2575-158">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="a2575-158">`N` can be:</span></span>

  - <span data-ttu-id="a2575-159">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="a2575-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="a2575-160">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="a2575-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="a2575-161">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2575-161">This is the default behavior.</span></span>
  - <span data-ttu-id="a2575-162">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="a2575-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="a2575-163">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a2575-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="a2575-164">**`--roll-forward <SETTING>`\*\*\*\*Disponible en commençant par .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="a2575-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="a2575-165">Contrôle la façon dont le rouleau vers l’avant est appliqué à l’application.</span><span class="sxs-lookup"><span data-stu-id="a2575-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="a2575-166">La `SETTING` peut être l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="a2575-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="a2575-167">S’il `Minor` n’est pas spécifié, est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2575-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="a2575-168">`LatestPatch`- Roulez vers la version patch la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="a2575-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="a2575-169">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="a2575-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="a2575-170">`Minor`- Rouler vers l’avant à la version mineure supérieure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="a2575-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="a2575-171">Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a2575-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="a2575-172">`Major`- Rouler vers l’avant à la version principale supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="a2575-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="a2575-173">Si la version majeure demandée est présente, la stratégie Minor est utilisée.</span><span class="sxs-lookup"><span data-stu-id="a2575-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="a2575-174">`LatestMinor`- Rouler vers la version mineure la plus élevée, même si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="a2575-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="a2575-175">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="a2575-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="a2575-176">`LatestMajor`- Rouler vers l’avant à la plus haute version mineure majeure et la plus élevée, même si demandé majeur est présent.</span><span class="sxs-lookup"><span data-stu-id="a2575-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="a2575-177">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="a2575-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="a2575-178">`Disable`- Ne roulez pas vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="a2575-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="a2575-179">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a2575-179">Only bind to specified version.</span></span> <span data-ttu-id="a2575-180">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="a2575-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="a2575-181">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="a2575-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="a2575-182">À l’exception de `Disable`, tous les paramètres utiliseront la version patch disponible la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="a2575-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="a2575-183">Le comportement de roll forward peut également être configuré dans une propriété de fichier de projet, une propriété de fichier de configuration de temps d’exécution, et une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="a2575-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="a2575-184">Pour plus d’informations, voir [Le roll time de la version majeure vers l’avant](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a2575-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="a2575-185">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="a2575-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="a2575-186">Général</span><span class="sxs-lookup"><span data-stu-id="a2575-186">General</span></span>

| <span data-ttu-id="a2575-187">Commande</span><span class="sxs-lookup"><span data-stu-id="a2575-187">Command</span></span>                                       | <span data-ttu-id="a2575-188">Fonction</span><span class="sxs-lookup"><span data-stu-id="a2575-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="a2575-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="a2575-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="a2575-190">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="a2575-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="a2575-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="a2575-192">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="a2575-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="a2575-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="a2575-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="a2575-194">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="a2575-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="a2575-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="a2575-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="a2575-196">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="a2575-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="a2575-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="a2575-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="a2575-198">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="a2575-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="a2575-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a2575-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="a2575-200">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="a2575-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="a2575-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="a2575-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="a2575-202">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="a2575-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="a2575-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a2575-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="a2575-204">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a2575-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="a2575-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="a2575-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="a2575-206">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="a2575-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="a2575-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="a2575-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="a2575-208">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="a2575-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="a2575-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="a2575-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="a2575-210">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="a2575-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="a2575-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="a2575-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="a2575-212">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="a2575-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="a2575-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="a2575-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="a2575-214">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="a2575-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="a2575-215">test dotnet</span><span class="sxs-lookup"><span data-stu-id="a2575-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="a2575-216">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="a2575-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="a2575-217">Références de projets</span><span class="sxs-lookup"><span data-stu-id="a2575-217">Project references</span></span>

<span data-ttu-id="a2575-218">Commande</span><span class="sxs-lookup"><span data-stu-id="a2575-218">Command</span></span> | <span data-ttu-id="a2575-219">Fonction</span><span class="sxs-lookup"><span data-stu-id="a2575-219">Function</span></span>
--- | ---
[<span data-ttu-id="a2575-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="a2575-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="a2575-221">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="a2575-221">Adds a project reference.</span></span>
[<span data-ttu-id="a2575-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="a2575-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="a2575-223">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="a2575-223">Lists project references.</span></span>
[<span data-ttu-id="a2575-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="a2575-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="a2575-225">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="a2575-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="a2575-226">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="a2575-226">NuGet packages</span></span>

<span data-ttu-id="a2575-227">Commande</span><span class="sxs-lookup"><span data-stu-id="a2575-227">Command</span></span> | <span data-ttu-id="a2575-228">Fonction</span><span class="sxs-lookup"><span data-stu-id="a2575-228">Function</span></span>
--- | ---
[<span data-ttu-id="a2575-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="a2575-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="a2575-230">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a2575-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="a2575-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="a2575-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="a2575-232">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="a2575-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="a2575-233">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="a2575-233">NuGet commands</span></span>

<span data-ttu-id="a2575-234">Commande</span><span class="sxs-lookup"><span data-stu-id="a2575-234">Command</span></span> | <span data-ttu-id="a2575-235">Fonction</span><span class="sxs-lookup"><span data-stu-id="a2575-235">Function</span></span>
--- | ---
[<span data-ttu-id="a2575-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="a2575-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="a2575-237">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="a2575-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="a2575-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="a2575-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="a2575-239">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a2575-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="a2575-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="a2575-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="a2575-241">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="a2575-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="a2575-242">Commandes d’outils mondiaux, d’outils et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="a2575-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="a2575-243">Les outils sont des applications de console qui sont installées à partir de paquets NuGet et sont invoquées à partir de l’invite de commande.</span><span class="sxs-lookup"><span data-stu-id="a2575-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="a2575-244">Vous pouvez écrire des outils vous-même ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="a2575-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="a2575-245">Les outils sont également connus sous le nom d’outils globaux, d’outils de chemin à outils et d’outils locaux.</span><span class="sxs-lookup"><span data-stu-id="a2575-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="a2575-246">Pour plus d’informations, voir [.NET Core outils aperçu](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="a2575-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="a2575-247">Des outils globaux et de chemin d’outils sont disponibles à partir de .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="a2575-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="a2575-248">Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="a2575-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="a2575-249">Commande</span><span class="sxs-lookup"><span data-stu-id="a2575-249">Command</span></span> | <span data-ttu-id="a2575-250">Fonction</span><span class="sxs-lookup"><span data-stu-id="a2575-250">Function</span></span>
--- | ---
[<span data-ttu-id="a2575-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="a2575-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="a2575-252">Installe un outil sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="a2575-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="a2575-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="a2575-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="a2575-254">Répertorie tous les outils globaux, de chemin d’outils ou locaux actuellement installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="a2575-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="a2575-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="a2575-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="a2575-256">Désinstalle un outil de votre machine.</span><span class="sxs-lookup"><span data-stu-id="a2575-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="a2575-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="a2575-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="a2575-258">Mise à jour d’un outil qui est installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="a2575-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="a2575-259">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="a2575-259">Additional tools</span></span>

<span data-ttu-id="a2575-260">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="a2575-261">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="a2575-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="a2575-262">Outil</span><span class="sxs-lookup"><span data-stu-id="a2575-262">Tool</span></span>                                              | <span data-ttu-id="a2575-263">Fonction</span><span class="sxs-lookup"><span data-stu-id="a2575-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="a2575-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="a2575-264">dev-certs</span></span>                                         | <span data-ttu-id="a2575-265">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="a2575-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="a2575-266">Ef</span><span class="sxs-lookup"><span data-stu-id="a2575-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="a2575-267">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="a2575-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="a2575-268">sql-cache</span></span>                                         | <span data-ttu-id="a2575-269">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a2575-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="a2575-270">user-secrets</span><span class="sxs-lookup"><span data-stu-id="a2575-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="a2575-271">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a2575-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="a2575-272">Regarder</span><span class="sxs-lookup"><span data-stu-id="a2575-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="a2575-273">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="a2575-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="a2575-274">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="a2575-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="a2575-275">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2575-275">Examples</span></span>

<span data-ttu-id="a2575-276">Créez une nouvelle application de console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="a2575-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="a2575-277">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="a2575-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="a2575-278">Exécuter une application:</span><span class="sxs-lookup"><span data-stu-id="a2575-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="a2575-279">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="a2575-279">Environment variables</span></span>

- <span data-ttu-id="a2575-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="a2575-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="a2575-281">Spécifie l’emplacement des temps d’exécution .NET Core, s’ils ne sont pas installés dans l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="a2575-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="a2575-282">L’emplacement par `C:\Program Files\dotnet`défaut sur Windows est .</span><span class="sxs-lookup"><span data-stu-id="a2575-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="a2575-283">L’emplacement par défaut sur `/usr/share/dotnet`Linux et macOS est .</span><span class="sxs-lookup"><span data-stu-id="a2575-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="a2575-284">Cette variable d’environnement n’est utilisée que lorsque vous exécutez des applications via des exécutables générés (apphosts).</span><span class="sxs-lookup"><span data-stu-id="a2575-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="a2575-285">`DOTNET_ROOT(x86)`est utilisé à la place lors de l’exécution d’un 32 bits exécutable sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="a2575-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="a2575-286">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="a2575-286">The global packages folder.</span></span> <span data-ttu-id="a2575-287">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="a2575-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="a2575-288">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a2575-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="a2575-289">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a2575-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="a2575-290">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="a2575-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="a2575-291">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="a2575-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="a2575-292">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="a2575-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="a2575-293">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="a2575-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="a2575-294">Si elle n’est pas réglée, `true`elle par défaut à 1 (logique).</span><span class="sxs-lookup"><span data-stu-id="a2575-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="a2575-295">Set à 0 `false`(logique) pour ne pas résoudre à partir de l’emplacement global et ont isolé les installations .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a2575-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="a2575-296">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="a2575-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="a2575-297">`DOTNET_ROLL_FORWARD`**Disponible en commençant par .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="a2575-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="a2575-298">Détermine le comportement de rouler vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="a2575-298">Determines roll forward behavior.</span></span> <span data-ttu-id="a2575-299">Pour plus d’informations, voir l’option `--roll-forward` plus tôt dans cet article.</span><span class="sxs-lookup"><span data-stu-id="a2575-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="a2575-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponible en .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="a2575-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="a2575-301">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="a2575-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="a2575-302">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="a2575-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="a2575-303">Définit la langue de l’interface utilisateur CLI en utilisant une valeur locale telle que `en-us`.</span><span class="sxs-lookup"><span data-stu-id="a2575-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="a2575-304">Les valeurs prises en charge sont les mêmes que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2575-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="a2575-305">Pour plus d’informations, voir la section sur la modification de la langue de l’installateur dans la [documentation d’installation Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="a2575-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="a2575-306">Les règles de gestionnaire de ressources .NET s’appliquent, de sorte que vous n’avez pas à choisir un match&mdash;exact, vous pouvez également choisir les descendants dans l’arbre. `CultureInfo`</span><span class="sxs-lookup"><span data-stu-id="a2575-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="a2575-307">Par exemple, si vous `fr-CA`le définissez, le `fr` CLI trouvera et utilisera les traductions.</span><span class="sxs-lookup"><span data-stu-id="a2575-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="a2575-308">Si vous le définissez dans une langue qui n’est pas prise en charge, l’IMC retombe à l’anglais.</span><span class="sxs-lookup"><span data-stu-id="a2575-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="a2575-309">Pour les exécutables générés par l’INTERFACE graphique - désactive le popup de dialogue qui s’affiche normalement pour certaines classes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="a2575-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="a2575-310">Il n’écrit `stderr` et sort que dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="a2575-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="a2575-311">Équivalent à l’option `--additional-deps`CLI .</span><span class="sxs-lookup"><span data-stu-id="a2575-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="a2575-312">Remplace le RID détecté.</span><span class="sxs-lookup"><span data-stu-id="a2575-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="a2575-313">L’emplacement du « magasin partagé » auquel la résolution d’assemblage revient dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="a2575-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="a2575-314">Liste des assemblages à charger et exécuter des crochets de démarrage à partir de.</span><span class="sxs-lookup"><span data-stu-id="a2575-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="a2575-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="a2575-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="a2575-316">Contrôle les diagnostics traçant à `dotnet.exe`partir `hostfxr`des `hostpolicy`composants d’hébergement, tels que , , et .</span><span class="sxs-lookup"><span data-stu-id="a2575-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2575-317">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2575-317">See also</span></span>

- [<span data-ttu-id="a2575-318">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="a2575-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="a2575-319">paramètres de configuration de temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="a2575-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
