---
title: ICorProfilerCallback6, interface
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 0009d935e2e3b2abf590aca270113717ceb7e2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127481"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="9016c-102">ICorProfilerCallback6, interface</span><span class="sxs-lookup"><span data-stu-id="9016c-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="9016c-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="9016c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="9016c-104">Sous-classe de [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) qui fournit une méthode de rappel que le Common Language Runtime utilise pour notifier à un profileur qu’un assembly est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="9016c-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9016c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9016c-105">Methods</span></span>  
  
|<span data-ttu-id="9016c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="9016c-106">Method</span></span>|<span data-ttu-id="9016c-107">Description</span><span class="sxs-lookup"><span data-stu-id="9016c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9016c-108">GetAssemblyReferences, méthode</span><span class="sxs-lookup"><span data-stu-id="9016c-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="9016c-109">Notifie le profileur qu'un assembly en est au tout début du chargement, quand le CLR (Common Langage Runtime) effectue un parcours de fermeture de références d'assembly.</span><span class="sxs-lookup"><span data-stu-id="9016c-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9016c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="9016c-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9016c-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="9016c-111">Requirements</span></span>  
 <span data-ttu-id="9016c-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9016c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9016c-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9016c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9016c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9016c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9016c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9016c-115">See also</span></span>

- [<span data-ttu-id="9016c-116">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="9016c-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
