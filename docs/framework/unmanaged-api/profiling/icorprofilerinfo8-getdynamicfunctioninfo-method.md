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
ms.openlocfilehash: 90246ade67f797c04f0da5d9a68dadb83e4ce418
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973859"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="220af-102">ICorProfilerInfo8:: GetDynamicFunctionInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="220af-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>
  
 <span data-ttu-id="220af-103">Récupère des informations sur les méthodes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="220af-103">Retrieves information about dynamic methods.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="220af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="220af-104">Syntax</span></span>  
  
```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="220af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="220af-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="220af-106">dans ID de la fonction pour laquelle des informations doivent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="220af-106">[in] The ID of the function for which to retrieve information.</span></span>  

 `moduleId`  
 <span data-ttu-id="220af-107">dans Pointeur vers le module dans lequel la classe parente de la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="220af-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="220af-108">à Pointeur vers la signature de la fonction.</span><span class="sxs-lookup"><span data-stu-id="220af-108">[out] A pointer to the signature for the function.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="220af-109">à Pointeur vers le nombre d’octets pour la signature de fonction.</span><span class="sxs-lookup"><span data-stu-id="220af-109">[out] A pointer to the count of bytes for the function signature.</span></span>
  
 `cchName`  
 <span data-ttu-id="220af-110">[in] Taille maximale du tableau `wszName`.</span><span class="sxs-lookup"><span data-stu-id="220af-110">[in] The maximum size of the `wszName` array.</span></span>
  
 `pcchName`  
 <span data-ttu-id="220af-111">à Nombre de caractères dans le `wszName` tableau.</span><span class="sxs-lookup"><span data-stu-id="220af-111">[out] The number of characters in the `wszName` array.</span></span>

 `wszName` \
 <span data-ttu-id="220af-112">à Tableau d `WCHAR` 'qui est le nom de la fonction, s’il en existe un.</span><span class="sxs-lookup"><span data-stu-id="220af-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="220af-113">Notes</span><span class="sxs-lookup"><span data-stu-id="220af-113">Remarks</span></span>  
 <span data-ttu-id="220af-114">Certaines méthodes telles que les stubs IL ou les LCG n’ont pas de métadonnées associées qui peuvent être récupérées à l’aide des API [IMetaDataImport](../metadata/imetadataimport-interface.md) et [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="220af-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="220af-115">Ces méthodes peuvent être rencontrées par les profileurs par le biais de pointeurs d’instruction ou en écoutant [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="220af-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

 <span data-ttu-id="220af-116">Cette API peut être utilisée pour récupérer des informations sur les méthodes dynamiques, y compris un nom convivial, si disponible.</span><span class="sxs-lookup"><span data-stu-id="220af-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>  
  

## <a name="requirements"></a><span data-ttu-id="220af-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="220af-117">Requirements</span></span>  
 <span data-ttu-id="220af-118">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="220af-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="220af-119">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="220af-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="220af-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="220af-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="220af-121">**Versions de .NET Framework:** [! INCLURE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="220af-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="220af-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="220af-122">See also</span></span>
- [<span data-ttu-id="220af-123">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="220af-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

