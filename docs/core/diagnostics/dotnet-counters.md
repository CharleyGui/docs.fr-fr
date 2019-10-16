---
title: dotnet-Counters-.NET Core
description: Découvrez comment installer et utiliser l’outil en ligne de commande dotnet-Counter.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321588"
---
# <a name="dotnet-counters"></a>dotnet-compteurs

**Cet article s’applique à : ✓** .net Core 3,0 SDK et versions ultérieures

## <a name="install-dotnet-counters"></a>Installer dotnet-Counters

Pour installer la dernière version Release du [package NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, utilisez la commande d’installation de l' [outil dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>Résumé

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>Description

`dotnet-counters` est un outil d’analyse des performances pour la surveillance de l’intégrité ad hoc et l’enquête sur les performances de premier niveau. Il peut observer les valeurs des compteurs de performance publiées via l’API <xref:System.Diagnostics.Tracing.EventCounter>. Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation de l’UC ou le taux d’exceptions levées dans votre application .NET Core pour voir s’il y a quelque chose de suspect avant de vous plonger dans une investigation de performances plus sérieuse à l’aide de `PerfView` ou `dotnet-trace`.

## <a name="options"></a>Options

- **`--version`**

  Affiche la version de l’utilitaire dotnet-Counters.

- **`-h|--help`**

  Affiche l’aide de la ligne de commande.

## <a name="commands"></a>Commandes

| Commande                                             |
| --------------------------------------------------- |
| [liste dotnet-Counters](#dotnet-counters-list)       |
| [analyse dotnet-Counters](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a>liste dotnet-Counters

Affiche la liste des noms et des descriptions des compteurs, regroupés par fournisseur.

### <a name="synopsis"></a>Résumé

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>Exemple

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

## <a name="dotnet-counters-monitor"></a>analyse dotnet-Counters

Affiche régulièrement les valeurs des compteurs sélectionnés.

### <a name="synopsis"></a>Résumé

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>Options

- **`-p|--process-id <PID>`**

  ID du processus à analyser.

- **`--refresh-interval <SECONDS>`**

  Nombre de secondes avant la mise à jour des compteurs affichés

- **`counter_list <COUNTERS>`**

  Liste séparée par des espaces des compteurs. Les compteurs peuvent être spécifiés `provider_name[:counter_name]`. Si le `provider_name` est utilisé sans `counter_name` éligible, tous les compteurs sont affichés. Pour découvrir les noms de fournisseur et de compteur, utilisez la commande [dotnet-Counters List](#dotnet-counters-list) .

### <a name="examples"></a>Exemples

- Surveillez tous les compteurs de `System.Runtime` à un intervalle d’actualisation de 3 secondes :

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

- Surveiller uniquement l’utilisation de l’UC et la taille du tas GC à partir de `System.Runtime` :

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- Analyser les valeurs `EventCounter` à partir des `EventSource` définies par l’utilisateur. Pour plus d’informations, consultez [Didacticiel : Comment mesurer les performances pour les événements très fréquents à l’aide de EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
