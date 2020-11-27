---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 0d6326889077e36ad49aa6267ae7285849c6818d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275864"
---
# <a name="4201---endsqlcommandexecute"></a>4201 - EndSqlCommandExecute

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|4201|  
|Mots clés|WFInstanceStore|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique que l'exécution d'une commande SQL est terminée.  
  
## <a name="message"></a>Message  

 Fin de l'exécution de la commande SQL : %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|Commande SQL exécutée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
