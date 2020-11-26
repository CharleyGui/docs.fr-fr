---
title: 3501 - InferredContractDescription
ms.date: 03/30/2017
ms.assetid: 21a70849-4fc0-41d2-b9a4-db5aa2acdf1a
ms.openlocfilehash: 88a04c0eb6d12876592702ad4dba3a17aa8da122
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245287"
---
# <a name="3501---inferredcontractdescription"></a>3501 - InferredContractDescription

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|3501|  
|Mots clés|WFServices|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Indique qu'un ContractDescription a été déduit de WorkflowService.  
  
## <a name="message"></a>Message  

 ContractDescription avec Name='%1' et Namespace='%2' a été déduit de WorkflowService.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Nom|xs:string|Nom de ContractDescription.|  
|Espace de noms|xs:string|Espace de noms de ContractDescription.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
