---
title: 'Point de terminaison : sessions de messagerie fiable ayant renvoyé une erreur par seconde'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 26fd8236af6516716f7cf9c7c06f669473bdfc3a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163187"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Point de terminaison : sessions de messagerie fiable ayant renvoyé une erreur par seconde
Nom du compteur : Sessions de messagerie fiable ayant renvoyé une erreur par seconde.  
  
## <a name="description"></a>Description  
 Nombre de sessions de messagerie fiable ayant renvoyé une erreur au niveau de ce point de terminaison par seconde.  
  
 Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
