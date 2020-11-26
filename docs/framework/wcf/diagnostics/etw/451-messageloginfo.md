---
title: 451 - MessageLogInfo
ms.date: 03/30/2017
ms.assetid: 485b4b29-dc21-4a35-93f8-5f4726d6aa5a
ms.openlocfilehash: 2b5dd36099e1d9978cb1136462c224a79465f823
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242784"
---
# <a name="451---messageloginfo"></a>451 - MessageLogInfo

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|451|  
|Mots clés|Dépannage, WCFMessageLogging|  
|Level|Informations|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis lorsque les informations du journal des messages sont envoyées.  
  
## <a name="message"></a>Message  

 %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|data1|`xs:string`||  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
