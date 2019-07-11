---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished (méthode)
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba9f9d4ee5f95def3dcd2d757517e225c826cb9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757992"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="f7cb2-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished (méthode)</span><span class="sxs-lookup"><span data-stu-id="f7cb2-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="f7cb2-103">[Pris en charge dans le .NET Framework 4.7 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="f7cb2-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="f7cb2-104">Notifie le profileur chaque fois que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7cb2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7cb2-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7cb2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7cb2-106">Parameters</span></span>  
<span data-ttu-id="f7cb2-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="f7cb2-107">[in] `functionId`</span></span>  
<span data-ttu-id="f7cb2-108">L’identificateur de la fonction en mémoire pour le JIT démarrage de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="f7cb2-109">[in] `hrStatus` </span><span class="sxs-lookup"><span data-stu-id="f7cb2-109">[in] `hrStatus` </span></span>  
<span data-ttu-id="f7cb2-110">Une valeur qui indique si la compilation JIT a réussi.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-110">A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="f7cb2-111">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="f7cb2-111">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="f7cb2-112">`true` pour indiquer que le blocage peut entraîner l’exécution pour attendre que le thread appelant retourner à partir de ce rappel ; `false` pour indiquer que le blocage n’affecte pas l’opération du runtime.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-112">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="f7cb2-113">Notes</span><span class="sxs-lookup"><span data-stu-id="f7cb2-113">Remarks</span></span>  

<span data-ttu-id="f7cb2-114">Ce rappel est déclenché chaque fois que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-114">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="f7cb2-115">Cela inclut diverses de stubs de langage intermédiaire et de méthodes LCG.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-115">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="f7cb2-116">Son objectif est de fournir les enregistreurs de profileur avec suffisamment d’informations pour identifier la méthode compilée pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-116">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="f7cb2-117">`functionId` les valeurs ne peut pas être permet de résoudre à leurs jetons de métadonnées, car les méthodes dynamiques ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f7cb2-117">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7cb2-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7cb2-118">Requirements</span></span>  
 <span data-ttu-id="f7cb2-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7cb2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7cb2-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7cb2-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7cb2-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7cb2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7cb2-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f7cb2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7cb2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7cb2-123">See also</span></span>

- [<span data-ttu-id="f7cb2-124">DynamicMethodJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="f7cb2-124">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="f7cb2-125">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="f7cb2-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
