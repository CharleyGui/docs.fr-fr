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
ms.openlocfilehash: d59de04e6af6cfec473899e0a3edadcb3257d385
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665681"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="3adfa-102">ICorProfilerInfo8:: GetDynamicFunctionInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="3adfa-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>

<span data-ttu-id="3adfa-103">Récupère des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="3adfa-103">Retrieves information about dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="3adfa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3adfa-104">Syntax</span></span>

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a><span data-ttu-id="3adfa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3adfa-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="3adfa-106">dans ID de la fonction pour laquelle des informations doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="3adfa-106">[in] The ID of the function for which to retrieve information.</span></span>

`moduleId` \
<span data-ttu-id="3adfa-107">dans Pointeur vers le module dans lequel la classe parente de la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="3adfa-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>

`ppvSig` \
<span data-ttu-id="3adfa-108">à Pointeur vers la signature de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3adfa-108">[out] A pointer to the signature for the function.</span></span>

`pbSig` \
<span data-ttu-id="3adfa-109">à Pointeur vers le nombre d’octets pour la signature de fonction.</span><span class="sxs-lookup"><span data-stu-id="3adfa-109">[out] A pointer to the count of bytes for the function signature.</span></span>

`cchName` \
<span data-ttu-id="3adfa-110">[in] Taille maximale du tableau `wszName`.</span><span class="sxs-lookup"><span data-stu-id="3adfa-110">[in] The maximum size of the `wszName` array.</span></span>

`pcchName` \
<span data-ttu-id="3adfa-111">à Nombre de caractères dans le `wszName` tableau.</span><span class="sxs-lookup"><span data-stu-id="3adfa-111">[out] The number of characters in the `wszName` array.</span></span>

`wszName` \
<span data-ttu-id="3adfa-112">à Tableau d `WCHAR` 'qui est le nom de la fonction, s’il en existe un.</span><span class="sxs-lookup"><span data-stu-id="3adfa-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>

## <a name="remarks"></a><span data-ttu-id="3adfa-113">Notes</span><span class="sxs-lookup"><span data-stu-id="3adfa-113">Remarks</span></span>

<span data-ttu-id="3adfa-114">Certaines méthodes telles que les stubs IL ou les LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API [IMetaDataImport](../metadata/imetadataimport-interface.md) et [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3adfa-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="3adfa-115">Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="3adfa-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

<span data-ttu-id="3adfa-116">Cette API peut être utilisée pour récupérer des informations sur les méthodes dynamiques, y compris un nom convivial, si disponible.</span><span class="sxs-lookup"><span data-stu-id="3adfa-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>

## <a name="requirements"></a><span data-ttu-id="3adfa-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3adfa-117">Requirements</span></span>

<span data-ttu-id="3adfa-118">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3adfa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="3adfa-119">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3adfa-119">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="3adfa-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3adfa-120">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3adfa-121">**Versions de .NET Framework:** [! INCLURE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="3adfa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="3adfa-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3adfa-122">See also</span></span>

- [<span data-ttu-id="3adfa-123">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="3adfa-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
