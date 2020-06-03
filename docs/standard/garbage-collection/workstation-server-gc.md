---
title: Station de travail et garbage collection serveur (GC)
description: En savoir plus sur les garbage collection de station de travail et de serveur dans .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 5ff2b1fe2f997913e071f35ec5abb167ed757608
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306693"
---
# <a name="workstation-and-server-garbage-collection"></a>Garbage collection de station de travail et de serveur

Le garbage collector s'ajuste automatiquement et peut travailler dans une large gamme de scénarios. Toutefois, vous pouvez [définir le type de garbage collection](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) en fonction des caractéristiques de la charge de travail. Le CLR fournit les types de garbage collection suivants :

- Station de travail garbage collection (GC), conçue pour les applications clientes. Il s’agit de la version de catalogue global par défaut pour les applications autonomes. Pour les applications hébergées, par exemple, celles hébergées par ASP.NET, l’hôte détermine la version GC par défaut.

  Le garbage collection de station de travail peut être simultané ou non simultané. La garbage collection simultanée (ou d' *arrière-plan*) permet aux threads managés de continuer à fonctionner pendant une garbage collection. L' [garbage collection d’arrière-plan](background-gc.md) remplace les [garbage collection simultanées](background-gc.md#concurrent-garbage-collection) dans .NET Framework 4 et versions ultérieures.

- Garbage collection de serveur, prévu pour les applications serveur qui ont besoin d'un débit et d'une extensibilité.

  - Dans .NET Core, les garbage collection serveur peuvent être non simultanés ou en arrière-plan.

  - Dans .NET Framework 4,5 et versions ultérieures, le garbage collection de serveur peut être non simultané ou en arrière-plan. Dans .NET Framework 4 et versions antérieures, le garbage collection de serveur n’est pas simultané.

L’illustration suivante montre les threads dédiés qui exécutent les garbage collection sur un serveur :

![Threads de garbage collection du serveur](media/gc-server.png)

## <a name="performance-considerations"></a>Considérations relatives aux performances

### <a name="workstation-gc"></a>Garbage collector pour station de travail

Voici les considérations liées aux threads et aux performances pour le garbage collection de station de travail :

- La collecte se produit sur le thread utilisateur qui a déclenché le garbage collection et reste à la même priorité. Étant donné que les threads utilisateur sont généralement exécutés à la priorité normale, le garbage collector (qui s'exécute sur un thread de priorité normale) doit rivaliser avec d'autres threads pour le temps processeur. (Les threads qui exécutent du code natif ne sont pas suspendus sur le serveur ou la station de travail garbage collection.)

- Le garbage collection de station de travail est toujours utilisé sur un ordinateur doté d’un seul processeur, quel que soit le [paramètre de configuration](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

### <a name="server-gc"></a>Garbage collector pour serveur

Voici les considérations liées aux threads et aux performances pour le garbage collection de serveur :

- La collecte se produit sur plusieurs threads dédiés qui s'exécutent au niveau de priorité `THREAD_PRIORITY_HIGHEST` .

- Un tas et un thread dédié pour effectuer le garbage collection sont fournis pour chaque UC, et les tas sont collectés au même moment. Chaque tas contient un tas de petits objets et un tas d'objets volumineux, et tous les tas peuvent faire l'objet d'accès par du code utilisateur. Les objets des différents tas peuvent faire référence les uns aux autres.

- Étant donné que plusieurs threads de garbage collection fonctionnent ensemble, le garbage collection de serveur est plus rapide que le garbage collection de station de travail sur un tas de même taille.

- Le garbage collection de serveur présente souvent des segments de plus grande taille. Toutefois, il ne s’agit que d’une généralisation : la taille de segment est spécifique à l’implémentation et peut faire l’objet de modifications. N’effectuez pas d’hypothèses sur la taille des segments alloués par le garbage collector lors du paramétrage de votre application.

- Le garbage collection de serveur peut consommer beaucoup de ressources. Par exemple, imaginez qu’il y a 12 processus qui utilisent le garbage collector de serveur exécuté sur un ordinateur doté de quatre processeurs. Si tous les processus se produisent pour collecter les opérations de garbage collection en même temps, ils interféreraient entre eux, car 12 threads sont planifiés sur le même processeur. Si les processus sont actifs, il n’est pas judicieux de leur demander d’utiliser le garbage collection de serveur.

Si vous exécutez des centaines d’instances d’une application, envisagez d’utiliser des garbage collection de station de travail avec garbage collection simultanée désactivée. Cela provoquera moins de changements de contexte, ce qui peut améliorer les performances.

## <a name="see-also"></a>Voir aussi

- [garbage collection d’arrière-plan](background-gc.md)
- [Options de configuration au moment de l’exécution pour garbage collection](../../core/run-time-config/garbage-collector.md)
