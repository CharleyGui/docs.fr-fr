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
ms.openlocfilehash: 1a9e377ba98c0c2302e341149bd5acb46c24051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699987"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="0d212-102">ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="0d212-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>

<span data-ttu-id="0d212-103">Appelée lorsqu’un `catch` bloc pour une exception est exécuté à l’intérieur du Common Language Runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="0d212-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="0d212-104">Cette méthode est obsolète dans la version 2,0 de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0d212-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d212-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0d212-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="0d212-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d212-106">Requirements</span></span>  

 <span data-ttu-id="0d212-107">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d212-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d212-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d212-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d212-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d212-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d212-110">**Versions de .NET Framework :** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="0d212-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d212-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d212-111">See also</span></span>

- [<span data-ttu-id="0d212-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="0d212-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0d212-113">ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="0d212-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
