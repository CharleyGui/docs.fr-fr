---
title: 103 - ActivityStateRecord
ms.date: 03/30/2017
ms.assetid: 57636a9a-561e-44aa-aef9-1f1894aaa6dd
ms.openlocfilehash: 02c33f02b7650c9f9b7527c319de3b58980fdd6c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275074"
---
# <a name="103---activitystaterecord"></a>103 - ActivityStateRecord

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|Id|103|  
|Mots clés|EndToEndMonitoring, Dépannage, HealthMonitoring, WFTracking|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis par le participant de suivi ETW lorsqu'une activité dans une instance de workflow émet un événement ActivityStateRecord.  
  
## <a name="message"></a>Message  

 TrackRecord = ActivityStateRecord, InstanceID =% 1, RecordNumber=%2, EventTime=%3, état =% 4, Name=%5, ActivityId=%6, ActivityInstanceId=%7, ActivityTypeName=%8, Arguments=%9, Variables=%10, Annotations=%11, ProfileName =% 12  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ID d'instance pour le workflow|  
|RecordNumber|xs:long|Numéro de séquence de l'enregistrement émis.|  
|EventTime|xs:dateTime|Heure au format UTC à laquelle l'événement a été émis|  
|State|xs:string|État de l'activité.|  
|Nom|xs:string|Nom de l'activité qui a émis l'événement|  
|ActivityId|xs:string|ID d'activité de l'activité émettrice|  
|ActivityInstanceId|xs:string|ID d'instance de l'activité de l'activité émettrice|  
|ActivityTypeName|xs:string|Nom de type de l'activité émettrice|  
|Arguments|xs:string|Arguments suivis avec cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "argumentName" type="System.String"> argumentValue \</item> \</items> .  Si aucun argument n’a été suivi, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur d’annotation par \<items> ... \</items> .  Les types suivants sont stockés comme valeur retournée par ToString (); String, Char, bool, int, Short, long, uint, ushort, ulong, System. Single, float, double, System. Guid, System. DateTimeOffset, System. DateTime.  Tous les autres types sont sérialisés à l'aide de System.Runtime.Serialization.NetDataContractSerializer.|  
|Variables|xs:string|Les variables suivies avec cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "variableName" type="System.String"> VariableValue \</item> \</items> .  Si aucune variable n’a été suivie, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur des variables par \<items> ... \</items> .  Les types suivants sont stockés comme valeur retournée par ToString (); String, Char, bool, int, Short, long, uint, ushort, ulong, System. Single, float, double, System. Guid, System. DateTimeOffset, System. DateTime.  Tous les autres types sont sérialisés à l'aide de System.Runtime.Serialization.NetDataContractSerializer.|  
|Annotations|xs:string|Annotations ayant été ajoutées à cet événement.  Les valeurs sont stockées dans un élément XML au format \<items> \< item  name = "annotationName" type="System.String"> annotationValue \</item> \</items> .  Si aucune annotation n’est spécifiée, la chaîne contient \<items/> . La taille d'événement ETW est limitée par la taille de la mémoire tampon ETW ou par la charge utile maximale pour un événement ETW. Si la taille de l’événement dépasse les limites ETW, l’événement est tronqué en supprimant les annotations et en remplaçant la valeur d’annotation par \<items> ... \</items> .|  
|ProfileName|xs:string|Nom ou modèle de suivi qui a provoqué l'émission de cet événement|  
|HostReference|xs:string|Pour les services hébergés sur le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.  Son format est défini comme suit : « nom du site Web chemin d’accès virtuel de l’application&#124;chemin d’accès virtuel du service&#124;ServiceName » exemple : « site Web par défaut/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService »|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
