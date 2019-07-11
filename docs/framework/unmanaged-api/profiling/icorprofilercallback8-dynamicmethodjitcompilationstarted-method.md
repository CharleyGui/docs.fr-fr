---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted (méthode)
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a60f074ce0081df07a61d0b832d542c8873776f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757985"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="5ffca-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted (méthode)</span><span class="sxs-lookup"><span data-stu-id="5ffca-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="5ffca-103">[Pris en charge dans le .NET Framework 4.7 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="5ffca-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="5ffca-104">Notifie le profileur chaque fois que la compilation JIT d’une méthode dynamique a démarré.</span><span class="sxs-lookup"><span data-stu-id="5ffca-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ffca-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ffca-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ffca-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ffca-106">Parameters</span></span>  
<span data-ttu-id="5ffca-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="5ffca-107">[in] `functionId`</span></span>  
<span data-ttu-id="5ffca-108">L’identificateur de la fonction en mémoire pour le JIT démarrage de la compilation.</span><span class="sxs-lookup"><span data-stu-id="5ffca-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="5ffca-109">[in] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="5ffca-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="5ffca-110">`true` pour indiquer que le blocage peut entraîner l’exécution pour attendre que le thread appelant retourner à partir de ce rappel ; `false` pour indiquer que le blocage n’affecte pas l’opération du runtime.</span><span class="sxs-lookup"><span data-stu-id="5ffca-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="5ffca-111">[in] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="5ffca-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="5ffca-112">Pointeur vers le premier octet d’en-tête de langage intermédiaire de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5ffca-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="5ffca-113">[in] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="5ffca-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="5ffca-114">Le nombre d’octets dans l’en-tête de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="5ffca-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="5ffca-115">Notes</span><span class="sxs-lookup"><span data-stu-id="5ffca-115">Remarks</span></span>  

<span data-ttu-id="5ffca-116">Ce rappel est déclenché chaque fois qu’une méthode dynamique est compilé par JIT.</span><span class="sxs-lookup"><span data-stu-id="5ffca-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="5ffca-117">Cela inclut diverses de stubs de langage intermédiaire et de méthodes LCG.</span><span class="sxs-lookup"><span data-stu-id="5ffca-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="5ffca-118">Son objectif est de fournir les enregistreurs de profileur avec suffisamment d’informations pour identifier la méthode compilée pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5ffca-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="5ffca-119">`functionId` les valeurs ne peut pas être permet de résoudre à leurs jetons de métadonnées, car les méthodes dynamiques ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5ffca-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="5ffca-120">Le `pILHeader` pointeur est uniquement valid pendant le rappel.</span><span class="sxs-lookup"><span data-stu-id="5ffca-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ffca-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ffca-121">Requirements</span></span>  
 <span data-ttu-id="5ffca-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ffca-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ffca-123">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5ffca-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ffca-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ffca-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ffca-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5ffca-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ffca-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ffca-126">See also</span></span>

- [<span data-ttu-id="5ffca-127">DynamicMethodJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="5ffca-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="5ffca-128">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="5ffca-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
