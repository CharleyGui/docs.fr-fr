---
title: Opérations traitées avec des résultats incertains par seconde
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: 9162809ec467f282674e0ab21f7ce5e4d2222da4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249980"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="7dd43-102">Opérations traitées avec des résultats incertains par seconde</span><span class="sxs-lookup"><span data-stu-id="7dd43-102">Transacted Operations In Doubt Per Second</span></span>

<span data-ttu-id="7dd43-103">Nom du compteur : Opérations traitées avec des résultats incertains par seconde.</span><span class="sxs-lookup"><span data-stu-id="7dd43-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7dd43-104">Description</span><span class="sxs-lookup"><span data-stu-id="7dd43-104">Description</span></span>  

 <span data-ttu-id="7dd43-105">Nombre d'opérations transactionnelles avec un résultat incertain dans ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="7dd43-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="7dd43-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="7dd43-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7dd43-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="7dd43-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
