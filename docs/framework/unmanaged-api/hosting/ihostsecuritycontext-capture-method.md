---
title: IHostSecurityContext::Capture, méthode
ms.date: 03/30/2017
api_name:
- IHostSecurityContext.Capture
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext::Capture
helpviewer_keywords:
- Capture method [.NET Framework hosting]
- IHostSecurityContext::Capture method [.NET Framework hosting]
ms.assetid: ae0836d0-1170-4494-bac5-d0e809df51a2
topic_type:
- apiref
ms.openlocfilehash: 96bb3a530bf4c63c3662ecfa635a929381fc0de6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121537"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="e66ab-102">IHostSecurityContext::Capture, méthode</span><span class="sxs-lookup"><span data-stu-id="e66ab-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="e66ab-103">Obtient un clone de l’instance [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) retournée à partir d’un appel à [IHostSecurityManager :: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="e66ab-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e66ab-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e66ab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e66ab-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="e66ab-106">à Pointeur vers l’adresse d’un clone de l’objet `IHostSecurityContext` à capturer.</span><span class="sxs-lookup"><span data-stu-id="e66ab-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e66ab-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e66ab-107">Return Value</span></span>  
  
|<span data-ttu-id="e66ab-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e66ab-108">HRESULT</span></span>|<span data-ttu-id="e66ab-109">Description</span><span class="sxs-lookup"><span data-stu-id="e66ab-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e66ab-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e66ab-110">S_OK</span></span>|<span data-ttu-id="e66ab-111">`Capture` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="e66ab-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="e66ab-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e66ab-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e66ab-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="e66ab-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e66ab-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e66ab-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e66ab-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="e66ab-115">The call timed out.</span></span>|  
|<span data-ttu-id="e66ab-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e66ab-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e66ab-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="e66ab-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e66ab-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e66ab-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e66ab-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="e66ab-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e66ab-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e66ab-120">E_FAIL</span></span>|<span data-ttu-id="e66ab-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="e66ab-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e66ab-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e66ab-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e66ab-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e66ab-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e66ab-124">Notes</span><span class="sxs-lookup"><span data-stu-id="e66ab-124">Remarks</span></span>  
 <span data-ttu-id="e66ab-125">Le pointeur d’interface retourné par `Capture` est un clone du contexte capturé.</span><span class="sxs-lookup"><span data-stu-id="e66ab-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="e66ab-126">Lorsque ces informations sont déplacées à travers un point de code asynchrone, leur durée de vie est séparée de celle du pointeur sur lequel l’appel a été effectué.</span><span class="sxs-lookup"><span data-stu-id="e66ab-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="e66ab-127">Le pointeur d’origine peut donc être relâché.</span><span class="sxs-lookup"><span data-stu-id="e66ab-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e66ab-128">spécifications</span><span class="sxs-lookup"><span data-stu-id="e66ab-128">Requirements</span></span>  
 <span data-ttu-id="e66ab-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e66ab-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66ab-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e66ab-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e66ab-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e66ab-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e66ab-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e66ab-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66ab-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e66ab-133">See also</span></span>

- [<span data-ttu-id="e66ab-134">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="e66ab-134">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e66ab-135">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="e66ab-135">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
