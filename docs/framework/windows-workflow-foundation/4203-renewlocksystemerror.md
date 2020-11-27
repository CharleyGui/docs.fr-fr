---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 17617e25c5cf8cecae608438529e9ce1a7d506f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251267"
---
# <a name="4203---renewlocksystemerror"></a>4203 - RenewLockSystemError

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|4203|  
|Mots clés|WFInstanceStore|  
|Level|Error|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique que le fournisseur SQL n'a pas pu étendre l'expiration du verrou, car l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé. Le SqlWorkflowInstanceStore sera annulé.  
  
## <a name="message"></a>Message  

 Échec de l'extension de l'expiration du verrou ; l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé. Abandon de SqlWorkflowInstanceStore.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
