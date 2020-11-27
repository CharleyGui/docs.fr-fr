---
title: 102 - WorkflowInstanceAbortedRecord
ms.date: 03/30/2017
ms.assetid: bde4378d-4eea-4907-aaf2-c1a2bc770a37
ms.openlocfilehash: a48e3e27787a9f6dd133240f20ed67230d837698
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275464"
---
# <a name="102---workflowinstanceabortedrecord"></a>102 - WorkflowInstanceAbortedRecord

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|Id|102|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Level|Avertissement|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis par le participant de suivi ETW lorsqu'une instance de workflow émet un événement WorkflowInstanceAbortedRecord.  
  
## <a name="message"></a>Message  

 TrackRecord = WorkflowInstanceAbortedRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, Reason = %5, Annotations = %6, ProfileName = %7  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|ActivityDefinitionId|xs:string|Nom de l'activité racine dans le workflow|  
|Motif|xs:string|Raison pour laquelle le workflow a été abandonné|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "annotationName" type="System.String"> annotationValue \</item> \</items> .  Si aucune annotation n’est spécifiée, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur d’annotation par \<items> ... \</items> .|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini comme suit : « nom du site Web chemin d’accès virtuel de l’application&#124;chemin d’accès virtuel du service&#124;ServiceName » exemple : « site Web par défaut/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService »|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
