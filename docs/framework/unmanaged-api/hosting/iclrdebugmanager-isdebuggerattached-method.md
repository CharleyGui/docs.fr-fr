---
title: ICLRDebugManager::IsDebuggerAttached, méthode
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 71e11d7db3bd679e7972fb2f6ce098edc3399885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731018"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="3d728-102">ICLRDebugManager::IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="3d728-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="3d728-103">Obtient une valeur qui indique si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="3d728-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d728-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d728-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d728-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d728-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="3d728-106">[out] `true` Si un débogueur est attaché au processus ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="3d728-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d728-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3d728-107">Return Value</span></span>  
  
|<span data-ttu-id="3d728-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d728-108">HRESULT</span></span>|<span data-ttu-id="3d728-109">Description</span><span class="sxs-lookup"><span data-stu-id="3d728-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d728-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d728-110">S_OK</span></span>|<span data-ttu-id="3d728-111">`IsDebuggerAttached` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3d728-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="3d728-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d728-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d728-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="3d728-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d728-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d728-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d728-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3d728-115">The call timed out.</span></span>|  
|<span data-ttu-id="3d728-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d728-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d728-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3d728-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d728-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d728-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d728-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="3d728-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3d728-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d728-120">E_FAIL</span></span>|<span data-ttu-id="3d728-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3d728-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d728-122">Une fois que la méthode a retourné E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3d728-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d728-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3d728-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d728-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d728-124">Remarks</span></span>  

 <span data-ttu-id="3d728-125">`IsDebuggerAttached` permet à l’hôte d’interroger le CLR pour déterminer si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="3d728-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d728-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d728-126">Requirements</span></span>  

 <span data-ttu-id="3d728-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d728-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d728-128">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3d728-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d728-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d728-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d728-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d728-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d728-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d728-131">See also</span></span>

- [<span data-ttu-id="3d728-132">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="3d728-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="3d728-133">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="3d728-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="3d728-134">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="3d728-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
