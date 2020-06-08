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
ms.openlocfilehash: b587f30a01623c6e9806bcd9d01058a0880be239
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499907"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="f49b7-102">ICorProfilerCallback::RootReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="f49b7-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="f49b7-103">Notifie le profileur des informations sur les références racines après garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f49b7-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f49b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f49b7-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f49b7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f49b7-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="f49b7-106">dans Nombre de références dans le `rootRefIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="f49b7-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="f49b7-107">dans Tableau d’ID d’objet qui référencent un objet statique ou un objet sur la pile.</span><span class="sxs-lookup"><span data-stu-id="f49b7-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f49b7-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="f49b7-108">Remarks</span></span>  
 <span data-ttu-id="f49b7-109">`RootReferences`Et [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) sont appelés pour avertir le profileur.</span><span class="sxs-lookup"><span data-stu-id="f49b7-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="f49b7-110">Les profileurs implémentent normalement l’un ou l’autre, mais pas les deux, car les informations transmises `RootReferences2` sont un sur-ensemble de qui est passé `RootReferences` .</span><span class="sxs-lookup"><span data-stu-id="f49b7-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="f49b7-111">Il est possible que le `rootRefIds` tableau contienne un objet null.</span><span class="sxs-lookup"><span data-stu-id="f49b7-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="f49b7-112">Par exemple, toutes les références d’objets déclarées sur la pile sont traitées comme des racines par le garbage collector et sont toujours signalées.</span><span class="sxs-lookup"><span data-stu-id="f49b7-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="f49b7-113">Les ID d’objet retournés par `RootReferences` ne sont pas valides pendant le rappel lui-même, car le garbage collection peut être en train de déplacer des objets d’anciennes adresses vers de nouvelles adresses.</span><span class="sxs-lookup"><span data-stu-id="f49b7-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="f49b7-114">Par conséquent, les profileurs ne doivent pas tenter d’inspecter les objets pendant un `RootReferences` appel.</span><span class="sxs-lookup"><span data-stu-id="f49b7-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="f49b7-115">Quand [ICorProfilerCallback2 :: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) est appelé, tous les objets ont été déplacés vers leurs nouveaux emplacements et peuvent être inspectés en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="f49b7-115">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49b7-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f49b7-116">Requirements</span></span>  
 <span data-ttu-id="f49b7-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f49b7-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49b7-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f49b7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f49b7-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f49b7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f49b7-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f49b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49b7-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f49b7-121">See also</span></span>

- [<span data-ttu-id="f49b7-122">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f49b7-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
