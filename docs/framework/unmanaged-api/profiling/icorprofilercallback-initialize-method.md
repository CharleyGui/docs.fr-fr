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
ms.openlocfilehash: e4a003b30c495852a3a68d44d92bef35c3ed7812
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866294"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="5679e-102">ICorProfilerCallback::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="5679e-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="5679e-103">Appelé pour initialiser le profileur de code chaque fois qu’une nouvelle application common language runtime (CLR) est démarrée.</span><span class="sxs-lookup"><span data-stu-id="5679e-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5679e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5679e-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5679e-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="5679e-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="5679e-106">\[in] pointeur vers une interface [IUnknown](/cpp/atl/iunknown) que le profileur doit interroger pour obtenir un pointeur d’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5679e-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="5679e-107">Notes</span><span class="sxs-lookup"><span data-stu-id="5679e-107">Remarks</span></span>  
 <span data-ttu-id="5679e-108">L’appel de `Initialize` est la seule possibilité d’activer (ou de désactiver) les rappels qui sont immuables.</span><span class="sxs-lookup"><span data-stu-id="5679e-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="5679e-109">Une fois qu’un rappel est activé par l’appel de `Initialize`, il ne peut pas être désactivé ultérieurement à l’aide de [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="5679e-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="5679e-110">La valeur COR_PRF_MONITOR_IMMUTABLE de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indique quels événements sont immuables.</span><span class="sxs-lookup"><span data-stu-id="5679e-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5679e-111">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="5679e-111">Requirements</span></span>  
 <span data-ttu-id="5679e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5679e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5679e-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5679e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5679e-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5679e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5679e-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5679e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5679e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5679e-116">See also</span></span>

- [<span data-ttu-id="5679e-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="5679e-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5679e-118">Shutdown, méthode</span><span class="sxs-lookup"><span data-stu-id="5679e-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
