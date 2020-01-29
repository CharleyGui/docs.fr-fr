---
title: Didacticiel de débogage d’une fuite de mémoire
description: Découvrez comment déboguer une fuite de mémoire dans .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737731"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Didacticiel : déboguer une fuite de mémoire dans .NET Core

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 3,0 et versions ultérieures

Ce didacticiel présente les outils permettant d’analyser une fuite de mémoire .NET Core.

Ce didacticiel utilise un exemple d’application, conçu pour une fuite de mémoire intentionnelle. L’exemple est fourni en tant qu’exercice. Vous pouvez analyser une application qui présente involontairement une fuite de mémoire.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
>
> - Examinez l’utilisation de la mémoire managée avec [dotnet-Counters](dotnet-counters.md).
> - Générez un fichier dump.
> - Analyser l’utilisation de la mémoire à l’aide du fichier dump.

## <a name="prerequisites"></a>Prerequisites

Le didacticiel utilise les éléments suivants :

- [Kit de développement logiciel (SDK) .net Core 3,0](https://dotnet.microsoft.com/download/dotnet-core) ou version ultérieure.
- [dotnet-trace](dotnet-trace.md) pour répertorier les processus.
- [dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée.
- [dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage.
- Exemple d’application [cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) à diagnostiquer.

Ce didacticiel part du principe que l’exemple et les outils sont installés et prêts à l’emploi.

## <a name="examine-managed-memory-usage"></a>Examiner l’utilisation de la mémoire managée

Avant de commencer à collecter les données de diagnostics pour nous aider dans ce scénario, vous devez vous assurer que vous voyez une fuite de mémoire (croissance de la mémoire). Vous pouvez utiliser l’outil [dotnet-Counters pour le](dotnet-counters.md) confirmer.

Ouvrez une fenêtre de console et accédez au répertoire où vous avez téléchargé et décompressé l' [exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Exécutez la cible :

```dotnetcli
dotnet run
```

À partir d’une console distincte, recherchez l’ID de processus à l’aide de l’outil [dotnet-trace](dotnet-trace.md) :

```console
dotnet-trace ps
```

La sortie doit ressembler à ce qui suit :

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

À présent, vérifiez l’utilisation de la mémoire managée avec l’outil [dotnet-Counters](dotnet-counters.md) . Le `--refresh-interval` spécifie le nombre de secondes entre les actualisations :

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

La sortie dynamique doit ressembler à ce qui suit :

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

Se focaliser sur cette ligne :

```console
    GC Heap Size (MB)                                  4
```

Vous pouvez voir que la mémoire du tas managé est de 4 Mo juste après le démarrage.

À présent, cliquez sur l’URL `http://localhost:5000/api/diagscenario/memleak/20000`.

Notez que l’utilisation de la mémoire a augmenté jusqu’à 30 Mo.

```console
    GC Heap Size (MB)                                 30
```

En observant l’utilisation de la mémoire, vous pouvez en toute sécurité indiquer que la mémoire augmente ou subit une fuite. L’étape suivante consiste à collecter les données appropriées pour l’analyse de la mémoire.

### <a name="generate-memory-dump"></a>Générer un vidage de la mémoire

Lors de l’analyse de fuites de mémoire possibles, vous devez accéder au segment de mémoire de l’application. Vous pouvez ensuite analyser le contenu de la mémoire. En examinant les relations entre les objets, vous créez des théories sur la raison pour laquelle la mémoire n’est pas libérée. Une source de données de diagnostics courante est un vidage de la mémoire sur Windows ou le vidage de base équivalent sur Linux. Pour générer un dump d’une application .NET Core, vous pouvez utiliser l’outil [dotnet-dump)](dotnet-dump.md) .

À l’aide de l' [exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) précédemment démarré, exécutez la commande suivante pour générer un vidage Linux Core :

```dotnetcli
dotnet-dump collect -p 4807
```

Le résultat est un vidage central situé dans le même dossier.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Redémarrer le processus en échec

Une fois le vidage collecté, vous devez disposer d’informations suffisantes pour diagnostiquer le processus en échec. Si le processus en échec est en cours d’exécution sur un serveur de production, il s’agit de l’heure idéale pour la correction à terme, en redémarrant le processus.

Dans ce didacticiel, vous avez maintenant terminé l' [exemple de cible de débogage](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) et vous pouvez le fermer. Accédez au terminal qui a démarré le serveur, puis appuyez sur `Control-C`.

### <a name="analyze-the-core-dump"></a>Analyser le vidage principal

Maintenant que vous avez généré un vidage de base, utilisez l’outil [dotnet-dump)](dotnet-dump.md) pour analyser le vidage :

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Où `core_20190430_185145` est le nom de l’image de base que vous souhaitez analyser.

> [!NOTE]
> Si vous voyez une erreur indiquant que *libdl.so* est introuvable, vous devrez peut-être installer le package *libc6-dev* . Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Linux](../linux-prerequisites.md).

Une invite s’affiche, dans laquelle vous pouvez entrer des commandes SOS. En règle générale, la première chose que vous souhaitez examiner est l’état global du tas géré :

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

Ici, vous pouvez voir que la plupart des objets sont des objets `String` ou `Customer`.

Vous pouvez réutiliser la commande `dumpheap` avec la table de méthodes (MT) pour obtenir la liste de toutes les instances de `String` :

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

Vous pouvez maintenant utiliser la commande `gcroot` sur une instance `System.String` pour voir comment et pourquoi l’objet est rooté. Soyez patient, car cette commande prend plusieurs minutes avec un segment de mémoire de 30 Mo :

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

Vous pouvez voir que la `String` est directement détenue par l’objet `Customer` et détenue indirectement par un objet `CustomerCache`.

Vous pouvez continuer à vider les objets pour voir que la plupart des objets `String` suivent un modèle similaire. À ce stade, l’investigation a fourni suffisamment d’informations pour identifier la cause racine de votre code.

Cette procédure générale vous permet d’identifier la source de fuites de mémoire majeures.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Dans ce didacticiel, vous avez démarré un exemple de serveur Web. Ce serveur doit avoir été arrêté, comme expliqué dans la section [redémarrage de l’échec du processus](#restart-the-failed-process) .

Vous pouvez également supprimer le fichier dump qui a été créé.

## <a name="next-steps"></a>Étapes suivantes :

Félicitations, vous avez terminé ce didacticiel.

Nous publions toujours d’autres didacticiels de diagnostic. Vous pouvez lire les versions préliminaires dans le référentiel [dotnet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) .

Ce didacticiel a abordé les principes de base des outils de diagnostic .NET clés. Pour une utilisation avancée, consultez la documentation de référence suivante :

* [dotnet-trace](dotnet-trace.md) pour répertorier les processus.
* [dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire managée.
* [dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de vidage.
