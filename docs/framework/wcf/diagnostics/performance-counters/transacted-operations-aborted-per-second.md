---
title: Nombre d'opérations traitées abandonnées par seconde
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: d03f1faf7d2a00d02500fe9759ba940445d8eee3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164019"
---
# <a name="transacted-operations-aborted-per-second"></a>Nombre d'opérations traitées abandonnées par seconde
Nom du compteur : nombre d'opérations traitées abandonnées par seconde.  
  
## <a name="description"></a>Description  
 Nombre d’opérations transactionnelles abandonnées dans ce service par seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
