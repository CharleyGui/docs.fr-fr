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
ms.openlocfilehash: bbd4c9e40f257cc66b638ba01ef8e51205922ece
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866388"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="f608e-102">ICorProfilerCallback::ExceptionSearchFunctionLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="f608e-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="f608e-103">Indique au profileur que la phase de recherche de la gestion des exceptions a fini de rechercher une fonction.</span><span class="sxs-lookup"><span data-stu-id="f608e-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f608e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f608e-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f608e-105">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f608e-105">Requirements</span></span>  
 <span data-ttu-id="f608e-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f608e-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f608e-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f608e-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f608e-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f608e-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f608e-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f608e-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f608e-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f608e-110">See also</span></span>

- [<span data-ttu-id="f608e-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f608e-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f608e-112">ExceptionSearchFunctionEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="f608e-112">ExceptionSearchFunctionEnter Method</span></span>](icorprofilercallback-exceptionsearchfunctionenter-method.md)
