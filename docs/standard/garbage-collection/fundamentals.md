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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330414"
---
# <a name="fundamentals-of-garbage-collection"></a>Notions de base du garbage collection

Dans le common language runtime (CLR), le garbage collector (GC) sert de gestionnaire de mémoire automatique. Il fournit les avantages suivants :

- Vous permet de développer votre application sans avoir à libérer manuellement la mémoire.

- Il alloue efficacement les objets sur le tas managé.

- Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets managés obtiennent automatiquement un contenu propre au démarrage, ce qui fait que leurs constructeurs n'ont pas à initialiser chaque champ de données.

- Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.

Cet article décrit les concepts fondamentaux de garbage collection.

## <a name="fundamentals-of-memory"></a>Notions de base de la mémoire

La liste suivante résume les concepts importants de la mémoire CLR.

- Chaque processus possède son propre espace d'adressage virtuel séparé. Tous les processus sur le même ordinateur partagent la même mémoire physique et le même fichier d’échange, le cas échéant.

- Par défaut, sur les ordinateurs 32 bits, chaque processus a un espace d'adressage virtuel en mode utilisateur de 2 Go.

- En tant que développeur d'applications, vous travaillez uniquement avec l'espace d'adressage virtuel et ne gérez jamais directement la mémoire physique. Le garbage collector alloue et libère la mémoire virtuelle pour vous sur le tas managé.

  Si vous écrivez du code natif, vous utilisez des fonctions Windows pour travailler avec l’espace d’adressage virtuel. Ces fonctions allouent et libèrent la mémoire virtuelle pour vous sur les tas natifs.

- La mémoire virtuelle peut être dans trois états :

  - Libre. Il n'existe aucune référence au bloc de mémoire et celui-ci est disponible pour allocation.

  - Réservé. Le bloc de mémoire est disponible pour votre utilisation et ne peut pas être utilisé pour une autre demande d'allocation. Toutefois, vous ne pouvez pas stocker de données dans ce bloc de mémoire tant qu'il n'est pas validé.

  - Validé. Le bloc de mémoire est assigné au stockage physique.

- L'espace d'adressage virtuel peut être fragmenté. Cela signifie qu'il existe des blocs libres, également appelés trous, dans l'espace d'adressage. Lorsqu'une allocation de mémoire virtuelle est demandée, le gestionnaire de mémoire virtuelle doit rechercher un bloc unique libre suffisamment grand pour satisfaire la demande d'allocation. Même si vous disposez de 2 Go d'espace libre, l'allocation qui requiert 2 Go échoue, sauf si tout cet espace libre est contenu dans un bloc d'adresse unique.

- Vous pouvez manquer de mémoire s’il n’y a pas suffisamment d’espace d’adressage virtuel à réserver ou d’espace physique à valider.

  Le fichier d’échange est utilisé même si la sollicitation de la mémoire physique (c’est-à-dire, la demande de mémoire physique) est faible. La première fois que la sollicitation de la mémoire physique est élevée, le système d’exploitation doit libérer de l’espace dans la mémoire physique pour stocker les données, et il sauvegarde certaines des données qui se trouvent dans la mémoire physique dans le fichier d’échange. Ces données ne sont pas paginées tant qu’elles ne sont pas nécessaires, il est donc possible de rencontrer la pagination dans les situations où la sollicitation de la mémoire physique est faible.

## <a name="conditions-for-a-garbage-collection"></a>Conditions pour une opération garbage collection

Le garbage collection se produit lorsque l'une des conditions suivantes est vraie :

- Le système possède peu de mémoire physique. Cela est détecté par la notification de mémoire insuffisante du système d’exploitation ou la mémoire insuffisante, comme indiqué par l’hôte.

- La mémoire utilisée par les objets alloués sur le tas managé dépasse un seuil acceptable. Ce seuil est continuellement ajusté à mesure que le processus s'exécute.

- La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée. Dans presque tous les cas, vous n’avez pas à appeler cette méthode, car le garbage collector s’exécute continuellement. Cette méthode est principalement utilisée pour les situations uniques et les tests.

## <a name="the-managed-heap"></a>Tas managé

Une fois que le garbage collector est initialisé par le CLR, il alloue un segment de mémoire pour stocker et gérer des objets. Cette mémoire est appelée tas managé, par opposition à un tas natif dans le système d'exploitation.

Il existe un tas managé pour chaque processus managé. Tous les threads du processus allouent de la mémoire pour les objets sur le même tas.

Pour réserver de la mémoire, le garbage collector appelle la fonction [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) de Windows et réserve un segment de mémoire à la fois pour les applications managées. Le garbage collector réserve également des segments, si nécessaire, et libère des segments dans le système d’exploitation (après avoir effacé leurs objets) en appelant la fonction [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) de Windows.

> [!IMPORTANT]
> La taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris les mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

Moins il y a d'objets alloués sur le tas, moins le garbage collector a à faire. Lorsque vous allouez des objets, n'utilisez pas de valeurs arrondies qui dépassent vos besoins, par exemple en allouant un tableau de 32 octets lorsque vous avez besoin de seulement 15 octets.

Lorsqu'un garbage collection est déclenché, le garbage collector libère la mémoire occupée par les objets morts. Le processus de libération compacte les objets vivants afin qu'ils soient déplacés ensemble, et l'espace inutilisé est supprimé, ce qui entraîne la diminution du tas. Les objets alloués ensemble restent ainsi ensemble sur le tas managé, pour conserver leur emplacement.

Le déroulement (fréquence et durée) des garbage collection est le résultat du volume des allocations et de la quantité de mémoire restante sur le tas managé.

Le tas peut être considéré comme l’accumulation de deux tas : le [tas de grands objets](large-object-heap.md) et le tas de petits objets.

Le [tas de grands objets](large-object-heap.md) contient des objets d’au moins 85 000 octets. Ces objets du tas d'objets volumineux sont généralement des tableaux. Il est rare qu'un objet d'instance soit extrêmement grand.

> [!TIP]
> Vous pouvez [configurer la taille de seuil](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) pour les objets à atteindre sur le tas d’objets volumineux.

## <a name="generations"></a>Générations

Le tas est organisé en générations. Il peut ainsi gérer des objets durables et éphémères. Le garbage collection consiste principalement en la récupération d'objets éphémères qui occupent généralement une petite partie du tas. Il existe trois générations d'objets sur le tas :

- **Génération 0**. Il s'agit de la génération la plus jeune, qui contient des objets éphémères. Un exemple d'objet éphémère est une variable temporaire. Le garbage collection a le plus souvent lieu dans cette génération.

  Les objets alloués récemment forment une nouvelle génération d’objets et sont implicitement des collections de génération 0. Toutefois, s’il s’agit d’objets volumineux, ils sont placés sur le tas d’objets volumineux dans une collection de génération 2.

  La plupart des objets sont libérés pour l’opération garbage collection dans la génération 0 et ne survivent pas à la génération suivante.

- **Génération 1**. Cette génération contient des objets éphémères et sert de tampon entre objets éphémères et objets durables.

- **Génération 2**. Cette génération contient des objets durables. Un exemple d’objet de longue durée est un objet dans une application serveur qui contient des données statiques qui sont actives pendant la durée du processus.

Les opérations garbage collection se produisent sur des générations spécifiques, selon les conditions spécifiées. La collecte d'une génération signifie la collecte des objets de cette génération et de toutes ses générations plus jeunes. Les opérations garbage collection de génération 2 sont également appelées garbage collection complet, car elles libèrent tous les objets de toutes les générations (autrement dit, tous les objets du tas managé).

### <a name="survival-and-promotions"></a>Survie et promotions

Les objets qui ne sont pas récupérés dans un garbage collection sont appelés survivants et sont promus à la génération suivante. Les objets qui survivent à un garbage collection de génération 0 sont promus à la génération 1, les objets qui survivent à un garbage collection de génération 1 sont promus à la génération 2 et les objets qui survivent à un garbage collection de génération 2 restent dans la génération 2.

Lorsque le garbage collector détecte que le taux de survie est élevé dans une génération, il augmente le seuil des allocations pour cette génération. La collection suivante obtient une taille substantielle de mémoire libérée. Le CLR équilibre continuellement deux priorités : ne pas permettre à la plage de travail d’une application d’être trop volumineuse en retardant garbage collection et en empêchant l’exécution trop fréquente du garbage collection.

### <a name="ephemeral-generations-and-segments"></a>Segments et générations éphémères

Étant donné que les objets des générations 0 et 1 sont éphémères, ces générations sont appelées générations éphémères.

Les générations éphémères doivent être allouées dans le segment de mémoire appelé segment éphémère. Chaque nouveau segment acquis par le garbage collector devient le nouveau segment éphémère et contient les objets qui ont survécu à un garbage collection de génération 0. L'ancien segment éphémère devient le nouveau segment de génération 2.

La taille du segment éphémère varie selon qu’il s’agit d’un système 32 bits ou 64 bits, et du type de garbage collector en cours d’exécution. Le tableau ci-dessous répertorie les valeurs par défaut.

||32 bits|64 bits|
|-|-------------|-------------|
|Garbage collector pour station de travail|16 Mo|256 Mo|
|Garbage collector pour serveur|64 Mo|4 Go|
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

  En règle générale, le tas d’objets volumineux (LOH) n’est pas compacté, car la copie d’objets volumineux impose une baisse des performances. Toutefois, dans .NET Core et dans .NET Framework 4.5.1 et versions ultérieures, vous pouvez utiliser la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> pour compacter le tas d’objets volumineux à la demande. En outre, le LOH est automatiquement compacté lorsqu’une limite inconditionnelle est définie en spécifiant l’un ou l’autre des éléments suivants :

  - limite de mémoire sur un conteneur, ou
  - options de configuration [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) ou [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) Runtime

Le garbage collector utilise les informations suivantes pour déterminer si les objets sont vivants :

- **Racines de pile**. Variables de pile fournies par le compilateur juste-à-temps (JIT) et l'explorateur de pile. Les optimisations JIT peuvent rallonger ou raccourcir les régions de code au sein desquelles les variables de pile sont signalées au garbage collector.

- **Handles de garbage collection**. Handles qui pointent vers les objets managés qui peuvent être alloués par le code utilisateur ou par le Common Language Runtime.

- **Données statiques**. Objets statiques des domaines d'application qui pourraient référencer d'autres objets. Chaque domaine d'application effectue le suivi de ses objets statiques.

Avant qu'une opération garbage collection ne démarre, tous les threads managés sont suspendus à l'exception du thread qui a déclenché l'opération.

L'illustration suivante montre un thread qui déclenche un garbage collection et entraîne l'interruption des autres threads.

![Lorsqu’un thread déclenche un garbage collection](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipuler des ressources non managées

Si les objets managés référencent des objets non managés à l’aide de leurs handles de fichiers natifs, vous devez libérer explicitement les objets non managés, car le garbage collector effectue uniquement le suivi de la mémoire sur le tas managé.

Les utilisateurs de l’objet managé ne peuvent pas supprimer les ressources natives utilisées par l’objet. Pour effectuer le nettoyage, vous pouvez rendre l’objet managé finalisable. La finalisation est constituée d’actions de nettoyage qui s’exécutent lorsque l’objet n’est plus utilisé. Lorsque l’objet managé meurt, il effectue les actions de nettoyage spécifiées dans sa méthode de finaliseur.

Lorsqu'un objet finalisable est détecté comme étant mort, son finaliseur est placé dans une file d'attente afin que ses actions de nettoyage soient exécutées, mais l'objet lui-même est promu à la génération suivante. Par conséquent, vous devez attendre jusqu’au garbage collection suivant sur cette génération (qui n’est pas nécessairement le garbage collection suivant) pour déterminer si l’objet a été récupéré.

Pour plus d’informations sur la finalisation, consultez <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>Garbage collection de station de travail et de serveur

Le garbage collector s'ajuste automatiquement et peut travailler dans une large gamme de scénarios. Vous pouvez utiliser un [paramètre de fichier de configuration](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) pour définir le type de garbage collection en fonction des caractéristiques de la charge de travail. Le CLR fournit les types de garbage collection suivants :

- Le garbage collection de station de travail (GC) est conçu pour les applications clientes. Il s’agit de la version de catalogue global par défaut pour les applications autonomes. Pour les applications hébergées, par exemple, celles hébergées par ASP.NET, l’hôte détermine la version GC par défaut.

  Le garbage collection de station de travail peut être simultané ou non simultané. Le garbage collection simultané permet aux threads managés de continuer à fonctionner pendant un garbage collection. L' [garbage collection d’arrière-plan](#background-workstation-garbage-collection) remplace les [garbage collection simultanées](#concurrent-garbage-collection) dans .NET Framework 4 et versions ultérieures.

- Garbage collection de serveur, prévu pour les applications serveur qui ont besoin d'un débit et d'une extensibilité.

  - Dans .NET Core, les garbage collection serveur peuvent être non simultanés ou en arrière-plan.

  - Dans .NET Framework 4,5 et versions ultérieures, le garbage collection de serveur peut être non simultané ou en arrière-plan (l’garbage collection d’arrière-plan remplace le garbage collection simultané). Dans .NET Framework 4 et versions antérieures, le garbage collection de serveur n’est pas simultané.

L’illustration suivante montre les threads dédiés qui exécutent les garbage collection sur un serveur :

![Threads de nettoyage de la mémoire du serveur](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Comparer la station de travail et le serveur garbage collection

Voici les considérations liées aux threads et aux performances pour le garbage collection de station de travail :

- La collecte se produit sur le thread utilisateur qui a déclenché le garbage collection et reste à la même priorité. Étant donné que les threads utilisateur sont généralement exécutés à la priorité normale, le garbage collector (qui s'exécute sur un thread de priorité normale) doit rivaliser avec d'autres threads pour le temps processeur. (Les threads qui exécutent du code natif ne sont pas suspendus sur le serveur ou la station de travail garbage collection.)

- Le garbage collection de station de travail est toujours utilisé sur un ordinateur doté d’un seul processeur, quel que soit le [paramètre de configuration](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Voici les considérations liées aux threads et aux performances pour le garbage collection de serveur :

- La collecte se produit sur plusieurs threads dédiés qui s'exécutent au niveau de priorité `THREAD_PRIORITY_HIGHEST` .

- Un tas et un thread dédié pour effectuer le garbage collection sont fournis pour chaque UC, et les tas sont collectés au même moment. Chaque tas contient un tas de petits objets et un tas d'objets volumineux, et tous les tas peuvent faire l'objet d'accès par du code utilisateur. Les objets des différents tas peuvent faire référence les uns aux autres.

- Étant donné que plusieurs threads de garbage collection fonctionnent ensemble, le garbage collection de serveur est plus rapide que le garbage collection de station de travail sur un tas de même taille.

- Le garbage collection de serveur présente souvent des segments de plus grande taille. Toutefois, il ne s’agit que d’une généralisation : la taille de segment est spécifique à l’implémentation et peut faire l’objet de modifications. N’effectuez pas d’hypothèses sur la taille des segments alloués par le garbage collector lors du paramétrage de votre application.

- Le garbage collection de serveur peut consommer beaucoup de ressources. Supposons, par exemple, qu’il y ait 12 processus utilisant le garbage collection de serveur exécuté sur un ordinateur doté de 4 processeurs. Si tous les processus se produisent pour collecter les opérations de garbage collection en même temps, ils interféreraient entre eux, car 12 threads sont planifiés sur le même processeur. Si les processus sont actifs, il n’est pas judicieux de leur demander d’utiliser le garbage collection de serveur.

Si vous exécutez des centaines d’instances d’une application, envisagez d’utiliser des garbage collection de station de travail avec garbage collection simultanée désactivée. Cela provoquera moins de changements de contexte, ce qui peut améliorer les performances.

## <a name="background-workstation-garbage-collection"></a>Nettoyage de la mémoire de la station de travail en arrière-plan

Dans garbage collection de station de travail en arrière-plan, les générations éphémères (0 et 1) sont collectées si nécessaire pendant que la collection de génération 2 est en cours. La station de travail en arrière-plan garbage collection est exécutée sur un thread dédié et s’applique uniquement aux collections de génération 2.

L’garbage collection d’arrière-plan est activée par défaut et peut être activée ou désactivée avec le paramètre de configuration [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) dans .NET Framework applications ou le paramètre [System. gc. concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) dans les applications .net core.

> [!NOTE]
> L’garbage collection d’arrière-plan remplace la [garbage collection simultanée](#concurrent-garbage-collection) et est disponible dans .NET Framework 4 et versions ultérieures. Dans .NET Framework 4, il est pris en charge uniquement pour les garbage collection de station de travail. À compter de .NET Framework 4,5, le garbage collection d’arrière-plan est disponible pour les garbage collection de station de travail et de serveur.

Une collecte sur des générations éphémères pendant le garbage collection d'arrière-plan est appelée garbage collection de premier plan. Lorsque des opérations garbage collection de premier plan ont lieu, tous les threads managés sont suspendus.

Lorsque garbage collection d’arrière-plan est en cours et que vous avez alloué assez d’objets dans la génération 0, le CLR effectue une garbage collection de premier plan de génération 0 ou 1. Le thread de garbage collection d'arrière-plan dédié vérifie des points sécurisés fréquents de façon à déterminer s'il existe une demande de garbage collection de premier plan. Le cas échéant, la collecte d'arrière-plan s'interrompt afin que le garbage collection de premier plan puisse se produire. Une fois le garbage collection de premier plan terminé, le thread de garbage collection d'arrière-plan dédié et les threads utilisateur reprennent.

Le garbage collection d'arrière-plan supprime les restrictions d'allocation imposées par le garbage collection simultané, car des opérations garbage collection éphémères peuvent se produire pendant le garbage collection d'arrière-plan. L’garbage collection d’arrière-plan peut supprimer des objets morts dans les générations éphémères. Il peut également développer le tas si nécessaire pendant une garbage collection de la génération 1.

L’illustration suivante montre le nettoyage de la mémoire en arrière-plan effectué sur un thread dédié distinct, sur une station de travail :

![Nettoyage de la mémoire de la station de travail en arrière-plan](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Nettoyage de la mémoire du serveur en arrière-plan

À compter de .NET Framework 4,5, le serveur d’arrière-plan garbage collection est le mode par défaut pour les garbage collection serveur.

Le serveur d’arrière-plan garbage collection fonctionne de la même façon que les garbage collection de station de travail en arrière-plan, décrits dans la section précédente, mais il existe quelques différences :

- La station de travail en arrière-plan garbage collection utilise un thread d’arrière-plan garbage collection dédié, tandis que le serveur d’arrière-plan garbage collection utilise plusieurs En règle générale, il existe un thread dédié pour chaque processeur logique.

- Contrairement au thread du garbage collection de station de travail en arrière-plan, ces threads n'expirent pas.

L’illustration suivante montre le nettoyage de la mémoire en arrière-plan effectué sur un thread dédié distinct, sur un serveur :

![Nettoyage de la mémoire du serveur en arrière-plan](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Garbage collection simultané

> [!TIP]
> Cette section s’applique à :
>
> - .NET Framework 3,5 et versions antérieures pour stations de travail garbage collection
> - .NET Framework 4 et versions antérieures pour le serveur garbage collection
>
> Le garbage collection simultané est remplacé par le [garbage collection d’arrière-plan](#background-workstation-garbage-collection) dans les versions ultérieures.

Dans les garbage collection de station de travail ou de serveur, vous pouvez [activer des garbage collection simultanées](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), ce qui permet aux threads de s’exécuter simultanément avec un thread dédié qui exécute le garbage collection pour la majeure partie de la durée de la collection. Cette option affecte uniquement les opérations garbage collection de génération 2. Les générations 0 et 1 sont toujours non simultanées car elles se terminent très rapidement.

Le garbage collection simultané permet aux applications interactives d'être plus réactives en réduisant les pauses d'une collection. Les threads managés peuvent continuer à s'exécuter une grande partie de la durée du garbage collection simultané. Cela génère des pauses plus courtes pendant l'opération garbage collection.

Le garbage collection simultané est exécuté sur un thread dédié. Par défaut, le CLR effectue le garbage collection de station de travail avec le garbage collection simultané activé. Ceci est vrai pour les ordinateurs multiprocesseur et à processeur unique.

L'illustration suivante montre le garbage collection simultané exécuté sur un thread dédié différent.

![Threads de garbage collection simultanés](./media/gc-concurrent.png)

## <a name="see-also"></a>Voir aussi

- [Options de configuration pour GC](../../core/run-time-config/garbage-collector.md)
- [Garbage collection](index.md)
