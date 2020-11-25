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
ms.openlocfilehash: 0e6fe3430696c16405d4ae414436bb12882c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732346"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="8284e-102">ICorProfilerCallback9 ::D méthode ynamicMethodUnloaded</span><span class="sxs-lookup"><span data-stu-id="8284e-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="8284e-103">[Pris en charge dans les .NET Framework 4.7.2 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="8284e-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="8284e-104">Notifie le profileur chaque fois qu’une méthode dynamique est récupérée par le garbage collector et déchargée par la suite.</span><span class="sxs-lookup"><span data-stu-id="8284e-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8284e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8284e-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8284e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8284e-106">Parameters</span></span>  

<span data-ttu-id="8284e-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8284e-107">[in] `functionId`</span></span>  
<span data-ttu-id="8284e-108">Identificateur de la fonction en mémoire qui a été récupéré par le garbage collector et déchargée.</span><span class="sxs-lookup"><span data-stu-id="8284e-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="8284e-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8284e-109">Requirements</span></span>  

 <span data-ttu-id="8284e-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8284e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8284e-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8284e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8284e-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8284e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8284e-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8284e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8284e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8284e-114">See also</span></span>

- [<span data-ttu-id="8284e-115">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="8284e-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8284e-116">Méthode ICorProfilerCallback8. DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="8284e-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="8284e-117">ICorProfilerCallback9, interface</span><span class="sxs-lookup"><span data-stu-id="8284e-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="8284e-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="8284e-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
