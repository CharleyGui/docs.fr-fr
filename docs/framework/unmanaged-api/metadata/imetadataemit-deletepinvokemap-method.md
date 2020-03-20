---
title: IMetaDataEmit::DeletePinvokeMap, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 45f40dcd419e8e2fdf8a3349ccc9461854ad9aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175731"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="937ba-102">IMetaDataEmit::DeletePinvokeMap, méthode</span><span class="sxs-lookup"><span data-stu-id="937ba-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="937ba-103">Détruit les métadonnées de cartographie PInvoke pour l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="937ba-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="937ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="937ba-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="937ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="937ba-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="937ba-106">[dans] Un `mdFieldDef` `mdMethodDef` ou un jeton qui représente l’objet pour lequel supprimer les métadonnées de cartographie PInvoke.</span><span class="sxs-lookup"><span data-stu-id="937ba-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="937ba-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="937ba-107">Requirements</span></span>  
 <span data-ttu-id="937ba-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="937ba-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="937ba-109">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="937ba-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="937ba-110">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="937ba-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="937ba-111">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="937ba-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="937ba-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="937ba-112">See also</span></span>

- [<span data-ttu-id="937ba-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="937ba-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="937ba-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="937ba-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
