---
title: ICorProfilerInfo4::GetILToNativeMapping2, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: 37d6b6d5112089df18fb138086db5e138a69629c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697751"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="1abd9-102">ICorProfilerInfo4::GetILToNativeMapping2, méthode</span><span class="sxs-lookup"><span data-stu-id="1abd9-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>

<span data-ttu-id="1abd9-103">Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la version recompilée juste-à-temps de la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1abd9-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1abd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1abd9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1abd9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1abd9-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="1abd9-106">[in] ID de la fonction contenant le code.</span><span class="sxs-lookup"><span data-stu-id="1abd9-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="1abd9-107">[in] Identité de la fonction recompilée juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="1abd9-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="1abd9-108">L’identité doit être égale à zéro dans le .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="1abd9-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="1abd9-109">[in] Taille maximale du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="1abd9-110">[out] Nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.</span><span class="sxs-lookup"><span data-stu-id="1abd9-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="1abd9-111">[out] Tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP` qui spécifient chacune les offsets.</span><span class="sxs-lookup"><span data-stu-id="1abd9-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="1abd9-112">Suite au retour de la méthode `GetILToNativeMapping2`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1abd9-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="1abd9-113">Remarks</span></span>  

 <span data-ttu-id="1abd9-114">`GetILToNativeMapping2` est semblable à la méthode [ICorProfilerInfo :: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) , sauf qu’elle permet au profileur de spécifier l’ID de la fonction recompilée dans les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="1abd9-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1abd9-115">La méthode [ICorProfilerFunctionControl :: SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) n’est pas implémentée dans le .NET Framework 4,5. par conséquent, les fonctions qui ont été recompilées juste-à-temps ne peuvent pas avoir un mappage il-à-natif qui diffère de la fonction initialement compilée.</span><span class="sxs-lookup"><span data-stu-id="1abd9-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="1abd9-116">Par conséquent, `GetILToNativeMapping2` ne peut pas être appelé avec un ID recompilé juste-à-zéro dans le .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="1abd9-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="1abd9-117">La méthode `GetILToNativeMapping2` retourne un tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="1abd9-118">Pour indiquer que certaines plages d’instructions natives correspondent à des régions de code spéciales (par exemple, le prologue), le champ d’une entrée dans le tableau peut avoir `ilOffset` la valeur de l’énumération [CorDebugIlToNativeMappingTypes,](../debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1abd9-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="1abd9-119">Suite au retour de `GetILToNativeMapping2`, vous devez vérifier que la mémoire tampon `map` est suffisamment grande pour contenir toutes les structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="1abd9-120">Pour ce faire, comparez la valeur de `cMap` à celle du paramètre `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="1abd9-121">Si la valeur `pcMap`, une fois multipliée par la taille d'une structure `COR_DEBUG_IL_TO_NATIVE_MAP`, est supérieure à `cMap`, allouez une mémoire tampon `map` plus grande, mettez à jour `cMap` pour refléter la nouvelle taille et rappelez `GetILToNativeMapping2`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="1abd9-122">Vous pouvez également commencer par appeler `GetILToNativeMapping2` avec un tampon `map` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="1abd9-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="1abd9-123">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcMap` et rappeler `GetILToNativeMapping2`.</span><span class="sxs-lookup"><span data-stu-id="1abd9-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1abd9-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1abd9-124">Requirements</span></span>  

 <span data-ttu-id="1abd9-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1abd9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1abd9-126">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1abd9-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1abd9-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1abd9-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1abd9-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1abd9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1abd9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1abd9-129">See also</span></span>

- [<span data-ttu-id="1abd9-130">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="1abd9-130">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="1abd9-131">ICorProfilerInfo4, interface</span><span class="sxs-lookup"><span data-stu-id="1abd9-131">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1abd9-132">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="1abd9-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1abd9-133">Profilage</span><span class="sxs-lookup"><span data-stu-id="1abd9-133">Profiling</span></span>](index.md)
