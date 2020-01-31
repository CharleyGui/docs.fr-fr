---
title: ICorDebugFunction3::GetActiveReJitRequestILCode, méthode
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 70a55b833acb7fa946c694a63e1e8b51562938bc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777726"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="ede0a-102">ICorDebugFunction3::GetActiveReJitRequestILCode, méthode</span><span class="sxs-lookup"><span data-stu-id="ede0a-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="ede0a-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="ede0a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ede0a-104">Obtient un pointeur d’interface vers un [ICorDebugILCode](icordebugilcode-interface.md) qui contient le langage intermédiaire d’une requête ReJIT active.</span><span class="sxs-lookup"><span data-stu-id="ede0a-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ede0a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ede0a-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ede0a-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="ede0a-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="ede0a-107">Un pointeur depuis une demande ReJIT active vers le langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="ede0a-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ede0a-108">Notes</span><span class="sxs-lookup"><span data-stu-id="ede0a-108">Remarks</span></span>  
 <span data-ttu-id="ede0a-109">Si la méthode représentée par cet objet `ICorDebugFunction3` a une demande ReJIT active, `ppReJitedILCode` retourne un pointeur vers son langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="ede0a-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="ede0a-110">S’il n’y a aucune requête active, ce qui est un cas courant, `ppReJitedILCode` a la **valeur null**.</span><span class="sxs-lookup"><span data-stu-id="ede0a-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="ede0a-111">Une requête ReJIT devient active juste après le retour de l’exécution de l’appel de la méthode [ICorProfilerCallback4 :: getrejitparameters,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ede0a-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="ede0a-112">Il est possible qu'elle ne soit pas encore compilée en mode juste-à-temps et que des threads soient toujours en cours d'exécution dans la version d'origine du code.</span><span class="sxs-lookup"><span data-stu-id="ede0a-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="ede0a-113">Une requête ReJIT devient inactive pendant l’appel du profileur à la méthode [ICorProfilerInfo4 :: requestrevert,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ede0a-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="ede0a-114">Même après le rétablissement du langage intermédiaire, un thread peut toujours être en train d'exécuter le code ReJIT (recompilé en mode juste-à-temps).</span><span class="sxs-lookup"><span data-stu-id="ede0a-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede0a-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="ede0a-115">Requirements</span></span>  
 <span data-ttu-id="ede0a-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede0a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede0a-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ede0a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ede0a-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ede0a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ede0a-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede0a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede0a-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ede0a-120">See also</span></span>

- [<span data-ttu-id="ede0a-121">ICorDebugFunction3, interface</span><span class="sxs-lookup"><span data-stu-id="ede0a-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="ede0a-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="ede0a-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ede0a-123">ReJIT : Guide pratique</span><span class="sxs-lookup"><span data-stu-id="ede0a-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
