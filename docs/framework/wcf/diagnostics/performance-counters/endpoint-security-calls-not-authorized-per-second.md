---
title: 'Point de terminaison : appels de sécurité non autorisés par seconde'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 8c287ef4c156bb0a76a4b1d08b0d70b40bd76229
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163174"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="680d4-102">Point de terminaison : appels de sécurité non autorisés par seconde</span><span class="sxs-lookup"><span data-stu-id="680d4-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="680d4-103">Nom du compteur : Appels de sécurité non autorisés par seconde.</span><span class="sxs-lookup"><span data-stu-id="680d4-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="680d4-104">Description</span><span class="sxs-lookup"><span data-stu-id="680d4-104">Description</span></span>  
 <span data-ttu-id="680d4-105">Nombre de messages entrants en une seconde qui proviennent d’un utilisateur valide et sont protégés correctement, mais pour lesquels l’utilisateur n’est pas autorisé à effectuer des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="680d4-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="680d4-106">Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="680d4-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="680d4-107">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="680d4-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="680d4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="680d4-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
