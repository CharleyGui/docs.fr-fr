---
title: ICorProfilerCallback::RootReferences, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 948628f469eecabfbbe792dcc3edf2e1204ffc36
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865959"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="6d2a3-102">ICorProfilerCallback::RootReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="6d2a3-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="6d2a3-103">Notifie le profileur des informations sur les références racines après garbage collection.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d2a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d2a3-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d2a3-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="6d2a3-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="6d2a3-106">dans Nombre de références dans le tableau de `rootRefIds`.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="6d2a3-107">dans Tableau d’ID d’objet qui référencent un objet statique ou un objet sur la pile.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d2a3-108">Notes</span><span class="sxs-lookup"><span data-stu-id="6d2a3-108">Remarks</span></span>  
 <span data-ttu-id="6d2a3-109">`RootReferences` et [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) sont appelés pour avertir le profileur.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="6d2a3-110">Les profileurs implémentent normalement l’un ou l’autre, mais pas les deux à la fois, car les informations transmises `RootReferences2` sont un sur-ensemble de celles passées dans `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="6d2a3-111">Il est possible que le tableau `rootRefIds` contienne un objet null.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="6d2a3-112">Par exemple, toutes les références d’objets déclarées sur la pile sont traitées comme des racines par le garbage collector et sont toujours signalées.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="6d2a3-113">Les ID d’objet retournés par `RootReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets d’anciennes adresses vers de nouvelles adresses.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="6d2a3-114">Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un appel de `RootReferences`.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="6d2a3-115">Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="6d2a3-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d2a3-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="6d2a3-116">Requirements</span></span>  
 <span data-ttu-id="6d2a3-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d2a3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d2a3-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6d2a3-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6d2a3-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d2a3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d2a3-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d2a3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d2a3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d2a3-121">See also</span></span>

- [<span data-ttu-id="6d2a3-122">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="6d2a3-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
