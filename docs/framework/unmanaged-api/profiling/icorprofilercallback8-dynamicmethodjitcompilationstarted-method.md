---
title: ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177044"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="58c53-102">ICorProfilerCallback8::DynamicMethodJITCompilationLa méthode</span><span class="sxs-lookup"><span data-stu-id="58c53-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="58c53-103">[Soutenu dans le cadre .NET 4.7 et les versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="58c53-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="58c53-104">Informe le profileur chaque fois que la compilation JIT d’une méthode dynamique a commencé.</span><span class="sxs-lookup"><span data-stu-id="58c53-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58c53-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58c53-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58c53-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58c53-106">Parameters</span></span>  
<span data-ttu-id="58c53-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="58c53-107">[in] `functionId`</span></span>  
<span data-ttu-id="58c53-108">L’identifiant de la fonction mémoire pour laquelle la compilation JIT est commencée.</span><span class="sxs-lookup"><span data-stu-id="58c53-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="58c53-109">[dans] `fIsSafeToBlock` pour indiquer que le blocage peut faire attendre le temps d’exécution pour que le fil d’appel revienne de ce 
 `true` rappel; `false` pour indiquer que le blocage n’affectera pas le fonctionnement de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="58c53-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="58c53-110">[dans] `pILHeader` Un pointeur au premier byte de l’en-tête il de la méthode.</span><span class="sxs-lookup"><span data-stu-id="58c53-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="58c53-111">[dans] `cbILHeader` Le nombre d’octets dans l’en-tête de l’IL.</span><span class="sxs-lookup"><span data-stu-id="58c53-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="58c53-112">Notes </span><span class="sxs-lookup"><span data-stu-id="58c53-112">Remarks</span></span>  

<span data-ttu-id="58c53-113">Ce rappel est déclenché chaque fois qu’une méthode dynamique est compilée par JIT.</span><span class="sxs-lookup"><span data-stu-id="58c53-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="58c53-114">Cela comprend divers talons IL et méthodes LCG.</span><span class="sxs-lookup"><span data-stu-id="58c53-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="58c53-115">Son objectif est de fournir aux auteurs de profileur suffisamment d’informations pour identifier la méthode compilée aux utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="58c53-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="58c53-116">`functionId`les valeurs ne peuvent pas être utilisées pour résoudre leurs jetons de métadonnées, parce que les méthodes dynamiques n’ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="58c53-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="58c53-117">Le `pILHeader` pointeur n’est valable que pendant le rappel.</span><span class="sxs-lookup"><span data-stu-id="58c53-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="58c53-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="58c53-118">Requirements</span></span>  
 <span data-ttu-id="58c53-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58c53-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58c53-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="58c53-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="58c53-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58c53-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58c53-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="58c53-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58c53-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58c53-123">See also</span></span>

- [<span data-ttu-id="58c53-124">DynamicMethodJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="58c53-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="58c53-125">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="58c53-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
