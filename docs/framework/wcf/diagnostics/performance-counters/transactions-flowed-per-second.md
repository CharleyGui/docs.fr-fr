---
title: Transactions passées par seconde
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: d55856a5d820df2c668863a2a3e853995a113143
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552204"
---
# <a name="transactions-flowed-per-second"></a>Transactions passées par seconde
Nom du compteur : transactions passées par seconde  
  
## <a name="description"></a>Description  
 Nombre de transactions transmises à cette opération en une seconde. Ce compteur est incrémenté à chaque fois qu'un ID de transaction est présent dans un message envoyé à l'opération.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
