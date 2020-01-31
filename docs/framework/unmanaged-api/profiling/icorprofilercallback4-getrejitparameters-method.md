---
title: ICorProfilerCallback4::GetReJITParameters, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 858d65783515a89a434cf719ef9d5a999643094c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865309"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="b6901-102">ICorProfilerCallback4::GetReJITParameters, méthode</span><span class="sxs-lookup"><span data-stu-id="b6901-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>
<span data-ttu-id="b6901-103">Permet au profileur de code de définir d’autres indicateurs de génération de code pour un nouveau corps de méthode recompilée.</span><span class="sxs-lookup"><span data-stu-id="b6901-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6901-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6901-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6901-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="b6901-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="b6901-106">dans Module qui contient la méthode pour laquelle le CLR a besoin de paramètres de recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="b6901-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="b6901-107">dans `MethodDef` de la méthode pour laquelle le CLR a besoin de paramètres de recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="b6901-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="b6901-108">dans Pointeur vers une interface [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) que le profileur peut utiliser pour fournir des informations de recompilation JIT pour la méthode en cours de recompilation.</span><span class="sxs-lookup"><span data-stu-id="b6901-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6901-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b6901-109">Remarks</span></span>  
 <span data-ttu-id="b6901-110">Le CLR émet un rappel de `GetReJITParameters` afin que le profileur puisse spécifier les paramètres pour la recompilation d’une méthode donnée.</span><span class="sxs-lookup"><span data-stu-id="b6901-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="b6901-111">Le rappel `GetReJITParameters` est émis une seule fois par fonction ; les paramètres fournis par le profileur s’appliquent à toutes les instances de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="b6901-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6901-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b6901-112">Requirements</span></span>  
 <span data-ttu-id="b6901-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6901-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6901-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6901-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6901-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6901-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6901-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6901-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6901-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6901-117">See also</span></span>

- [<span data-ttu-id="b6901-118">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b6901-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b6901-119">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="b6901-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="b6901-120">JITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="b6901-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="b6901-121">ReJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="b6901-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
