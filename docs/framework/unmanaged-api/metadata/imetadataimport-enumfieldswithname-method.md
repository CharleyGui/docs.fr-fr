---
title: IMetaDataImport::EnumFieldsWithName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: bb8b531a884c9d3c2f33aa4aec5c4dbeaafe2b66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177342"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="676f1-102">IMetaDataImport::EnumFieldsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="676f1-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="676f1-103">Énumère les jetons FieldDef du type spécifié avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="676f1-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="676f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="676f1-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="676f1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="676f1-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="676f1-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="676f1-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="676f1-107">[dans] Le jeton du type dont les champs doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="676f1-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="676f1-108">[dans] Le nom de champ qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="676f1-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="676f1-109">[out] Array utilisé pour stocker les jetons FieldDef.</span><span class="sxs-lookup"><span data-stu-id="676f1-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="676f1-110">[in] Taille maximale du tableau `rFields`.</span><span class="sxs-lookup"><span data-stu-id="676f1-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="676f1-111">[out] Le nombre réel de jetons FieldDef retourné dans `rFields`.</span><span class="sxs-lookup"><span data-stu-id="676f1-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="676f1-112">Notes </span><span class="sxs-lookup"><span data-stu-id="676f1-112">Remarks</span></span>  
 <span data-ttu-id="676f1-113">Contrairement à [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` jette tous les jetons de champ qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="676f1-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="676f1-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="676f1-114">Return Value</span></span>  
  
|<span data-ttu-id="676f1-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="676f1-115">HRESULT</span></span>|<span data-ttu-id="676f1-116">Description</span><span class="sxs-lookup"><span data-stu-id="676f1-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="676f1-117">`EnumFieldsWithName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="676f1-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="676f1-118">Il n’y a pas de champs à énumérer.</span><span class="sxs-lookup"><span data-stu-id="676f1-118">There are no fields to enumerate.</span></span> <span data-ttu-id="676f1-119">Dans ce `pcTokens` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="676f1-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="676f1-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="676f1-120">Requirements</span></span>  
 <span data-ttu-id="676f1-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="676f1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="676f1-122">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="676f1-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="676f1-123">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="676f1-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="676f1-124">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="676f1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676f1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="676f1-125">See also</span></span>

- [<span data-ttu-id="676f1-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="676f1-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="676f1-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="676f1-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
