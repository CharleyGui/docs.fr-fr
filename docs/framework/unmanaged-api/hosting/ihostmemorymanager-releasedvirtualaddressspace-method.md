---
title: IHostMemoryManager::ReleasedVirtualAddressSpace, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
ms.openlocfilehash: 8a875d59d270f087ce22079830818a9205309cc5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731291"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="4069d-102">IHostMemoryManager::ReleasedVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="4069d-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>

<span data-ttu-id="4069d-103">Avertit l’hôte que le common language runtime (CLR) a fini d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4069d-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4069d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4069d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4069d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4069d-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="4069d-106">dans Pointeur vers l’adresse de début de la mémoire à libérer.</span><span class="sxs-lookup"><span data-stu-id="4069d-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4069d-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="4069d-107">Remarks</span></span>  

 <span data-ttu-id="4069d-108">La `ReleasedVirtualAddressSpace` méthode est une méthode de rappel qui doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="4069d-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="4069d-109">Elle est appelée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="4069d-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4069d-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4069d-110">Requirements</span></span>  

 <span data-ttu-id="4069d-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4069d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4069d-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4069d-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4069d-113">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4069d-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4069d-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4069d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4069d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4069d-115">See also</span></span>

- [<span data-ttu-id="4069d-116">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="4069d-116">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
