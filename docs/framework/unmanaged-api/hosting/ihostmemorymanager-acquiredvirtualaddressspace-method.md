---
title: IHostMemoryManager::AcquiredVirtualAddressSpace, méthode
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
ms.openlocfilehash: 58fce616ae05dcc622369a706f010f91d657389f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700624"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="562a4-102">IHostMemoryManager::AcquiredVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="562a4-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>

<span data-ttu-id="562a4-103">Avertit l’hôte que le common language runtime (CLR) a acquis la mémoire spécifiée à partir du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="562a4-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="562a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="562a4-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="562a4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="562a4-105">Parameters</span></span>  

 `startAddress`  
 <span data-ttu-id="562a4-106">dans Adresse de début de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="562a4-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="562a4-107">dans Taille, en octets, de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="562a4-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="562a4-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="562a4-108">Remarks</span></span>  

 <span data-ttu-id="562a4-109">La `AcquiredVirtualAddressSpace` méthode est une méthode de rappel qui doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="562a4-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="562a4-110">Elle est appelée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="562a4-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="562a4-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="562a4-111">Requirements</span></span>  

 <span data-ttu-id="562a4-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="562a4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="562a4-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="562a4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="562a4-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="562a4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="562a4-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="562a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="562a4-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="562a4-116">See also</span></span>

- [<span data-ttu-id="562a4-117">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="562a4-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
