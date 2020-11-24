---
title: IHostMAlloc::Free, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Free
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Free
helpviewer_keywords:
- IHostMAlloc::Free method [.NET Framework hosting]
- Free method, IHostMAlloc interface [.NET Framework hosting]
ms.assetid: c89abf5b-1120-4437-8b57-4a99fb3ae7f9
topic_type:
- apiref
ms.openlocfilehash: d4c9048c89d55ed048a55a771572823905a056df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687123"
---
# <a name="ihostmallocfree-method"></a><span data-ttu-id="2d1c8-102">IHostMAlloc::Free, méthode</span><span class="sxs-lookup"><span data-stu-id="2d1c8-102">IHostMAlloc::Free Method</span></span>

<span data-ttu-id="2d1c8-103">Libère de la mémoire qui a été allouée à l’aide de la fonction [Alloc](ihostmalloc-alloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2d1c8-103">Frees memory that was allocated by using the [Alloc](ihostmalloc-alloc-method.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d1c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d1c8-104">Syntax</span></span>  
  
```cpp  
HRESULT Free (  
    [in] void* pMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d1c8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d1c8-105">Parameters</span></span>  

 `pMem`  
 <span data-ttu-id="2d1c8-106">dans Pointeur vers la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-106">[in] A pointer to the memory to be freed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d1c8-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2d1c8-107">Return Value</span></span>  
  
|<span data-ttu-id="2d1c8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d1c8-108">HRESULT</span></span>|<span data-ttu-id="2d1c8-109">Description</span><span class="sxs-lookup"><span data-stu-id="2d1c8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d1c8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d1c8-110">S_OK</span></span>|<span data-ttu-id="2d1c8-111">`Free` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-111">`Free` returned successfully.</span></span>|  
|<span data-ttu-id="2d1c8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d1c8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d1c8-113">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d1c8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d1c8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d1c8-115">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-115">The call timed out.</span></span>|  
|<span data-ttu-id="2d1c8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d1c8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d1c8-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d1c8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d1c8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d1c8-119">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d1c8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d1c8-120">E_FAIL</span></span>|<span data-ttu-id="2d1c8-121">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d1c8-122">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d1c8-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2d1c8-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="2d1c8-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="2d1c8-125">Une tentative a été effectuée pour libérer de la mémoire qui n’a pas été allouée par le biais de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-125">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d1c8-126">Remarques</span><span class="sxs-lookup"><span data-stu-id="2d1c8-126">Remarks</span></span>  

 <span data-ttu-id="2d1c8-127">Si le `pMem` paramètre fait référence à une région de mémoire qui n’a pas été allouée à l’aide d’un appel à `Alloc` , l’hôte doit retourner HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="2d1c8-127">If the `pMem` parameter refers to a region of memory that was not allocated by using a call to `Alloc`, the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d1c8-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d1c8-128">Requirements</span></span>  

 <span data-ttu-id="2d1c8-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d1c8-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d1c8-130">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2d1c8-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d1c8-131">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2d1c8-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d1c8-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d1c8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1c8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d1c8-133">See also</span></span>

- [<span data-ttu-id="2d1c8-134">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="2d1c8-134">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="2d1c8-135">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="2d1c8-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
