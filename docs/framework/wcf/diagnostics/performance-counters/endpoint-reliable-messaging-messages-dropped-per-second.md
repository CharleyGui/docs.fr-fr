---
title: 'Point de terminaison : messages de messagerie fiable déposés par seconde'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: b8c0f91b2de5d023232756159a50236574308954
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290840"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a>Point de terminaison : messages de messagerie fiable déposés par seconde

Nom du compteur : messages de messagerie fiable déposés par seconde.  
  
## <a name="description"></a>Description  

 Nombre total de messages de messagerie fiable déposés au niveau de ce point de terminaison en une seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
