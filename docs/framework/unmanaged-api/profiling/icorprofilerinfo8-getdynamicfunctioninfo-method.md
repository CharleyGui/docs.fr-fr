---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: eaf33f3b0de7a18e400cd16d29c046784e2e190f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495318"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="a67b8-102">ICorProfilerInfo8 :: GetDynamicFunctionInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="a67b8-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="a67b8-103">Récupère des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="a67b8-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="a67b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a67b8-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a><span data-ttu-id="a67b8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a67b8-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="a67b8-106">\[in] ID de la fonction pour laquelle des informations doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="a67b8-106">\[in] The ID of the function for which to retrieve information.</span></span>

- `moduleId`

  <span data-ttu-id="a67b8-107">\[in] pointeur vers le module dans lequel la classe parente de la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="a67b8-107">\[in] A pointer to the module in which the function's parent class is defined.</span></span>

- `ppvSig`

  <span data-ttu-id="a67b8-108">\[out] pointeur vers la signature de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a67b8-108">\[out] A pointer to the signature for the function.</span></span>

- `pbSig`

  <span data-ttu-id="a67b8-109">\[out] pointeur vers le nombre d’octets pour la signature de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a67b8-109">\[out] A pointer to the count of bytes for the function signature.</span></span>

- `cchName`

  <span data-ttu-id="a67b8-110">\[in] taille maximale du `wszName` tableau.</span><span class="sxs-lookup"><span data-stu-id="a67b8-110">\[in] The maximum size of the `wszName` array.</span></span>

- `pcchName`

  <span data-ttu-id="a67b8-111">\[out] nombre de caractères dans le `wszName` tableau.</span><span class="sxs-lookup"><span data-stu-id="a67b8-111">\[out] The number of characters in the `wszName` array.</span></span>

- `wszName`

  <span data-ttu-id="a67b8-112">\[out] tableau de `WCHAR` qui est le nom de la fonction, s’il en existe un.</span><span class="sxs-lookup"><span data-stu-id="a67b8-112">\[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="a67b8-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="a67b8-113">Remarks</span></span>

<span data-ttu-id="a67b8-114">Certaines méthodes telles que les stubs IL ou les LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API [IMetaDataImport](../metadata/imetadataimport-interface.md) et [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a67b8-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="a67b8-115">Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback8 ::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="a67b8-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="a67b8-116">Cette API peut être utilisée pour récupérer des informations sur les méthodes dynamiques, y compris un nom convivial, si disponible.</span><span class="sxs-lookup"><span data-stu-id="a67b8-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="a67b8-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a67b8-117">Requirements</span></span>

<span data-ttu-id="a67b8-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a67b8-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a67b8-119">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a67b8-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="a67b8-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a67b8-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="a67b8-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a67b8-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a67b8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a67b8-122">See also</span></span>

- [<span data-ttu-id="a67b8-123">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="a67b8-123">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)
