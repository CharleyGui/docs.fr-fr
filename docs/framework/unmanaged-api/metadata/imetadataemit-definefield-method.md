---
title: IMetaDataEmit::DefineField, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineField
helpviewer_keywords:
- IMetaDataEmit::DefineField method [.NET Framework metadata]
- DefineField method, IMetaDataEmit interface [.NET Framework metadata
ms.assetid: 6b5be4fc-2e86-499c-8b09-833160bca767
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 057bae1d702fa091ebc3d3178c9fba35d5dd3d90
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777656"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="78ac4-102">IMetaDataEmit::DefineField, méthode</span><span class="sxs-lookup"><span data-stu-id="78ac4-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="78ac4-103">Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.</span><span class="sxs-lookup"><span data-stu-id="78ac4-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ac4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78ac4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineField (   
    [in]  mdTypeDef   td,   
    [in]  LPCWSTR     szName,   
    [in]  DWORD       dwFieldFlags,   
    [in]  PCCOR_SIGNATURE pvSigBlob,   
    [in]  ULONG       cbSigBlob,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue,   
    [out] mdFieldDef  *pmd   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78ac4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78ac4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="78ac4-106">[in] Le `mdTypeDef` jeton pour l’interface ou la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="78ac4-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="78ac4-107">[in] Le nom du champ au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="78ac4-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="78ac4-108">[in] Les attributs de champ.</span><span class="sxs-lookup"><span data-stu-id="78ac4-108">[in] The field attributes.</span></span> <span data-ttu-id="78ac4-109">Il s’agit d’un masque de bits de `CorFieldAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="78ac4-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="78ac4-110">[in] La signature de champ comme un objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="78ac4-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="78ac4-111">[in] Le nombre d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="78ac4-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="78ac4-112">[in] Le `ELEMENT_TYPE_` *\** pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="78ac4-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="78ac4-113">Il s’agit d’un `CorElementType` valeur.</span><span class="sxs-lookup"><span data-stu-id="78ac4-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="78ac4-114">Si vous ne définissez pas une valeur constante pour le champ, utilisez `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="78ac4-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="78ac4-115">[in] La valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="78ac4-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="78ac4-116">[in] La taille en caractères (Unicode) de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="78ac4-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="78ac4-117">[out] Le `mdFieldDef` jeton attribué.</span><span class="sxs-lookup"><span data-stu-id="78ac4-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78ac4-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="78ac4-118">Requirements</span></span>  
 <span data-ttu-id="78ac4-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78ac4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78ac4-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="78ac4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="78ac4-121">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78ac4-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78ac4-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78ac4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ac4-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78ac4-123">See also</span></span>

- [<span data-ttu-id="78ac4-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="78ac4-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="78ac4-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="78ac4-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
