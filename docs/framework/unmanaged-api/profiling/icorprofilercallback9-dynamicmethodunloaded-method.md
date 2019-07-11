---
title: ICorProfilerCallback9::DynamicMethodUnloaded (méthode)
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 680bd351a64632e67432ee03352ee7caa8f4b2d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780389"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="8ad69-102">ICorProfilerCallback9::DynamicMethodUnloaded (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ad69-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="8ad69-103">[Pris en charge dans le .NET Framework 4.7.2 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="8ad69-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="8ad69-104">Notifie le profileur chaque fois qu’une méthode dynamique est garbage collectées et déchargé par la suite.</span><span class="sxs-lookup"><span data-stu-id="8ad69-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad69-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8ad69-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad69-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8ad69-106">Parameters</span></span>  
<span data-ttu-id="8ad69-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8ad69-107">[in] `functionId`</span></span>  
<span data-ttu-id="8ad69-108">L’identificateur de la fonction en mémoire qui a été garbage collectées et déchargé.</span><span class="sxs-lookup"><span data-stu-id="8ad69-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="8ad69-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ad69-109">Requirements</span></span>  
 <span data-ttu-id="8ad69-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad69-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad69-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ad69-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ad69-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ad69-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ad69-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad69-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad69-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad69-114">See also</span></span>

- [<span data-ttu-id="8ad69-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ad69-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8ad69-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished (méthode)</span><span class="sxs-lookup"><span data-stu-id="8ad69-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="8ad69-117">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="8ad69-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="8ad69-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="8ad69-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
