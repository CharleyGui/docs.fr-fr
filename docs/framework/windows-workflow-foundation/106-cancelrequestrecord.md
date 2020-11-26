---
title: 106 - CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: e7b736d78486b0de7c108e6212d2aa1857e01cc4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238897"
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|Id|106|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis par le participant de suivi ETW lorsqu'une activité dans une instance de workflow émet un événement cancelrequestedrecord.  
  
## <a name="message"></a>Message  

 TrackRecord = CancelRequestedRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityId=%5, ActivityInstanceId=%6, ActivityTypeName =% 7, ChildActivityName =% 8, ChildActivityId =% 9, ChildActivityInstanceId =% 10, ChildActivityTypeName =% 11, Annotations=%12, ProfileName =% 13  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|Nom|xs:string|Nom de l'activité qui a demandé l'opération d'annulation|  
|ActivityId|xs:string|ID de l'activité qui a demandé l'opération d'annulation|  
|ActivityInstanceId|xs:string|ID d'instance de l'activité qui a demandé l'opération d'annulation|  
|ActivityTypeName|xs:string|Type de l'activité qui a demandé l'opération d'annulation|  
|ChildActivityName|xs:string|Nom de l'activité qui est annulée|  
|ChildActivityId|xs:string|ID de l'activité qui est annulée|  
|ChildActivityInstanceId|xs:string|ID d'instance de l'activité qui est annulée|  
|ChildActivityTypeName|xs:string|Type de l'activité qui est annulée|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "annotationName" type="System.String"> annotationValue \</item> \</items> .  Si aucune annotation n’est spécifiée, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur d’annotation par \<items> ... \</items> .|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini comme suit : « nom du site Web chemin d’accès virtuel de l’application&#124;chemin d’accès virtuel du service&#124;ServiceName » exemple : « site Web par défaut/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService »|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
