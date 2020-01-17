---
title: Opérations traitées validées par seconde
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: b81146516413c4afa9baf9a533797f0867a1b20d
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163850"
---
# <a name="transacted-operations-committed-per-second"></a>Opérations traitées validées par seconde
Nom du compteur : opérations transactionnelles validées par seconde  
  
## <a name="description"></a>Description  
 Nombre d’opérations transactionnelles qui ont été validées sur un service en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
