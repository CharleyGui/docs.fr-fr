---
title: dotnet-dump-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: e008dcfc734a8742c495ea32a7a149c9a55c54c6
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598112"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="41c23-103">Utilitaire de collecte et d’analyse des vidages (dotnet-dump)</span><span class="sxs-lookup"><span data-stu-id="41c23-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="41c23-104">**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="41c23-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="41c23-105">`dotnet-dump` n’est pas pris en charge sur macOS.</span><span class="sxs-lookup"><span data-stu-id="41c23-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="install-dotnet-dump"></a><span data-ttu-id="41c23-106">Installer dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="41c23-106">Install dotnet-dump</span></span>

<span data-ttu-id="41c23-107">Pour installer la dernière version Release du `dotnet-dump` [package NuGet](https://www.nuget.org/packages/dotnet-dump), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="41c23-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="41c23-108">Synopsis</span><span class="sxs-lookup"><span data-stu-id="41c23-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="41c23-109">Description</span><span class="sxs-lookup"><span data-stu-id="41c23-109">Description</span></span>

<span data-ttu-id="41c23-110">L' `dotnet-dump` outil Global est un moyen de collecter et d’analyser les vidages Windows et Linux sans que le débogueur natif ne soit impliqué `lldb` sur Linux.</span><span class="sxs-lookup"><span data-stu-id="41c23-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="41c23-111">Cet outil est important sur les plateformes telles que Alpine Linux où un travail complet `lldb` n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="41c23-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="41c23-112">L' `dotnet-dump` outil vous permet d’exécuter des commandes SOS pour analyser les incidents et le garbage collector (GC), mais il ne s’agit pas d’un débogueur natif, de sorte que l’affichage des frames de pile natifs n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="41c23-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="41c23-113">Options</span><span class="sxs-lookup"><span data-stu-id="41c23-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="41c23-114">Affiche la version de l’utilitaire dotnet-dump.</span><span class="sxs-lookup"><span data-stu-id="41c23-114">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="41c23-115">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="41c23-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="41c23-116">Commandes</span><span class="sxs-lookup"><span data-stu-id="41c23-116">Commands</span></span>

| <span data-ttu-id="41c23-117">Commande</span><span class="sxs-lookup"><span data-stu-id="41c23-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="41c23-118">dotnet-vider la collecte</span><span class="sxs-lookup"><span data-stu-id="41c23-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="41c23-119">dotnet-vider l’analyse</span><span class="sxs-lookup"><span data-stu-id="41c23-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="41c23-120">dotnet-vider la collecte</span><span class="sxs-lookup"><span data-stu-id="41c23-120">dotnet-dump collect</span></span>

<span data-ttu-id="41c23-121">Capture un vidage à partir d’un processus.</span><span class="sxs-lookup"><span data-stu-id="41c23-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="41c23-122">Synopsis</span><span class="sxs-lookup"><span data-stu-id="41c23-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="41c23-123">Options</span><span class="sxs-lookup"><span data-stu-id="41c23-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="41c23-124">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="41c23-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="41c23-125">Spécifie le numéro d’identification du processus à partir duquel une image mémoire doit être collectée.</span><span class="sxs-lookup"><span data-stu-id="41c23-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="41c23-126">Spécifie le type de vidage, qui détermine les types d’informations collectées à partir du processus.</span><span class="sxs-lookup"><span data-stu-id="41c23-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="41c23-127">Il existe trois types :</span><span class="sxs-lookup"><span data-stu-id="41c23-127">There are three types:</span></span>

  - <span data-ttu-id="41c23-128">`Full` -Le plus grand vidage contenant la mémoire, y compris les images de module.</span><span class="sxs-lookup"><span data-stu-id="41c23-128">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="41c23-129">`Heap` -Un vidage volumineux et relativement complet contenant des listes de modules, des listes de threads, toutes les piles, des informations sur les exceptions, des informations de gestion et toute la mémoire sauf pour les images mappées.</span><span class="sxs-lookup"><span data-stu-id="41c23-129">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="41c23-130">`Mini` -Un petit dump contenant des listes de modules, des listes de threads, des informations sur les exceptions et toutes les piles.</span><span class="sxs-lookup"><span data-stu-id="41c23-130">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="41c23-131">S’il n’est pas spécifié, `Full` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="41c23-131">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="41c23-132">Chemin d’accès complet et nom du fichier dans lequel le dump collecté doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="41c23-132">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="41c23-133">S’il n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="41c23-133">If not specified:</span></span>

  - <span data-ttu-id="41c23-134">La valeur par défaut est *. \ dump_YYYYMMDD_HHMMSS. dmp* sur Windows.</span><span class="sxs-lookup"><span data-stu-id="41c23-134">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="41c23-135">La valeur par défaut est *./core_YYYYMMDD_HHMMSS* sur Linux.</span><span class="sxs-lookup"><span data-stu-id="41c23-135">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="41c23-136">AAAAMMJJ correspond à année/mois/jour et HHMMSS à heure/minute/seconde.</span><span class="sxs-lookup"><span data-stu-id="41c23-136">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="41c23-137">Active la journalisation des diagnostics de collection de vidages.</span><span class="sxs-lookup"><span data-stu-id="41c23-137">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="41c23-138">dotnet-vider l’analyse</span><span class="sxs-lookup"><span data-stu-id="41c23-138">dotnet-dump analyze</span></span>

<span data-ttu-id="41c23-139">Démarre un interpréteur de commandes interactif pour explorer un vidage.</span><span class="sxs-lookup"><span data-stu-id="41c23-139">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="41c23-140">Le shell accepte différentes [commandes SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="41c23-140">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="41c23-141">Synopsis</span><span class="sxs-lookup"><span data-stu-id="41c23-141">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="41c23-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="41c23-142">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="41c23-143">Spécifie le chemin d’accès au fichier de vidage à analyser.</span><span class="sxs-lookup"><span data-stu-id="41c23-143">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="41c23-144">Options</span><span class="sxs-lookup"><span data-stu-id="41c23-144">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="41c23-145">Spécifie la [commande](#analyze-sos-commands) à exécuter dans le shell au démarrage.</span><span class="sxs-lookup"><span data-stu-id="41c23-145">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="41c23-146">Analyser les commandes SOS</span><span class="sxs-lookup"><span data-stu-id="41c23-146">Analyze SOS commands</span></span>

| <span data-ttu-id="41c23-147">Commande</span><span class="sxs-lookup"><span data-stu-id="41c23-147">Command</span></span>                             | <span data-ttu-id="41c23-148">Fonction</span><span class="sxs-lookup"><span data-stu-id="41c23-148">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="41c23-149">Affiche toutes les commandes disponibles</span><span class="sxs-lookup"><span data-stu-id="41c23-149">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="41c23-150">Affiche la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-150">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="41c23-151">Quitte le mode interactif.</span><span class="sxs-lookup"><span data-stu-id="41c23-151">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="41c23-152">Fournit uniquement une trace de la pile du code managé.</span><span class="sxs-lookup"><span data-stu-id="41c23-152">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="41c23-153">Répertorie les threads managés qui exécutent.</span><span class="sxs-lookup"><span data-stu-id="41c23-153">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="41c23-154">Affiche des informations sur les machines à États asynchrones sur le tas récupéré par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="41c23-154">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="41c23-155">Affiche des détails sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="41c23-155">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="41c23-156">Affiche des informations sur une structure de classe EE à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-156">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="41c23-157">Affiche des informations sur un délégué.</span><span class="sxs-lookup"><span data-stu-id="41c23-157">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="41c23-158">Affiche des informations sur tous les AppDomains et tous les assemblys dans les domaines.</span><span class="sxs-lookup"><span data-stu-id="41c23-158">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="41c23-159">Affiche des informations sur le tas récupéré par le garbage collector et des statistiques de collection concernant les objets.</span><span class="sxs-lookup"><span data-stu-id="41c23-159">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="41c23-160">Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée.</span><span class="sxs-lookup"><span data-stu-id="41c23-160">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="41c23-161">Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="41c23-161">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="41c23-162">Affiche des informations sur une structure MethodDesc à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-162">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="41c23-163">Affiche des informations sur une structure de module EE à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-163">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="41c23-164">Affiche des informations sur une table de méthodes à l'adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-164">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="41c23-165">Affiche des informations sur un objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-165">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="41c23-166">Affiche tous les objets managés recherchés dans les limites de la pile actuelle.</span><span class="sxs-lookup"><span data-stu-id="41c23-166">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="41c23-167">Affiche des informations sur la mémoire de processus consommée par les structures de données de Runtime internes.</span><span class="sxs-lookup"><span data-stu-id="41c23-167">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="41c23-168">Affiche tous les objets enregistrés pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="41c23-168">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="41c23-169">Affiche des informations sur les références (ou racines) à un objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-169">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="41c23-170">Affiche l’emplacement dans le tas GC de l’argument passé.</span><span class="sxs-lookup"><span data-stu-id="41c23-170">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="41c23-171">Affiche la structure MethodDesc à l’adresse spécifiée dans le code JIT.</span><span class="sxs-lookup"><span data-stu-id="41c23-171">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="41c23-172">Libère toutes les ressources utilisées par la famille de commandes `hist*`.</span><span class="sxs-lookup"><span data-stu-id="41c23-172">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="41c23-173">Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="41c23-173">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="41c23-174">Affiche les réadressages du journal de stress garbage collection liés à `<arguments>` .</span><span class="sxs-lookup"><span data-stu-id="41c23-174">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="41c23-175">Affiche toutes les entrées de journal qui référencent un objet à l'adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-175">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="41c23-176">Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.</span><span class="sxs-lookup"><span data-stu-id="41c23-176">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="41c23-177">Affiche les modules natifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="41c23-177">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="41c23-178">Affiche la structure MethodTable et la structure EEClass pour le `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="41c23-178">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="41c23-179">Affiche tout objet dérivé de la classe d’exception à l’adresse `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="41c23-179">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="41c23-180">Active la prise en charge du serveur de symboles</span><span class="sxs-lookup"><span data-stu-id="41c23-180">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="41c23-181">Affiche les informations sur le support SyncBlock.</span><span class="sxs-lookup"><span data-stu-id="41c23-181">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="41c23-182">Définit ou affiche l’ID de thread actuel pour les commandes SOS.</span><span class="sxs-lookup"><span data-stu-id="41c23-182">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="41c23-183">Utilisation de `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="41c23-183">Using `dotnet-dump`</span></span>

<span data-ttu-id="41c23-184">La première étape consiste à collecter un vidage.</span><span class="sxs-lookup"><span data-stu-id="41c23-184">The first step is to collect a dump.</span></span> <span data-ttu-id="41c23-185">Cette étape peut être ignorée si un vidage de base a déjà été généré.</span><span class="sxs-lookup"><span data-stu-id="41c23-185">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="41c23-186">Le système d’exploitation ou la fonctionnalité intégrée de création de [dump](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) de .net Core Runtime peuvent créer des vidages de noyau.</span><span class="sxs-lookup"><span data-stu-id="41c23-186">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="41c23-187">À présent, analysez le vidage de base avec la `analyze` commande :</span><span class="sxs-lookup"><span data-stu-id="41c23-187">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="41c23-188">Cette action affiche une session interactive qui accepte des commandes comme :</span><span class="sxs-lookup"><span data-stu-id="41c23-188">This action brings up an interactive session that accepts commands like:</span></span>

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

<span data-ttu-id="41c23-189">Pour voir une exception non gérée qui a interrompu votre application :</span><span class="sxs-lookup"><span data-stu-id="41c23-189">To see an unhandled exception that killed your app:</span></span>

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

## <a name="special-instructions-for-docker"></a><span data-ttu-id="41c23-190">Instructions spéciales pour l’ancrage</span><span class="sxs-lookup"><span data-stu-id="41c23-190">Special instructions for Docker</span></span>

<span data-ttu-id="41c23-191">Si vous exécutez dans le cadre de l’arrimeur, la collection de vidages requiert des `SYS_PTRACE` fonctionnalités ( `--cap-add=SYS_PTRACE` ou `--privileged` ).</span><span class="sxs-lookup"><span data-stu-id="41c23-191">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="41c23-192">Sur les images de la station d’accueil Linux Microsoft .NET Core SDK, certaines `dotnet-dump` commandes peuvent lever l’exception suivante :</span><span class="sxs-lookup"><span data-stu-id="41c23-192">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="41c23-193">Exception non gérée : System.DllNotFoundException : impossible de charger la bibliothèque partagée « libdl.so » ou l’une de ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="41c23-193">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="41c23-194">Pour contourner ce problème, installez le package « libc6-dev ».</span><span class="sxs-lookup"><span data-stu-id="41c23-194">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="41c23-195">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41c23-195">See also</span></span>

- [<span data-ttu-id="41c23-196">Blog sur la collecte et l’analyse des vidages de mémoire</span><span class="sxs-lookup"><span data-stu-id="41c23-196">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="41c23-197">Outil d’analyse de tas (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="41c23-197">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
