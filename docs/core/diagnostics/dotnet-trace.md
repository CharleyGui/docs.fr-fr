---
title: outil de diagnostic dotnet-trace-CLI .NET
description: Découvrez comment installer et utiliser l’outil CLI dotnet-trace pour collecter les traces .NET d’un processus en cours d’exécution sans le profileur natif, à l’aide de .NET EventPipe.
ms.date: 11/17/2020
ms.openlocfilehash: a2925ac0a0815fe48ca9b36b643ff896aa3c0ff6
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593205"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>utilitaire d’analyse des performances dotnet-trace

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="install"></a>Installer

Il existe deux façons de télécharger et d’installer `dotnet-trace` :

- **outil Global dotnet :**

  Pour installer la dernière version Release du `dotnet-trace` [package NuGet](https://www.nuget.org/packages/dotnet-trace), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- **Téléchargement direct :**

  Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :

  | Système d''exploitation  | Plateforme |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [ARM](https://aka.ms/dotnet-trace/win-arm) \| [ARM-x64](https://aka.ms/dotnet-trace/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-trace/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-trace/linux-x64) \| [ARM](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64) |

## <a name="synopsis"></a>Synopsis

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Description

L' `dotnet-trace` outil :

* Est un outil .NET Core multiplateforme.
* Active la collecte des traces .NET Core d’un processus en cours d’exécution sans profileur natif.
* Repose sur [`EventPipe`](./eventpipe.md) le Runtime .net core.
* Offre la même expérience sur Windows, Linux ou macOS.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

- **`--version`**

  Affiche la version de l’utilitaire dotnet-trace.

## <a name="commands"></a>Commandes

| Commande                                                   |
|-----------------------------------------------------------|
| [dotnet-collecte des traces](#dotnet-trace-collect)             |
| [conversion dotnet-trace](#dotnet-trace-convert)             |
| [dotnet-trace PS](#dotnet-trace-ps)                       |
| [liste de suivi dotnet-profils](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a>dotnet-collecte des traces

Collecte une trace de diagnostic à partir d’un processus en cours d’exécution.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a>Options

- **`--buffersize <size>`**

  Définit la taille de la mémoire tampon circulaire en mémoire, en mégaoctets. 256 Mo par défaut.

- **`--clreventlevel <clreventlevel>`**

  Commentaires des événements CLR à émettre.

- **`--clrevents <clrevents>`**

  Liste des événements du runtime CLR à émettre.

- **`--format {Chromium|NetTrace|Speedscope}`**

  Définit le format de sortie pour la conversion du fichier de trace. Par défaut, il s’agit de `NetTrace`.

- **`-n, --name <name>`**

  Nom du processus à partir duquel la trace doit être collectée.

- **`--diagnostic-port <path-to-port>`**

  Nom du port de diagnostic à créer. Consultez [utiliser le port de diagnostic pour collecter une trace à partir du démarrage](#use-diagnostic-port-to-collect-a-trace-from-app-startup) de l’application pour savoir comment utiliser cette option pour collecter une trace à partir du démarrage de l’application.

- **`-o|--output <trace-file-path>`**

  Chemin de sortie pour les données de trace collectées. S’il n’est pas spécifié, la valeur par défaut est `trace.nettrace` .

- **`-p|--process-id <PID>`**

  ID de processus à partir duquel la trace doit être collectée.

- **`--profile <profile-name>`**

  Ensemble de configurations de fournisseur nommé prédéfini qui permet de spécifier succinctement des scénarios de suivi courants. Les profils suivants sont disponibles :

 | Profil | Description |
 |---------|-------------|
 |`cpu-sampling`|Utile pour le suivi de l’utilisation de l’UC et des informations générales du Runtime .NET. Il s’agit de l’option par défaut si aucun profil ou fournisseur n’est spécifié.|
 |`gc-verbose`|Effectue le suivi des collections GC et des exemples d’allocations d’objets.|
 |`gc-collect`|Effectue le suivi des collections GC uniquement à faible surcharge.|

- **`--providers <list-of-comma-separated-providers>`**

  Liste séparée par des virgules des `EventPipe` fournisseurs à activer. Ces fournisseurs complètent tous les fournisseurs implicites par `--profile <profile-name>` . S’il existe une incohérence pour un fournisseur particulier, cette configuration est prioritaire par rapport à la configuration implicite à partir du profil.

  Cette liste de fournisseurs se présente sous la forme suivante :

  - `Provider[,Provider]`
  - `Provider` se présente sous la forme : `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .
  - `KeyValueArgs` se présente sous la forme : `[key1=value1][;key2=value2]` .

- **`-- <command>` (pour les applications cibles exécutant .NET 5,0 uniquement)**

  Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0. Cela peut être utile lors du diagnostic de problèmes qui se produisent tôt dans le processus, tels que le problème de performance de démarrage ou le chargeur d’assembly et les erreurs de Binder.

  > [!NOTE]
  > L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application. Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.

> [!NOTE]
> L’arrêt de la trace peut prendre beaucoup de temps (jusqu’à quelques minutes) pour les applications de grande taille. Le Runtime doit envoyer sur le cache de type pour tout le code managé qui a été capturé dans la trace.

## <a name="dotnet-trace-convert"></a>conversion dotnet-trace

Convertit les `nettrace` traces en d’autres formats pour les utiliser avec d’autres outils d’analyse de trace.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a>Arguments

- **`<input-filename>`**

  Fichier de trace d’entrée à convertir. La valeur par défaut est *trace. NetTrace*.

### <a name="options"></a>Options

- **`--format <Chromium|NetTrace|Speedscope>`**

  Définit le format de sortie pour la conversion du fichier de trace.

- **`-o|--output <output-filename>`**

  Nom du fichier de sortie. L’extension du format cible sera ajoutée.

> [!NOTE]
> La conversion `nettrace` de fichiers en `chromium` `speedscope` fichiers ou est irréversible. `speedscope``chromium`les fichiers et ne contiennent pas toutes les informations nécessaires à la reconstruction des `nettrace` fichiers. Toutefois, la `convert` commande conserve le fichier d’origine `nettrace` . par conséquent, ne supprimez pas ce fichier si vous envisagez de l’ouvrir à l’avenir.

## <a name="dotnet-trace-ps"></a>dotnet-trace PS

 Répertorie les processus dotnet à partir desquels les traces peuvent être collectées.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>liste de suivi dotnet-profils

Répertorie les profils de suivi prédéfinis avec une description des fournisseurs et des filtres dans chaque profil.

### <a name="synopsis"></a>Synopsis

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Collecter une trace avec dotnet-trace

Pour collecter des traces à l’aide de `dotnet-trace` :

- Obtient l’identificateur de processus (PID) de l’application .NET Core à partir duquel collecter les traces.

  - Sur Windows, vous pouvez utiliser le gestionnaire des tâches ou la `tasklist` commande, par exemple.
  - Sur Linux, par exemple, la `ps` commande.
  - [dotnet-trace PS](#dotnet-trace-ps)

- Exécutez la commande suivante :

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  La commande précédente génère une sortie similaire à ce qui suit :

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Arrêtez la collecte en appuyant sur la `<Enter>` touche. `dotnet-trace` terminera la journalisation des événements dans le fichier *trace. NetTrace* .

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a>Lancer une application enfant et collecter une trace à partir de son démarrage à l’aide de dotnet-trace

> [!IMPORTANT]
> Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.

Parfois, il peut être utile de collecter une trace d’un processus à partir de son démarrage. Pour les applications qui exécutent .NET 5,0 ou une version ultérieure, il est possible de le faire à l’aide de dotnet-trace.

Cette opération démarre `hello.exe` avec `arg1` et `arg2` comme ses arguments de ligne de commande et collecte une trace à partir de son démarrage au moment de l’exécution :

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

La commande précédente génère une sortie similaire à ce qui suit :

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

Vous pouvez arrêter la collecte de la trace en appuyant sur ou sur la `<Enter>` `<Ctrl + C>` touche. Cela va également se terminer `hello.exe` .

> [!NOTE]
> `hello.exe`Le lancement via dotnet-trace rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout.
> La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant.
> Si le processus enfant se termine avant l’outil, l’outil s’arrête également et la trace doit être visible en toute sécurité.

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a>Utiliser le port de diagnostic pour collecter une trace à partir du démarrage de l’application

  > [!IMPORTANT]
  > Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.

Le port de diagnostic est une nouvelle fonctionnalité d’exécution qui a été ajoutée dans .NET 5, qui vous permet de démarrer le suivi à partir du démarrage de l’application. Pour ce faire à l’aide de `dotnet-trace` , vous pouvez utiliser `dotnet-trace collect -- <command>` comme décrit dans les exemples ci-dessus ou utiliser l' `--diagnostic-port` option.

L’utilisation `dotnet-trace <collect|monitor> -- <command>` de pour lancer l’application en tant que processus enfant est la manière la plus simple de la suivre rapidement de son démarrage.

Toutefois, lorsque vous souhaitez mieux contrôler la durée de vie de l’application faisant l’objet d’un suivi (par exemple, surveiller l’application pendant les 10 premières minutes uniquement et continuer l’exécution) ou si vous devez interagir avec l’application à l’aide de l’interface CLI, l’utilisation `--diagnostic-port` de l’option vous permet de contrôler à la fois l’application cible en cours d’analyse et `dotnet-trace` .

1. La commande ci-dessous `dotnet-trace` crée un socket de diagnostic nommé `myport.sock` et attend une connexion.

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    Sortie :

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. Dans une console distincte, lancez l’application cible avec la variable d’environnement `DOTNET_DiagnosticPorts` définie sur la valeur dans la `dotnet-trace` sortie.

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    Vous devez ensuite activer `dotnet-trace` le suivi pour démarrer le suivi `my-dotnet-app` :

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > Le lancement de votre application avec `dotnet run` peut être problématique, car l’interface CLI dotnet peut générer de nombreux processus enfants qui ne sont pas votre application et qui peuvent se connecter à `dotnet-trace` avant votre application, en laissant votre application interrompue au moment de l’exécution. Nous vous recommandons d’utiliser directement une version autonome de l’application ou `dotnet exec` d’utiliser pour lancer l’application.

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Afficher la trace capturée à partir de dotnet-trace

Sur Windows, les fichiers *. NetTrace* peuvent être affichés sur [PerfView](https://github.com/microsoft/perfview) pour l’analyse : pour les traces collectées sur d’autres plateformes, le fichier de trace peut être déplacé vers un ordinateur Windows à afficher sur PerfView.

Sur Linux, la trace peut être affichée en modifiant le format de sortie de `dotnet-trace` en `speedscope` . Le format du fichier de sortie peut être modifié à l’aide de l' `-f|--format` option : crée `-f speedscope` `dotnet-trace` un `speedscope` fichier. Vous pouvez choisir entre `nettrace` (option par défaut) et `speedscope` . `Speedscope` les fichiers peuvent être ouverts à l’adresse <https://www.speedscope.app> .

> [!NOTE]
> Le Runtime .NET Core génère des traces au `nettrace` format. Les suivis sont convertis en speedscope (si spécifié) une fois la trace terminée. Étant donné que certaines conversions peuvent entraîner une perte de données, le fichier d’origine `nettrace` est conservé en regard du fichier converti.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Utiliser dotnet-trace pour collecter des valeurs de compteur au fil du temps

`dotnet-trace` puissiez

* Utilisez `EventCounter` pour la surveillance de l’intégrité de base dans les environnements sensibles aux performances. Par exemple, en production.
* Collectez les traces afin qu’elles n’aient pas besoin d’être affichées en temps réel.

Par exemple, pour collecter les valeurs de compteur de performance du runtime, utilisez la commande suivante :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

La commande précédente indique aux compteurs Runtime de signaler une fois toutes les secondes pour une surveillance de l’intégrité légère. Le remplacement d' `EventCounterIntervalSec=1` une valeur supérieure (par exemple, 60) permet la collecte d’une trace plus petite avec moins de granularité dans les données du compteur.

La commande suivante réduit la surcharge et la taille de trace plus grande que la taille précédente :

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

La commande précédente désactive les événements d’exécution et le profileur de pile managée.

## <a name="net-providers"></a>Fournisseurs .NET

Le Runtime .NET Core prend en charge les fournisseurs .NET suivants. .NET Core utilise les mêmes mots clés pour activer `Event Tracing for Windows (ETW)` et les `EventPipe` suivis.

| Nom du fournisseur                            | Informations |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Fournisseur de runtime](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Mots clés du runtime CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Fournisseur d’arrêt](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Mots clés d’arrêt du CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Active l’exemple de profileur. |
