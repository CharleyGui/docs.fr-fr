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
ms.openlocfilehash: d924dbf21a0f0b046c8d8f8f294e91bc5ff6c015
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869409"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="d2318-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="d2318-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="d2318-103">Obtient le jeton de métadonnées et une instance d’interface de métadonnées qui peuvent être utilisés par rapport au jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2318-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2318-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2318-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2318-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d2318-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d2318-106">dans ID de la fonction pour laquelle obtenir le jeton de métadonnées et l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d2318-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="d2318-107">dans ID de référence de l’interface de métadonnées pour l’extraction de l’instance de.</span><span class="sxs-lookup"><span data-stu-id="d2318-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="d2318-108">à Pointeur vers l’adresse de l’instance d’interface de métadonnées qui peut être utilisée par rapport au jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2318-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="d2318-109">à Pointeur vers le jeton de métadonnées pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2318-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2318-110">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d2318-110">Requirements</span></span>  
 <span data-ttu-id="d2318-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2318-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2318-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d2318-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d2318-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2318-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2318-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2318-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2318-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2318-115">See also</span></span>

- [<span data-ttu-id="d2318-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="d2318-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
