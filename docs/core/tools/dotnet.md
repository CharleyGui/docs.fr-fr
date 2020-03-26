---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134078"
---
# <a name="dotnet-command"></a><span data-ttu-id="1725b-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="1725b-103">dotnet command</span></span>

<span data-ttu-id="1725b-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="1725b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1725b-105">Nom</span><span class="sxs-lookup"><span data-stu-id="1725b-105">Name</span></span>

<span data-ttu-id="1725b-106">`dotnet`- Le pilote générique pour le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1725b-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="1725b-107">Synopsis</span></span>

<span data-ttu-id="1725b-108">Pour obtenir des informations sur les commandes disponibles et l’environnement :</span><span class="sxs-lookup"><span data-stu-id="1725b-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="1725b-109">Pour exécuter une commande (nécessite l’installation SDK):</span><span class="sxs-lookup"><span data-stu-id="1725b-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="1725b-110">Pour exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="1725b-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="1725b-111">`--roll-forward`est disponible depuis .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="1725b-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="1725b-112">Utilisation `--roll-forward-on-no-candidate-fx` pour .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="1725b-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="1725b-113">Description</span><span class="sxs-lookup"><span data-stu-id="1725b-113">Description</span></span>

<span data-ttu-id="1725b-114">La `dotnet` commande a deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="1725b-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="1725b-115">Il fournit des commandes pour travailler avec des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="1725b-116">Par exemple, [`dotnet build`](dotnet-build.md) construit un projet.</span><span class="sxs-lookup"><span data-stu-id="1725b-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="1725b-117">Chaque commande définit ses propres options et arguments.</span><span class="sxs-lookup"><span data-stu-id="1725b-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="1725b-118">Toutes les commandes `--help` prennent en charge l’option d’imprimer de la documentation brève sur la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="1725b-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="1725b-119">Il exécute des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="1725b-120">Vous spécifiez `.dll` le chemin vers un fichier de demande pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="1725b-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="1725b-121">Par exemple, `dotnet myapp.dll` `myapp` exécute l’application.</span><span class="sxs-lookup"><span data-stu-id="1725b-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="1725b-122">Voir [le déploiement de l’application .NET Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.</span><span class="sxs-lookup"><span data-stu-id="1725b-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="1725b-123">Options</span><span class="sxs-lookup"><span data-stu-id="1725b-123">Options</span></span>

<span data-ttu-id="1725b-124">Différentes options sont `dotnet` disponibles pour lui-même, pour l’exécution d’une commande, et pour l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="1725b-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="1725b-125">Options pour dotnet par lui-même</span><span class="sxs-lookup"><span data-stu-id="1725b-125">Options for dotnet by itself</span></span>

<span data-ttu-id="1725b-126">Les options suivantes `dotnet` sont pour lui-même.</span><span class="sxs-lookup"><span data-stu-id="1725b-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="1725b-127">Par exemple : `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="1725b-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="1725b-128">Ils impriment des informations sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="1725b-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="1725b-129">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="1725b-130">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="1725b-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="1725b-131">Imprime une liste des temps d’exécution .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="1725b-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="1725b-132">Imprime une liste des SDKs .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="1725b-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1725b-133">Imprime une liste de commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="1725b-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="1725b-134">Options SDK pour l’exécution d’une commande</span><span class="sxs-lookup"><span data-stu-id="1725b-134">SDK options for running a command</span></span>

<span data-ttu-id="1725b-135">Les options suivantes `dotnet` sont pour avec une commande.</span><span class="sxs-lookup"><span data-stu-id="1725b-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="1725b-136">Par exemple : `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="1725b-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="1725b-137">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="1725b-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="1725b-138">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="1725b-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1725b-139">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1725b-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1725b-140">Pas pris en charge dans tous les commandements.</span><span class="sxs-lookup"><span data-stu-id="1725b-140">Not supported in every command.</span></span> <span data-ttu-id="1725b-141">Voir la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="1725b-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1725b-142">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="1725b-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="1725b-143">Chaque commande définit les options spécifiques à cette commande.</span><span class="sxs-lookup"><span data-stu-id="1725b-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="1725b-144">Voir la page de commande spécifique pour une liste d’options disponibles.</span><span class="sxs-lookup"><span data-stu-id="1725b-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="1725b-145">Options d’exécution</span><span class="sxs-lookup"><span data-stu-id="1725b-145">Runtime options</span></span>

<span data-ttu-id="1725b-146">Les options suivantes `dotnet` sont disponibles lors de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="1725b-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="1725b-147">Par exemple : `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="1725b-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="1725b-148">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="1725b-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="1725b-149">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="1725b-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="1725b-150">Un fichier *deps.json* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour résoudre les conflits d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="1725b-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="1725b-151">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="1725b-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="1725b-152">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="1725b-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="1725b-153">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="1725b-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="1725b-154">Un fichier *runtimeconfig.json* est un fichier de configuration qui contient des paramètres de temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="1725b-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="1725b-155">Pour plus d’informations, voir [paramètres de configuration .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="1725b-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="1725b-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponible en .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="1725b-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="1725b-157">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="1725b-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="1725b-158">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="1725b-158">`N` can be:</span></span>

  - <span data-ttu-id="1725b-159">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="1725b-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="1725b-160">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="1725b-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="1725b-161">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="1725b-161">This is the default behavior.</span></span>
  - <span data-ttu-id="1725b-162">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="1725b-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="1725b-163">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="1725b-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="1725b-164">**`--roll-forward <SETTING>`\*\*\*\*Disponible en commençant par .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="1725b-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="1725b-165">Contrôle la façon dont le rouleau vers l’avant est appliqué à l’application.</span><span class="sxs-lookup"><span data-stu-id="1725b-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="1725b-166">La `SETTING` peut être l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="1725b-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="1725b-167">S’il `Minor` n’est pas spécifié, est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="1725b-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="1725b-168">`LatestPatch`- Roulez vers la version patch la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="1725b-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="1725b-169">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="1725b-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="1725b-170">`Minor`- Rouler vers l’avant à la version mineure supérieure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="1725b-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="1725b-171">Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1725b-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="1725b-172">`Major`- Rouler vers l’avant à la version principale supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="1725b-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="1725b-173">Si la version majeure demandée est présente, la stratégie Minor est utilisée.</span><span class="sxs-lookup"><span data-stu-id="1725b-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="1725b-174">`LatestMinor`- Rouler vers la version mineure la plus élevée, même si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="1725b-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="1725b-175">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="1725b-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="1725b-176">`LatestMajor`- Rouler vers l’avant à la plus haute version mineure majeure et la plus élevée, même si demandé majeur est présent.</span><span class="sxs-lookup"><span data-stu-id="1725b-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="1725b-177">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="1725b-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="1725b-178">`Disable`- Ne roulez pas vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="1725b-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="1725b-179">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1725b-179">Only bind to specified version.</span></span> <span data-ttu-id="1725b-180">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="1725b-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="1725b-181">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="1725b-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="1725b-182">À l’exception de `Disable`, tous les paramètres utiliseront la version patch disponible la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="1725b-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="1725b-183">Le comportement de roll forward peut également être configuré dans une propriété de fichier de projet, une propriété de fichier de configuration de temps d’exécution, et une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="1725b-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="1725b-184">Pour plus d’informations, voir [Le roll time de la version majeure vers l’avant](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="1725b-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="1725b-185">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="1725b-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="1725b-186">Général</span><span class="sxs-lookup"><span data-stu-id="1725b-186">General</span></span>

| <span data-ttu-id="1725b-187">Commande</span><span class="sxs-lookup"><span data-stu-id="1725b-187">Command</span></span>                                       | <span data-ttu-id="1725b-188">Fonction</span><span class="sxs-lookup"><span data-stu-id="1725b-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="1725b-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="1725b-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="1725b-190">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="1725b-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="1725b-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="1725b-192">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="1725b-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="1725b-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="1725b-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="1725b-194">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="1725b-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="1725b-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="1725b-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="1725b-196">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="1725b-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="1725b-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="1725b-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="1725b-198">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="1725b-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="1725b-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1725b-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="1725b-200">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1725b-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="1725b-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="1725b-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="1725b-202">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="1725b-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="1725b-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="1725b-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="1725b-204">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="1725b-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="1725b-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="1725b-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="1725b-206">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="1725b-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="1725b-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="1725b-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="1725b-208">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="1725b-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="1725b-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="1725b-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="1725b-210">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="1725b-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="1725b-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="1725b-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="1725b-212">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="1725b-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="1725b-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="1725b-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="1725b-214">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="1725b-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="1725b-215">test dotnet</span><span class="sxs-lookup"><span data-stu-id="1725b-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="1725b-216">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="1725b-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="1725b-217">Références de projets</span><span class="sxs-lookup"><span data-stu-id="1725b-217">Project references</span></span>

<span data-ttu-id="1725b-218">Commande</span><span class="sxs-lookup"><span data-stu-id="1725b-218">Command</span></span> | <span data-ttu-id="1725b-219">Fonction</span><span class="sxs-lookup"><span data-stu-id="1725b-219">Function</span></span>
--- | ---
[<span data-ttu-id="1725b-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="1725b-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="1725b-221">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="1725b-221">Adds a project reference.</span></span>
[<span data-ttu-id="1725b-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="1725b-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="1725b-223">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="1725b-223">Lists project references.</span></span>
[<span data-ttu-id="1725b-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="1725b-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="1725b-225">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="1725b-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="1725b-226">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="1725b-226">NuGet packages</span></span>

<span data-ttu-id="1725b-227">Commande</span><span class="sxs-lookup"><span data-stu-id="1725b-227">Command</span></span> | <span data-ttu-id="1725b-228">Fonction</span><span class="sxs-lookup"><span data-stu-id="1725b-228">Function</span></span>
--- | ---
[<span data-ttu-id="1725b-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="1725b-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="1725b-230">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="1725b-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="1725b-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="1725b-232">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="1725b-233">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="1725b-233">NuGet commands</span></span>

<span data-ttu-id="1725b-234">Commande</span><span class="sxs-lookup"><span data-stu-id="1725b-234">Command</span></span> | <span data-ttu-id="1725b-235">Fonction</span><span class="sxs-lookup"><span data-stu-id="1725b-235">Function</span></span>
--- | ---
[<span data-ttu-id="1725b-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="1725b-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="1725b-237">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="1725b-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="1725b-238">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="1725b-238">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="1725b-239">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="1725b-239">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="1725b-240">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="1725b-240">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="1725b-241">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1725b-241">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="1725b-242">dotnet nuget ajouter source</span><span class="sxs-lookup"><span data-stu-id="1725b-242">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="1725b-243">Ajoute une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-243">Adds a NuGet source.</span></span>
[<span data-ttu-id="1725b-244">dotnet nuget source désactiver</span><span class="sxs-lookup"><span data-stu-id="1725b-244">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="1725b-245">Désactive une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-245">Disables a NuGet source.</span></span>
[<span data-ttu-id="1725b-246">dotnet nuget activer la source</span><span class="sxs-lookup"><span data-stu-id="1725b-246">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="1725b-247">Permet une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-247">Enables a NuGet source.</span></span>
[<span data-ttu-id="1725b-248">dotnet nuget liste source</span><span class="sxs-lookup"><span data-stu-id="1725b-248">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="1725b-249">Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="1725b-249">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="1725b-250">dotnet nuget supprimer la source</span><span class="sxs-lookup"><span data-stu-id="1725b-250">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="1725b-251">Supprime une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-251">Removes a NuGet source.</span></span>
[<span data-ttu-id="1725b-252">source de mise à jour de nuget dotnet</span><span class="sxs-lookup"><span data-stu-id="1725b-252">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="1725b-253">Mise à jour d’une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="1725b-253">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="1725b-254">Commandes d’outils mondiaux, d’outils et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="1725b-254">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="1725b-255">Les outils sont des applications de console qui sont installées à partir de paquets NuGet et sont invoquées à partir de l’invite de commande.</span><span class="sxs-lookup"><span data-stu-id="1725b-255">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="1725b-256">Vous pouvez écrire des outils vous-même ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="1725b-256">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="1725b-257">Les outils sont également connus sous le nom d’outils globaux, d’outils de chemin à outils et d’outils locaux.</span><span class="sxs-lookup"><span data-stu-id="1725b-257">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="1725b-258">Pour plus d’informations, voir [.NET Core outils aperçu](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="1725b-258">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="1725b-259">Des outils globaux et de chemin d’outils sont disponibles à partir de .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="1725b-259">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="1725b-260">Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="1725b-260">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="1725b-261">Commande</span><span class="sxs-lookup"><span data-stu-id="1725b-261">Command</span></span> | <span data-ttu-id="1725b-262">Fonction</span><span class="sxs-lookup"><span data-stu-id="1725b-262">Function</span></span>
--- | ---
[<span data-ttu-id="1725b-263">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="1725b-263">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="1725b-264">Installe un outil sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="1725b-264">Installs a tool on your machine.</span></span>
[<span data-ttu-id="1725b-265">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="1725b-265">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="1725b-266">Répertorie tous les outils globaux, de chemin d’outils ou locaux actuellement installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="1725b-266">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="1725b-267">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="1725b-267">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="1725b-268">Désinstalle un outil de votre machine.</span><span class="sxs-lookup"><span data-stu-id="1725b-268">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="1725b-269">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="1725b-269">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="1725b-270">Mise à jour d’un outil qui est installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="1725b-270">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="1725b-271">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="1725b-271">Additional tools</span></span>

<span data-ttu-id="1725b-272">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-272">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="1725b-273">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="1725b-273">These tools are listed in the following table:</span></span>

| <span data-ttu-id="1725b-274">Outil</span><span class="sxs-lookup"><span data-stu-id="1725b-274">Tool</span></span>                                              | <span data-ttu-id="1725b-275">Fonction</span><span class="sxs-lookup"><span data-stu-id="1725b-275">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="1725b-276">dev-certs</span><span class="sxs-lookup"><span data-stu-id="1725b-276">dev-certs</span></span>                                         | <span data-ttu-id="1725b-277">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="1725b-277">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="1725b-278">Ef</span><span class="sxs-lookup"><span data-stu-id="1725b-278">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="1725b-279">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-279">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="1725b-280">sql-cache</span><span class="sxs-lookup"><span data-stu-id="1725b-280">sql-cache</span></span>                                         | <span data-ttu-id="1725b-281">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1725b-281">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="1725b-282">user-secrets</span><span class="sxs-lookup"><span data-stu-id="1725b-282">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="1725b-283">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1725b-283">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="1725b-284">Regarder</span><span class="sxs-lookup"><span data-stu-id="1725b-284">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="1725b-285">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="1725b-285">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="1725b-286">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="1725b-286">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="1725b-287">Exemples</span><span class="sxs-lookup"><span data-stu-id="1725b-287">Examples</span></span>

<span data-ttu-id="1725b-288">Créez une nouvelle application de console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="1725b-288">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="1725b-289">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="1725b-289">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="1725b-290">Exécuter une application:</span><span class="sxs-lookup"><span data-stu-id="1725b-290">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="1725b-291">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="1725b-291">Environment variables</span></span>

- <span data-ttu-id="1725b-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="1725b-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="1725b-293">Spécifie l’emplacement des temps d’exécution .NET Core, s’ils ne sont pas installés dans l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="1725b-293">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="1725b-294">L’emplacement par `C:\Program Files\dotnet`défaut sur Windows est .</span><span class="sxs-lookup"><span data-stu-id="1725b-294">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="1725b-295">L’emplacement par défaut sur `/usr/share/dotnet`Linux et macOS est .</span><span class="sxs-lookup"><span data-stu-id="1725b-295">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="1725b-296">Cette variable d’environnement n’est utilisée que lorsque vous exécutez des applications via des exécutables générés (apphosts).</span><span class="sxs-lookup"><span data-stu-id="1725b-296">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="1725b-297">`DOTNET_ROOT(x86)`est utilisé à la place lors de l’exécution d’un 32 bits exécutable sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="1725b-297">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="1725b-298">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="1725b-298">The global packages folder.</span></span> <span data-ttu-id="1725b-299">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="1725b-299">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="1725b-300">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1725b-300">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="1725b-301">Précise si les messages de bienvenue et de télémétrie .NET Core sont affichés en première diffusion.</span><span class="sxs-lookup"><span data-stu-id="1725b-301">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="1725b-302">Configurez `true` pour couper ces `true` `1`messages `yes` (valeurs, , `false` ou acceptés) ou définis pour permettre (valeurs, `false` `0`, ou `no` accepté).</span><span class="sxs-lookup"><span data-stu-id="1725b-302">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="1725b-303">Si elle n’est `false` pas définie, la valeur par défaut est et les messages seront affichés en première exécution.</span><span class="sxs-lookup"><span data-stu-id="1725b-303">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="1725b-304">Notez que ce drapeau n’a `DOTNET_CLI_TELEMETRY_OPTOUT` aucun effet sur la télémétrie (voir pour refuser d’envoyer de la télémétrie).</span><span class="sxs-lookup"><span data-stu-id="1725b-304">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="1725b-305">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1725b-305">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="1725b-306">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="1725b-306">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="1725b-307">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="1725b-307">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="1725b-308">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="1725b-308">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="1725b-309">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="1725b-309">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="1725b-310">Si elle n’est pas réglée, `true`elle par défaut à 1 (logique).</span><span class="sxs-lookup"><span data-stu-id="1725b-310">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="1725b-311">Set à 0 `false`(logique) pour ne pas résoudre à partir de l’emplacement global et ont isolé les installations .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1725b-311">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="1725b-312">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="1725b-312">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="1725b-313">`DOTNET_ROLL_FORWARD`**Disponible en commençant par .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="1725b-313">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="1725b-314">Détermine le comportement de rouler vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="1725b-314">Determines roll forward behavior.</span></span> <span data-ttu-id="1725b-315">Pour plus d’informations, voir l’option `--roll-forward` plus tôt dans cet article.</span><span class="sxs-lookup"><span data-stu-id="1725b-315">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="1725b-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponible en .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="1725b-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="1725b-317">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="1725b-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="1725b-318">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="1725b-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="1725b-319">Définit la langue de l’interface utilisateur CLI en utilisant une valeur locale telle que `en-us`.</span><span class="sxs-lookup"><span data-stu-id="1725b-319">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="1725b-320">Les valeurs prises en charge sont les mêmes que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1725b-320">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="1725b-321">Pour plus d’informations, voir la section sur la modification de la langue de l’installateur dans la [documentation d’installation Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="1725b-321">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="1725b-322">Les règles de gestionnaire de ressources .NET s’appliquent, de sorte que vous n’avez pas à choisir un match&mdash;exact, vous pouvez également choisir les descendants dans l’arbre. `CultureInfo`</span><span class="sxs-lookup"><span data-stu-id="1725b-322">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="1725b-323">Par exemple, si vous `fr-CA`le définissez, le `fr` CLI trouvera et utilisera les traductions.</span><span class="sxs-lookup"><span data-stu-id="1725b-323">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="1725b-324">Si vous le définissez dans une langue qui n’est pas prise en charge, l’IMC retombe à l’anglais.</span><span class="sxs-lookup"><span data-stu-id="1725b-324">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="1725b-325">Pour les exécutables générés par l’INTERFACE graphique - désactive le dialogue popup, qui montre normalement pour certaines classes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="1725b-325">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="1725b-326">Il n’écrit `stderr` et sort que dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="1725b-326">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="1725b-327">Équivalent à l’option `--additional-deps`CLI .</span><span class="sxs-lookup"><span data-stu-id="1725b-327">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="1725b-328">Remplace le RID détecté.</span><span class="sxs-lookup"><span data-stu-id="1725b-328">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="1725b-329">L’emplacement du « magasin partagé » auquel la résolution d’assemblage revient dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="1725b-329">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="1725b-330">Liste des assemblages à charger et exécuter des crochets de démarrage à partir de.</span><span class="sxs-lookup"><span data-stu-id="1725b-330">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="1725b-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="1725b-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="1725b-332">Contrôle les diagnostics traçant à `dotnet.exe`partir `hostfxr`des `hostpolicy`composants d’hébergement, tels que , , et .</span><span class="sxs-lookup"><span data-stu-id="1725b-332">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="1725b-333">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1725b-333">See also</span></span>

- [<span data-ttu-id="1725b-334">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="1725b-334">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="1725b-335">paramètres de configuration de temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="1725b-335">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
