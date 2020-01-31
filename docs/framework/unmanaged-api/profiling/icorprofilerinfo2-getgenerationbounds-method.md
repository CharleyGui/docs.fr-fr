---
title: ICorProfilerInfo2::GetGenerationBounds, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
ms.openlocfilehash: 3cdc185408576f5679daacef4dde438d66e490ff
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862748"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="6edce-102">ICorProfilerInfo2::GetGenerationBounds, méthode</span><span class="sxs-lookup"><span data-stu-id="6edce-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="6edce-103">Obtient les régions de la mémoire, qui sont des segments du tas, composant les différentes générations de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6edce-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6edce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6edce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6edce-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6edce-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="6edce-106">[in] Nombre d'éléments alloués par l'appelant pour le tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="6edce-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="6edce-107">[out] Pointeur vers un entier qui spécifie le nombre total de plages, dont une partie ou la totalité sera retournée dans le tableau `ranges`.</span><span class="sxs-lookup"><span data-stu-id="6edce-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="6edce-108">à Tableau de structures [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , qui décrivent chacune une plage (autrement dit, un bloc) de mémoire dans la génération qui est en cours d’garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6edce-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6edce-109">Notes</span><span class="sxs-lookup"><span data-stu-id="6edce-109">Remarks</span></span>  
 <span data-ttu-id="6edce-110">La méthode `GetGenerationBounds` peut être appelée à partir de tout rappel de profileur, à condition que le garbage collection ne soit pas en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="6edce-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="6edce-111">La plupart des décalages de générations ont lieu pendant les opérations de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6edce-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="6edce-112">Les générations peuvent devenir plus volumineuses entre les collections, mais elles ne se déplacent généralement pas.</span><span class="sxs-lookup"><span data-stu-id="6edce-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="6edce-113">Par conséquent, les endroits les plus intéressants pour appeler `GetGenerationBounds` sont dans `ICorProfilerCallback2::GarbageCollectionStarted` et `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="6edce-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="6edce-114">Pendant le démarrage du programme, certains objets sont alloués par le Common Language Runtime (CLR) lui-même, en général dans les générations 3 et 0.</span><span class="sxs-lookup"><span data-stu-id="6edce-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="6edce-115">Ainsi, quand le code managé commence à s'exécuter, ces générations contiennent déjà des objets.</span><span class="sxs-lookup"><span data-stu-id="6edce-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="6edce-116">Normalement, les générations 1 et 2 sont vides, à l'exception des objets factices qui sont générés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6edce-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="6edce-117">(La taille des objets factices est de 12 octets dans les implémentations 32 bits du CLR ; la taille est supérieure dans les implémentations de 64 bits.) Vous pouvez également voir les plages de génération 2 qui se trouvent dans les modules produits par le générateur d’images natives (NGen. exe).</span><span class="sxs-lookup"><span data-stu-id="6edce-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="6edce-118">Dans ce cas, les objets de la génération 2 sont des *objets figés*qui sont alloués quand Ngen. exe s’exécute plutôt que par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="6edce-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="6edce-119">Cette fonction utilise des mémoires tampons allouées par l'appelant.</span><span class="sxs-lookup"><span data-stu-id="6edce-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6edce-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6edce-120">Requirements</span></span>  
 <span data-ttu-id="6edce-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6edce-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6edce-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6edce-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6edce-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6edce-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6edce-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6edce-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6edce-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6edce-125">See also</span></span>

- [<span data-ttu-id="6edce-126">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="6edce-126">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="6edce-127">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="6edce-127">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="6edce-128">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="6edce-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6edce-129">Profilage</span><span class="sxs-lookup"><span data-stu-id="6edce-129">Profiling</span></span>](index.md)
