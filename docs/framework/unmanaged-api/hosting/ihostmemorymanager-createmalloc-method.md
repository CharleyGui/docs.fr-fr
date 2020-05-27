---
title: IHostMemoryManager::CreateMAlloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.CreateMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::CreateMAlloc
helpviewer_keywords:
- CreateAlloc method [.NET Framework hosting]
- IHostMemoryManager::CreateMAlloc method [.NET Framework hosting]
ms.assetid: 9ee6e052-bef7-4350-9e4f-edfffd99ad6f
topic_type:
- apiref
ms.openlocfilehash: 89c1d7b043d4369bf16a851924711c3c9d75791e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804527"
---
# <a name="ihostmemorymanagercreatemalloc-method"></a><span data-ttu-id="57e28-102">IHostMemoryManager::CreateMAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="57e28-102">IHostMemoryManager::CreateMAlloc Method</span></span>
<span data-ttu-id="57e28-103">Obtient un pointeur d’interface vers une instance d' [IHostMalloc](ihostmalloc-interface.md) qui est utilisé pour effectuer des demandes d’allocation à partir d’un tas créé par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="57e28-103">Gets an interface pointer to an [IHostMAlloc](ihostmalloc-interface.md) instance that is used to make allocation requests from a heap created by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57e28-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMalloc (  
    [in]  DWORD         dwMallocType,  
    [out] IHostMalloc **ppMalloc  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57e28-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="57e28-105">Parameters</span></span>  
 `dwMallocType`  
 <span data-ttu-id="57e28-106">dans Combinaison d' [MALLOC_TYPE](malloc-type-enumeration.md) indicateurs qui spécifie les caractéristiques de la mémoire qui est allouée.</span><span class="sxs-lookup"><span data-stu-id="57e28-106">[in] A combination of [MALLOC_TYPE](malloc-type-enumeration.md) flags that specifies the characteristics of the memory that is being allocated.</span></span>  
  
 `ppMAlloc`  
 <span data-ttu-id="57e28-107">à Pointeur vers l’adresse d’une `IHostMAlloc` instance fournie par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="57e28-107">[out] A pointer to the address of an `IHostMAlloc` instance provided by the host.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57e28-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="57e28-108">Return Value</span></span>  
  
|<span data-ttu-id="57e28-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57e28-109">HRESULT</span></span>|<span data-ttu-id="57e28-110">Description</span><span class="sxs-lookup"><span data-stu-id="57e28-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57e28-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="57e28-111">S_OK</span></span>|<span data-ttu-id="57e28-112">`CreateMAlloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="57e28-112">`CreateMAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="57e28-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57e28-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57e28-114">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="57e28-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57e28-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57e28-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57e28-116">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="57e28-116">The call timed out.</span></span>|  
|<span data-ttu-id="57e28-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57e28-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57e28-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="57e28-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57e28-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57e28-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57e28-120">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="57e28-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57e28-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57e28-121">E_FAIL</span></span>|<span data-ttu-id="57e28-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="57e28-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57e28-123">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="57e28-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57e28-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57e28-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="57e28-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="57e28-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="57e28-126">La mémoire physique disponible est insuffisante pour terminer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="57e28-126">Not enough physical memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57e28-127">Notes</span><span class="sxs-lookup"><span data-stu-id="57e28-127">Remarks</span></span>  
 <span data-ttu-id="57e28-128">`CreateMAlloc`retourne un objet qui permet au CLR de faire des demandes d’allocation via l’hôte au lieu d’utiliser les fonctions Win32 standard.</span><span class="sxs-lookup"><span data-stu-id="57e28-128">`CreateMAlloc` returns an object that allows the CLR to make allocation requests through the host instead of using the standard Win32 functions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57e28-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="57e28-129">Requirements</span></span>  
 <span data-ttu-id="57e28-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57e28-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57e28-131">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57e28-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57e28-132">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="57e28-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57e28-133">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57e28-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e28-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57e28-134">See also</span></span>

- [<span data-ttu-id="57e28-135">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="57e28-135">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
- [<span data-ttu-id="57e28-136">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="57e28-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
