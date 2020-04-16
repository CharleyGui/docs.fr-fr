---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: d700f35f3c977524ff3857da99519882eb0136e9
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463266"
---
# <a name="dotnet-command"></a><span data-ttu-id="0fd13-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="0fd13-103">dotnet command</span></span>

<span data-ttu-id="0fd13-104">**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="0fd13-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0fd13-105">Nom</span><span class="sxs-lookup"><span data-stu-id="0fd13-105">Name</span></span>

<span data-ttu-id="0fd13-106">`dotnet`- Le pilote générique pour le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0fd13-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="0fd13-107">Synopsis</span></span>

<span data-ttu-id="0fd13-108">Pour obtenir des informations sur les commandes disponibles et l’environnement :</span><span class="sxs-lookup"><span data-stu-id="0fd13-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="0fd13-109">Pour exécuter une commande (nécessite l’installation SDK):</span><span class="sxs-lookup"><span data-stu-id="0fd13-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="0fd13-110">Pour exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="0fd13-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="0fd13-111">`--roll-forward`est disponible depuis .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="0fd13-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="0fd13-112">Utilisation `--roll-forward-on-no-candidate-fx` pour .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="0fd13-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="0fd13-113">Description</span><span class="sxs-lookup"><span data-stu-id="0fd13-113">Description</span></span>

<span data-ttu-id="0fd13-114">La `dotnet` commande a deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="0fd13-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="0fd13-115">Il fournit des commandes pour travailler avec des projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="0fd13-116">Par exemple, [`dotnet build`](dotnet-build.md) construit un projet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="0fd13-117">Chaque commande définit ses propres options et arguments.</span><span class="sxs-lookup"><span data-stu-id="0fd13-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="0fd13-118">Toutes les commandes `--help` prennent en charge l’option d’imprimer de la documentation brève sur la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="0fd13-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="0fd13-119">Il exécute des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="0fd13-120">Vous spécifiez `.dll` le chemin vers un fichier de demande pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="0fd13-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="0fd13-121">Pour exécuter l’application signifie trouver et exécuter le point d’entrée, qui dans le cas des applications console est la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="0fd13-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="0fd13-122">Par exemple, `dotnet myapp.dll` `myapp` exécute l’application.</span><span class="sxs-lookup"><span data-stu-id="0fd13-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="0fd13-123">Voir [le déploiement de l’application .NET Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.</span><span class="sxs-lookup"><span data-stu-id="0fd13-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="0fd13-124">Options</span><span class="sxs-lookup"><span data-stu-id="0fd13-124">Options</span></span>

<span data-ttu-id="0fd13-125">Différentes options sont `dotnet` disponibles pour lui-même, pour l’exécution d’une commande, et pour l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="0fd13-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="0fd13-126">Options pour dotnet par lui-même</span><span class="sxs-lookup"><span data-stu-id="0fd13-126">Options for dotnet by itself</span></span>

<span data-ttu-id="0fd13-127">Les options suivantes `dotnet` sont pour lui-même.</span><span class="sxs-lookup"><span data-stu-id="0fd13-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="0fd13-128">Par exemple : `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="0fd13-129">Ils impriment des informations sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="0fd13-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="0fd13-130">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="0fd13-131">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="0fd13-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="0fd13-132">Imprime une liste des temps d’exécution .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="0fd13-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="0fd13-133">Une version x86 du SDK ne répertorie que les runtimes x86, et une version x64 du SDK ne répertorie que les runtimes x64.</span><span class="sxs-lookup"><span data-stu-id="0fd13-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="0fd13-134">Imprime une liste des SDKs .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="0fd13-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0fd13-135">Imprime une liste de commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="0fd13-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="0fd13-136">Options SDK pour l’exécution d’une commande</span><span class="sxs-lookup"><span data-stu-id="0fd13-136">SDK options for running a command</span></span>

<span data-ttu-id="0fd13-137">Les options suivantes `dotnet` sont pour avec une commande.</span><span class="sxs-lookup"><span data-stu-id="0fd13-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="0fd13-138">Par exemple : `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="0fd13-139">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="0fd13-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0fd13-140">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="0fd13-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0fd13-141">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0fd13-142">Pas pris en charge dans tous les commandements.</span><span class="sxs-lookup"><span data-stu-id="0fd13-142">Not supported in every command.</span></span> <span data-ttu-id="0fd13-143">Voir la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="0fd13-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0fd13-144">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="0fd13-145">Chaque commande définit les options spécifiques à cette commande.</span><span class="sxs-lookup"><span data-stu-id="0fd13-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="0fd13-146">Voir la page de commande spécifique pour une liste d’options disponibles.</span><span class="sxs-lookup"><span data-stu-id="0fd13-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="0fd13-147">Options d’exécution</span><span class="sxs-lookup"><span data-stu-id="0fd13-147">Runtime options</span></span>

<span data-ttu-id="0fd13-148">Les options suivantes `dotnet` sont disponibles lors de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="0fd13-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="0fd13-149">Par exemple : `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-149">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="0fd13-150">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="0fd13-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="0fd13-151">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="0fd13-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="0fd13-152">Un fichier *deps.json* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour résoudre les conflits d’assemblage.</span><span class="sxs-lookup"><span data-stu-id="0fd13-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0fd13-153">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="0fd13-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="0fd13-154">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="0fd13-154">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="0fd13-155">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="0fd13-155">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="0fd13-156">Un fichier *runtimeconfig.json* est un fichier de configuration qui contient des paramètres de temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0fd13-156">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="0fd13-157">Pour plus d’informations, voir [paramètres de configuration .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0fd13-157">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="0fd13-158">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponible en .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0fd13-158">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0fd13-159">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="0fd13-159">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="0fd13-160">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="0fd13-160">`N` can be:</span></span>

  - <span data-ttu-id="0fd13-161">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="0fd13-161">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="0fd13-162">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="0fd13-162">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="0fd13-163">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="0fd13-163">This is the default behavior.</span></span>
  - <span data-ttu-id="0fd13-164">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="0fd13-164">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="0fd13-165">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0fd13-165">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="0fd13-166">**`--roll-forward <SETTING>`\*\*\*\*Disponible en commençant par .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="0fd13-166">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="0fd13-167">Contrôle la façon dont le rouleau vers l’avant est appliqué à l’application.</span><span class="sxs-lookup"><span data-stu-id="0fd13-167">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="0fd13-168">La `SETTING` peut être l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="0fd13-168">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="0fd13-169">S’il `Minor` n’est pas spécifié, est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="0fd13-169">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="0fd13-170">`LatestPatch`- Roulez vers la version patch la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="0fd13-170">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="0fd13-171">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="0fd13-171">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="0fd13-172">`Minor`- Rouler vers l’avant à la version mineure supérieure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="0fd13-172">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="0fd13-173">Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0fd13-173">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="0fd13-174">`Major`- Rouler vers l’avant à la version principale supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="0fd13-174">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="0fd13-175">Si la version majeure demandée est présente, la stratégie Minor est utilisée.</span><span class="sxs-lookup"><span data-stu-id="0fd13-175">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="0fd13-176">`LatestMinor`- Rouler vers la version mineure la plus élevée, même si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="0fd13-176">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="0fd13-177">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="0fd13-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0fd13-178">`LatestMajor`- Rouler vers l’avant à la plus haute version mineure majeure et la plus élevée, même si demandé majeur est présent.</span><span class="sxs-lookup"><span data-stu-id="0fd13-178">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="0fd13-179">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="0fd13-179">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0fd13-180">`Disable`- Ne roulez pas vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="0fd13-180">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="0fd13-181">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0fd13-181">Only bind to specified version.</span></span> <span data-ttu-id="0fd13-182">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="0fd13-182">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="0fd13-183">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="0fd13-183">This value is only recommended for testing.</span></span>

<span data-ttu-id="0fd13-184">À l’exception de `Disable`, tous les paramètres utiliseront la version patch disponible la plus élevée.</span><span class="sxs-lookup"><span data-stu-id="0fd13-184">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="0fd13-185">Le comportement de roll forward peut également être configuré dans une propriété de fichier de projet, une propriété de fichier de configuration de temps d’exécution, et une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="0fd13-185">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="0fd13-186">Pour plus d’informations, voir [Le roll time de la version majeure vers l’avant](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0fd13-186">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="0fd13-187">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="0fd13-187">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0fd13-188">Général</span><span class="sxs-lookup"><span data-stu-id="0fd13-188">General</span></span>

| <span data-ttu-id="0fd13-189">Commande</span><span class="sxs-lookup"><span data-stu-id="0fd13-189">Command</span></span>                                       | <span data-ttu-id="0fd13-190">Fonction</span><span class="sxs-lookup"><span data-stu-id="0fd13-190">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0fd13-191">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0fd13-191">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="0fd13-192">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-192">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0fd13-193">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="0fd13-193">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="0fd13-194">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="0fd13-194">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="0fd13-195">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0fd13-195">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="0fd13-196">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="0fd13-196">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="0fd13-197">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0fd13-197">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="0fd13-198">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="0fd13-198">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0fd13-199">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0fd13-199">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="0fd13-200">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="0fd13-200">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0fd13-201">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0fd13-201">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="0fd13-202">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0fd13-202">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0fd13-203">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0fd13-203">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="0fd13-204">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="0fd13-204">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0fd13-205">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0fd13-205">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="0fd13-206">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="0fd13-206">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0fd13-207">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0fd13-207">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="0fd13-208">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="0fd13-208">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0fd13-209">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0fd13-209">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="0fd13-210">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="0fd13-210">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0fd13-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0fd13-211">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="0fd13-212">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="0fd13-212">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0fd13-213">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0fd13-213">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="0fd13-214">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="0fd13-214">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0fd13-215">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0fd13-215">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="0fd13-216">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="0fd13-216">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0fd13-217">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0fd13-217">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="0fd13-218">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="0fd13-218">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="0fd13-219">Références de projets</span><span class="sxs-lookup"><span data-stu-id="0fd13-219">Project references</span></span>

<span data-ttu-id="0fd13-220">Commande</span><span class="sxs-lookup"><span data-stu-id="0fd13-220">Command</span></span> | <span data-ttu-id="0fd13-221">Fonction</span><span class="sxs-lookup"><span data-stu-id="0fd13-221">Function</span></span>
--- | ---
[<span data-ttu-id="0fd13-222">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="0fd13-222">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0fd13-223">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-223">Adds a project reference.</span></span>
[<span data-ttu-id="0fd13-224">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0fd13-224">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0fd13-225">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-225">Lists project references.</span></span>
[<span data-ttu-id="0fd13-226">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0fd13-226">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0fd13-227">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-227">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0fd13-228">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="0fd13-228">NuGet packages</span></span>

<span data-ttu-id="0fd13-229">Commande</span><span class="sxs-lookup"><span data-stu-id="0fd13-229">Command</span></span> | <span data-ttu-id="0fd13-230">Fonction</span><span class="sxs-lookup"><span data-stu-id="0fd13-230">Function</span></span>
--- | ---
[<span data-ttu-id="0fd13-231">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0fd13-231">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0fd13-232">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-232">Adds a NuGet package.</span></span>
[<span data-ttu-id="0fd13-233">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="0fd13-233">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0fd13-234">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-234">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0fd13-235">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="0fd13-235">NuGet commands</span></span>

<span data-ttu-id="0fd13-236">Commande</span><span class="sxs-lookup"><span data-stu-id="0fd13-236">Command</span></span> | <span data-ttu-id="0fd13-237">Fonction</span><span class="sxs-lookup"><span data-stu-id="0fd13-237">Function</span></span>
--- | ---
[<span data-ttu-id="0fd13-238">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0fd13-238">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0fd13-239">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="0fd13-239">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0fd13-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0fd13-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0fd13-241">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="0fd13-241">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="0fd13-242">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="0fd13-242">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0fd13-243">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0fd13-243">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0fd13-244">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="0fd13-244">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="0fd13-245">Ajoute une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-245">Adds a NuGet source.</span></span>
[<span data-ttu-id="0fd13-246">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="0fd13-246">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="0fd13-247">Désactive une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-247">Disables a NuGet source.</span></span>
[<span data-ttu-id="0fd13-248">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="0fd13-248">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="0fd13-249">Permet une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-249">Enables a NuGet source.</span></span>
[<span data-ttu-id="0fd13-250">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="0fd13-250">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="0fd13-251">Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="0fd13-251">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="0fd13-252">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="0fd13-252">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="0fd13-253">Supprime une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-253">Removes a NuGet source.</span></span>
[<span data-ttu-id="0fd13-254">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="0fd13-254">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="0fd13-255">Mise à jour d’une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fd13-255">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="0fd13-256">Commandes d’outils mondiaux, d’outils et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="0fd13-256">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="0fd13-257">Les outils sont des applications de console qui sont installées à partir de paquets NuGet et sont invoquées à partir de l’invite de commande.</span><span class="sxs-lookup"><span data-stu-id="0fd13-257">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0fd13-258">Vous pouvez écrire des outils vous-même ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="0fd13-258">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0fd13-259">Les outils sont également connus sous le nom d’outils globaux, d’outils de chemin à outils et d’outils locaux.</span><span class="sxs-lookup"><span data-stu-id="0fd13-259">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0fd13-260">Pour plus d’informations, voir [.NET Core outils aperçu](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0fd13-260">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="0fd13-261">Des outils globaux et de chemin d’outils sont disponibles à partir de .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="0fd13-261">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="0fd13-262">Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="0fd13-262">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="0fd13-263">Commande</span><span class="sxs-lookup"><span data-stu-id="0fd13-263">Command</span></span> | <span data-ttu-id="0fd13-264">Fonction</span><span class="sxs-lookup"><span data-stu-id="0fd13-264">Function</span></span>
--- | ---
[<span data-ttu-id="0fd13-265">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0fd13-265">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="0fd13-266">Installe un outil sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="0fd13-266">Installs a tool on your machine.</span></span>
[<span data-ttu-id="0fd13-267">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="0fd13-267">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="0fd13-268">Répertorie tous les outils globaux, de chemin d’outils ou locaux actuellement installés sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="0fd13-268">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="0fd13-269">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="0fd13-269">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="0fd13-270">Désinstalle un outil de votre machine.</span><span class="sxs-lookup"><span data-stu-id="0fd13-270">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="0fd13-271">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="0fd13-271">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="0fd13-272">Mise à jour d’un outil qui est installé sur votre machine.</span><span class="sxs-lookup"><span data-stu-id="0fd13-272">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="0fd13-273">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="0fd13-273">Additional tools</span></span>

<span data-ttu-id="0fd13-274">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-274">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="0fd13-275">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="0fd13-275">These tools are listed in the following table:</span></span>

| <span data-ttu-id="0fd13-276">Outil</span><span class="sxs-lookup"><span data-stu-id="0fd13-276">Tool</span></span>                                              | <span data-ttu-id="0fd13-277">Fonction</span><span class="sxs-lookup"><span data-stu-id="0fd13-277">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="0fd13-278">dev-certs</span><span class="sxs-lookup"><span data-stu-id="0fd13-278">dev-certs</span></span>                                         | <span data-ttu-id="0fd13-279">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="0fd13-279">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="0fd13-280">Ef</span><span class="sxs-lookup"><span data-stu-id="0fd13-280">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="0fd13-281">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-281">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="0fd13-282">sql-cache</span><span class="sxs-lookup"><span data-stu-id="0fd13-282">sql-cache</span></span>                                         | <span data-ttu-id="0fd13-283">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0fd13-283">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="0fd13-284">user-secrets</span><span class="sxs-lookup"><span data-stu-id="0fd13-284">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="0fd13-285">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0fd13-285">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="0fd13-286">Regarder</span><span class="sxs-lookup"><span data-stu-id="0fd13-286">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="0fd13-287">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="0fd13-287">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="0fd13-288">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-288">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="0fd13-289">Exemples</span><span class="sxs-lookup"><span data-stu-id="0fd13-289">Examples</span></span>

<span data-ttu-id="0fd13-290">Créez une nouvelle application de console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="0fd13-290">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="0fd13-291">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="0fd13-291">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="0fd13-292">Exécuter une application:</span><span class="sxs-lookup"><span data-stu-id="0fd13-292">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="0fd13-293">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="0fd13-293">Environment variables</span></span>

- <span data-ttu-id="0fd13-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="0fd13-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="0fd13-295">Spécifie l’emplacement des temps d’exécution .NET Core, s’ils ne sont pas installés dans l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="0fd13-295">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="0fd13-296">L’emplacement par `C:\Program Files\dotnet`défaut sur Windows est .</span><span class="sxs-lookup"><span data-stu-id="0fd13-296">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="0fd13-297">L’emplacement par défaut sur `/usr/share/dotnet`Linux et macOS est .</span><span class="sxs-lookup"><span data-stu-id="0fd13-297">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="0fd13-298">Cette variable d’environnement n’est utilisée que lorsque vous exécutez des applications via des exécutables générés (apphosts).</span><span class="sxs-lookup"><span data-stu-id="0fd13-298">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="0fd13-299">`DOTNET_ROOT(x86)`est utilisé à la place lors de l’exécution d’un 32 bits exécutable sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="0fd13-299">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="0fd13-300">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="0fd13-300">The global packages folder.</span></span> <span data-ttu-id="0fd13-301">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="0fd13-301">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="0fd13-302">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="0fd13-302">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="0fd13-303">Précise si les messages de bienvenue et de télémétrie .NET Core sont affichés en première diffusion.</span><span class="sxs-lookup"><span data-stu-id="0fd13-303">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="0fd13-304">Configurez `true` pour couper ces `true` `1`messages `yes` (valeurs, , `false` ou acceptés) ou définis pour permettre (valeurs, `false` `0`, ou `no` accepté).</span><span class="sxs-lookup"><span data-stu-id="0fd13-304">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0fd13-305">Si elle n’est `false` pas définie, la valeur par défaut est et les messages seront affichés en première exécution.</span><span class="sxs-lookup"><span data-stu-id="0fd13-305">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="0fd13-306">Notez que ce drapeau n’a `DOTNET_CLI_TELEMETRY_OPTOUT` aucun effet sur la télémétrie (voir pour refuser d’envoyer de la télémétrie).</span><span class="sxs-lookup"><span data-stu-id="0fd13-306">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="0fd13-307">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0fd13-307">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0fd13-308">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="0fd13-308">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0fd13-309">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="0fd13-309">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0fd13-310">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="0fd13-310">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="0fd13-311">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="0fd13-311">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="0fd13-312">Si elle n’est pas réglée, `true`elle par défaut à 1 (logique).</span><span class="sxs-lookup"><span data-stu-id="0fd13-312">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="0fd13-313">Set à 0 `false`(logique) pour ne pas résoudre à partir de l’emplacement global et ont isolé les installations .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fd13-313">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="0fd13-314">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0fd13-314">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="0fd13-315">`DOTNET_ROLL_FORWARD`**Disponible en commençant par .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0fd13-315">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="0fd13-316">Détermine le comportement de rouler vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="0fd13-316">Determines roll forward behavior.</span></span> <span data-ttu-id="0fd13-317">Pour plus d’informations, voir l’option `--roll-forward` plus tôt dans cet article.</span><span class="sxs-lookup"><span data-stu-id="0fd13-317">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="0fd13-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponible en .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0fd13-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0fd13-319">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-319">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="0fd13-320">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0fd13-320">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="0fd13-321">Définit la langue de l’interface utilisateur CLI en utilisant une valeur locale telle que `en-us`.</span><span class="sxs-lookup"><span data-stu-id="0fd13-321">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="0fd13-322">Les valeurs prises en charge sont les mêmes que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0fd13-322">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="0fd13-323">Pour plus d’informations, voir la section sur la modification de la langue de l’installateur dans la [documentation d’installation Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="0fd13-323">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="0fd13-324">Les règles de gestionnaire de ressources .NET s’appliquent, de sorte que vous n’avez pas à choisir un match&mdash;exact, vous pouvez également choisir les descendants dans l’arbre. `CultureInfo`</span><span class="sxs-lookup"><span data-stu-id="0fd13-324">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="0fd13-325">Par exemple, si vous `fr-CA`le définissez, le `fr` CLI trouvera et utilisera les traductions.</span><span class="sxs-lookup"><span data-stu-id="0fd13-325">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="0fd13-326">Si vous le définissez dans une langue qui n’est pas prise en charge, l’IMC retombe à l’anglais.</span><span class="sxs-lookup"><span data-stu-id="0fd13-326">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="0fd13-327">Pour les exécutables générés par l’INTERFACE graphique - désactive le dialogue popup, qui montre normalement pour certaines classes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="0fd13-327">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="0fd13-328">Il n’écrit `stderr` et sort que dans ces cas.</span><span class="sxs-lookup"><span data-stu-id="0fd13-328">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="0fd13-329">Équivalent à l’option `--additional-deps`CLI .</span><span class="sxs-lookup"><span data-stu-id="0fd13-329">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="0fd13-330">Remplace le RID détecté.</span><span class="sxs-lookup"><span data-stu-id="0fd13-330">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="0fd13-331">L’emplacement du « magasin partagé » auquel la résolution d’assemblage revient dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="0fd13-331">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="0fd13-332">Liste des assemblages à charger et exécuter des crochets de démarrage à partir de.</span><span class="sxs-lookup"><span data-stu-id="0fd13-332">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="0fd13-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="0fd13-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="0fd13-334">Contrôle les diagnostics traçant à `dotnet.exe`partir `hostfxr`des `hostpolicy`composants d’hébergement, tels que , , et .</span><span class="sxs-lookup"><span data-stu-id="0fd13-334">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fd13-335">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0fd13-335">See also</span></span>

- [<span data-ttu-id="0fd13-336">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="0fd13-336">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="0fd13-337">paramètres de configuration de temps d’exécution .NET Core</span><span class="sxs-lookup"><span data-stu-id="0fd13-337">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
