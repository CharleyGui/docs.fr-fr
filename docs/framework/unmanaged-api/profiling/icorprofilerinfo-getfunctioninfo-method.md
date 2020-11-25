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
ms.openlocfilehash: 6aaa02d72dd10fe72d773246d55216143786dabb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722534"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="07566-102">ICorProfilerInfo::GetFunctionInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="07566-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>

<span data-ttu-id="07566-103">Obtient la classe parente et le jeton de métadonnées pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="07566-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07566-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07566-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07566-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="07566-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="07566-106">dans ID de la fonction pour laquelle obtenir la classe parente et le jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="07566-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="07566-107">[out] Pointeur vers la classe parente de la fonction.</span><span class="sxs-lookup"><span data-stu-id="07566-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="07566-108">[out] Pointeur vers le module dans lequel la classe parente de la fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="07566-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="07566-109">[out] Pointeur vers le jeton de métadonnées de la fonction.</span><span class="sxs-lookup"><span data-stu-id="07566-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07566-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="07566-110">Remarks</span></span>  

 <span data-ttu-id="07566-111">Le code du profileur peut appeler [ICorProfilerInfo :: GetModuleMetaData,](icorprofilerinfo-getmodulemetadata-method.md) pour obtenir une interface de métadonnées pour un module donné.</span><span class="sxs-lookup"><span data-stu-id="07566-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="07566-112">Le jeton de métadonnées qui est retourné à l'emplacement référencé par `pToken` peut alors servir à accéder aux métadonnées pour la fonction.</span><span class="sxs-lookup"><span data-stu-id="07566-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="07566-113">Le `ClassID` d’une fonction sur une classe générique peut ne pas pouvoir être obtenu sans plus d’informations contextuelles sur l’utilisation de la fonction.</span><span class="sxs-lookup"><span data-stu-id="07566-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="07566-114">Dans ce cas, `pClassId` est égal à 0.</span><span class="sxs-lookup"><span data-stu-id="07566-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="07566-115">Le code du profileur doit utiliser [ICorProfilerInfo2 :: GetFunctionInfo2,](icorprofilerinfo2-getfunctioninfo2-method.md) avec une valeur COR_PRF_FRAME_INFO pour fournir davantage de contexte.</span><span class="sxs-lookup"><span data-stu-id="07566-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07566-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="07566-116">Requirements</span></span>  

 <span data-ttu-id="07566-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07566-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07566-118">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07566-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07566-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07566-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07566-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07566-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07566-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07566-121">See also</span></span>

- [<span data-ttu-id="07566-122">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="07566-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
