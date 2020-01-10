---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715578"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quels sont les outils de diagnostic disponibles dans .NET Core ?

Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.

Cet article vous aide à trouver les différents outils dont vous avez besoin.

## <a name="managed-debuggers"></a>Débogueurs gérés

Les [débogueurs managés](managed-debuggers.md) vous permettent d’interagir avec votre programme. La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code. Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.

## <a name="logging-and-tracing"></a>Journalisation et suivi

La [journalisation et le suivi](logging-tracing.md) sont des techniques associées. Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux. Les fichiers consignent le détail des tâches exécutées par un programme. Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes. Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.

## <a name="unit-testing"></a>Test unitaire

Le [test unitaire](../testing/index.md) est un composant clé de l’intégration et du déploiement continus de logiciels de haute qualité. Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>Outils globaux .NET Core dotnet diagnostic

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-Counters](dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau. Il observe les valeurs de compteur de performance publiées via l’API <xref:System.Diagnostics.Tracing.EventCounter>. Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation du processeur ou le taux d’exceptions levées dans votre application .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

L’outil [dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les vidages noyau Windows et Linux sans débogueur natif.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core comprend ce qui est appelé le `EventPipe` par le biais duquel les données de diagnostic sont exposées. L’outil [dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes à partir de votre application, ce qui peut aider dans les scénarios où vous devez provoquer une exécution lente des applications.

## <a name="net-core-diagnostics-tutorials"></a>Tutoriels de diagnostics .NET Core

### <a name="debug-a-memory-leak"></a>Déboguer une fuite de mémoire

[Didacticiel : déboguer une fuite de mémoire](debug-memory-leak.md) vous guide tout au long de la détection d’une fuite de mémoire. L’outil [dotnet-Counters](dotnet-counters.md) est utilisé pour confirmer la fuite et l’outil [dotnet-dump](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.
