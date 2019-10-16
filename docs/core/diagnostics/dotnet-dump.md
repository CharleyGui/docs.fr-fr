---
title: dotnet-dump-.NET Core
description: Installation et utilisation de l’outil en ligne de commande dotnet-dump.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 7eba0cba28f0575be4b374b26e9aca26a70df603
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321595"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Utilitaire de collecte et d’analyse des vidages (`dotnet-dump`)

**Cet article s’applique à : ✓** .net Core 3,0 SDK et versions ultérieures

> [!NOTE]
> `dotnet-dump` n’est pas pris en charge sur macOS.

## <a name="installing-dotnet-dump"></a>Installation de `dotnet-dump`

Pour installer la dernière version Release du [package NuGet](https://www.nuget.org/packages/dotnet-dump)`dotnet-dump`, utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Résumé

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Description

L’outil Global `dotnet-dump` est un moyen de collecter et d’analyser les vidages Windows et Linux sans qu’un débogueur natif ne soit impliqué comme `lldb` sur Linux. Cet outil est important sur les plateformes telles que Alpine Linux où un @no__t entièrement opérationnel n’est pas disponible. L’outil `dotnet-dump` vous permet d’exécuter des commandes SOS pour analyser les incidents et le garbage collector (GC), mais il ne s’agit pas d’un débogueur natif, de sorte que l’affichage des frames de pile natifs n’est pas pris en charge.

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire dotnet-Counters.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                     |
| ------------------------------------------- |
| [dotnet-vider la collecte](#dotnet-dump-collect) |
| [dotnet-vider l’analyse](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-vider la collecte

Capture un vidage à partir d’un processus.

### <a name="synopsis"></a>Résumé

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Options

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

- **`-p|--process-id <PID>`**

  Spécifie le numéro d’identification du processus à partir duquel une image mémoire doit être collectée.

- **`--type <Heap|Mini>`**

  Spécifie le type passif, qui détermine les types d’informations collectées à partir du processus. Il existe deux types :

  - `Heap`-un vidage volumineux et relativement complet contenant des listes de modules, des listes de threads, toutes les piles, des informations sur les exceptions, des informations de gestion et toute la mémoire sauf pour les images mappées.
  - `Mini`-un petit dump contenant des listes de modules, des listes de threads, des informations sur les exceptions et toutes les piles.

  S’il n’est pas spécifié, `Heap` est la valeur par défaut.

- **`-o|--output <output_dump_path>`**

  Chemin d’accès complet et nom du fichier dans lequel le dump collecté doit être écrit.

  S’il n’est pas spécifié :

  - La valeur par défaut est *.\dump_YYYYMMDD_HHMMSS.dmp* sur Windows.
  - La valeur par défaut est *./core_YYYYMMDD_HHMMSS* sur Linux.

  AAAAMMJJ correspond à année/mois/jour et HHMMSS à heure/minute/seconde.

- **`--diag`**

  Active la journalisation des diagnostics de collection de vidages.

## <a name="dotnet-dump-analyze"></a>dotnet-vider l’analyse

Démarre un interpréteur de commandes interactif pour explorer un vidage. Le shell accepte différentes [commandes SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Résumé

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Arguments

- **`<dump_path>`**

  Spécifie le chemin d’accès au fichier de vidage à analyser.

### <a name="options"></a>Options

- **`-c|--command <debug_command>`**

  Spécifie la [commande](#analyze-sos-commands) à exécuter dans le shell au démarrage.

### <a name="analyze-sos-commands"></a>Analyser les commandes SOS

| Commande                             | Fonction                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Affiche toutes les commandes disponibles                                                               |
| `soshelp|help <command>`            | Affiche la commande spécifiée.                                                               |
| `exit|quit`                         | Quitte le mode interactif.                                                                       |
| `clrstack <arguments>`              | Fournit uniquement une trace de la pile du code managé.                                                  |
| `clrthreads <arguments>`            | Répertorie les threads managés qui exécutent.                                                            |
| `dumpasync <arguments>`             | Affiche des informations sur les machines à États asynchrones sur le tas récupéré par le garbage collector.                |
| `dumpassembly <arguments>`          | Affiche des détails sur un assembly.                                                           |
| `dumpclass <arguments>`             | Affiche des informations sur une structure de classe EE à l’adresse spécifiée.                     |
| `dumpdelegate <arguments>`          | Affiche des informations sur un délégué.                                                        |
| `dumpdomain <arguments>`            | Affiche des informations sur tous les AppDomains et tous les assemblys dans les domaines.                |
| `dumpheap <arguments>`              | Affiche des informations sur le tas récupéré par le garbage collector et des statistiques de collection concernant les objets.       |
| `dumpil <arguments>`                | Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée. |
| `dumplog <arguments>`               | Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié.                         |
| `dumpmd <arguments>`                | Affiche des informations sur une structure MethodDesc à l’adresse spécifiée.                   |
| `dumpmodule <arguments>`            | Affiche des informations sur une structure de module EE à l’adresse spécifiée.                    |
| `dumpmt <arguments>`                | Affiche des informations sur une table de méthodes à l'adresse spécifiée.                           |
| `dumpobj <arguments>`               | Affiche des informations sur un objet à l’adresse spécifiée.                                       |
| `dso|dumpstackobjects <arguments>`  | Affiche tous les objets managés recherchés dans les limites de la pile actuelle.                    |
| `eeheap <arguments>`                | Affiche des informations sur la mémoire de processus consommée par les structures de données de Runtime internes.              |
| `finalizequeue <arguments>`         | Affiche tous les objets enregistrés pour la finalisation.                                             |
| `gcroot <arguments>`                | Affiche des informations sur les références (ou racines) à un objet à l’adresse spécifiée.              |
| `gcwhere <arguments>`               | Affiche l’emplacement dans le tas GC de l’argument passé.                               |
| `ip2md <arguments>`                 | Affiche la structure MethodDesc à l’adresse spécifiée dans le code JIT.                       |
| `histclear <arguments>`             | Libère toutes les ressources utilisées par la famille de commandes `hist*`.                                |
| `histinit <arguments>`              | Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.                     |
| `histobj <arguments>`               | Affiche les réadressages du journal de stress garbage collection en rapport avec `<arguments>`.              |
| `histobjfind <arguments>`           | Affiche toutes les entrées de journal qui référencent un objet à l'adresse spécifiée.               |
| `histroot <arguments>`              | Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.        |
| `lm|modules`                        | Affiche les modules natifs dans le processus.                                                   |
| `name2ee <arguments>`               | Affiche la structure MethodTable et la structure EEClass pour le `<argument>`.                |
| `pe|printexception <arguments>`     | Affiche tout objet dérivé de la classe d’exception à l’adresse `<argument>`.             |
| `setsymbolserver <arguments>`       | Active la prise en charge du serveur de symboles                                                             |
| `syncblk <arguments>`               | Affiche les informations sur le support SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Définit ou affiche l’ID de thread actuel pour les commandes SOS.                                  |

## <a name="using-dotnet-dump"></a>Utilisation de `dotnet-dump`

La première étape consiste à collecter un vidage. Cette étape peut être ignorée si un vidage de base a déjà été généré. Le système d’exploitation ou la fonctionnalité intégrée de création de [dump](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/xplat-minidump-generation.md#configurationpolicy) de .net Core Runtime peuvent créer des vidages de noyau.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

À présent, analysez le vidage de base avec la commande `analyze` :

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Cette action affiche une session interactive qui accepte des commandes comme :

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

Pour voir une exception non gérée qui a interrompu votre application :

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

## <a name="special-instructions-for-docker"></a>Instructions spéciales pour l’ancrage

Si vous exécutez dans le cadre de l’arrimeur, la collection de vidages requiert des fonctionnalités `SYS_PTRACE` (`--cap-add=SYS_PTRACE` ou `--privileged`).

Sur les images de la station d’accueil Linux Microsoft .NET Core SDK, certaines commandes `dotnet-dump` peuvent lever l’exception suivante :

> Exception non gérée : System. DllNotFoundException : impossible de charger la bibliothèque partagée « libdl.so » ou l’une de ses dépendances.

Pour contourner ce problème, installez le package « libc6-dev ».
