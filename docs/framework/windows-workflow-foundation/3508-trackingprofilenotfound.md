---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 23262427c3da730eaf930a8b483c7c4d4ec3a3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289839"
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|3508|  
|Mots clés|WFServices|  
|Level|Commentaires|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Indique si un TrackingProfile est introuvable dans le fichier de configuration ou un ActivityDefinitionId ne correspond pas au modèle.  
  
## <a name="message"></a>Message  

 TrackingProfile « %1 » pour le ActivityDefinitionId « %2 » introuvable. TrackingProfile est introuvable dans le fichier de configuration ou ActivityDefinitionId ne correspond pas.  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|Nom du modèle de suivi.|  
|ActivityDefinitionId|xs:string|ID de définition d'activité.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
