---
title: 'Service : appels de sécurité non autorisés par seconde'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 59e044f7c5946b32d959119939f972e081a8f57b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540489"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="fd98b-102">Service : appels de sécurité non autorisés par seconde</span><span class="sxs-lookup"><span data-stu-id="fd98b-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="fd98b-103">Nom du compteur : appels de sécurité non autorisés par seconde.</span><span class="sxs-lookup"><span data-stu-id="fd98b-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd98b-104">Description</span><span class="sxs-lookup"><span data-stu-id="fd98b-104">Description</span></span>  
 <span data-ttu-id="fd98b-105">Nombre de messages entrants par seconde qui proviennent d'un utilisateur valide et sont correctement protégés, mais pour lesquels l'utilisateur n'est pas autorisé à effectuer des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="fd98b-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="fd98b-106">Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="fd98b-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="fd98b-107">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="fd98b-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fd98b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="fd98b-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
