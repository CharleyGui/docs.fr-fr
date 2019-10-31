---
title: COR_GC_THREAD_STATS, structure
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136988"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="8d89f-102">COR_GC_THREAD_STATS, structure</span><span class="sxs-lookup"><span data-stu-id="8d89f-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="8d89f-103">Contains per-thread statistics pertaining to garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8d89f-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d89f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d89f-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="8d89f-105">Membres</span><span class="sxs-lookup"><span data-stu-id="8d89f-105">Members</span></span>  
  
|<span data-ttu-id="8d89f-106">Membre</span><span class="sxs-lookup"><span data-stu-id="8d89f-106">Member</span></span>|<span data-ttu-id="8d89f-107">Description</span><span class="sxs-lookup"><span data-stu-id="8d89f-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="8d89f-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span><span class="sxs-lookup"><span data-stu-id="8d89f-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="8d89f-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span><span class="sxs-lookup"><span data-stu-id="8d89f-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="8d89f-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8d89f-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d89f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="8d89f-111">Remarks</span></span>  
 <span data-ttu-id="8d89f-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="8d89f-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d89f-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="8d89f-113">Requirements</span></span>  
 <span data-ttu-id="8d89f-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d89f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d89f-115">**Header:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="8d89f-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="8d89f-116">**Library:** Included as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d89f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d89f-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d89f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d89f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d89f-118">See also</span></span>

- [<span data-ttu-id="8d89f-119">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="8d89f-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="8d89f-120">IHostTask, interface</span><span class="sxs-lookup"><span data-stu-id="8d89f-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
