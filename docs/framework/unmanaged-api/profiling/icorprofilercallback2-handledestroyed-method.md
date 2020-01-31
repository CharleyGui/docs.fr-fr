---
title: ICorProfilerCallback2::HandleDestroyed, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleDestroyed
helpviewer_keywords:
- ICorProfilerCallback2::HandleDestroyed method [.NET Framework profiling]
- HandleDestroyed method [.NET Framework profiling]
ms.assetid: ab4f4bbd-40c7-4667-bfde-60cd73803110
topic_type:
- apiref
ms.openlocfilehash: b2618da708a1c4351b56a15af9156a68392a0d59
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865748"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="eb20e-102">ICorProfilerCallback2::HandleDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="eb20e-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="eb20e-103">Notifie le profileur de code qu’un handle de garbage collection a été détruit.</span><span class="sxs-lookup"><span data-stu-id="eb20e-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb20e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb20e-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb20e-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="eb20e-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="eb20e-106">dans ID du descripteur pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="eb20e-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb20e-107">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="eb20e-107">Requirements</span></span>  
 <span data-ttu-id="eb20e-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb20e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb20e-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb20e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb20e-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb20e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb20e-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb20e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb20e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb20e-112">See also</span></span>

- [<span data-ttu-id="eb20e-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="eb20e-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="eb20e-114">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="eb20e-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
