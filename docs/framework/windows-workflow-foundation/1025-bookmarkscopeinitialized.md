---
title: 1025 - BookmarkScopeInitialized
ms.date: 03/30/2017
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
ms.openlocfilehash: 47b4813c21ef637922117d5adf41b3c907c57f32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275269"
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 - BookmarkScopeInitialized

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|1025|  
|Mots clés|WFRuntime|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique qu'un BookmarkScope a été initialisé.  
  
## <a name="message"></a>Message  

 Le BookmarkScope avec TemporaryId : « %1 » a été initialisé avec l'ID : « %2 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:string|ID temporaire du signet.|  
|InitializedId|xs:string|Identificateur initialisé du signet.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
