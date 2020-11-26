---
title: 1148 - FlowchartSwitchCaseNotFound
ms.date: 03/30/2017
ms.assetid: 9ee7fcee-e040-4306-968e-ed840a1cb00c
ms.openlocfilehash: fb9f4be3dba0f8632f1ae074ad9ddb726c5d84ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241705"
---
# <a name="1148---flowchartswitchcasenotfound"></a>1148 - FlowchartSwitchCaseNotFound

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1148|  
|Mots clés|WFActivities|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'une correspondance de cas ou un cas par défaut est introuvable dans un organigramme. L'exécution de Flowchart va se terminer.  
  
## <a name="message"></a>Message  

 Flowchart « %1 »/FlowSwitch - impossible de trouver l'activité Case ou un cas par défaut correspondant au résultat de l'expression. L'exécution de Flowchart va se terminer.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Organigramme|xs:string|Nom complet de l'organigramme.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
