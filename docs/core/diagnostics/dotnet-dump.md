---
title: dotnet-dump - .NET Core
description: Installation et utilisation de l’outil de ligne de commande dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: c78ddb6447021f61f2452c075733b7d33e051ca0
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888200"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="b9b03-103">Service de collecte`dotnet-dump`et d’analyse des décharges ( )</span><span class="sxs-lookup"><span data-stu-id="b9b03-103">Dump collection and analysis utility (`dotnet-dump`)</span></span>

<span data-ttu-id="b9b03-104">**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="b9b03-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="b9b03-105">`dotnet-dump`n’est pas pris en charge sur macOS.</span><span class="sxs-lookup"><span data-stu-id="b9b03-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="installing-dotnet-dump"></a><span data-ttu-id="b9b03-106">Installation de `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="b9b03-106">Installing `dotnet-dump`</span></span>

<span data-ttu-id="b9b03-107">Pour installer la dernière `dotnet-dump` version du [paquet NuGet,](https://www.nuget.org/packages/dotnet-dump)utilisez la commande [d’installation d’outils dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="b9b03-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="b9b03-108">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b9b03-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="b9b03-109">Description</span><span class="sxs-lookup"><span data-stu-id="b9b03-109">Description</span></span>

<span data-ttu-id="b9b03-110">L’outil `dotnet-dump` global est un moyen de collecter et d’analyser les `lldb` décharges Windows et Linux sans aucun débbugger indigène impliqué comme sur Linux.</span><span class="sxs-lookup"><span data-stu-id="b9b03-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="b9b03-111">Cet outil est important sur des plates-formes comme Alpine Linux où un travail `lldb` complet n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="b9b03-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="b9b03-112">L’outil `dotnet-dump` vous permet d’exécuter des commandes SOS pour analyser les plantages et le collecteur d’ordures (GC), mais ce n’est pas un débbuggeur indigène de sorte que les choses comme l’affichage des cadres de pile indigène ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b9b03-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="b9b03-113">Options</span><span class="sxs-lookup"><span data-stu-id="b9b03-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="b9b03-114">Affiche la version de l’utilitaire dotnet-dump.</span><span class="sxs-lookup"><span data-stu-id="b9b03-114">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b9b03-115">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b9b03-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="b9b03-116">Commandes</span><span class="sxs-lookup"><span data-stu-id="b9b03-116">Commands</span></span>

| <span data-ttu-id="b9b03-117">Commande</span><span class="sxs-lookup"><span data-stu-id="b9b03-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="b9b03-118">dotnet-dump recueillir</span><span class="sxs-lookup"><span data-stu-id="b9b03-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="b9b03-119">Analyse de dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="b9b03-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="b9b03-120">dotnet-dump recueillir</span><span class="sxs-lookup"><span data-stu-id="b9b03-120">dotnet-dump collect</span></span>

<span data-ttu-id="b9b03-121">Capture une décharge à partir d’un processus.</span><span class="sxs-lookup"><span data-stu-id="b9b03-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="b9b03-122">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b9b03-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="b9b03-123">Options</span><span class="sxs-lookup"><span data-stu-id="b9b03-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="b9b03-124">Affiche l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b9b03-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="b9b03-125">Spécifie le numéro d’identification du processus pour recueillir un dépotoir de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b9b03-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="b9b03-126">Spécifie le type de décharge, qui détermine les types d’informations qui sont recueillies à partir du processus.</span><span class="sxs-lookup"><span data-stu-id="b9b03-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="b9b03-127">Il en existe deux types :</span><span class="sxs-lookup"><span data-stu-id="b9b03-127">There are two types:</span></span>

  - <span data-ttu-id="b9b03-128">`Heap`- Un dépotoir grand et relativement complet contenant des listes de modules, des listes de threads, toutes les piles, des informations d’exception, des informations de poignée, et toute la mémoire, sauf pour les images cartographiées.</span><span class="sxs-lookup"><span data-stu-id="b9b03-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="b9b03-129">`Mini`- Un petit dépotoir contenant des listes de modules, des listes de threads, des informations d’exception et toutes les piles.</span><span class="sxs-lookup"><span data-stu-id="b9b03-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="b9b03-130">S’il `Heap` n’est pas spécifié, est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="b9b03-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="b9b03-131">Le chemin complet et le nom de fichier où le dépotoir collecté doit être écrit.</span><span class="sxs-lookup"><span data-stu-id="b9b03-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="b9b03-132">S’il n’est pas spécifié :</span><span class="sxs-lookup"><span data-stu-id="b9b03-132">If not specified:</span></span>

  - <span data-ttu-id="b9b03-133">Par défaut à *.dump_YYYYMMDD_HHMMSS.dmp* sur Windows.</span><span class="sxs-lookup"><span data-stu-id="b9b03-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="b9b03-134">Par défaut à *./core_YYYYMMDD_HHMMSS* sur Linux.</span><span class="sxs-lookup"><span data-stu-id="b9b03-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="b9b03-135">YYYYMMDD est année/mois/jour et HHMMSS est Heure/Minute/Second.</span><span class="sxs-lookup"><span data-stu-id="b9b03-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="b9b03-136">Permet l’enregistrement diagnostique de la collecte des décharges.</span><span class="sxs-lookup"><span data-stu-id="b9b03-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="b9b03-137">Analyse de dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="b9b03-137">dotnet-dump analyze</span></span>

<span data-ttu-id="b9b03-138">Démarre une coquille interactive pour explorer un dépotoir.</span><span class="sxs-lookup"><span data-stu-id="b9b03-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="b9b03-139">La coquille accepte diverses [commandes SOS](#analyze-sos-commands).</span><span class="sxs-lookup"><span data-stu-id="b9b03-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="b9b03-140">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b9b03-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="b9b03-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="b9b03-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="b9b03-142">Spécifie le chemin vers le fichier de décharge à analyser.</span><span class="sxs-lookup"><span data-stu-id="b9b03-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="b9b03-143">Options</span><span class="sxs-lookup"><span data-stu-id="b9b03-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="b9b03-144">Spécifie la [commande](#analyze-sos-commands) de courir dans la coquille au départ.</span><span class="sxs-lookup"><span data-stu-id="b9b03-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="b9b03-145">Analyser les commandes SOS</span><span class="sxs-lookup"><span data-stu-id="b9b03-145">Analyze SOS commands</span></span>

| <span data-ttu-id="b9b03-146">Commande</span><span class="sxs-lookup"><span data-stu-id="b9b03-146">Command</span></span>                             | <span data-ttu-id="b9b03-147">Fonction</span><span class="sxs-lookup"><span data-stu-id="b9b03-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="b9b03-148">Affiche toutes les commandes disponibles</span><span class="sxs-lookup"><span data-stu-id="b9b03-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="b9b03-149">Affiche la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="b9b03-150">Sortie en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="b9b03-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="b9b03-151">Fournit uniquement une trace de la pile du code managé.</span><span class="sxs-lookup"><span data-stu-id="b9b03-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="b9b03-152">Répertorie les threads gérés en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b9b03-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="b9b03-153">Affiche des informations sur les machines d’état async sur le tas d’ordures collectés.</span><span class="sxs-lookup"><span data-stu-id="b9b03-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="b9b03-154">Affiche les détails d’une assemblée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="b9b03-155">Affiche des informations sur une structure de classe EE à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="b9b03-156">Affiche des informations sur un délégué.</span><span class="sxs-lookup"><span data-stu-id="b9b03-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="b9b03-157">Affiche toutes les informations sur toutes les AppDomains et tous les assemblages dans les domaines.</span><span class="sxs-lookup"><span data-stu-id="b9b03-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="b9b03-158">Affiche des informations sur le tas d’ordures et les statistiques de collecte sur les objets.</span><span class="sxs-lookup"><span data-stu-id="b9b03-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="b9b03-159">Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="b9b03-160">Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="b9b03-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="b9b03-161">Affiche des informations sur une structure MethodDesc à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="b9b03-162">Affiche des informations sur une structure de module EE à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="b9b03-163">Affiche des informations sur une table de méthodes à l'adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="b9b03-164">Affiche des informations sur un objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="b9b03-165">Affiche tous les objets managés recherchés dans les limites de la pile actuelle.</span><span class="sxs-lookup"><span data-stu-id="b9b03-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="b9b03-166">Affiche des informations sur la mémoire de processus consommée par les structures internes de données en temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="b9b03-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="b9b03-167">Affiche tous les objets enregistrés pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="b9b03-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="b9b03-168">Affiche des informations sur les références (ou les racines) à un objet à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="b9b03-169">Affiche l’emplacement dans le tas GC de l’argument passé.</span><span class="sxs-lookup"><span data-stu-id="b9b03-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="b9b03-170">Affiche la structure MethodDesc à l’adresse spécifiée dans le code JIT.</span><span class="sxs-lookup"><span data-stu-id="b9b03-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="b9b03-171">Libère toutes les ressources utilisées par la famille de commandes `hist*`.</span><span class="sxs-lookup"><span data-stu-id="b9b03-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="b9b03-172">Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="b9b03-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="b9b03-173">Affiche les relocalisations de journaux `<arguments>`de recouvrement de stress de collecte d’ordures liées à .</span><span class="sxs-lookup"><span data-stu-id="b9b03-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="b9b03-174">Affiche toutes les entrées de journal qui référencent un objet à l'adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="b9b03-175">Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b9b03-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="b9b03-176">Affiche les modules natifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b9b03-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="b9b03-177">Affiche la structure MethodTable et la `<argument>`structure EEClass pour le .</span><span class="sxs-lookup"><span data-stu-id="b9b03-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="b9b03-178">Affiche tout objet dérivé de la `<argument>`classe Exception à l’adresse .</span><span class="sxs-lookup"><span data-stu-id="b9b03-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="b9b03-179">Permet le support serveur symbole</span><span class="sxs-lookup"><span data-stu-id="b9b03-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="b9b03-180">Affiche les informations du titulaire SyncBlock.</span><span class="sxs-lookup"><span data-stu-id="b9b03-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="b9b03-181">Définit ou affiche l’ID de thread actuel pour les commandes SOS.</span><span class="sxs-lookup"><span data-stu-id="b9b03-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="b9b03-182">Utilisation de `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="b9b03-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="b9b03-183">La première étape consiste à collecter un dépotoir.</span><span class="sxs-lookup"><span data-stu-id="b9b03-183">The first step is to collect a dump.</span></span> <span data-ttu-id="b9b03-184">Cette étape peut être ignorée si un décharge de base a déjà été généré.</span><span class="sxs-lookup"><span data-stu-id="b9b03-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="b9b03-185">Le système d’exploitation ou la fonction de génération de [décharges](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) intégrées du .NET Core peut créer chacun des décharges de base.</span><span class="sxs-lookup"><span data-stu-id="b9b03-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="b9b03-186">Maintenant, analysez le `analyze` déchargeur de base avec la commande :</span><span class="sxs-lookup"><span data-stu-id="b9b03-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="b9b03-187">Cette action évoque une session interactive qui accepte les commandes comme :</span><span class="sxs-lookup"><span data-stu-id="b9b03-187">This action brings up an interactive session that accepts commands like:</span></span>

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

<span data-ttu-id="b9b03-188">Pour voir une exception non gérée qui a tué votre application :</span><span class="sxs-lookup"><span data-stu-id="b9b03-188">To see an unhandled exception that killed your app:</span></span>

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

## <a name="special-instructions-for-docker"></a><span data-ttu-id="b9b03-189">Instructions spéciales pour Docker</span><span class="sxs-lookup"><span data-stu-id="b9b03-189">Special instructions for Docker</span></span>

<span data-ttu-id="b9b03-190">Si vous êtes en cours d’exécution`--cap-add=SYS_PTRACE` `--privileged`sous Docker, la collecte de décharge nécessite des `SYS_PTRACE` capacités ( ou ).</span><span class="sxs-lookup"><span data-stu-id="b9b03-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="b9b03-191">Sur microsoft .NET Core SDK `dotnet-dump` Linux Docker images, certaines commandes peuvent jeter l’exception suivante:</span><span class="sxs-lookup"><span data-stu-id="b9b03-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="b9b03-192">Exception non gérée : System.DllNotFoundException: Incapable de charger la bibliothèque partagée 'libdl.so' ou l’une de ses dépendances' exception.</span><span class="sxs-lookup"><span data-stu-id="b9b03-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="b9b03-193">Pour contourner ce problème, installez le paquet "libc6-dev".</span><span class="sxs-lookup"><span data-stu-id="b9b03-193">To work around this problem, install the "libc6-dev" package.</span></span>
