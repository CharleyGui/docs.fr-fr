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
ms.openlocfilehash: 08e76e295e30ede48733ab35870ec965eb157f60
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499868"
---
# <a name="icorprofilercallbackruntimeresumestarted-method"></a><span data-ttu-id="46fef-102">ICorProfilerCallback::RuntimeResumeStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="46fef-102">ICorProfilerCallback::RuntimeResumeStarted Method</span></span>
<span data-ttu-id="46fef-103">Indique au profileur que le runtime reprend tous les threads d’exécution.</span><span class="sxs-lookup"><span data-stu-id="46fef-103">Notifies the profiler that the runtime is resuming all run-time threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46fef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46fef-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="46fef-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="46fef-105">Requirements</span></span>  
 <span data-ttu-id="46fef-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46fef-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46fef-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46fef-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46fef-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46fef-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46fef-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46fef-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46fef-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46fef-110">See also</span></span>

- [<span data-ttu-id="46fef-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="46fef-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="46fef-112">RuntimeResumeFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="46fef-112">RuntimeResumeFinished Method</span></span>](icorprofilercallback-runtimeresumefinished-method.md)
