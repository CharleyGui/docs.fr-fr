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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175094"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="b4b93-102">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="b4b93-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="b4b93-103">[Soutenu dans le cadre .NET 4.7 et les versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="b4b93-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="b4b93-104">Une sous-classe [d’ICorProfilerCallback7](icorprofilercallback7-interface.md) qui fournit des méthodes de rappel utilisées par l’heure courante de l’exécution de la langue pour informer le profileur que la compilation JIT d’une méthode dynamique a commencé et terminé.</span><span class="sxs-lookup"><span data-stu-id="b4b93-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="b4b93-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b4b93-105">Methods</span></span>  
  
|<span data-ttu-id="b4b93-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="b4b93-106">Method</span></span>|<span data-ttu-id="b4b93-107">Description</span><span class="sxs-lookup"><span data-stu-id="b4b93-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4b93-108">DynamicMethodJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="b4b93-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="b4b93-109">Informe le profileur que la compilation JIT d’une méthode dynamique a commencé.</span><span class="sxs-lookup"><span data-stu-id="b4b93-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="b4b93-110">DynamicMethodJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="b4b93-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="b4b93-111">Informe le profileur que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="b4b93-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4b93-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b4b93-112">Requirements</span></span>  
 <span data-ttu-id="b4b93-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b93-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b93-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4b93-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="b4b93-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b93-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b4b93-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b4b93-116">See also</span></span>

- [<span data-ttu-id="b4b93-117">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="b4b93-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b4b93-118">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="b4b93-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
