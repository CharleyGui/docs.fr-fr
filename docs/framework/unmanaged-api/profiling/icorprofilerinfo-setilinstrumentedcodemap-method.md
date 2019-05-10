---
title: ICorProfilerInfo::SetILInstrumentedCodeMap, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ec0f986efe24b0b69df9d2ecd93335f7ac5db28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606633"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="fd9f9-102">ICorProfilerInfo::SetILInstrumentedCodeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="fd9f9-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="fd9f9-103">Définit une carte de code pour la fonction spécifiée à l’aide d’entrées de mappage Microsoft intermediate language (MSIL) spécifiées.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd9f9-104">Dans le .NET Framework version 2.0, l’appel `SetILInstrumentedCodeMap` sur un `FunctionID` que représente une fonction générique dans un domaine d’application affecte toutes les instances de cette fonction dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd9f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd9f9-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd9f9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fd9f9-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fd9f9-107">[in] L’ID de la fonction pour laquelle définir la carte de code.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="fd9f9-108">[in] Valeur booléenne qui indique si l’appel à la `SetILInstrumentedCodeMap` méthode est le premier pour un particulier `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="fd9f9-109">Définissez `fStartJit` à `true` dans le premier appel à `SetILInstrumentedCodeMap` pour une donnée `FunctionID`et `false` par la suite.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="fd9f9-110">[in] Le nombre d’éléments dans le `cILMapEntries` tableau.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="fd9f9-111">[in] Tableau de structures COR_IL_MAP, dont chacun spécifie un offset MSIL.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd9f9-112">Notes</span><span class="sxs-lookup"><span data-stu-id="fd9f9-112">Remarks</span></span>  
 <span data-ttu-id="fd9f9-113">Un profileur insère souvent des instructions dans le code source d’une méthode pour instrumenter cette méthode (par exemple, pour avertir lorsqu’une ligne source donnée est atteinte).</span><span class="sxs-lookup"><span data-stu-id="fd9f9-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="fd9f9-114">`SetILInstrumentedCodeMap` permet à un profileur mapper les instructions MSIL d’origine à leurs nouveaux emplacements.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="fd9f9-115">Un profileur peut utiliser le [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) méthode pour obtenir l’offset MSIL d’origine pour un offset natif donné.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="fd9f9-116">Le débogueur suppose que chaque ancien offset fait référence à un offset MSIL dans le code MSIL non modifié d’origine, et que chaque nouveau décalage fait référence à l’offset MSIL dans le nouveau code instrumenté.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="fd9f9-117">Le mappage doit être trié par ordre croissant.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="fd9f9-118">Pour le pas à pas fonctionne correctement, suivez ces instructions :</span><span class="sxs-lookup"><span data-stu-id="fd9f9-118">For stepping to work properly, follow these guidelines:</span></span>  
  
- <span data-ttu-id="fd9f9-119">Ne réorganisez pas le code MSIL instrumenté.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-119">Do not reorder instrumented MSIL code.</span></span>  
  
- <span data-ttu-id="fd9f9-120">Ne supprimez pas le code MSIL d’origine.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-120">Do not remove the original MSIL code.</span></span>  
  
- <span data-ttu-id="fd9f9-121">Inclure des entrées pour tous les points de séquence à partir du fichier de base de données (PDB) du programme dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="fd9f9-122">Le mappage n’interpole pas les entrées manquantes.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="fd9f9-123">Ainsi, étant donné le plan suivant :</span><span class="sxs-lookup"><span data-stu-id="fd9f9-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="fd9f9-124">(0 ancien, 0 nouveau)</span><span class="sxs-lookup"><span data-stu-id="fd9f9-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="fd9f9-125">(5 anciens, 10 nouveaux)</span><span class="sxs-lookup"><span data-stu-id="fd9f9-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="fd9f9-126">(9 ancien, 20 nouveaux)</span><span class="sxs-lookup"><span data-stu-id="fd9f9-126">(9 old, 20 new)</span></span>  
  
    - <span data-ttu-id="fd9f9-127">Un ancien offset de 0, 1, 2, 3 ou 4 sera mappé à nouveau décalage 0.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    - <span data-ttu-id="fd9f9-128">Un ancien offset de 5, 6, 7 ou 8 sera mappé à nouveau décalage de 10.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    - <span data-ttu-id="fd9f9-129">Un ancien offset de 9 ou version ultérieure sera mappé à nouveau décalage de 20.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    - <span data-ttu-id="fd9f9-130">Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien offset 0.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    - <span data-ttu-id="fd9f9-131">Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien offset 5.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    - <span data-ttu-id="fd9f9-132">Un nouveau décalage supérieur ou égal à 20 sera mappé à l’ancien offset 9.</span><span class="sxs-lookup"><span data-stu-id="fd9f9-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd9f9-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="fd9f9-133">Requirements</span></span>  
 <span data-ttu-id="fd9f9-134">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd9f9-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd9f9-135">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd9f9-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd9f9-136">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd9f9-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd9f9-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd9f9-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9f9-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd9f9-138">See also</span></span>

- [<span data-ttu-id="fd9f9-139">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="fd9f9-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
