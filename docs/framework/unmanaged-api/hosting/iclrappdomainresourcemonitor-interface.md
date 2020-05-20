---
title: ICLRAppDomainResourceMonitor, interface
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 08dc0f0891d960cb7b402b30455e606aaff7bcea
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616006"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="813aa-102">ICLRAppDomainResourceMonitor, interface</span><span class="sxs-lookup"><span data-stu-id="813aa-102">ICLRAppDomainResourceMonitor Interface</span></span>
<span data-ttu-id="813aa-103">Fournit des méthodes qui inspectent la mémoire et l’utilisation de l’UC d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="813aa-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="813aa-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="813aa-104">Methods</span></span>  
  
|<span data-ttu-id="813aa-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="813aa-105">Method</span></span>|<span data-ttu-id="813aa-106">Description</span><span class="sxs-lookup"><span data-stu-id="813aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="813aa-107">GetCurrentAllocated, méthode</span><span class="sxs-lookup"><span data-stu-id="813aa-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="813aa-108">Obtient la taille totale, en octets, de toutes les allocations de mémoire effectuées par le domaine d’application depuis sa création, sans soustraire la mémoire qui a été récupérée par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="813aa-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="813aa-109">GetCurrentSurvived, méthode</span><span class="sxs-lookup"><span data-stu-id="813aa-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="813aa-110">Obtient le nombre d’octets qui ont survécu au dernier garbage collection de blocage complet et qui sont référencés par le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="813aa-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="813aa-111">GetCurrentCpuTime, méthode</span><span class="sxs-lookup"><span data-stu-id="813aa-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="813aa-112">Obtient le temps processeur total utilisé par tous les threads lors de l’exécution dans le domaine d’application actuel, depuis la création du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="813aa-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="813aa-113">Notes</span><span class="sxs-lookup"><span data-stu-id="813aa-113">Remarks</span></span>  
 <span data-ttu-id="813aa-114">L' `ICLRAppDomainResourceMonitor` interface fournit des fonctionnalités qui sont similaires aux propriétés managées suivantes :</span><span class="sxs-lookup"><span data-stu-id="813aa-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="813aa-115">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="813aa-115">Requirements</span></span>  
 <span data-ttu-id="813aa-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="813aa-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="813aa-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="813aa-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="813aa-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="813aa-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="813aa-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="813aa-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="813aa-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="813aa-120">See also</span></span>

- [<span data-ttu-id="813aa-121">\<appDomainResourceMonitoring>, élément</span><span class="sxs-lookup"><span data-stu-id="813aa-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="813aa-122">Analyse des ressources du domaine d’application</span><span class="sxs-lookup"><span data-stu-id="813aa-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="813aa-123">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="813aa-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="813aa-124">Hébergement</span><span class="sxs-lookup"><span data-stu-id="813aa-124">Hosting</span></span>](index.md)
