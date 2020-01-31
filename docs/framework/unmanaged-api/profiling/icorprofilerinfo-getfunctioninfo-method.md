---
title: ICorProfilerInfo::GetFunctionInfo, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: 823cc5638ff3e0955aca0bd9ba5795f6b369c6b0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863619"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="a9cff-102">ICorProfilerInfo::GetFunctionInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="a9cff-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="a9cff-103">Obtient la classe parente et le jeton de métadonnées pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a9cff-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9cff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9cff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9cff-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="a9cff-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a9cff-106">dans ID de la fonction pour laquelle obtenir la classe parente et le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="a9cff-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="a9cff-107">[out] Pointeur vers la classe parente de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a9cff-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="a9cff-108">[out] Pointeur vers le module dans lequel la classe parente de la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="a9cff-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="a9cff-109">[out] Pointeur vers le jeton de métadonnées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a9cff-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9cff-110">Notes</span><span class="sxs-lookup"><span data-stu-id="a9cff-110">Remarks</span></span>  
 <span data-ttu-id="a9cff-111">Le code du profileur peut appeler [ICorProfilerInfo :: GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) pour obtenir une interface de métadonnées pour un module donné.</span><span class="sxs-lookup"><span data-stu-id="a9cff-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="a9cff-112">Le jeton de métadonnées qui est retourné à l'emplacement référencé par `pToken` peut alors servir à accéder aux métadonnées pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="a9cff-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="a9cff-113">La `ClassID` d’une fonction sur une classe générique peut ne pas pouvoir être obtenue sans plus d’informations contextuelles sur l’utilisation de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a9cff-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="a9cff-114">Dans ce cas, `pClassId` est égal à 0.</span><span class="sxs-lookup"><span data-stu-id="a9cff-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="a9cff-115">Le code du profileur doit utiliser [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) avec une valeur COR_PRF_FRAME_INFO pour fournir davantage de contexte.</span><span class="sxs-lookup"><span data-stu-id="a9cff-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9cff-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="a9cff-116">Requirements</span></span>  
 <span data-ttu-id="a9cff-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9cff-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9cff-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9cff-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9cff-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9cff-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9cff-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9cff-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9cff-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9cff-121">See also</span></span>

- [<span data-ttu-id="a9cff-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="a9cff-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
