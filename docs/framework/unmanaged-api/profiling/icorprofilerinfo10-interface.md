---
title: Interface ICorProfilerInfo10
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2bc716110c14972e5b2c32bceb3123b16e87c61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449843"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="e347c-102">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="e347c-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="e347c-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span><span class="sxs-lookup"><span data-stu-id="e347c-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="e347c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e347c-104">Methods</span></span>  

| <span data-ttu-id="e347c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e347c-105">Method</span></span>|<span data-ttu-id="e347c-106">Description</span><span class="sxs-lookup"><span data-stu-id="e347c-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="e347c-107">EnumerateObjectReferences Method</span><span class="sxs-lookup"><span data-stu-id="e347c-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="e347c-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span><span class="sxs-lookup"><span data-stu-id="e347c-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="e347c-109">IsFrozenObject Method</span><span class="sxs-lookup"><span data-stu-id="e347c-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="e347c-110">Given an ObjectID, determines whether the object is in a read-only segment.</span><span class="sxs-lookup"><span data-stu-id="e347c-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="e347c-111">GetLOHObjectSizeThreshold Method</span><span class="sxs-lookup"><span data-stu-id="e347c-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="e347c-112">Gets the value of the configured LOH threshold.</span><span class="sxs-lookup"><span data-stu-id="e347c-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="e347c-113">RequestReJITWithInliners Method</span><span class="sxs-lookup"><span data-stu-id="e347c-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="e347c-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span><span class="sxs-lookup"><span data-stu-id="e347c-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="e347c-115">SuspendRuntime Method</span><span class="sxs-lookup"><span data-stu-id="e347c-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="e347c-116">Suspends the runtime without performing a GC.</span><span class="sxs-lookup"><span data-stu-id="e347c-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="e347c-117">ResumeRuntime Method</span><span class="sxs-lookup"><span data-stu-id="e347c-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="e347c-118">Resumes the runtime without performing a GC.</span><span class="sxs-lookup"><span data-stu-id="e347c-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="e347c-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="e347c-119">Requirements</span></span>  
<span data-ttu-id="e347c-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="e347c-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="e347c-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e347c-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="e347c-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e347c-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="e347c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e347c-123">See also</span></span>

- [<span data-ttu-id="e347c-124">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="e347c-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
