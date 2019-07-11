---
title: ICorProfilerCallback::ExceptionSearchFilterEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d39dbf44b21400c8eb5a7abf361dc868b8d39a22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756099"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="e4dd5-102">ICorProfilerCallback::ExceptionSearchFilterEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="e4dd5-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="e4dd5-103">Notifie le profileur que la phase de recherche de gestion des exceptions a commencé l’exécution d’un filtre d’exception définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e4dd5-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4dd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4dd5-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4dd5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e4dd5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e4dd5-106">[in] L’ID de la fonction qui contient le filtre.</span><span class="sxs-lookup"><span data-stu-id="e4dd5-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4dd5-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e4dd5-107">Requirements</span></span>  
 <span data-ttu-id="e4dd5-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4dd5-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4dd5-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e4dd5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4dd5-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4dd5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4dd5-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4dd5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4dd5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e4dd5-112">See also</span></span>

- [<span data-ttu-id="e4dd5-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="e4dd5-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e4dd5-114">ExceptionSearchFilterLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="e4dd5-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
