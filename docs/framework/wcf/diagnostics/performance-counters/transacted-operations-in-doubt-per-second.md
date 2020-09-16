---
title: Opérations traitées avec des résultats incertains par seconde
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 59186b1fc113bb87264a8b946cfee2719ff50b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550597"
---
# <a name="transacted-operations-in-doubt-per-second"></a>Opérations traitées avec des résultats incertains par seconde
Nom du compteur : Opérations traitées avec des résultats incertains par seconde.  
  
## <a name="description"></a>Description  
 Nombre d'opérations transactionnelles avec un résultat incertain dans ce service en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
