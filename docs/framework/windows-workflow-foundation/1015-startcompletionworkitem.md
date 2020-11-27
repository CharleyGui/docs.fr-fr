---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: c0d8572f192a8faa22327fd671cd9ea49c5054ca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275542"
---
# <a name="1015---startcompletionworkitem"></a>1015 - StartCompletionWorkItem

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1015|  
|Mots clés|WFRuntime|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'un CompletionWorkItem démarre l'exécution.  
  
## <a name="message"></a>Message  

 Début de l'exécution d'un CompletionWorkItem pour l'activité parente « %1 », DisplayName : « %2 », InstanceId : « %3 ». Activité terminée « %4 », DisplayName : « %5 », InstanceId : « %6 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|Nom de type de l'activité parente.|  
|ParentDisplayName|xs:string|Nom complet de l'activité parente.|  
|ParentInstanceId|xs:string|ID d'instance de l'activité parente.|  
|CompletedActivity|xs:string|Nom de type de l'activité achevée.|  
|CompletedActivityDisplayName|xs:string|Nom complet de l'activité achevée.|  
|CompletedActivityInstanceId|xs:string|ID d'instance de l'activité achevée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
