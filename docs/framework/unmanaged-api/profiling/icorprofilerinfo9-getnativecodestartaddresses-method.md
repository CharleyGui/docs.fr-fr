---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868276"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="f8ae4-102">ICorProfilerInfo9 :: GetNativeCodeStartAddresses, méthode</span><span class="sxs-lookup"><span data-stu-id="f8ae4-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="f8ae4-103">Étant donné une functionId et rejitId, énumère l’adresse de début du code natif de toutes les versions JIT de ce code qui existent actuellement.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8ae4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8ae4-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="f8ae4-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="f8ae4-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="f8ae4-106">\[in] ID de la fonction dont les adresses de début de code natif doivent être retournées.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="f8ae4-107">\[dans] identité de la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="f8ae4-108">\[dans] taille maximale du tableau de `codeStartAddresses`.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="f8ae4-109">\[out] nombre d’adresses disponibles.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="f8ae4-110">\[out] tableau de `UINT_PTR`, chacun d’entre eux étant l’adresse de début d’un corps natif pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8ae4-111">Notes</span><span class="sxs-lookup"><span data-stu-id="f8ae4-111">Remarks</span></span>

<span data-ttu-id="f8ae4-112">Lorsque la compilation à plusieurs niveaux est activée, une fonction peut avoir plusieurs corps de code natif.</span><span class="sxs-lookup"><span data-stu-id="f8ae4-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8ae4-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="f8ae4-113">Requirements</span></span>

<span data-ttu-id="f8ae4-114">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="f8ae4-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="f8ae4-115">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8ae4-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f8ae4-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8ae4-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f8ae4-117">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8ae4-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f8ae4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8ae4-118">See also</span></span>

- [<span data-ttu-id="f8ae4-119">Interface ICorProfilerInfo9</span><span class="sxs-lookup"><span data-stu-id="f8ae4-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)
