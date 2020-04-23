---
title: Workstation vs collecte des ordures serveur (GC)
description: En savoir plus sur la collecte des stations de travail et des ordures serveur dans .NET.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103554"
---
# <a name="workstation-and-server-garbage-collection"></a>Garbage collection de station de travail et de serveur

Le garbage collector s'ajuste automatiquement et peut travailler dans une large gamme de scénarios. Cependant, vous pouvez [définir le type de collecte des ordures](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) en fonction des caractéristiques de la charge de travail. Le CLR fournit les types de garbage collection suivants :

- Collecte des ordures de poste de travail (GC), qui est conçu pour les applications client. C’est la saveur GC par défaut pour les applications autonomes. Pour les applications hébergées, par exemple, celles hébergées par ASP.NET, l’hôte détermine la saveur GC par défaut.

  Le garbage collection de station de travail peut être simultané ou non simultané. La collecte simultanée (ou *de fond)* des ordures permet aux threads gérés de poursuivre leurs opérations lors d’une collecte des ordures. [La collecte des ordures de fond](background-gc.md) remplace la collecte [simultanée des ordures](background-gc.md#concurrent-garbage-collection) dans .NET Framework 4 et les versions ultérieures.

- Garbage collection de serveur, prévu pour les applications serveur qui ont besoin d'un débit et d'une extensibilité.

  - Dans .NET Core, la collecte des ordures du serveur peut être non simultanée ou arrière-plan.

  - Dans .NET Framework 4.5 et les versions ultérieures, la collecte des ordures du serveur peut être non simultanée ou arrière-plan. Dans .NET Framework 4 et les versions précédentes, la collecte des ordures du serveur n’est pas simultanée.

L’illustration suivante montre les fils dédiés qui effectuent la collecte des ordures sur un serveur :

![Threads de garbage collection du serveur](./media/gc-server.png)

## <a name="performance-considerations"></a>Considérations relatives aux performances

### <a name="workstation-gc"></a>Garbage collector pour station de travail

Voici les considérations liées aux threads et aux performances pour le garbage collection de station de travail :

- La collecte se produit sur le thread utilisateur qui a déclenché le garbage collection et reste à la même priorité. Étant donné que les threads utilisateur sont généralement exécutés à la priorité normale, le garbage collector (qui s'exécute sur un thread de priorité normale) doit rivaliser avec d'autres threads pour le temps processeur. (Les fils qui exécutent le code natif ne sont pas suspendus sur le serveur ou la collecte des ordures de poste de travail.)

- La collecte des ordures de poste de travail est toujours utilisée sur un ordinateur qui n’a qu’un seul processeur, quel que soit le réglage de [configuration.](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)

### <a name="server-gc"></a>Garbage collector pour serveur

Voici les considérations liées aux threads et aux performances pour le garbage collection de serveur :

- La collecte se produit sur plusieurs threads dédiés qui s'exécutent au niveau de priorité `THREAD_PRIORITY_HIGHEST` .

- Un tas et un thread dédié pour effectuer le garbage collection sont fournis pour chaque UC, et les tas sont collectés au même moment. Chaque tas contient un tas de petits objets et un tas d'objets volumineux, et tous les tas peuvent faire l'objet d'accès par du code utilisateur. Les objets des différents tas peuvent faire référence les uns aux autres.

- Étant donné que plusieurs threads de garbage collection fonctionnent ensemble, le garbage collection de serveur est plus rapide que le garbage collection de station de travail sur un tas de même taille.

- Le garbage collection de serveur présente souvent des segments de plus grande taille. Cependant, il ne s’agit que d’une généralisation : la taille du segment est spécifique à la mise en œuvre et peut être modifiée. Ne faites pas d’hypothèses sur la taille des segments attribués par le collecteur d’ordures lors de l’accordage de votre application.

- Le garbage collection de serveur peut consommer beaucoup de ressources. Par exemple, imaginez qu’il existe 12 processus qui utilisent le serveur GC fonctionnant sur un ordinateur qui a quatre processeurs. Si tous les processus se produisent pour ramasser les ordures en même temps, ils interfèrent les uns avec les autres, car il y aurait 12 threads prévus sur le même processeur. Si les processus sont actifs, ce n’est pas une bonne idée de les avoir tous utiliser serveur GC.

Si vous exécutez des centaines d’instances d’une application, envisagez d’utiliser la collecte des ordures de poste de travail avec la collecte simultanée des ordures désactivées. Cela provoquera moins de changements de contexte, ce qui peut améliorer les performances.

## <a name="see-also"></a>Voir aussi

- [Collecte des ordures de fond](background-gc.md)
- [Options de configuration en temps d’exécution pour la collecte des ordures](../../core/run-time-config/garbage-collector.md)
