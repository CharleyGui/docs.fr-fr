---
title: ICorProfilerCallback2::FinalizeableObjectQueued, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: e2e01c396a67614464e3d4ca50de992388961463
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499819"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="05d0b-102">ICorProfilerCallback2::FinalizeableObjectQueued, méthode</span><span class="sxs-lookup"><span data-stu-id="05d0b-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="05d0b-103">Notifie le profileur de code qu’un objet avec un finaliseur a été mis en file d’attente dans le thread finaliseur pour l’exécution de sa `Finalize` méthode.</span><span class="sxs-lookup"><span data-stu-id="05d0b-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05d0b-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05d0b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05d0b-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="05d0b-106">dans Valeur de l’énumération [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) qui décrit les aspects du finaliseur.</span><span class="sxs-lookup"><span data-stu-id="05d0b-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="05d0b-107">dans ID de l’objet qui a été mis en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="05d0b-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d0b-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05d0b-108">Requirements</span></span>  
 <span data-ttu-id="05d0b-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05d0b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d0b-110">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="05d0b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05d0b-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05d0b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05d0b-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d0b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d0b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05d0b-113">See also</span></span>

- [<span data-ttu-id="05d0b-114">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="05d0b-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="05d0b-115">ICorProfilerCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="05d0b-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
