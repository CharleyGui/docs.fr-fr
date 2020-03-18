---
title: dotnet-compteurs - .NET Core
description: Apprenez à installer et à utiliser l’outil de ligne de commande dotnet-counter.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147176"
---
# <a name="dotnet-counters"></a>dotnet-counters

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

## <a name="install-dotnet-counters"></a>Installer des compteurs dotnet

Pour installer la dernière `dotnet-counters` version du [paquet NuGet,](https://www.nuget.org/packages/dotnet-counters)utilisez la commande [d’installation d’outils dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Synopsis

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Description

`dotnet-counters`est un outil de surveillance du rendement pour la surveillance de la santé ad hoc et l’enquête de premier niveau sur le rendement. Il peut observer les valeurs de <xref:System.Diagnostics.Tracing.EventCounter> compteur de performance qui sont publiées via l’API. Par exemple, vous pouvez surveiller rapidement des choses comme l’utilisation du processeur ou le taux d’exceptions jetées dans `PerfView` votre `dotnet-trace`application .NET Core pour voir s’il ya quelque chose de suspect avant de plonger dans une enquête de performance plus grave en utilisant ou .

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire dotnet-counters.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                             |
| --------------------------------------------------- |
| [dotnet-compteurs recueillir](#dotnet-counters-collect) |
| [liste de compteurs dotnet](#dotnet-counters-list)       |
| [moniteur dotnet-compteurs](#dotnet-counters-monitor) |
| [dotnet-compteurs ps](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a>dotnet-compteurs recueillir

Recueillir périodiquement des valeurs de compteur sélectionnées et les exporter dans un format de fichier spécifié pour le post-traitement.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  L’ID du processus à surveiller.

- **`--refresh-interval <SECONDS>`**

  Le nombre de secondes à retarder entre la mise à jour des compteurs affichés

- **`counter_list <COUNTERS>`**

  Un espace séparé liste de compteurs. Les compteurs `provider_name[:counter_name]`peuvent être spécifiés . Si `provider_name` le est utilisé `counter_name`sans qualification, alors tous les compteurs sont affichés. Pour découvrir les noms des fournisseurs et des comptoirs, utilisez la commande [de liste de compteurs pointnet.](#dotnet-counters-list)

- **`--format <csv|json>`**

  TLe format à exporter. Actuellement disponible: csv, json.

- **`-o|--output <output>`**

  Le nom du fichier de sortie.

### <a name="examples"></a>Exemples

- Recueillir tous les compteurs à un intervalle de rafraîchissement de 3 secondes et de générer un csv comme sortie:

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a>liste de compteurs dotnet

Affiche une liste de noms et de descriptions de compteurs, regroupés par fournisseur.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a> Exemple

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a>moniteur dotnet-compteurs

Affiche des valeurs périodiquement rafraîchissantes de certains compteurs.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  L’ID du processus à surveiller.

- **`--refresh-interval <SECONDS>`**

  Le nombre de secondes à retarder entre la mise à jour des compteurs affichés

- **`counter_list <COUNTERS>`**

  Un espace séparé liste de compteurs. Les compteurs `provider_name[:counter_name]`peuvent être spécifiés . Si `provider_name` le est utilisé `counter_name`sans qualification, alors tous les compteurs sont affichés. Pour découvrir les noms des fournisseurs et des comptoirs, utilisez la commande [de liste de compteurs pointnet.](#dotnet-counters-list)

### <a name="examples"></a>Exemples

- Surveillez tous `System.Runtime` les compteurs à partir d’un intervalle de rafraîchissement de 3 secondes :

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- Surveiller juste l’utilisation de processeur `System.Runtime`et la taille de tas de GC de :

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Surveiller `EventCounter` les valeurs `EventSource`de l’utilisateur défini . Pour plus d’informations, voir [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a>dotnet-compteurs ps

Affichez une liste de processus dotnet qui peuvent être surveillés.

### <a name="synopsis"></a>Synopsis

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a> Exemple

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
