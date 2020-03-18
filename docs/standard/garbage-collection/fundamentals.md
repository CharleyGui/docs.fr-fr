---
title: Notions de base du garbage collection
description: Découvrez comment fonctionne le récupérateur de mémoire et comment le configurer pour optimiser ses performances.
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400539"
---
# <a name="fundamentals-of-garbage-collection"></a>Notions de base du garbage collection

Dans le langage courant runtime (CLR), le collecteur d’ordures (GC) sert de gestionnaire automatique de mémoire. Elle vous permet de bénéficier des avantages suivants :

- Vous permet de développer votre application sans avoir à libérer manuellement la mémoire.

- Il alloue efficacement les objets sur le tas managé.

- Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets managés obtiennent automatiquement un contenu propre au démarrage, ce qui fait que leurs constructeurs n'ont pas à initialiser chaque champ de données.

- Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.

Cet article décrit les concepts fondamentaux de la collecte des ordures.

## <a name="fundamentals-of-memory"></a>Notions de base de la mémoire

La liste suivante résume les concepts importants de la mémoire CLR.

- Chaque processus possède son propre espace d'adressage virtuel séparé. Tous les processus sur le même ordinateur partagent la même mémoire physique et le fichier de page, s’il y en a un.

- Par défaut, sur les ordinateurs 32 bits, chaque processus a un espace d'adressage virtuel en mode utilisateur de 2 Go.

- En tant que développeur d'applications, vous travaillez uniquement avec l'espace d'adressage virtuel et ne gérez jamais directement la mémoire physique. Le garbage collector alloue et libère la mémoire virtuelle pour vous sur le tas managé.

  Si vous écrivez du code natif, vous utilisez les fonctions Windows pour travailler avec l’espace d’adresse virtuel. Ces fonctions allouent et libèrent la mémoire virtuelle pour vous sur les tas natifs.

- La mémoire virtuelle peut être dans trois états :

  - Libre. Il n'existe aucune référence au bloc de mémoire et celui-ci est disponible pour allocation.

  - Réservé. Le bloc de mémoire est disponible pour votre utilisation et ne peut pas être utilisé pour une autre demande d'allocation. Toutefois, vous ne pouvez pas stocker de données dans ce bloc de mémoire tant qu'il n'est pas validé.

  - Validé. Le bloc de mémoire est assigné au stockage physique.

- L'espace d'adressage virtuel peut être fragmenté. Cela signifie qu'il existe des blocs libres, également appelés trous, dans l'espace d'adressage. Lorsqu'une allocation de mémoire virtuelle est demandée, le gestionnaire de mémoire virtuelle doit rechercher un bloc unique libre suffisamment grand pour satisfaire la demande d'allocation. Même si vous disposez de 2 Go d'espace libre, l'allocation qui requiert 2 Go échoue, sauf si tout cet espace libre est contenu dans un bloc d'adresse unique.

- Vous pouvez manquer de mémoire s’il n’y a pas assez d’espace d’adresse virtuelle pour réserver ou de l’espace physique à engager.

  Le fichier de page est utilisé même si la pression de mémoire physique (c’est-à-dire la demande de mémoire physique) est faible. La première fois que la pression de mémoire physique est élevée, le système d’exploitation doit faire de la place dans la mémoire physique pour stocker des données, et il soutient certaines des données qui sont en mémoire physique au fichier de page. Ces données ne sont pas bipées jusqu’à ce qu’elles soient nécessaires, il est donc possible de rencontrer des paging dans des situations où la pression de mémoire physique est faible.

## <a name="conditions-for-a-garbage-collection"></a>Conditions pour une opération garbage collection

Le garbage collection se produit lorsque l'une des conditions suivantes est vraie :

- Le système possède peu de mémoire physique. Ceci est détecté par la notification à faible mémoire de l’OS ou la mémoire basse comme indiqué par l’hôte.

- La mémoire utilisée par les objets alloués sur le tas managé dépasse un seuil acceptable. Ce seuil est continuellement ajusté à mesure que le processus s'exécute.

- La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée. Dans presque tous les cas, vous n’avez pas à appeler cette méthode, car le garbage collector s’exécute continuellement. Cette méthode est principalement utilisée pour les situations uniques et les tests.

## <a name="the-managed-heap"></a>Tas managé

Une fois que le garbage collector est initialisé par le CLR, il alloue un segment de mémoire pour stocker et gérer des objets. Cette mémoire est appelée tas managé, par opposition à un tas natif dans le système d'exploitation.

Il existe un tas managé pour chaque processus managé. Tous les threads du processus allouent de la mémoire pour les objets sur le même tas.

Pour réserver la mémoire, le collecteur d’ordures appelle la fonction [Windows VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) et réserve un segment de mémoire à la fois pour les applications gérées. Le collecteur d’ordures réserve également des segments, au besoin, et libère des segments de nouveau au système d’exploitation (après les avoir effacés de tous les objets) en appelant la fonction [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) Windows.

> [!IMPORTANT]
> La taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris les mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

Moins il y a d'objets alloués sur le tas, moins le garbage collector a à faire. Lorsque vous allouez des objets, n'utilisez pas de valeurs arrondies qui dépassent vos besoins, par exemple en allouant un tableau de 32 octets lorsque vous avez besoin de seulement 15 octets.

Lorsqu'un garbage collection est déclenché, le garbage collector libère la mémoire occupée par les objets morts. Le processus de libération compacte les objets vivants afin qu'ils soient déplacés ensemble, et l'espace inutilisé est supprimé, ce qui entraîne la diminution du tas. Les objets alloués ensemble restent ainsi ensemble sur le tas managé, pour conserver leur emplacement.

Le déroulement (fréquence et durée) des garbage collection est le résultat du volume des allocations et de la quantité de mémoire restante sur le tas managé.

Le tas peut être considéré comme l’accumulation de deux tas : le [tas de grands objets](large-object-heap.md) et le tas de petits objets.

Le [tas de grands objets](large-object-heap.md) contient des objets d’au moins 85 000 octets. Ces objets du tas d'objets volumineux sont généralement des tableaux. Il est rare qu'un objet d'instance soit extrêmement grand.

> [!TIP]
> Vous pouvez [configurer la taille du seuil](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pour que les objets aillent sur le tas de gros objets.

## <a name="generations"></a>Générations

Le tas est organisé en générations. Il peut ainsi gérer des objets durables et éphémères. Le garbage collection consiste principalement en la récupération d'objets éphémères qui occupent généralement une petite partie du tas. Il existe trois générations d'objets sur le tas :

- **Génération 0**. Il s'agit de la génération la plus jeune, qui contient des objets éphémères. Un exemple d'objet éphémère est une variable temporaire. Le garbage collection a le plus souvent lieu dans cette génération.

  Les objets nouvellement attribués forment une nouvelle génération d’objets et sont implicitement des collections de génération 0. Cependant, s’il s’agit de gros objets, ils vont sur le tas de gros objets dans une collection de génération 2.

  La plupart des objets sont libérés pour l'opération garbage collection dans la génération 0 et ne survivent pas à la génération suivante.

- **Génération 1**. Cette génération contient des objets éphémères et sert de tampon entre objets éphémères et objets durables.

- **Génération 2**. Cette génération contient des objets durables. Un exemple d’objet à longue durée de vie est un objet dans une application serveur qui contient des données statiques qui sont en direct pendant toute la durée du processus.

Les opérations garbage collection se produisent sur des générations spécifiques, selon les conditions spécifiées. La collecte d'une génération signifie la collecte des objets de cette génération et de toutes ses générations plus jeunes. Les opérations garbage collection de génération 2 sont également appelées garbage collection complet, car elles libèrent tous les objets de toutes les générations (autrement dit, tous les objets du tas managé).

### <a name="survival-and-promotions"></a>Survie et promotions

Les objets qui ne sont pas récupérés dans une collecte des ordures sont connus sous le nom de survivants et sont promus à la prochaine génération. Les objets qui survivent à un garbage collection de génération 0 sont promus à la génération 1, les objets qui survivent à un garbage collection de génération 1 sont promus à la génération 2 et les objets qui survivent à un garbage collection de génération 2 restent dans la génération 2.

Lorsque le éboueur détecte que le taux de survie est élevé en une génération, il augmente le seuil d’allocation pour cette génération. La collection suivante reçoit une taille substantielle de mémoire récupérée. Le CLR équilibre continuellement deux priorités : ne pas laisser l’ensemble de travail d’une application devenir trop grand en retardant la collecte des ordures et en ne laissant pas la collecte des ordures fonctionner trop fréquemment.

### <a name="ephemeral-generations-and-segments"></a>Segments et générations éphémères

Étant donné que les objets des générations 0 et 1 sont éphémères, ces générations sont appelées générations éphémères.

Les générations éphémères doivent être allouées dans le segment de mémoire appelé segment éphémère. Chaque nouveau segment acquis par le garbage collector devient le nouveau segment éphémère et contient les objets qui ont survécu à un garbage collection de génération 0. L'ancien segment éphémère devient le nouveau segment de génération 2.

La taille du segment éphémère varie selon qu’un système est 32 ou 64 bits, et sur le type de collecteur d’ordures qu’il est en cours d’exécution. Le tableau ci-dessous répertorie les valeurs par défaut.

||32 bits|64 bits|
|-|-------------|-------------|
|Garbage collector pour station de travail|16 Mo|256 octets|
|Garbage collector pour serveur|64 Mo|4 Go|
|Garbage collector pour serveur > 4 processeurs logiques|32 Mo|2 Go|
|Garbage collector pour serveur > 8 processeurs logiques|16 Mo|1 Go|

Le segment éphémère peut inclure des objets de la génération 2. Les objets de génération 2 peuvent utiliser plusieurs segments (autant que votre processus en requiert et que la mémoire en autorise).

La quantité de mémoire libérée à partir d'un garbage collection éphémère est limitée à la taille du segment éphémère. La quantité de mémoire libérée est proportionnelle à l'espace occupé par les objets morts.

## <a name="what-happens-during-a-garbage-collection"></a>Déroulement d’une opération garbage collection

Une opération garbage collection présente les phases suivantes :

- Une phase de marquage qui recherche et crée une liste de tous les objets actifs.

- Une phase de déplacement qui met à jour les références aux objets qui seront compactés.

- Une phase de compactage qui libère l'espace occupé par les objets morts et compacte les objets survivants. La phase de compactage déplace les objets qui ont survécu à un garbage collection vers l'extrémité la plus ancienne du segment.

  Étant donné que les collections de génération 2 peuvent occuper plusieurs segments, les objets promus dans la génération 2 peuvent être déplacés dans un segment plus ancien. Les survivants des générations 1 et 2 peuvent être déplacés vers un autre segment, car ils sont promus à la génération 2.

  Normalement, le grand tas d’objets (LOH) n’est pas compacté, car la copie de gros objets impose une pénalité de performance. Cependant, dans .NET Core et en .NET Framework 4.5.1 et plus tard, vous pouvez utiliser la <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> propriété pour compacter le tas de gros objets sur demande. En outre, le LOH est automatiquement compacté lorsqu’une limite dure est définie en spécifiant soit :

  - une limite de mémoire sur un conteneur, ou
  - les options de configuration [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) ou [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

Le garbage collector utilise les informations suivantes pour déterminer si les objets sont vivants :

- **Empiler les racines**. Variables de pile fournies par le compilateur juste-à-temps (JIT) et l'explorateur de pile. Les optimisations JIT peuvent allonger ou raccourcir les régions de code dans lesquelles les variables de pile sont signalées au collecteur d’ordures.

- **Poignées de collecte des ordures**. Handles qui pointent vers les objets managés qui peuvent être alloués par le code utilisateur ou par le Common Language Runtime.

- **Données statiques**. Objets statiques des domaines d'application qui pourraient référencer d'autres objets. Chaque domaine d'application effectue le suivi de ses objets statiques.

Avant qu'une opération garbage collection ne démarre, tous les threads managés sont suspendus à l'exception du thread qui a déclenché l'opération.

L'illustration suivante montre un thread qui déclenche un garbage collection et entraîne l'interruption des autres threads.

![Lorsqu'un thread déclenche un nettoyage de la mémoire](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipuler les ressources non manipulées

Si les objets gérés font référence à des objets non gérés en utilisant leurs poignées de fichiers indigènes, vous devez libérer explicitement les objets non gérés, parce que le collecteur d’ordures ne suit la mémoire que sur le tas géré.

Les utilisateurs de l’objet géré ne peuvent pas disposer des ressources indigènes utilisées par l’objet. Pour effectuer le nettoyage, vous pouvez rendre l’objet géré finalisé. La finalisation consiste en des actions de nettoyage qui s’exécutent lorsque l’objet n’est plus utilisé. Lorsque l’objet géré meurt, il effectue des actions de nettoyage qui sont spécifiées dans sa méthode de finalisateur.

Lorsqu'un objet finalisable est détecté comme étant mort, son finaliseur est placé dans une file d'attente afin que ses actions de nettoyage soient exécutées, mais l'objet lui-même est promu à la génération suivante. Par conséquent, vous devez attendre jusqu'au garbage collection suivant sur cette génération (qui n'est pas nécessairement le garbage collection suivant) pour déterminer si l'objet a été récupéré.

Pour plus d’informations <xref:System.Object.Finalize?displayProperty=nameWithType>sur la finalisation, voir .

## <a name="workstation-and-server-garbage-collection"></a>Garbage collection de station de travail et de serveur

Le garbage collector s'ajuste automatiquement et peut travailler dans une large gamme de scénarios. Vous pouvez utiliser un [paramètre de fichiers](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) de configuration pour définir le type de collecte des ordures en fonction des caractéristiques de la charge de travail. Le CLR fournit les types de garbage collection suivants :

- La collecte des ordures de poste de travail (GC) est conçue pour les applications client. C’est la saveur GC par défaut pour les applications autonomes. Pour les applications hébergées, par exemple, celles hébergées par ASP.NET, l’hôte détermine la saveur GC par défaut.

  Le garbage collection de station de travail peut être simultané ou non simultané. Le garbage collection simultané permet aux threads managés de continuer à fonctionner pendant un garbage collection. [La collecte des ordures de fond](#background-workstation-garbage-collection) remplace la collecte [simultanée des ordures](#concurrent-garbage-collection) dans .NET Framework 4 et les versions ultérieures.

- Garbage collection de serveur, prévu pour les applications serveur qui ont besoin d'un débit et d'une extensibilité.

  - Dans .NET Core, la collecte des ordures du serveur peut être non simultanée ou arrière-plan.

  - Dans .NET Framework 4.5 et les versions ultérieures, la collecte des ordures du serveur peut être non simultanée ou arrière-plan (la collecte des ordures de fond remplace la collecte simultanée des ordures). Dans .NET Framework 4 et les versions précédentes, la collecte des ordures du serveur n’est pas simultanée.

L’illustration suivante montre les fils dédiés qui effectuent la collecte des ordures sur un serveur :

![Threads de garbage collection du serveur](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Comparez la station de travail et la collecte des ordures des serveurs

Voici les considérations liées aux threads et aux performances pour le garbage collection de station de travail :

- La collecte se produit sur le thread utilisateur qui a déclenché le garbage collection et reste à la même priorité. Étant donné que les threads utilisateur sont généralement exécutés à la priorité normale, le garbage collector (qui s'exécute sur un thread de priorité normale) doit rivaliser avec d'autres threads pour le temps processeur. (Les fils qui exécutent le code natif ne sont pas suspendus sur le serveur ou la collecte des ordures de poste de travail.)

- La collecte des ordures de poste de travail est toujours utilisée sur un ordinateur qui n’a qu’un seul processeur, quel que soit le réglage de [configuration.](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)

Voici les considérations liées aux threads et aux performances pour le garbage collection de serveur :

- La collecte se produit sur plusieurs threads dédiés qui s'exécutent au niveau de priorité `THREAD_PRIORITY_HIGHEST` .

- Un tas et un thread dédié pour effectuer le garbage collection sont fournis pour chaque UC, et les tas sont collectés au même moment. Chaque tas contient un tas de petits objets et un tas d'objets volumineux, et tous les tas peuvent faire l'objet d'accès par du code utilisateur. Les objets des différents tas peuvent faire référence les uns aux autres.

- Étant donné que plusieurs threads de garbage collection fonctionnent ensemble, le garbage collection de serveur est plus rapide que le garbage collection de station de travail sur un tas de même taille.

- Le garbage collection de serveur présente souvent des segments de plus grande taille. Cependant, il ne s’agit que d’une généralisation : la taille du segment est spécifique à la mise en œuvre et peut être modifiée. Ne faites pas d’hypothèses sur la taille des segments attribués par le collecteur d’ordures lors de l’accordage de votre application.

- Le garbage collection de serveur peut consommer beaucoup de ressources. Par exemple, imaginez qu’il existe 12 processus qui utilisent le serveur GC fonctionnant sur un ordinateur qui a 4 processeurs. Si tous les processus se produisent pour ramasser les ordures en même temps, ils interfèrent les uns avec les autres, car il y aurait 12 threads prévus sur le même processeur. Si les processus sont actifs, ce n’est pas une bonne idée de les avoir tous utiliser serveur GC.

Si vous exécutez des centaines d’instances d’une application, envisagez d’utiliser la collecte des ordures de poste de travail avec la collecte simultanée des ordures désactivées. Cela provoquera moins de changements de contexte, ce qui peut améliorer les performances.

## <a name="background-workstation-garbage-collection"></a>Nettoyage de la mémoire de la station de travail en arrière-plan

Dans la collecte des ordures de poste de travail de fond, les générations éphémères (0 et 1) sont collectées au besoin pendant que la collecte de la génération 2 est en cours. La collecte des ordures de poste de travail de fond est effectuée sur un fil dédié et ne s’applique qu’aux collections de génération 2.

La collecte des ordures de fond est activée par défaut et peut être activée ou désactivée avec le paramètre de configuration [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) dans les applications .NET Framework ou le paramètre [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) dans les applications .NET Core.

> [!NOTE]
> La collecte des ordures de fond remplace [la collecte simultanée des ordures](#concurrent-garbage-collection) et est disponible dans .NET Framework 4 et les versions ultérieures. Dans .NET Framework 4, il n’est pris en charge que pour la collecte des ordures de poste de travail. En commençant par .NET Framework 4.5, la collecte des ordures de fond est disponible pour la collecte des ordures de poste de travail et de serveur.

Une collecte sur des générations éphémères pendant le garbage collection d'arrière-plan est appelée garbage collection de premier plan. Lorsque des opérations garbage collection de premier plan ont lieu, tous les threads managés sont suspendus.

Lorsque la collecte des ordures de fond est en cours et que vous avez alloué suffisamment d’objets en génération 0, le CLR effectue une collecte des ordures de première génération ou de génération 1. Le thread de garbage collection d'arrière-plan dédié vérifie des points sécurisés fréquents de façon à déterminer s'il existe une demande de garbage collection de premier plan. Le cas échéant, la collecte d'arrière-plan s'interrompt afin que le garbage collection de premier plan puisse se produire. Une fois le garbage collection de premier plan terminé, le thread de garbage collection d'arrière-plan dédié et les threads utilisateur reprennent.

Le garbage collection d'arrière-plan supprime les restrictions d'allocation imposées par le garbage collection simultané, car des opérations garbage collection éphémères peuvent se produire pendant le garbage collection d'arrière-plan. La collecte des ordures de fond peut enlever des objets morts dans des générations éphémères. Il peut également étendre le tas si nécessaire au cours d’une collecte des ordures de génération 1.

L’illustration suivante montre le nettoyage de la mémoire en arrière-plan effectué sur un thread dédié distinct, sur une station de travail :

![Nettoyage de la mémoire de la station de travail en arrière-plan](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Nettoyage de la mémoire du serveur en arrière-plan

À partir de .NET Framework 4.5, la collecte des ordures serveur d’arrière-plan est le mode par défaut pour la collecte des ordures du serveur.

Fonctions de collecte des ordures du serveur de fond de la même façon que la collecte des ordures de poste de travail de fond, décrite dans la section précédente, mais il y a quelques différences :

- La collecte des ordures de poste de travail de fond utilise un fil de collecte d’ordures de fond dédié, tandis que la collecte des ordures de serveur d’arrière-plan utilise plusieurs fils. Typiquement, il ya un thread dédié pour chaque processeur logique.

- Contrairement au thread du garbage collection de station de travail en arrière-plan, ces threads n'expirent pas.

L’illustration suivante montre le nettoyage de la mémoire en arrière-plan effectué sur un thread dédié distinct, sur un serveur :

![Nettoyage de la mémoire du serveur en arrière-plan](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Garbage collection simultané

> [!TIP]
> Cette section s’applique à :
>
> - .NET Framework 3.5 et plus tôt pour la collecte des ordures de poste de travail
> - .NET Framework 4 et plus tôt pour la collecte des ordures du serveur
>
> Les déchets concomitants sont remplacés par [la collecte des ordures de fond](#background-workstation-garbage-collection) dans les versions ultérieures.

Dans le poste de travail ou la collecte des ordures serveur, vous pouvez activer la [collecte simultanée des ordures](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), ce qui permet aux threads de fonctionner en même temps qu’un fil dédié qui effectue la collecte des ordures pendant la majeure partie de la durée de la collecte. Cette option affecte uniquement les opérations garbage collection de génération 2. Les générations 0 et 1 sont toujours non simultanées car elles se terminent très rapidement.

Le garbage collection simultané permet aux applications interactives d'être plus réactives en réduisant les pauses d'une collection. Les threads managés peuvent continuer à s'exécuter une grande partie de la durée du garbage collection simultané. Cela génère des pauses plus courtes pendant l'opération garbage collection.

Le garbage collection simultané est exécuté sur un thread dédié. Par défaut, le CLR effectue le garbage collection de station de travail avec le garbage collection simultané activé. Ceci est vrai pour les ordinateurs multiprocesseur et à processeur unique.

L'illustration suivante montre le garbage collection simultané exécuté sur un thread dédié différent.

![Threads de nettoyage de la mémoire simultanés](./media/gc-concurrent.png)

## <a name="see-also"></a>Voir aussi

- [Options de configuration pour GC](../../core/run-time-config/garbage-collector.md)
- [Nettoyage de la mémoire](index.md) (garbage collection)
