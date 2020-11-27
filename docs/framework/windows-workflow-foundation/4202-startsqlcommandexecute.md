---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: d3f27c6ed28efe9d099dcedfc676b839ae9b1dee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275838"
---
# <a name="4202---startsqlcommandexecute"></a>4202 - StartSqlCommandExecute

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|4202|  
|Mots clés|WFInstanceStore|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'une commande SQL est exécutée.  
  
## <a name="message"></a>Message  

 Démarrage de l'exécution de la commande SQL : %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|SqlCommand|xs:string|Commande SQL exécutée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
