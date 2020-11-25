---
title: ICorProfilerCallback::ExceptionCLRCatcherFound, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 894084978f976bcee71138d35534a80b5f9cda5f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699974"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="df98d-102">ICorProfilerCallback::ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="df98d-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>

<span data-ttu-id="df98d-103">Appelée lorsqu’un `catch` bloc pour une exception est trouvé à l’intérieur du Common Language Runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="df98d-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="df98d-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="df98d-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df98d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="df98d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="df98d-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df98d-106">Requirements</span></span>  

 <span data-ttu-id="df98d-107">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df98d-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df98d-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df98d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df98d-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df98d-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df98d-110">**Version de .NET Framework :** 1,0</span><span class="sxs-lookup"><span data-stu-id="df98d-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df98d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df98d-111">See also</span></span>

- [<span data-ttu-id="df98d-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="df98d-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="df98d-113">ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="df98d-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
