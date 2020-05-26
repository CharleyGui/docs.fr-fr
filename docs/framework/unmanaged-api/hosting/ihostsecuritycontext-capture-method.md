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
ms.openlocfilehash: 40857620e47befce361ff8cb04af527915051df3
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804207"
---
# <a name="ihostsecuritycontextcapture-method"></a><span data-ttu-id="3fefc-102">IHostSecurityContext::Capture, méthode</span><span class="sxs-lookup"><span data-stu-id="3fefc-102">IHostSecurityContext::Capture Method</span></span>
<span data-ttu-id="3fefc-103">Obtient un clone de l’instance [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) retournée à partir d’un appel à [IHostSecurityManager :: GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="3fefc-103">Gets a clone of the [IHostSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md) instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fefc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fefc-104">Syntax</span></span>  
  
```cpp
HRESULT Capture (  
    [out] IHostSecurityContext** ppClonedContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fefc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3fefc-105">Parameters</span></span>  
 `ppClonedContext`  
 <span data-ttu-id="3fefc-106">à Pointeur vers l’adresse d’un clone de l' `IHostSecurityContext` objet à capturer.</span><span class="sxs-lookup"><span data-stu-id="3fefc-106">[out] A pointer to the address of a clone of the `IHostSecurityContext` object to be captured.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fefc-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3fefc-107">Return Value</span></span>  
  
|<span data-ttu-id="3fefc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fefc-108">HRESULT</span></span>|<span data-ttu-id="3fefc-109">Description</span><span class="sxs-lookup"><span data-stu-id="3fefc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fefc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fefc-110">S_OK</span></span>|<span data-ttu-id="3fefc-111">`Capture`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3fefc-111">`Capture` returned successfully.</span></span>|  
|<span data-ttu-id="3fefc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fefc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fefc-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="3fefc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fefc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fefc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fefc-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="3fefc-115">The call timed out.</span></span>|  
|<span data-ttu-id="3fefc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fefc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fefc-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="3fefc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fefc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fefc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fefc-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="3fefc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fefc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fefc-120">E_FAIL</span></span>|<span data-ttu-id="3fefc-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3fefc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fefc-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="3fefc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fefc-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3fefc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fefc-124">Notes</span><span class="sxs-lookup"><span data-stu-id="3fefc-124">Remarks</span></span>  
 <span data-ttu-id="3fefc-125">Le pointeur d’interface retourné par `Capture` est un clone du contexte capturé.</span><span class="sxs-lookup"><span data-stu-id="3fefc-125">The interface pointer returned from `Capture` is a clone of the captured context.</span></span> <span data-ttu-id="3fefc-126">Lorsque ces informations sont déplacées à travers un point de code asynchrone, leur durée de vie est séparée de celle du pointeur sur lequel l’appel a été effectué.</span><span class="sxs-lookup"><span data-stu-id="3fefc-126">When this information is moved across an asynchronous code point, its lifetime is separated from that of the pointer against which the call was made.</span></span> <span data-ttu-id="3fefc-127">Le pointeur d’origine peut donc être relâché.</span><span class="sxs-lookup"><span data-stu-id="3fefc-127">The original pointer can therefore be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fefc-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3fefc-128">Requirements</span></span>  
 <span data-ttu-id="3fefc-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fefc-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fefc-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3fefc-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fefc-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3fefc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fefc-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fefc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fefc-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3fefc-133">See also</span></span>

- [<span data-ttu-id="3fefc-134">IHostSecurityContext, interface</span><span class="sxs-lookup"><span data-stu-id="3fefc-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="3fefc-135">IHostSecurityManager, interface</span><span class="sxs-lookup"><span data-stu-id="3fefc-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
