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
ms.openlocfilehash: 2391ad854b17ec117940a3d3568c40d6cf7f4725
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498971"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="3a134-102">ICorProfilerCallback9 ::D méthode ynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="3a134-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>
<span data-ttu-id="3a134-103">[Pris en charge dans les .NET Framework 4.7.2 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="3a134-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="3a134-104">Notifie le profileur chaque fois qu’une méthode dynamique est récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="3a134-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a134-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a134-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a134-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a134-106">Parameters</span></span>  
<span data-ttu-id="3a134-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="3a134-107">[in] `functionId`</span></span>  
<span data-ttu-id="3a134-108">Identificateur de la fonction en mémoire qui a été récupéré par le garbage collector et déchargée.</span><span class="sxs-lookup"><span data-stu-id="3a134-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a134-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3a134-109">Requirements</span></span>  
 <span data-ttu-id="3a134-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a134-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a134-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a134-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a134-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a134-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a134-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3a134-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a134-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a134-114">See also</span></span>

- [<span data-ttu-id="3a134-115">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="3a134-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="3a134-116">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="3a134-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="3a134-117">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="3a134-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="3a134-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="3a134-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
