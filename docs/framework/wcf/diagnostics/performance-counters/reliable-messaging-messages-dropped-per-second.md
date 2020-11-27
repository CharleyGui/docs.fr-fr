---
title: Messages de messagerie fiable déposés par seconde
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 1e6db155f21fb2443394bc3a65235d4e9539dab3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276176"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Messages de messagerie fiable déposés par seconde

Nom du compteur : messages de messagerie fiable déposés par seconde.  
  
## <a name="description"></a>Description  

 Nombre total de messages de messagerie fiable déposés dans ce service en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
