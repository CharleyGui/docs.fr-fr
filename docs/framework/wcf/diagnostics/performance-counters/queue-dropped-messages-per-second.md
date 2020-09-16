---
title: Messages déposés par le transport de mise en file d'attente par seconde
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 22b6091693b6a4c8eac9816e8ac15660f4636ec9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552750"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="2ee6d-102">Messages déposés par le transport de mise en file d'attente par seconde</span><span class="sxs-lookup"><span data-stu-id="2ee6d-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="2ee6d-103">Nom du compteur : messages de la file d’attente déposés par seconde.</span><span class="sxs-lookup"><span data-stu-id="2ee6d-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2ee6d-104">Description</span><span class="sxs-lookup"><span data-stu-id="2ee6d-104">Description</span></span>  
 <span data-ttu-id="2ee6d-105">Nombre de messages supprimés du transport de mise en file d'attente au niveau de ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="2ee6d-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="2ee6d-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="2ee6d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2ee6d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2ee6d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
