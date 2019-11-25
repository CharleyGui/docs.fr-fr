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

In the common language runtime (CLR), the garbage collector (GC) serves as an automatic memory manager. Il fournit les avantages suivants :

- Enables you to develop your application without having to manually free memory.

- Il alloue efficacement les objets sur le tas managé.

- Il libère les objets qui ne sont plus utilisés, efface leur mémoire et garde la mémoire disponible pour les futures allocations. Les objets managés obtiennent automatiquement un contenu propre au démarrage, ce qui fait que leurs constructeurs n'ont pas à initialiser chaque champ de données.

- Il sécurise la mémoire en s'assurant qu'un objet ne peut pas utiliser le contenu d'un autre objet.

This article describes the core concepts of garbage collection.

## <a name="fundamentals-of-memory"></a>Notions de base de la mémoire

La liste suivante résume les concepts importants de la mémoire CLR.

- Chaque processus possède son propre espace d'adressage virtuel séparé. All processes on the same computer share the same physical memory and the page file, if there is one.

- Par défaut, sur les ordinateurs 32 bits, chaque processus a un espace d'adressage virtuel en mode utilisateur de 2 Go.

- En tant que développeur d'applications, vous travaillez uniquement avec l'espace d'adressage virtuel et ne gérez jamais directement la mémoire physique. Le garbage collector alloue et libère la mémoire virtuelle pour vous sur le tas managé.

  If you are writing native code, you use Windows functions to work with the virtual address space. Ces fonctions allouent et libèrent la mémoire virtuelle pour vous sur les tas natifs.

- La mémoire virtuelle peut être dans trois états :

  - Libre. Il n'existe aucune référence au bloc de mémoire et celui-ci est disponible pour allocation.

  - Réservé. Le bloc de mémoire est disponible pour votre utilisation et ne peut pas être utilisé pour une autre demande d'allocation. Toutefois, vous ne pouvez pas stocker de données dans ce bloc de mémoire tant qu'il n'est pas validé.

  - Validé. Le bloc de mémoire est assigné au stockage physique.

- L'espace d'adressage virtuel peut être fragmenté. Cela signifie qu'il existe des blocs libres, également appelés trous, dans l'espace d'adressage. Lorsqu'une allocation de mémoire virtuelle est demandée, le gestionnaire de mémoire virtuelle doit rechercher un bloc unique libre suffisamment grand pour satisfaire la demande d'allocation. Même si vous disposez de 2 Go d'espace libre, l'allocation qui requiert 2 Go échoue, sauf si tout cet espace libre est contenu dans un bloc d'adresse unique.

- You can run out of memory if there isn't enough virtual address space to reserve or physical space to commit.

  The page file is used even if physical memory pressure (that is, demand for physical memory) is low. The first time physical memory pressure is high, the operating system must make room in physical memory to store data, and it backs up some of the data that is in physical memory to the page file. That data is not paged until it's needed, so it's possible to encounter paging in situations where the physical memory pressure is low.

## <a name="conditions-for-a-garbage-collection"></a>Conditions pour une opération garbage collection

Le garbage collection se produit lorsque l'une des conditions suivantes est vraie :

- Le système possède peu de mémoire physique. This is detected by either the low memory notification from the OS or low memory as indicated by the host.

- La mémoire utilisée par les objets alloués sur le tas managé dépasse un seuil acceptable. Ce seuil est continuellement ajusté à mesure que le processus s'exécute.

- La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée. Dans presque tous les cas, vous n'avez pas à appeler cette méthode, car le garbage collector s'exécute continuellement. Cette méthode est principalement utilisée pour les situations uniques et les tests.

## <a name="the-managed-heap"></a>Tas managé

Une fois que le garbage collector est initialisé par le CLR, il alloue un segment de mémoire pour stocker et gérer des objets. Cette mémoire est appelée tas managé, par opposition à un tas natif dans le système d'exploitation.

Il existe un tas managé pour chaque processus managé. Tous les threads du processus allouent de la mémoire pour les objets sur le même tas.

To reserve memory, the garbage collector calls the Windows [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) function and reserves one segment of memory at a time for managed applications. The garbage collector also reserves segments, as needed, and releases segments back to the operating system (after clearing them of any objects) by calling the Windows [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) function.

> [!IMPORTANT]
> La taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris les mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

Moins il y a d'objets alloués sur le tas, moins le garbage collector a à faire. Lorsque vous allouez des objets, n'utilisez pas de valeurs arrondies qui dépassent vos besoins, par exemple en allouant un tableau de 32 octets lorsque vous avez besoin de seulement 15 octets.

Lorsqu'un garbage collection est déclenché, le garbage collector libère la mémoire occupée par les objets morts. Le processus de libération compacte les objets vivants afin qu'ils soient déplacés ensemble, et l'espace inutilisé est supprimé, ce qui entraîne la diminution du tas. Les objets alloués ensemble restent ainsi ensemble sur le tas managé, pour conserver leur emplacement.

Le déroulement (fréquence et durée) des garbage collection est le résultat du volume des allocations et de la quantité de mémoire restante sur le tas managé.

Le tas peut être considéré comme l’accumulation de deux tas : le [tas de grands objets](large-object-heap.md) et le tas de petits objets.

Le [tas de grands objets](large-object-heap.md) contient des objets d’au moins 85 000 octets. Ces objets du tas d'objets volumineux sont généralement des tableaux. Il est rare qu'un objet d'instance soit extrêmement grand.

> [!TIP]
> You can [configure the threshold size](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) for objects to go on the large object heap.

## <a name="generations"></a>Générations

Le tas est organisé en générations. Il peut ainsi gérer des objets durables et éphémères. Le garbage collection consiste principalement en la récupération d'objets éphémères qui occupent généralement une petite partie du tas. Il existe trois générations d'objets sur le tas :

- **Génération 0**. Il s'agit de la génération la plus jeune, qui contient des objets éphémères. Un exemple d'objet éphémère est une variable temporaire. Le garbage collection a le plus souvent lieu dans cette génération.

  Newly allocated objects form a new generation of objects and are implicitly generation 0 collections. However, if they are large objects, they go on the large object heap in a generation 2 collection.

  La plupart des objets sont libérés pour l'opération garbage collection dans la génération 0 et ne survivent pas à la génération suivante.

- **Génération 1**. Cette génération contient des objets éphémères et sert de tampon entre objets éphémères et objets durables.

- **Génération 2**. Cette génération contient des objets durables. An example of a long-lived object is an object in a server application that contains static data that's live for the duration of the process.

Les opérations garbage collection se produisent sur des générations spécifiques, selon les conditions spécifiées. La collecte d'une génération signifie la collecte des objets de cette génération et de toutes ses générations plus jeunes. Les opérations garbage collection de génération 2 sont également appelées garbage collection complet, car elles libèrent tous les objets de toutes les générations (autrement dit, tous les objets du tas managé).

### <a name="survival-and-promotions"></a>Survie et promotions

Objects that are not reclaimed in a garbage collection are known as survivors and are promoted to the next generation. Les objets qui survivent à un garbage collection de génération 0 sont promus à la génération 1, les objets qui survivent à un garbage collection de génération 1 sont promus à la génération 2 et les objets qui survivent à un garbage collection de génération 2 restent dans la génération 2.

When the garbage collector detects that the survival rate is high in a generation, it increases the threshold of allocations for that generation. The next collection gets a substantial size of reclaimed memory. The CLR continually balances two priorities: not letting an application's working set get too large by delaying garbage collection and not letting the garbage collection run too frequently.

### <a name="ephemeral-generations-and-segments"></a>Segments et générations éphémères

Étant donné que les objets des générations 0 et 1 sont éphémères, ces générations sont appelées générations éphémères.

Les générations éphémères doivent être allouées dans le segment de mémoire appelé segment éphémère. Chaque nouveau segment acquis par le garbage collector devient le nouveau segment éphémère et contient les objets qui ont survécu à un garbage collection de génération 0. L'ancien segment éphémère devient le nouveau segment de génération 2.

The size of the ephemeral segment varies depending on whether a system is 32-bit or 64-bit, and on the type of garbage collector it is running. Le tableau ci-dessous répertorie les valeurs par défaut.

||32 bits|64 bits|
|-|-------------|-------------|
|Garbage collector pour station de travail|16 Mo|256 Mo|
|Garbage collector pour serveur|64 Mo|4 Go|
|Garbage collector pour serveur > 4 processeurs logiques|32 Mo|2 Go|
|Garbage collector pour serveur > 8 processeurs logiques|16 Mo|1 Go|

Le segment éphémère peut inclure des objets de la génération 2. Les objets de génération 2 peuvent utiliser plusieurs segments (autant que votre processus en requiert et que la mémoire en autorise).

La quantité de mémoire libérée à partir d'un garbage collection éphémère est limitée à la taille du segment éphémère. La quantité de mémoire libérée est proportionnelle à l'espace occupé par les objets morts.

## <a name="what-happens-during-a-garbage-collection"></a>Déroulement d'une opération garbage collection

Une opération garbage collection présente les phases suivantes :

- Une phase de marquage qui recherche et crée une liste de tous les objets actifs.

- Une phase de déplacement qui met à jour les références aux objets qui seront compactés.

- Une phase de compactage qui libère l'espace occupé par les objets morts et compacte les objets survivants. La phase de compactage déplace les objets qui ont survécu à un garbage collection vers l'extrémité la plus ancienne du segment.

  Étant donné que les collections de génération 2 peuvent occuper plusieurs segments, les objets promus dans la génération 2 peuvent être déplacés dans un segment plus ancien. Les survivants des générations 1 et 2 peuvent être déplacés vers un autre segment, car ils sont promus à la génération 2.

  Ordinarily, the large object heap (LOH) is not compacted, because copying large objects imposes a performance penalty. However, in .NET Core and in .NET Framework 4.5.1 and later, you can use the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property to compact the large object heap on demand. In addition, the LOH is automatically compacted when a hard limit is set by specifying either:

  - a memory limit on a container, or
  - the [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) or [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) run-time configuration options

Le garbage collector utilise les informations suivantes pour déterminer si les objets sont vivants :

- **Racines de pile**. Variables de pile fournies par le compilateur juste-à-temps (JIT) et l'explorateur de pile. JIT optimizations can lengthen or shorten regions of code within which stack variables are reported to the garbage collector.

- **Handles de garbage collection**. Handles qui pointent vers les objets managés qui peuvent être alloués par le code utilisateur ou par le Common Language Runtime.

- **Données statiques**. Objets statiques des domaines d'application qui pourraient référencer d'autres objets. Chaque domaine d'application effectue le suivi de ses objets statiques.

Avant qu'une opération garbage collection ne démarre, tous les threads managés sont suspendus à l'exception du thread qui a déclenché l'opération.

L'illustration suivante montre un thread qui déclenche un garbage collection et entraîne l'interruption des autres threads.

![Lorsqu'un thread déclenche un nettoyage de la mémoire](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulate unmanaged resources

If managed objects reference unmanaged objects by using their native file handles, you have to explicitly free the unmanaged objects, because the garbage collector only tracks memory on the managed heap.

Users of the managed object may not dispose the native resources used by the object. To perform the cleanup, you can make the managed object finalizable. Finalization consists of cleanup actions that execute when the object is no longer in use. When the managed object dies, it performs cleanup actions that are specified in its finalizer method.

Lorsqu'un objet finalisable est détecté comme étant mort, son finaliseur est placé dans une file d'attente afin que ses actions de nettoyage soient exécutées, mais l'objet lui-même est promu à la génération suivante. Par conséquent, vous devez attendre jusqu'au garbage collection suivant sur cette génération (qui n'est pas nécessairement le garbage collection suivant) pour déterminer si l'objet a été récupéré.

For more information about finalization, see <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>Garbage collection de station de travail et de serveur

Le garbage collector s'ajuste automatiquement et peut travailler dans une large gamme de scénarios. You can use a [configuration file setting](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) to set the type of garbage collection based on the characteristics of the workload. Le CLR fournit les types de garbage collection suivants :

- Workstation garbage collection (GC) is designed for client apps. It is the default GC flavor for standalone apps. For hosted apps, for example, those hosted by ASP.NET, the host determines the default GC flavor.

  Le garbage collection de station de travail peut être simultané ou non simultané. Le garbage collection simultané permet aux threads managés de continuer à fonctionner pendant un garbage collection. [Background garbage collection](#background-workstation-garbage-collection) replaces [concurrent garbage collection](#concurrent-garbage-collection) in .NET Framework 4 and later versions.

- Garbage collection de serveur, prévu pour les applications serveur qui ont besoin d'un débit et d'une extensibilité.

  - In .NET Core, server garbage collection can be non-concurrent or background.

  - In .NET Framework 4.5 and later versions, server garbage collection can be non-concurrent or background (background garbage collection replaces concurrent garbage collection). In .NET Framework 4 and previous versions, server garbage collection is non-concurrent.

The following illustration shows the dedicated threads that perform the garbage collection on a server:

![Threads de nettoyage de la mémoire du serveur](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Compare workstation and server garbage collection

Voici les considérations liées aux threads et aux performances pour le garbage collection de station de travail :

- La collecte se produit sur le thread utilisateur qui a déclenché le garbage collection et reste à la même priorité. Étant donné que les threads utilisateur sont généralement exécutés à la priorité normale, le garbage collector (qui s'exécute sur un thread de priorité normale) doit rivaliser avec d'autres threads pour le temps processeur. (Threads that run native code are not suspended on either server or workstation garbage collection.)

- Workstation garbage collection is always used on a computer that has only one processor, regardless of the [configuration setting](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Voici les considérations liées aux threads et aux performances pour le garbage collection de serveur :

- La collecte se produit sur plusieurs threads dédiés qui s'exécutent au niveau de priorité `THREAD_PRIORITY_HIGHEST` .

- Un tas et un thread dédié pour effectuer le garbage collection sont fournis pour chaque UC, et les tas sont collectés au même moment. Chaque tas contient un tas de petits objets et un tas d'objets volumineux, et tous les tas peuvent faire l'objet d'accès par du code utilisateur. Les objets des différents tas peuvent faire référence les uns aux autres.

- Étant donné que plusieurs threads de garbage collection fonctionnent ensemble, le garbage collection de serveur est plus rapide que le garbage collection de station de travail sur un tas de même taille.

- Le garbage collection de serveur présente souvent des segments de plus grande taille. However, this is only a generalization: segment size is implementation-specific and is subject to change. Don't make assumptions about the size of segments allocated by the garbage collector when tuning your app.

- Le garbage collection de serveur peut consommer beaucoup de ressources. For example, imagine that there are 12 processes that use server GC running on a computer that has 4 processors. If all the processes happen to collect garbage at the same time, they would interfere with each other, as there would be 12 threads scheduled on the same processor. If the processes are active, it's not a good idea to have them all use server GC.

If you're running hundreds of instances of an application, consider using workstation garbage collection with concurrent garbage collection disabled. Cela provoquera moins de changements de contexte, ce qui peut améliorer les performances.

## <a name="background-workstation-garbage-collection"></a>Nettoyage de la mémoire de la station de travail en arrière-plan

In background workstation garbage collection, ephemeral generations (0 and 1) are collected as needed while the collection of generation 2 is in progress. Background workstation garbage collection is performed on a dedicated thread and applies only to generation 2 collections.

Background garbage collection is enabled by default and can be enabled or disabled with the [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration setting in .NET Framework apps or the [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) setting in .NET Core apps.

> [!NOTE]
> Background garbage collection replaces [concurrent garbage collection](#concurrent-garbage-collection) and is available in .NET Framework 4 and later versions. In .NET Framework 4, it's supported only for workstation garbage collection. Starting with .NET Framework 4.5, background garbage collection is available for both workstation and server garbage collection.

Une collecte sur des générations éphémères pendant le garbage collection d'arrière-plan est appelée garbage collection de premier plan. Lorsque des opérations garbage collection de premier plan ont lieu, tous les threads managés sont suspendus.

When background garbage collection is in progress and you've allocated enough objects in generation 0, the CLR performs a generation 0 or generation 1 foreground garbage collection. Le thread de garbage collection d'arrière-plan dédié vérifie des points sécurisés fréquents de façon à déterminer s'il existe une demande de garbage collection de premier plan. Le cas échéant, la collecte d'arrière-plan s'interrompt afin que le garbage collection de premier plan puisse se produire. Une fois le garbage collection de premier plan terminé, le thread de garbage collection d'arrière-plan dédié et les threads utilisateur reprennent.

Le garbage collection d'arrière-plan supprime les restrictions d'allocation imposées par le garbage collection simultané, car des opérations garbage collection éphémères peuvent se produire pendant le garbage collection d'arrière-plan. Background garbage collection can remove dead objects in ephemeral generations. It can also expand the heap if needed during a generation 1 garbage collection.

L’illustration suivante montre le nettoyage de la mémoire en arrière-plan effectué sur un thread dédié distinct, sur une station de travail :

![Nettoyage de la mémoire de la station de travail en arrière-plan](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Nettoyage de la mémoire du serveur en arrière-plan

Starting with .NET Framework 4.5, background server garbage collection is the default mode for server garbage collection.

Background server garbage collection functions similarly to background workstation garbage collection, described in the previous section, but there are a few differences:

- Background workstation garbage collection uses one dedicated background garbage collection thread, whereas background server garbage collection uses multiple threads. Typically, there's a dedicated thread for each logical processor.

- Contrairement au thread du garbage collection de station de travail en arrière-plan, ces threads n'expirent pas.

L’illustration suivante montre le nettoyage de la mémoire en arrière-plan effectué sur un thread dédié distinct, sur un serveur :

![Nettoyage de la mémoire du serveur en arrière-plan](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Garbage collection simultané

> [!TIP]
> This section applies to:
>
> - .NET Framework 3.5 and earlier for workstation garbage collection
> - .NET Framework 4 and earlier for server garbage collection
>
> Concurrent garbage is replaced by [background garbage collection](#background-workstation-garbage-collection) in later versions.

In workstation or server garbage collection, you can [enable concurrent garbage collection](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), which enables threads to run concurrently with a dedicated thread that performs the garbage collection for most of the duration of the collection. Cette option affecte uniquement les opérations garbage collection de génération 2. Les générations 0 et 1 sont toujours non simultanées car elles se terminent très rapidement.

Le garbage collection simultané permet aux applications interactives d'être plus réactives en réduisant les pauses d'une collection. Les threads managés peuvent continuer à s'exécuter une grande partie de la durée du garbage collection simultané. Cela génère des pauses plus courtes pendant l'opération garbage collection.

Le garbage collection simultané est exécuté sur un thread dédié. Par défaut, le CLR effectue le garbage collection de station de travail avec le garbage collection simultané activé. Ceci est vrai pour les ordinateurs multiprocesseur et à processeur unique.

L'illustration suivante montre le garbage collection simultané exécuté sur un thread dédié différent.

![Threads de nettoyage de la mémoire simultanés](./media/gc-concurrent.png)

## <a name="see-also"></a>Voir aussi

- [Configuration options for GC](../../core/run-time-config/garbage-collector.md)
- [Garbage collection](index.md)
