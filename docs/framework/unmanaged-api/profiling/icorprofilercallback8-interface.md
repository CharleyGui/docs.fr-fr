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
ms.openlocfilehash: 22a133d02bb69026190428905379323362943d40
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732383"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="868cd-102">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="868cd-102">ICorProfilerCallback8 Interface</span></span>

<span data-ttu-id="868cd-103">[Pris en charge dans le .NET Framework 4,7 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="868cd-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="868cd-104">Sous-classe de [ICorProfilerCallback7](icorprofilercallback7-interface.md) qui fournit des méthodes de rappel utilisées par le Common Language Runtime pour notifier au profileur que la compilation JIT d’une méthode dynamique a démarré et se termine.</span><span class="sxs-lookup"><span data-stu-id="868cd-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="868cd-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="868cd-105">Methods</span></span>  
  
|<span data-ttu-id="868cd-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="868cd-106">Method</span></span>|<span data-ttu-id="868cd-107">Description</span><span class="sxs-lookup"><span data-stu-id="868cd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="868cd-108">DynamicMethodJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="868cd-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="868cd-109">Notifie le profileur que la compilation JIT d’une méthode dynamique a démarré.</span><span class="sxs-lookup"><span data-stu-id="868cd-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="868cd-110">DynamicMethodJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="868cd-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="868cd-111">Notifie le profileur que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="868cd-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="868cd-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="868cd-112">Requirements</span></span>  

 <span data-ttu-id="868cd-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="868cd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="868cd-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="868cd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="868cd-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="868cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="868cd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="868cd-116">See also</span></span>

- [<span data-ttu-id="868cd-117">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="868cd-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="868cd-118">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="868cd-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
