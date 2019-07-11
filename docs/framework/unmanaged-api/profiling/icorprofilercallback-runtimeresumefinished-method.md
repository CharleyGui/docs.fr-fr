---
title: ICorProfilerCallback::RuntimeResumeFinished, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 883e226042225b63097acf731b13abd69cc757ba
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750419"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="f9b23-102">ICorProfilerCallback::RuntimeResumeFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="f9b23-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>
<span data-ttu-id="f9b23-103">Notifie le profileur que le runtime a repris tous les threads d’exécution et a retourné un fonctionnement normal.</span><span class="sxs-lookup"><span data-stu-id="f9b23-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9b23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9b23-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f9b23-105">Notes</span><span class="sxs-lookup"><span data-stu-id="f9b23-105">Remarks</span></span>  
 <span data-ttu-id="f9b23-106">Le `RuntimeResumeFinished` n’est pas garanti que le rappel se produisent sur le même thread que le [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="f9b23-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="f9b23-107">Toutefois, il est garanti pour se produire sur le même thread que le [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) rappel.</span><span class="sxs-lookup"><span data-stu-id="f9b23-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9b23-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9b23-108">Requirements</span></span>  
 <span data-ttu-id="f9b23-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9b23-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9b23-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9b23-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9b23-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9b23-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9b23-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9b23-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9b23-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9b23-113">See also</span></span>

- [<span data-ttu-id="f9b23-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f9b23-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
