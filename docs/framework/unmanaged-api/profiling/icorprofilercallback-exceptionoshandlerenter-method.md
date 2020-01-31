---
title: ICorProfilerCallback::ExceptionOSHandlerEnter, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
ms.openlocfilehash: e27fd3147182e8c820fb1d30f172e0517ca4e77e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866471"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="f5d1d-102">ICorProfilerCallback::ExceptionOSHandlerEnter, méthode</span><span class="sxs-lookup"><span data-stu-id="f5d1d-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>
<span data-ttu-id="f5d1d-103">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="f5d1d-103">Not implemented.</span></span> <span data-ttu-id="f5d1d-104">Un profileur qui a besoin d’informations sur les exceptions non managées doit obtenir ces informations par d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="f5d1d-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5d1d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5d1d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f5d1d-106">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f5d1d-106">Requirements</span></span>  
 <span data-ttu-id="f5d1d-107">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5d1d-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5d1d-108">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f5d1d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5d1d-109">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5d1d-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5d1d-110">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5d1d-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d1d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5d1d-111">See also</span></span>

- [<span data-ttu-id="f5d1d-112">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="f5d1d-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
