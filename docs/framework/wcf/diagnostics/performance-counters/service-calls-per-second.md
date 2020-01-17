---
title: 'Service : appels par seconde'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: be5d77169a71d6f44205a1150da5239eceff7d9c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163902"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="fcddc-102">Service : appels par seconde</span><span class="sxs-lookup"><span data-stu-id="fcddc-102">Service: Calls Per Second</span></span>
<span data-ttu-id="fcddc-103">Nom du compteur : Appels par seconde.</span><span class="sxs-lookup"><span data-stu-id="fcddc-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fcddc-104">Description</span><span class="sxs-lookup"><span data-stu-id="fcddc-104">Description</span></span>  
 <span data-ttu-id="fcddc-105">Nombre d'appels à ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="fcddc-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="fcddc-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="fcddc-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fcddc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) où le numérateur (N) représente le nombre d'opérations exécutées au cours du dernier intervalle échantillon, le dénominateur (D) représente le nombre de graduations écoulées au cours du dernier intervalle échantillon, et F représente la fréquence des graduations.</span><span class="sxs-lookup"><span data-stu-id="fcddc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
