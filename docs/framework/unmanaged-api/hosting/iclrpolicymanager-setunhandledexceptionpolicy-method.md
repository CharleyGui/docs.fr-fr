---
title: ICLRPolicyManager::SetUnhandledExceptionPolicy, méthode
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetUnhandledExceptionPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy
helpviewer_keywords:
- ICLRPolicyManager::SetUnhandledExceptionPolicy method [.NET Framework hosting]
- SetUnhandledExceptionPolicy method [.NET Framework hosting]
ms.assetid: 5268480e-280a-4931-b7a3-dc3ffdf7f78f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab00ccd85481f1c6d37e1132e0ecab5e0e86be90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768879"
---
# <a name="iclrpolicymanagersetunhandledexceptionpolicy-method"></a><span data-ttu-id="517fb-102">ICLRPolicyManager::SetUnhandledExceptionPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="517fb-102">ICLRPolicyManager::SetUnhandledExceptionPolicy Method</span></span>
<span data-ttu-id="517fb-103">Spécifie le comportement du common language runtime (CLR) lorsqu’une exception non gérée se produit.</span><span class="sxs-lookup"><span data-stu-id="517fb-103">Specifies the behavior of the common language runtime (CLR) when an unhandled exception occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="517fb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="517fb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnhandledExceptionPolicy (  
    [in] EClrUnhandledExceptionPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="517fb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="517fb-105">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="517fb-106">[in] Un de la [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) valeurs indiquant si le comportement est défini par le CLR ou de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="517fb-106">[in] One of the [EClrUnhandledException](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md) values, indicating whether the behavior is set by the CLR or the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="517fb-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="517fb-107">Return Value</span></span>  
  
|<span data-ttu-id="517fb-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="517fb-108">HRESULT</span></span>|<span data-ttu-id="517fb-109">Description</span><span class="sxs-lookup"><span data-stu-id="517fb-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="517fb-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="517fb-110">S_OK</span></span>|<span data-ttu-id="517fb-111">`SetUnhandledExceptionPolicy` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="517fb-111">`SetUnhandledExceptionPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="517fb-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="517fb-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="517fb-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="517fb-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="517fb-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="517fb-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="517fb-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="517fb-115">The call timed out.</span></span>|  
|<span data-ttu-id="517fb-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="517fb-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="517fb-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="517fb-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="517fb-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="517fb-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="517fb-119">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="517fb-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="517fb-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="517fb-120">E_FAIL</span></span>|<span data-ttu-id="517fb-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="517fb-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="517fb-122">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="517fb-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="517fb-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="517fb-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="517fb-124">Notes</span><span class="sxs-lookup"><span data-stu-id="517fb-124">Remarks</span></span>  
 <span data-ttu-id="517fb-125">Par défaut, le CLR est le dernier gestionnaire de toutes les exceptions non gérées et son comportement par défaut consiste à détruire le processus.</span><span class="sxs-lookup"><span data-stu-id="517fb-125">By default, the CLR is the final handler for all unhandled exceptions, and its default behavior is to tear down the process.</span></span> <span data-ttu-id="517fb-126">L’hôte peut modifier ce comportement en définissant le `policy` valeur à eHostDeterminedPolicy.</span><span class="sxs-lookup"><span data-stu-id="517fb-126">The host can change this behavior by setting the `policy` value to eHostDeterminedPolicy.</span></span> <span data-ttu-id="517fb-127">Cette valeur permet à l’hôte d’implémenter son propre comportement par défaut, comme dans les versions antérieures du CLR.</span><span class="sxs-lookup"><span data-stu-id="517fb-127">This value allows the host to implement its own default behavior, as with earlier versions of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="517fb-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="517fb-128">Requirements</span></span>  
 <span data-ttu-id="517fb-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="517fb-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="517fb-130">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="517fb-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="517fb-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="517fb-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="517fb-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="517fb-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517fb-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="517fb-133">See also</span></span>

- [<span data-ttu-id="517fb-134">EClrUnhandledException, énumération</span><span class="sxs-lookup"><span data-stu-id="517fb-134">EClrUnhandledException Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrunhandledexception-enumeration.md)
- [<span data-ttu-id="517fb-135">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="517fb-135">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="517fb-136">ICLRPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="517fb-136">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="517fb-137">IHostPolicyManager, interface</span><span class="sxs-lookup"><span data-stu-id="517fb-137">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
