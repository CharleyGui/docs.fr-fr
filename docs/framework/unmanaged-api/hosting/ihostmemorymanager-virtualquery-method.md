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
ms.openlocfilehash: 16d146766786f129d6da38bde1126ce8afe5e70f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963688"
---
# <a name="ihostmemorymanagervirtualquery-method"></a><span data-ttu-id="bfda6-102">IHostMemoryManager::VirtualQuery, méthode</span><span class="sxs-lookup"><span data-stu-id="bfda6-102">IHostMemoryManager::VirtualQuery Method</span></span>
<span data-ttu-id="bfda6-103">Sert de wrapper logique pour la fonction Win32 correspondante.</span><span class="sxs-lookup"><span data-stu-id="bfda6-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="bfda6-104">L’implémentation Win32 de `VirtualQuery` récupère des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="bfda6-104">The Win32 implementation of `VirtualQuery` retrieves information about a range of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfda6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfda6-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfda6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bfda6-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="bfda6-107">dans Pointeur vers l’adresse de la mémoire virtuelle à interroger.</span><span class="sxs-lookup"><span data-stu-id="bfda6-107">[in] A pointer to the address in virtual memory to be queried.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="bfda6-108">à Pointeur vers une structure qui contient des informations sur la région de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bfda6-108">[out] A pointer to a structure that contains information about the specified memory region.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="bfda6-109">dans Taille, en octets, de la mémoire tampon vers `lpBuffer` laquelle pointe.</span><span class="sxs-lookup"><span data-stu-id="bfda6-109">[in] The size, in bytes, of the buffer that `lpBuffer` points to.</span></span>  
  
 `pResult`  
 <span data-ttu-id="bfda6-110">à Pointeur vers le nombre d’octets retournés par la mémoire tampon d’informations.</span><span class="sxs-lookup"><span data-stu-id="bfda6-110">[out] A pointer to the number of bytes returned by the information buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfda6-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bfda6-111">Return Value</span></span>  
  
|<span data-ttu-id="bfda6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bfda6-112">HRESULT</span></span>|<span data-ttu-id="bfda6-113">Description</span><span class="sxs-lookup"><span data-stu-id="bfda6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bfda6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="bfda6-114">S_OK</span></span>|<span data-ttu-id="bfda6-115">`VirtualQuery`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="bfda6-115">`VirtualQuery` returned successfully.</span></span>|  
|<span data-ttu-id="bfda6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bfda6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bfda6-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="bfda6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bfda6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bfda6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bfda6-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="bfda6-119">The call timed out.</span></span>|  
|<span data-ttu-id="bfda6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bfda6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bfda6-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="bfda6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bfda6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bfda6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bfda6-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="bfda6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bfda6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bfda6-124">E_FAIL</span></span>|<span data-ttu-id="bfda6-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bfda6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bfda6-126">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="bfda6-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bfda6-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bfda6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfda6-128">Notes</span><span class="sxs-lookup"><span data-stu-id="bfda6-128">Remarks</span></span>  
 <span data-ttu-id="bfda6-129">`VirtualQuery`fournit des informations sur une plage de pages dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="bfda6-129">`VirtualQuery` provides information about a range of pages in the virtual address space of the calling process.</span></span> <span data-ttu-id="bfda6-130">Cette implémentation définit la valeur du `pResult` paramètre sur le nombre d’octets retournés dans la mémoire tampon d’informations et retourne une valeur HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bfda6-130">This implementation sets the value of the `pResult` parameter to the number of bytes returned in the information buffer, and returns an HRESULT value.</span></span> <span data-ttu-id="bfda6-131">Dans la fonction `VirtualQuery` Win32, la valeur de retour est la taille de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="bfda6-131">In the Win32 `VirtualQuery` function, the return value is the buffer size.</span></span> <span data-ttu-id="bfda6-132">Pour plus d’informations, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="bfda6-132">For more information, see the Windows Platform documentation.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bfda6-133">L’implémentation de du système d' `VirtualQuery` exploitation de n’entraîne pas de blocage et peut s’exécuter jusqu’à la fin avec les threads aléatoires suspendus dans le code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bfda6-133">The operating system's implementation of `VirtualQuery` does not incur deadlock and can run to completion with random threads suspended in user code.</span></span> <span data-ttu-id="bfda6-134">Soyez très prudent lors de l’implémentation d’une version hébergée de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="bfda6-134">Use great caution when implementing a hosted version of this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfda6-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bfda6-135">Requirements</span></span>  
 <span data-ttu-id="bfda6-136">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfda6-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfda6-137">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bfda6-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bfda6-138">**Bibliothèque** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bfda6-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bfda6-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfda6-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfda6-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bfda6-140">See also</span></span>

- [<span data-ttu-id="bfda6-141">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="bfda6-141">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
