---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 2fc509dac7e13f30f74c24d8b98cba55ed5f8e1d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275113"
---
# <a name="1028---completetransactioncontextworkitem"></a>1028 - CompleteTransactionContextWorkItem

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1028|  
|Mots clés|WFRuntime|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'un TransactionContextWorkItem est terminé.  
  
## <a name="message"></a>Message  

 TransactionContextWorkItem est terminé pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
