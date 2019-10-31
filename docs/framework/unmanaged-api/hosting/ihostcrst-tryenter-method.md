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
ms.openlocfilehash: f4b40a595bbdea4dd390a42af6a0d4b1a5efa2f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130493"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="4fdfe-102">IHostCrst::TryEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="4fdfe-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="4fdfe-103">Tente d’entrer dans la section critique représentée par l’instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fdfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fdfe-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fdfe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4fdfe-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="4fdfe-106">dans L’une des valeurs [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si l’opération bloque.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="4fdfe-107">[out] `true` si la section critique peut être entrée ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4fdfe-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4fdfe-108">Return Value</span></span>  
  
|<span data-ttu-id="4fdfe-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4fdfe-109">HRESULT</span></span>|<span data-ttu-id="4fdfe-110">Description</span><span class="sxs-lookup"><span data-stu-id="4fdfe-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4fdfe-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4fdfe-111">S_OK</span></span>|<span data-ttu-id="4fdfe-112">`TryEnter` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="4fdfe-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4fdfe-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4fdfe-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4fdfe-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4fdfe-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4fdfe-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-116">The call timed out.</span></span>|  
|<span data-ttu-id="4fdfe-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4fdfe-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4fdfe-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4fdfe-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4fdfe-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4fdfe-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4fdfe-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4fdfe-121">E_FAIL</span></span>|<span data-ttu-id="4fdfe-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4fdfe-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4fdfe-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fdfe-125">Notes</span><span class="sxs-lookup"><span data-stu-id="4fdfe-125">Remarks</span></span>  
 <span data-ttu-id="4fdfe-126">`TryEnter` est retourné immédiatement et indique si le thread appelant est entré dans la section critique.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="4fdfe-127">Cette méthode reflète la fonction Wind32 `TryEnterCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="4fdfe-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fdfe-128">spécifications</span><span class="sxs-lookup"><span data-stu-id="4fdfe-128">Requirements</span></span>  
 <span data-ttu-id="4fdfe-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fdfe-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fdfe-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4fdfe-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fdfe-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4fdfe-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fdfe-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fdfe-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fdfe-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fdfe-133">See also</span></span>

- [<span data-ttu-id="4fdfe-134">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="4fdfe-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="4fdfe-135">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="4fdfe-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="4fdfe-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="4fdfe-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
