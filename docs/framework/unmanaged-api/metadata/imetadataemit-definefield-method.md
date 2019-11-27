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
ms.openlocfilehash: 40f24a4ea628ce92a27ab1bfe97fc87a57dfa4f0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432547"
---
# <a name="imetadataemitdefinefield-method"></a><span data-ttu-id="429c8-102">IMetaDataEmit::DefineField, méthode</span><span class="sxs-lookup"><span data-stu-id="429c8-102">IMetaDataEmit::DefineField Method</span></span>
<span data-ttu-id="429c8-103">Crée une définition pour un champ avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de champ.</span><span class="sxs-lookup"><span data-stu-id="429c8-103">Creates a definition for a field with the specified metadata signature, and gets a token to that field definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="429c8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="429c8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="429c8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="429c8-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="429c8-106">dans Jeton `mdTypeDef` pour l’interface ou la classe englobante.</span><span class="sxs-lookup"><span data-stu-id="429c8-106">[in] The `mdTypeDef` token for the enclosing class or interface.</span></span>  
  
 `szName`  
 <span data-ttu-id="429c8-107">dans Nom du champ en Unicode.</span><span class="sxs-lookup"><span data-stu-id="429c8-107">[in] The field name in Unicode.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="429c8-108">dans Attributs du champ.</span><span class="sxs-lookup"><span data-stu-id="429c8-108">[in] The field attributes.</span></span> <span data-ttu-id="429c8-109">Il s’agit d’un masque de ré`CorFieldAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="429c8-109">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="429c8-110">dans Signature de champ en tant qu’objet BLOB.</span><span class="sxs-lookup"><span data-stu-id="429c8-110">[in] The field signature as a BLOB.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="429c8-111">dans Nombre d’octets dans `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="429c8-111">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="429c8-112">dans `ELEMENT_TYPE_` *\** pour la valeur de constante.</span><span class="sxs-lookup"><span data-stu-id="429c8-112">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="429c8-113">Il s’agit d’une valeur `CorElementType`.</span><span class="sxs-lookup"><span data-stu-id="429c8-113">This is a `CorElementType` value.</span></span> <span data-ttu-id="429c8-114">Si vous ne définissez pas de valeur de constante pour le champ, utilisez `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="429c8-114">If not defining a constant value for the field, use `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="429c8-115">dans Valeur de constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="429c8-115">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="429c8-116">dans Taille en caractères (Unicode) de `pValue`.</span><span class="sxs-lookup"><span data-stu-id="429c8-116">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
 `pmd`  
 <span data-ttu-id="429c8-117">à Jeton `mdFieldDef` assigné.</span><span class="sxs-lookup"><span data-stu-id="429c8-117">[out] The `mdFieldDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="429c8-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="429c8-118">Requirements</span></span>  
 <span data-ttu-id="429c8-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="429c8-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="429c8-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="429c8-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="429c8-121">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="429c8-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="429c8-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="429c8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429c8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="429c8-123">See also</span></span>

- [<span data-ttu-id="429c8-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="429c8-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="429c8-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="429c8-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
