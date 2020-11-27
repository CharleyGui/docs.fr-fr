---
title: 404 - ResumeSignpostEvent
ms.date: 03/30/2017
ms.assetid: 395cc7ca-f35f-4295-be97-39a077f99c97
ms.openlocfilehash: 81b28a5f1ee0470b211ce0c8efbfaffc597de46e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288916"
---
# <a name="404---resumesignpostevent"></a>404 - ResumeSignpostEvent

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|404|  
|Mots clés|Dépannage|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement marque la reprise d'une activité de bout en bout. Il contient le nom de l'activité.  
  
## <a name="message"></a>Message  

 Limite d'activité.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Données étendues|`xs:string`|Nom de l’activité.|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
