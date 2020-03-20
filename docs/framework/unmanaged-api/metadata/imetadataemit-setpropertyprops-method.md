---
title: IMetaDataEmit::SetPropertyProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPropertyProps
helpviewer_keywords:
- SetPropertyProps method [.NET Framework metadata]
- IMetaDataEmit::SetPropertyProps method [.NET Framework metadata]
ms.assetid: e2501fc8-b2bc-4dcc-9205-e3acd5a53ffe
topic_type:
- apiref
ms.openlocfilehash: dc6375f3e2cff1a744a8ff2e6a6adab27bbf8af3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177480"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="4728e-102">IMetaDataEmit::SetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="4728e-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="4728e-103">Définit les fonctionnalités stockées dans les métadonnées pour une propriété définie par un appel préalable à [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="4728e-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4728e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4728e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPropertyProps (
    [in]  mdProperty      pr,
    [in]  DWORD           dwPropFlags,
    [in]  DWORD           dwCPlusTypeFlag,
    [in]  void const      *pValue,
    [in]  ULONG           cchValue,
    [in]  mdMethodDef     mdSetter,
    [in]  mdMethodDef     mdGetter,
    [in]  mdMethodDef     rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4728e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4728e-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="4728e-106">[dans] Le jeton pour que la propriété soit changée</span><span class="sxs-lookup"><span data-stu-id="4728e-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="4728e-107">[dans] Drapeaux de propriété.</span><span class="sxs-lookup"><span data-stu-id="4728e-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="4728e-108">[dans] Le type de valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="4728e-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="4728e-109">[dans] La valeur par défaut pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="4728e-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="4728e-110">[dans] Le nombre de caractères `pValue`(Unicode) dans .</span><span class="sxs-lookup"><span data-stu-id="4728e-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="4728e-111">[dans] La méthode qui définit la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="4728e-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="4728e-112">[dans] La méthode qui obtient la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="4728e-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="4728e-113">[dans] Un éventail d’autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="4728e-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="4728e-114">Terminez ce `mdTokenNil` tableau avec un jeton.</span><span class="sxs-lookup"><span data-stu-id="4728e-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4728e-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4728e-115">Requirements</span></span>  
 <span data-ttu-id="4728e-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4728e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4728e-117">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4728e-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4728e-118">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4728e-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4728e-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4728e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4728e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4728e-120">See also</span></span>

- [<span data-ttu-id="4728e-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4728e-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4728e-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="4728e-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
