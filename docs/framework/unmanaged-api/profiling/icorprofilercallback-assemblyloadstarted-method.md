---
title: ICorProfilerCallback::AssemblyLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: b83be5e79c533e7e5a2468a12a0793d300700428
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866636"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="2ed13-102">ICorProfilerCallback::AssemblyLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="2ed13-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>
<span data-ttu-id="2ed13-103">Notifie le profileur qu’un assembly est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="2ed13-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed13-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ed13-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ed13-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="2ed13-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="2ed13-106">\[in] identifie l’assembly en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="2ed13-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="2ed13-107">Notes</span><span class="sxs-lookup"><span data-stu-id="2ed13-107">Remarks</span></span>  
 <span data-ttu-id="2ed13-108">La valeur de `assemblyId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: AssemblyLoadFinished,](icorprofilercallback-assemblyloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="2ed13-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ed13-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2ed13-109">Requirements</span></span>  
 <span data-ttu-id="2ed13-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ed13-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ed13-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2ed13-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2ed13-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ed13-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ed13-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ed13-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed13-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ed13-114">See also</span></span>

- [<span data-ttu-id="2ed13-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="2ed13-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
