---
title: IHostIoCompletionManager::Bind, méthode
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 5231db8de6129ed593e4e0d508b312b7034c01f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733904"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="8a063-102">IHostIoCompletionManager::Bind, méthode</span><span class="sxs-lookup"><span data-stu-id="8a063-102">IHostIoCompletionManager::Bind Method</span></span>

<span data-ttu-id="8a063-103">Lie le handle spécifié à un port de terminaison d’e/s qui a été créé par un appel antérieur à [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="8a063-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a063-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a063-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a063-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a063-105">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="8a063-106">dans Le port de terminaison d’e/s auquel effectuer la liaison `hHandle` .</span><span class="sxs-lookup"><span data-stu-id="8a063-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="8a063-107">Si la valeur de `hPort` est null, `hHandle` est lié au port de terminaison d’e/s par défaut.</span><span class="sxs-lookup"><span data-stu-id="8a063-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="8a063-108">dans Handle du système d’exploitation auquel effectuer la liaison `hPort` .</span><span class="sxs-lookup"><span data-stu-id="8a063-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a063-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8a063-109">Return Value</span></span>  
  
|<span data-ttu-id="8a063-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a063-110">HRESULT</span></span>|<span data-ttu-id="8a063-111">Description</span><span class="sxs-lookup"><span data-stu-id="8a063-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a063-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a063-112">S_OK</span></span>|<span data-ttu-id="8a063-113">`Bind` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8a063-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="8a063-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8a063-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8a063-115">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="8a063-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8a063-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8a063-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8a063-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8a063-117">The call timed out.</span></span>|  
|<span data-ttu-id="8a063-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8a063-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8a063-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8a063-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8a063-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8a063-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8a063-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="8a063-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8a063-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a063-122">E_FAIL</span></span>|<span data-ttu-id="8a063-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8a063-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8a063-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="8a063-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8a063-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8a063-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a063-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a063-126">Remarks</span></span>  

 <span data-ttu-id="8a063-127">Un port de terminaison d’e/s est créé à l’aide d’un appel à `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="8a063-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="8a063-128">Le CLR appelle `Bind` pour lier un handle à ce port.</span><span class="sxs-lookup"><span data-stu-id="8a063-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a063-129">Quand une demande d’e/s se termine, l’hôte doit appeler la méthode [ICLRIoCompletionManager :: OnComplete](iclriocompletionmanager-oncomplete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8a063-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a063-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a063-130">Requirements</span></span>  

 <span data-ttu-id="8a063-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a063-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a063-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8a063-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a063-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a063-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a063-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a063-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a063-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a063-135">See also</span></span>

- [<span data-ttu-id="8a063-136">ICLRIoCompletionManager, interface</span><span class="sxs-lookup"><span data-stu-id="8a063-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
