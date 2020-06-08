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
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500102"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="a12fd-102">ICorProfilerCallback::Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="a12fd-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="a12fd-103">Appelé pour initialiser le profileur de code chaque fois qu’une nouvelle application common language runtime (CLR) est démarrée.</span><span class="sxs-lookup"><span data-stu-id="a12fd-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a12fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a12fd-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a12fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a12fd-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="a12fd-106">\[in] pointeur vers une interface [IUnknown](/cpp/atl/iunknown) que le profileur doit interroger pour obtenir un pointeur d’interface [ICorProfilerInfo](icorprofilerinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a12fd-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="a12fd-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a12fd-107">Remarks</span></span>  
 <span data-ttu-id="a12fd-108">L' `Initialize` appel est la seule possibilité d’activer (ou de désactiver) les rappels qui sont immuables.</span><span class="sxs-lookup"><span data-stu-id="a12fd-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="a12fd-109">Une fois qu’un rappel est activé par l' `Initialize` appel, il ne peut pas être désactivé ultérieurement à l’aide de [ICorProfilerInfo :: SetEventMask](icorprofilerinfo-seteventmask-method.md).</span><span class="sxs-lookup"><span data-stu-id="a12fd-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="a12fd-110">La valeur COR_PRF_MONITOR_IMMUTABLE de l’énumération [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) indique quels événements sont immuables.</span><span class="sxs-lookup"><span data-stu-id="a12fd-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a12fd-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a12fd-111">Requirements</span></span>  
 <span data-ttu-id="a12fd-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a12fd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a12fd-113">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a12fd-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a12fd-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a12fd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a12fd-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a12fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a12fd-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a12fd-116">See also</span></span>

- [<span data-ttu-id="a12fd-117">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="a12fd-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a12fd-118">Shutdown Method</span><span class="sxs-lookup"><span data-stu-id="a12fd-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
