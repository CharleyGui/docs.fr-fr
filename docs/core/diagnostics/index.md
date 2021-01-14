---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: ee79057e45700e17fdd37cc36288b790d64d7a09
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188476"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quels sont les outils de diagnostic disponibles dans .NET Core ?

Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.

Cet article vous aide à trouver les différents outils dont vous avez besoin.

## <a name="managed-debuggers"></a>Débogueurs gérés

Les [débogueurs managés](managed-debuggers.md) vous permettent d’interagir avec votre programme. La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code. Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.

## <a name="logging-and-tracing"></a>Journalisation et suivi

La [journalisation et le suivi](logging-tracing.md) sont des techniques associées. Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux. Les fichiers consignent le détail des tâches exécutées par un programme. Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes. Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.

## <a name="metrics"></a>Mesures

[EventCounters](event-counters.md) vous permet d’écrire des mesures pour identifier et surveiller les problèmes de performances. Les métriques entraînent une baisse des performances par rapport au suivi, ce qui le rend plus adapté à une analyse des performances Always on. Le Runtime .NET et les bibliothèques publient plusieurs [EventCounters bien connus](available-counters.md) que vous pouvez également surveiller.

## <a name="unit-testing"></a>Test unitaire

Le [test unitaire](../testing/index.md) est un composant clé de l’intégration et du déploiement continus de logiciels de haute qualité. Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.

## <a name="dumps"></a>Vidages

Un [dump](./dumps.md) est un fichier qui contient un instantané du processus au moment de la création. Elles peuvent être utiles pour examiner l’état de votre application à des fins de débogage.

## <a name="symbols"></a>symboles

Les symboles sont une condition fondamentale pour le débogage et d’autres outils de diagnostic. Le contenu des fichiers de symboles varie selon les langages, les compilateurs et les plateformes. À un niveau très élevé, les symboles sont un mappage entre le code source et le binaire produit par le compilateur. Ces mappages sont utilisés pour fournir des informations telles que le numéro de ligne et les noms de vos variables locales dans les outils de diagnostic tels que [Visual Studio](/visualstudio/debugger/what-is-debugging) et [Visual Studio code](https://code.visualstudio.com/Docs/editor/debugging).  Le lien suivant contient une explication détaillée des [symboles](/windows/win32/dxtecharts/debugging-with-symbols) pour Windows, bien que la plupart des concepts s’appliquent également à d’autres plateformes. Les [symboles portables .net](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) ont une extension de fichier « PDB » similaire à celle de Windows PDB, mais ne sont pas compatibles avec le format PDB Windows.

## <a name="collect-diagnostics-in-containers"></a>Collecter les diagnostics dans les conteneurs

Les outils de diagnostic utilisés dans les environnements Linux non conteneurs peuvent également être utilisés pour [collecter les diagnostics dans des conteneurs](diagnostics-in-containers.md). Il n’y a que quelques modifications d’utilisation nécessaires pour s’assurer que les outils fonctionnent dans un conteneur d’ancrage.

## <a name="net-core-diagnostic-global-tools"></a>Outils globaux de diagnostic .NET Core

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-Counters](dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau. Il observe les valeurs de compteur de performance publiées par le biais de l' <xref:System.Diagnostics.Tracing.EventCounter> API. Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation du processeur ou le taux d’exceptions levées dans votre application .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

L’outil [dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les vidages noyau Windows et Linux sans débogueur natif.

### <a name="dotnet-gcdump"></a>dotnet-gcdump

L’outil [dotnet-gcdump](dotnet-gcdump.md) est un moyen de collecter des vidages de mémoire GC (garbage collector) des processus .net en direct.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core comprend ce qui est appelé `EventPipe` par le biais duquel les données de diagnostic sont exposées. L’outil [dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes à partir de votre application, ce qui peut aider dans les scénarios où vous devez provoquer une exécution lente des applications.

### <a name="dotnet-symbol"></a>dotnet-symbol

[dotnet-Symbol télécharge des](dotnet-symbol.md) fichiers (symboles, DAC/DBI, fichiers hôtes, etc.) nécessaires à l’ouverture d’un vidage principal ou d’un minidump. Utilisez cet outil si vous avez besoin de symboles et de modules pour déboguer un fichier de vidage capturé sur un autre ordinateur.

### <a name="dotnet-sos"></a>dotnet-sos

[dotnet-SOS](dotnet-sos.md) installe l' [extension de débogage SOS](sos-debugging-extension.md) sur Linux et MacOS (et sur Windows si vous utilisez [WinDbg/CDB](/windows-hardware/drivers/debugger/debugger-download-tools)).

### <a name="perfcollect"></a>PerfCollect

[PerfCollect](trace-perfcollect-lttng.md) est un script bash que vous pouvez utiliser pour collecter des traces avec `perf` et `LTTng` pour une analyse des performances plus approfondie des applications .net s’exécutant sur des distributions Linux.

## <a name="net-core-diagnostics-tutorials"></a>Tutoriels de diagnostics .NET Core

### <a name="debug-a-memory-leak"></a>Déboguer une fuite de mémoire

[Didacticiel : déboguer une fuite de mémoire](debug-memory-leak.md) vous guide tout au long de la détection d’une fuite de mémoire. L’outil [dotnet-Counters](dotnet-counters.md) est utilisé pour confirmer la fuite et l’outil [dotnet-dump](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.

### <a name="debug-high-cpu-usage"></a>Déboguer une utilisation élevée du processeur

[Didacticiel : déboguer l’utilisation intensive du processeur](debug-highcpu.md) vous guide tout au long de l’examen de l’utilisation intensive du processeur. Elle utilise l’outil [dotnet-Counters](dotnet-counters.md) pour vérifier l’utilisation intensive du processeur. Il vous guide ensuite dans l’utilisation [de trace for Performance Analysis Utility ( `dotnet-trace` )](dotnet-trace.md) ou Linux `perf` pour collecter et afficher le profil d’utilisation de l’UC.

### <a name="debug-deadlock"></a>Déboguer un interblocage

[Didacticiel : déboguer le blocage](debug-deadlock.md) vous montre comment utiliser l’outil [dotnet-dump](dotnet-dump.md) pour examiner les threads et les verrous.

### <a name="debug-a-stackoverflow"></a>Déboguer StackOverflow

[Didacticiel : déboguer un StackOverflow](debug-stackoverflow.md) montre comment déboguer un <xref:System.StackOverflowException> sur Linux.

### <a name="debug-linux-dumps"></a>Déboguer des vidages Linux

[Déboguer les vidages Linux](debug-linux-dumps.md) explique comment collecter et analyser les vidages sur Linux.

### <a name="measure-performance-using-eventcounters"></a>Mesurer les performances à l’aide de EventCounters

[Didacticiel : mesurer les performances à l’aide de EventCounters dans .net](event-counter-perf.md) montre comment utiliser l' <xref:System.Diagnostics.Tracing.EventCounter> API pour mesurer les performances dans votre application .net.
