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
ms.openlocfilehash: 607143d7848534329a55a9caebdb6b9175b2749c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866414"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="b1b18-102">ICorProfilerCallback::ExceptionSearchFilterLeave, méthode</span><span class="sxs-lookup"><span data-stu-id="b1b18-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>
<span data-ttu-id="b1b18-103">Notifie le profileur qu’un filtre utilisateur vient de terminer son exécution.</span><span class="sxs-lookup"><span data-stu-id="b1b18-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1b18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1b18-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="b1b18-105">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="b1b18-105">Requirements</span></span>  
 <span data-ttu-id="b1b18-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1b18-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1b18-107">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b1b18-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1b18-108">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1b18-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1b18-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1b18-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1b18-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1b18-110">See also</span></span>

- [<span data-ttu-id="b1b18-111">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="b1b18-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b1b18-112">ExceptionSearchFilterEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="b1b18-112">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
