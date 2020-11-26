---
title: 452 - MessageLogWarning
ms.date: 03/30/2017
ms.assetid: 22a9f6ea-5b5f-4110-8a4e-9be9c983fbbb
ms.openlocfilehash: 484909bcdac27c1b04be967df1182a67294f4920
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242654"
---
# <a name="452---messagelogwarning"></a>452 - MessageLogWarning

## <a name="properties"></a>Propriétés  
  
|||  
|-|-|  
|id|452|  
|Mots clés|Dépannage, WCFMessageLogging|  
|Level|Avertissement|  
|Channel|Microsoft-Windows-Application Server-Applications/Analyse|  
  
## <a name="description"></a>Description  

 Cet événement est émis lorsque l'avertissement du journal des messages est envoyé.  
  
## <a name="message"></a>Message  

 %1  
  
## <a name="details"></a>Détails  
  
|Nom d'élément de données|Type d'élément de données|Description|  
|--------------------|--------------------|-----------------|  
|data1|`xs:string`||  
|AppDomain|`xs:string`|Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.|
