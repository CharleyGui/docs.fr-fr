---
title: ICorProfilerInfo::SetFunctionIDMapper, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 4ba3c378b93e3ae1ef288c0edabfacfcfd7070d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438679"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a><span data-ttu-id="27323-102">ICorProfilerInfo::SetFunctionIDMapper, méthode</span><span class="sxs-lookup"><span data-stu-id="27323-102">ICorProfilerInfo::SetFunctionIDMapper Method</span></span>
<span data-ttu-id="27323-103">Spécifie la fonction implémentée par le profileur qui sera appelée pour mapper des valeurs `FunctionID` sur d'autres valeurs, qui sont passées aux raccordements d'entrée/sortie de fonction du profileur.</span><span class="sxs-lookup"><span data-stu-id="27323-103">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27323-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27323-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27323-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="27323-105">Parameters</span></span>  
 `pFunc`  
 <span data-ttu-id="27323-106">dans Pointeur vers l’implémentation de [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) qui sera appelée pour mapper les valeurs de `FunctionID` à leurs autres valeurs.</span><span class="sxs-lookup"><span data-stu-id="27323-106">[in] A pointer to the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27323-107">Notes</span><span class="sxs-lookup"><span data-stu-id="27323-107">Remarks</span></span>  
 <span data-ttu-id="27323-108">Les alternatives pour les valeurs de `FunctionID` seront passées aux raccordements d’entrée/sortie de fonction du profileur ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)et [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) qui sont spécifiés par la méthode [ICorProfilerInfo2 :: SetEnterLeaveFunctionHooks2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27323-108">The alternatives for the `FunctionID` values will be passed to the profiler's function entry/exit hooks ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)) that are specified by the [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) method.</span></span>  
  
 <span data-ttu-id="27323-109">La `FunctionIDMapper` ne peut être définie qu’une seule fois et il est recommandé de la définir dans le rappel [ICorProfilerCallback :: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27323-109">The `FunctionIDMapper` can be set only once and it is recommended that you set it in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27323-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="27323-110">Requirements</span></span>  
 <span data-ttu-id="27323-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27323-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27323-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27323-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27323-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27323-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27323-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27323-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27323-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="27323-115">See also</span></span>

- [<span data-ttu-id="27323-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="27323-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
