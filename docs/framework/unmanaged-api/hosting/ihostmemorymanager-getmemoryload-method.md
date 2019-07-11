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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 917ebe3c2001a9bc87978685d7f9a19eb3d98220
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767201"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="8443d-102">IHostMemoryManager::GetMemoryLoad, méthode</span><span class="sxs-lookup"><span data-stu-id="8443d-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="8443d-103">Obtient la quantité de mémoire physique qui est actuellement en cours d’utilisation et par conséquent pas disponible, comme indiqué par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="8443d-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8443d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8443d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8443d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8443d-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="8443d-106">[out] Pointeur vers le pourcentage approximatif de mémoire physique totale qui est actuellement en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="8443d-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="8443d-107">[out] Pointeur vers le nombre d’octets disponibles pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="8443d-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8443d-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8443d-108">Return Value</span></span>  
  
|<span data-ttu-id="8443d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8443d-109">HRESULT</span></span>|<span data-ttu-id="8443d-110">Description</span><span class="sxs-lookup"><span data-stu-id="8443d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8443d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8443d-111">S_OK</span></span>|<span data-ttu-id="8443d-112">`GetMemoryLoad` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8443d-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="8443d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8443d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8443d-114">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="8443d-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8443d-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8443d-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8443d-116">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="8443d-116">The call timed out.</span></span>|  
|<span data-ttu-id="8443d-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8443d-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8443d-118">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="8443d-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8443d-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8443d-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8443d-120">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="8443d-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8443d-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8443d-121">E_FAIL</span></span>|<span data-ttu-id="8443d-122">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="8443d-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8443d-123">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="8443d-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8443d-124">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="8443d-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8443d-125">Notes</span><span class="sxs-lookup"><span data-stu-id="8443d-125">Remarks</span></span>  
 <span data-ttu-id="8443d-126">`GetMemoryLoad` encapsule le Win32 `GlobalMemoryStatus` (fonction).</span><span class="sxs-lookup"><span data-stu-id="8443d-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="8443d-127">La valeur de `pMemoryLoad` est l’équivalent de la `dwMemoryLoad` champ dans le `MEMORYSTATUS` structure retournée à partir de `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="8443d-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="8443d-128">Le runtime utilise la valeur de retour comme une méthode heuristique pour le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="8443d-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="8443d-129">Par exemple, si l’hôte signale que la majorité de la mémoire est en cours d’utilisation, le garbage collector peut choisir de collecter à partir de plusieurs générations afin d’augmenter la quantité de mémoire qui peut potentiellement deviennent disponible.</span><span class="sxs-lookup"><span data-stu-id="8443d-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8443d-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8443d-130">Requirements</span></span>  
 <span data-ttu-id="8443d-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8443d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8443d-132">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8443d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8443d-133">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8443d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8443d-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8443d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8443d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8443d-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="8443d-136">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="8443d-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
