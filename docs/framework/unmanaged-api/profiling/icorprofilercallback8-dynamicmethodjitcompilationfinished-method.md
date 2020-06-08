---
title: ICorProfilerCallback8 ::D méthode ynamicMethodJITCompilationFinished
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 554cc93de934061e87322c7557e05545e5e7bc62
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499075"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="8d50c-102">ICorProfilerCallback8 ::D méthode ynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="8d50c-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>
<span data-ttu-id="8d50c-103">[Pris en charge dans le .NET Framework 4,7 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="8d50c-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="8d50c-104">Notifie le profileur chaque fois que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="8d50c-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d50c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d50c-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d50c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d50c-106">Parameters</span></span>  
<span data-ttu-id="8d50c-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="8d50c-107">[in] `functionId`</span></span>  
<span data-ttu-id="8d50c-108">Identificateur de la fonction en mémoire pour laquelle la compilation JIT est démarrée.</span><span class="sxs-lookup"><span data-stu-id="8d50c-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="8d50c-109">[in] `hrStatus` Valeur qui indique si la compilation JIT a réussi.</span><span class="sxs-lookup"><span data-stu-id="8d50c-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="8d50c-110">[in] `fIsSafeToBlock` 
 `true` pour indiquer que le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; `false`pour indiquer que le blocage n’affectera pas le fonctionnement du Runtime.</span><span class="sxs-lookup"><span data-stu-id="8d50c-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="8d50c-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="8d50c-111">Remarks</span></span>  

<span data-ttu-id="8d50c-112">Ce rappel est déclenché chaque fois que la compilation JIT d’une méthode dynamique est terminée.</span><span class="sxs-lookup"><span data-stu-id="8d50c-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="8d50c-113">Cela comprend plusieurs stubs IL et méthodes LCG.</span><span class="sxs-lookup"><span data-stu-id="8d50c-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="8d50c-114">Son objectif est de fournir aux rédacteurs de profileur suffisamment d’informations pour identifier la méthode compilée pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8d50c-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="8d50c-115">`functionId`les valeurs ne peuvent pas être utilisées pour la résolution de leurs jetons de métadonnées, car les méthodes dynamiques n’ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8d50c-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="8d50c-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8d50c-116">Requirements</span></span>  
 <span data-ttu-id="8d50c-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d50c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d50c-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8d50c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8d50c-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d50c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d50c-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8d50c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d50c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d50c-121">See also</span></span>

- [<span data-ttu-id="8d50c-122">DynamicMethodJITCompilationStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="8d50c-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8d50c-123">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="8d50c-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
