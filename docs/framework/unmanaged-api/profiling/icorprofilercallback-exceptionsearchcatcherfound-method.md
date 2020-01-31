---
title: ICorProfilerCallback::ExceptionSearchCatcherFound, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 8f5997dddf78dd75d482bc45d2ee730b20d9ab16
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866470"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="77fad-102">ICorProfilerCallback::ExceptionSearchCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="77fad-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="77fad-103">Notifie le profileur que la phase de recherche de la gestion des exceptions a localisé un gestionnaire pour l’exception qui a été levée.</span><span class="sxs-lookup"><span data-stu-id="77fad-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77fad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77fad-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77fad-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="77fad-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="77fad-106">\[in] ID de la fonction qui contient le gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="77fad-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="77fad-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="77fad-107">Requirements</span></span>  
 <span data-ttu-id="77fad-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77fad-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77fad-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77fad-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77fad-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77fad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77fad-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77fad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77fad-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77fad-112">See also</span></span>

- [<span data-ttu-id="77fad-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="77fad-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
