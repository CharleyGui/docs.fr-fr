---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 85f788ec61cc441e7271fb7a8aba843f37d20a57
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782724"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="9b1fd-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="9b1fd-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>
<span data-ttu-id="9b1fd-103">Notifie le profileur que la phase de déroulement de la gestion des exceptions a commencé à une fonction de déroulement.</span><span class="sxs-lookup"><span data-stu-id="9b1fd-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b1fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b1fd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b1fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b1fd-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="9b1fd-106">[in] L’ID de la fonction qui n’est pas vidée.</span><span class="sxs-lookup"><span data-stu-id="9b1fd-106">[in] The ID of the function that is being unwound.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b1fd-107">Notes</span><span class="sxs-lookup"><span data-stu-id="9b1fd-107">Remarks</span></span>  
 <span data-ttu-id="9b1fd-108">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="9b1fd-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="9b1fd-109">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel renvoie.</span><span class="sxs-lookup"><span data-stu-id="9b1fd-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="9b1fd-110">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="9b1fd-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b1fd-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9b1fd-111">Requirements</span></span>  
 <span data-ttu-id="9b1fd-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b1fd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b1fd-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b1fd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b1fd-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b1fd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b1fd-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b1fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1fd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b1fd-116">See also</span></span>

- [<span data-ttu-id="9b1fd-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="9b1fd-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9b1fd-118">ExceptionUnwindFunctionLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="9b1fd-118">ExceptionUnwindFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)
