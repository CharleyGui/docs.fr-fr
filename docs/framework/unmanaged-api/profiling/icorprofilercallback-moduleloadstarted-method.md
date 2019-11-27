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
ms.openlocfilehash: 55927167f8b61ade4ef479b30b85ad8d82be8025
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445927"
---
# <a name="icorprofilercallbackmoduleloadstarted-method"></a><span data-ttu-id="42062-102">ICorProfilerCallback::ModuleLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="42062-102">ICorProfilerCallback::ModuleLoadStarted Method</span></span>
<span data-ttu-id="42062-103">Notifie le profileur qu’un module est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="42062-103">Notifies the profiler that a module is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42062-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42062-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadStarted(  
    [in] ModuleID moduleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42062-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42062-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="42062-106">dans ID du module en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="42062-106">[in] The ID of the module that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42062-107">Notes</span><span class="sxs-lookup"><span data-stu-id="42062-107">Remarks</span></span>  
 <span data-ttu-id="42062-108">La valeur de `moduleId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="42062-108">The value of `moduleId` is not valid for an information request until the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42062-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="42062-109">Requirements</span></span>  
 <span data-ttu-id="42062-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42062-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42062-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="42062-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="42062-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42062-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42062-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42062-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42062-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42062-114">See also</span></span>

- [<span data-ttu-id="42062-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="42062-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
