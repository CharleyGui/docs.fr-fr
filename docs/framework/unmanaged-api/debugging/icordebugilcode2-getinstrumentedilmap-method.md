---
title: ICorDebugILCode2::GetInstrumentedILMap, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 728a6c83dc321fa28dc4ff84c4e874d886524b36
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788572"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="751aa-102">ICorDebugILCode2::GetInstrumentedILMap, méthode</span><span class="sxs-lookup"><span data-stu-id="751aa-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>
<span data-ttu-id="751aa-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="751aa-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="751aa-104">Retourne un mappage des décalages du langage intermédiaire instrumenté par le profileur avec les décalages du langage intermédiaire de la méthode d'origine pour cette instance.</span><span class="sxs-lookup"><span data-stu-id="751aa-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="751aa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="751aa-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="751aa-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="751aa-106">Parameters</span></span>  
 <span data-ttu-id="751aa-107">cMap</span><span class="sxs-lookup"><span data-stu-id="751aa-107">cMap</span></span>  
 <span data-ttu-id="751aa-108">[en entrée] La capacité de stockage du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="751aa-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="751aa-109">Pour plus d'informations, consultez la section Notes.</span><span class="sxs-lookup"><span data-stu-id="751aa-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="751aa-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="751aa-110">pcMap</span></span>  
 <span data-ttu-id="751aa-111">[en sortie] Le nombre de valeurs COR_IL_MAP écrites dans le tableau du mappage.</span><span class="sxs-lookup"><span data-stu-id="751aa-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="751aa-112">map</span><span class="sxs-lookup"><span data-stu-id="751aa-112">map</span></span>  
 <span data-ttu-id="751aa-113">[en sortie] Un tableau de valeurs COR_IL_MAP qui fournissent des informations sur les mappages du langage intermédiaire instrumenté par le profileur avec le langage intermédiaire de la méthode d'origine.</span><span class="sxs-lookup"><span data-stu-id="751aa-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="751aa-114">Notes</span><span class="sxs-lookup"><span data-stu-id="751aa-114">Remarks</span></span>  
 <span data-ttu-id="751aa-115">Si le profileur définit le mappage en appelant la méthode [ICorProfilerInfo :: SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) , le débogueur peut appeler cette méthode pour récupérer le mappage et pour utiliser le mappage en interne lors du calcul des offsets de langage intermédiaire pour les traces de la pile et les durées de vie des variables.</span><span class="sxs-lookup"><span data-stu-id="751aa-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="751aa-116">Si `cMap` a la valeur 0 et que `pcMap` est non**null**, `pcMap` est défini sur le nombre de valeurs COR_IL_MAP disponibles.</span><span class="sxs-lookup"><span data-stu-id="751aa-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="751aa-117">Si `cMap` est différent de zéro, il représente la capacité de stockage du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="751aa-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="751aa-118">Lorsque la méthode est retournée, `map` contient au maximum `cMap` éléments, et `pcMap` est défini sur le nombre de valeurs COR_IL_MAP effectivement écrites dans le tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="751aa-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="751aa-119">Si le langage intermédiaire n'a pas été instrumenté ou si le mappage n'a pas été fourni par le profileur, cette méthode retourne `S_OK` et définit `pcMap` à 0.</span><span class="sxs-lookup"><span data-stu-id="751aa-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="751aa-120">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="751aa-120">Requirements</span></span>  
 <span data-ttu-id="751aa-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="751aa-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="751aa-122">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="751aa-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="751aa-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="751aa-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="751aa-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="751aa-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="751aa-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="751aa-125">See also</span></span>

- [<span data-ttu-id="751aa-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="751aa-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="751aa-127">ICorDebugILCode2, interface</span><span class="sxs-lookup"><span data-stu-id="751aa-127">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="751aa-128">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="751aa-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
