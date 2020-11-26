---
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 66251141cdf66c18ad0c1334f6f3e6c0629b4b33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241055"
---
# <a name="403---suspendsignpostevent"></a>403 - SuspendSignpostEvent

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|403|  
|Mots clés|Dépannage|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement marque l'interruption d'une activité de bout en bout. Il contient le nom de l'activité.  
  
## <a name="message"></a>Message  

 Limite d'activité.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Données étendues|`xs:string`|Nom de l’activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
