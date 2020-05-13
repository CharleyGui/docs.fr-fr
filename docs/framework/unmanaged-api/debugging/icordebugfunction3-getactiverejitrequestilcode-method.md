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
ms.openlocfilehash: 9e7f682752cfefae63b574655a4fc5e8964146a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213177"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="05122-102">ICorDebugFunction3::GetActiveReJitRequestILCode, méthode</span><span class="sxs-lookup"><span data-stu-id="05122-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="05122-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="05122-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="05122-104">Obtient un pointeur d’interface vers un [ICorDebugILCode](icordebugilcode-interface.md) qui contient le langage intermédiaire d’une requête ReJIT active.</span><span class="sxs-lookup"><span data-stu-id="05122-104">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05122-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05122-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05122-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05122-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="05122-107">Un pointeur depuis une demande ReJIT active vers le langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="05122-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05122-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="05122-108">Remarks</span></span>  
 <span data-ttu-id="05122-109">Si la méthode représentée par cet objet `ICorDebugFunction3` a une demande ReJIT active, `ppReJitedILCode` retourne un pointeur vers son langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="05122-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="05122-110">S’il n’y a aucune requête active, ce qui est un cas courant, `ppReJitedILCode` est **null**.</span><span class="sxs-lookup"><span data-stu-id="05122-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="05122-111">Une requête ReJIT devient active juste après le retour de l’exécution de l’appel de la méthode [ICorProfilerCallback4 :: getrejitparameters,](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="05122-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="05122-112">Il est possible qu'elle ne soit pas encore compilée en mode juste-à-temps et que des threads soient toujours en cours d'exécution dans la version d'origine du code.</span><span class="sxs-lookup"><span data-stu-id="05122-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="05122-113">Une requête ReJIT devient inactive pendant l’appel du profileur à la méthode [ICorProfilerInfo4 :: requestrevert,](../profiling/icorprofilerinfo4-requestrevert-method.md) .</span><span class="sxs-lookup"><span data-stu-id="05122-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="05122-114">Même après le rétablissement du langage intermédiaire, un thread peut toujours être en train d'exécuter le code ReJIT (recompilé en mode juste-à-temps).</span><span class="sxs-lookup"><span data-stu-id="05122-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05122-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="05122-115">Requirements</span></span>  
 <span data-ttu-id="05122-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05122-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05122-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05122-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05122-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05122-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05122-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05122-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05122-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05122-120">See also</span></span>

- [<span data-ttu-id="05122-121">ICorDebugFunction3, interface</span><span class="sxs-lookup"><span data-stu-id="05122-121">ICorDebugFunction3 Interface</span></span>](icordebugfunction3-interface.md)
- [<span data-ttu-id="05122-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="05122-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="05122-123">ReJIT : Guide pratique</span><span class="sxs-lookup"><span data-stu-id="05122-123">ReJIT: A How-To Guide</span></span>](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
