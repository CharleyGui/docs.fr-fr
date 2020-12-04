---
title: Événements d’exécution du garbage collection
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques au garbage collector .NET.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588611"
---
# <a name="net-runtime-garbage-collection-events"></a>Événements de garbage collection du Runtime .NET

Ces événements collectent des informations relatives au garbage collection. Ils facilitent le diagnostic et le débogage, notamment la détermination du nombre de fois que garbage collection a été effectué, la quantité de mémoire libérée pendant la garbage collection, etc. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)

## <a name="gcstart_v2-event"></a>Événement GCStart_V2

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCStart_V1`|1|Un garbage collection a démarré.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|Le *n* ième garbage collection.|
|`Depth`|`win:UInt32`|La génération est collectée.|
|`Reason`|`win:UInt32`|Pourquoi le garbage collection a été déclenché :<br /><br /> `0x0` -Allocation de tas de petits objets.<br /><br /> `0x1` Induit.<br /><br /> `0x2` -Mémoire insuffisante.<br /><br /> `0x3` Vidé.<br /><br /> `0x4` -Allocation du tas d’objets volumineux.<br /><br /> `0x5` -Espace insuffisant (pour un tas de petits objets).<br /><br /> `0x6` -Espace insuffisant (pour le tas d’objets volumineux).<br /><br /> `0x7` -Induite mais n’est pas forcée comme un blocage.|
|`Type`|`win:UInt32`|`0x0` -Le blocage garbage collection s’est produit en dehors des garbage collection en arrière-plan.<br /><br /> `0x1` -Garbage collection d’arrière-plan.<br /><br /> `0x2` -Les garbage collection bloquantes se sont produites lors de la garbage collection d’arrière-plan.|
|`ClrInstanceID`|win:UInt16|ID unique de l’instance de CoreCLR.|

## <a name="gcend_v1-event"></a>Événement GCEnd_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCEnd_V1`|2|Un garbage collection s'est terminé.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|Le *n* ième garbage collection.|
|`Depth`|`win:UInt32`|Génération ayant été collectée.|
|`ClrInstanceID`|win:UInt16|ID unique de l’instance de CoreCLR.|

## <a name="gcheapstats_v2-event"></a>Événement GCHeapStats_V2

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Description|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|4|Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|Taille, en octets, de la mémoire de génération 0.|
|`TotalPromotedSize0`|`win:UInt64`|Nombre d'octets promus de la génération 0 à la génération 1.|
|`GenerationSize1`|`win:UInt64`|Taille, en octets, de la mémoire de génération 1.|
|`TotalPromotedSize1`|`win:UInt64`|Nombre d'octets promus de la génération 1 à la génération 2.|
|`GenerationSize2`|`win:UInt64`|Taille, en octets, de la mémoire de génération 2.|
|`TotalPromotedSize2`|`win:UInt64`|Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.|
|`GenerationSize3`|`win:UInt64`|Taille, en octets, du tas des objets volumineux.|
|`TotalPromotedSize3`|`win:UInt64`|Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.|
|`FinalizationPromotedSize`|`win:UInt64`|Taille totale, en octets, des objets qui sont prêts pour la finalisation.|
|`FinalizationPromotedCount`|`win:UInt64`|Nombre d'objets qui sont prêts pour la finalisation.|
|`PinnedObjectCount`|`win:UInt32`|Nombre d'objets (non déplaçables) épinglés.|
|`SinkBlockCount`|`win:UInt32`|Nombre de blocs de synchronisation en cours d'utilisation.|
|`GCHandleCount`|`win:UInt32`|Nombre de handles de garbage collection en cours d'utilisation.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|
|`GenerationSize4`|`win:UInt64`|Taille, en octets, du tas d’objets épinglés.|
|`TotalPromotedSize4`|`win:UInt64`|Nombre d’octets qui ont survécu dans le tas d’objets épinglés après la dernière collection.|

## <a name="gccreatesegment_v1-event"></a>Événement GCCreateSegment_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|5|Un nouveau segment de garbage collection a été créé. En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|Adresse du segment.|
|`Size`|`win:UInt64`|Taille du segment.|
|`Type`|`win:UInt32`|0x0 – Tas de petits objets.<br /><br /> 0x1 – Tas d'objets volumineux.<br /><br /> 0x2 – Tas en lecture seule.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.

## <a name="gcfreesegment_v1-event"></a>Événement GCFreeSegment_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|6|Un nouveau segment de garbage collection a été libéré.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|Adresse du segment.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="gcrestarteebegin_v1-event"></a>Événement GCRestartEEBegin_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|7|La reprise du common language runtime après sa suspension a commencé.|

Cet événement n’a pas de données d’événement.

## <a name="gcrestarteeend_v1-event"></a>Événement GCRestartEEEnd_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID d'événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|3|La reprise du common language runtime après sa suspension s'est terminée.|

Cet événement n’a pas de données d’événement.

## <a name="gcsuspendeeend_v1-event"></a>Événement GCSuspendEEEnd_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|8|Fin de la suspension du moteur d'exécution pour le garbage collection.|

Cet événement n’a pas de données d’événement.

## <a name="gcsuspendeebegin_v1-event"></a>Événement GCSuspendEEBegin_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|8|Début de la suspension du moteur d'exécution pour le garbage collection.|

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|Le *n* ième garbage collection.|
|`Reason`|`win:UInt32`|Raison de la suspension EE.<br/><br/>`0x0`: Suspendre pour d’autres<br/><br/>`0x1`: Suspend pour GC.<br/><br/>`0x2`: Suspend for AppDomain Shutdown.<br/><br/>`0x3`: Suspend la présentation du code.<br/><br/>`0x4`: Suspendre pour l’arrêt.<br/><br/>`0x5`: Suspend pour le débogueur.<br/><br/>`0x6`: Suspension de la préparation du catalogue global.<br/><br/>`0x7`: Interrompre le balayage du débogueur|

## <a name="gcallocationtick_v3-event"></a>Événement GCAllocationTick_V3

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Verbose (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|10|Chaque fois qu'environ 100 Ko sont alloués.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|Taille de l'allocation, en octets. Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets). Si l'allocation est supérieure, ce champ contient une valeur tronquée. Utilisez `AllocationAmount64` pour les allocations très volumineuses.|
|`AllocationKind`|`win:UInt32`|`0x0` -Allocation d’objets de petite taille (l’allocation est dans le tas de petits objets).<br /><br /> `0x1` -Allocation d’objets volumineux (l’allocation est dans le tas d’objets volumineux).|
|`AllocationAmount64`|`win:UInt64`|Taille de l'allocation, en octets. Cette valeur est correcte pour les allocations très volumineuses.|
|`TypeId`|`win:Pointer`|Adresse de MethodTable. Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).|
|`TypeName`|`win:UnicodeString`|Nom du type ayant été alloué. Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).|
|`HeapIndex`|`win:UInt32`|Segment de mémoire où l'objet a été alloué. Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.|
|`Address`|`win:Pointer`|Adresse du dernier objet alloué.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="gccreateconcurrentthread_v1-event"></a>Événement GCCreateConcurrentThread_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|11|Un thread de garbage collection simultané a été créé.|

Cet événement n’a pas de données d’événement.

## <a name="gcterminateconcurrentthread_v1-event"></a>Événement GCTerminateConcurrentThread_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|
|`ThreadingKeyword` (0x10000)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|12|Un thread de garbage collection simultané s'est terminé.|

Cet événement n’a pas de données d’événement.

## <a name="gcfinalizersbegin_v1-event"></a>Événement GCFinalizersBegin_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|14|Début de l'exécution des finaliseurs.|

Cet événement n’a pas de données d’événement.

## <a name="gcfinalizersend_v1-event"></a>Événement GCFinalizersEnd_V1

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|13|Fin de l'exécution des finaliseurs.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|Nombre de finaliseurs exécutés.|
|`ClrInstanceID`|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|

## <a name="setgchandle-event"></a>Événement SetGCHandle

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCHandleKeyword` 0X2|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`SetGCHandle`|30|Un descripteur GC a été défini.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|Adresse du handle alloué.|
|`ObjectID`|`win:Pointer`|Adresse de l’objet dont le handle a été créé.|
|`Kind`|`win:UInt32`|Type de descripteur GC défini. <br /><br />`0x0`: WeakShort <br/><br/>`0x1`: WeakLong <br /><br />`0x2`: Fort <br /><br />`0x3`: Épinglé <br /><br />`0x4`: Variable<br /><br />`0x5`: RefCounted <br /><br />`0x6`: Dépendant<br /><br />`0x7`: AsyncPinned<br /><br />`0x8`: Handle sizedref|
|`Generation`|`win:UInt32`|Génération de l’objet dont le handle a été créé.|
|`AppDomainID`|`win:UInt64`|ID AppDomain.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="destroygchandle-event"></a>Événement DestroyGCHandle

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCHandleKeyword` 0X2|Informatif (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|31|Un descripteur GC est détruit.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|Adresse du handle détruit.|
|`ClrInstanceID`|win:UInt16|ID unique de l’instance de CoreCLR.|

## <a name="pinobjectatgctime-event"></a>Événement PinObjectAtGCTime

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Détaillé (5)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|33|Un objet a été épinglé pendant un GC.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|Adresse du handle.|
|`ObjectID`|`win:Pointer`|Adresse de l’objet épinglé.|
|`ObjectSize`|`win:UInt64`|Taille de l’objet épinglé.|
|`TypeName`|`win:UnicodeString`|Nom du type de l’objet épinglé.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="gctriggered-event"></a>Événement GCTriggered

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Détaillé (5)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCTriggered`|33|Un GC a été déclenché.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|Raison pour laquelle un GC a été déclenché.<br/><br/>`0x0`: AllocSmall<br/><br/>`0x1`: Induite <br/><br/>`0x2`: LowMemory <br/><br/>`0x3`: Vide <br/><br/>`0x4`: AllocLarge <br/><br/>`0x5`: OutOfSpaceSmallObjectHeap <br/><br/>`0x6`: OutOfSpaceLargeObjectHeap <br/><br/>`0x7`:InducedNoForce <br/><br/>`0x8`: Contrainte <br/><br/>`0x9`: InducedLowMemory|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="increasememorypressure-event"></a>Événement IncreaseMemoryPressure

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informations (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|200|La sollicitation de la mémoire a été augmentée.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`ClrInstanceID`|win:UInt16|ID unique de l’instance de CoreCLR.|

## <a name="decreasememorypressure-event"></a>Événement DecreaseMemoryPressure

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informations (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|201|La sollicitation de la mémoire a été réduite.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|Octets libérés.|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|

## <a name="gcmarkwithtype-event"></a>Événement GCMarkWithType

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Informations (4)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|----------------|---------------|-----------------|
|`GCMarkWithType`|202|Une racine GC a été marquée au cours de la phase de marque GC.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|Numéro du tas.|
|`ClrInstanceID`|win:UInt16|ID unique de l’instance de CoreCLR.|
|`Type`|`win:UInt32`|Type de racine GC.<br/><br/>`0x0`: Pile<br/><br/>`0x1`: Finaliseur<br/><br/>`0x2`: Handle<br/><br/>`0x3`: Plus ancien<br/><br/>`0x4`: Handle sizedref<br/><br/>`0x5`: Dépassement de capacité<br/><br/>|
|`Bytes`|`win:UInt64`|Nombre d’octets marqués.|

## <a name="gcjoin_v2-event"></a>Événement GCJoin_V2

Le tableau suivant montre les mots clés et les niveaux.

|Mot clé pour déclencher l'événement|Level|
|-----------------------------------|-----------|
|`GCKeyword` (0x1)|Détaillé (5)|

Le tableau ci-dessous montre les informations liées aux événements.

|Événement|ID de l’événement|Moment du déclenchement|
|-----------|--------------|-----------------|
|`GCJoin_V2`|203|Thread de GC joint.|

Le tableau ci-dessous montre les données d’événements.

|Nom du champ|Type de données|Description|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|Numéro du tas|
|`JoinTime`|`win:UInt32`|Indique si cet événement est déclenché au début d’une jointure ou d’une fin de jointure (pour le début de la jointure `0x0` , pour la fin de la `0x1` jointure)|
|`JoinType`|`win:UInt32`|Type de jointure. <br/><br/>`0x0`: Dernière jointure<br/><br/>`0x1`: Joindre <br/><br/>`0x2`: Redémarrer <br/><br/>`0x3`: Première jointure inverse<br/><br/>`0x4`: Jointure inverse<br/><br/>|
|`ClrInstanceID`|`win:UInt16`|ID unique de l’instance de CoreCLR.|
