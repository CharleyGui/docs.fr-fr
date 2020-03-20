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
ms.openlocfilehash: 8ca5ab70f60de4d783800fb18612a8f04cb9cee1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177711"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="15656-102">IMetaDataEmit::DefineField, méthode</span><span class="sxs-lookup"><span data-stu-id="15656-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="15656-103">Crée une définition pour un champ avec la signature spécifiée de métadonnées, et obtient un jeton à cette définition de champ.</span><span class="sxs-lookup"><span data-stu-id="15656-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15656-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15656-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="15656-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="15656-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="15656-106">[dans] Le `mdTypeDef` jeton pour la classe ou l’interface d’enceinte.</span><span class="sxs-lookup"><span data-stu-id="15656-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="15656-107">[dans] Le nom de champ dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="15656-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="15656-108">[dans] Le champ attribue.</span><span class="sxs-lookup"><span data-stu-id="15656-108">[in] The field attributes.</span></span> <span data-ttu-id="15656-109">C’est un peu `CorFieldAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="15656-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="15656-110">[dans] La signature de champ comme un BLOB.</span><span class="sxs-lookup"><span data-stu-id="15656-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="15656-111">[dans] Le compte d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="15656-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="15656-112">[dans] Le `ELEMENT_TYPE_` *\** pour la valeur constante.</span><span class="sxs-lookup"><span data-stu-id="15656-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="15656-113">C’est `CorElementType` une valeur.</span><span class="sxs-lookup"><span data-stu-id="15656-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="15656-114">Si ce n’est pas définir `ELEMENT_TYPE_END`une valeur constante pour le champ, utilisez .</span><span class="sxs-lookup"><span data-stu-id="15656-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="15656-115">[dans] La valeur constante pour le domaine.</span><span class="sxs-lookup"><span data-stu-id="15656-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="15656-116">[dans] La taille dans (Unicode) caractères de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="15656-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="15656-117">[out] Le `mdFieldDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="15656-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15656-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="15656-118">Requirements</span></span>  
 <span data-ttu-id="15656-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15656-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15656-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="15656-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15656-121">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15656-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15656-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15656-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15656-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="15656-123">See also</span></span>

- [<span data-ttu-id="15656-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="15656-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="15656-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="15656-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
