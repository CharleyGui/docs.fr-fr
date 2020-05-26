---
title: IHostMAlloc::DebugAlloc, méthode
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 8475362ede5ea28009d5abc54c286d6f2a6fed0f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804635"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="d288d-102">IHostMAlloc::DebugAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="d288d-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="d288d-103">Demande que l’hôte alloue la quantité de mémoire spécifiée à partir du tas et effectue également le suivi de l’emplacement où la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="d288d-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d288d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d288d-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d288d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d288d-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="d288d-106">dans Taille, en octets, de la demande d’allocation de mémoire actuelle.</span><span class="sxs-lookup"><span data-stu-id="d288d-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="d288d-107">dans L’une des valeurs [EMemoryCriticalLevel,](ememorycriticallevel-enumeration.md) , indiquant l’impact d’un échec d’allocation.</span><span class="sxs-lookup"><span data-stu-id="d288d-107">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="d288d-108">dans Fichier de code de l’exécutable en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="d288d-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="d288d-109">dans Numéro de la ligne `pszFileName` où l’allocation a été demandée.</span><span class="sxs-lookup"><span data-stu-id="d288d-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="d288d-110">à Pointeur vers la mémoire allouée, ou null si la demande n’a pas pu être effectuée.</span><span class="sxs-lookup"><span data-stu-id="d288d-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d288d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d288d-111">Return Value</span></span>  
  
|<span data-ttu-id="d288d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d288d-112">HRESULT</span></span>|<span data-ttu-id="d288d-113">Description</span><span class="sxs-lookup"><span data-stu-id="d288d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d288d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d288d-114">S_OK</span></span>|<span data-ttu-id="d288d-115">`DebugAlloc`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d288d-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="d288d-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d288d-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d288d-117">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="d288d-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d288d-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d288d-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d288d-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d288d-119">The call timed out.</span></span>|  
|<span data-ttu-id="d288d-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d288d-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d288d-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d288d-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d288d-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d288d-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d288d-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="d288d-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d288d-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d288d-124">E_FAIL</span></span>|<span data-ttu-id="d288d-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d288d-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d288d-126">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d288d-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d288d-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d288d-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d288d-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d288d-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d288d-129">Mémoire disponible insuffisante pour terminer la demande d’allocation.</span><span class="sxs-lookup"><span data-stu-id="d288d-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d288d-130">Notes</span><span class="sxs-lookup"><span data-stu-id="d288d-130">Remarks</span></span>  
 <span data-ttu-id="d288d-131">Le CLR obtient un pointeur d’interface vers une instance [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) en appelant la méthode [IHostMemoryManager :: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d288d-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="d288d-132">`DebugAlloc`permet au runtime d’obtenir des informations de fichier de code à utiliser pendant le débogage.</span><span class="sxs-lookup"><span data-stu-id="d288d-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d288d-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d288d-133">Requirements</span></span>  
 <span data-ttu-id="d288d-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d288d-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d288d-135">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d288d-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d288d-136">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d288d-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d288d-137">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d288d-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d288d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d288d-138">See also</span></span>

- [<span data-ttu-id="d288d-139">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="d288d-139">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="d288d-140">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="d288d-140">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
