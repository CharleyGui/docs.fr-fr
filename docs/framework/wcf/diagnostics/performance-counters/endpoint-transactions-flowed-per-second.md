---
title: 'Point de terminaison : transactions passées par seconde'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163551"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Point de terminaison : transactions passées par seconde
Nom du compteur : transactions passées par seconde.  
  
## <a name="description"></a>Description  
 Nombre de transactions transférées vers les opérations au niveau de ce point de terminaison en une seconde. Ce compteur est incrémenté à chaque ID de transaction présent dans un message envoyé vers le point de terminaison.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
