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
ms.openlocfilehash: 70c03d34bdf9bd315994b2bfa09631efac2565ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500219"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="69f7c-102">ICorProfilerCallback::ExceptionSearchCatcherFound, méthode</span><span class="sxs-lookup"><span data-stu-id="69f7c-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="69f7c-103">Notifie le profileur que la phase de recherche de la gestion des exceptions a localisé un gestionnaire pour l’exception qui a été levée.</span><span class="sxs-lookup"><span data-stu-id="69f7c-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69f7c-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69f7c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="69f7c-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="69f7c-106">\[in] ID de la fonction qui contient le gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="69f7c-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="69f7c-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="69f7c-107">Requirements</span></span>  
 <span data-ttu-id="69f7c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69f7c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69f7c-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="69f7c-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69f7c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="69f7c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69f7c-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69f7c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69f7c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="69f7c-112">See also</span></span>

- [<span data-ttu-id="69f7c-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="69f7c-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
