---
title: Utilisation élevée du processeur par le débogage-.NET Core
description: Un didacticiel qui vous guide tout au long du débogage de l’utilisation élevée de l’UC dans .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 93076bbce3baf3a219b25c927d2aba3d2d57456f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557800"
---
# <a name="debug-high-cpu-usage-in-net-core"></a>Déboguer une utilisation élevée du processeur dans .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,1 et versions ultérieures

Dans ce didacticiel, vous allez apprendre à déboguer un scénario d’utilisation excessive de l’UC. À l’aide de l’exemple fourni ASP.NET Core référentiel de code source de l' [application Web](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , vous pouvez provoquer un blocage intentionnellement. Le point de terminaison subira un blocage et l’accumulation des threads. Vous allez apprendre à utiliser différents outils pour diagnostiquer ce scénario avec plusieurs éléments clés de données de diagnostic.

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
>
> - Examiner l’utilisation élevée du processeur
> - Déterminer l’utilisation de l’UC avec [dotnet-Counters](dotnet-counters.md)
> - Utiliser [dotnet-trace](dotnet-trace.md) pour la génération de trace
> - Performances des profils dans PerfView
> - Diagnostiquer et résoudre l’utilisation excessive du processeur

## <a name="prerequisites"></a>Conditions préalables

Le didacticiel utilise :

- [Kit de développement logiciel (SDK) .net Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.
- [Exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) pour déclencher le scénario.
- [dotnet-trace](dotnet-trace.md) pour répertorier les processus et générer un profil.
- [dotnet-compteurs](dotnet-counters.md) pour surveiller l’utilisation de l’UC.

## <a name="cpu-counters"></a>Compteurs UC

Avant de tenter de collecter les données de diagnostic, vous devez observer une condition d’UC élevée. Exécutez l' [exemple d’application](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) à l’aide de la commande suivante à partir du répertoire racine du projet.

```dotnetcli
dotnet run
```

Pour Rechercher l’ID de processus, utilisez la commande suivante :

```dotnetcli
dotnet-trace ps
```

Prenez note de l’ID de processus à partir de la sortie de la commande. Notre ID de processus était `22884` , mais la vôtre sera différente. Pour vérifier l’utilisation actuelle de l’UC, utilisez la commande [dotnet-Counters](dotnet-counters.md) Tool :

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

Le `refresh-interval` est le nombre de secondes entre les valeurs de l’UC d’interrogation de compteur. La sortie doit ressembler à ce qui suit :

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

Avec l’application Web en cours d’exécution, immédiatement après le démarrage, l’UC n’est pas consommée et est signalée à `0%` . Accédez à l' `api/diagscenario/highcpu` itinéraire avec `60000` comme paramètre d’itinéraire :

`https://localhost:5001/api/diagscenario/highcpu/60000`

À présent, réexécutez la commande [dotnet-Counters](dotnet-counters.md) . Pour surveiller uniquement le `cpu-usage` , spécifiez `System.Runtime[cpu-usage]` dans le cadre de la commande.

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

Vous devez voir une augmentation de l’utilisation de l’UC comme indiqué ci-dessous :

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

Pendant toute la durée de la demande, l’utilisation de l’UC passera à environ 25%. En fonction de l’ordinateur hôte, attendez-vous à varier l’utilisation du processeur.

> [!TIP]
> Pour visualiser une utilisation du processeur encore plus élevée, vous pouvez exercer ce point de terminaison dans plusieurs onglets de navigateur simultanément.

À ce stade, vous pouvez indiquer en toute sécurité que l’UC s’exécute plus haut que prévu.

## <a name="trace-generation"></a>Génération de trace

Lors de l’analyse d’une requête lente, vous avez besoin d’un outil de diagnostic qui peut fournir des informations sur ce que fait le code. Le choix habituel est un profileur, et il existe différentes options de profileur à choisir.

### <a name="linux"></a>[Linux](#tab/linux)

L' `perf` outil peut être utilisé pour générer des profils d’application .net core. Quittez l’instance précédente de l' [exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).

Définissez la `COMPlus_PerfMapEnabled` variable d’environnement pour que l’application .net Core crée un `map` fichier dans le `/tmp` répertoire. Ce `map` fichier est utilisé par `perf` pour mapper l’adresse de l’UC aux fonctions générées juste-à-temps par nom. Pour plus d’informations, consultez [écrire une carte de performances](../run-time-config/debugging-profiling.md#write-perf-map).

Exécutez l' [exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) dans la même session de terminal.

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

Renouvelez le point de terminaison de l’API UC élevée ( `https://localhost:5001/api/diagscenario/highcpu/60000` ). Pendant qu’elle s’exécute dans la requête de 1 minute, exécutez la `perf` commande avec votre ID de processus :

```bash
sudo perf record -p 2266 -g
```

La `perf` commande démarre le processus de collecte des performances. Laissez-le s’exécuter pendant environ 20-30 secondes, puis appuyez sur <kbd>Ctrl + C</kbd> pour quitter le processus de collecte. Vous pouvez utiliser la même `perf` commande pour afficher la sortie de la trace.

```bash
sudo perf report -f
```

Vous pouvez également générer un _graphique à flamme_ à l’aide des commandes suivantes :

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

Cette commande génère un `flamegraph.svg` que vous pouvez afficher dans le navigateur pour examiner le problème de performances :

[![Image SVG du graphique à flamme](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)

### <a name="windows"></a>[Windows](#tab/windows)

Sur Windows, vous pouvez utiliser l’outil [dotnet-trace](dotnet-trace.md) en tant que profileur. À l’aide de l' [exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)précédent, réexécutez le point de terminaison d’UC élevé ( `https://localhost:5001/api/diagscenario/highcpu/60000` ). Pendant qu’elle s’exécute dans la requête de 1 minute, utilisez la `collect` commande comme suit :

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

Laissez [dotnet-trace](dotnet-trace.md) s’exécuter pendant environ 20-30 secondes, puis appuyez sur <kbd>entrée</kbd> pour quitter la collection. Le résultat est un `nettrace` fichier situé dans le même dossier. Les `nettrace` fichiers sont un excellent moyen d’utiliser les outils d’analyse existants sur Windows.

Ouvrez `nettrace` avec [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) comme indiqué ci-dessous.

[![Image PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)

---

## <a name="see-also"></a>Voir aussi

- [dotnet-trace](dotnet-trace.md) pour répertorier les processus
- [dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée
- [dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage
- [dotnet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Déboguer un interblocage dans .NET Core](debug-deadlock.md)
