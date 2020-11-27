---
title: 'Point de terminaison : transactions passées par seconde'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: b814d7ca9e286426289c611b3a6bf5a52c1b2335
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256428"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="004bb-102">Point de terminaison : transactions passées par seconde</span><span class="sxs-lookup"><span data-stu-id="004bb-102">Endpoint: Transactions Flowed Per Second</span></span>

<span data-ttu-id="004bb-103">Nom du compteur : transactions passées par seconde.</span><span class="sxs-lookup"><span data-stu-id="004bb-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="004bb-104">Description</span><span class="sxs-lookup"><span data-stu-id="004bb-104">Description</span></span>  

 <span data-ttu-id="004bb-105">Nombre de transactions transférées vers les opérations au niveau de ce point de terminaison en une seconde.</span><span class="sxs-lookup"><span data-stu-id="004bb-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="004bb-106">Ce compteur est incrémenté à chaque ID de transaction présent dans un message envoyé vers le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="004bb-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="004bb-107">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="004bb-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="004bb-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="004bb-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
