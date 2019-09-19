---
title: Événements ETW d'analyse de ressource de domaine d'application
ms.date: 03/30/2017
helpviewer_keywords:
- ETW, application domain monitoring events
- application domain monitoring events [.NET Framework]
ms.assetid: d38ff268-a2ee-434e-b504-d570880e0289
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0e4002ae248022a9e4380c79174109494b5e4ca
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046768"
---
# <a name="application-domain-resource-monitoring-arm-etw-events"></a>Événements ETW d'analyse de ressource de domaine d'application
<a name="top"></a> Ces événements fournissent des informations de diagnostic détaillées sur l'état d'un domaine d'application. Vous pouvez utiliser ces événements ou la fonctionnalité ARM d'analyse de ressource de domaine d'application pour obtenir les mêmes informations.  
  
 Cette catégorie comprend les événements suivants :  
  
- [Événement ThreadCreated](#threadcreated_event)  
  
- [Événement AppDomainMemAllocated](#appdomainmemallocated_event)  
  
- [Événement AppDomainMemSurvived](#appdomainmemsurvived_event)  
  
- [Événement ThreadAppDomainEnter](#threadappdomainenter_event)  
  
- [Événement ThreadTerminated](#threadterminated_event)  
  
<a name="threadcreated_event"></a>   
## <a name="threadcreated-event"></a>Événement ThreadCreated  
 Cet événement est également déclenché sous le fournisseur d'arrêt en tant que `ThreadDC` (sous le mot clé `AppDomainResourceManagementRundownKeyword` ). Il s’agit du seul événement déclenché sous le fournisseur d'arrêt dans cette catégorie.  
  
 Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informatif(4)|  
|`ThreadingKeyword` (0x10000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ThreadCreated`|85|Un thread a été créé pour le domaine d'application.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|ID du thread qui a été créé.|  
|AppDomainID|win:UInt64|Identificateur du domaine d'application pour lequel l'activité du thread est signalée.|  
|Indicateurs|win:UInt32|Indicateurs de création de thread.|  
|ManagedThreadIndex|win:UInt32|Index managé du thread qui a été créé.|  
|OSThreadID|win:UInt32|ID de système d’exploitation du thread qui a été créé.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Revenir en haut](#top)  
  
<a name="appdomainmemallocated_event"></a>   
## <a name="appdomainmemallocated-event"></a>Événement AppDomainMemAllocated  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`AppDomainMemAllocated`|83|Chaque bloc de 4 Mo de mémoire (environ) est alloué dans le domaine d'application.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identificateur du domaine d'application pour lequel l'utilisation des ressources est signalée.|  
|Allocated|win:UInt64|Nombre total d'octets alloués dans ce domaine d'application depuis sa création (la quantité de mémoire libérée n'est pas soustraite).|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Revenir en haut](#top)  
  
<a name="appdomainmemsurvived_event"></a>   
## <a name="appdomainmemsurvived-event"></a>Événement AppDomainMemSurvived  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`AppDomainMemSurvived`|84|Chaque garbage collection est terminé.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|AppDomainID|win:UInt64|Identificateur du domaine pour lequel l’utilisation des ressources est signalée.|  
|Survived|win:UInt64|Nombre d'octets ayant survécu après la dernière collection et qui sont conservés par ce domaine d'application. Ce nombre est exact et complet après une collection complète, mais peut être incomplet après une collection éphémère.|  
|ProcessSurvived|win:UInt64|Nombre total d'octets qui ont survécu à la dernière collection. Après une collection complète, ce nombre représente le nombre d'octets maintenus actifs dans les tas managés. Après une collection éphémère, ce nombre représente le nombre d'octets maintenus actifs dans les générations éphémères.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Revenir en haut](#top)  
  
<a name="threadappdomainenter_event"></a>   
## <a name="threadappdomainenter-event"></a>Événement ThreadAppDomainEnter  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informatif(4)|  
|`ThreadingKeyword` (0x10000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ThreadAppDomainEnter`|87|Un thread entre dans un domaine d'application.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|Identificateur du thread.|  
|AppDomainID|win:UInt64|Identificateur du domaine d'application.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
 [Revenir en haut](#top)  
  
<a name="threadterminated_event"></a>   
## <a name="threadterminated-event"></a>Événement ThreadTerminated  
 Le tableau suivant montre les mots clés et les niveaux.  
  
|Mot clé pour déclencher l'événement|Niveau|  
|-----------------------------------|-----------|  
|`AppDomainResourceManagementKeyword` (0x800)|Informatif(4)|  
|`ThreadingKeyword` (0x10000)|Informatif(4)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID d'événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`ThreadTerminated`|86|Un thread se termine.|  
  
 Le tableau ci-dessous montre les données d’événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ThreadID|win:UInt64|Identificateur du thread.|  
|AppDomainID|win:UInt64|Identificateur du domaine d'application.|  
|ClrInstanceID|win:UInt16|ID unique de l'instance de CLR ou CoreCLR.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
