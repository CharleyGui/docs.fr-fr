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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9e78c4d7319a931ca7090d6f99651bc9660e4af8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782053"
---
# <a name="imetadataemitsetpropertyprops-method"></a><span data-ttu-id="00fcb-102">IMetaDataEmit::SetPropertyProps, méthode</span><span class="sxs-lookup"><span data-stu-id="00fcb-102">IMetaDataEmit::SetPropertyProps Method</span></span>
<span data-ttu-id="00fcb-103">Définit les fonctionnalités stockées dans les métadonnées pour une propriété définie par un appel antérieur à [DefineProperty, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span><span class="sxs-lookup"><span data-stu-id="00fcb-103">Sets the features stored in metadata for a property defined by a prior call to [DefineProperty Method](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00fcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00fcb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="00fcb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="00fcb-105">Parameters</span></span>  
 `pr`  
 <span data-ttu-id="00fcb-106">[in] Le jeton pour la propriété à modifier</span><span class="sxs-lookup"><span data-stu-id="00fcb-106">[in] The token for the property to be changed</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="00fcb-107">[in] Indicateurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="00fcb-107">[in] Property flags.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="00fcb-108">[in] Le type de la valeur de propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="00fcb-108">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="00fcb-109">[in] La valeur par défaut pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="00fcb-109">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="00fcb-110">[in] Le nombre de caractères (Unicode) les caractères de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="00fcb-110">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="00fcb-111">[in] La méthode qui définit la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="00fcb-111">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="00fcb-112">[in] La méthode qui obtient la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="00fcb-112">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="00fcb-113">[in] Tableau des autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="00fcb-113">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="00fcb-114">Mettre fin à ce tableau avec un `mdTokenNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="00fcb-114">Terminate this array with an `mdTokenNil` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00fcb-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="00fcb-115">Requirements</span></span>  
 <span data-ttu-id="00fcb-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00fcb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00fcb-117">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00fcb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00fcb-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00fcb-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="00fcb-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00fcb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fcb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00fcb-120">See also</span></span>

- [<span data-ttu-id="00fcb-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="00fcb-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="00fcb-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="00fcb-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
