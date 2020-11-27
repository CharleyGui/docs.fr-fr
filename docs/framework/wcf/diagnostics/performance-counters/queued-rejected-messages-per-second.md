---
title: Messages rejetés par le transport de mise en file d'attente par seconde
ms.date: 03/30/2017
ms.assetid: 77ea9aa3-b9e2-4a1d-a65e-5ca115ba0567
ms.openlocfilehash: 2b7686ee94ab051bc255bdb71681c8d1c473094c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276202"
---
# <a name="queued-rejected-messages-per-second"></a><span data-ttu-id="4c21e-102">Messages rejetés par le transport de mise en file d'attente par seconde</span><span class="sxs-lookup"><span data-stu-id="4c21e-102">Queued Rejected Messages Per Second</span></span>

<span data-ttu-id="4c21e-103">Nom du compteur : Messages rejetés par le transport de mise en file d'attente par seconde.</span><span class="sxs-lookup"><span data-stu-id="4c21e-103">Counter Name: Queued Messages Rejected Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4c21e-104">Description</span><span class="sxs-lookup"><span data-stu-id="4c21e-104">Description</span></span>  

 <span data-ttu-id="4c21e-105">Nombre de messages vers ce service qui ont été rejetés par le transport de mise en file d'attente en une seconde.</span><span class="sxs-lookup"><span data-stu-id="4c21e-105">Number of messages that are rejected by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="4c21e-106">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="4c21e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4c21e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="4c21e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
