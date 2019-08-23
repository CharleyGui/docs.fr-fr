---
title: IHostCrst::Enter, méthode
ms.date: 03/30/2017
api_name:
- IHostCrst.Enter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Enter
helpviewer_keywords:
- Enter method [.NET Framework hosting]
- IHostCrst::Enter method [.NET Framework hosting]
ms.assetid: 100dd7eb-7053-4295-9bb3-32ba47f6ec79
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdc597e741023af1c7cc1f48e378083157dd4a5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937738"
---
# <a name="ihostcrstenter-method"></a><span data-ttu-id="01b9a-102">IHostCrst::Enter, méthode</span><span class="sxs-lookup"><span data-stu-id="01b9a-102">IHostCrst::Enter Method</span></span>
<span data-ttu-id="01b9a-103">Entre dans la section critique qui est représentée par l’instance [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) actuelle.</span><span class="sxs-lookup"><span data-stu-id="01b9a-103">Enters the critical section that is represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01b9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01b9a-104">Syntax</span></span>  
  
```cpp  
HRESULT Enter (  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01b9a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01b9a-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="01b9a-106">dans L’une des valeurs [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) , indiquant l’action que l’hôte doit effectuer si l’opération bloque.</span><span class="sxs-lookup"><span data-stu-id="01b9a-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01b9a-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="01b9a-107">Return Value</span></span>  
  
|<span data-ttu-id="01b9a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01b9a-108">HRESULT</span></span>|<span data-ttu-id="01b9a-109">Description</span><span class="sxs-lookup"><span data-stu-id="01b9a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01b9a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="01b9a-110">S_OK</span></span>|<span data-ttu-id="01b9a-111">`Enter`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="01b9a-111">`Enter` returned successfully.</span></span>|  
|<span data-ttu-id="01b9a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01b9a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01b9a-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="01b9a-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01b9a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01b9a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01b9a-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="01b9a-115">The call timed out.</span></span>|  
|<span data-ttu-id="01b9a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01b9a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01b9a-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="01b9a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01b9a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01b9a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01b9a-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="01b9a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01b9a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01b9a-120">E_FAIL</span></span>|<span data-ttu-id="01b9a-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="01b9a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01b9a-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="01b9a-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01b9a-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01b9a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01b9a-124">Notes</span><span class="sxs-lookup"><span data-stu-id="01b9a-124">Remarks</span></span>  
 <span data-ttu-id="01b9a-125">`Enter`reflète la fonction `EnterCriticalSection` Win32.</span><span class="sxs-lookup"><span data-stu-id="01b9a-125">`Enter` mirrors the Win32 `EnterCriticalSection` function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01b9a-126">Cette méthode n’est pas retournée tant que la section critique n’est pas entrée.</span><span class="sxs-lookup"><span data-stu-id="01b9a-126">This method does not return until the critical section is entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01b9a-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01b9a-127">Requirements</span></span>  
 <span data-ttu-id="01b9a-128">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01b9a-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01b9a-129">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01b9a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01b9a-130">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01b9a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01b9a-131">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01b9a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b9a-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01b9a-132">See also</span></span>

- [<span data-ttu-id="01b9a-133">ICLRSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="01b9a-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="01b9a-134">IHostCrst, interface</span><span class="sxs-lookup"><span data-stu-id="01b9a-134">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="01b9a-135">IHostSyncManager, interface</span><span class="sxs-lookup"><span data-stu-id="01b9a-135">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
