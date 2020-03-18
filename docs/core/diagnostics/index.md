---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399048"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quels sont les outils de diagnostic disponibles dans .NET Core ?

Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.

Cet article vous aide à trouver les différents outils dont vous avez besoin.

## <a name="managed-debuggers"></a>Débogueurs gérés

[Les débbuggeurs gérés](managed-debuggers.md) vous permettent d’interagir avec votre programme. La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code. Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.

## <a name="logging-and-tracing"></a>Journalisation et suivi

[L’exploitation forestière et le traçage](logging-tracing.md) sont des techniques connexes. Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux. Les fichiers consignent le détail des tâches exécutées par un programme. Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes. Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.

## <a name="unit-testing"></a>Test des unités

[Le test unitaire](../testing/index.md) est un élément clé de l’intégration continue et du déploiement de logiciels de haute qualité. Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.

## <a name="net-core-dotnet-diagnostic-global-tools"></a>.NET Core dotnet diagnostic Global Tools

### <a name="dotnet-counters"></a>dotnet-counters

[dotnet-counters](dotnet-counters.md) est un outil de surveillance des performances pour la surveillance de la santé de premier niveau et l’enquête sur le rendement. Il observe les valeurs de <xref:System.Diagnostics.Tracing.EventCounter> compteur de performance publiées via l’API. Par exemple, vous pouvez surveiller rapidement des choses comme l’utilisation du processeur ou le taux d’exceptions jetés dans votre application .NET Core.

### <a name="dotnet-dump"></a>dotnet-dump

[L’outil dotnet-dump](dotnet-dump.md) est un moyen de collecter et d’analyser les décharges de base de Windows et Linux sans un débbugger indigène.

### <a name="dotnet-trace"></a>dotnet-trace

.NET Core comprend ce `EventPipe` qu’on appelle le moyen par lequel les données diagnostiques sont exposées. [L’outil dotnet-trace](dotnet-trace.md) vous permet de consommer des données de profilage intéressantes de votre application qui peuvent vous aider dans les scénarios où vous devez provoquer des applications qui fonctionnent lentement.

## <a name="net-core-diagnostics-tutorials"></a>Tutoriels de diagnostics .NET Core

### <a name="debug-a-memory-leak"></a>Déboguer une fuite de mémoire

[Tutorial: Debug une fuite de mémoire](debug-memory-leak.md) marche à travers la recherche d’une fuite de mémoire. [L’outil dotnet-compteurs](dotnet-counters.md) est utilisé pour confirmer la fuite et [l’outil de décharge de dotnet](dotnet-dump.md) est utilisé pour diagnostiquer la fuite.
