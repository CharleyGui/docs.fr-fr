---
title: Méthode ICorProfilerFunctionControl::SetILInstrumentedCodeMap
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: b2fca16b3b859df8bd7409149eb5a3cf7b011c5c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864581"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="eae0c-102">Méthode ICorProfilerFunctionControl::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="eae0c-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="eae0c-103">Définit une carte de code pour la fonction spécifiée à l’aide des entrées de mappage CIL (Common Intermediate Language) spécifiées.</span><span class="sxs-lookup"><span data-stu-id="eae0c-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eae0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eae0c-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eae0c-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="eae0c-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="eae0c-106">[en entrée] Le nombre d'entrées de la mappe.</span><span class="sxs-lookup"><span data-stu-id="eae0c-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="eae0c-107">[en entrée] Le tableau alloué par l'appelant, contenant des entrées COR_IL_MAP.</span><span class="sxs-lookup"><span data-stu-id="eae0c-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="eae0c-108">L’interprétation de ces entrées est la même que pour la méthode [ICorProfilerInfo :: SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="eae0c-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eae0c-109">Notes</span><span class="sxs-lookup"><span data-stu-id="eae0c-109">Remarks</span></span>  
 <span data-ttu-id="eae0c-110">La définition du mappage en appelant cette méthode permet au débogueur de récupérer le mappage en appelant [ICorDebugILCode2 :: getinstrumentedilmap,](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="eae0c-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="eae0c-111">Elle permet aussi au débogueur d'utiliser le mappage en interne lors du calcul des décalages du langage intermédiaire pour les traces de pile et les cycles de vie des variables.</span><span class="sxs-lookup"><span data-stu-id="eae0c-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eae0c-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="eae0c-112">Requirements</span></span>  
 <span data-ttu-id="eae0c-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eae0c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eae0c-114">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eae0c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eae0c-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eae0c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eae0c-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eae0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae0c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eae0c-117">See also</span></span>

- [<span data-ttu-id="eae0c-118">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="eae0c-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
