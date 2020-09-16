---
title: Messages incohérents en file d'attente par seconde
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 39118b515949e6ad4f6ff651037cd757a6dd9bbf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552646"
---
# <a name="queued-poison-messages-per-second"></a>Messages incohérents en file d'attente par seconde
Nom du compteur : Messages incohérents en file d'attente par seconde.  
  
## <a name="description"></a>Description  
 Nombre de messages vers ce service marqués comme incohérents par le transport de mise en file d'attente par seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
