---
title: IMetaDataEmit::DefineCustomAttribute, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 9c4ed282e259aa46fc0cb0175214dc51d3d5fbee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175887"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="a0933-102">IMetaDataEmit::DefineCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="a0933-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="a0933-103">Crée une définition pour un attribut personnalisé avec la signature spécifiée de métadonnées, à attacher à l’objet spécifié, et obtient un jeton à cette définition d’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a0933-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0933-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0933-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0933-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0933-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="a0933-106">[dans] Le jeton pour l’article propriétaire.</span><span class="sxs-lookup"><span data-stu-id="a0933-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="a0933-107">[dans] Le jeton qui identifie l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a0933-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="a0933-108">[dans] Un pointeur à l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a0933-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="a0933-109">[dans] Le compte d’octets dans `pCustomAttribute`.</span><span class="sxs-lookup"><span data-stu-id="a0933-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="a0933-110">[out] Le `mdCustomAttribute` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="a0933-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0933-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a0933-111">Requirements</span></span>  
 <span data-ttu-id="a0933-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0933-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0933-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="a0933-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0933-114">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0933-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0933-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0933-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0933-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0933-116">See also</span></span>

- [<span data-ttu-id="a0933-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a0933-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a0933-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a0933-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
