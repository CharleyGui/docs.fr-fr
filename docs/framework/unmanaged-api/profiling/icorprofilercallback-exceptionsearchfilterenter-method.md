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
ms.openlocfilehash: d58f2013e93eb1c7030d26ec60b0ab5ab08d0524
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699857"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="01229-102">ICorProfilerCallback::ExceptionSearchFilterEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="01229-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>

<span data-ttu-id="01229-103">Notifie le profileur que la phase de recherche de la gestion des exceptions a commencé l’exécution d’un filtre d’exception défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="01229-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01229-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01229-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01229-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01229-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="01229-106">\[in] ID de la fonction qui contient le filtre.</span><span class="sxs-lookup"><span data-stu-id="01229-106">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="01229-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01229-107">Requirements</span></span>  

 <span data-ttu-id="01229-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01229-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01229-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01229-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01229-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01229-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01229-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01229-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01229-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01229-112">See also</span></span>

- [<span data-ttu-id="01229-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="01229-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="01229-114">ExceptionSearchFilterLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="01229-114">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
