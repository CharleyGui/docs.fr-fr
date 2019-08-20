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
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973979"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="cd414-102">ICorProfilerInfo10:: RequestReJITWithInliners, méthode</span><span class="sxs-lookup"><span data-stu-id="cd414-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>
  
<span data-ttu-id="cd414-103">ReJITs les méthodes demandées, ainsi que les Inlines des méthodes demandées.</span><span class="sxs-lookup"><span data-stu-id="cd414-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="cd414-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd414-104">Syntax</span></span>  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd414-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd414-105">Parameters</span></span>  
 
 `dwRejitFlags` \
 <span data-ttu-id="cd414-106">dans Masque de [réCOR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="cd414-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>
 
 `cFunctions`  
 <span data-ttu-id="cd414-107">[in] Nombre de fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="cd414-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="cd414-108">[in] Spécifie la partie `moduleId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="cd414-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="cd414-109">[in] Spécifie la partie `methodId` des paires (`module`, `methodDef`) qui identifient les fonctions à recompiler.</span><span class="sxs-lookup"><span data-stu-id="cd414-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  

## <a name="remarks"></a><span data-ttu-id="cd414-110">Notes</span><span class="sxs-lookup"><span data-stu-id="cd414-110">Remarks</span></span>  
  <span data-ttu-id="cd414-111">[Requestrejit,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) n’effectue aucun suivi des méthodes Inline.</span><span class="sxs-lookup"><span data-stu-id="cd414-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="cd414-112">Le profileur devait bloquer l’incorporation ou suivre l’inline et appeler `RequestReJIT` pour tous les inlineers pour s’assurer que chaque instance d’une méthode Inline était ReJITted.</span><span class="sxs-lookup"><span data-stu-id="cd414-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="cd414-113">Cela pose un problème avec ReJIT lors de l’attachement, car le profileur n’est pas présent pour surveiller l’incorporation.</span><span class="sxs-lookup"><span data-stu-id="cd414-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="cd414-114">Cette méthode peut être appelée pour garantir que l’ensemble complet des Inlines sera également ReJITted.</span><span class="sxs-lookup"><span data-stu-id="cd414-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>  

## <a name="requirements"></a><span data-ttu-id="cd414-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cd414-115">Requirements</span></span>  
 <span data-ttu-id="cd414-116">**Plateformes** Consultez [systèmes d’exploitation pris en charge par .net Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="cd414-116">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="cd414-117">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cd414-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd414-118">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd414-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd414-119">**Versions de .net:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd414-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cd414-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd414-120">See also</span></span>
- [<span data-ttu-id="cd414-121">Interface ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="cd414-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
