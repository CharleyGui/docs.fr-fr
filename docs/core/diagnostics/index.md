---
title: Vue d’ensemble des outils de diagnostics - .NET Core
description: Une vue d’ensemble des outils et techniques disponibles pour diagnostiquer les applications .NET Core.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.topic: overview
ms.openlocfilehash: f107d15fa5584bb5a4834b5f11f1096bec7eb749
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68974147"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>Quels sont les outils de diagnostic disponibles dans .NET Core ?

Les logiciels ne se comportent pas toujours comme vous l'attendez, mais .NET Core dispose d’outils et d’API qui vous aideront à diagnostiquer ces problèmes rapidement et efficacement.

Cet article vous aide à trouver les différents outils dont vous avez besoin.

## <a name="managed-debuggersmanaged-debuggersmd"></a>[Débogueurs gérés](managed-debuggers.md)
Les débogueurs gérés vous permettent d'interagir avec votre programme. La pause, l'exécution incrémentale, l'examen et la reprise vous offrent un aperçu du comportement de votre code. Un débogueur est le premier choix pour diagnostiquer les problèmes fonctionnels qui peuvent être facilement reproduits.

## <a name="logging-and-tracinglogging-tracingmd"></a>[Journalisation et suivi](logging-tracing.md)
La journalisation et le suivi sont des techniques connexes. Elles se réfèrent au code d'instrumentation permettant de créer des fichiers journaux. Les fichiers consignent le détail des tâches exécutées par un programme. Ces informations peuvent être utilisées pour diagnostiquer les problèmes les plus complexes. Combinées à l'horodatage, ces techniques sont également très utiles dans les analyses de performances.

## <a name="unit-testingtestingindexmd"></a>[Tests unitaires](../testing/index.md)
Le test unitaire est un élément clé de l'intégration et du déploiement continus de logiciels de haute qualité. Les tests unitaires sont conçus pour vous prévenir d’un problème survenu.
