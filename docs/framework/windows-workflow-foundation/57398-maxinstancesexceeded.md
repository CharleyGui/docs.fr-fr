---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289176"
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|57398|  
|Mots clés|WFServices|  
|Level|Avertissement|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Indique que le système a atteint la limite définie pour la limitation des « MaxConcurrentInstances ».  
  
## <a name="message"></a>Message  

 Le système a atteint la limite définie pour la limitation des 'MaxConcurrentInstances'. La limite a été définie sur %1. La valeur de limitation peut être modifiée en modifiant l'attribut « maxConcurrentInstances » de l'élément serviceThrottle ou en modifiant la propriété « MaxConcurrentInstances » à l'aide du comportement ServiceThrottlingBehavior.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom|xs:string|Nom de l'élément.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
