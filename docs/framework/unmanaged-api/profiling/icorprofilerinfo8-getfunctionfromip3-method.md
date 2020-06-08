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
ms.openlocfilehash: 6822757608429ca5f4ef9520ab7574d440b67b26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495254"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="180f5-102">ICorProfilerInfo8 :: GetFunctionFromIP3, méthode</span><span class="sxs-lookup"><span data-stu-id="180f5-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="180f5-103">Mappe un pointeur d’instruction de code managé à une FunctionID.</span><span class="sxs-lookup"><span data-stu-id="180f5-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="180f5-104">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="180f5-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="180f5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="180f5-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="180f5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="180f5-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="180f5-107">\[in] pointeur d’instruction en code managé.</span><span class="sxs-lookup"><span data-stu-id="180f5-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="180f5-108">\[out] ID de la fonction.</span><span class="sxs-lookup"><span data-stu-id="180f5-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="180f5-109">\[out] identité de la version recompilée juste-à-temps de la fonction.</span><span class="sxs-lookup"><span data-stu-id="180f5-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="180f5-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="180f5-110">Remarks</span></span>

<span data-ttu-id="180f5-111">Cette méthode fonctionne pour les méthodes dynamiques et non dynamiques.</span><span class="sxs-lookup"><span data-stu-id="180f5-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="180f5-112">Il s’agit d’un sur-ensemble de [getfunctionfromip2,](icorprofilerinfo4-getfunctionfromip2-method.md), qui fonctionne uniquement pour les fonctions avec métadonnées.</span><span class="sxs-lookup"><span data-stu-id="180f5-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="180f5-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="180f5-113">Requirements</span></span>

<span data-ttu-id="180f5-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="180f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="180f5-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="180f5-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="180f5-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="180f5-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="180f5-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="180f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="180f5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="180f5-118">See also</span></span>

- [<span data-ttu-id="180f5-119">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="180f5-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
