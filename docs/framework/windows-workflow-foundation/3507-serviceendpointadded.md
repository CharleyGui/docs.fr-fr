---
title: 3507 - ServiceEndpointAdded
ms.date: 03/30/2017
ms.assetid: c068fc0e-07ee-4551-9824-ea7216e1fe37
ms.openlocfilehash: 903071e7b1f89dc3489b8d3ac05427d699a33a7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240756"
---
# <a name="3507---serviceendpointadded"></a>3507 - ServiceEndpointAdded

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|3507|  
|Mots clés|WFServices|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Indique qu'un point de terminaison du service a été ajouté.  
  
## <a name="message"></a>Message  

 Un point de terminaison du service a été ajouté pour l'adresse « %1 », la liaison « %2 » et le contrat « %3 ».  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|Adresse|xs:string|Adresse du point de terminaison.|  
|Liaison|xs:string|Liaison du point de terminaison.|  
|Contrat|xs:string|Contrat du point de terminaison.|  
|AppDomain|xs:string|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
