---
title: outil de diagnostic dotnet-dump-.NET CLI
description: Découvrez comment installer et utiliser l’outil CLI dotnet-dump pour collecter et analyser les vidages Windows et Linux sans débogueur natif.
ms.date: 11/17/2020
ms.openlocfilehash: 84b3796f4ee92880e6d432df606a6addfd2471b0
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189802"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="c9817-103">Utilitaire de collecte et d’analyse des vidages (dotnet-dump)</span><span class="sxs-lookup"><span data-stu-id="c9817-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="c9817-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="c9817-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="c9817-105">`dotnet-dump` pour macOS est pris en charge uniquement avec .NET 5,0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="c9817-105">`dotnet-dump` for macOS is only supported with .NET 5.0 and later versions.</span></span>

## <a name="install"></a><span data-ttu-id="c9817-106">Installer</span><span class="sxs-lookup"><span data-stu-id="c9817-106">Install</span></span>

<span data-ttu-id="c9817-107">Il existe deux façons de télécharger et d’installer `dotnet-dump` :</span><span class="sxs-lookup"><span data-stu-id="c9817-107">There are two ways to download and install `dotnet-dump`:</span></span>

- <span data-ttu-id="c9817-108">**outil Global dotnet :**</span><span class="sxs-lookup"><span data-stu-id="c9817-108">**dotnet global tool:**</span></span>

  <span data-ttu-id="c9817-109">Pour installer la dernière version Release du `dotnet-dump` [package NuGet](https://www.nuget.org/packages/dotnet-dump), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="c9817-109">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- <span data-ttu-id="c9817-110">**Téléchargement direct :**</span><span class="sxs-lookup"><span data-stu-id="c9817-110">**Direct download:**</span></span>

  <span data-ttu-id="c9817-111">Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :</span><span class="sxs-lookup"><span data-stu-id="c9817-111">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="c9817-112">Système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="c9817-112">OS</span></span>  | <span data-ttu-id="c9817-113">Plateforme</span><span class="sxs-lookup"><span data-stu-id="c9817-113">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="c9817-114">Windows</span><span class="sxs-lookup"><span data-stu-id="c9817-114">Windows</span></span> | <span data-ttu-id="c9817-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [ARM](https://aka.ms/dotnet-dump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-dump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="c9817-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span></span> |
  | <span data-ttu-id="c9817-116">macOS</span><span class="sxs-lookup"><span data-stu-id="c9817-116">macOS</span></span>   | [<span data-ttu-id="c9817-117">x64</span><span class="sxs-lookup"><span data-stu-id="c9817-117">x64</span></span>](https://aka.ms/dotnet-dump/osx-x64) |
  | <span data-ttu-id="c9817-118">Linux</span><span class="sxs-lookup"><span data-stu-id="c9817-118">Linux</span></span>   | <span data-ttu-id="c9817-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [ARM](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="c9817-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="c9817-120">Pour utiliser `dotnet-dump` sur une application x86, vous avez besoin d’une version x86 correspondante de l’outil.</span><span class="sxs-lookup"><span data-stu-id="c9817-120">To use `dotnet-dump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c9817-121">Synopsis</span><span class="sxs-lookup"><span data-stu-id="c9817-121">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="c9817-122">Description</span><span class="sxs-lookup"><span data-stu-id="c9817-122">Description</span></span>

<span data-ttu-id="c9817-123">L' `dotnet-dump` outil Global est un moyen de collecter et d’analyser les vidages Windows et Linux sans que le débogueur natif ne soit impliqué `lldb` sur Linux.</span><span class="sxs-lookup"><span data-stu-id="c9817-123">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="c9817-124">Cet outil est important sur les plateformes telles que Alpine Linux où un travail complet `lldb` n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="c9817-124">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="c9817-125">L' `dotnet-dump` outil vous permet d’exécuter des commandes SOS pour analyser les incidents et le garbage collector (GC), mais il ne s’agit pas d’un débogueur natif, de sorte que l’affichage des frames de pile natifs n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c9817-125">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="c9817-126">Options</span><span class="sxs-lookup"><span data-stu-id="c9817-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="c9817-127">Affiche la version de l’utilitaire dotnet-dump.</span><span class="sxs-lookup"><span data-stu-id="c9817-127">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c9817-128">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c9817-128">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="c9817-129">Commandes</span><span class="sxs-lookup"><span data-stu-id="c9817-129">Commands</span></span>

| <span data-ttu-id="c9817-130">Commande</span><span class="sxs-lookup"><span data-stu-id="c9817-130">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="c9817-131">dotnet-vider la collecte</span><span class="sxs-lookup"><span data-stu-id="c9817-131">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="c9817-132">dotnet-vider l’analyse</span><span class="sxs-lookup"><span data-stu-id="c9817-132">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="c9817-133">dotnet-vider la collecte</span><span class="sxs-lookup"><span data-stu-id="c9817-133">dotnet-dump collect</span></span>

<span data-ttu-id="c9817-134">Capture un vidage à partir d’un processus.</span><span class="sxs-lookup"><span data-stu-id="c9817-134">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c9817-135">Synopsis</span><span class="sxs-lookup"><span data-stu-id="c9817-135">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="c9817-136">Options</span><span class="sxs-lookup"><span data-stu-id="c9817-136">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="c9817-137">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c9817-137">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="c9817-138">Spécifie le numéro d’identification du processus à partir duquel un vidage doit être collecté.</span><span class="sxs-lookup"><span data-stu-id="c9817-138">Specifies the process ID number to collect a dump from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="c9817-139">Spécifie le nom du processus à partir duquel un vidage doit être collecté.</span><span class="sxs-lookup"><span data-stu-id="c9817-139">Specifies the name of the process to collect a dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="c9817-140">Spécifie le type de vidage, qui détermine les types d’informations collectées à partir du processus.</span><span class="sxs-lookup"><span data-stu-id="c9817-140">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="c9817-141">Il existe trois types :</span><span class="sxs-lookup"><span data-stu-id="c9817-141">There are three types:</span></span>

  - <span data-ttu-id="c9817-142">`Full` -Le plus grand vidage contenant la mémoire, y compris les images de module.</span><span class="sxs-lookup"><span data-stu-id="c9817-142">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="c9817-143">`Heap` -Un vidage volumineux et relativement complet contenant des listes de modules, des listes de threads, toutes les piles, des informations sur les exceptions, des informations de gestion et toute la mémoire sauf pour les images mappées.</span><span class="sxs-lookup"><span data-stu-id="c9817-143">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="c9817-144">`Mini` -Un petit dump contenant des listes de modules, des listes de threads, des informations sur les exceptions et toutes les piles.</span><span class="sxs-lookup"><span data-stu-id="c9817-144">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="c9817-145">S’il n’est pas spécifié, `Full` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c9817-145">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="c9817-146">Chemin d’accès complet et nom du fichier dans lequel le dump collecté doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="c9817-146">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="c9817-147">S’il n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="c9817-147">If not specified:</span></span>

  - <span data-ttu-id="c9817-148">La valeur par défaut est *. \ dump_YYYYMMDD_HHMMSS. dmp* sur Windows.</span><span class="sxs-lookup"><span data-stu-id="c9817-148">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="c9817-149">La valeur par défaut est *./core_YYYYMMDD_HHMMSS* sur Linux.</span><span class="sxs-lookup"><span data-stu-id="c9817-149">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="c9817-150">AAAAMMJJ correspond à année/mois/jour et HHMMSS à heure/minute/seconde.</span><span class="sxs-lookup"><span data-stu-id="c9817-150">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="c9817-151">Active la journalisation des diagnostics de collection de vidages.</span><span class="sxs-lookup"><span data-stu-id="c9817-151">Enables dump collection diagnostic logging.</span></span>

> [!NOTE]
> <span data-ttu-id="c9817-152">Sur Linux et macOS, cette commande attend l’application cible et `dotnet-dump` partager la même variable d' `TMPDIR` environnement.</span><span class="sxs-lookup"><span data-stu-id="c9817-152">On Linux and macOS, this command expects the target application and `dotnet-dump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="c9817-153">Dans le cas contraire, la commande expire.</span><span class="sxs-lookup"><span data-stu-id="c9817-153">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="c9817-154">Pour collecter un vidage à l’aide de `dotnet-dump` , il doit être exécuté en tant que même utilisateur que l’utilisateur qui exécute le processus cible ou en tant que racine.</span><span class="sxs-lookup"><span data-stu-id="c9817-154">To collect a dump using `dotnet-dump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="c9817-155">Dans le cas contraire, l’outil ne parviendra pas à établir une connexion avec le processus cible.</span><span class="sxs-lookup"><span data-stu-id="c9817-155">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="c9817-156">dotnet-vider l’analyse</span><span class="sxs-lookup"><span data-stu-id="c9817-156">dotnet-dump analyze</span></span>

<span data-ttu-id="c9817-157">Démarre un interpréteur de commandes interactif pour explorer un vidage.</span><span class="sxs-lookup"><span data-stu-id="c9817-157">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="c9817-158">Le shell accepte différentes [commandes SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="c9817-158">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="c9817-159">Synopsis</span><span class="sxs-lookup"><span data-stu-id="c9817-159">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="c9817-160">Arguments</span><span class="sxs-lookup"><span data-stu-id="c9817-160">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="c9817-161">Spécifie le chemin d’accès au fichier de vidage à analyser.</span><span class="sxs-lookup"><span data-stu-id="c9817-161">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="c9817-162">Options</span><span class="sxs-lookup"><span data-stu-id="c9817-162">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="c9817-163">Spécifie la [commande](#analyze-sos-commands) à exécuter dans le shell au démarrage.</span><span class="sxs-lookup"><span data-stu-id="c9817-163">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="c9817-164">Analyser les commandes SOS</span><span class="sxs-lookup"><span data-stu-id="c9817-164">Analyze SOS commands</span></span>

| <span data-ttu-id="c9817-165">Commande</span><span class="sxs-lookup"><span data-stu-id="c9817-165">Command</span></span>                             | <span data-ttu-id="c9817-166">Fonction</span><span class="sxs-lookup"><span data-stu-id="c9817-166">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="c9817-167">Affiche toutes les commandes disponibles</span><span class="sxs-lookup"><span data-stu-id="c9817-167">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="c9817-168">Affiche la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-168">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="c9817-169">Quitte le mode interactif.</span><span class="sxs-lookup"><span data-stu-id="c9817-169">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="c9817-170">Fournit uniquement une trace de la pile du code managé.</span><span class="sxs-lookup"><span data-stu-id="c9817-170">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="c9817-171">Répertorie les threads managés qui exécutent.</span><span class="sxs-lookup"><span data-stu-id="c9817-171">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="c9817-172">Affiche des informations sur les machines à États asynchrones sur le tas récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="c9817-172">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="c9817-173">Affiche des détails sur l’assembly à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-173">Displays details about the assembly at the specified address.</span></span>                                 |
| `dumpclass <arguments>`             | <span data-ttu-id="c9817-174">Affiche des informations sur la `EEClass` structure à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-174">Displays information about the `EEClass` structure at the specified address.</span></span>                  |
| `dumpdelegate <arguments>`          | <span data-ttu-id="c9817-175">Affiche des informations sur le délégué à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-175">Displays information about the delegate at the specified address.</span></span>                             |
| `dumpdomain <arguments>`            | <span data-ttu-id="c9817-176">Affiche des informations sur tous les AppDomains et tous les assemblys au sein du domaine spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9817-176">Displays information all the AppDomains and all assemblies within the specified domain.</span></span>       |
| `dumpheap <arguments>`              | <span data-ttu-id="c9817-177">Affiche des informations sur le tas récupéré par le garbage collector et des statistiques de collection concernant les objets.</span><span class="sxs-lookup"><span data-stu-id="c9817-177">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="c9817-178">Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée.</span><span class="sxs-lookup"><span data-stu-id="c9817-178">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="c9817-179">Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="c9817-179">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="c9817-180">Affiche des informations sur la `MethodDesc` structure à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-180">Displays information about the `MethodDesc` structure at the specified address.</span></span>               |
| `dumpmodule <arguments>`            | <span data-ttu-id="c9817-181">Affiche des informations sur le module à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-181">Displays information about the module at the specified address.</span></span>                               |
| `dumpmt <arguments>`                | <span data-ttu-id="c9817-182">Affiche des informations sur le `MethodTable` à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-182">Displays information about the `MethodTable` at the specified address.</span></span>                        |
| `dumpobj <arguments>`               | <span data-ttu-id="c9817-183">Affiche des informations sur l’objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-183">Displays info about the object at the specified address.</span></span>                                      |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="c9817-184">Affiche tous les objets managés recherchés dans les limites de la pile actuelle.</span><span class="sxs-lookup"><span data-stu-id="c9817-184">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="c9817-185">Affiche des informations sur la mémoire de processus consommée par les structures de données de Runtime internes.</span><span class="sxs-lookup"><span data-stu-id="c9817-185">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="c9817-186">Affiche tous les objets enregistrés pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="c9817-186">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="c9817-187">Affiche des informations sur les références (ou racines) à l’objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-187">Displays info about references (or roots) to the object at the specified address.</span></span>             |
| `gcwhere <arguments>`               | <span data-ttu-id="c9817-188">Affiche l’emplacement dans le tas GC de l’argument passé.</span><span class="sxs-lookup"><span data-stu-id="c9817-188">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="c9817-189">Affiche la `MethodDesc` structure à l’adresse spécifiée dans le code JIT.</span><span class="sxs-lookup"><span data-stu-id="c9817-189">Displays the `MethodDesc` structure at the specified address in JIT code.</span></span>                     |
| `histclear <arguments>`             | <span data-ttu-id="c9817-190">Libère toutes les ressources utilisées par la famille de commandes `hist*`.</span><span class="sxs-lookup"><span data-stu-id="c9817-190">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="c9817-191">Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="c9817-191">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="c9817-192">Affiche les réadressages du journal de stress garbage collection liés à `<arguments>` .</span><span class="sxs-lookup"><span data-stu-id="c9817-192">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="c9817-193">Affiche toutes les entrées de journal qui référencent l’objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-193">Displays all the log entries that reference the object at the specified address.</span></span>              |
| `histroot <arguments>`              | <span data-ttu-id="c9817-194">Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c9817-194">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="c9817-195">Affiche les modules natifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="c9817-195">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="c9817-196">Affiche les `MethodTable` `EEClass` structures et pour le `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="c9817-196">Displays the `MethodTable` and `EEClass` structures for the `<argument>`.</span></span>                     |
| `pe|printexception <arguments>`     | <span data-ttu-id="c9817-197">Affiche tout objet dérivé de la <xref:System.Exception> classe pour `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="c9817-197">Displays any object derived from the <xref:System.Exception> class for the `<argument>`.</span></span>      |
| `setsymbolserver <arguments>`       | <span data-ttu-id="c9817-198">Active la prise en charge du serveur de symboles</span><span class="sxs-lookup"><span data-stu-id="c9817-198">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="c9817-199">Affiche les informations sur le support SyncBlock.</span><span class="sxs-lookup"><span data-stu-id="c9817-199">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="c9817-200">Définit ou affiche l’ID de thread actuel pour les commandes SOS.</span><span class="sxs-lookup"><span data-stu-id="c9817-200">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

> [!NOTE]
> <span data-ttu-id="c9817-201">Vous trouverez des informations supplémentaires dans l' [extension de débogage SOS pour .net](sos-debugging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="c9817-201">Additional details can be found in [SOS Debugging Extension for .NET](sos-debugging-extension.md).</span></span>

## <a name="using-dotnet-dump"></a><span data-ttu-id="c9817-202">Utilisation de `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="c9817-202">Using `dotnet-dump`</span></span>

<span data-ttu-id="c9817-203">La première étape consiste à collecter un vidage.</span><span class="sxs-lookup"><span data-stu-id="c9817-203">The first step is to collect a dump.</span></span> <span data-ttu-id="c9817-204">Cette étape peut être ignorée si un vidage de base a déjà été généré.</span><span class="sxs-lookup"><span data-stu-id="c9817-204">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="c9817-205">Le système d’exploitation ou la fonctionnalité intégrée de création de [dump](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) de .net Core Runtime peuvent créer des vidages de noyau.</span><span class="sxs-lookup"><span data-stu-id="c9817-205">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="c9817-206">À présent, analysez le vidage de base avec la `analyze` commande :</span><span class="sxs-lookup"><span data-stu-id="c9817-206">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="c9817-207">Cette action affiche une session interactive qui accepte des commandes comme :</span><span class="sxs-lookup"><span data-stu-id="c9817-207">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="c9817-208">Pour voir une exception non gérée qui a interrompu votre application :</span><span class="sxs-lookup"><span data-stu-id="c9817-208">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="c9817-209">Instructions spéciales pour l’ancrage</span><span class="sxs-lookup"><span data-stu-id="c9817-209">Special instructions for Docker</span></span>

<span data-ttu-id="c9817-210">Si vous exécutez dans le cadre de l’arrimeur, la collection de vidages requiert des `SYS_PTRACE` fonctionnalités ( `--cap-add=SYS_PTRACE` ou `--privileged` ).</span><span class="sxs-lookup"><span data-stu-id="c9817-210">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="c9817-211">Sur les images de la station d’accueil Linux Microsoft .NET Core SDK, certaines `dotnet-dump` commandes peuvent lever l’exception suivante :</span><span class="sxs-lookup"><span data-stu-id="c9817-211">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="c9817-212">Exception non gérée : System.DllNotFoundException : impossible de charger la bibliothèque partagée « libdl.so » ou l’une de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="c9817-212">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="c9817-213">Pour contourner ce problème, installez le package « libc6-dev ».</span><span class="sxs-lookup"><span data-stu-id="c9817-213">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9817-214">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9817-214">See also</span></span>

- [<span data-ttu-id="c9817-215">Blog sur la collecte et l’analyse des vidages de mémoire</span><span class="sxs-lookup"><span data-stu-id="c9817-215">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="c9817-216">Outil d’analyse de tas (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="c9817-216">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
