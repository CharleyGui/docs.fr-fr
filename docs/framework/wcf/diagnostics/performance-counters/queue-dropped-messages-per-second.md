---
title: Messages déposés par le transport de mise en file d'attente par seconde
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 81ba15965676ba7ffe5ca2aaac5e1d0e94e27962
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266036"
---
# <a name="queue-dropped-messages-per-second"></a>Messages déposés par le transport de mise en file d'attente par seconde

Nom du compteur : messages de la file d’attente déposés par seconde.  
  
## <a name="description"></a>Description  

 Nombre de messages supprimés du transport de mise en file d'attente au niveau de ce service en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
