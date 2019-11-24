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
ms.openlocfilehash: 8dc551b2b1e29aba371e56eecfd981f16b4b1e3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439039"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="d185f-102">ICorProfilerInfo::GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="d185f-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="d185f-103">Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d185f-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d185f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d185f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d185f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d185f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d185f-106">[in] ID de la fonction contenant le code.</span><span class="sxs-lookup"><span data-stu-id="d185f-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="d185f-107">[in] Taille maximale du tableau `map`.</span><span class="sxs-lookup"><span data-stu-id="d185f-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="d185f-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span><span class="sxs-lookup"><span data-stu-id="d185f-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="d185f-109">[out] Tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP` qui spécifient chacune les offsets.</span><span class="sxs-lookup"><span data-stu-id="d185f-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="d185f-110">Suite au retour de la méthode `GetILToNativeMapping`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="d185f-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d185f-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d185f-111">Remarks</span></span>  
 <span data-ttu-id="d185f-112">La méthode `GetILToNativeMapping` retourne un tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="d185f-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d185f-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="d185f-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="d185f-114">Suite au retour de `GetILToNativeMapping`, vous devez vérifier que la mémoire tampon `map` est suffisamment grande pour contenir toutes les structures `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="d185f-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d185f-115">Pour ce faire, comparez la valeur de `cMap` à celle du paramètre `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="d185f-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="d185f-116">Si la valeur `pcMap`, une fois multipliée par la taille d'une structure `COR_DEBUG_IL_TO_NATIVE_MAP`, est supérieure à `cMap`, allouez une mémoire tampon `map` plus grande, mettez à jour `cMap` pour refléter la nouvelle taille et rappelez `GetILToNativeMapping`.</span><span class="sxs-lookup"><span data-stu-id="d185f-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="d185f-117">Vous pouvez également commencer par appeler `GetILToNativeMapping` avec un tampon `map` de longueur nulle pour obtenir la taille correcte du tampon.</span><span class="sxs-lookup"><span data-stu-id="d185f-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d185f-118">Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcMap` et rappeler `GetILToNativeMapping`.</span><span class="sxs-lookup"><span data-stu-id="d185f-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d185f-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="d185f-119">Requirements</span></span>  
 <span data-ttu-id="d185f-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d185f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d185f-121">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d185f-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d185f-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d185f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d185f-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d185f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d185f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d185f-124">See also</span></span>

- [<span data-ttu-id="d185f-125">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d185f-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d185f-126">GetILToNativeMapping2, méthode</span><span class="sxs-lookup"><span data-stu-id="d185f-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="d185f-127">Interfaces de profilage</span><span class="sxs-lookup"><span data-stu-id="d185f-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d185f-128">Profilage</span><span class="sxs-lookup"><span data-stu-id="d185f-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
