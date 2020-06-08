---
title: ICorProfilerCallback::ExceptionSearchFilterLeave, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
ms.openlocfilehash: fbece20701fbde5551e025b4f116f9873abf444d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500206"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="489bb-102">ICorProfilerCallback::ExceptionSearchFilterLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="489bb-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="489bb-103">Notifie le profileur qu’un filtre utilisateur vient de terminer son exécution.</span><span class="sxs-lookup"><span data-stu-id="489bb-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="489bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="489bb-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="489bb-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="489bb-105">Requirements</span></span>  
 <span data-ttu-id="489bb-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="489bb-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="489bb-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="489bb-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="489bb-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="489bb-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="489bb-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="489bb-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="489bb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="489bb-110">See also</span></span>

- [<span data-ttu-id="489bb-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="489bb-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="489bb-112">ExceptionSearchFilterEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="489bb-112">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
