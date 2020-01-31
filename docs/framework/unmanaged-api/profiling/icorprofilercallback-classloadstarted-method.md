---
title: ICorProfilerCallback::ClassLoadStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 5b465216da39e8cf207f0614519720453c384ae9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866583"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="e4cee-102">ICorProfilerCallback::ClassLoadStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="e4cee-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="e4cee-103">Notifie le profileur qu’une classe est en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="e4cee-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4cee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4cee-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4cee-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="e4cee-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="e4cee-106">\[in] identifie la classe en cours de chargement.</span><span class="sxs-lookup"><span data-stu-id="e4cee-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4cee-107">Notes</span><span class="sxs-lookup"><span data-stu-id="e4cee-107">Remarks</span></span>  
 <span data-ttu-id="e4cee-108">La valeur de `classId` n’est pas valide pour une demande d’informations tant que la méthode [ICorProfilerCallback :: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) n’est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="e4cee-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4cee-109">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="e4cee-109">Requirements</span></span>  
 <span data-ttu-id="e4cee-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4cee-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4cee-111">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4cee-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4cee-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4cee-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4cee-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4cee-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cee-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4cee-114">See also</span></span>

- [<span data-ttu-id="e4cee-115">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e4cee-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
