---
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 6e43b0ab1e2d35657bae43e7239a677643154fa9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238728"
---
# <a name="1101---workflowactivitystart"></a>1101 - WorkflowActivityStart

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1101|  
|Mots clés|WFRuntime|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'une activité du flux de travail a démarré.  
  
## <a name="message"></a>Message  

 ID WorkflowInstance : « %1 » Activité E2E  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|ID de l'instance de flux de travail.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
