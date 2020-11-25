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
ms.openlocfilehash: 02f36068f12bf0a40e5f0ac477803abfb84c72a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729531"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="47157-102">IHostCrst::TryEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="47157-102">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="47157-103">Tente d’entrer dans la section critique représentée par l’instance [IHostCrst](ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="47157-103">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47157-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47157-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47157-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="47157-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="47157-106">dans L’une des valeurs [WAIT_OPTION](wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si l’opération bloque.</span><span class="sxs-lookup"><span data-stu-id="47157-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="47157-107">[out] `true` Si la section critique peut être entrée ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="47157-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47157-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="47157-108">Return Value</span></span>  
  
|<span data-ttu-id="47157-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47157-109">HRESULT</span></span>|<span data-ttu-id="47157-110">Description</span><span class="sxs-lookup"><span data-stu-id="47157-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47157-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="47157-111">S_OK</span></span>|<span data-ttu-id="47157-112">`TryEnter` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="47157-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="47157-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="47157-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="47157-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="47157-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="47157-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="47157-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="47157-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="47157-116">The call timed out.</span></span>|  
|<span data-ttu-id="47157-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="47157-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="47157-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="47157-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="47157-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="47157-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="47157-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="47157-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="47157-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47157-121">E_FAIL</span></span>|<span data-ttu-id="47157-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="47157-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="47157-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="47157-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="47157-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="47157-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47157-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="47157-125">Remarks</span></span>  

 <span data-ttu-id="47157-126">`TryEnter` retourne immédiatement et indique si le thread appelant est entré dans la section critique.</span><span class="sxs-lookup"><span data-stu-id="47157-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="47157-127">Cette méthode reflète la `TryEnterCriticalSection` fonction Wind32.</span><span class="sxs-lookup"><span data-stu-id="47157-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47157-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47157-128">Requirements</span></span>  

 <span data-ttu-id="47157-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47157-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47157-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="47157-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47157-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47157-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47157-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47157-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47157-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47157-133">See also</span></span>

- [<span data-ttu-id="47157-134">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="47157-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="47157-135">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="47157-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="47157-136">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="47157-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
