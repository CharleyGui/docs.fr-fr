---
title: ICorProfilerInfo4::InitializeCurrentThread, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868432"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="93bd9-102">ICorProfilerInfo4::InitializeCurrentThread, méthode</span><span class="sxs-lookup"><span data-stu-id="93bd9-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="93bd9-103">Initialise le thread actuel avant les appels d’API du profileur suivants sur le même thread, afin que l’interblocage puisse être évité.</span><span class="sxs-lookup"><span data-stu-id="93bd9-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93bd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93bd9-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="93bd9-105">Notes</span><span class="sxs-lookup"><span data-stu-id="93bd9-105">Remarks</span></span>  
 <span data-ttu-id="93bd9-106">Nous vous recommandons d’appeler `InitializeCurrentThread` sur tout thread qui appellera une API de profileur alors qu’il y a des threads suspendus.</span><span class="sxs-lookup"><span data-stu-id="93bd9-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="93bd9-107">Cette méthode est généralement utilisée par les profileurs d’échantillonnage qui créent leur propre thread pour appeler la méthode [ICorProfilerInfo2 ::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) pour effectuer des parcours de pile pendant que le thread cible est suspendu.</span><span class="sxs-lookup"><span data-stu-id="93bd9-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="93bd9-108">En appelant `InitializeCurrentThread` une fois que le profileur a créé le thread d’échantillonnage pour la première fois, les profileurs peuvent garantir que l’initialisation différée par thread que le CLR effectue normalement pendant le premier appel à `DoStackSnapshot` peut désormais se produire en toute sécurité quand aucun autre thread n’est suspendu.</span><span class="sxs-lookup"><span data-stu-id="93bd9-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93bd9-109">`InitializeCurrentThread` effectue l’initialisation à l’avance pour terminer les tâches qui prennent des verrous et peut se bloquer.</span><span class="sxs-lookup"><span data-stu-id="93bd9-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="93bd9-110">Appelez `InitializeCurrentThread` uniquement lorsqu’il n’y a pas de threads suspendus.</span><span class="sxs-lookup"><span data-stu-id="93bd9-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93bd9-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="93bd9-111">Requirements</span></span>  
 <span data-ttu-id="93bd9-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93bd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93bd9-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="93bd9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="93bd9-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93bd9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93bd9-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93bd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93bd9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93bd9-116">See also</span></span>

- [<span data-ttu-id="93bd9-117">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="93bd9-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="93bd9-118">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="93bd9-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="93bd9-119">Profilage</span><span class="sxs-lookup"><span data-stu-id="93bd9-119">Profiling</span></span>](index.md)
