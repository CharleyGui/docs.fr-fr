---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.topic: overview
ms.openlocfilehash: c0a45a1bfe866ad42890db576b5dd5098b1dbc3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318350"
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

### <a name="dotnet-counters"></a>dotnet-compteurs

[dotnet-Counters](dotnet-counters.md) est un outil d’analyse des performances pour l’analyse de l’intégrité et des performances de premier niveau. Il observe les valeurs de compteur de performance publiées via l’API <xref:System.Diagnostics.Tracing.EventCounter>. Par exemple, vous pouvez rapidement surveiller des éléments tels que l’utilisation du processeur ou le taux d’exceptions levées dans votre application .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

L’outil [dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les vidages noyau Windows et Linux sans débogueur natif.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core comprend ce qui est appelé le `EventPipe` par le biais duquel les données de diagnostic sont exposées. L’outil [dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes à partir de votre application, ce qui peut aider dans les scénarios où vous devez provoquer une exécution lente des applications.
