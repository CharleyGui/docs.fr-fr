---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: b8bf8431c4e2b82c6aac95820eb45de2a404e976
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294272"
---
# <a name="1035---runtimetransactionset"></a>1035 - RuntimeTransactionSet

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1035|  
|Mots clés|WFRuntime|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'une activité a défini la transaction d'exécution.  
  
## <a name="message"></a>Message  

 La transaction d’exécution a été définie par l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».  Exécution isolée de l’activité' %4 ', DisplayName : ' %5 ', InstanceId : ' %6 '.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|IsolatedActivity|xs:string|Nom de type de l’activité dans laquelle la transaction est isolée.|  
|IsolatedActivityDisplayName|xs:string|Nom complet de l’activité dans laquelle la transaction est isolée.|  
|IsolatedActivityInstanceId|xs:string|ID d’instance de l’activité dans laquelle la transaction est isolée.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
