---
title: ICorProfilerCallback8 ::D méthode ynamicMethodJITCompilationStarted
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 46a25fc6e9119481f728275e0569429cc6c46dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725428"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="7aaac-102">ICorProfilerCallback8 ::D méthode ynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="7aaac-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="7aaac-103">[Pris en charge dans le .NET Framework 4,7 et versions ultérieures]</span><span class="sxs-lookup"><span data-stu-id="7aaac-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="7aaac-104">Notifie le profileur chaque fois que la compilation JIT d’une méthode dynamique a démarré.</span><span class="sxs-lookup"><span data-stu-id="7aaac-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aaac-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7aaac-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aaac-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7aaac-106">Parameters</span></span>  

<span data-ttu-id="7aaac-107">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="7aaac-107">[in] `functionId`</span></span>  
<span data-ttu-id="7aaac-108">Identificateur de la fonction en mémoire pour laquelle la compilation JIT est démarrée.</span><span class="sxs-lookup"><span data-stu-id="7aaac-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="7aaac-109">[in] `fIsSafeToBlock` 
 `true` pour indiquer que le blocage peut amener le runtime à attendre que le thread appelant retourne à partir de ce rappel ; `false`pour indiquer que le blocage n’affectera pas le fonctionnement du Runtime.</span><span class="sxs-lookup"><span data-stu-id="7aaac-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="7aaac-110">[in] `pILHeader` Pointeur vers le premier octet de l’en-tête IL de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7aaac-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="7aaac-111">[in] `cbILHeader` Nombre d’octets dans l’en-tête IL.</span><span class="sxs-lookup"><span data-stu-id="7aaac-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="7aaac-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="7aaac-112">Remarks</span></span>  

<span data-ttu-id="7aaac-113">Ce rappel est déclenché chaque fois qu’une méthode dynamique est compilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="7aaac-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="7aaac-114">Cela comprend plusieurs stubs IL et méthodes LCG.</span><span class="sxs-lookup"><span data-stu-id="7aaac-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="7aaac-115">Son objectif est de fournir aux rédacteurs de profileur suffisamment d’informations pour identifier la méthode compilée pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="7aaac-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="7aaac-116">`functionId` les valeurs ne peuvent pas être utilisées pour la résolution de leurs jetons de métadonnées, car les méthodes dynamiques n’ont pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7aaac-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="7aaac-117">Le `pILHeader` pointeur est valide uniquement pendant le rappel.</span><span class="sxs-lookup"><span data-stu-id="7aaac-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="7aaac-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7aaac-118">Requirements</span></span>  

 <span data-ttu-id="7aaac-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7aaac-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aaac-120">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7aaac-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7aaac-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aaac-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aaac-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7aaac-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aaac-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aaac-123">See also</span></span>

- [<span data-ttu-id="7aaac-124">DynamicMethodJITCompilationFinished, méthode</span><span class="sxs-lookup"><span data-stu-id="7aaac-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="7aaac-125">ICorProfilerCallback8, interface</span><span class="sxs-lookup"><span data-stu-id="7aaac-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
