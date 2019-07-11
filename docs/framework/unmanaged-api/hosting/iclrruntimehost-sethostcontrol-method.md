---
title: ICLRRuntimeHost::SetHostControl, méthode
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cf6255bfd23b38be63cd609798643f9fa1e1f93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765770"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="77cf0-102">ICLRRuntimeHost::SetHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="77cf0-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="77cf0-103">Définit le pointeur d’interface que le common language runtime (CLR) peut utiliser pour obtenir l’implémentation de l’hôte de [IHostControl, Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="77cf0-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77cf0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77cf0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77cf0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77cf0-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="77cf0-106">[in] Pointeur d’interface vers l’implémentation de l’hôte de [IHostControl, Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="77cf0-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77cf0-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="77cf0-107">Return Value</span></span>  
  
|<span data-ttu-id="77cf0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="77cf0-108">HRESULT</span></span>|<span data-ttu-id="77cf0-109">Description</span><span class="sxs-lookup"><span data-stu-id="77cf0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="77cf0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="77cf0-110">S_OK</span></span>|<span data-ttu-id="77cf0-111">`SetHostControl` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="77cf0-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="77cf0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="77cf0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="77cf0-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="77cf0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="77cf0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="77cf0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="77cf0-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="77cf0-115">The call timed out.</span></span>|  
|<span data-ttu-id="77cf0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="77cf0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="77cf0-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="77cf0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="77cf0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="77cf0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="77cf0-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="77cf0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="77cf0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="77cf0-120">E_FAIL</span></span>|<span data-ttu-id="77cf0-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="77cf0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="77cf0-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="77cf0-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="77cf0-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="77cf0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="77cf0-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="77cf0-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="77cf0-125">Le CLR a déjà été initialisé.</span><span class="sxs-lookup"><span data-stu-id="77cf0-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77cf0-126">Notes</span><span class="sxs-lookup"><span data-stu-id="77cf0-126">Remarks</span></span>  
 <span data-ttu-id="77cf0-127">Vous devez appeler `SetHostControl` avant que le CLR est initialisé, autrement dit, avant d’appeler [méthode Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) ou utiliser une de la [Interfaces de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="77cf0-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="77cf0-128">Il est recommandé d’appeler `SetHostControl` immédiatement après l’appel [CorBindToCurrentRuntime, fonction](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) ou [fonction CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="77cf0-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77cf0-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="77cf0-129">Requirements</span></span>  
 <span data-ttu-id="77cf0-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77cf0-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77cf0-131">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="77cf0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="77cf0-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77cf0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77cf0-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77cf0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cf0-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77cf0-134">See also</span></span>

- [<span data-ttu-id="77cf0-135">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="77cf0-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="77cf0-136">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="77cf0-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
