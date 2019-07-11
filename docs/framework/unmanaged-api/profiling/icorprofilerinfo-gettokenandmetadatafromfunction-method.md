---
title: ICorProfilerInfo::GetTokenAndMetadataFromFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetTokenAndMetadataFromFunction
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction
helpviewer_keywords:
- ICorProfilerInfo::GetTokenAndMetadataFromFunction method [.NET Framework profiling]
- GetTokenAndMetadataFromFunction method [.NET Framework profiling]
ms.assetid: e525aa16-c923-4b16-833b-36f1f0dd70fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b608b8818890bdb27a956a90c7987cf7c421304d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772274"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="839c5-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="839c5-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="839c5-103">Obtient le jeton de métadonnées et une instance d’interface de métadonnées qui permettre être utilisée avec le jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="839c5-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839c5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="839c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="839c5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="839c5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="839c5-106">[in] L’ID de la fonction pour laquelle obtenir le jeton de métadonnées et l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="839c5-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="839c5-107">[in] L’ID de référence de l’interface de métadonnées pour obtenir l’instance de.</span><span class="sxs-lookup"><span data-stu-id="839c5-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="839c5-108">[out] Pointeur vers l’adresse de l’instance d’interface de métadonnées qui permettre être utilisé avec le jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="839c5-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="839c5-109">[out] Pointeur vers le jeton de métadonnées pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="839c5-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="839c5-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="839c5-110">Requirements</span></span>  
 <span data-ttu-id="839c5-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="839c5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="839c5-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="839c5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="839c5-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="839c5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="839c5-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="839c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839c5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="839c5-115">See also</span></span>

- [<span data-ttu-id="839c5-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="839c5-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
