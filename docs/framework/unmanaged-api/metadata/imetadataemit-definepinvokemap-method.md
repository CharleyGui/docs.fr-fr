---
title: IMetaDataEmit::DefinePinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
ms.openlocfilehash: e414bc5a7d537e8d153541f05b22dd91578e8739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177754"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="c339e-102">IMetaDataEmit::DefinePinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="c339e-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="c339e-103">Définit les caractéristiques de la signature PInvoke de la méthode référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="c339e-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c339e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c339e-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c339e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c339e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c339e-106">[dans] Le jeton pour la méthode cible.</span><span class="sxs-lookup"><span data-stu-id="c339e-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="c339e-107">[dans] Drapeaux utilisés par PInvoke pour faire la cartographie.</span><span class="sxs-lookup"><span data-stu-id="c339e-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="c339e-108">[dans] Le nom de la méthode d’exportation cible dans un DLL non menté.</span><span class="sxs-lookup"><span data-stu-id="c339e-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="c339e-109">[dans] Le jeton pour la cible indigène DLL.</span><span class="sxs-lookup"><span data-stu-id="c339e-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c339e-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c339e-110">Requirements</span></span>  
 <span data-ttu-id="c339e-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c339e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c339e-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="c339e-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c339e-113">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c339e-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c339e-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c339e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c339e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c339e-115">See also</span></span>

- [<span data-ttu-id="c339e-116">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c339e-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c339e-117">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="c339e-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
