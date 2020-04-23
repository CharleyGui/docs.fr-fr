---
title: Collecte des ordures de fond
description: Découvrez la collecte des ordures de fond dans .NET et comment il diffère dans la station de travail et la collecte des ordures serveur.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103561"
---
# <a name="background-garbage-collection"></a>Collecte des ordures de fond

En arrière-plan de collecte des ordures (GC), les générations éphémères (0 et 1) sont collectées au besoin alors que la collecte de la génération 2 est en cours. La collecte des ordures de fond est effectuée sur un ou plusieurs threads dédiés, selon qu’il s’agit de l’arrière-plan ou du serveur GC, et ne s’applique qu’aux collections de génération 2.

La collecte des ordures de fond est activée par défaut. Il peut être activé ou désactivé avec le paramètre de configuration [GCConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) dans les applications .NET Framework ou le paramètre [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) dans les applications .NET Core.

> [!NOTE]
> La collecte des ordures de fond remplace [la collecte simultanée des ordures](#concurrent-garbage-collection) et est disponible dans .NET Framework 4 et les versions ultérieures. Dans .NET Framework 4, il n’est pris en charge que pour la collecte des ordures de poste de *travail.* En commençant par .NET Framework 4.5, la collecte des ordures de fond est disponible pour la collecte des ordures *de poste de travail* et de *serveur.*

Une collection sur les générations éphémères pendant la collecte des ordures de fond est connue sous le nom de collecte des ordures *de premier plan.* Lorsque des opérations garbage collection de premier plan ont lieu, tous les threads managés sont suspendus.

Lorsque la collecte des ordures de fond est en cours et que vous avez alloué suffisamment d’objets en génération 0, le CLR effectue une collecte des ordures de première génération ou de génération 1. Le thread de garbage collection d'arrière-plan dédié vérifie des points sécurisés fréquents de façon à déterminer s'il existe une demande de garbage collection de premier plan. Le cas échéant, la collecte d'arrière-plan s'interrompt afin que le garbage collection de premier plan puisse se produire. Une fois la collecte des ordures au premier plan terminée, les fils de collecte des ordures de fond et les fils d’utilisateur reprennent.

Le garbage collection d'arrière-plan supprime les restrictions d'allocation imposées par le garbage collection simultané, car des opérations garbage collection éphémères peuvent se produire pendant le garbage collection d'arrière-plan. La collecte des ordures de fond peut enlever des objets morts dans des générations éphémères. Il peut également étendre le tas si nécessaire au cours d’une collecte des ordures de génération 1.

## <a name="background-workstation-vs-server-gc"></a>Poste de travail d’arrière-plan vs serveur GC

En commençant par .NET Framework 4.5, la collecte des ordures de fond est disponible pour le serveur GC. Background GC est le mode par défaut pour la collecte des ordures du serveur.

Fonctions de collecte des ordures du serveur de fond de la même façon que la collecte des ordures de poste de travail de fond, mais il y a quelques différences :

- La collecte des ordures de poste de travail de fond utilise un fil de collecte d’ordures de fond dédié, tandis que la collecte des ordures de serveur d’arrière-plan utilise plusieurs fils. Typiquement, il ya un thread dédié pour chaque processeur logique.

- Contrairement au fil de collecte des ordures de fond de poste de travail, les fils GC serveur d’arrière-plan ne s’arrêtent pas.

L’illustration suivante montre la collecte des ordures *de poste de travail* de fond effectuée sur un fil distinct et dédié :

![Nettoyage de la mémoire de la station de travail en arrière-plan](./media/fundamentals/background-workstation-garbage-collection.png)

L’illustration suivante montre la collecte des ordures *du serveur* de fond effectuée sur des fils distincts et dédiés :

![Nettoyage de la mémoire du serveur en arrière-plan](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Garbage collection simultané

> [!TIP]
> Cette section s’applique à :
>
> - .NET Framework 3.5 et plus tôt pour la collecte des ordures de poste de travail
> - .NET Framework 4 et plus tôt pour la collecte des ordures du serveur
>
> Les déchets concomitants sont remplacés par la collecte des ordures de fond dans les versions ultérieures.

Dans le poste de travail ou la collecte des ordures serveur, vous pouvez activer la [collecte simultanée des ordures](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), ce qui permet aux threads de fonctionner en même temps qu’un fil dédié qui effectue la collecte des ordures pendant la majeure partie de la durée de la collecte. Cette option n’affecte que les collectes d’ordures de la génération 2; générations 0 et 1 sont toujours non-concurrentes parce qu’elles finissent rapidement.

Le garbage collection simultané permet aux applications interactives d'être plus réactives en réduisant les pauses d'une collection. Les threads managés peuvent continuer à s'exécuter une grande partie de la durée du garbage collection simultané. Cela génère des pauses plus courtes pendant l'opération garbage collection.

Le garbage collection simultané est exécuté sur un thread dédié. Par défaut, le CLR effectue la collecte des ordures de poste de travail avec la collecte simultanée des ordures activées sur les ordinateurs à processeur unique et multi-processeurs.

L'illustration suivante montre le garbage collection simultané exécuté sur un thread dédié différent.

![Threads de nettoyage de la mémoire simultanés](./media/gc-concurrent.png)

## <a name="see-also"></a>Voir aussi

- [Garbage collection de station de travail et de serveur](workstation-server-gc.md)
- [Options de configuration en temps d’exécution pour la collecte des ordures](../../core/run-time-config/garbage-collector.md)
