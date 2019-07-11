---
title: IHostCrst::TryEnter, méthode
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0b4074d9dab8ad46468930373ad44b0c72bd690
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763740"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="5a6df-102">IHostCrst::TryEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="5a6df-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="5a6df-103">Tente d’entrer la section critique représentée par le [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="5a6df-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a6df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a6df-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a6df-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5a6df-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="5a6df-106">[in] Parmi les [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) valeurs indiquant quelle action l’hôte doit effectuer si l’opération se bloque.</span><span class="sxs-lookup"><span data-stu-id="5a6df-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="5a6df-107">[out] `true` si la section critique peut être entrées ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="5a6df-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a6df-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5a6df-108">Return Value</span></span>  
  
|<span data-ttu-id="5a6df-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5a6df-109">HRESULT</span></span>|<span data-ttu-id="5a6df-110">Description</span><span class="sxs-lookup"><span data-stu-id="5a6df-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a6df-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5a6df-111">S_OK</span></span>|<span data-ttu-id="5a6df-112">`TryEnter` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="5a6df-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="5a6df-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5a6df-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5a6df-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="5a6df-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5a6df-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5a6df-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5a6df-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="5a6df-116">The call timed out.</span></span>|  
|<span data-ttu-id="5a6df-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5a6df-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5a6df-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="5a6df-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5a6df-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5a6df-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5a6df-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="5a6df-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5a6df-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5a6df-121">E_FAIL</span></span>|<span data-ttu-id="5a6df-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5a6df-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5a6df-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="5a6df-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5a6df-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="5a6df-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a6df-125">Notes</span><span class="sxs-lookup"><span data-stu-id="5a6df-125">Remarks</span></span>  
 <span data-ttu-id="5a6df-126">`TryEnter` retourne immédiatement et indique si le thread appelant est entré à la section critique.</span><span class="sxs-lookup"><span data-stu-id="5a6df-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="5a6df-127">Cette méthode reflète le Wind32 `TryEnterCriticalSection` (fonction).</span><span class="sxs-lookup"><span data-stu-id="5a6df-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a6df-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5a6df-128">Requirements</span></span>  
 <span data-ttu-id="5a6df-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a6df-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a6df-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5a6df-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5a6df-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5a6df-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5a6df-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a6df-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a6df-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a6df-133">See also</span></span>

- [<span data-ttu-id="5a6df-134">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="5a6df-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5a6df-135">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="5a6df-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="5a6df-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="5a6df-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
