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
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136562"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="3113f-102">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="3113f-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="3113f-103">[Pris en charge dans les .NET Framework 4.7.2 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="3113f-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="3113f-104">Sous-classe de [ICorProfilerCallback8](icorprofilercallback8-interface.md) qui fournit une méthode de rappel utilisée par le Common Language Runtime pour informer le profileur qu’une méthode dynamique a été récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="3113f-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3113f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3113f-105">Methods</span></span>  
  
|<span data-ttu-id="3113f-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="3113f-106">Method</span></span>|<span data-ttu-id="3113f-107">Description</span><span class="sxs-lookup"><span data-stu-id="3113f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3113f-108">DynamicMethodUnloaded, méthode</span><span class="sxs-lookup"><span data-stu-id="3113f-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="3113f-109">Notifie le profileur qu’une méthode dynamique a été récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="3113f-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3113f-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="3113f-110">Requirements</span></span>  
 <span data-ttu-id="3113f-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3113f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3113f-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3113f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="3113f-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3113f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="3113f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3113f-114">See also</span></span>

- [<span data-ttu-id="3113f-115">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="3113f-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3113f-116">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="3113f-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="3113f-117">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="3113f-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="3113f-118">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="3113f-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
