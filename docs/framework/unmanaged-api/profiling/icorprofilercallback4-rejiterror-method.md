---
title: ICorProfilerCallback4::ReJITError, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430109"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="cd9d3-102">ICorProfilerCallback4::ReJITError, méthode</span><span class="sxs-lookup"><span data-stu-id="cd9d3-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="cd9d3-103">Notifie le profileur que le compilateur juste-à-temps (JIT) a rencontré une erreur dans le processus de recompilation.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd9d3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd9d3-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd9d3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd9d3-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="cd9d3-106">dans `ModuleID` dans lequel la tentative de recompilation a échoué.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="cd9d3-107">dans `MethodDef` de la méthode sur laquelle la tentative de recompilation a échoué.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="cd9d3-108">dans Instance de fonction qui est recompilée ou marquée pour la recompilation.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="cd9d3-109">Cette valeur peut être `NULL` si l’échec s’est produit par méthode au lieu d’une base par instanciation (par exemple, si le profileur a spécifié un jeton de métadonnées non valide pour la méthode à recompiler).</span><span class="sxs-lookup"><span data-stu-id="cd9d3-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="cd9d3-110">dans HRESULT qui indique la nature de l’échec.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="cd9d3-111">Pour obtenir la liste des valeurs, consultez la section HRESULT d’État.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd9d3-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cd9d3-112">Return Value</span></span>  
 <span data-ttu-id="cd9d3-113">Les valeurs retournées depuis ce rappel sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="cd9d3-114">HRESULT d'état</span><span class="sxs-lookup"><span data-stu-id="cd9d3-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="cd9d3-115">HRESULT du tableau d'états</span><span class="sxs-lookup"><span data-stu-id="cd9d3-115">Status array HRESULT</span></span>|<span data-ttu-id="cd9d3-116">Description</span><span class="sxs-lookup"><span data-stu-id="cd9d3-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="cd9d3-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="cd9d3-117">E_INVALIDARG</span></span>|<span data-ttu-id="cd9d3-118">Le jeton `moduleID` ou `methodDef` est `NULL`.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="cd9d3-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="cd9d3-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="cd9d3-120">Le module n'est pas encore totalement chargé ou il est en cours de déchargement.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="cd9d3-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="cd9d3-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="cd9d3-122">Le module spécifié a été généré dynamiquement (par exemple, par `Reflection.Emit`) et n’est donc pas pris en charge par cette méthode.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="cd9d3-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="cd9d3-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="cd9d3-124">La méthode est instanciée dans un assembly pouvant être collecté et ne peut donc pas être recompilée.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="cd9d3-125">Notez que les types et les fonctions définis dans un contexte non réfléchissant (par exemple, `List<MyCollectibleStruct>`) peuvent être instanciés dans un assembly pouvant être collecté.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="cd9d3-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="cd9d3-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="cd9d3-127">La mémoire du CLR est insuffisante lors de la tentative de marquage de la méthode spécifiée pour la recompilation JIT.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="cd9d3-128">Autres</span><span class="sxs-lookup"><span data-stu-id="cd9d3-128">Other</span></span>|<span data-ttu-id="cd9d3-129">Le système d'exploitation a retourné un échec en dehors du contrôle du CLR.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="cd9d3-130">Par exemple, si un appel système pour modifier la protection d’accès d’une page de mémoire échoue, l’erreur du système d’exploitation s’affiche.</span><span class="sxs-lookup"><span data-stu-id="cd9d3-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd9d3-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cd9d3-131">Requirements</span></span>  
 <span data-ttu-id="cd9d3-132">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd9d3-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd9d3-133">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd9d3-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd9d3-134">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd9d3-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd9d3-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd9d3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd9d3-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd9d3-136">See also</span></span>

- [<span data-ttu-id="cd9d3-137">ICorProfilerCallback, interface</span><span class="sxs-lookup"><span data-stu-id="cd9d3-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cd9d3-138">ICorProfilerCallback4, interface</span><span class="sxs-lookup"><span data-stu-id="cd9d3-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
