---
title: 'Service : transactions passées par seconde'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: e8fbc314321a46fd3539998bd3dd22770086ca37
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164006"
---
# <a name="service-transactions-flowed-per-second"></a>Service : transactions passées par seconde
Nom du compteur : transactions passées par seconde.  
  
## <a name="description"></a>Description  
 Nombre de transactions passées aux opérations dans ce service en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
