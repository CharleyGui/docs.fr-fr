---
title: ICorProfilerCallback9::DynamicMethodUnloaded Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0eb38c83e9ab706c96bdef971f0bf17cc096822b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177031"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="de7c3-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span><span class="sxs-lookup"><span data-stu-id="de7c3-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="de7c3-103">[Soutenu dans le cadre .NET 4.7.2 et les versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="de7c3-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="de7c3-104">Informe le profileur chaque fois qu’une méthode dynamique est recueillie par ordures et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="de7c3-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de7c3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de7c3-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de7c3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="de7c3-106">Parameters</span></span>  
<span data-ttu-id="de7c3-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="de7c3-107">[in] `functionId`</span></span>  
<span data-ttu-id="de7c3-108">L’identifiant de la fonction mémoire qui a été recueillie et déchargée.</span><span class="sxs-lookup"><span data-stu-id="de7c3-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="de7c3-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="de7c3-109">Requirements</span></span>  
 <span data-ttu-id="de7c3-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de7c3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de7c3-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="de7c3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="de7c3-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de7c3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de7c3-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="de7c3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de7c3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de7c3-114">See also</span></span>

- [<span data-ttu-id="de7c3-115">ICorProfilerCallback8.DynamicMethodJITCompilationLa méthode</span><span class="sxs-lookup"><span data-stu-id="de7c3-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="de7c3-116">ICorProfilerCallback8.DynamicMethodJITCompilationLa méthode définie</span><span class="sxs-lookup"><span data-stu-id="de7c3-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="de7c3-117">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="de7c3-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="de7c3-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="de7c3-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
