---
title: Messages déposés par le transport de mise en file d'attente par seconde
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 81ba15965676ba7ffe5ca2aaac5e1d0e94e27962
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266036"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="c6b6a-102">Messages déposés par le transport de mise en file d'attente par seconde</span><span class="sxs-lookup"><span data-stu-id="c6b6a-102">Queue Dropped Messages Per Second</span></span>

<span data-ttu-id="c6b6a-103">Nom du compteur : messages de la file d’attente déposés par seconde.</span><span class="sxs-lookup"><span data-stu-id="c6b6a-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6b6a-104">Description</span><span class="sxs-lookup"><span data-stu-id="c6b6a-104">Description</span></span>  

 <span data-ttu-id="c6b6a-105">Nombre de messages supprimés du transport de mise en file d'attente au niveau de ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="c6b6a-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="c6b6a-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="c6b6a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c6b6a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c6b6a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
