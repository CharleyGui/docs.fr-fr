---
title: ICorProfilerInfo::GetILToNativeMapping, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
ms.openlocfilehash: f9abb3ae9cd3f9c70485e584399a6ed32b32a572
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870614"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="d0b98-102">ICorProfilerInfo::GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="d0b98-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="d0b98-103">Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d0b98-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0b98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0b98-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0b98-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d0b98-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d0b98-106">[in] ID de la fonction contenant le code.</span><span class="sxs-lookup"><span data-stu-id="d0b98-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="d0b98-107">[in] Taille maximale du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="d0b98-108">[out] Nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.</span><span class="sxs-lookup"><span data-stu-id="d0b98-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="d0b98-109">[out] Tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP` qui spécifient chacune les offsets.</span><span class="sxs-lookup"><span data-stu-id="d0b98-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="d0b98-110">Suite au retour de la méthode `GetILToNativeMapping`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0b98-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d0b98-111">Remarks</span></span>  
 <span data-ttu-id="d0b98-112">La méthode `GetILToNativeMapping` retourne un tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d0b98-113">Pour indiquer que certaines plages d’instructions natives correspondent à des régions de code spéciales (par exemple, le prologue), le champ `ilOffset` de l’entrée du tableau peut être défini sur une valeur de l’énumération [CorDebugIlToNativeMappingTypes,](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="d0b98-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="d0b98-114">Suite au retour de `GetILToNativeMapping`, vous devez vérifier que la mémoire tampon `map` est suffisamment grande pour contenir toutes les structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d0b98-115">Pour ce faire, comparez la valeur de `cMap` à celle du paramètre `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="d0b98-116">Si la valeur `pcMap`, une fois multipliée par la taille d'une structure `COR_DEBUG_IL_TO_NATIVE_MAP`, est supérieure à `cMap`, allouez une mémoire tampon `map` plus grande, mettez à jour `cMap` pour refléter la nouvelle taille et rappelez `GetILToNativeMapping`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="d0b98-117">Vous pouvez également commencer par appeler `GetILToNativeMapping` avec un tampon `map` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="d0b98-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d0b98-118">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcMap` et rappeler `GetILToNativeMapping`.</span><span class="sxs-lookup"><span data-stu-id="d0b98-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0b98-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d0b98-119">Requirements</span></span>  
 <span data-ttu-id="d0b98-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0b98-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0b98-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0b98-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0b98-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0b98-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0b98-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0b98-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b98-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0b98-124">See also</span></span>

- [<span data-ttu-id="d0b98-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d0b98-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="d0b98-126">GetILToNativeMapping2, méthode</span><span class="sxs-lookup"><span data-stu-id="d0b98-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="d0b98-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="d0b98-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d0b98-128">Profilage</span><span class="sxs-lookup"><span data-stu-id="d0b98-128">Profiling</span></span>](index.md)
