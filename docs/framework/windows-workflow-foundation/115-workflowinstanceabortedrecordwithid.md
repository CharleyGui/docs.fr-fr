---
title: 115 - WorkflowInstanceAbortedRecordWithId
ms.date: 03/30/2017
ms.assetid: 0293dd4e-e6ae-473a-b3d6-c2d38f9bd875
ms.openlocfilehash: 69c0c58de36a7fff916b11deba888b7cef7c626e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285146"
---
# <a name="115---workflowinstanceabortedrecordwithid"></a>115 - WorkflowInstanceAbortedRecordWithId

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|115|  
|Mots clés|HealthMonitoring, WFTracking|  
|Level|Avertissement|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceAbortedRecord.  
  
## <a name="message"></a>Message  

 TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7, WorkflowDefinitionIdentity = %8  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|ActivityDefinitionId|xs:string|Nom de l'activité racine dans le workflow|  
|State|xs:string|État actuel du workflow.|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement. Les valeurs sont stockées dans un élément XML au format \<items> \< item name = "annotationName" type="System.String"> annotationValue \</item> \</items> . Si aucune annotation n’est spécifiée, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur d’annotation par \<items> ... \</items> .|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|WorkflowDefinitionIdentity|xs:string|ID de flux de travail.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
