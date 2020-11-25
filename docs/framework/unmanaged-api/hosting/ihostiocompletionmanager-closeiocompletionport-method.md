---
title: IHostIoCompletionManager::CloseIoCompletionPort, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: a45f8ab6372776bece09e408bc9887bfaddb0955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727365"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="01ad6-102">IHostIoCompletionManager::CloseIoCompletionPort, méthode</span><span class="sxs-lookup"><span data-stu-id="01ad6-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>

<span data-ttu-id="01ad6-103">Demande que l’hôte ferme un port qui a été ouvert par un appel antérieur à [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="01ad6-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01ad6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01ad6-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01ad6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01ad6-105">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="01ad6-106">dans Handle du port à fermer.</span><span class="sxs-lookup"><span data-stu-id="01ad6-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01ad6-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="01ad6-107">Return Value</span></span>  
  
|<span data-ttu-id="01ad6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01ad6-108">HRESULT</span></span>|<span data-ttu-id="01ad6-109">Description</span><span class="sxs-lookup"><span data-stu-id="01ad6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01ad6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="01ad6-110">S_OK</span></span>|<span data-ttu-id="01ad6-111">`CloseIoCompletionPort` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="01ad6-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="01ad6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01ad6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01ad6-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="01ad6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01ad6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01ad6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01ad6-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="01ad6-115">The call timed out.</span></span>|  
|<span data-ttu-id="01ad6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01ad6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01ad6-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="01ad6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01ad6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01ad6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01ad6-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="01ad6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01ad6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01ad6-120">E_FAIL</span></span>|<span data-ttu-id="01ad6-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="01ad6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01ad6-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="01ad6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01ad6-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01ad6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="01ad6-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="01ad6-124">E_INVALIDARG</span></span>|<span data-ttu-id="01ad6-125">Un descripteur de port non valide a été passé.</span><span class="sxs-lookup"><span data-stu-id="01ad6-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01ad6-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="01ad6-126">Remarks</span></span>  

 <span data-ttu-id="01ad6-127">`hPort` doit être un handle vers un port qui a été créé par un appel antérieur à `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="01ad6-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01ad6-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01ad6-128">Requirements</span></span>  

 <span data-ttu-id="01ad6-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01ad6-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01ad6-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01ad6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01ad6-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01ad6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01ad6-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01ad6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ad6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01ad6-133">See also</span></span>

- [<span data-ttu-id="01ad6-134">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="01ad6-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="01ad6-135">IHostIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="01ad6-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
