---
title: IHostMemoryManager::VirtualProtect, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualProtect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualProtect
helpviewer_keywords:
- IHostMemoryManager::VirtualProtect method [.NET Framework hosting]
- VirtualProtect method [.NET Framework hosting]
ms.assetid: 13be0299-df0d-4951-aabf-0676a30b385f
topic_type:
- apiref
ms.openlocfilehash: d39ad45e143026f40ffcf1339e923837f9e812c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195857"
---
# <a name="ihostmemorymanagervirtualprotect-method"></a><span data-ttu-id="26d24-102">IHostMemoryManager::VirtualProtect, méthode</span><span class="sxs-lookup"><span data-stu-id="26d24-102">IHostMemoryManager::VirtualProtect Method</span></span>
<span data-ttu-id="26d24-103">Sert de wrapper logique pour la fonction Win32 correspondante.</span><span class="sxs-lookup"><span data-stu-id="26d24-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="26d24-104">L’implémentation Win32 de `VirtualProtect` modifie la protection sur une région de pages validées dans l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="26d24-104">The Win32 implementation of `VirtualProtect` changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d24-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26d24-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualProtect (  
    [in]  void*   lpAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flNewProtect,  
    [out] DWORD*  pflOldProtect  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26d24-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="26d24-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="26d24-107">dans Pointeur vers l’adresse de base de la mémoire virtuelle dont les attributs de protection doivent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="26d24-107">[in] A pointer to the base address of the virtual memory whose protection attributes are to be changed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="26d24-108">dans Taille, en octets, de la région des pages de mémoire à modifier.</span><span class="sxs-lookup"><span data-stu-id="26d24-108">[in] The size, in bytes, of the region of memory pages to be changed.</span></span>  
  
 `flNewProtect`  
 <span data-ttu-id="26d24-109">dans Type de protection de la mémoire à appliquer.</span><span class="sxs-lookup"><span data-stu-id="26d24-109">[in] The type of memory protection to apply.</span></span>  
  
 `pflOldProtect`  
 <span data-ttu-id="26d24-110">à Pointeur vers la valeur de protection de la mémoire précédente.</span><span class="sxs-lookup"><span data-stu-id="26d24-110">[out] A pointer to the previous memory protection value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26d24-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="26d24-111">Return Value</span></span>  
  
|<span data-ttu-id="26d24-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="26d24-112">HRESULT</span></span>|<span data-ttu-id="26d24-113">Description</span><span class="sxs-lookup"><span data-stu-id="26d24-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26d24-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="26d24-114">S_OK</span></span>|<span data-ttu-id="26d24-115">`VirtualProtect` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="26d24-115">`VirtualProtect` returned successfully.</span></span>|  
|<span data-ttu-id="26d24-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="26d24-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="26d24-117">Le common language runtime (CLR) n’a pas été chargé dans un processus, ou le CLR est dans un État dans lequel il ne peut pas exécuter de code managé ou traiter correctement l’appel.</span><span class="sxs-lookup"><span data-stu-id="26d24-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="26d24-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="26d24-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="26d24-119">Le délai d’attente de l’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="26d24-119">The call timed out.</span></span>|  
|<span data-ttu-id="26d24-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="26d24-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="26d24-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="26d24-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="26d24-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="26d24-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="26d24-123">Un événement a été annulé alors qu’un thread ou une fibre bloqué était en attente.</span><span class="sxs-lookup"><span data-stu-id="26d24-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="26d24-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="26d24-124">E_FAIL</span></span>|<span data-ttu-id="26d24-125">Une défaillance catastrophique inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="26d24-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="26d24-126">Quand une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="26d24-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="26d24-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="26d24-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26d24-128">Notes</span><span class="sxs-lookup"><span data-stu-id="26d24-128">Remarks</span></span>  
 <span data-ttu-id="26d24-129">Cette implémentation de `VirtualProtect` retourne une valeur HRESULT, tandis que l’implémentation Win32 retourne une valeur différente de zéro pour indiquer la réussite, et une valeur zéro pour indiquer l’échec.</span><span class="sxs-lookup"><span data-stu-id="26d24-129">This implementation of `VirtualProtect` returns an HRESULT value, while the Win32 implementation returns a non-zero value to indicate success, and a zero value to indicate failure.</span></span> <span data-ttu-id="26d24-130">Pour plus d’informations, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="26d24-130">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d24-131">spécifications</span><span class="sxs-lookup"><span data-stu-id="26d24-131">Requirements</span></span>  
 <span data-ttu-id="26d24-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d24-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d24-133">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26d24-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26d24-134">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26d24-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26d24-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26d24-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d24-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26d24-136">See also</span></span>

- [<span data-ttu-id="26d24-137">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="26d24-137">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
