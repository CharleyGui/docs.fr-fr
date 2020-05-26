---
title: IHostMalloc, interface
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: 8f4e1cd7586df7d8e2a577d26f06eaed6b2c8bb7
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804603"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="283a6-102">IHostMalloc, interface</span><span class="sxs-lookup"><span data-stu-id="283a6-102">IHostMalloc Interface</span></span>
<span data-ttu-id="283a6-103">Fournit des méthodes qui permettent au common language runtime (CLR) de demander des allocations affinées à partir du tas par le biais de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="283a6-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="283a6-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="283a6-104">Methods</span></span>  
  
|<span data-ttu-id="283a6-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="283a6-105">Method</span></span>|<span data-ttu-id="283a6-106">Description</span><span class="sxs-lookup"><span data-stu-id="283a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="283a6-107">Alloc, méthode</span><span class="sxs-lookup"><span data-stu-id="283a6-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="283a6-108">Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas.</span><span class="sxs-lookup"><span data-stu-id="283a6-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="283a6-109">DebugAlloc, méthode</span><span class="sxs-lookup"><span data-stu-id="283a6-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="283a6-110">Demande que l’hôte alloue la quantité de mémoire demandée à partir du tas et effectue également le suivi de l’emplacement où la mémoire a été allouée.</span><span class="sxs-lookup"><span data-stu-id="283a6-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="283a6-111">Free, méthode</span><span class="sxs-lookup"><span data-stu-id="283a6-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="283a6-112">Libère de la mémoire qui a été allouée à l’aide de la `Alloc` méthode.</span><span class="sxs-lookup"><span data-stu-id="283a6-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="283a6-113">Notes</span><span class="sxs-lookup"><span data-stu-id="283a6-113">Remarks</span></span>  
 <span data-ttu-id="283a6-114">Le CLR obtient un pointeur d’interface vers une `IHostMalloc` instance en appelant la méthode [IHostMemoryManager :: CreateMAlloc](ihostmemorymanager-createmalloc-method.md) .</span><span class="sxs-lookup"><span data-stu-id="283a6-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="283a6-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="283a6-115">Requirements</span></span>  
 <span data-ttu-id="283a6-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="283a6-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="283a6-117">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="283a6-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="283a6-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="283a6-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="283a6-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="283a6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="283a6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="283a6-120">See also</span></span>

- [<span data-ttu-id="283a6-121">IHostMemoryManager, interface</span><span class="sxs-lookup"><span data-stu-id="283a6-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="283a6-122">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="283a6-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
