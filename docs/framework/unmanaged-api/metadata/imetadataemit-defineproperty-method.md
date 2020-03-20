---
title: IMetaDataEmit::DefineProperty, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineProperty
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineProperty
helpviewer_keywords:
- IMetaDataEmit::DefineProperty method [.NET Framework metadata]
- DefineProperty method [.NET Framework metadata]
ms.assetid: 5c4c1dc2-d40d-4173-bbe6-7058fb21c98f
topic_type:
- apiref
ms.openlocfilehash: eb3ecbf39376e7126b5ec93a26badcbf5076d1db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175783"
---
# <a name="imetadataemitdefineproperty-method"></a><span data-ttu-id="9260d-102">IMetaDataEmit::DefineProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="9260d-102">IMetaDataEmit::DefineProperty Method</span></span>
<span data-ttu-id="9260d-103">Crée une définition de propriété pour `get` le `set` type spécifié, avec les accesseurs spécifiés et la méthode, et obtient un jeton à cette définition de propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-103">Creates a property definition for the specified type, with the specified `get` and `set` method accessors, and gets a token to that property definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9260d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9260d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineProperty (
    [in]  mdTypeDef          td,
    [in]  LPCWSTR            szProperty,
    [in]  DWORD              dwPropFlags,
    [in]  PCCOR_SIGNATURE    pvSig,
    [in]  ULONG              cbSig,
    [in]  DWORD              dwCPlusTypeFlag,
    [in]  void const         *pValue,
    [in]  ULONG              cchValue,
    [in]  mdMethodDef        mdSetter,
    [in]  mdMethodDef        mdGetter,
    [in]  mdMethodDef        rmdOtherMethods[],
    [out] mdProperty         *pmdProp
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9260d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9260d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="9260d-106">[dans] Le jeton pour la classe ou l’interface sur laquelle la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="9260d-106">[in] The token for class or interface on which the property is being defined.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="9260d-107">[in] Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-107">[in] The name of the property.</span></span>  
  
 `dwPropFlags`  
 <span data-ttu-id="9260d-108">[dans] Les drapeaux de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-108">[in] The property flags.</span></span>  
  
 `pvSig`  
 <span data-ttu-id="9260d-109">[dans] La signature de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-109">[in] The property signature.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="9260d-110">[dans] Le compte d’octets dans `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="9260d-110">[in] The count of bytes in `pvSig`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="9260d-111">[dans] Le type de valeur par défaut de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-111">[in] The type of the property's default value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="9260d-112">[dans] La valeur par défaut pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-112">[in] The default value for the property.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="9260d-113">[dans] Le nombre de caractères `pValue`(Unicode) dans .</span><span class="sxs-lookup"><span data-stu-id="9260d-113">[in] The count of (Unicode) characters in `pValue`.</span></span>  
  
 `mdSetter`  
 <span data-ttu-id="9260d-114">[dans] La méthode qui définit la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-114">[in] The method that sets the property value.</span></span>  
  
 `mdGetter`  
 <span data-ttu-id="9260d-115">[dans] La méthode qui obtient la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-115">[in] The method that gets the property value.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="9260d-116">[dans] Un éventail d’autres méthodes associées à la propriété.</span><span class="sxs-lookup"><span data-stu-id="9260d-116">[in] An array of other methods associated with the property.</span></span> <span data-ttu-id="9260d-117">Terminez le `mdTokenNil`tableau avec un .</span><span class="sxs-lookup"><span data-stu-id="9260d-117">Terminate the array with an `mdTokenNil`.</span></span>  
  
 `pmdProp`  
 <span data-ttu-id="9260d-118">[out] Le `mdProperty` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="9260d-118">[out] The `mdProperty` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9260d-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9260d-119">Requirements</span></span>  
 <span data-ttu-id="9260d-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9260d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9260d-121">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="9260d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9260d-122">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9260d-122">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9260d-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9260d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9260d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9260d-124">See also</span></span>

- [<span data-ttu-id="9260d-125">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9260d-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9260d-126">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9260d-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
