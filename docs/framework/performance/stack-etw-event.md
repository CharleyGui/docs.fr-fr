---
title: Événement ETW de pile
description: En savoir plus sur l’événement ETW de pile, qui doit être utilisé conjointement avec d’autres événements pour générer des traces de pile après le déclenchement d’un événement.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: 3b890e587abd5cb1b7315fe41897f24638fd4604
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236206"
---
# <a name="stack-etw-event"></a>Événement ETW de pile

L’événement de pile doit être utilisé conjointement avec d’autres événements pour générer des arborescences d’appels de procédure après le déclenchement d’un événement. Il est enregistré quand le fournisseur du runtime est activé. Il s’agit d’un événement très fréquent, car il est déclenché à chaque déclenchement d’un autre événement runtime. Pour cette raison, nous vous recommandons d’utiliser cet événement avec précaution.  
  
 Le tableau suivant montre les mots clés et les niveaux. (Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)  
  
|Mot clé pour déclencher l'événement|Level|  
|-----------------------------------|-----------|  
|`StackKeyword` (0x40000000)|LogAlways(0)|  
  
 Le tableau ci-dessous montre les informations liées aux événements.  
  
|Événement|ID de l’événement|Moment du déclenchement|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|82|Conjointement avec d’autres événements pour générer les arborescences des appels de procédure après un événement.|  
  
 Le tableau ci-dessous montre les données liées aux événements.  
  
|Nom du champ|Type de données|Description|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win:Uint16|Identificateur de runtime unique.|  
|Reserved1|win:UInt8|Réservé.|  
|Reserved2|win:UInt8|Réservé.|  
|FrameCount|win:UInt32|Nombre de frames dans l’arborescence des appels de procédure.|  
|Pile|win:Pointer|Colonnes de pointeurs d’instruction.|  
  
## <a name="see-also"></a>Voir aussi

- [Événements ETW du CLR](clr-etw-events.md)
