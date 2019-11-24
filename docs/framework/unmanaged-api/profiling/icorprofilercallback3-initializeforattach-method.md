---
title: ICorProfilerCallback3::InitializeForAttach, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439522"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="cb8d9-102">ICorProfilerCallback3::InitializeForAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="cb8d9-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="cb8d9-103">Appelée par le Common Language Runtime (CLR) pour permettre au profileur d’initialiser son état après une opération d’attachement.</span><span class="sxs-lookup"><span data-stu-id="cb8d9-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb8d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb8d9-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb8d9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cb8d9-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="cb8d9-106">[in] Pointeur d'interface pour l'interface `ICorProfilerInfo*`.</span><span class="sxs-lookup"><span data-stu-id="cb8d9-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="cb8d9-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span><span class="sxs-lookup"><span data-stu-id="cb8d9-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="cb8d9-108">Si ce paramètre est null, `cbClientData` est égal à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="cb8d9-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="cb8d9-109">Le CLR libère cette mémoire au retour de `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="cb8d9-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="cb8d9-110">[in] Taille, en octets, des données vers lesquelles `pvClientData` pointe.</span><span class="sxs-lookup"><span data-stu-id="cb8d9-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb8d9-111">Notes</span><span class="sxs-lookup"><span data-stu-id="cb8d9-111">Remarks</span></span>  
 <span data-ttu-id="cb8d9-112">Le CLR appelle `InitializeForAttach` pour permettre au profileur de demander des rappels.</span><span class="sxs-lookup"><span data-stu-id="cb8d9-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb8d9-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="cb8d9-113">Requirements</span></span>  
 <span data-ttu-id="cb8d9-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb8d9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb8d9-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cb8d9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb8d9-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb8d9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb8d9-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb8d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb8d9-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb8d9-118">See also</span></span>

- [<span data-ttu-id="cb8d9-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="cb8d9-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cb8d9-120">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="cb8d9-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cb8d9-121">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="cb8d9-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="cb8d9-122">Profilage</span><span class="sxs-lookup"><span data-stu-id="cb8d9-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
