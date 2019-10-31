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
ms.openlocfilehash: 66aab8081a5cce8c5ba986470bc91eb0604781a5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121514"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="986f7-102">IHostSecurityManager::GetSecurityContext, méthode</span><span class="sxs-lookup"><span data-stu-id="986f7-102">IHostSecurityManager::GetSecurityContext Method</span></span>
<span data-ttu-id="986f7-103">Obtient le [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) demandé à partir de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="986f7-103">Gets the requested [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="986f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="986f7-104">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,   
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="986f7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="986f7-105">Parameters</span></span>  
 `eContextType`  
 <span data-ttu-id="986f7-106">dans L’une des valeurs [EContextType,](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) , indiquant le type de contexte de sécurité à retourner.</span><span class="sxs-lookup"><span data-stu-id="986f7-106">[in] One of the [EContextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="986f7-107">à Adresse d’un pointeur d’interface vers le `IHostSecurityContext` de `eContextType`.</span><span class="sxs-lookup"><span data-stu-id="986f7-107">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="986f7-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="986f7-108">Return Value</span></span>  
  
|<span data-ttu-id="986f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="986f7-109">HRESULT</span></span>|<span data-ttu-id="986f7-110">Description</span><span class="sxs-lookup"><span data-stu-id="986f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="986f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="986f7-111">S_OK</span></span>|<span data-ttu-id="986f7-112">`GetSecurityContext` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="986f7-112">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="986f7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="986f7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="986f7-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="986f7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="986f7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="986f7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="986f7-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="986f7-116">The call timed out.</span></span>|  
|<span data-ttu-id="986f7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="986f7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="986f7-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="986f7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="986f7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="986f7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="986f7-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="986f7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="986f7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="986f7-121">E_FAIL</span></span>|<span data-ttu-id="986f7-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="986f7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="986f7-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="986f7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="986f7-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="986f7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="986f7-125">Notes</span><span class="sxs-lookup"><span data-stu-id="986f7-125">Remarks</span></span>  
 <span data-ttu-id="986f7-126">Un hôte peut contrôler tout l’accès du code aux jetons de thread à la fois par le CLR et le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="986f7-126">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="986f7-127">Il peut également s’assurer que les informations de contexte de sécurité complètes sont transmises sur des opérations asynchrones ou des points de code avec accès restreint au code.</span><span class="sxs-lookup"><span data-stu-id="986f7-127">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="986f7-128">`IHostSecurityContext` encapsule ces informations de contexte de sécurité, qui sont opaques pour le CLR.</span><span class="sxs-lookup"><span data-stu-id="986f7-128">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="986f7-129">Le CLR capture ces informations et les déplace dans la répartition des éléments de travail du pool de threads, l’exécution du finaliseur et la construction des modules et des classes.</span><span class="sxs-lookup"><span data-stu-id="986f7-129">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="986f7-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="986f7-130">Requirements</span></span>  
 <span data-ttu-id="986f7-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="986f7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="986f7-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="986f7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="986f7-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="986f7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="986f7-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="986f7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986f7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="986f7-135">See also</span></span>

- [<span data-ttu-id="986f7-136">EContextType, énumération</span><span class="sxs-lookup"><span data-stu-id="986f7-136">EContextType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [<span data-ttu-id="986f7-137">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="986f7-137">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="986f7-138">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="986f7-138">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
