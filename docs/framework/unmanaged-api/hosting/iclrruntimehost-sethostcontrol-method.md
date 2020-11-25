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
ms.openlocfilehash: 32483be43d4d4fe9d185c091e15a13c6feb95600
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728821"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="a42ce-102">ICLRRuntimeHost::SetHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="a42ce-102">ICLRRuntimeHost::SetHostControl Method</span></span>

<span data-ttu-id="a42ce-103">Définit le pointeur d’interface que le common language runtime (CLR) peut utiliser pour accéder à l’implémentation de l’hôte de l' [interface IHostControl](ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a42ce-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a42ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a42ce-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a42ce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a42ce-105">Parameters</span></span>  

 `pHostControl`  
 <span data-ttu-id="a42ce-106">dans Pointeur d’interface vers l’implémentation de l’hôte de l' [interface IHostControl](ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a42ce-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a42ce-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="a42ce-107">Return Value</span></span>  
  
|<span data-ttu-id="a42ce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a42ce-108">HRESULT</span></span>|<span data-ttu-id="a42ce-109">Description</span><span class="sxs-lookup"><span data-stu-id="a42ce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a42ce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a42ce-110">S_OK</span></span>|<span data-ttu-id="a42ce-111">`SetHostControl` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="a42ce-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="a42ce-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a42ce-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a42ce-113">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="a42ce-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a42ce-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a42ce-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a42ce-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="a42ce-115">The call timed out.</span></span>|  
|<span data-ttu-id="a42ce-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a42ce-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a42ce-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="a42ce-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a42ce-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a42ce-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a42ce-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="a42ce-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a42ce-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a42ce-120">E_FAIL</span></span>|<span data-ttu-id="a42ce-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a42ce-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a42ce-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a42ce-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a42ce-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a42ce-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a42ce-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="a42ce-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="a42ce-125">Le CLR a déjà été initialisé.</span><span class="sxs-lookup"><span data-stu-id="a42ce-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a42ce-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="a42ce-126">Remarks</span></span>  

 <span data-ttu-id="a42ce-127">`SetHostControl`Avant d’initialiser le CLR, vous devez appeler avant d’appeler la [méthode Start](iclrruntimehost-start-method.md) ou d’utiliser l’une des [interfaces de métadonnées](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="a42ce-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="a42ce-128">Il est recommandé d’appeler `SetHostControl` immédiatement après l’appel de la [fonction CorBindToCurrentRuntime,](corbindtocurrentruntime-function.md) ou de la [fonction CorBindToRuntimeEx](corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="a42ce-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a42ce-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a42ce-129">Requirements</span></span>  

 <span data-ttu-id="a42ce-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a42ce-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a42ce-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a42ce-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a42ce-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a42ce-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a42ce-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a42ce-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a42ce-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a42ce-134">See also</span></span>

- [<span data-ttu-id="a42ce-135">ICLRRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a42ce-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="a42ce-136">IHostControl, interface</span><span class="sxs-lookup"><span data-stu-id="a42ce-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
