---
title: Messages déposés par le transport de mise en file d'attente par seconde
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 6ec762d7e5dd7daf63b5df76e1ffb48957538538
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164032"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="e8f75-102">Messages déposés par le transport de mise en file d'attente par seconde</span><span class="sxs-lookup"><span data-stu-id="e8f75-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="e8f75-103">Nom du compteur : messages de la file d’attente déposés par seconde.</span><span class="sxs-lookup"><span data-stu-id="e8f75-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e8f75-104">Description</span><span class="sxs-lookup"><span data-stu-id="e8f75-104">Description</span></span>  
 <span data-ttu-id="e8f75-105">Nombre de messages supprimés du transport de mise en file d'attente au niveau de ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="e8f75-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="e8f75-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="e8f75-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e8f75-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e8f75-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
