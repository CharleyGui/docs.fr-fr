---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: f14dff33217656c35379a214f007ccb3642ef4b1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866453"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="75b66-102">ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="75b66-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="75b66-103">Appelée lorsqu’un bloc `catch` pour une exception est exécuté à l’intérieur du common language runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="75b66-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="75b66-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75b66-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b66-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75b66-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="75b66-106">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="75b66-106">Requirements</span></span>  
 <span data-ttu-id="75b66-107">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75b66-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75b66-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75b66-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75b66-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75b66-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75b66-110">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="75b66-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b66-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75b66-111">See also</span></span>

- [<span data-ttu-id="75b66-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="75b66-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="75b66-113">ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="75b66-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
