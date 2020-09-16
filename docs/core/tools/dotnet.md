---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: 4476dcf36455e0dc1b89712409818cf7e0352f2c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537663"
---
# <a name="dotnet-command"></a><span data-ttu-id="b03c0-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="b03c0-103">dotnet command</span></span>

<span data-ttu-id="b03c0-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b03c0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b03c0-105">Name</span><span class="sxs-lookup"><span data-stu-id="b03c0-105">Name</span></span>

<span data-ttu-id="b03c0-106">`dotnet` -Pilote générique pour le CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b03c0-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b03c0-107">Synopsis</span></span>

<span data-ttu-id="b03c0-108">Pour obtenir des informations sur les commandes disponibles et l’environnement :</span><span class="sxs-lookup"><span data-stu-id="b03c0-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="b03c0-109">Pour exécuter une commande (installation du kit de développement logiciel (SDK) requise) :</span><span class="sxs-lookup"><span data-stu-id="b03c0-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="b03c0-110">Pour exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="b03c0-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="b03c0-111">`--roll-forward` est disponible depuis .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="b03c0-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="b03c0-112">Utilisez `--roll-forward-on-no-candidate-fx` pour .net Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="b03c0-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="b03c0-113">Description</span><span class="sxs-lookup"><span data-stu-id="b03c0-113">Description</span></span>

<span data-ttu-id="b03c0-114">La `dotnet` commande a deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="b03c0-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="b03c0-115">Il fournit des commandes pour travailler avec les projets .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="b03c0-116">Par exemple, [`dotnet build`](dotnet-build.md) génère un projet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="b03c0-117">Chaque commande définit ses propres options et arguments.</span><span class="sxs-lookup"><span data-stu-id="b03c0-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="b03c0-118">Toutes les commandes prennent en charge l' `--help` option d’impression d’une brève documentation sur la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="b03c0-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="b03c0-119">Il exécute des applications .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="b03c0-120">Vous spécifiez le chemin d’accès à un fichier d’application `.dll` pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="b03c0-121">Pour exécuter l’application, vous devez rechercher et exécuter le point d’entrée, ce qui, dans le cas des applications console, est la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="b03c0-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="b03c0-122">Par exemple, `dotnet myapp.dll` exécute l' `myapp` application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="b03c0-123">Consultez [déploiement d’applications .net Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.</span><span class="sxs-lookup"><span data-stu-id="b03c0-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="b03c0-124">Options</span><span class="sxs-lookup"><span data-stu-id="b03c0-124">Options</span></span>

<span data-ttu-id="b03c0-125">Différentes options sont disponibles pour `dotnet` par elle-même, pour exécuter une commande et pour exécuter une application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="b03c0-126">Options de dotnet par lui-même</span><span class="sxs-lookup"><span data-stu-id="b03c0-126">Options for dotnet by itself</span></span>

<span data-ttu-id="b03c0-127">Les options suivantes sont destinées `dotnet` à elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="b03c0-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="b03c0-128">Par exemple : `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="b03c0-129">Ils affichent des informations sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="b03c0-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="b03c0-130">Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="b03c0-131">Affiche la version du SDK .NET Core en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="b03c0-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="b03c0-132">Imprime une liste des runtimes .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="b03c0-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="b03c0-133">Une version x86 du kit de développement logiciel (SDK) répertorie uniquement les runtimes x86, et une version x64 du kit de développement logiciel (SDK) répertorie uniquement les runtimes x64.</span><span class="sxs-lookup"><span data-stu-id="b03c0-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="b03c0-134">Affiche la liste des kits de développement logiciel (SDK) .NET Core installés.</span><span class="sxs-lookup"><span data-stu-id="b03c0-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b03c0-135">Imprime une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="b03c0-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="b03c0-136">Options du kit de développement logiciel pour exécuter une commande</span><span class="sxs-lookup"><span data-stu-id="b03c0-136">SDK options for running a command</span></span>

<span data-ttu-id="b03c0-137">Les options suivantes concernent `dotnet` avec une commande.</span><span class="sxs-lookup"><span data-stu-id="b03c0-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="b03c0-138">Par exemple : `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="b03c0-139">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="b03c0-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="b03c0-140">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="b03c0-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b03c0-141">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="b03c0-142">Non pris en charge dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="b03c0-142">Not supported in every command.</span></span> <span data-ttu-id="b03c0-143">Consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="b03c0-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b03c0-144">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="b03c0-145">Chaque commande définit des options spécifiques à cette commande.</span><span class="sxs-lookup"><span data-stu-id="b03c0-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="b03c0-146">Pour obtenir la liste des options disponibles, consultez la page de commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="b03c0-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="b03c0-147">Options d’exécution</span><span class="sxs-lookup"><span data-stu-id="b03c0-147">Runtime options</span></span>

<span data-ttu-id="b03c0-148">Les options suivantes sont disponibles lors de l' `dotnet` exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="b03c0-149">Par exemple : `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="b03c0-150">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="b03c0-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="b03c0-151">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b03c0-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="b03c0-152">Un *deps.jssur* un fichier contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour traiter les conflits d’assembly.</span><span class="sxs-lookup"><span data-stu-id="b03c0-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="b03c0-153">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="b03c0-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="b03c0-154">Chemin d’accès à la *deps.jssur* le fichier.</span><span class="sxs-lookup"><span data-stu-id="b03c0-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="b03c0-155">Un *deps.jssur le* fichier est un fichier de configuration qui contient des informations sur les dépendances nécessaires à l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="b03c0-156">Ce fichier est généré par le kit SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-156">This file is generated by the .NET Core SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="b03c0-157">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="b03c0-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="b03c0-158">Un *runtimeconfig.jssur le* fichier est un fichier de configuration qui contient des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b03c0-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="b03c0-159">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="b03c0-159">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="b03c0-160">**`--roll-forward <SETTING>`\*\*\*\*Disponible à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="b03c0-161">Contrôle la façon dont la restauration par progression est appliquée à l’application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="b03c0-162">`SETTING`Peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="b03c0-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="b03c0-163">S’il n’est pas spécifié, `Minor` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b03c0-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="b03c0-164">`LatestPatch` -Restauration par progression vers la version de correctif la plus récente.</span><span class="sxs-lookup"><span data-stu-id="b03c0-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="b03c0-165">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="b03c0-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="b03c0-166">`Minor` -Restaurer par progression jusqu’à la version mineure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="b03c0-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="b03c0-167">Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b03c0-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="b03c0-168">`Major` -Restauration par progression vers la version principale la plus basse, et version mineure la plus faible, si la version principale demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="b03c0-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="b03c0-169">Si la version majeure demandée est présente, la stratégie Minor est utilisée.</span><span class="sxs-lookup"><span data-stu-id="b03c0-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="b03c0-170">`LatestMinor` -Restaurer par progression vers la version mineure la plus élevée, même si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="b03c0-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="b03c0-171">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="b03c0-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="b03c0-172">`LatestMajor` -Restauration par progression vers la version mineure la plus élevée et la plus élevée, même si la version principale demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="b03c0-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="b03c0-173">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="b03c0-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="b03c0-174">`Disable` -Ne pas restaurer par progression.</span><span class="sxs-lookup"><span data-stu-id="b03c0-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="b03c0-175">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b03c0-175">Only bind to specified version.</span></span> <span data-ttu-id="b03c0-176">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="b03c0-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="b03c0-177">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="b03c0-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="b03c0-178">À l’exception de `Disable` , tous les paramètres utilisent la version de correctif la plus élevée disponible.</span><span class="sxs-lookup"><span data-stu-id="b03c0-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="b03c0-179">Le comportement de restauration par progression peut également être configuré dans une propriété de fichier projet, une propriété de fichier de configuration au moment de l’exécution et une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="b03c0-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="b03c0-180">Pour plus d’informations, consultez [restauration par progression du runtime de version principale](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b03c0-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="b03c0-181">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponible dans le kit de développement logiciel (SDK) .net Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="b03c0-182">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="b03c0-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="b03c0-183">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="b03c0-183">`N` can be:</span></span>

  - <span data-ttu-id="b03c0-184">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="b03c0-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="b03c0-185">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="b03c0-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="b03c0-186">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="b03c0-186">This is the default behavior.</span></span>
  - <span data-ttu-id="b03c0-187">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="b03c0-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="b03c0-188">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b03c0-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="b03c0-189">À compter de .NET Core 3,0, cette option est remplacée par `--roll-forward` , et cette option doit être utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="b03c0-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="b03c0-190">Version du runtime .NET Core à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-190">Version of the .NET Core runtime to use to run the application.</span></span>

  <span data-ttu-id="b03c0-191">Cette option remplace la version de la première référence de Framework dans le fichier de l’application `.runtimeconfig.json` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="b03c0-192">Cela signifie qu’il ne fonctionne comme prévu que s’il n’existe qu’une seule référence d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="b03c0-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="b03c0-193">Si l’application a plus d’une référence d’infrastructure, l’utilisation de cette option peut provoquer des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b03c0-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="b03c0-194">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="b03c0-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="b03c0-195">Général</span><span class="sxs-lookup"><span data-stu-id="b03c0-195">General</span></span>

| <span data-ttu-id="b03c0-196">Commande</span><span class="sxs-lookup"><span data-stu-id="b03c0-196">Command</span></span>                                       | <span data-ttu-id="b03c0-197">Fonction</span><span class="sxs-lookup"><span data-stu-id="b03c0-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="b03c0-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b03c0-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="b03c0-199">Génère une application .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-199">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="b03c0-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="b03c0-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="b03c0-201">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="b03c0-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="b03c0-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b03c0-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="b03c0-203">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="b03c0-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="b03c0-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="b03c0-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="b03c0-205">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="b03c0-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="b03c0-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b03c0-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="b03c0-207">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="b03c0-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="b03c0-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b03c0-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="b03c0-209">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="b03c0-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="b03c0-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="b03c0-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="b03c0-211">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="b03c0-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="b03c0-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b03c0-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="b03c0-213">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="b03c0-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="b03c0-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b03c0-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="b03c0-215">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="b03c0-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="b03c0-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b03c0-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="b03c0-217">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="b03c0-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="b03c0-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b03c0-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="b03c0-219">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="b03c0-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="b03c0-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="b03c0-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="b03c0-221">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="b03c0-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="b03c0-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b03c0-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="b03c0-223">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="b03c0-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="b03c0-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="b03c0-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="b03c0-225">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="b03c0-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="b03c0-226">Références de projets</span><span class="sxs-lookup"><span data-stu-id="b03c0-226">Project references</span></span>

<span data-ttu-id="b03c0-227">Commande</span><span class="sxs-lookup"><span data-stu-id="b03c0-227">Command</span></span> | <span data-ttu-id="b03c0-228">Fonction</span><span class="sxs-lookup"><span data-stu-id="b03c0-228">Function</span></span>
--- | ---
[<span data-ttu-id="b03c0-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="b03c0-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="b03c0-230">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-230">Adds a project reference.</span></span>
[<span data-ttu-id="b03c0-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="b03c0-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="b03c0-232">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-232">Lists project references.</span></span>
[<span data-ttu-id="b03c0-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="b03c0-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="b03c0-234">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="b03c0-235">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="b03c0-235">NuGet packages</span></span>

<span data-ttu-id="b03c0-236">Commande</span><span class="sxs-lookup"><span data-stu-id="b03c0-236">Command</span></span> | <span data-ttu-id="b03c0-237">Fonction</span><span class="sxs-lookup"><span data-stu-id="b03c0-237">Function</span></span>
--- | ---
[<span data-ttu-id="b03c0-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="b03c0-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="b03c0-239">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="b03c0-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="b03c0-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="b03c0-241">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="b03c0-242">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="b03c0-242">NuGet commands</span></span>

<span data-ttu-id="b03c0-243">Commande</span><span class="sxs-lookup"><span data-stu-id="b03c0-243">Command</span></span> | <span data-ttu-id="b03c0-244">Fonction</span><span class="sxs-lookup"><span data-stu-id="b03c0-244">Function</span></span>
--- | ---
[<span data-ttu-id="b03c0-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="b03c0-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="b03c0-246">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="b03c0-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="b03c0-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="b03c0-248">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="b03c0-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="b03c0-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="b03c0-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="b03c0-250">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="b03c0-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="b03c0-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="b03c0-252">Ajoute une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="b03c0-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="b03c0-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="b03c0-254">Désactive une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="b03c0-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="b03c0-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="b03c0-256">Active une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="b03c0-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="b03c0-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="b03c0-258">Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="b03c0-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="b03c0-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="b03c0-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="b03c0-260">Supprime une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="b03c0-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="b03c0-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="b03c0-262">Met à jour une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="b03c0-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="b03c0-263">Commandes globales, de chemin d’accès d’outil et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="b03c0-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="b03c0-264">Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b03c0-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="b03c0-265">Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="b03c0-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="b03c0-266">Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux.</span><span class="sxs-lookup"><span data-stu-id="b03c0-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="b03c0-267">Pour plus d’informations, consultez [vue d’ensemble des outils .net Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="b03c0-267">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="b03c0-268">Les outils globaux et de chemin d’accès aux outils sont disponibles à partir de kit SDK .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="b03c0-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="b03c0-269">Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="b03c0-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="b03c0-270">Commande</span><span class="sxs-lookup"><span data-stu-id="b03c0-270">Command</span></span> | <span data-ttu-id="b03c0-271">Fonction</span><span class="sxs-lookup"><span data-stu-id="b03c0-271">Function</span></span>
--- | ---
[<span data-ttu-id="b03c0-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="b03c0-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="b03c0-273">Installe un outil sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="b03c0-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="b03c0-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="b03c0-275">Répertorie tous les outils globaux, de chemin d’accès d’outil ou locaux actuellement installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="b03c0-276">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="b03c0-276">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="b03c0-277">Désinstalle un outil de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-277">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="b03c0-278">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="b03c0-278">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="b03c0-279">Met à jour un outil qui est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-279">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="b03c0-280">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b03c0-280">Additional tools</span></span>

<span data-ttu-id="b03c0-281">À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-281">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="b03c0-282">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="b03c0-282">These tools are listed in the following table:</span></span>

| <span data-ttu-id="b03c0-283">Outil</span><span class="sxs-lookup"><span data-stu-id="b03c0-283">Tool</span></span>                                              | <span data-ttu-id="b03c0-284">Fonction</span><span class="sxs-lookup"><span data-stu-id="b03c0-284">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="b03c0-285">dev-certs</span><span class="sxs-lookup"><span data-stu-id="b03c0-285">dev-certs</span></span>                                         | <span data-ttu-id="b03c0-286">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="b03c0-286">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="b03c0-287">EF</span><span class="sxs-lookup"><span data-stu-id="b03c0-287">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="b03c0-288">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="b03c0-288">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="b03c0-289">sql-cache</span><span class="sxs-lookup"><span data-stu-id="b03c0-289">sql-cache</span></span>                                         | <span data-ttu-id="b03c0-290">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b03c0-290">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="b03c0-291">user-secrets</span><span class="sxs-lookup"><span data-stu-id="b03c0-291">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="b03c0-292">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b03c0-292">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="b03c0-293">vérifier</span><span class="sxs-lookup"><span data-stu-id="b03c0-293">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="b03c0-294">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="b03c0-294">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="b03c0-295">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-295">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="b03c0-296">Exemples</span><span class="sxs-lookup"><span data-stu-id="b03c0-296">Examples</span></span>

<span data-ttu-id="b03c0-297">Créez une application de console .NET Core :</span><span class="sxs-lookup"><span data-stu-id="b03c0-297">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="b03c0-298">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="b03c0-298">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="b03c0-299">Exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="b03c0-299">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="b03c0-300">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="b03c0-300">Environment variables</span></span>

- <span data-ttu-id="b03c0-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="b03c0-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="b03c0-302">Spécifie l’emplacement des runtimes .NET Core, s’ils ne sont pas installés à l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="b03c0-302">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="b03c0-303">L’emplacement par défaut sur Windows est `C:\Program Files\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-303">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="b03c0-304">L’emplacement par défaut sur Linux et macOS est `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-304">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="b03c0-305">Cette variable d’environnement est utilisée uniquement lors de l’exécution d’applications via des exécutables générés (apphosts).</span><span class="sxs-lookup"><span data-stu-id="b03c0-305">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="b03c0-306">`DOTNET_ROOT(x86)` est utilisé à la place lors de l’exécution d’un fichier exécutable 32 bits sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="b03c0-306">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="b03c0-307">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="b03c0-307">The global packages folder.</span></span> <span data-ttu-id="b03c0-308">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="b03c0-308">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="b03c0-309">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b03c0-309">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="b03c0-310">Spécifie si les messages de bienvenue et de télémétrie .NET Core s’affichent lors de la première exécution.</span><span class="sxs-lookup"><span data-stu-id="b03c0-310">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="b03c0-311">Affectez la valeur pour `true` désactiver ces messages (valeurs `true` , `1` ou `yes` acceptés) ou la valeur à `false` autoriser (valeurs `false` , `0` ou `no` acceptées).</span><span class="sxs-lookup"><span data-stu-id="b03c0-311">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="b03c0-312">Si la valeur n’est pas définie, la valeur par défaut est `false` et les messages sont affichés lors de la première exécution.</span><span class="sxs-lookup"><span data-stu-id="b03c0-312">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="b03c0-313">Cet indicateur n’a aucun effet sur la télémétrie (voir pour le refus `DOTNET_CLI_TELEMETRY_OPTOUT` d’envoyer des données de télémétrie).</span><span class="sxs-lookup"><span data-stu-id="b03c0-313">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="b03c0-314">Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b03c0-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="b03c0-315">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="b03c0-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="b03c0-316">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="b03c0-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="b03c0-317">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="b03c0-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="b03c0-318">Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="b03c0-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="b03c0-319">S’il n’est pas défini, la valeur par défaut est 1 (logique `true` ).</span><span class="sxs-lookup"><span data-stu-id="b03c0-319">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="b03c0-320">Définissez sur 0 (logique `false` ) pour ne pas résoudre à partir de l’emplacement global et disposer d’installations .net Core isolées.</span><span class="sxs-lookup"><span data-stu-id="b03c0-320">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="b03c0-321">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="b03c0-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="b03c0-322">`DOTNET_ROLL_FORWARD`**Disponible à partir de .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-322">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="b03c0-323">Détermine le comportement de restauration par progression.</span><span class="sxs-lookup"><span data-stu-id="b03c0-323">Determines roll forward behavior.</span></span> <span data-ttu-id="b03c0-324">Pour plus d’informations, consultez l' `--roll-forward` option plus haut dans cet article.</span><span class="sxs-lookup"><span data-stu-id="b03c0-324">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="b03c0-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE`**Disponible à partir de .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="b03c0-326">Si la valeur est `1` (activé), permet de restaurer une version préliminaire à partir d’une version Release.</span><span class="sxs-lookup"><span data-stu-id="b03c0-326">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="b03c0-327">Par défaut ( `0` -désactivé), quand une version Release du Runtime .net Core est demandée, la restauration par progression ne prend en compte que les versions de version installée.</span><span class="sxs-lookup"><span data-stu-id="b03c0-327">By default (`0` - disabled), when a release version of .NET Core runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="b03c0-328">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b03c0-328">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="b03c0-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponible dans .net Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="b03c0-330">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="b03c0-330">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="b03c0-331">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="b03c0-331">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="b03c0-332">Ce paramètre est remplacé dans .NET Core 3,0 par `DOTNET_ROLL_FORWARD` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-332">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="b03c0-333">Les nouveaux paramètres doivent être utilisés à la place.</span><span class="sxs-lookup"><span data-stu-id="b03c0-333">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="b03c0-334">Définit le langage de l’interface utilisateur CLI à l’aide d’une valeur de paramètres régionaux telle que `en-us` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-334">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="b03c0-335">Les valeurs prises en charge sont les mêmes que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b03c0-335">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="b03c0-336">Pour plus d’informations, consultez la section relative à la modification du langage d’installation dans la [documentation d’installation de Visual Studio](/visualstudio/install/install-visual-studio?view=vs-2019).</span><span class="sxs-lookup"><span data-stu-id="b03c0-336">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="b03c0-337">Les règles .NET Resource Manager s’appliquent. vous n’avez donc pas à choisir une correspondance exacte &mdash; . vous pouvez également choisir des descendants dans l' `CultureInfo` arborescence.</span><span class="sxs-lookup"><span data-stu-id="b03c0-337">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="b03c0-338">Par exemple, si vous affectez la valeur à `fr-CA` , l’interface CLI trouvera et utilisera les `fr` traductions.</span><span class="sxs-lookup"><span data-stu-id="b03c0-338">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="b03c0-339">Si vous définissez une langue qui n’est pas prise en charge, l’interface CLI revient à l’anglais.</span><span class="sxs-lookup"><span data-stu-id="b03c0-339">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="b03c0-340">Pour les exécutables générés par l’interface utilisateur graphique : désactive la boîte de dialogue contextuelle, qui affiche généralement certaines classes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="b03c0-340">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="b03c0-341">Il écrit uniquement `stderr` dans et se termine dans ces cas-là.</span><span class="sxs-lookup"><span data-stu-id="b03c0-341">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="b03c0-342">Équivalent à l’option CLI `--additional-deps` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-342">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="b03c0-343">Remplace le RID détecté.</span><span class="sxs-lookup"><span data-stu-id="b03c0-343">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="b03c0-344">Emplacement du « magasin partagé » dans lequel la résolution de l’assembly revient dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="b03c0-344">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="b03c0-345">Liste des assemblys à partir desquels charger et exécuter des raccordements de démarrage.</span><span class="sxs-lookup"><span data-stu-id="b03c0-345">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="b03c0-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR`**Disponible à partir de .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="b03c0-347">Spécifie un répertoire dans lequel une application à fichier unique est extraite avant d’être exécutée.</span><span class="sxs-lookup"><span data-stu-id="b03c0-347">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="b03c0-348">Pour plus d’informations, consultez [fichiers exécutables à fichier unique](../whats-new/dotnet-core-3-0.md#single-file-executables).</span><span class="sxs-lookup"><span data-stu-id="b03c0-348">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="b03c0-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="b03c0-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="b03c0-350">Contrôle le suivi des diagnostics à partir des composants d’hébergement, tels que `dotnet.exe` , `hostfxr` et `hostpolicy` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-350">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="b03c0-351">`COREHOST_TRACE=[0/1]` -le suivi par défaut est `0` désactivé.</span><span class="sxs-lookup"><span data-stu-id="b03c0-351">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="b03c0-352">Si la valeur `1` est, le suivi des diagnostics est activé.</span><span class="sxs-lookup"><span data-stu-id="b03c0-352">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="b03c0-353">`COREHOST_TRACEFILE=<file path>` -n’a d’effet que si le suivi est activé via `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-353">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="b03c0-354">Lorsque cette valeur est définie, les informations de traçage sont écrites dans le fichier spécifié, dans le cas contraire, les informations de traçage sont écrites dans `stderr` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-354">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="b03c0-355">**Disponible à partir de .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-355">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="b03c0-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` -la valeur par défaut est `4` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="b03c0-357">Le paramètre est utilisé uniquement lorsque le suivi est activé via `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="b03c0-357">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="b03c0-358">**Disponible à partir de .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="b03c0-358">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="b03c0-359">`4` -toutes les informations de traçage sont écrites</span><span class="sxs-lookup"><span data-stu-id="b03c0-359">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="b03c0-360">`3` -Seuls les messages d’information, d’avertissement et d’erreur sont écrits</span><span class="sxs-lookup"><span data-stu-id="b03c0-360">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="b03c0-361">`2` -Seuls les messages d’avertissement et d’erreur sont écrits</span><span class="sxs-lookup"><span data-stu-id="b03c0-361">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="b03c0-362">`1` -Seuls les messages d’erreur sont écrits</span><span class="sxs-lookup"><span data-stu-id="b03c0-362">`1` - only error messages are written</span></span>

  <span data-ttu-id="b03c0-363">La méthode habituelle pour obtenir des informations de suivi détaillées sur le démarrage de l’application consiste à définir, puis à `COREHOST_TRACE=1` `COREHOST_TRACEFILE=host_trace.txt` exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="b03c0-363">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="b03c0-364">Un nouveau fichier `host_trace.txt` est créé dans le répertoire actif avec les informations détaillées.</span><span class="sxs-lookup"><span data-stu-id="b03c0-364">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="b03c0-365">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b03c0-365">See also</span></span>

- [<span data-ttu-id="b03c0-366">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="b03c0-366">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="b03c0-367">Paramètres de configuration du Runtime .NET Core</span><span class="sxs-lookup"><span data-stu-id="b03c0-367">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
