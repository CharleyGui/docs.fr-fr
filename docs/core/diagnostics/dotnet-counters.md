---
title: outil de diagnostic dotnet-Counters-.NET CLI
description: Découvrez comment installer et utiliser l’outil CLI dotnet-Counter pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau.
ms.date: 11/17/2020
ms.openlocfilehash: 44d74cfaca7483b1506fe7ad762818e9b9ed7d63
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058088"
---
# <a name="investigate-performance-counters-dotnet-counters"></a>Examiner les compteurs de performance (dotnet-Counters)

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

## <a name="install"></a>Installer

Il existe deux façons de télécharger et d’installer `dotnet-counters` :

- **outil Global dotnet :**

  Pour installer la dernière version Release du `dotnet-counters` [package NuGet](https://www.nuget.org/packages/dotnet-counters), utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- **Téléchargement direct :**

  Téléchargez le fichier exécutable de l’outil qui correspond à votre plateforme :

  | Système d’exploitation  | Plateforme |
  | --- | -------- |
  | Windows | [x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [ARM](https://aka.ms/dotnet-counters/win-arm) \| [ARM-x64](https://aka.ms/dotnet-counters/win-arm64) |
  | macOS   | [x64](https://aka.ms/dotnet-counters/osx-x64) |
  | Linux   | [x64](https://aka.ms/dotnet-counters/linux-x64) \| [ARM](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64) |

## <a name="synopsis"></a>Synopsis

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Description

`dotnet-counters` est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau. Il peut observer les valeurs des compteurs de performance publiées via l' <xref:System.Diagnostics.Tracing.EventCounter> API. Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide `PerfView` de ou de `dotnet-trace` .

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire dotnet-Counters.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                             |
|-----------------------------------------------------|
| [dotnet-compteurs Collect](#dotnet-counters-collect) |
| [liste dotnet-Counters](#dotnet-counters-list)       |
| [analyse dotnet-Counters](#dotnet-counters-monitor) |
| [dotnet-Counters PS](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a>dotnet-compteurs Collect

Collectez périodiquement les valeurs de compteur sélectionnées et exportez-les dans un format de fichier spécifié pour le retraitement.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  ID du processus à partir duquel collecter les données de compteur.

- **`-n|--name <name>`**

  Nom du processus à partir duquel collecter les données de compteur.

- **`--diagnostic-port`**

  Nom du port de diagnostic à créer. Consultez [utilisation du port de diagnostic](#using-diagnostic-port) pour savoir comment utiliser cette option pour démarrer l’analyse des compteurs à partir du démarrage de l’application.

- **`--refresh-interval <SECONDS>`**

  Nombre de secondes avant la mise à jour des compteurs affichés

- **`--counters <COUNTERS>`**

  Liste de compteurs séparés par des virgules. Les compteurs peuvent être spécifiés `provider_name[:counter_name]` . Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés. Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .

- **`--format <csv|json>`**

  Format à exporter. Actuellement disponible : CSV, JSON.

- **`-o|--output <output>`**

  Nom du fichier de sortie.

- **`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**

  Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0. `dotnet-counters` lance un processus avec la commande fournie et collecte les métriques demandées. Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.

  > [!NOTE]
  > L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application. Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.

  > [!NOTE]
  > Le lancement d’un exécutable .NET via dotnet-Counter rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout. La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant. Si le processus enfant se termine avant l’outil, l’outil s’arrête également et la trace doit être visible en toute sécurité. Si vous devez utiliser stdin/stdout, vous pouvez utiliser l' `--diagnostic-port` option. Pour plus d’informations, consultez [utilisation du port de diagnostic](#using-diagnostic-port) .

### <a name="examples"></a>Exemples

- Collecter tous les compteurs à un intervalle d’actualisation de 3 secondes et générer un CSV en tant que sortie :

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- Démarrez `dotnet mvc.dll` en tant que processus enfant et commencez à collecter des compteurs Runtime et ASP.net Core des compteurs d’hébergement à partir du démarrage, puis enregistrez-le en tant que sortie JSON :

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a>liste dotnet-Counters

Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Exemple

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> Les `Microsoft.AspNetCore.Hosting` compteurs s’affichent lorsque des processus identifiés prennent en charge ces compteurs, par exemple, quand une application ASP.net Core s’exécute sur l’ordinateur hôte.

## <a name="dotnet-counters-monitor"></a>analyse dotnet-Counters

Affiche régulièrement les valeurs des compteurs sélectionnés.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  ID du processus à analyser.

- **`-n|--name <name>`**

  Nom du processus à analyser.

- **`--diagnostic-port`**

  Nom du port de diagnostic à créer. Consultez [utilisation du port de diagnostic](#using-diagnostic-port) pour savoir comment utiliser cette option pour démarrer l’analyse des compteurs à partir du démarrage de l’application.

- **`--refresh-interval <SECONDS>`**

  Nombre de secondes avant la mise à jour des compteurs affichés

- **`--counters <COUNTERS>`**

  Liste de compteurs séparés par des virgules. Les compteurs peuvent être spécifiés `provider_name[:counter_name]` . Si le `provider_name` est utilisé sans liste de compteurs éligibles, tous les compteurs du fournisseur sont affichés. Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .

 **`-- <command>` (pour les applications cibles exécutant .NET 5,0 ou version ultérieure uniquement)**

  Après les paramètres de configuration de la collection, l’utilisateur peut ajouter `--` suivi d’une commande pour démarrer une application .net avec au moins un runtime 5,0. `dotnet-counters` lance un processus avec la commande fournie et surveille les métriques demandées. Cela est souvent utile pour collecter des métriques pour le chemin de démarrage de l’application et peut être utilisé pour diagnostiquer ou surveiller les problèmes qui se produisent tôt avant ou après le point d’entrée principal.

  > [!NOTE]
  > L’utilisation de cette option permet de surveiller le premier processus .NET 5,0 qui communique avec l’outil, ce qui signifie que si votre commande lance plusieurs applications .NET, elle ne collecte que la première application. Par conséquent, il est recommandé d’utiliser cette option sur les applications autonomes ou à l’aide de l' `dotnet exec <app.dll>` option.

  > [!NOTE]
  > Le lancement d’un exécutable .NET via dotnet-Counter rend son entrée/sortie redirigée et vous ne pouvez pas interagir avec son stdin/stdout. La sortie de l’outil via CTRL + C ou SIGTERM met fin en toute sécurité à la fois à l’outil et au processus enfant. Si le processus enfant se termine avant l’outil, l’outil s’arrête également. Si vous devez utiliser stdin/stdout, vous pouvez utiliser l' `--diagnostic-port` option. Pour plus d’informations, consultez [utilisation du port de diagnostic](#using-diagnostic-port) .

### <a name="examples"></a>Exemples

- Surveiller tous les compteurs à partir d' `System.Runtime` un intervalle d’actualisation de 3 secondes :

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Surveiller `EventCounter` les valeurs de définies par l’utilisateur `EventSource` . Pour plus d’informations, consultez [Didacticiel : mesurer les performances à l’aide de EventCounters dans .net Core](event-counter-perf.md).

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- Affichez tous les compteurs connus disponibles dans `dotnet-counters` :

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime              
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- Affichez tous les compteurs connus disponibles dans `dotnet-counters` pour les applications .net 5 :

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime                     
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting       
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http                    
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- Lancer `my-aspnet-server.exe` et surveiller le nombre d’assemblys chargés à partir de leur démarrage (.net 5,0 ou version ultérieure uniquement) :

  > [!IMPORTANT]
  > Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- Lancer `my-aspnet-server.exe` avec `arg1` et `arg2` en tant qu’arguments de ligne de commande et surveiller sa plage de travail et sa taille de tas GC depuis son démarrage (.net 5,0 ou version ultérieure uniquement) :

  > [!IMPORTANT]
  > Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a>dotnet-Counters PS

Affiche la liste des processus dotnet qui peuvent être analysés.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a>Exemple

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a>Utilisation du port de diagnostic

  > [!IMPORTANT]
  > Cela fonctionne pour les applications qui exécutent .NET 5,0 ou une version ultérieure uniquement.

Le port de diagnostic est une nouvelle fonctionnalité d’exécution qui a été ajoutée dans .NET 5, qui vous permet de démarrer l’analyse ou la collecte des compteurs à partir du démarrage de l’application. Pour ce faire à l’aide de `dotnet-counters` , vous pouvez utiliser `dotnet-counters <collect|monitor> -- <command>` comme décrit dans les exemples ci-dessus ou utiliser l' `--diagnostic-port` option.

L’utilisation `dotnet-counters <collect|monitor> -- <command>` de pour lancer l’application en tant que processus enfant est le moyen le plus simple de l’analyser rapidement à partir de son démarrage.

Toutefois, lorsque vous souhaitez mieux contrôler la durée de vie de l’application surveillée (par exemple, surveiller l’application pendant les 10 premières minutes uniquement et continuer l’exécution) ou si vous devez interagir avec l’application à l’aide de l’interface CLI, l’utilisation `--diagnostic-port` de l’option vous permet de contrôler à la fois l’application cible en cours d’analyse et `dotnet-counters` .

1. La commande suivante permet aux compteurs dotnet de créer un socket de diagnostic nommé `myport.sock` et d’attendre une connexion.

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    Sortie :

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. Dans une console distincte, lancez l’application cible avec la variable d’environnement `DOTNET_DiagnosticPorts` définie sur la valeur dans la `dotnet-counters` sortie.

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    Cela doit ensuite permettre `dotnet-counters` de démarrer la collecte des compteurs sur `my-dotnet-app` :

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > Le lancement de votre application avec `dotnet run` peut être problématique, car l’interface CLI dotnet peut générer de nombreux processus enfants qui ne sont pas votre application et qui peuvent se connecter à `dotnet-counters` avant votre application, en laissant votre application interrompue au moment de l’exécution. Nous vous recommandons d’utiliser directement une version autonome de l’application ou `dotnet exec` d’utiliser pour lancer l’application.
