---
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 48182d7c5fe8f29842a17f28c0ea296f93b31089
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251254"
---
# <a name="4206---unlockinstanceexception"></a>4206 - UnlockInstanceException

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|4206|  
|Mots clés|WFInstanceStore|  
|Level|Error|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'une exception s'est produite lors de la tentative de déverrouillage d'une instance.  
  
## <a name="message"></a>Message  

 Exception %1 rencontrée lors de la tentative de déverrouillage de l'instance.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:string|Message de l'exception SQL.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
