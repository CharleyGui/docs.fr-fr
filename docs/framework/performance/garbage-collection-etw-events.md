---
title: Événements ETW de garbage collection
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5e10a1dc1ad3230213a20b850741a6ec0468294
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616422"
---
# <a name="garbage-collection-etw-events"></a>Événements ETW de garbage collection
<a name="top"></a> Ces événements collectent des informations relatives au garbage collection. Ils vous aident dans le diagnostic et le débogage, y compris pour déterminer combien de fois le garbage collection a été effectué, la quantité de mémoire libérée pendant le garbage collection, etc.  
  
 Cette catégorie comprend les événements suivants :  
  
- [Événement GCStart_V1](#gcstart_v1_event)  
  
- [Événement GCEnd_V1](#gcend_v1_event)  
  
- [Événement GCHeapStats_V1](#gcheapstats_v1_event)  
  
- [Événement GCCreateSegment_V1](#gccreatesegment_v1_event)  
  
- [Événement GCFreeSegment_V1](#gcfreesegment_v1_event)  
  
- [Événement GCRestartEEBegin_V1](#gcrestarteebegin_v1_event)  
  
- [Événement GCRestartEEEnd_V1](#gcrestarteeend_v1_event)  
  
- [Événement GCSuspendEE_V1](#gcsuspendee_v1_event)  
  
- [Événement GCSuspendEEEnd_V1](#gcsuspendeeend_v1_event)  
  
- [Événement GCAllocationTick_V2](#gcallocationtick_v2_event)  
  
- [Événement GCFinalizersBegin_V1](#gcfinalizersbegin_v1_event)  
  
- [Événement GCFinalizersEnd_V1](#gcfinalizersend_v1_event)  
  
- [Événement GCCreateConcurrentThread_V1](#gccreateconcurrentthread_v1_event)  
  
- [Événement GCTerminateConcurrentThread_V1](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstartv1-event"></a>Événement GCStart_V1  
 Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|1|Un garbage collection a démarré.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Nombre|win:UInt32|Le *n*ième garbage collection.|  
|Profondeur|win:UInt32|La génération est collectée.|  
|Raison|win:UInt32|Pourquoi le garbage collection a été déclenché :<br /><br /> 0x0 – Allocation de tas de petits objets.<br /><br /> 0x1 – Induit.<br /><br /> 0x2 – Mémoire insuffisante.<br /><br /> 0x3 – Vide.<br /><br /> 0x4 – Allocation de tas d'objets volumineux.<br /><br /> 0x5 – Espace insuffisant (pour un tas de petits objets)<br /><br /> 0x6 – Espace insuffisant (pour un tas d'objets volumineux)<br /><br /> 0x7 – Induit mais non forcé comme blocage|  
|Type|win:UInt32|0x0 – Un blocage de garbage collection s'est produit en dehors du garbage collection d'arrière-plan.<br /><br /> 0x1 – Garbage collection d'arrière-plan.<br /><br /> 0x2 – Un blocage de garbage collection s'est produit pendant le garbage collection d'arrière-plan.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcendv1-event"></a>Événement GCEnd_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|2|Un garbage collection s'est terminé.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Nombre|win:UInt32|Le *n*ième garbage collection.|  
|Profondeur|win:UInt32|Génération ayant été collectée.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstatsv1-event"></a>Événement GCHeapStats_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Description|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|4|Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|GenerationSize0|win:UInt64|Taille, en octets, de la mémoire de génération 0.|  
|TotalPromotedSize0|win:UInt64|Nombre d'octets promus de la génération 0 à la génération 1.|  
|GenerationSize1|win:UInt64|Taille, en octets, de la mémoire de génération 1.|  
|TotalPromotedSize1|win:UInt64|Nombre d'octets promus de la génération 1 à la génération 2.|  
|GenerationSize2|win:UInt64|Taille, en octets, de la mémoire de génération 2.|  
|TotalPromotedSize2|win:UInt64|Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.|  
|GenerationSize3|win:UInt64|Taille, en octets, du tas des objets volumineux.|  
|TotalPromotedSize3|win:UInt64|Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.|  
|FinalizationPromotedSize|win:UInt64|Taille totale, en octets, des objets qui sont prêts pour la finalisation.|  
|FinalizationPromotedSize|win:UInt64|Nombre d'objets qui sont prêts pour la finalisation.|  
|PinnedObjectCount|win:UInt32|Nombre d'objets (non déplaçables) épinglés.|  
|SinkBlockCount|win:UInt32|Nombre de blocs de synchronisation en cours d'utilisation.|  
|GCHandleCount|win:UInt32|Nombre de handles de garbage collection en cours d'utilisation.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegmentv1-event"></a>Événement GCCreateSegment_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|5|Un nouveau segment de garbage collection a été créé. En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Adresse|win:UInt64|Adresse du segment.|  
|Taille|win:UInt64|Taille du segment.|  
|Type|win:UInt32|0x0 – Tas de petits objets.<br /><br /> 0x1 – Tas d'objets volumineux.<br /><br /> 0x2 – Tas en lecture seule.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques. Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.  
  
 [Retour au début](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegmentv1-event"></a>Événement GCFreeSegment_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|6|Un nouveau segment de garbage collection a été libéré.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Adresse|win:UInt64|Adresse du segment.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebeginv1-event"></a>Événement GCRestartEEBegin_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|7|La reprise du common language runtime après sa suspension a commencé.|  
  
 Aucune donnée d'événement.  
  
 [Retour au début](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeendv1-event"></a>Événement GCRestartEEEnd_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|3|La reprise du common language runtime après sa suspension s'est terminée.|  
  
 Aucune donnée d'événement.  
  
 [Retour au début](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendeev1-event"></a>Événement GCSuspendEE_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|9|Début de la suspension du moteur d'exécution pour le garbage collection.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Raison|win:UInt16|0x0 – Autre.<br /><br /> 0x1 – Garbage collection.<br /><br /> 0x2 – Fermeture du domaine d'application.<br /><br /> 0x3 – Pitching de code.<br /><br /> 0x4 – Arrêt.<br /><br /> 0x5 – Débogueur.<br /><br /> 0x6 – Préparation pour le garbage collection.|  
|Nombre|win:UInt32|Nombre GC à ce moment-là. En règle générale, vous verrez un événement de démarrage de GC par la suite et son nombre doit être égal à ce nombre + 1 à mesure que nous augmentons l’index GC pendant un garbage collection.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeendv1-event"></a>Événement GCSuspendEEEnd_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|8|Fin de la suspension du moteur d'exécution pour le garbage collection.|  
  
 Aucune donnée d'événement.  
  
 [Retour au début](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtickv2-event"></a>Événement GCAllocationTick_V2  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|10|Chaque fois qu'environ 100 Ko sont alloués.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|AllocationAmount|win:UInt32|Taille de l'allocation, en octets. Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets). Si l'allocation est supérieure, ce champ contient une valeur tronquée. Utilisez `AllocationAmount64` pour les allocations très volumineuses.|  
|AllocationKind|win:UInt32|0x0 – Allocation de petits objets (l'allocation se fait dans le tas de petits objets).<br /><br /> 0x1 – Allocation d'objets volumineux (l'allocation se fait dans le tas des objets volumineux).|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
|AllocationAmount64|win:UInt64|Taille de l'allocation, en octets. Cette valeur est correcte pour les allocations très volumineuses.|  
|TypeId|win:Pointer|Adresse de MethodTable. Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).|  
|TypeName|win:UnicodeString|Nom du type ayant été alloué. Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).|  
|HeapIndex|win:UInt32|Segment de mémoire où l'objet a été alloué. Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.|  
  
 [Retour au début](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbeginv1-event"></a>Événement GCFinalizersBegin_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|14|Début de l'exécution des finaliseurs.|  
  
 Aucune donnée d'événement.  
  
 [Retour au début](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersendv1-event"></a>Événement GCFinalizersEnd_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|13|Fin de l'exécution des finaliseurs.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|Nombre|win:UInt32|Nombre de finaliseurs exécutés.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Retour au début](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthreadv1-event"></a>Événement GCCreateConcurrentThread_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|11|Un thread de garbage collection simultané a été créé.|  
  
 Aucune donnée d'événement.  
  
 [Retour au début](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthreadv1-event"></a>Événement GCTerminateConcurrentThread_V1  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`GCKeyword` (0x1)|Informatif (4)|  
|`ThreadingKeyword` (0x10000)|Informatif (4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|12|Un thread de garbage collection simultané s'est terminé.|  
  
 Aucune donnée d'événement.  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md)
