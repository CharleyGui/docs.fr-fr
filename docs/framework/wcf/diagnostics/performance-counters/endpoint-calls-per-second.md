---
title: 'Point de terminaison : appels par seconde'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: 7a3a9bcdb3485efa01ceed61495dd87d64424d50
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550317"
---
# <a name="endpoint-calls-per-second"></a>Point de terminaison : appels par seconde
Nom du compteur : Appels par seconde.  
  
## <a name="description"></a>Description  
 Nombre d'appels à ce point de terminaison en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
