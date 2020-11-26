---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: 832ced406b6079fad8f4b9bea512a6d390bdcc0f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241939"
---
# <a name="219---serviceexception"></a>219 - ServiceException

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|219|  
|Mots clés|EndToEndMonitoring, HealthMonitoring, Dépannage, ServiceModel|  
|Level|Error|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis lorsqu'un service WCF rencontre une exception non gérée. Cela inclut les exceptions non gérées pendant l'activation, pendant le traitement du message et dans le code utilisateur.  
  
## <a name="message"></a>Message  

 Une exception non gérée de type '%2' s'est produite lors du traitement du message. Exception totale ToString : %1.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ExceptionToString|`xs:string`|Résultat de l'appel à `ToString`() sur l'exception CLR.|  
|ExceptionTypeName|`xs:string`|CLR FullName du type de l'exception.|  
|HostReference|`xs:string`|Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web. Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ». Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».|  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
