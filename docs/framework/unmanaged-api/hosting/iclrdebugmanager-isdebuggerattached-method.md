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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30159748c1103cbc8efaf8929387052bbe5c3ec7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773124"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="a960b-102">ICLRDebugManager::IsDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="a960b-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="a960b-103">Obtient une valeur qui indique si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="a960b-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a960b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a960b-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a960b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a960b-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="a960b-106">[out] `true` si un débogueur est attaché au processus ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="a960b-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a960b-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a960b-107">Return Value</span></span>  
  
|<span data-ttu-id="a960b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a960b-108">HRESULT</span></span>|<span data-ttu-id="a960b-109">Description</span><span class="sxs-lookup"><span data-stu-id="a960b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a960b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a960b-110">S_OK</span></span>|<span data-ttu-id="a960b-111">`IsDebuggerAttached` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a960b-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="a960b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a960b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a960b-113">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="a960b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a960b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a960b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a960b-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a960b-115">The call timed out.</span></span>|  
|<span data-ttu-id="a960b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a960b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a960b-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a960b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a960b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a960b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a960b-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="a960b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a960b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a960b-120">E_FAIL</span></span>|<span data-ttu-id="a960b-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a960b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a960b-122">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="a960b-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a960b-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a960b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a960b-124">Notes</span><span class="sxs-lookup"><span data-stu-id="a960b-124">Remarks</span></span>  
 <span data-ttu-id="a960b-125">`IsDebuggerAttached` permet à l’hôte interroger le CLR pour déterminer si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="a960b-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a960b-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a960b-126">Requirements</span></span>  
 <span data-ttu-id="a960b-127">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a960b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a960b-128">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a960b-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a960b-129">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a960b-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a960b-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a960b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a960b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a960b-131">See also</span></span>

- [<span data-ttu-id="a960b-132">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="a960b-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a960b-133">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="a960b-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="a960b-134">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="a960b-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
