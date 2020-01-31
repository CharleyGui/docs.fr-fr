---
title: ICorProfilerCallback2::GarbageCollectionStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
ms.openlocfilehash: c90c790c519cc0c422657e6e2d8040a365fbf48c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865777"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="f76f1-102">ICorProfilerCallback2::GarbageCollectionStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="f76f1-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="f76f1-103">Notifie le profileur de code que garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="f76f1-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f76f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f76f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f76f1-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f76f1-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="f76f1-106">dans Nombre total d’entrées dans le tableau de `generationCollected`.</span><span class="sxs-lookup"><span data-stu-id="f76f1-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="f76f1-107">dans Tableau de valeurs booléennes, qui sont `true` si la génération qui correspond à l’index de tableau est collectée par ce garbage collection ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="f76f1-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="f76f1-108">Le tableau est indexé par une valeur de l’énumération [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) , qui indique la génération.</span><span class="sxs-lookup"><span data-stu-id="f76f1-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="f76f1-109">dans Valeur de l’énumération [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) qui indique la raison pour laquelle l’garbage collection a été induite.</span><span class="sxs-lookup"><span data-stu-id="f76f1-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f76f1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="f76f1-110">Remarks</span></span>  
 <span data-ttu-id="f76f1-111">Tous les rappels relatifs à ce garbage collection se produisent entre le rappel `GarbageCollectionStarted` et le rappel [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) correspondant.</span><span class="sxs-lookup"><span data-stu-id="f76f1-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="f76f1-112">Ces rappels n’ont pas besoin de se produire sur le même thread.</span><span class="sxs-lookup"><span data-stu-id="f76f1-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="f76f1-113">Le profileur peut inspecter en toute sécurité les objets dans leurs emplacements d’origine pendant le rappel de `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="f76f1-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="f76f1-114">Le garbage collector commence à déplacer des objets après le retour de `GarbageCollectionStarted`.</span><span class="sxs-lookup"><span data-stu-id="f76f1-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="f76f1-115">Une fois que le profileur a retourné à partir de ce rappel, le profileur doit considérer tous les ID d’objet comme non valides jusqu’à ce qu’il reçoive un rappel `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="f76f1-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f76f1-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f76f1-116">Requirements</span></span>  
 <span data-ttu-id="f76f1-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f76f1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f76f1-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f76f1-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f76f1-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f76f1-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f76f1-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f76f1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f76f1-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f76f1-121">See also</span></span>

- [<span data-ttu-id="f76f1-122">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f76f1-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f76f1-123">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="f76f1-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
