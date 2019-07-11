---
title: IHostMemoryManager::NeedsVirtualAddressSpace, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ed64ad8a6ae8ef46f423471436c3fce29d6fe5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767807"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="6df19-102">IHostMemoryManager::NeedsVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="6df19-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="6df19-103">Avertit l’hôte que le common language runtime (CLR) va essayer d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6df19-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df19-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6df19-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df19-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6df19-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="6df19-106">[in] Adresse de départ de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="6df19-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="6df19-107">[in] La taille, en octets, de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="6df19-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6df19-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6df19-108">Remarks</span></span>  
 <span data-ttu-id="6df19-109">Le `NeedsVirtualAddressSpace` méthode est une méthode de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="6df19-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="6df19-110">Elle est appelée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="6df19-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="6df19-111">Si l’hôte ne souhaite pas que le CLR à utiliser la mémoire spécifiée, elle peut retourner un HRESULT E_OUTOFMEMORY.</span><span class="sxs-lookup"><span data-stu-id="6df19-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df19-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6df19-112">Requirements</span></span>  
 <span data-ttu-id="6df19-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df19-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df19-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6df19-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6df19-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6df19-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6df19-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6df19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df19-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6df19-117">See also</span></span>

- [<span data-ttu-id="6df19-118">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="6df19-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
