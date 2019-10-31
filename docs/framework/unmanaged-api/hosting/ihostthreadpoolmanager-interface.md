---
title: IHostThreadPoolManager, interface
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122084"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="fea31-102">IHostThreadPoolManager, interface</span><span class="sxs-lookup"><span data-stu-id="fea31-102">IHostThreadPoolManager Interface</span></span>
<span data-ttu-id="fea31-103">Fournit des méthodes qui permettent au common language runtime (CLR) de configurer le pool de threads et de mettre en file d’attente des éléments de travail dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="fea31-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fea31-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="fea31-104">Methods</span></span>  
  
|<span data-ttu-id="fea31-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-105">Method</span></span>|<span data-ttu-id="fea31-106">Description</span><span class="sxs-lookup"><span data-stu-id="fea31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fea31-107">GetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-107">GetAvailableThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="fea31-108">Obtient le nombre de threads dans le pool de threads qui ne traitent pas actuellement des éléments de travail.</span><span class="sxs-lookup"><span data-stu-id="fea31-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="fea31-109">GetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-109">GetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="fea31-110">Obtient le nombre maximal de threads que l’hôte conserve simultanément dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="fea31-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="fea31-111">GetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-111">GetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="fea31-112">Obtient le nombre minimal de threads inactifs que l’hôte gère en prévision des demandes.</span><span class="sxs-lookup"><span data-stu-id="fea31-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="fea31-113">QueueUserWorkItem, méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-113">QueueUserWorkItem Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="fea31-114">Met en file d’attente une fonction pour l’exécution et fournit un objet contenant les données que la fonction doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="fea31-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="fea31-115">SetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-115">SetMaxThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="fea31-116">Définit le nombre maximal de threads que l’hôte peut conserver dans le pool de threads.</span><span class="sxs-lookup"><span data-stu-id="fea31-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="fea31-117">SetMinThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="fea31-117">SetMinThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="fea31-118">Définit le nombre minimal de threads inactifs que l’hôte doit gérer en prévision des demandes.</span><span class="sxs-lookup"><span data-stu-id="fea31-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea31-119">Notes</span><span class="sxs-lookup"><span data-stu-id="fea31-119">Remarks</span></span>  
 <span data-ttu-id="fea31-120">L’hôte n’est pas tenu de configurer le pool de threads à l’aide des valeurs spécifiées dans les appels aux méthodes `SetMaxThreads` et `SetMinThreads`.</span><span class="sxs-lookup"><span data-stu-id="fea31-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="fea31-121">Dans ce cas, l’hôte doit retourner une valeur HRESULT d’E_NOTIMPL à partir de ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="fea31-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fea31-122">spécifications</span><span class="sxs-lookup"><span data-stu-id="fea31-122">Requirements</span></span>  
 <span data-ttu-id="fea31-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fea31-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fea31-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fea31-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fea31-125">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fea31-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fea31-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fea31-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea31-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fea31-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="fea31-128">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="fea31-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
