---
title: ICorProfilerCallback::ModuleLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadStarted
helpviewer_keywords:
- ModuleLoadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadStarted method [.NET Framework profiling]
ms.assetid: 9cd2fe75-408a-400f-a6b1-9979624a2fe2
topic_type:
- apiref
ms.openlocfilehash: 88da5a968bf224dc5b6f45ee5d1d2e75386086f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866154"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="c70da-102">ICorProfilerCallback::ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="c70da-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="c70da-103">Notifie le profileur qu’un module est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="c70da-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c70da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c70da-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c70da-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="c70da-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="c70da-106">dans ID du module en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="c70da-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c70da-107">Notes</span><span class="sxs-lookup"><span data-stu-id="c70da-107">Remarks</span></span>  
 <span data-ttu-id="c70da-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="c70da-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c70da-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c70da-109">Requirements</span></span>  
 <span data-ttu-id="c70da-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c70da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c70da-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c70da-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c70da-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c70da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c70da-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c70da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c70da-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c70da-114">See also</span></span>

- [<span data-ttu-id="c70da-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c70da-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
