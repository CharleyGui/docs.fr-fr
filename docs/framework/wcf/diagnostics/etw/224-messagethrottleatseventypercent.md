---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 26b860b88313a971960a65b599562ef1ccb4e7da
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243519"
---
# <a name="224---messagethrottleatseventypercent"></a>224 - MessageThrottleAtSeventyPercent

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|224|  
|Mots clés|EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel|  
|Level|Avertissement|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 L'événement `MessageThrottleExceeded` est émis lorsque l'un des accélérateurs de service principaux a été dépassé. Cet événement est émis lorsque le pic d'activité diminue et que la valeur actuelle de l'accélérateur est de 70 % de la limitation actuellement définie. Notez que cet événement n'est émis que lorsque l'activité ralentit. Si la valeur actuelle tourne autour de 70 %, (par exemple, 70,69,70,71,70,69), seule la première occurrence de 70 % provoque un événement. Une fois cet événement émis, les prochains dépassements de la limitation définie pour l'accélérateur entraînent un événement `MessageThrottleExceeded`.  
  
## <a name="message"></a>Message  

 La valeur de la limitation '%1' de '%2' est à 70%%.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom de l'accélérateur|`xs:string`|Nom de l'accélérateur qui a été dépassé. `MaxConcurrentCalls`, `MaxConcurrentInstances` ou  `MaxConcurrentSessions`.|  
|Limite|`xs:long`|Limitation configurée actuellement pour l'accélérateur.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ». Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
