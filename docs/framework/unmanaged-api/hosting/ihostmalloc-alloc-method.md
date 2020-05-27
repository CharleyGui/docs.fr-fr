---
title: IHostMAlloc::Alloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: 6f58e2290afa166d48306c0bbb50edd1df36888b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804643"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="9aa0e-102">IHostMAlloc::Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="9aa0e-102">IHostMAlloc::Alloc Method</span></span>
<span data-ttu-id="9aa0e-103">Demande que l’hôte alloue la quantité de mémoire spécifiée à partir du tas.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-103">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aa0e-104">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aa0e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9aa0e-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="9aa0e-106">dans Taille, en octets, de la demande d’allocation de mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="9aa0e-107">dans L’une des valeurs [EMemoryCriticalLevel,](ememorycriticallevel-enumeration.md) , indiquant l’impact d’un échec d’allocation.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="9aa0e-108">à Pointeur vers la mémoire allouée, ou null si la demande n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-108">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9aa0e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9aa0e-109">Return Value</span></span>  
  
|<span data-ttu-id="9aa0e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9aa0e-110">HRESULT</span></span>|<span data-ttu-id="9aa0e-111">Description</span><span class="sxs-lookup"><span data-stu-id="9aa0e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9aa0e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9aa0e-112">S_OK</span></span>|<span data-ttu-id="9aa0e-113">`Alloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-113">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="9aa0e-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9aa0e-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9aa0e-115">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9aa0e-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9aa0e-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9aa0e-117">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-117">The call timed out.</span></span>|  
|<span data-ttu-id="9aa0e-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9aa0e-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9aa0e-119">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9aa0e-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9aa0e-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9aa0e-121">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9aa0e-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9aa0e-122">E_FAIL</span></span>|<span data-ttu-id="9aa0e-123">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9aa0e-124">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9aa0e-125">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9aa0e-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9aa0e-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9aa0e-127">Mémoire disponible insuffisante pour terminer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="9aa0e-127">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9aa0e-128">Notes</span><span class="sxs-lookup"><span data-stu-id="9aa0e-128">Remarks</span></span>  
 <span data-ttu-id="9aa0e-129">Le CLR obtient un pointeur d’interface vers une `IHostMalloc` instance en appelant la méthode [IHostMemoryManager :: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9aa0e-129">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa0e-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9aa0e-130">Requirements</span></span>  
 <span data-ttu-id="9aa0e-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aa0e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa0e-132">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9aa0e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9aa0e-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9aa0e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aa0e-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa0e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa0e-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aa0e-135">See also</span></span>

- [<span data-ttu-id="9aa0e-136">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="9aa0e-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="9aa0e-137">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="9aa0e-137">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
