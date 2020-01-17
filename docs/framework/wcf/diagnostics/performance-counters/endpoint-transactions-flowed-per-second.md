---
title: 'Point de terminaison : transactions passées par seconde'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163551"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="beea4-102">Point de terminaison : transactions passées par seconde</span><span class="sxs-lookup"><span data-stu-id="beea4-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="beea4-103">Nom du compteur : transactions passées par seconde.</span><span class="sxs-lookup"><span data-stu-id="beea4-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="beea4-104">Description</span><span class="sxs-lookup"><span data-stu-id="beea4-104">Description</span></span>  
 <span data-ttu-id="beea4-105">Nombre de transactions transférées vers les opérations au niveau de ce point de terminaison en une seconde.</span><span class="sxs-lookup"><span data-stu-id="beea4-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="beea4-106">Ce compteur est incrémenté à chaque ID de transaction présent dans un message envoyé vers le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="beea4-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="beea4-107">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="beea4-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="beea4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="beea4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
