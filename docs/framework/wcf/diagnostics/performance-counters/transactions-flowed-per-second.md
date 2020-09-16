---
title: Transactions passées par seconde
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: d55856a5d820df2c668863a2a3e853995a113143
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552204"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="2eac8-102">Transactions passées par seconde</span><span class="sxs-lookup"><span data-stu-id="2eac8-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="2eac8-103">Nom du compteur : transactions passées par seconde</span><span class="sxs-lookup"><span data-stu-id="2eac8-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="2eac8-104">Description</span><span class="sxs-lookup"><span data-stu-id="2eac8-104">Description</span></span>  
 <span data-ttu-id="2eac8-105">Nombre de transactions transmises à cette opération en une seconde.</span><span class="sxs-lookup"><span data-stu-id="2eac8-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="2eac8-106">Ce compteur est incrémenté à chaque fois qu'un ID de transaction est présent dans un message envoyé à l'opération.</span><span class="sxs-lookup"><span data-stu-id="2eac8-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="2eac8-107">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="2eac8-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2eac8-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="2eac8-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
