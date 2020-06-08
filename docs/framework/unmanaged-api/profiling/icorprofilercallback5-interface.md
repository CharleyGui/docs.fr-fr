---
title: ICorProfilerCallback5, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499205"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="4439e-102">ICorProfilerCallback5, interface</span><span class="sxs-lookup"><span data-stu-id="4439e-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="4439e-103">Complète les informations pour aider un profileur à identifier la fermeture complète d’objets actifs, lorsqu’il est utilisé avec la méthode [ICorProfilerCallback :: RootReferences](icorprofilercallback-rootreferences-method.md) ou [ICorProfilerCallback2 :: RootReferences2](icorprofilercallback2-rootreferences2-method.md) avec les méthodes [ICorProfilerCallback :: ObjectReferences](icorprofilercallback-objectreferences-method.md) et [conditionalweaktableelementreferences,](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4439e-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="4439e-104">`ICorProfilerCallback5` doit être implémentée par un profileur de mémoire managée pour s'abonner aux notifications relatives aux handles dépendants.</span><span class="sxs-lookup"><span data-stu-id="4439e-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4439e-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="4439e-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4439e-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4439e-106">Methods</span></span>  
  
|<span data-ttu-id="4439e-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="4439e-107">Method</span></span>|<span data-ttu-id="4439e-108">Description</span><span class="sxs-lookup"><span data-stu-id="4439e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4439e-109">ConditionalWeakTableElementReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="4439e-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="4439e-110">Identifie la fermeture transitive des objets référencés par ces racines via les références des champs des membres directs et via les dépendances de `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="4439e-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4439e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4439e-111">Requirements</span></span>  
 <span data-ttu-id="4439e-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4439e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4439e-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4439e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4439e-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4439e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4439e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4439e-115">See also</span></span>

- [<span data-ttu-id="4439e-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="4439e-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4439e-117">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="4439e-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
