---
title: Appels de sécurité non autorisés par seconde
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 8aed9f6b8c60c8aecd1b576c13a7063e3a492046
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552503"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="c7d43-102">Appels de sécurité non autorisés par seconde</span><span class="sxs-lookup"><span data-stu-id="c7d43-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="c7d43-103">Nom du compteur : Appels de sécurité non autorisés par seconde.</span><span class="sxs-lookup"><span data-stu-id="c7d43-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c7d43-104">Description</span><span class="sxs-lookup"><span data-stu-id="c7d43-104">Description</span></span>  
 <span data-ttu-id="c7d43-105">Nombre d'appels dont l'autorisation a échoué lors de cette opération en une seconde.</span><span class="sxs-lookup"><span data-stu-id="c7d43-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="c7d43-106">Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="c7d43-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="c7d43-107">Il indique que le message entrant provient d’un utilisateur valide et qu’il est correctement protégé, mais que l’utilisateur n’est pas autorisé à exécuter des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c7d43-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="c7d43-108">Ce compteur est de type de compteur de performance [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="c7d43-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c7d43-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c7d43-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
