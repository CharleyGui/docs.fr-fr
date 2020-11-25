---
title: ICorProfilerCallback9, interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 23b91a2a58c6e76b31b94e0fa3661dfbc8e18e33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712766"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="a5747-102">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="a5747-102">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="a5747-103">[Pris en charge dans les .NET Framework 4.7.2 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="a5747-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="a5747-104">Sous-classe de [ICorProfilerCallback8](icorprofilercallback8-interface.md) qui fournit une méthode de rappel utilisée par le Common Language Runtime pour informer le profileur qu’une méthode dynamique a été récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="a5747-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5747-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="a5747-105">Methods</span></span>  
  
|<span data-ttu-id="a5747-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="a5747-106">Method</span></span>|<span data-ttu-id="a5747-107">Description</span><span class="sxs-lookup"><span data-stu-id="a5747-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5747-108">DynamicMethodUnloaded, méthode</span><span class="sxs-lookup"><span data-stu-id="a5747-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="a5747-109">Notifie le profileur qu’une méthode dynamique a été récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="a5747-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5747-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5747-110">Requirements</span></span>  

 <span data-ttu-id="a5747-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5747-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5747-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5747-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="a5747-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a5747-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="a5747-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5747-114">See also</span></span>

- [<span data-ttu-id="a5747-115">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="a5747-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="a5747-116">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="a5747-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="a5747-117">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="a5747-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="a5747-118">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="a5747-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
