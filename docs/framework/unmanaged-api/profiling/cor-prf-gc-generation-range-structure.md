---
title: COR_PRF_GC_GENERATION_RANGE, structure
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: 0bdb8cd02e0beb69e3ec594b0aadd741a5f0d924
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428339"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="5d405-102">COR_PRF_GC_GENERATION_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="5d405-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="5d405-103">Décrit une plage (un bloc) de mémoire qui va faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="5d405-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d405-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5d405-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="5d405-105">Membres</span><span class="sxs-lookup"><span data-stu-id="5d405-105">Members</span></span>  
  
|<span data-ttu-id="5d405-106">Membre</span><span class="sxs-lookup"><span data-stu-id="5d405-106">Member</span></span>|<span data-ttu-id="5d405-107">Description</span><span class="sxs-lookup"><span data-stu-id="5d405-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="5d405-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span><span class="sxs-lookup"><span data-stu-id="5d405-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="5d405-109">The ID of an object that specifies the starting location of the block of memory.</span><span class="sxs-lookup"><span data-stu-id="5d405-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="5d405-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span><span class="sxs-lookup"><span data-stu-id="5d405-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="5d405-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span><span class="sxs-lookup"><span data-stu-id="5d405-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d405-112">Notes</span><span class="sxs-lookup"><span data-stu-id="5d405-112">Remarks</span></span>  
 <span data-ttu-id="5d405-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="5d405-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d405-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="5d405-114">Requirements</span></span>  
 <span data-ttu-id="5d405-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d405-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d405-116">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="5d405-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="5d405-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d405-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d405-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d405-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d405-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d405-119">See also</span></span>

- [<span data-ttu-id="5d405-120">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="5d405-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
