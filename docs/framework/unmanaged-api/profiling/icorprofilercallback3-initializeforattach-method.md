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
ms.openlocfilehash: 9bff594d0307153fb468b28c1535977f06997748
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499712"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="8a794-102">ICorProfilerCallback3::InitializeForAttach, méthode</span><span class="sxs-lookup"><span data-stu-id="8a794-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="8a794-103">Appelée par le Common Language Runtime (CLR) pour permettre au profileur d’initialiser son état après une opération d’attachement.</span><span class="sxs-lookup"><span data-stu-id="8a794-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a794-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a794-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a794-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a794-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="8a794-106">[in] Pointeur d'interface pour l'interface `ICorProfilerInfo*`.</span><span class="sxs-lookup"><span data-stu-id="8a794-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="8a794-107">dans Pointeur vers les données passées à la méthode [ICLRProfiling :: AttachProfiler](iclrprofiling-attachprofiler-method.md) dans son `pvClientData` paramètre.</span><span class="sxs-lookup"><span data-stu-id="8a794-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="8a794-108">Si ce paramètre est null, `cbClientData` est égal à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="8a794-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="8a794-109">Le CLR libère cette mémoire au retour de `InitializeForAttach`.</span><span class="sxs-lookup"><span data-stu-id="8a794-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="8a794-110">[in] Taille, en octets, des données vers lesquelles `pvClientData` pointe.</span><span class="sxs-lookup"><span data-stu-id="8a794-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a794-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a794-111">Remarks</span></span>  
 <span data-ttu-id="8a794-112">Le CLR appelle `InitializeForAttach` pour permettre au profileur de demander des rappels.</span><span class="sxs-lookup"><span data-stu-id="8a794-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a794-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a794-113">Requirements</span></span>  
 <span data-ttu-id="8a794-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a794-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a794-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a794-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a794-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a794-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a794-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a794-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a794-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a794-118">See also</span></span>

- [<span data-ttu-id="8a794-119">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8a794-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8a794-120">ICorProfilerInfo3, interface</span><span class="sxs-lookup"><span data-stu-id="8a794-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="8a794-121">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="8a794-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8a794-122">Profilage</span><span class="sxs-lookup"><span data-stu-id="8a794-122">Profiling</span></span>](index.md)
