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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cb8783ba1427ecc2396abb32f350664ddf83d19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779315"
---
# <a name="icorprofilercallback2handledestroyed-method"></a><span data-ttu-id="d6999-102">ICorProfilerCallback2::HandleDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="d6999-102">ICorProfilerCallback2::HandleDestroyed Method</span></span>
<span data-ttu-id="d6999-103">Notifie le profileur de code qu’un handle de garbage collection a été détruit.</span><span class="sxs-lookup"><span data-stu-id="d6999-103">Notifies the code profiler that a garbage collection handle has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6999-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6999-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleDestroyed(  
    [in] GCHandleID handleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6999-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d6999-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="d6999-106">[in] L’ID du handle pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="d6999-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6999-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d6999-107">Requirements</span></span>  
 <span data-ttu-id="d6999-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6999-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6999-109">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6999-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6999-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6999-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6999-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6999-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6999-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6999-112">See also</span></span>

- [<span data-ttu-id="d6999-113">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d6999-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d6999-114">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="d6999-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
