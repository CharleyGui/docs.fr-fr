---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868328"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="dce3c-102">ICorProfilerInfo8 :: GetFunctionFromIP3, méthode</span><span class="sxs-lookup"><span data-stu-id="dce3c-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="dce3c-103">Mappe un pointeur d’instruction de code managé à une FunctionID.</span><span class="sxs-lookup"><span data-stu-id="dce3c-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="dce3c-104">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="dce3c-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="dce3c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dce3c-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="dce3c-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="dce3c-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="dce3c-107">\[dans] pointeur d’instruction en code managé.</span><span class="sxs-lookup"><span data-stu-id="dce3c-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="dce3c-108">\[out] ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="dce3c-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="dce3c-109">\[out] identité de la version recompilée juste-à-temps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="dce3c-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="dce3c-110">Notes</span><span class="sxs-lookup"><span data-stu-id="dce3c-110">Remarks</span></span>

<span data-ttu-id="dce3c-111">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="dce3c-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="dce3c-112">Il s’agit d’un sur-ensemble de [getfunctionfromip2,](icorprofilerinfo4-getfunctionfromip2-method.md), qui fonctionne uniquement pour les fonctions avec métadonnées.</span><span class="sxs-lookup"><span data-stu-id="dce3c-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="dce3c-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="dce3c-113">Requirements</span></span>

<span data-ttu-id="dce3c-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dce3c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="dce3c-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dce3c-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="dce3c-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce3c-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="dce3c-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="dce3c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="dce3c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dce3c-118">See also</span></span>

- [<span data-ttu-id="dce3c-119">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="dce3c-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
