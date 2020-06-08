---
title: ICorProfilerInfo4::GetReJITIDs, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: ba15440df79dded95a8afa9438657d064e167f36
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495968"
---
# <a name="icorprofilerinfo4getrejitids-method"></a><span data-ttu-id="6c0b5-102">ICorProfilerInfo4::GetReJITIDs, méthode</span><span class="sxs-lookup"><span data-stu-id="6c0b5-102">ICorProfilerInfo4::GetReJITIDs Method</span></span>
<span data-ttu-id="6c0b5-103">Retourne un tableau d’ID identifiant toutes les versions recompilées juste-à-temps de la fonction spécifiée qui sont toujours allouées.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-103">Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.</span></span> <span data-ttu-id="6c0b5-104">Cela inclut les versions recompilées par le JIT des fonctions qui ont été annulées par la suite, mais qui n’ont pas encore été libérées (par exemple, quand le domaine d’application qui contient la fonction restaurée est toujours utilisé).</span><span class="sxs-lookup"><span data-stu-id="6c0b5-104">This includes JIT-recompiled versions of functions that have been subsequently reverted but not yet freed (for example, when the application domain that contains the reverted function is still in use).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c0b5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c0b5-105">Syntax</span></span>  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c0b5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c0b5-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="6c0b5-107">dans `FunctionID`De l’instance de fonction pour laquelle énumérer les versions.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-107">[in] The `FunctionID` of the function instance for which to enumerate versions.</span></span>  
  
 `cReJitIds`  
 <span data-ttu-id="6c0b5-108">dans Nombre d’ID recompilés par le compilateur JIT alloués dans le `reJitIds` tableau.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-108">[in] The number of JIT-recompiled IDs allocated in the `reJitIds` array.</span></span>  
  
 `pcReJitIds`  
 <span data-ttu-id="6c0b5-109">à Nombre réel d’ID recompilés juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-109">[out] The actual number of JIT-recompiled IDs.</span></span>  
  
 `reJitIds`  
 <span data-ttu-id="6c0b5-110">à Tableau alloué par l’appelant qui contient les ID recompilés juste-à-temps pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-110">[out] A caller-allocated array that will contain the JIT-recompiled IDs for the specified function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c0b5-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="6c0b5-111">Remarks</span></span>  
 <span data-ttu-id="6c0b5-112">`GetReJITIDs`énumère les ID recompilés JIT actifs pour une instance de fonction donnée.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-112">`GetReJITIDs` enumerates the active JIT-recompiled IDs for a given function instance.</span></span> <span data-ttu-id="6c0b5-113">Il suit le même modèle d’utilisation que les autres `ICorProfilerInfo` fonctions qui acceptent les mémoires tampons allouées par l’appelant.</span><span class="sxs-lookup"><span data-stu-id="6c0b5-113">It follows the same usage pattern as other `ICorProfilerInfo` functions that accept caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c0b5-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c0b5-114">Requirements</span></span>  
 <span data-ttu-id="6c0b5-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c0b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c0b5-116">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c0b5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c0b5-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c0b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c0b5-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c0b5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c0b5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c0b5-119">See also</span></span>

- [<span data-ttu-id="6c0b5-120">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="6c0b5-120">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="6c0b5-121">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="6c0b5-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="6c0b5-122">Profilage</span><span class="sxs-lookup"><span data-stu-id="6c0b5-122">Profiling</span></span>](index.md)
