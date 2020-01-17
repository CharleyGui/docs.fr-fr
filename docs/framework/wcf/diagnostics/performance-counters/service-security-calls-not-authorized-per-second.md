---
title: 'Service : appels de sécurité non autorisés par seconde'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 964eff97a58ab7d5a68dbc1891473ae8d04a50ad
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163876"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="7d4c6-102">Service : appels de sécurité non autorisés par seconde</span><span class="sxs-lookup"><span data-stu-id="7d4c6-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="7d4c6-103">Nom du compteur : appels de sécurité non autorisés par seconde.</span><span class="sxs-lookup"><span data-stu-id="7d4c6-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="7d4c6-104">Description</span><span class="sxs-lookup"><span data-stu-id="7d4c6-104">Description</span></span>  
 <span data-ttu-id="7d4c6-105">Nombre de messages entrants par seconde qui proviennent d'un utilisateur valide et sont correctement protégés, mais pour lesquels l'utilisateur n'est pas autorisé à effectuer des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7d4c6-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="7d4c6-106">Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="7d4c6-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="7d4c6-107">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="7d4c6-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7d4c6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="7d4c6-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
