---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 42ed23654622e29df8ffc210c8d5ba572fa69fd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275347"
---
# <a name="1021---schedulebookmarkworkitem"></a>1021 - ScheduleBookmarkWorkItem

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1021|  
|Mots clés|WFRuntime|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'un BookmarkWorkItem a été planifié.  
  
## <a name="message"></a>Message  

 Un BookmarkWorkItem a été planifié pour l’activité « %1 », DisplayName : « %2 », InstanceId : « %3 ».  BookmarkName : %4, BookmarkScope : %5.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Activité|xs:string|Nom de type de l'activité.|  
|DisplayName|xs:string|Nom complet de l'activité.|  
|InstanceId|xs:string|ID d'instance de l'activité.|  
|BookmarkName|xs:string|Nom du signet.|  
|BookmarkScope|xs:string|Portée du signet.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
