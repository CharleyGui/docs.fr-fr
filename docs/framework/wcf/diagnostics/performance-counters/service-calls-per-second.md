---
title: 'Service : appels par seconde'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5066108d8183502eeaec7c25186c00d9978261b7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546931"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="d8f20-102">Service : appels par seconde</span><span class="sxs-lookup"><span data-stu-id="d8f20-102">Service: Calls Per Second</span></span>
<span data-ttu-id="d8f20-103">Nom du compteur : Appels par seconde.</span><span class="sxs-lookup"><span data-stu-id="d8f20-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8f20-104">Description</span><span class="sxs-lookup"><span data-stu-id="d8f20-104">Description</span></span>  
 <span data-ttu-id="d8f20-105">Nombre d'appels à ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="d8f20-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="d8f20-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="d8f20-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d8f20-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) où le numérateur (N) représente le nombre d'opérations exécutées au cours du dernier intervalle échantillon, le dénominateur (D) représente le nombre de graduations écoulées au cours du dernier intervalle échantillon, et F représente la fréquence des graduations.</span><span class="sxs-lookup"><span data-stu-id="d8f20-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
