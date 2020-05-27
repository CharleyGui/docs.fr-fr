---
title: IHostTaskManager::EndDelayAbort, méthode
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: 156626ce907c13987c0cca15016263291961037d
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841969"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="49155-102">IHostTaskManager::EndDelayAbort, méthode</span><span class="sxs-lookup"><span data-stu-id="49155-102">IHostTaskManager::EndDelayAbort Method</span></span>
<span data-ttu-id="49155-103">Indique à l’hôte que le code managé quitte la période pendant laquelle la tâche en cours ne doit pas être abandonnée, à la suite d’un appel antérieur à [IHostTaskManager :: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span><span class="sxs-lookup"><span data-stu-id="49155-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49155-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49155-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="49155-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="49155-105">Return Value</span></span>  
  
|<span data-ttu-id="49155-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49155-106">HRESULT</span></span>|<span data-ttu-id="49155-107">Description</span><span class="sxs-lookup"><span data-stu-id="49155-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49155-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="49155-108">S_OK</span></span>|<span data-ttu-id="49155-109">`EndDelayAbort`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="49155-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="49155-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="49155-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="49155-111">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="49155-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="49155-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="49155-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="49155-113">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="49155-113">The call timed out.</span></span>|  
|<span data-ttu-id="49155-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="49155-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="49155-115">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="49155-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="49155-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="49155-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="49155-117">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="49155-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="49155-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49155-118">E_FAIL</span></span>|<span data-ttu-id="49155-119">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="49155-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49155-120">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="49155-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="49155-121">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="49155-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="49155-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="49155-122">E_UNEXPECTED</span></span>|<span data-ttu-id="49155-123">`EndDelayAbort`a été appelé sans appel correspondant à `BeginDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="49155-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49155-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="49155-124">Remarks</span></span>  
 <span data-ttu-id="49155-125">Le CLR effectue un appel correspondant à `BeginDelayAbort` sur la tâche actuelle avant d’appeler `EndDelayAbort` .</span><span class="sxs-lookup"><span data-stu-id="49155-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="49155-126">En l’absence d’un tel appel, l’implémentation de [IHostTaskManager](ihosttaskmanager-interface.md) par l’hôte doit retourner E_UNEXPECTED à partir de `EndDelayAbort` et ne doit effectuer aucune action.</span><span class="sxs-lookup"><span data-stu-id="49155-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49155-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="49155-127">Requirements</span></span>  
 <span data-ttu-id="49155-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49155-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49155-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="49155-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49155-130">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="49155-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49155-131">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49155-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49155-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49155-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="49155-133">ICLRTask, interface</span><span class="sxs-lookup"><span data-stu-id="49155-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="49155-134">ICLRTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="49155-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="49155-135">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="49155-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="49155-136">IHostTaskManager, interface</span><span class="sxs-lookup"><span data-stu-id="49155-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
