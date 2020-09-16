---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e3d5a09730cb8e477bd506749017a403acff1696
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540555"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="0c5f2-102">ICorProfilerInfo10 :: RequestReJITWithInliners, méthode</span><span class="sxs-lookup"><span data-stu-id="0c5f2-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="0c5f2-103">ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c5f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0c5f2-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="0c5f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0c5f2-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="0c5f2-106">\[in] masque de [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="0c5f2-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="0c5f2-107">\[in] nombre de fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="0c5f2-108">\[in] spécifie la `moduleId` partie des `module` paires (, `methodDef` ) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="0c5f2-109">\[in] spécifie la `methodId` partie des `module` paires (, `methodDef` ) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c5f2-110">Notes</span><span class="sxs-lookup"><span data-stu-id="0c5f2-110">Remarks</span></span>

<span data-ttu-id="0c5f2-111">[Requestrejit,](icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="0c5f2-112">Le profileur devait bloquer l’incorporation ou suivre l’inline et appeler `RequestReJIT` pour tous les inlineers pour s’assurer que chaque instance d’une méthode Inline était ReJITted.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="0c5f2-113">Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="0c5f2-114">Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.</span><span class="sxs-lookup"><span data-stu-id="0c5f2-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c5f2-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0c5f2-115">Requirements</span></span>

<span data-ttu-id="0c5f2-116">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/windows.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="0c5f2-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="0c5f2-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c5f2-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="0c5f2-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c5f2-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0c5f2-119">**Versions de .net :**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c5f2-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0c5f2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c5f2-120">See also</span></span>

- [<span data-ttu-id="0c5f2-121">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="0c5f2-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
