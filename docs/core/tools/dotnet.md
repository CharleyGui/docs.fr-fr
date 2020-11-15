---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour l’interface CLI .NET) et son utilisation.
ms.date: 11/11/2020
ms.openlocfilehash: 7a0c8f2eb7ab407bd725db56cbf31da4689970e4
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634023"
---
# <a name="dotnet-command"></a><span data-ttu-id="2f352-103">Commande dotnet</span><span class="sxs-lookup"><span data-stu-id="2f352-103">dotnet command</span></span>

<span data-ttu-id="2f352-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="2f352-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2f352-105">Name</span><span class="sxs-lookup"><span data-stu-id="2f352-105">Name</span></span>

<span data-ttu-id="2f352-106">`dotnet` -Pilote générique pour l’interface CLI .NET.</span><span class="sxs-lookup"><span data-stu-id="2f352-106">`dotnet` - The generic driver for the .NET CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2f352-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="2f352-107">Synopsis</span></span>

<span data-ttu-id="2f352-108">Pour obtenir des informations sur les commandes disponibles et l’environnement :</span><span class="sxs-lookup"><span data-stu-id="2f352-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="2f352-109">Pour exécuter une commande (installation du kit de développement logiciel (SDK) requise) :</span><span class="sxs-lookup"><span data-stu-id="2f352-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="2f352-110">Pour exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="2f352-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="2f352-111">`--roll-forward` est disponible depuis .NET Core 3. x.</span><span class="sxs-lookup"><span data-stu-id="2f352-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="2f352-112">Utilisez `--roll-forward-on-no-candidate-fx` pour .net Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="2f352-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="2f352-113">Description</span><span class="sxs-lookup"><span data-stu-id="2f352-113">Description</span></span>

<span data-ttu-id="2f352-114">La `dotnet` commande a deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="2f352-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="2f352-115">Il fournit des commandes pour travailler avec des projets .NET.</span><span class="sxs-lookup"><span data-stu-id="2f352-115">It provides commands for working with .NET projects.</span></span>

  <span data-ttu-id="2f352-116">Par exemple, [`dotnet build`](dotnet-build.md) génère un projet.</span><span class="sxs-lookup"><span data-stu-id="2f352-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="2f352-117">Chaque commande définit ses propres options et arguments.</span><span class="sxs-lookup"><span data-stu-id="2f352-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="2f352-118">Toutes les commandes prennent en charge l' `--help` option d’impression d’une brève documentation sur la façon d’utiliser la commande.</span><span class="sxs-lookup"><span data-stu-id="2f352-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="2f352-119">Il exécute des applications .NET.</span><span class="sxs-lookup"><span data-stu-id="2f352-119">It runs .NET applications.</span></span>

  <span data-ttu-id="2f352-120">Vous spécifiez le chemin d’accès à un fichier d’application `.dll` pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="2f352-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="2f352-121">Pour exécuter l’application, vous devez rechercher et exécuter le point d’entrée, ce qui, dans le cas des applications console, est la `Main` méthode.</span><span class="sxs-lookup"><span data-stu-id="2f352-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="2f352-122">Par exemple, `dotnet myapp.dll` exécute l' `myapp` application.</span><span class="sxs-lookup"><span data-stu-id="2f352-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="2f352-123">Consultez [déploiement d’applications .net](../deploying/index.md) pour en savoir plus sur les options de déploiement.</span><span class="sxs-lookup"><span data-stu-id="2f352-123">See [.NET application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="2f352-124">Options</span><span class="sxs-lookup"><span data-stu-id="2f352-124">Options</span></span>

<span data-ttu-id="2f352-125">Différentes options sont disponibles pour `dotnet` par elle-même, pour exécuter une commande et pour exécuter une application.</span><span class="sxs-lookup"><span data-stu-id="2f352-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="2f352-126">Options de dotnet par lui-même</span><span class="sxs-lookup"><span data-stu-id="2f352-126">Options for dotnet by itself</span></span>

<span data-ttu-id="2f352-127">Les options suivantes sont destinées `dotnet` à elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="2f352-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="2f352-128">Par exemple : `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="2f352-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="2f352-129">Ils affichent des informations sur l’environnement.</span><span class="sxs-lookup"><span data-stu-id="2f352-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="2f352-130">Affiche des informations détaillées sur une installation .NET et l’environnement de l’ordinateur, telles que le système d’exploitation actuel, et la validation de l’algorithme SHA de la version .NET.</span><span class="sxs-lookup"><span data-stu-id="2f352-130">Prints out detailed information about a .NET installation and the machine environment, such as the current operating system, and commit SHA of the .NET version.</span></span>

- **`--version`**

  <span data-ttu-id="2f352-131">Imprime la version du kit de développement logiciel (SDK) .NET en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="2f352-131">Prints out the version of the .NET SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="2f352-132">Imprime une liste des runtimes .NET installés.</span><span class="sxs-lookup"><span data-stu-id="2f352-132">Prints out a list of the installed .NET runtimes.</span></span> <span data-ttu-id="2f352-133">Une version x86 du kit de développement logiciel (SDK) répertorie uniquement les runtimes x86, et une version x64 du kit de développement logiciel (SDK) répertorie uniquement les runtimes x64.</span><span class="sxs-lookup"><span data-stu-id="2f352-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="2f352-134">Affiche la liste des kits de développement logiciel (SDK) .NET installés.</span><span class="sxs-lookup"><span data-stu-id="2f352-134">Prints out a list of the installed .NET SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2f352-135">Imprime une liste des commandes disponibles.</span><span class="sxs-lookup"><span data-stu-id="2f352-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="2f352-136">Options du kit de développement logiciel pour exécuter une commande</span><span class="sxs-lookup"><span data-stu-id="2f352-136">SDK options for running a command</span></span>

<span data-ttu-id="2f352-137">Les options suivantes concernent `dotnet` avec une commande.</span><span class="sxs-lookup"><span data-stu-id="2f352-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="2f352-138">Par exemple : `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="2f352-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="2f352-139">Active la sortie de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="2f352-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2f352-140">Définit le niveau de détail de la commande.</span><span class="sxs-lookup"><span data-stu-id="2f352-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2f352-141">Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2f352-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="2f352-142">Non pris en charge dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="2f352-142">Not supported in every command.</span></span> <span data-ttu-id="2f352-143">Consultez la page de commande spécifique pour déterminer si cette option est disponible.</span><span class="sxs-lookup"><span data-stu-id="2f352-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2f352-144">Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="2f352-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="2f352-145">Chaque commande définit des options spécifiques à cette commande.</span><span class="sxs-lookup"><span data-stu-id="2f352-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="2f352-146">Pour obtenir la liste des options disponibles, consultez la page de commande spécifique.</span><span class="sxs-lookup"><span data-stu-id="2f352-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="2f352-147">Options d’exécution</span><span class="sxs-lookup"><span data-stu-id="2f352-147">Runtime options</span></span>

<span data-ttu-id="2f352-148">Les options suivantes sont disponibles lors de l' `dotnet` exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="2f352-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="2f352-149">Par exemple : `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="2f352-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="2f352-150">Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.</span><span class="sxs-lookup"><span data-stu-id="2f352-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="2f352-151">Chemin d’un fichier *.deps.json* supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="2f352-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="2f352-152">Un *deps.jssur* un fichier contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour traiter les conflits d’assembly.</span><span class="sxs-lookup"><span data-stu-id="2f352-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="2f352-153">Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.</span><span class="sxs-lookup"><span data-stu-id="2f352-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="2f352-154">Chemin d’accès à la *deps.jssur* le fichier.</span><span class="sxs-lookup"><span data-stu-id="2f352-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="2f352-155">Un *deps.jssur le* fichier est un fichier de configuration qui contient des informations sur les dépendances nécessaires à l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="2f352-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="2f352-156">Ce fichier est généré par le kit de développement logiciel (SDK) .NET.</span><span class="sxs-lookup"><span data-stu-id="2f352-156">This file is generated by the .NET SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="2f352-157">Chemin d’un fichier *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="2f352-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="2f352-158">Un *runtimeconfig.jssur le* fichier est un fichier de configuration qui contient des paramètres d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f352-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="2f352-159">Pour plus d’informations, consultez [paramètres de configuration du Runtime .net](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="2f352-159">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="2f352-160">**`--roll-forward <SETTING>`\*\*\*\*Disponible à partir de kit SDK .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="2f352-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="2f352-161">Contrôle la façon dont la restauration par progression est appliquée à l’application.</span><span class="sxs-lookup"><span data-stu-id="2f352-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="2f352-162">`SETTING`Peut prendre l’une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="2f352-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="2f352-163">S’il n’est pas spécifié, `Minor` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f352-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="2f352-164">`LatestPatch` -Restauration par progression vers la version de correctif la plus récente.</span><span class="sxs-lookup"><span data-stu-id="2f352-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="2f352-165">Cette valeur désactive la restauration par progression d’une version mineure.</span><span class="sxs-lookup"><span data-stu-id="2f352-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="2f352-166">`Minor` -Restaurer par progression jusqu’à la version mineure la plus basse, si la version mineure demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="2f352-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="2f352-167">Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2f352-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="2f352-168">`Major` -Restauration par progression vers la version principale la plus basse, et version mineure la plus faible, si la version principale demandée est manquante.</span><span class="sxs-lookup"><span data-stu-id="2f352-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="2f352-169">Si la version majeure demandée est présente, la stratégie Minor est utilisée.</span><span class="sxs-lookup"><span data-stu-id="2f352-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="2f352-170">`LatestMinor` -Restaurer par progression vers la version mineure la plus élevée, même si la version mineure demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="2f352-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="2f352-171">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="2f352-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="2f352-172">`LatestMajor` -Restauration par progression vers la version mineure la plus élevée et la plus élevée, même si la version principale demandée est présente.</span><span class="sxs-lookup"><span data-stu-id="2f352-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="2f352-173">Conçu pour les scénarios d’hébergement de composant.</span><span class="sxs-lookup"><span data-stu-id="2f352-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="2f352-174">`Disable` -Ne pas restaurer par progression.</span><span class="sxs-lookup"><span data-stu-id="2f352-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="2f352-175">Lier uniquement à la version spécifiée.</span><span class="sxs-lookup"><span data-stu-id="2f352-175">Only bind to specified version.</span></span> <span data-ttu-id="2f352-176">Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs.</span><span class="sxs-lookup"><span data-stu-id="2f352-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="2f352-177">Cette valeur est recommandée uniquement à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="2f352-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="2f352-178">À l’exception de `Disable` , tous les paramètres utilisent la version de correctif la plus élevée disponible.</span><span class="sxs-lookup"><span data-stu-id="2f352-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="2f352-179">Le comportement de restauration par progression peut également être configuré dans une propriété de fichier projet, une propriété de fichier de configuration au moment de l’exécution et une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="2f352-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="2f352-180">Pour plus d’informations, consultez [restauration par progression du runtime de version principale](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="2f352-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="2f352-181">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponible dans le kit de développement logiciel (SDK) .net Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="2f352-182">Définit le comportement quand le framework partagé requis n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="2f352-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="2f352-183">Voici à quoi `N` peut correspondre :</span><span class="sxs-lookup"><span data-stu-id="2f352-183">`N` can be:</span></span>

  - <span data-ttu-id="2f352-184">`0` : désactiver l’extrapolation même pour les versions mineures.</span><span class="sxs-lookup"><span data-stu-id="2f352-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="2f352-185">`1` : extrapoler la version mineure, mais pas la version majeure.</span><span class="sxs-lookup"><span data-stu-id="2f352-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="2f352-186">Il s'agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f352-186">This is the default behavior.</span></span>
  - <span data-ttu-id="2f352-187">`2` : extrapoler les versions majeures et mineures.</span><span class="sxs-lookup"><span data-stu-id="2f352-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="2f352-188">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="2f352-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="2f352-189">À compter de .NET Core 3,0, cette option est remplacée par `--roll-forward` , et cette option doit être utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="2f352-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="2f352-190">Version du Runtime .NET à utiliser pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="2f352-190">Version of the .NET runtime to use to run the application.</span></span>

  <span data-ttu-id="2f352-191">Cette option remplace la version de la première référence de Framework dans le fichier de l’application `.runtimeconfig.json` .</span><span class="sxs-lookup"><span data-stu-id="2f352-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="2f352-192">Cela signifie qu’il ne fonctionne comme prévu que s’il n’existe qu’une seule référence d’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="2f352-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="2f352-193">Si l’application a plus d’une référence d’infrastructure, l’utilisation de cette option peut provoquer des erreurs.</span><span class="sxs-lookup"><span data-stu-id="2f352-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="2f352-194">Commandes dotnet</span><span class="sxs-lookup"><span data-stu-id="2f352-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="2f352-195">Général</span><span class="sxs-lookup"><span data-stu-id="2f352-195">General</span></span>

| <span data-ttu-id="2f352-196">Commande</span><span class="sxs-lookup"><span data-stu-id="2f352-196">Command</span></span>                                       | <span data-ttu-id="2f352-197">Fonction</span><span class="sxs-lookup"><span data-stu-id="2f352-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="2f352-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="2f352-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="2f352-199">Génère une application .NET.</span><span class="sxs-lookup"><span data-stu-id="2f352-199">Builds a .NET application.</span></span>                                     |
| [<span data-ttu-id="2f352-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="2f352-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="2f352-201">Interagit avec les serveurs démarrés par une build.</span><span class="sxs-lookup"><span data-stu-id="2f352-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="2f352-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="2f352-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="2f352-203">Nettoie les sorties de build.</span><span class="sxs-lookup"><span data-stu-id="2f352-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="2f352-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="2f352-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="2f352-205">Affiche plus de documentation détaillée en ligne pour la commande.</span><span class="sxs-lookup"><span data-stu-id="2f352-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="2f352-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="2f352-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="2f352-207">Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="2f352-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="2f352-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="2f352-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="2f352-209">Fournit l’accès à la ligne de commande MSBuild.</span><span class="sxs-lookup"><span data-stu-id="2f352-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="2f352-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="2f352-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="2f352-211">Initialise un projet C# ou F# pour un modèle donné.</span><span class="sxs-lookup"><span data-stu-id="2f352-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="2f352-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="2f352-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="2f352-213">Crée un package NuGet à partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2f352-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="2f352-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="2f352-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="2f352-215">Publie une application .NET dépendante du framework ou autonome.</span><span class="sxs-lookup"><span data-stu-id="2f352-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="2f352-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="2f352-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="2f352-217">Restaure les dépendances d’une application donnée.</span><span class="sxs-lookup"><span data-stu-id="2f352-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="2f352-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="2f352-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="2f352-219">Exécute l’application à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="2f352-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="2f352-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="2f352-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="2f352-221">Options pour ajouter, supprimer et lister des projets dans un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="2f352-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="2f352-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="2f352-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="2f352-223">Stocke les assemblys dans le magasin de packages de runtime.</span><span class="sxs-lookup"><span data-stu-id="2f352-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="2f352-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="2f352-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="2f352-225">Exécute des tests à l’aide d’un lanceur de tests.</span><span class="sxs-lookup"><span data-stu-id="2f352-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="2f352-226">Références de projets</span><span class="sxs-lookup"><span data-stu-id="2f352-226">Project references</span></span>

<span data-ttu-id="2f352-227">Commande</span><span class="sxs-lookup"><span data-stu-id="2f352-227">Command</span></span> | <span data-ttu-id="2f352-228">Fonction</span><span class="sxs-lookup"><span data-stu-id="2f352-228">Function</span></span>
--- | ---
[<span data-ttu-id="2f352-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="2f352-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="2f352-230">Ajoute une référence au projet.</span><span class="sxs-lookup"><span data-stu-id="2f352-230">Adds a project reference.</span></span>
[<span data-ttu-id="2f352-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="2f352-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="2f352-232">Liste les références du projet.</span><span class="sxs-lookup"><span data-stu-id="2f352-232">Lists project references.</span></span>
[<span data-ttu-id="2f352-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="2f352-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="2f352-234">Supprime une référence de projet.</span><span class="sxs-lookup"><span data-stu-id="2f352-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="2f352-235">Packages NuGet</span><span class="sxs-lookup"><span data-stu-id="2f352-235">NuGet packages</span></span>

<span data-ttu-id="2f352-236">Commande</span><span class="sxs-lookup"><span data-stu-id="2f352-236">Command</span></span> | <span data-ttu-id="2f352-237">Fonction</span><span class="sxs-lookup"><span data-stu-id="2f352-237">Function</span></span>
--- | ---
[<span data-ttu-id="2f352-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="2f352-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="2f352-239">Ajoute un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="2f352-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="2f352-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="2f352-241">Supprime un package NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="2f352-242">Commandes NuGet</span><span class="sxs-lookup"><span data-stu-id="2f352-242">NuGet commands</span></span>

<span data-ttu-id="2f352-243">Commande</span><span class="sxs-lookup"><span data-stu-id="2f352-243">Command</span></span> | <span data-ttu-id="2f352-244">Fonction</span><span class="sxs-lookup"><span data-stu-id="2f352-244">Function</span></span>
--- | ---
[<span data-ttu-id="2f352-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="2f352-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="2f352-246">Supprime ou retire un package du serveur.</span><span class="sxs-lookup"><span data-stu-id="2f352-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="2f352-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="2f352-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="2f352-248">Effectue une transmission de type push d’un package sur le serveur et le publie.</span><span class="sxs-lookup"><span data-stu-id="2f352-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="2f352-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="2f352-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="2f352-250">Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f352-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="2f352-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="2f352-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="2f352-252">Ajoute une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="2f352-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="2f352-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="2f352-254">Désactive une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="2f352-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="2f352-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="2f352-256">Active une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="2f352-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="2f352-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="2f352-258">Répertorie toutes les sources NuGet configurées.</span><span class="sxs-lookup"><span data-stu-id="2f352-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="2f352-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="2f352-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="2f352-260">Supprime une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="2f352-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="2f352-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="2f352-262">Met à jour une source NuGet.</span><span class="sxs-lookup"><span data-stu-id="2f352-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="2f352-263">Commandes globales, de chemin d’accès d’outil et d’outils locaux</span><span class="sxs-lookup"><span data-stu-id="2f352-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="2f352-264">Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="2f352-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="2f352-265">Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers.</span><span class="sxs-lookup"><span data-stu-id="2f352-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="2f352-266">Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux.</span><span class="sxs-lookup"><span data-stu-id="2f352-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="2f352-267">Pour plus d’informations, consultez [vue d’ensemble des outils .net](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="2f352-267">For more information, see [.NET tools overview](global-tools.md).</span></span> <span data-ttu-id="2f352-268">Les outils globaux et de chemin d’accès aux outils sont disponibles à partir de kit SDK .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="2f352-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="2f352-269">Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2f352-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="2f352-270">Commande</span><span class="sxs-lookup"><span data-stu-id="2f352-270">Command</span></span> | <span data-ttu-id="2f352-271">Fonction</span><span class="sxs-lookup"><span data-stu-id="2f352-271">Function</span></span>
--- | ---
[<span data-ttu-id="2f352-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="2f352-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="2f352-273">Installe un outil sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f352-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="2f352-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="2f352-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="2f352-275">Répertorie tous les outils globaux, de chemin d’accès d’outil ou locaux actuellement installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f352-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="2f352-276">recherche d’outils dotnet</span><span class="sxs-lookup"><span data-stu-id="2f352-276">dotnet tool search</span></span>](dotnet-tool-list.md) | <span data-ttu-id="2f352-277">Recherche dans NuGet.org les outils dont le nom ou les métadonnées contiennent le terme de recherche spécifié.</span><span class="sxs-lookup"><span data-stu-id="2f352-277">Searches NuGet.org for tools that have the specified search term in their name or metadata.</span></span>
[<span data-ttu-id="2f352-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="2f352-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="2f352-279">Désinstalle un outil de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f352-279">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="2f352-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="2f352-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="2f352-281">Met à jour un outil qui est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2f352-281">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="2f352-282">Outils supplémentaires</span><span class="sxs-lookup"><span data-stu-id="2f352-282">Additional tools</span></span>

<span data-ttu-id="2f352-283">À compter de kit SDK .NET Core 2.1.300, un certain nombre d’outils qui étaient uniquement disponibles par projet à l’aide `DotnetCliToolReference` de sont désormais disponibles dans le cadre du kit de développement logiciel (SDK) .net.</span><span class="sxs-lookup"><span data-stu-id="2f352-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET SDK.</span></span> <span data-ttu-id="2f352-284">Ces outils sont répertoriés dans le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="2f352-284">These tools are listed in the following table:</span></span>

| <span data-ttu-id="2f352-285">Outil</span><span class="sxs-lookup"><span data-stu-id="2f352-285">Tool</span></span>                                              | <span data-ttu-id="2f352-286">Fonction</span><span class="sxs-lookup"><span data-stu-id="2f352-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="2f352-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="2f352-287">dev-certs</span></span>                                         | <span data-ttu-id="2f352-288">Crée et gère les certificats de développement.</span><span class="sxs-lookup"><span data-stu-id="2f352-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="2f352-289">EF</span><span class="sxs-lookup"><span data-stu-id="2f352-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="2f352-290">Outils en ligne de commande Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="2f352-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="2f352-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="2f352-291">sql-cache</span></span>                                         | <span data-ttu-id="2f352-292">Outils en ligne de commande du cache SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2f352-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="2f352-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="2f352-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="2f352-294">Gère les secrets de développement de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f352-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="2f352-295">vérifier</span><span class="sxs-lookup"><span data-stu-id="2f352-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="2f352-296">Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier.</span><span class="sxs-lookup"><span data-stu-id="2f352-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="2f352-297">Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="2f352-297">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="2f352-298">Exemples</span><span class="sxs-lookup"><span data-stu-id="2f352-298">Examples</span></span>

<span data-ttu-id="2f352-299">Créez une application de console .NET :</span><span class="sxs-lookup"><span data-stu-id="2f352-299">Create a new .NET console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="2f352-300">Générez un projet et ses dépendances dans un répertoire donné :</span><span class="sxs-lookup"><span data-stu-id="2f352-300">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="2f352-301">Exécuter une application :</span><span class="sxs-lookup"><span data-stu-id="2f352-301">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="2f352-302">Variables d'environnement</span><span class="sxs-lookup"><span data-stu-id="2f352-302">Environment variables</span></span>

- <span data-ttu-id="2f352-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="2f352-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="2f352-304">Spécifie l’emplacement des runtimes .NET, s’ils ne sont pas installés à l’emplacement par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f352-304">Specifies the location of the .NET runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="2f352-305">L’emplacement par défaut sur Windows est `C:\Program Files\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="2f352-305">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="2f352-306">L’emplacement par défaut sur Linux et macOS est `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="2f352-306">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="2f352-307">Cette variable d’environnement est utilisée uniquement lors de l’exécution d’applications via des exécutables générés (apphosts).</span><span class="sxs-lookup"><span data-stu-id="2f352-307">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="2f352-308">`DOTNET_ROOT(x86)` est utilisé à la place lors de l’exécution d’un fichier exécutable 32 bits sur un système d’exploitation 64 bits.</span><span class="sxs-lookup"><span data-stu-id="2f352-308">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `NUGET_PACKAGES`

  <span data-ttu-id="2f352-309">Le dossier de packages global.</span><span class="sxs-lookup"><span data-stu-id="2f352-309">The global packages folder.</span></span> <span data-ttu-id="2f352-310">S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.</span><span class="sxs-lookup"><span data-stu-id="2f352-310">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="2f352-311">Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2f352-311">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="2f352-312">Spécifie si les messages de bienvenue et de télémétrie .NET s’affichent lors de la première exécution.</span><span class="sxs-lookup"><span data-stu-id="2f352-312">Specifies whether .NET welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="2f352-313">Affectez la valeur pour `true` désactiver ces messages (valeurs `true` , `1` ou `yes` acceptés) ou la valeur à `false` autoriser (valeurs `false` , `0` ou `no` acceptées).</span><span class="sxs-lookup"><span data-stu-id="2f352-313">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="2f352-314">Si la valeur n’est pas définie, la valeur par défaut est `false` et les messages sont affichés lors de la première exécution.</span><span class="sxs-lookup"><span data-stu-id="2f352-314">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="2f352-315">Cet indicateur n’a aucun effet sur la télémétrie (voir pour le refus `DOTNET_CLI_TELEMETRY_OPTOUT` d’envoyer des données de télémétrie).</span><span class="sxs-lookup"><span data-stu-id="2f352-315">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="2f352-316">Spécifie si les données relatives à l’utilisation des outils .NET sont collectées et envoyées à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2f352-316">Specifies whether data about the .NET tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="2f352-317">Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`).</span><span class="sxs-lookup"><span data-stu-id="2f352-317">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="2f352-318">Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`).</span><span class="sxs-lookup"><span data-stu-id="2f352-318">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="2f352-319">Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.</span><span class="sxs-lookup"><span data-stu-id="2f352-319">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="2f352-320">Spécifie si le Runtime .NET, le Framework partagé ou le kit de développement logiciel (SDK) sont résolus à partir de l’emplacement global.</span><span class="sxs-lookup"><span data-stu-id="2f352-320">Specifies whether .NET runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="2f352-321">S’il n’est pas défini, la valeur par défaut est 1 (logique `true` ).</span><span class="sxs-lookup"><span data-stu-id="2f352-321">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="2f352-322">Définissez sur 0 (logique `false` ) pour ne pas résoudre à partir de l’emplacement global et avoir des installations .net isolées.</span><span class="sxs-lookup"><span data-stu-id="2f352-322">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET installations.</span></span> <span data-ttu-id="2f352-323">Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="2f352-323">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="2f352-324">`DOTNET_ROLL_FORWARD`**Disponible à partir de .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-324">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="2f352-325">Détermine le comportement de restauration par progression.</span><span class="sxs-lookup"><span data-stu-id="2f352-325">Determines roll forward behavior.</span></span> <span data-ttu-id="2f352-326">Pour plus d’informations, consultez l' `--roll-forward` option plus haut dans cet article.</span><span class="sxs-lookup"><span data-stu-id="2f352-326">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="2f352-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE`**Disponible à partir de .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="2f352-328">Si la valeur est `1` (activé), permet de restaurer une version préliminaire à partir d’une version Release.</span><span class="sxs-lookup"><span data-stu-id="2f352-328">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="2f352-329">Par défaut ( `0` -désactivé), quand une version Release du Runtime .net est demandée, la restauration par progression ne prend en compte que les versions de version installée.</span><span class="sxs-lookup"><span data-stu-id="2f352-329">By default (`0` - disabled), when a release version of .NET runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="2f352-330">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="2f352-330">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="2f352-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponible dans .net Core 2. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="2f352-332">Désactive la restauration par progression d’une version mineure, si la valeur est `0`.</span><span class="sxs-lookup"><span data-stu-id="2f352-332">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="2f352-333">Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="2f352-333">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="2f352-334">Ce paramètre est remplacé dans .NET Core 3,0 par `DOTNET_ROLL_FORWARD` .</span><span class="sxs-lookup"><span data-stu-id="2f352-334">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="2f352-335">Les nouveaux paramètres doivent être utilisés à la place.</span><span class="sxs-lookup"><span data-stu-id="2f352-335">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="2f352-336">Définit le langage de l’interface utilisateur CLI à l’aide d’une valeur de paramètres régionaux telle que `en-us` .</span><span class="sxs-lookup"><span data-stu-id="2f352-336">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="2f352-337">Les valeurs prises en charge sont les mêmes que pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f352-337">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="2f352-338">Pour plus d’informations, consultez la section relative à la modification du langage d’installation dans la [documentation d’installation de Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="2f352-338">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="2f352-339">Les règles .NET Resource Manager s’appliquent. vous n’avez donc pas à choisir une correspondance exacte &mdash; . vous pouvez également choisir des descendants dans l' `CultureInfo` arborescence.</span><span class="sxs-lookup"><span data-stu-id="2f352-339">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="2f352-340">Par exemple, si vous affectez la valeur à `fr-CA` , l’interface CLI trouvera et utilisera les `fr` traductions.</span><span class="sxs-lookup"><span data-stu-id="2f352-340">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="2f352-341">Si vous définissez une langue qui n’est pas prise en charge, l’interface CLI revient à l’anglais.</span><span class="sxs-lookup"><span data-stu-id="2f352-341">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="2f352-342">Pour les exécutables générés par l’interface utilisateur graphique : désactive la boîte de dialogue contextuelle, qui affiche généralement certaines classes d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="2f352-342">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="2f352-343">Il écrit uniquement `stderr` dans et se termine dans ces cas-là.</span><span class="sxs-lookup"><span data-stu-id="2f352-343">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="2f352-344">Équivalent à l’option CLI `--additional-deps` .</span><span class="sxs-lookup"><span data-stu-id="2f352-344">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="2f352-345">Remplace le RID détecté.</span><span class="sxs-lookup"><span data-stu-id="2f352-345">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="2f352-346">Emplacement du « magasin partagé » dans lequel la résolution de l’assembly revient dans certains cas.</span><span class="sxs-lookup"><span data-stu-id="2f352-346">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="2f352-347">Liste des assemblys à partir desquels charger et exécuter des raccordements de démarrage.</span><span class="sxs-lookup"><span data-stu-id="2f352-347">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="2f352-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR`**Disponible à partir de .net Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="2f352-349">Spécifie un répertoire dans lequel une application à fichier unique est extraite avant d’être exécutée.</span><span class="sxs-lookup"><span data-stu-id="2f352-349">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="2f352-350">Pour plus d’informations, consultez [fichiers exécutables à fichier unique](../whats-new/dotnet-core-3-0.md#single-file-executables).</span><span class="sxs-lookup"><span data-stu-id="2f352-350">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="2f352-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="2f352-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="2f352-352">Contrôle le suivi des diagnostics à partir des composants d’hébergement, tels que `dotnet.exe` , `hostfxr` et `hostpolicy` .</span><span class="sxs-lookup"><span data-stu-id="2f352-352">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="2f352-353">`COREHOST_TRACE=[0/1]` -le suivi par défaut est `0` désactivé.</span><span class="sxs-lookup"><span data-stu-id="2f352-353">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="2f352-354">Si la valeur `1` est, le suivi des diagnostics est activé.</span><span class="sxs-lookup"><span data-stu-id="2f352-354">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="2f352-355">`COREHOST_TRACEFILE=<file path>` -n’a d’effet que si le suivi est activé via `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="2f352-355">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="2f352-356">Lorsque cette valeur est définie, les informations de traçage sont écrites dans le fichier spécifié, dans le cas contraire, les informations de traçage sont écrites dans `stderr` .</span><span class="sxs-lookup"><span data-stu-id="2f352-356">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="2f352-357">**Disponible à partir de .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-357">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="2f352-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` -la valeur par défaut est `4` .</span><span class="sxs-lookup"><span data-stu-id="2f352-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="2f352-359">Le paramètre est utilisé uniquement lorsque le suivi est activé via `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="2f352-359">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="2f352-360">**Disponible à partir de .NET Core 3. x.**</span><span class="sxs-lookup"><span data-stu-id="2f352-360">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="2f352-361">`4` -toutes les informations de traçage sont écrites</span><span class="sxs-lookup"><span data-stu-id="2f352-361">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="2f352-362">`3` -Seuls les messages d’information, d’avertissement et d’erreur sont écrits</span><span class="sxs-lookup"><span data-stu-id="2f352-362">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="2f352-363">`2` -Seuls les messages d’avertissement et d’erreur sont écrits</span><span class="sxs-lookup"><span data-stu-id="2f352-363">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="2f352-364">`1` -Seuls les messages d’erreur sont écrits</span><span class="sxs-lookup"><span data-stu-id="2f352-364">`1` - only error messages are written</span></span>

  <span data-ttu-id="2f352-365">La méthode habituelle pour obtenir des informations de suivi détaillées sur le démarrage de l’application consiste à définir, puis à `COREHOST_TRACE=1` `COREHOST_TRACEFILE=host_trace.txt` exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="2f352-365">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="2f352-366">Un nouveau fichier `host_trace.txt` est créé dans le répertoire actif avec les informations détaillées.</span><span class="sxs-lookup"><span data-stu-id="2f352-366">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f352-367">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f352-367">See also</span></span>

- [<span data-ttu-id="2f352-368">Runtime Configuration Files</span><span class="sxs-lookup"><span data-stu-id="2f352-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="2f352-369">Paramètres de configuration .NET Runtime</span><span class="sxs-lookup"><span data-stu-id="2f352-369">.NET run-time configuration settings</span></span>](../run-time-config/index.md)
