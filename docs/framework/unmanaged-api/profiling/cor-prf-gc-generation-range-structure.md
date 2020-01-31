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
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867205"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="d50d9-102">COR_PRF_GC_GENERATION_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="d50d9-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="d50d9-103">Décrit une plage (un bloc) de mémoire qui va faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d50d9-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d50d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d50d9-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="d50d9-105">Members</span><span class="sxs-lookup"><span data-stu-id="d50d9-105">Members</span></span>  
  
|<span data-ttu-id="d50d9-106">Member</span><span class="sxs-lookup"><span data-stu-id="d50d9-106">Member</span></span>|<span data-ttu-id="d50d9-107">Description</span><span class="sxs-lookup"><span data-stu-id="d50d9-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="d50d9-108">Valeur de l’énumération [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) qui spécifie la génération à laquelle appartient le bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d50d9-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="d50d9-109">ID d’un objet qui spécifie l’emplacement de départ du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="d50d9-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="d50d9-110">Pointeur vers un entier qui spécifie la taille de la partie utilisée du bloc de mémoire (autrement dit, la quantité de mémoire utilisée dans le bloc).</span><span class="sxs-lookup"><span data-stu-id="d50d9-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="d50d9-111">Pointeur vers un entier qui spécifie la taille du bloc de mémoire (autrement dit, la quantité de mémoire réservée pour le bloc).</span><span class="sxs-lookup"><span data-stu-id="d50d9-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d50d9-112">Notes</span><span class="sxs-lookup"><span data-stu-id="d50d9-112">Remarks</span></span>  
 <span data-ttu-id="d50d9-113">La valeur `rangeLength` est garantie comme étant exacte uniquement si [ICorProfilerInfo2 :: GetGenerationBounds,](icorprofilerinfo2-getgenerationbounds-method.md) ou [Icorprofilerinfo2 :: GetObjectGeneration,](icorprofilerinfo2-getobjectgeneration-method.md), qui utilisent tous les deux la structure `COR_PRF_GC_GENERATION_RANGE`, est appelé à partir de la méthode [ICorProfilerCallback2 :: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) ou de la méthode [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d50d9-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d50d9-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d50d9-114">Requirements</span></span>  
 <span data-ttu-id="d50d9-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d50d9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d50d9-116">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="d50d9-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d50d9-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d50d9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d50d9-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d50d9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50d9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d50d9-119">See also</span></span>

- [<span data-ttu-id="d50d9-120">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="d50d9-120">Profiling Structures</span></span>](profiling-structures.md)
