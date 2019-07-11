---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad694f1a041346bc360e623829d2d38245773aaf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756073"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="3d62d-102">ICorProfilerCallback::ExceptionSearchFunctionLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="3d62d-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="3d62d-103">Notifie le profileur que la phase de recherche de gestion des exceptions a terminé la recherche d’une fonction.</span><span class="sxs-lookup"><span data-stu-id="3d62d-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d62d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d62d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3d62d-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d62d-105">Requirements</span></span>  
 <span data-ttu-id="3d62d-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d62d-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d62d-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3d62d-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3d62d-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d62d-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d62d-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d62d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d62d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d62d-110">See also</span></span>

- [<span data-ttu-id="3d62d-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="3d62d-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="3d62d-112">ExceptionSearchFunctionEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="3d62d-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
