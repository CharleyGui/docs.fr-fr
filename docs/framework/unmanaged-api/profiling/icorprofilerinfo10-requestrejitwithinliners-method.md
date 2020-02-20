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
ms.openlocfilehash: 99b6893854c358720259095bf3c0270cb3676483
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452173"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="9a4af-102">ICorProfilerInfo10 :: RequestReJITWithInliners, méthode</span><span class="sxs-lookup"><span data-stu-id="9a4af-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="9a4af-103">ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.</span><span class="sxs-lookup"><span data-stu-id="9a4af-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a4af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a4af-104">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="9a4af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a4af-105">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="9a4af-106">\[dans] masque de [réCOR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9a4af-106">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="9a4af-107">\[in] nombre de fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="9a4af-107">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="9a4af-108">\[in] spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="9a4af-108">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="9a4af-109">\[in] spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="9a4af-109">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="9a4af-110">Notes</span><span class="sxs-lookup"><span data-stu-id="9a4af-110">Remarks</span></span>

<span data-ttu-id="9a4af-111">[Requestrejit,](icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline.</span><span class="sxs-lookup"><span data-stu-id="9a4af-111">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="9a4af-112">Le profileur devait bloquer l’incorporation ou le suivi des Inlines et appeler `RequestReJIT` pour tous les Inlines afin de s’assurer que chaque instance d’une méthode Inline était ReJITted.</span><span class="sxs-lookup"><span data-stu-id="9a4af-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="9a4af-113">Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation.</span><span class="sxs-lookup"><span data-stu-id="9a4af-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="9a4af-114">Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.</span><span class="sxs-lookup"><span data-stu-id="9a4af-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="9a4af-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9a4af-115">Requirements</span></span>

<span data-ttu-id="9a4af-116">**Plateformes :** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="9a4af-116">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>

<span data-ttu-id="9a4af-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9a4af-117">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="9a4af-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a4af-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="9a4af-119">**Versions de .net :** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a4af-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9a4af-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a4af-120">See also</span></span>

- [<span data-ttu-id="9a4af-121">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="9a4af-121">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
