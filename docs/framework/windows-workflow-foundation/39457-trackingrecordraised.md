---
title: 39457 - TrackingRecordRaised
ms.date: 03/30/2017
ms.assetid: 5a2731d1-c731-4b79-bb69-016cb69ef481
ms.openlocfilehash: 5bf343f29528bdb3941e253b2fd5b39799d94c2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275903"
---
# <a name="39457---trackingrecordraised"></a>39457 - TrackingRecordRaised

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|39457|  
|Mots clés|WFRuntime|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'un TrackingRecord a été déclenché dans un TrackingParticipant.  
  
## <a name="message"></a>Message  

 Enregistrement suivi %1 élevé à %2.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|RecordNumber|xs:string|Numéro d'enregistrement de suivi.|  
|ParticipantId|xs:string|Participant de suivi.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
