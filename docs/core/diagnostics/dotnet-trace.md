---
title: outil de diagnostic dotnet-trace-CLI .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-trace pour collecter les traces .NET d’un processus en cours d’exécution sans le profileur natif, à l’aide de .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: a3b5748cb2a6c2060971fbad0d81ade00dc83087
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753664"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="bf7b1-103">utilitaire d’analyse des performances dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bf7b1-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="bf7b1-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bf7b1-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="bf7b1-105">Installer</span><span class="sxs-lookup"><span data-stu-id="bf7b1-105">Install</span></span>

<span data-ttu-id="bf7b1-106">Il existe deux façons de télécharger et d’installer `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="bf7b1-107">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="bf7b1-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="bf7b1-108">Pour installer la dernière version Release du `dotnet-trace` [package NuGet](https://www.nuget.org/packages/dotnet-trace), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="bf7b1-109">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="bf7b1-109">**Direct download:**</span></span>

  <span data-ttu-id="bf7b1-110">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="bf7b1-111">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="bf7b1-111">OS</span></span>  | <span data-ttu-id="bf7b1-112">Plateforme</span><span class="sxs-lookup"><span data-stu-id="bf7b1-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="bf7b1-113">Windows</span><span class="sxs-lookup"><span data-stu-id="bf7b1-113">Windows</span></span> | <span data-ttu-id="bf7b1-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [ARM](https://aka.ms/dotnet-trace/win-arm) \| [ARM-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="bf7b1-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="bf7b1-115">macOS</span><span class="sxs-lookup"><span data-stu-id="bf7b1-115">macOS</span></span>   | [<span data-ttu-id="bf7b1-116">x64</span><span class="sxs-lookup"><span data-stu-id="bf7b1-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="bf7b1-117">Linux</span><span class="sxs-lookup"><span data-stu-id="bf7b1-117">Linux</span></span>   | <span data-ttu-id="bf7b1-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [ARM](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="bf7b1-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="bf7b1-119">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bf7b1-119">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="bf7b1-120">Description</span><span class="sxs-lookup"><span data-stu-id="bf7b1-120">Description</span></span>

<span data-ttu-id="bf7b1-121">L' `dotnet-trace` outil :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-121">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="bf7b1-122">Est un outil .NET Core multiplateforme.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-122">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="bf7b1-123">Active la collecte des traces .NET Core d’un processus en cours d’exécution sans profileur natif.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-123">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="bf7b1-124">Repose sur [`EventPipe`](./eventpipe.md) le Runtime .net core.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-124">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="bf7b1-125">Offre la même expérience sur Windows, Linux ou macOS.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-125">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="bf7b1-126">Options</span><span class="sxs-lookup"><span data-stu-id="bf7b1-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="bf7b1-127">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-127">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="bf7b1-128">Affiche la version de l’utilitaire dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-128">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="bf7b1-129">Commandes</span><span class="sxs-lookup"><span data-stu-id="bf7b1-129">Commands</span></span>

| <span data-ttu-id="bf7b1-130">Commande</span><span class="sxs-lookup"><span data-stu-id="bf7b1-130">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="bf7b1-131">dotnet-collecte des traces</span><span class="sxs-lookup"><span data-stu-id="bf7b1-131">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="bf7b1-132">conversion dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bf7b1-132">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="bf7b1-133">dotnet-trace PS</span><span class="sxs-lookup"><span data-stu-id="bf7b1-133">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="bf7b1-134">liste de suivi dotnet-profils</span><span class="sxs-lookup"><span data-stu-id="bf7b1-134">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="bf7b1-135">dotnet-collecte des traces</span><span class="sxs-lookup"><span data-stu-id="bf7b1-135">dotnet-trace collect</span></span>

<span data-ttu-id="bf7b1-136">Collecte une trace de diagnostic à partir d’un processus en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-136">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="bf7b1-137">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bf7b1-137">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="bf7b1-138">Options</span><span class="sxs-lookup"><span data-stu-id="bf7b1-138">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="bf7b1-139">Définit la taille de la mémoire tampon circulaire en mémoire, en mégaoctets.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-139">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="bf7b1-140">256 Mo par défaut.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-140">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="bf7b1-141">Commentaires des événements CLR à émettre.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-141">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="bf7b1-142">Liste des événements du runtime CLR à émettre.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-142">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="bf7b1-143">Définit le format de sortie pour la conversion du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-143">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="bf7b1-144">Par défaut, il s’agit de `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-144">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="bf7b1-145">Nom du processus à partir duquel la trace doit être collectée.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-145">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="bf7b1-146">Nom du port de diagnostic à créer.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-146">The name of the diagnostic port to create.</span></span> <span data-ttu-id="bf7b1-147">Consultez [utiliser le port de diagnostic pour collecter une trace à partir du démarrage](#use-diagnostic-port-to-collect-a-trace-from-app-startup) de l’application pour savoir comment utiliser cette option pour collecter une trace à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-147">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="bf7b1-148">Chemin de sortie pour les données de trace collectées.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-148">The output path for the collected trace data.</span></span> <span data-ttu-id="bf7b1-149">S’il n’est pas spécifié, la valeur par défaut est `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-149">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="bf7b1-150">ID de processus à partir duquel la trace doit être collectée.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-150">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="bf7b1-151">Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-151">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="bf7b1-152">Les profils suivants sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-152">The following profiles are available:</span></span>

 | <span data-ttu-id="bf7b1-153">Profil</span><span class="sxs-lookup"><span data-stu-id="bf7b1-153">Profile</span></span> | <span data-ttu-id="bf7b1-154">Description</span><span class="sxs-lookup"><span data-stu-id="bf7b1-154">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="bf7b1-155">Utile pour le suivi de l’utilisation de l’UC et des informations générales du Runtime .NET.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-155">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="bf7b1-156">Il s’agit de l’option par défaut si aucun profil ou fournisseur n’est spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-156">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="bf7b1-157">Effectue le suivi des collections GC et des exemples d’allocations d’objets.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-157">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="bf7b1-158">Effectue le suivi des collections GC uniquement à faible surcharge.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-158">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="bf7b1-159">Liste séparée par des virgules des `EventPipe` fournisseurs à activer.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-159">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="bf7b1-160">Ces fournisseurs complètent tous les fournisseurs implicites par `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-160">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="bf7b1-161">S’il existe une incohérence pour un fournisseur particulier, cette configuration est prioritaire par rapport à la configuration implicite à partir du profil.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-161">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="bf7b1-162">Cette liste de fournisseurs se présente sous la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-162">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="bf7b1-163">`Provider` se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-163">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="bf7b1-164">`KeyValueArgs` se présente sous la forme : `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-164">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="bf7b1-165">**`-- <command>` (pour les applications cibles exécutant .NET 5,0 uniquement)**</span><span class="sxs-lookup"><span data-stu-id="bf7b1-165">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="bf7b1-166">Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-166">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="bf7b1-167">Cela peut être utile lors du diagnostic de problèmes qui se produisent tôt dans le processus, tels que le problème de performance de démarrage ou le chargeur d’assembly et les erreurs de Binder.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-167">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="bf7b1-168">L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-168">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="bf7b1-169">Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-169">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="bf7b1-170">L’arrêt de la trace peut prendre beaucoup de temps (jusqu’à quelques minutes) pour les applications de grande taille.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-170">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="bf7b1-171">Le Runtime doit envoyer sur le cache de type pour tout le code managé qui a été capturé dans la trace.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-171">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="bf7b1-172">conversion dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bf7b1-172">dotnet-trace convert</span></span>

<span data-ttu-id="bf7b1-173">Convertit les `nettrace` traces en d’autres formats pour les utiliser avec d’autres outils d’analyse de trace.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-173">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="bf7b1-174">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bf7b1-174">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="bf7b1-175">Arguments</span><span class="sxs-lookup"><span data-stu-id="bf7b1-175">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="bf7b1-176">Fichier de trace d’entrée à convertir.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-176">Input trace file to be converted.</span></span> <span data-ttu-id="bf7b1-177">La valeur par défaut est *trace. NetTrace*.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-177">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="bf7b1-178">Options</span><span class="sxs-lookup"><span data-stu-id="bf7b1-178">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="bf7b1-179">Définit le format de sortie pour la conversion du fichier de trace.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-179">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="bf7b1-180">Nom du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-180">Output filename.</span></span> <span data-ttu-id="bf7b1-181">L’extension du format cible sera ajoutée.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-181">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="bf7b1-182">La conversion `nettrace` de fichiers en `chromium` `speedscope` fichiers ou est irréversible.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-182">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="bf7b1-183">`speedscope``chromium`les fichiers et ne contiennent pas toutes les informations nécessaires à la reconstruction des `nettrace` fichiers.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-183">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="bf7b1-184">Toutefois, la `convert` commande conserve le fichier d’origine `nettrace` . par conséquent, ne supprimez pas ce fichier si vous envisagez de l’ouvrir à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-184">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="bf7b1-185">dotnet-trace PS</span><span class="sxs-lookup"><span data-stu-id="bf7b1-185">dotnet-trace ps</span></span>

 <span data-ttu-id="bf7b1-186">Répertorie les processus dotnet à partir desquels les traces peuvent être collectées.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-186">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="bf7b1-187">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bf7b1-187">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="bf7b1-188">liste de suivi dotnet-profils</span><span class="sxs-lookup"><span data-stu-id="bf7b1-188">dotnet-trace list-profiles</span></span>

<span data-ttu-id="bf7b1-189">Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-189">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="bf7b1-190">Synopsis</span><span class="sxs-lookup"><span data-stu-id="bf7b1-190">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="bf7b1-191">Collecter une trace avec dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bf7b1-191">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="bf7b1-192">Pour collecter des traces à l’aide de `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-192">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="bf7b1-193">Obtient l’identificateur de processus (PID) de l’application .NET Core à partir duquel collecter les traces.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-193">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="bf7b1-194">Sur Windows, vous pouvez utiliser le gestionnaire des tâches ou la `tasklist` commande, par exemple.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-194">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="bf7b1-195">Sur Linux, par exemple, la `ps` commande.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-195">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="bf7b1-196">dotnet-trace PS</span><span class="sxs-lookup"><span data-stu-id="bf7b1-196">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="bf7b1-197">Exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-197">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="bf7b1-198">La commande précédente génère une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-198">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="bf7b1-199">Arrêtez la collecte en appuyant sur la `<Enter>` touche.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-199">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="bf7b1-200">`dotnet-trace` terminera la journalisation des événements dans le fichier *trace. NetTrace* .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-200">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="bf7b1-201">Lancer une application enfant et collecter une trace à partir de son démarrage à l’aide de dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bf7b1-201">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bf7b1-202">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-202">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="bf7b1-203">Parfois, il peut être utile de collecter une trace d’un processus à partir de son démarrage.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-203">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="bf7b1-204">Pour les applications qui exécutent .NET 5,0 ou une version ultérieure, il est possible de le faire à l’aide de dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-204">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="bf7b1-205">Cette opération démarre `hello.exe` avec `arg1` et `arg2` comme ses arguments de ligne de commande et collecte une trace à partir de son démarrage au moment de l’exécution :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-205">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="bf7b1-206">La commande précédente génère une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-206">The preceding command generates output similar to the following:</span></span>

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

<span data-ttu-id="bf7b1-207">Vous pouvez arrêter la collecte de la trace en appuyant sur ou sur la `<Enter>` `<Ctrl + C>` touche.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-207">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="bf7b1-208">Cela va également se terminer `hello.exe` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-208">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="bf7b1-209">`hello.exe`Le lancement via dotnet-trace rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-209">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="bf7b1-210">La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-210">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="bf7b1-211">Si le processus enfant se termine avant l’outil, l’outil s’arrête également et la trace doit être visible en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-211">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="bf7b1-212">Utiliser le port de diagnostic pour collecter une trace à partir du démarrage de l’application</span><span class="sxs-lookup"><span data-stu-id="bf7b1-212">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="bf7b1-213">Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-213">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="bf7b1-214">Le port de diagnostic est une nouvelle fonctionnalité d’exécution qui a été ajoutée dans .NET 5, qui vous permet de démarrer le suivi à partir du démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-214">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="bf7b1-215">Pour ce faire à l’aide de `dotnet-trace` , vous pouvez utiliser `dotnet-trace collect -- <command>` comme décrit dans les exemples ci-dessus ou utiliser l' `--diagnostic-port` option.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-215">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="bf7b1-216">L’utilisation `dotnet-trace <collect|monitor> -- <command>` de pour lancer l’application en tant que processus enfant est la manière la plus simple de la suivre rapidement de son démarrage.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-216">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="bf7b1-217">Toutefois, lorsque vous souhaitez mieux contrôler la durée de vie de l’application faisant l’objet d’un suivi (par exemple, surveiller l’application pendant les 10 premières minutes uniquement et continuer l’exécution) ou si vous devez interagir avec l’application à l’aide de l’interface CLI, l’utilisation `--diagnostic-port` de l’option vous permet de contrôler à la fois l’application cible en cours d’analyse et `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-217">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="bf7b1-218">La commande ci-dessous `dotnet-trace` crée un socket de diagnostic nommé `myport.sock` et attend une connexion.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-218">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="bf7b1-219">Sortie :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-219">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="bf7b1-220">Dans une console distincte, lancez l’application cible avec la variable d’environnement `DOTNET_DiagnosticPorts` définie sur la valeur dans la `dotnet-trace` sortie.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-220">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="bf7b1-221">Vous devez ensuite activer `dotnet-trace` le suivi pour démarrer le suivi `my-dotnet-app` :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-221">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="bf7b1-222">Le lancement de votre application avec `dotnet run` peut être problématique, car l’interface CLI dotnet peut générer de nombreux processus enfants qui ne sont pas votre application et qui peuvent se connecter à `dotnet-trace` avant votre application, en laissant votre application interrompue au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-222">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="bf7b1-223">Nous vous recommandons d’utiliser directement une version autonome de l’application ou `dotnet exec` d’utiliser pour lancer l’application.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-223">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="bf7b1-224">Afficher la trace capturée à partir de dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bf7b1-224">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="bf7b1-225">Sur Windows, les fichiers *. NetTrace* peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse : pour les traces collectées sur d’autres plateformes, le fichier de trace peut être déplacé vers un ordinateur Windows à afficher sur PerfView.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-225">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="bf7b1-226">Sur Linux, la trace peut être affichée en modifiant le format de sortie de `dotnet-trace` en `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-226">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="bf7b1-227">Le format du fichier de sortie peut être modifié à l’aide de l' `-f|--format` option : crée `-f speedscope` `dotnet-trace` un `speedscope` fichier.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-227">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="bf7b1-228">Vous pouvez choisir entre `nettrace` (option par défaut) et `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-228">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="bf7b1-229">`Speedscope` les fichiers peuvent être ouverts à l’adresse <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-229">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="bf7b1-230">Le Runtime .NET Core génère des traces au `nettrace` format.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-230">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="bf7b1-231">Les suivis sont convertis en speedscope (si spécifié) une fois la trace terminée.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-231">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="bf7b1-232">Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier d’origine `nettrace` est conservé en regard du fichier converti.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-232">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="bf7b1-233">Utiliser dotnet-trace pour collecter des valeurs de compteur au fil du temps</span><span class="sxs-lookup"><span data-stu-id="bf7b1-233">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="bf7b1-234">`dotnet-trace` puissiez</span><span class="sxs-lookup"><span data-stu-id="bf7b1-234">`dotnet-trace` can:</span></span>

* <span data-ttu-id="bf7b1-235">Utilisez `EventCounter` pour la surveillance de l’intégrité de base dans les environnements sensibles aux performances.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-235">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="bf7b1-236">Par exemple, en production.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-236">For example, in production.</span></span>
* <span data-ttu-id="bf7b1-237">Collectez les traces afin qu’elles n’aient pas besoin d’être affichées en temps réel.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-237">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="bf7b1-238">Par exemple, pour collecter les valeurs de compteur de performance du runtime, utilisez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-238">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="bf7b1-239">La commande précédente indique aux compteurs Runtime de signaler une fois toutes les secondes pour une surveillance de l’intégrité légère.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-239">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="bf7b1-240">Le remplacement d' `EventCounterIntervalSec=1` une valeur supérieure (par exemple, 60) permet la collecte d’une trace plus petite avec moins de granularité dans les données du compteur.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-240">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="bf7b1-241">La commande suivante réduit la surcharge et la taille de trace plus grande que la taille précédente :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-241">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="bf7b1-242">La commande précédente désactive les événements d’exécution et le profileur de pile managée.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-242">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="bf7b1-243">Utilisez le fichier. rsp pour éviter de taper de longues commandes</span><span class="sxs-lookup"><span data-stu-id="bf7b1-243">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="bf7b1-244">Vous pouvez lancer `dotnet-trace` avec un `.rsp` fichier qui contient les arguments à passer.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-244">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="bf7b1-245">Cela peut être utile lorsque vous activez des fournisseurs qui attendent des arguments longs ou lorsque vous utilisez un environnement de Shell qui supprime les caractères.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-245">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="bf7b1-246">Par exemple, le fournisseur suivant peut être fastidieux à taper chaque fois que vous souhaitez effectuer un suivi :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-246">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="bf7b1-247">En outre, l’exemple précédent contient dans `"` le cadre de l’argument.</span><span class="sxs-lookup"><span data-stu-id="bf7b1-247">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="bf7b1-248">Étant donné que les guillemets ne sont pas gérés de la même façon par chaque interpréteur de commandes, vous pouvez rencontrer différents problèmes lors de l’utilisation de différents interpréteurs</span><span class="sxs-lookup"><span data-stu-id="bf7b1-248">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="bf7b1-249">Par exemple, la commande à entrer dans `zsh` est différente de la commande dans `cmd` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-249">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="bf7b1-250">Au lieu de taper cette variable à chaque fois, vous pouvez enregistrer le texte suivant dans un fichier appelé `myprofile.rsp` .</span><span class="sxs-lookup"><span data-stu-id="bf7b1-250">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="bf7b1-251">Une fois que vous avez enregistré `myprofile.rsp` , vous pouvez lancer `dotnet-trace` cette configuration à l’aide de la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="bf7b1-251">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="bf7b1-252">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf7b1-252">See also</span></span>

- [<span data-ttu-id="bf7b1-253">Fournisseurs d’événements connus de .NET</span><span class="sxs-lookup"><span data-stu-id="bf7b1-253">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
