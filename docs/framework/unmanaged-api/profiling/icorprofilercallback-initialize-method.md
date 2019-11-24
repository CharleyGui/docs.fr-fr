---
title: ICorProfilerCallback::Initialize, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434550"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="a1154-102">ICorProfilerCallback::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="a1154-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="a1154-103">Appelé pour initialiser le profileur de code chaque fois qu’une nouvelle application common language runtime (CLR) est démarrée.</span><span class="sxs-lookup"><span data-stu-id="a1154-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1154-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1154-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1154-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1154-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="a1154-106">[dans](/cpp/atl/iunknown) l’interface, le profileur doit interroger un pointeur d’interface [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a1154-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1154-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a1154-107">Remarks</span></span>  
 <span data-ttu-id="a1154-108">L’appel de `Initialize` est la seule possibilité d’activer (ou de désactiver) les rappels qui sont immuables.</span><span class="sxs-lookup"><span data-stu-id="a1154-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="a1154-109">Une fois qu’un rappel est activé par l’appel de `Initialize`, il ne peut pas être désactivé ultérieurement à l’aide de [ICorProfilerInfo :: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="a1154-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="a1154-110">La valeur COR_PRF_MONITOR_IMMUTABLE de l’énumération [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) indique quels événements sont immuables.</span><span class="sxs-lookup"><span data-stu-id="a1154-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1154-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1154-111">Requirements</span></span>  
 <span data-ttu-id="a1154-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1154-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1154-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1154-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1154-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1154-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1154-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1154-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1154-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1154-116">See also</span></span>

- [<span data-ttu-id="a1154-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a1154-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="a1154-118">Shutdown, méthode</span><span class="sxs-lookup"><span data-stu-id="a1154-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
