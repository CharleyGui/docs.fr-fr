---
title: IHostSecurityManager::GetSecurityContext, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176251"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="2148e-102">IHostSecurityManager::GetSecurityContext, méthode</span><span class="sxs-lookup"><span data-stu-id="2148e-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="2148e-103">Obtient le [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) demandé de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="2148e-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2148e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2148e-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2148e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2148e-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="2148e-106">[dans] L’une des valeurs [EContextType,](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) indiquant quel type de contexte de sécurité à retourner.</span><span class="sxs-lookup"><span data-stu-id="2148e-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="2148e-107">[out] L’adresse d’un `IHostSecurityContext` pointeur d’interface à la de `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="2148e-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2148e-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2148e-108">Return Value</span></span>  
  
|<span data-ttu-id="2148e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2148e-109">HRESULT</span></span>|<span data-ttu-id="2148e-110">Description</span><span class="sxs-lookup"><span data-stu-id="2148e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2148e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2148e-111">S_OK</span></span>|<span data-ttu-id="2148e-112">`GetSecurityContext`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2148e-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="2148e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2148e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2148e-114">L’heure courante de l’exécution de la langue (CLR) n’a pas été chargée dans un processus, ou le CLR est dans un état où il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="2148e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2148e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2148e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2148e-116">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="2148e-116">The call timed out.</span></span>|  
|<span data-ttu-id="2148e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2148e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2148e-118">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="2148e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2148e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2148e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2148e-120">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="2148e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2148e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2148e-121">E_FAIL</span></span>|<span data-ttu-id="2148e-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2148e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2148e-123">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2148e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2148e-124">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2148e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2148e-125">Notes </span><span class="sxs-lookup"><span data-stu-id="2148e-125">Remarks</span></span>  
 <span data-ttu-id="2148e-126">Un hôte peut contrôler l’accès au code aux jetons de thread par le CLR et le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2148e-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="2148e-127">Il peut également s’assurer que les informations complètes du contexte de sécurité sont transmises à travers des opérations asynchrones ou des points de code avec un accès restreint au code.</span><span class="sxs-lookup"><span data-stu-id="2148e-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="2148e-128">`IHostSecurityContext`encapsule cette information de contexte de sécurité, qui est opaque pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="2148e-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="2148e-129">Le CLR capture cette information et les déplace à travers la répartition des éléments de la piscine de fil, l’exécution de finalisateur, et la construction de module et de classe.</span><span class="sxs-lookup"><span data-stu-id="2148e-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2148e-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2148e-130">Requirements</span></span>  
 <span data-ttu-id="2148e-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2148e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2148e-132">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="2148e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2148e-133">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2148e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2148e-134">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2148e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2148e-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2148e-135">See also</span></span>

- [<span data-ttu-id="2148e-136">EContextType, énumération</span><span class="sxs-lookup"><span data-stu-id="2148e-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="2148e-137">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="2148e-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="2148e-138">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="2148e-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
