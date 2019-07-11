---
title: IHostMemoryManager::VirtualQuery, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 684d5e41e1d7cee2775aa0988d33a974315eac4e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772735"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="cd2f1-102">IHostMemoryManager::VirtualQuery, méthode</span><span class="sxs-lookup"><span data-stu-id="cd2f1-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="cd2f1-103">Sert de wrapper logique pour la fonction Win32 correspondante.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="cd2f1-104">L’implémentation Win32 de `VirtualQuery` récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2f1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd2f1-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd2f1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd2f1-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="cd2f1-107">[in] Pointeur vers l’adresse dans la mémoire virtuelle à interroger.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="cd2f1-108">[out] Un pointeur vers une structure qui contient des informations sur la région de mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="cd2f1-109">[in] La taille, en octets, de la mémoire tampon qui `lpBuffer` pointe vers.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="cd2f1-110">[out] Pointeur vers le nombre d’octets retournés par la mémoire tampon d’informations.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd2f1-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cd2f1-111">Return Value</span></span>  
  
|<span data-ttu-id="cd2f1-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd2f1-112">HRESULT</span></span>|<span data-ttu-id="cd2f1-113">Description</span><span class="sxs-lookup"><span data-stu-id="cd2f1-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd2f1-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd2f1-114">S_OK</span></span>|<span data-ttu-id="cd2f1-115">`VirtualQuery` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="cd2f1-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd2f1-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd2f1-117">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter le code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd2f1-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd2f1-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd2f1-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-119">The call timed out.</span></span>|  
|<span data-ttu-id="cd2f1-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd2f1-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd2f1-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd2f1-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd2f1-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd2f1-123">Un événement a été annulé alors qu’un thread bloqué ou Fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd2f1-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd2f1-124">E_FAIL</span></span>|<span data-ttu-id="cd2f1-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd2f1-126">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable au sein du processus.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd2f1-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd2f1-128">Notes</span><span class="sxs-lookup"><span data-stu-id="cd2f1-128">Remarks</span></span>  
 <span data-ttu-id="cd2f1-129">`VirtualQuery` Fournit des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="cd2f1-130">Cette implémentation définit la valeur de la `pResult` paramètre pour le nombre d’octets retournés dans la mémoire tampon d’informations et retourne une valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="cd2f1-131">Dans Win32 `VirtualQuery` (fonction), la valeur de retour est la taille du tampon.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="cd2f1-132">Pour plus d’informations, consultez la documentation de la plateforme de Windows.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd2f1-133">Implémentation du système d’exploitation de `VirtualQuery` n’entraîne pas d’interblocage et peut s’exécuter intégralement avec des threads aléatoires interrompus dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="cd2f1-134">Procédez avec précaution lors de l’implémentation d’une version hébergée de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="cd2f1-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd2f1-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cd2f1-135">Requirements</span></span>  
 <span data-ttu-id="cd2f1-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd2f1-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd2f1-137">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cd2f1-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd2f1-138">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cd2f1-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd2f1-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd2f1-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd2f1-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd2f1-140">See also</span></span>

- [<span data-ttu-id="cd2f1-141">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="cd2f1-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
