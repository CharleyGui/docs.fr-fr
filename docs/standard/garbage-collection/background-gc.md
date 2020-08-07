---
title: garbage collection d’arrière-plan
description: En savoir plus sur les garbage collection d’arrière-plan dans .NET et sur leur différence dans les garbage collection de station de travail et de serveur.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: bf88c14b2aeed94a548b6116749fa8669576afe1
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916999"
---
# <a name="background-garbage-collection"></a>garbage collection d’arrière-plan

En arrière-plan garbage collection (GC), les générations éphémères (0 et 1) sont collectées si nécessaire, tandis que la collection de génération 2 est en cours. L’garbage collection d’arrière-plan est exécuté sur un ou plusieurs threads dédiés, selon qu’il s’agit de l’arrière-plan ou du garbage collector du serveur, et s’applique uniquement aux collections de génération 2.

L’garbage collection d’arrière-plan est activé par défaut. Il peut être activé ou désactivé à l’aide du paramètre de configuration [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) dans .NET Framework applications ou du paramètre [System. gc. concurrent](../../core/run-time-config/garbage-collector.md#background-gc) dans les applications .net Core et .net 5 et versions ultérieures.

> [!NOTE]
> L’garbage collection d’arrière-plan remplace la [garbage collection simultanée](#concurrent-garbage-collection) et est disponible dans .NET Framework 4 et versions ultérieures. Dans .NET Framework 4, il est pris en charge uniquement pour les garbage collection de *station de travail* . À compter de .NET Framework 4,5, le garbage collection d’arrière-plan est disponible pour les garbage collection de *station de travail* et de *serveur* .

Une collection sur les générations éphémères au cours de la garbage collection d’arrière-plan est appelée garbage collection de *premier plan* . Lorsque des opérations garbage collection de premier plan ont lieu, tous les threads managés sont suspendus.

Lorsque garbage collection d’arrière-plan est en cours et que vous avez alloué assez d’objets dans la génération 0, le CLR effectue une garbage collection de premier plan de génération 0 ou 1. Le thread de garbage collection d'arrière-plan dédié vérifie des points sécurisés fréquents de façon à déterminer s'il existe une demande de garbage collection de premier plan. Le cas échéant, la collecte d'arrière-plan s'interrompt afin que le garbage collection de premier plan puisse se produire. Une fois le garbage collection de premier plan terminé, l’arrière-plan dédié garbage collection threads et les threads utilisateur reprennent.

Le garbage collection d'arrière-plan supprime les restrictions d'allocation imposées par le garbage collection simultané, car des opérations garbage collection éphémères peuvent se produire pendant le garbage collection d'arrière-plan. L’garbage collection d’arrière-plan peut supprimer des objets morts dans les générations éphémères. Il peut également développer le tas si nécessaire pendant une garbage collection de la génération 1.

## <a name="background-workstation-vs-server-gc"></a>Station de travail en arrière-plan et GC de serveur

À compter de .NET Framework 4,5, le garbage collection d’arrière-plan est disponible pour le garbage collection de serveur. Le GC d’arrière-plan est le mode par défaut pour le garbage collection serveur.

Le serveur d’arrière-plan garbage collection fonctionne de la même façon que les garbage collection de station de travail en arrière-plan, mais il existe quelques différences :

- La station de travail en arrière-plan garbage collection utilise un thread d’arrière-plan garbage collection dédié, tandis que le serveur d’arrière-plan garbage collection utilise plusieurs En règle générale, il existe un thread dédié pour chaque processeur logique.

- Contrairement au thread d’arrière-plan de station de travail garbage collection, les threads GC du serveur d’arrière-plan n’expirent pas.

L’illustration suivante montre les garbage collection de *station de travail* en arrière-plan effectuées sur un thread distinct dédié :

![Nettoyage de la mémoire de la station de travail en arrière-plan](media/fundamentals/background-workstation-garbage-collection.png)

L’illustration suivante montre les garbage collection de *serveur* d’arrière-plan effectuées sur des threads distincts et dédiés :

![Nettoyage de la mémoire du serveur en arrière-plan](media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Garbage collection simultané

> [!TIP]
> Cette section s’applique à :
>
> - .NET Framework 3,5 et versions antérieures pour stations de travail garbage collection
> - .NET Framework 4 et versions antérieures pour le serveur garbage collection
>
> Le garbage collection simultané est remplacé par le garbage collection d’arrière-plan dans les versions ultérieures.

Dans les garbage collection de station de travail ou de serveur, vous pouvez [activer des garbage collection simultanées](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), ce qui permet aux threads de s’exécuter simultanément avec un thread dédié qui exécute le garbage collection pour la majeure partie de la durée de la collection. Cette option affecte uniquement les garbage collections de génération 2. les générations 0 et 1 sont toujours non simultanées car elles se terminent rapidement.

Le garbage collection simultané permet aux applications interactives d'être plus réactives en réduisant les pauses d'une collection. Les threads managés peuvent continuer à s'exécuter une grande partie de la durée du garbage collection simultané. Cette conception produit des pauses plus courtes pendant qu’un garbage collection se produit.

Le garbage collection simultané est exécuté sur un thread dédié. Par défaut, le CLR exécute des garbage collection de station de travail avec des garbage collection simultanées activées sur des ordinateurs monoprocesseurs et multiprocesseurs.

L'illustration suivante montre le garbage collection simultané exécuté sur un thread dédié différent.

![Threads de nettoyage de la mémoire simultanés](media/gc-concurrent.png)

## <a name="see-also"></a>Voir aussi

- [Garbage collection de station de travail et de serveur](workstation-server-gc.md)
- [Options de configuration au moment de l’exécution pour garbage collection](../../core/run-time-config/garbage-collector.md)
