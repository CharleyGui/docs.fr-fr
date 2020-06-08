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
ms.openlocfilehash: 91fb902aab678e29c6e74380e3576fa5c4ae62d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500889"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="e9759-102">COR_PRF_GC_GENERATION_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="e9759-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="e9759-103">Décrit une plage (un bloc) de mémoire qui va faire l'objet d'une récupération de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e9759-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9759-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9759-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="e9759-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e9759-105">Members</span></span>  
  
|<span data-ttu-id="e9759-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e9759-106">Member</span></span>|<span data-ttu-id="e9759-107">Description</span><span class="sxs-lookup"><span data-stu-id="e9759-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="e9759-108">Valeur de l’énumération [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) qui spécifie la génération à laquelle appartient le bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e9759-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="e9759-109">ID d’un objet qui spécifie l’emplacement de départ du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="e9759-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="e9759-110">Pointeur vers un entier qui spécifie la taille de la partie utilisée du bloc de mémoire (autrement dit, la quantité de mémoire utilisée dans le bloc).</span><span class="sxs-lookup"><span data-stu-id="e9759-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="e9759-111">Pointeur vers un entier qui spécifie la taille du bloc de mémoire (autrement dit, la quantité de mémoire réservée pour le bloc).</span><span class="sxs-lookup"><span data-stu-id="e9759-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9759-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="e9759-112">Remarks</span></span>  
 <span data-ttu-id="e9759-113">La `rangeLength` précision de la valeur est garantie uniquement si [ICorProfilerInfo2 :: GetGenerationBounds,](icorprofilerinfo2-getgenerationbounds-method.md) ou [ICorProfilerInfo2 :: GetObjectGeneration,](icorprofilerinfo2-getobjectgeneration-method.md), qui utilisent tous les deux la `COR_PRF_GC_GENERATION_RANGE` structure, est appelé à partir de la méthode [ICorProfilerCallback2 :: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) ou de la méthode [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e9759-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9759-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e9759-114">Requirements</span></span>  
 <span data-ttu-id="e9759-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9759-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9759-116">**En-tête :** CorProf. idl</span><span class="sxs-lookup"><span data-stu-id="e9759-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e9759-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9759-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9759-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9759-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9759-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9759-119">See also</span></span>

- [<span data-ttu-id="e9759-120">Structures de profilage</span><span class="sxs-lookup"><span data-stu-id="e9759-120">Profiling Structures</span></span>](profiling-structures.md)
