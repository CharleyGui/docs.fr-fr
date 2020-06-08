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
ms.openlocfilehash: 1cc05f4c10f4a5b042ff14c05f3c85a7b5935184
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497892"
---
# <a name="icorprofilerinfogettokenandmetadatafromfunction-method"></a><span data-ttu-id="66947-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="66947-102">ICorProfilerInfo::GetTokenAndMetadataFromFunction Method</span></span>
<span data-ttu-id="66947-103">Obtient le jeton de métadonnées et une instance d’interface de métadonnées qui peuvent être utilisés par rapport au jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="66947-103">Gets the metadata token and a metadata interface instance that can be used against the token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66947-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66947-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenAndMetaDataFromFunction(  
    [in]  FunctionID functionId,  
    [in]  REFIID     riid,  
    [out] IUnknown   **ppImport,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66947-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66947-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="66947-106">dans ID de la fonction pour laquelle obtenir le jeton de métadonnées et l’interface de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="66947-106">[in] The ID of the function for which to get the metadata token and metadata interface.</span></span>  
  
 `riid`  
 <span data-ttu-id="66947-107">dans ID de référence de l’interface de métadonnées pour l’extraction de l’instance de.</span><span class="sxs-lookup"><span data-stu-id="66947-107">[in] The reference ID of the metadata interface to get the instance of.</span></span>  
  
 `ppImport`  
 <span data-ttu-id="66947-108">à Pointeur vers l’adresse de l’instance d’interface de métadonnées qui peut être utilisée par rapport au jeton pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="66947-108">[out] A pointer to the address of the metadata interface instance that can be used against the token for the specified function.</span></span>  
  
 `pToken`  
 <span data-ttu-id="66947-109">à Pointeur vers le jeton de métadonnées pour la fonction spécifiée.</span><span class="sxs-lookup"><span data-stu-id="66947-109">[out] A pointer to the metadata token for the specified function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66947-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66947-110">Requirements</span></span>  
 <span data-ttu-id="66947-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66947-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66947-112">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="66947-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="66947-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66947-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66947-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66947-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66947-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66947-115">See also</span></span>

- [<span data-ttu-id="66947-116">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="66947-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
