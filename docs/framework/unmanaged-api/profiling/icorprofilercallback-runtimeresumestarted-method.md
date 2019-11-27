---
title: ICorProfilerCallback::RuntimeResumeStarted, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeResumeStarted method [.NET Framework profiling]
- RuntimeResumeStarted method [.NET Framework profiling]
ms.assetid: 5854bfb2-c568-4f19-904a-7c9d41e7b995
topic_type:
- apiref
ms.openlocfilehash: fe204bbe6154bf3d512a998818cf053d1e96ab3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433536"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="13770-102">ICorProfilerCallback::RuntimeResumeStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="13770-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="13770-103">Indique au profileur que le runtime reprend tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="13770-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13770-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13770-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="13770-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="13770-105">Requirements</span></span>  
 <span data-ttu-id="13770-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13770-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13770-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="13770-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13770-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13770-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13770-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13770-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13770-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13770-110">See also</span></span>

- [<span data-ttu-id="13770-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="13770-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="13770-112">RuntimeResumeFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="13770-112">RuntimeResumeFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)
