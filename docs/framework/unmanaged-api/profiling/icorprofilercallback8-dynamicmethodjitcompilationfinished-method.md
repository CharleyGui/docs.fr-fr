---
title: ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175107"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="8b49b-102">ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode</span><span class="sxs-lookup"><span data-stu-id="8b49b-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="8b49b-103">[Soutenu dans le cadre .NET 4.7 et les versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="8b49b-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="8b49b-104">Informe le profileur chaque fois que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="8b49b-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b49b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b49b-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b49b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8b49b-106">Parameters</span></span>  
<span data-ttu-id="8b49b-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8b49b-107">[in] `functionId`</span></span>  
<span data-ttu-id="8b49b-108">L’identifiant de la fonction mémoire pour laquelle la compilation JIT est commencée.</span><span class="sxs-lookup"><span data-stu-id="8b49b-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="8b49b-109">[dans] `hrStatus` Une valeur qui indique si la compilation JIT a été couronnée de succès.</span><span class="sxs-lookup"><span data-stu-id="8b49b-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="8b49b-110">[dans] `fIsSafeToBlock` pour indiquer que le blocage peut faire attendre le temps d’exécution pour que le fil d’appel revienne de ce 
 `true` rappel; `false` pour indiquer que le blocage n’affectera pas le fonctionnement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8b49b-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="8b49b-111">Notes </span><span class="sxs-lookup"><span data-stu-id="8b49b-111">Remarks</span></span>  

<span data-ttu-id="8b49b-112">Ce rappel est déclenché chaque fois que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="8b49b-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="8b49b-113">Cela comprend divers talons IL et méthodes LCG.</span><span class="sxs-lookup"><span data-stu-id="8b49b-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="8b49b-114">Son objectif est de fournir aux auteurs de profileur suffisamment d’informations pour identifier la méthode compilée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8b49b-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="8b49b-115">`functionId`les valeurs ne peuvent pas être utilisées pour résoudre leurs jetons de métadonnées, parce que les méthodes dynamiques n’ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8b49b-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="8b49b-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8b49b-116">Requirements</span></span>  
 <span data-ttu-id="8b49b-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b49b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b49b-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8b49b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b49b-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b49b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b49b-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8b49b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b49b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b49b-121">See also</span></span>

- [<span data-ttu-id="8b49b-122">DynamicMethodJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="8b49b-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8b49b-123">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="8b49b-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
