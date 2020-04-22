---
title: Debug un tutoriel fuite de mémoire
description: Apprenez à déboiffer une fuite de mémoire dans .NET Core.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: d47992bab9dab64cf7f88ff679eef407dd891b5a
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021362"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Tutorial: Debug une fuite de mémoire dans .NET Core

**Cet article s’applique à:** ✔️ .NET Core 3.0 SDK et les versions ultérieures

Ce tutoriel démontre les outils pour analyser une fuite de mémoire .NET Core.

Ce tutoriel utilise une application d’échantillon, qui est conçu pour fuir intentionnellement la mémoire. L’échantillon est fourni comme exercice. Vous pouvez analyser une application qui fuit involontairement la mémoire aussi.

Ce didacticiel présente les procédures suivantes :

> [!div class="checklist"]
>
> - Examinez l’utilisation gérée de la mémoire avec [des compteurs pointnet.](dotnet-counters.md)
> - Générer un fichier de décharge.
> - Analyser l’utilisation de la mémoire à l’aide du fichier de décharge.

## <a name="prerequisites"></a>Prérequis

Le didacticiel utilise :

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) ou une version ultérieure.
- [pointnet-trace](dotnet-trace.md) à la liste des processus.
- [dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire gérée.
- [dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de décharge.
- Un [échantillon de débouger app cible](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) à diagnostiquer.

Le tutoriel suppose que l’échantillon et les outils sont installés et prêts à l’emploi.

## <a name="examine-managed-memory-usage"></a>Examiner l’utilisation gérée de la mémoire

Avant de commencer à collecter des données de diagnostic pour nous aider à provoquer ce scénario, vous devez vous assurer que vous voyez réellement une fuite de mémoire (croissance de la mémoire). Vous pouvez utiliser l’outil [dotnet-counters](dotnet-counters.md) pour confirmer cela.

Ouvrez une fenêtre de console et naviguez vers l’annuaire où vous avez téléchargé et décompressé la [cible de débbug échantillon](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/). Exécutez la cible :

```dotnetcli
dotnet run
```

À partir d’une console séparée, trouvez l’ID du processus à l’aide de l’outil [dotnet-trace](dotnet-trace.md) :

```console
dotnet-trace ps
```

La sortie doit ressembler à ce qui suit :

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Maintenant, vérifiez l’utilisation gérée de mémoire avec [l’outil dotnet-counters.](dotnet-counters.md) Le `--refresh-interval` spécifie le nombre de secondes entre les rafraîchissements:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

La production en direct devrait être similaire à :

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

En se concentrant sur cette ligne:

```console
    GC Heap Size (MB)                                  4
```

Vous pouvez voir que la mémoire de tas géré est de 4 Mo juste après le démarrage.

Maintenant, appuyez `http://localhost:5000/api/diagscenario/memleak/20000`sur l’URL .

Observez que l’utilisation de la mémoire est passée à 30 Mo.

```console
    GC Heap Size (MB)                                 30
```

En regardant l’utilisation de la mémoire, vous pouvez dire en toute sécurité que la mémoire est de plus en plus ou de fuite. L’étape suivante consiste à recueillir les bonnes données pour l’analyse de la mémoire.

### <a name="generate-memory-dump"></a>Générer un dépotoir de mémoire

Lors de l’analyse des fuites de mémoire possibles, vous devez accéder au tas de mémoire de l’application. Ensuite, vous pouvez analyser le contenu de la mémoire. En regardant les relations entre les objets, vous créez des théories sur les raisons pour lesquelles la mémoire n’est pas libérée. Une source de données diagnostiques courante est un dépotoir de mémoire sur Windows ou le décharge de base équivalent sur Linux. Pour générer un dépotoir d’une application .NET Core, vous pouvez utiliser l’outil [dotnet-dump).](dotnet-dump.md)

À l’aide de la [cible de débaillement de l’échantillon](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) précédemment commencée, exécutez la commande suivante pour générer un décharge de base Linux :

```dotnetcli
dotnet-dump collect -p 4807
```

Le résultat est un décharge de base situé dans le même dossier.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Redémarrer le processus défaillant

Une fois que le dépotoir est recueilli, vous devriez avoir suffisamment d’informations pour diagnostiquer le processus défectueus. Si le processus défaillant s’exécute sur un serveur de production, c’est maintenant le moment idéal pour l’assainissement à court terme en redémarrant le processus.

Dans ce tutoriel, vous avez maintenant terminé avec la [cible de débogé d’échantillons](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) et vous pouvez le fermer. Naviguez vers le terminal qui `Control-C`a commencé le serveur et appuyez .

### <a name="analyze-the-core-dump"></a>Analyser le dépotoir de base

Maintenant que vous avez un décharge de base généré, utilisez [l’outil de décharge de dotnet](dotnet-dump.md) pour analyser le dépotoir :

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Où `core_20190430_185145` est le nom de la décharge de base que vous voulez analyser.

> [!NOTE]
> Si vous voyez une erreur se plaindre que *libdl.so* ne peut pas être trouvé, vous devrez peut-être installer le paquet *libc6-dev.* Pour plus d’informations, consultez [Configuration requise pour .NET Core sur Linux](../install/dependencies.md?pivots=os-linux).

Vous serez présenté avec une invite où vous pouvez entrer les commandes SOS. Généralement, la première chose que vous voulez regarder est l’état global du tas géré:

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

Ici, vous pouvez voir `String` que `Customer` la plupart des objets sont soit ou des objets.

Vous pouvez `dumpheap` utiliser la commande à nouveau avec la table `String` de méthode (MT) pour obtenir une liste de tous les cas:

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

Vous pouvez maintenant `gcroot` utiliser `System.String` la commande sur une instance pour voir comment et pourquoi l’objet est enraciné. Soyez patient car cette commande prend plusieurs minutes avec un tas de 30 Mo :

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

Vous pouvez voir `String` que le `Customer` est directement détenu par `CustomerCache` l’objet et indirectement détenu par un objet.

Vous pouvez continuer à jeter `String` des objets pour voir que la plupart des objets suivent un modèle similaire. À ce stade, l’enquête a fourni suffisamment d’informations pour identifier la cause profonde de votre code.

Cette procédure générale vous permet d’identifier la source des principales fuites de mémoire.

## <a name="clean-up-resources"></a>Nettoyer les ressources

Dans ce tutoriel, vous avez lancé un exemple de serveur web. Ce serveur aurait dû être arrêté comme expliqué dans le redémarrage de la section [processus a échoué.](#restart-the-failed-process)

Vous pouvez également supprimer le fichier de décharge qui a été créé.

## <a name="next-steps"></a>Étapes suivantes

Félicitations pour avoir terminé ce tutoriel.

Nous publions encore plus de tutoriels diagnostiques. Vous pouvez lire les versions provisoires sur le référentiel [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

Ce tutoriel a couvert les bases des outils de diagnostic .NET clés. Pour une utilisation avancée, consultez la documentation de référence suivante :

* [pointnet-trace](dotnet-trace.md) à la liste des processus.
* [dotnet-compteurs](dotnet-counters.md) pour vérifier l’utilisation de la mémoire gérée.
* [dotnet-dump](dotnet-dump.md) pour collecter et analyser un fichier de décharge.
