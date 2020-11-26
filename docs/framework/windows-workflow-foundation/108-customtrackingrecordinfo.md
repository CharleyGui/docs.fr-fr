---
title: 108 - CustomTrackingRecordInfo
ms.date: 03/30/2017
ms.assetid: 5bee501e-4e00-42cd-b949-e88009c3d4e8
ms.openlocfilehash: 5fe45d62446d4dee23d29bed03dd490d8cb8efb8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238845"
---
# <a name="108---customtrackingrecordinfo"></a>108 - CustomTrackingRecordInfo

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|Id|108|  
|Mots clés|UserEvents, EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis par le participant de suivi ETW lorsqu'une activité au sein d'une instance de workflow émet un événement CustomTrackingRecord avec informations sur le niveau.  
  
## <a name="message"></a>Message  

 TrackRecord = CustomTrackingRecord, InstanceID = %1, RecordNumber=%2, EventTime=%3, Name=%4, ActivityName=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Data=%9, Annotations=%10, ProfileName = %11  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|Nom|xs:string|Nom de l'événement CustomTrackingRecord|  
|ActivityName|xs:string|Nom de l'activité qui a émis l'événement CustomTrackingRecord|  
|ActivityId|xs:string|ID de l'activité qui a émis l'événement CustomTrackingRecord|  
|ActivityInstanceId|xs:string|ID d'instance de l'activité qui a émis l'événement CustomTrackingRecord|  
|ActivityTypeName|xs:string|Nom de l'activité qui a émis l'événement CustomTrackingRecord|  
|Données|xs:string|Données suivies avec cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "dataName" type="System.String"> DataValue \</item> \</items> .  Si aucune donnée n’a été suivie, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur de données par \<items> ... \</items> .  Les types suivants sont stockés comme valeur retournée par ToString (); String, Char, bool, int, Short, long, uint, ushort, ulong, System. Single, float, double, System. Guid, System. DateTimeOffset, System. DateTime.  Tous les autres types sont sérialisés à l'aide de System.Runtime.Serialization.NetDataContractSerializer.|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "annotationName" type="System.String"> annotationValue \</item> \</items> .  Si aucune annotation n’est spécifiée, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur d’annotation par \<items> ... \</items> .|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini comme suit : « nom du site Web chemin d’accès virtuel de l’application&#124;chemin d’accès virtuel du service&#124;ServiceName » exemple : « site Web par défaut/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService »|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
