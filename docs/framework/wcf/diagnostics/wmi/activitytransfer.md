---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291113"
---
# <a name="activitytransfer"></a>ActivityTransfer

Événement du transfert de l'activité  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe ActivityTransfer ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe ActivityTransfer a les propriétés suivantes :  
  
### <a name="activityid"></a>ActivityID  
  
- Type de données : objet  
    Type d'accès : Lecture seule  
  
- ID d’activité  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- Type de données : objet  
    Type d'accès : Lecture seule  
  
- ID d'activité connexe  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel.|
