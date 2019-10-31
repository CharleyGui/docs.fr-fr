---
title: ICorProfilerCallback9 ::D méthode ynamicMethodUnloaded
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 05a788179ff40a6889ed613b5f8659dd3f8e066f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196316"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="28b23-102">ICorProfilerCallback9 ::D méthode ynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="28b23-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="28b23-103">[Pris en charge dans les .NET Framework 4.7.2 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="28b23-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="28b23-104">Notifie le profileur chaque fois qu’une méthode dynamique est récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="28b23-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b23-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28b23-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28b23-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="28b23-106">Parameters</span></span>  
<span data-ttu-id="28b23-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="28b23-107">[in] `functionId`</span></span>  
<span data-ttu-id="28b23-108">Identificateur de la fonction en mémoire qui a été récupéré par le garbage collector et déchargée.</span><span class="sxs-lookup"><span data-stu-id="28b23-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>   

## <a name="requirements"></a><span data-ttu-id="28b23-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="28b23-109">Requirements</span></span>  
 <span data-ttu-id="28b23-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b23-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b23-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28b23-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28b23-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28b23-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28b23-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="28b23-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b23-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28b23-114">See also</span></span>

- [<span data-ttu-id="28b23-115">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="28b23-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="28b23-116">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="28b23-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="28b23-117">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="28b23-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="28b23-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="28b23-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
