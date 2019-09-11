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
ms.openlocfilehash: 65eee2e834251817b461f1cd1debf212696d5a5f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855690"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="80dde-102">ICorProfilerInfo::SetILInstrumentedCodeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="80dde-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="80dde-103">Définit une carte de code pour la fonction spécifiée à l’aide des entrées de mappage MSIL (Microsoft Intermediate Language) spécifiées.</span><span class="sxs-lookup"><span data-stu-id="80dde-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="80dde-104">Dans la version 2,0 de .NET Framework, `SetILInstrumentedCodeMap` l’appel `FunctionID` de sur un qui représente une fonction générique dans un domaine d’application particulier affecte toutes les instances de cette fonction dans le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="80dde-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="80dde-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80dde-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="80dde-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="80dde-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="80dde-107">dans ID de la fonction pour laquelle définir la carte de code.</span><span class="sxs-lookup"><span data-stu-id="80dde-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="80dde-108">dans Valeur booléenne qui indique si l’appel à la `SetILInstrumentedCodeMap` méthode est le premier pour un particulier. `FunctionID`</span><span class="sxs-lookup"><span data-stu-id="80dde-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="80dde-109">`fStartJit` Affectez `true` à la valeur dans le `SetILInstrumentedCodeMap` premier appel à `FunctionID`pour un donné `false` , et par la suite.</span><span class="sxs-lookup"><span data-stu-id="80dde-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="80dde-110">dans Nombre d’éléments dans le `cILMapEntries` tableau.</span><span class="sxs-lookup"><span data-stu-id="80dde-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="80dde-111">dans Tableau de structures COR_IL_MAP, chacune spécifiant un décalage MSIL.</span><span class="sxs-lookup"><span data-stu-id="80dde-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="80dde-112">Notes</span><span class="sxs-lookup"><span data-stu-id="80dde-112">Remarks</span></span>

<span data-ttu-id="80dde-113">Un profileur insère souvent des instructions dans le code source d’une méthode afin d’instrumenter cette méthode (par exemple, pour notifier quand une ligne source donnée est atteinte).</span><span class="sxs-lookup"><span data-stu-id="80dde-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="80dde-114">`SetILInstrumentedCodeMap`permet à un profileur de mapper les instructions MSIL d’origine à leurs nouveaux emplacements.</span><span class="sxs-lookup"><span data-stu-id="80dde-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="80dde-115">Un profileur peut utiliser la méthode [ICorProfilerInfo :: GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) pour obtenir l’offset MSIL d’origine pour un offset natif donné.</span><span class="sxs-lookup"><span data-stu-id="80dde-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="80dde-116">Le débogueur suppose que chaque ancien offset fait référence à un offset MSIL dans le code MSIL non modifié d’origine, et que chaque nouvel offset fait référence à l’offset MSIL dans le nouveau code instrumenté.</span><span class="sxs-lookup"><span data-stu-id="80dde-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="80dde-117">Le mappage doit être trié par ordre de tri.</span><span class="sxs-lookup"><span data-stu-id="80dde-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="80dde-118">Pour que l’exécution pas à pas fonctionne correctement, suivez les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="80dde-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="80dde-119">Ne réorganisez pas le code MSIL instrumenté.</span><span class="sxs-lookup"><span data-stu-id="80dde-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="80dde-120">Ne supprimez pas le code MSIL d’origine.</span><span class="sxs-lookup"><span data-stu-id="80dde-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="80dde-121">Incluez les entrées de tous les points de séquence du fichier de base de données du programme (PDB) dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="80dde-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="80dde-122">Le mappage n’interpole pas les entrées manquantes.</span><span class="sxs-lookup"><span data-stu-id="80dde-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="80dde-123">Par conséquent, à partir de la carte suivante :</span><span class="sxs-lookup"><span data-stu-id="80dde-123">So, given the following map:</span></span>

  <span data-ttu-id="80dde-124">(0 ancien, 0 nouveau)</span><span class="sxs-lookup"><span data-stu-id="80dde-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="80dde-125">(5 anciennes, 10 nouvelles)</span><span class="sxs-lookup"><span data-stu-id="80dde-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="80dde-126">(9 vieux, 20 nouveaux)</span><span class="sxs-lookup"><span data-stu-id="80dde-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="80dde-127">Un ancien décalage de 0, 1, 2, 3 ou 4 sera mappé au nouveau décalage 0.</span><span class="sxs-lookup"><span data-stu-id="80dde-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="80dde-128">Un ancien décalage de 5, 6, 7 ou 8 sera mappé au nouveau décalage 10.</span><span class="sxs-lookup"><span data-stu-id="80dde-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="80dde-129">Un ancien décalage de 9 ou plus sera mappé au nouveau décalage 20.</span><span class="sxs-lookup"><span data-stu-id="80dde-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="80dde-130">Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien décalage 0.</span><span class="sxs-lookup"><span data-stu-id="80dde-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="80dde-131">Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien décalage 5.</span><span class="sxs-lookup"><span data-stu-id="80dde-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="80dde-132">Un nouveau décalage de 20 ou plus sera mappé à l’ancien décalage 9.</span><span class="sxs-lookup"><span data-stu-id="80dde-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="80dde-133">Dans le .NET Framework 3,5 et les versions antérieures, vous allouez le `rgILMapEntries` tableau en appelant la méthode [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) .</span><span class="sxs-lookup"><span data-stu-id="80dde-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="80dde-134">Étant donné que le runtime prend possession de cette mémoire, le profileur ne doit pas tenter de le libérer.</span><span class="sxs-lookup"><span data-stu-id="80dde-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="80dde-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="80dde-135">Requirements</span></span>

<span data-ttu-id="80dde-136">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80dde-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="80dde-137">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="80dde-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="80dde-138">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80dde-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="80dde-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80dde-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="80dde-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="80dde-140">See also</span></span>

- [<span data-ttu-id="80dde-141">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="80dde-141">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
