---
title: dotnet-dump - .NET Core
description: Installation et utilisation de l’outil de ligne de commande dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: 3c0e28d4efc96ae53ec7dfae243725ab400e6b8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737671"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Service de collecte`dotnet-dump`et d’analyse des décharges ( )

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

> [!NOTE]
> `dotnet-dump`n’est pas pris en charge sur macOS.

## <a name="installing-dotnet-dump"></a>Installation de `dotnet-dump`

Pour installer la dernière `dotnet-dump` version du [paquet NuGet,](https://www.nuget.org/packages/dotnet-dump)utilisez la commande [d’installation d’outils dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Synopsis

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Description

L’outil `dotnet-dump` global est un moyen de collecter et d’analyser les `lldb` décharges Windows et Linux sans aucun débbugger indigène impliqué comme sur Linux. Cet outil est important sur des plates-formes comme Alpine Linux où un travail `lldb` complet n’est pas disponible. L’outil `dotnet-dump` vous permet d’exécuter des commandes SOS pour analyser les plantages et le collecteur d’ordures (GC), mais ce n’est pas un débbuggeur indigène de sorte que les choses comme l’affichage des cadres de pile indigène ne sont pas pris en charge.

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire dotnet-counters.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                     |
| ------------------------------------------- |
| [dotnet-dump recueillir](#dotnet-dump-collect) |
| [Analyse de dotnet-dump](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>dotnet-dump recueillir

Capture une décharge à partir d’un processus.

### <a name="synopsis"></a>Synopsis

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Options

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

- **`-p|--process-id <PID>`**

  Spécifie le numéro d’identification du processus pour recueillir un dépotoir de mémoire.

- **`--type <Heap|Mini>`**

  Spécifie le type de décharge, qui détermine les types d’informations qui sont recueillies à partir du processus. Il en existe deux types :

  - `Heap`- Un dépotoir grand et relativement complet contenant des listes de modules, des listes de threads, toutes les piles, des informations d’exception, des informations de poignée, et toute la mémoire, sauf pour les images cartographiées.
  - `Mini`- Un petit dépotoir contenant des listes de modules, des listes de threads, des informations d’exception et toutes les piles.

  S’il `Heap` n’est pas spécifié, est la valeur par défaut.

- **`-o|--output <output_dump_path>`**

  Le chemin complet et le nom de fichier où le dépotoir collecté doit être écrit.

  S’il n’est pas spécifié :

  - Par défaut à *.dump_YYYYMMDD_HHMMSS.dmp* sur Windows.
  - Par défaut à *./core_YYYYMMDD_HHMMSS* sur Linux.

  YYYYMMDD est année/mois/jour et HHMMSS est Heure/Minute/Second.

- **`--diag`**

  Permet l’enregistrement diagnostique de la collecte des décharges.

## <a name="dotnet-dump-analyze"></a>Analyse de dotnet-dump

Démarre une coquille interactive pour explorer un dépotoir. La coquille accepte diverses [commandes SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Synopsis

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Arguments

- **`<dump_path>`**

  Spécifie le chemin vers le fichier de décharge à analyser.

### <a name="options"></a>Options

- **`-c|--command <debug_command>`**

  Spécifie la [commande](#analyze-sos-commands) de courir dans la coquille au départ.

### <a name="analyze-sos-commands"></a>Analyser les commandes SOS

| Commande                             | Fonction                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Affiche toutes les commandes disponibles                                                               |
| `soshelp|help <command>`            | Affiche la commande spécifiée.                                                               |
| `exit|quit`                         | Sortie en mode interactif.                                                                       |
| `clrstack <arguments>`              | Fournit uniquement une trace de la pile du code managé.                                                  |
| `clrthreads <arguments>`            | Répertorie les threads gérés en cours d’exécution.                                                            |
| `dumpasync <arguments>`             | Affiche des informations sur les machines d’état async sur le tas d’ordures collectés.                |
| `dumpassembly <arguments>`          | Affiche les détails d’une assemblée.                                                           |
| `dumpclass <arguments>`             | Affiche des informations sur une structure de classe EE à l’adresse spécifiée.                     |
| `dumpdelegate <arguments>`          | Affiche des informations sur un délégué.                                                        |
| `dumpdomain <arguments>`            | Affiche toutes les informations sur toutes les AppDomains et tous les assemblages dans les domaines.                |
| `dumpheap <arguments>`              | Affiche des informations sur le tas d’ordures et les statistiques de collecte sur les objets.       |
| `dumpil <arguments>`                | Affiche le Microsoft Intermediate Language (MSIL) associé à une méthode managée. |
| `dumplog <arguments>`               | Écrit le contenu d'un journal de contrainte en mémoire dans le fichier spécifié.                         |
| `dumpmd <arguments>`                | Affiche des informations sur une structure MethodDesc à l’adresse spécifiée.                   |
| `dumpmodule <arguments>`            | Affiche des informations sur une structure de module EE à l’adresse spécifiée.                    |
| `dumpmt <arguments>`                | Affiche des informations sur une table de méthodes à l'adresse spécifiée.                           |
| `dumpobj <arguments>`               | Affiche des informations sur un objet à l’adresse spécifiée.                                       |
| `dso|dumpstackobjects <arguments>`  | Affiche tous les objets managés recherchés dans les limites de la pile actuelle.                    |
| `eeheap <arguments>`                | Affiche des informations sur la mémoire de processus consommée par les structures internes de données en temps d’exécution.              |
| `finalizequeue <arguments>`         | Affiche tous les objets enregistrés pour la finalisation.                                             |
| `gcroot <arguments>`                | Affiche des informations sur les références (ou les racines) à un objet à l’adresse spécifiée.              |
| `gcwhere <arguments>`               | Affiche l’emplacement dans le tas GC de l’argument passé.                               |
| `ip2md <arguments>`                 | Affiche la structure MethodDesc à l’adresse spécifiée dans le code JIT.                       |
| `histclear <arguments>`             | Libère toutes les ressources utilisées par la famille de commandes `hist*`.                                |
| `histinit <arguments>`              | Initialise les structures SOS du journal de contrainte enregistré dans l’élément débogué.                     |
| `histobj <arguments>`               | Affiche les relocalisations de journaux `<arguments>`de recouvrement de stress de collecte d’ordures liées à .              |
| `histobjfind <arguments>`           | Affiche toutes les entrées de journal qui référencent un objet à l'adresse spécifiée.               |
| `histroot <arguments>`              | Affiche les informations liées aux promotions et aux réadressages de la racine spécifiée.        |
| `lm|modules`                        | Affiche les modules natifs dans le processus.                                                   |
| `name2ee <arguments>`               | Affiche la structure MethodTable et la `<argument>`structure EEClass pour le .                |
| `pe|printexception <arguments>`     | Affiche tout objet dérivé de la `<argument>`classe Exception à l’adresse .             |
| `setsymbolserver <arguments>`       | Permet le support serveur symbole                                                             |
| `syncblk <arguments>`               | Affiche les informations du titulaire SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Définit ou affiche l’ID de thread actuel pour les commandes SOS.                                  |

## <a name="using-dotnet-dump"></a>Utilisation de `dotnet-dump`

La première étape consiste à collecter un dépotoir. Cette étape peut être ignorée si un décharge de base a déjà été généré. Le système d’exploitation ou la fonction de génération de [décharges](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) intégrées du .NET Core peut créer chacun des décharges de base.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Maintenant, analysez le `analyze` déchargeur de base avec la commande :

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Cette action évoque une session interactive qui accepte les commandes comme :

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

Pour voir une exception non gérée qui a tué votre application :

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

## <a name="special-instructions-for-docker"></a>Instructions spéciales pour Docker

Si vous êtes en cours d’exécution`--cap-add=SYS_PTRACE` `--privileged`sous Docker, la collecte de décharge nécessite des `SYS_PTRACE` capacités ( ou ).

Sur microsoft .NET Core SDK `dotnet-dump` Linux Docker images, certaines commandes peuvent jeter l’exception suivante:

> Exception non gérée : System.DllNotFoundException: Incapable de charger la bibliothèque partagée 'libdl.so' ou l’une de ses dépendances' exception.

Pour contourner ce problème, installez le paquet "libc6-dev".
