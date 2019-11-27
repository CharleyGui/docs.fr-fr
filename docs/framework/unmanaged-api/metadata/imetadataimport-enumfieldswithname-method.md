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
ms.openlocfilehash: b240be3e5b0127de42cea43dd8e89a2cc656b28e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449513"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="c1267-102">IMetaDataImport::EnumFieldsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="c1267-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="c1267-103">Énumère les jetons FieldDef du type spécifié avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="c1267-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1267-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1267-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c1267-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1267-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c1267-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c1267-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="c1267-107">dans Jeton du type dont les champs doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="c1267-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="c1267-108">dans Nom du champ qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c1267-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="c1267-109">à Tableau utilisé pour stocker les jetons FieldDef.</span><span class="sxs-lookup"><span data-stu-id="c1267-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c1267-110">[in] Taille maximale du tableau `rFields`.</span><span class="sxs-lookup"><span data-stu-id="c1267-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c1267-111">à Nombre réel de jetons FieldDef retournés dans `rFields`.</span><span class="sxs-lookup"><span data-stu-id="c1267-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1267-112">Notes</span><span class="sxs-lookup"><span data-stu-id="c1267-112">Remarks</span></span>  
 <span data-ttu-id="c1267-113">Contrairement à [IMetaDataImport :: EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` ignore tous les jetons de champ qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="c1267-113">Unlike [IMetaDataImport::EnumFields](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1267-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1267-114">Return Value</span></span>  
  
|<span data-ttu-id="c1267-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1267-115">HRESULT</span></span>|<span data-ttu-id="c1267-116">Description</span><span class="sxs-lookup"><span data-stu-id="c1267-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c1267-117">`EnumFieldsWithName` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c1267-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c1267-118">Il n’y a aucun champ à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c1267-118">There are no fields to enumerate.</span></span> <span data-ttu-id="c1267-119">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="c1267-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c1267-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1267-120">Requirements</span></span>  
 <span data-ttu-id="c1267-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1267-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1267-122">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1267-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1267-123">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c1267-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1267-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1267-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1267-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1267-125">See also</span></span>

- [<span data-ttu-id="c1267-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c1267-126">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c1267-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c1267-127">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
