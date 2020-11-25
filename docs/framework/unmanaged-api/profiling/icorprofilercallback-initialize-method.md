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
ms.openlocfilehash: 26df1599af247bd08d3702d4ef3c5aa2f648620c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720371"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="21b07-102">ICorProfilerCallback::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="21b07-102">ICorProfilerCallback::Initialize Method</span></span>

<span data-ttu-id="21b07-103">Appelé pour initialiser le profileur de code chaque fois qu’une nouvelle application common language runtime (CLR) est démarrée.</span><span class="sxs-lookup"><span data-stu-id="21b07-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21b07-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21b07-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21b07-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="21b07-106">\[in] pointeur vers une interface [IUnknown](/cpp/atl/iunknown) que le profileur doit interroger pour obtenir un pointeur d’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="21b07-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="21b07-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="21b07-107">Remarks</span></span>  

 <span data-ttu-id="21b07-108">L' `Initialize` appel est la seule possibilité d’activer (ou de désactiver) les rappels qui sont immuables.</span><span class="sxs-lookup"><span data-stu-id="21b07-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="21b07-109">Une fois qu’un rappel est activé par l' `Initialize` appel, il ne peut pas être désactivé ultérieurement à l’aide de [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="21b07-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="21b07-110">La valeur COR_PRF_MONITOR_IMMUTABLE de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indique quels événements sont immuables.</span><span class="sxs-lookup"><span data-stu-id="21b07-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b07-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21b07-111">Requirements</span></span>  

 <span data-ttu-id="21b07-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21b07-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b07-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21b07-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21b07-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21b07-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b07-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b07-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b07-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21b07-116">See also</span></span>

- [<span data-ttu-id="21b07-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="21b07-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="21b07-118">Shutdown Method</span><span class="sxs-lookup"><span data-stu-id="21b07-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
