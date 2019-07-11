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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a17776b38d7e16b39f966e0d83d50a7d004d4c3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776073"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="f57a6-102">ICorProfilerCallback::ExceptionCLRCatcherExecute, méthode</span><span class="sxs-lookup"><span data-stu-id="f57a6-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="f57a6-103">Appelé lorsqu’un `catch` block pour une exception est exécutée dans le common language runtime (CLR) lui-même.</span><span class="sxs-lookup"><span data-stu-id="f57a6-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="f57a6-104">Cette méthode est obsolète dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="f57a6-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f57a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f57a6-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f57a6-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f57a6-106">Requirements</span></span>  
 <span data-ttu-id="f57a6-107">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f57a6-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f57a6-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f57a6-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f57a6-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f57a6-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f57a6-110">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="f57a6-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f57a6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f57a6-111">See also</span></span>

- [<span data-ttu-id="f57a6-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f57a6-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f57a6-113">ExceptionCLRCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="f57a6-113">ExceptionCLRCatcherFound Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)
