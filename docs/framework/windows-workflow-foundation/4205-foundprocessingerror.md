---
title: 4205 - FoundProcessingError
ms.date: 03/30/2017
ms.assetid: f2235a15-dd87-439e-8cb9-8b1b89a3dacf
ms.openlocfilehash: 2931d3723a04d7970197c9ebd79dc65ea43d67a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251241"
---
# <a name="4205---foundprocessingerror"></a>4205 - FoundProcessingError

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|4205|  
|Mots clés|WFInstanceStore|  
|Level|Error|  
|Channel|Microsoft-Windows-Application Server-Applications/Débogage|  
  
## <a name="description"></a>Description  

 Indique que la commande du fournisseur SQL a échoué.  
  
## <a name="message"></a>Message  

 Échec de la commande : %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|ExceptionMessage|xs:string|Message de l'exception SQL.|  
|Exception|xs:string|Détails de l'exception|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
