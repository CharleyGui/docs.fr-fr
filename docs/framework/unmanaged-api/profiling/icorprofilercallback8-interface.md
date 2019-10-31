---
title: ICorProfilerCallback8, interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136451"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="c215a-102">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="c215a-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="c215a-103">[Pris en charge dans le .NET Framework 4,7 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="c215a-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="c215a-104">Sous-classe de [ICorProfilerCallback7](icorprofilercallback7-interface.md) qui fournit des méthodes de rappel utilisées par le Common Language Runtime pour notifier au profileur que la compilation JIT d’une méthode dynamique a démarré et se termine.</span><span class="sxs-lookup"><span data-stu-id="c215a-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="c215a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c215a-105">Methods</span></span>  
  
|<span data-ttu-id="c215a-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="c215a-106">Method</span></span>|<span data-ttu-id="c215a-107">Description</span><span class="sxs-lookup"><span data-stu-id="c215a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c215a-108">DynamicMethodJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="c215a-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="c215a-109">Notifie le profileur que la compilation JIT d’une méthode dynamique a démarré.</span><span class="sxs-lookup"><span data-stu-id="c215a-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="c215a-110">DynamicMethodJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="c215a-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="c215a-111">Notifie le profileur que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="c215a-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c215a-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="c215a-112">Requirements</span></span>  
 <span data-ttu-id="c215a-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c215a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c215a-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c215a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="c215a-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c215a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="c215a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c215a-116">See also</span></span>

- [<span data-ttu-id="c215a-117">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="c215a-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c215a-118">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="c215a-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
