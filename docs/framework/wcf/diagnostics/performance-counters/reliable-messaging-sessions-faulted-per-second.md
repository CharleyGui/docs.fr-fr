---
title: Sessions de messagerie fiable ayant renvoyé une erreur par seconde
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: 427ce2be4bd9fae6fd39922d79ee7427179dfd18
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276150"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="840aa-102">Sessions de messagerie fiable ayant renvoyé une erreur par seconde</span><span class="sxs-lookup"><span data-stu-id="840aa-102">Reliable Messaging Sessions Faulted Per Second</span></span>

<span data-ttu-id="840aa-103">Nom du compteur : Sessions de messagerie fiable ayant renvoyé une erreur par seconde.</span><span class="sxs-lookup"><span data-stu-id="840aa-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="840aa-104">Description</span><span class="sxs-lookup"><span data-stu-id="840aa-104">Description</span></span>  

 <span data-ttu-id="840aa-105">Nombre de sessions de messagerie fiable ayant renvoyé une erreur dans ce service en une seconde.</span><span class="sxs-lookup"><span data-stu-id="840aa-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="840aa-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="840aa-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="840aa-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="840aa-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
