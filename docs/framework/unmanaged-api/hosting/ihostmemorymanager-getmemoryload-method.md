---
title: IHostMemoryManager::GetMemoryLoad, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176277"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="78e98-102">IHostMemoryManager::GetMemoryLoad, méthode</span><span class="sxs-lookup"><span data-stu-id="78e98-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="78e98-103">Obtient la quantité de mémoire physique qui est actuellement en usage, et donc indisponible, tel que rapporté par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="78e98-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78e98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78e98-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78e98-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="78e98-106">[out] Un pointeur sur le pourcentage approximatif de la mémoire physique totale qui est actuellement utilisé.</span><span class="sxs-lookup"><span data-stu-id="78e98-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="78e98-107">[out] Un pointeur sur le nombre d’octets disponibles à l’heure courante (CLR).</span><span class="sxs-lookup"><span data-stu-id="78e98-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78e98-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="78e98-108">Return Value</span></span>  
  
|<span data-ttu-id="78e98-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78e98-109">HRESULT</span></span>|<span data-ttu-id="78e98-110">Description</span><span class="sxs-lookup"><span data-stu-id="78e98-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78e98-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="78e98-111">S_OK</span></span>|<span data-ttu-id="78e98-112">`GetMemoryLoad`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="78e98-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="78e98-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="78e98-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="78e98-114">Le CLR n’a pas été chargé dans un processus, ou le CLR est dans un état dans lequel il ne peut pas exécuter le code géré ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="78e98-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="78e98-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78e98-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="78e98-116">L’appel s’est fait chronométrer.</span><span class="sxs-lookup"><span data-stu-id="78e98-116">The call timed out.</span></span>|  
|<span data-ttu-id="78e98-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="78e98-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="78e98-118">L’appelant n’est pas propriétaire de la serrure.</span><span class="sxs-lookup"><span data-stu-id="78e98-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="78e98-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="78e98-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="78e98-120">Un événement a été annulé alors qu’un fil bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="78e98-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="78e98-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="78e98-121">E_FAIL</span></span>|<span data-ttu-id="78e98-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="78e98-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="78e98-123">Lorsqu’une méthode revient E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="78e98-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="78e98-124">Les appels ultérieurs aux méthodes d’hébergement reviennent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="78e98-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78e98-125">Notes </span><span class="sxs-lookup"><span data-stu-id="78e98-125">Remarks</span></span>  
 <span data-ttu-id="78e98-126">`GetMemoryLoad`enveloppe la fonction `GlobalMemoryStatus` Win32.</span><span class="sxs-lookup"><span data-stu-id="78e98-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="78e98-127">La valeur `pMemoryLoad` de est `dwMemoryLoad` l’équivalent `MEMORYSTATUS` du `GlobalMemoryStatus`champ dans la structure restitué de .</span><span class="sxs-lookup"><span data-stu-id="78e98-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="78e98-128">Le temps d’exécution utilise la valeur de retour comme un heuristique pour le collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="78e98-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="78e98-129">Par exemple, si l’hôte signale que la majorité de la mémoire est utilisée, le collecteur d’ordures peut choisir de recueillir de plusieurs générations pour augmenter la quantité de mémoire qui peut potentiellement devenir disponible.</span><span class="sxs-lookup"><span data-stu-id="78e98-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78e98-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78e98-130">Requirements</span></span>  
 <span data-ttu-id="78e98-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78e98-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e98-132">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="78e98-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78e98-133">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78e98-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78e98-134">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e98-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e98-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78e98-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="78e98-136">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="78e98-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
