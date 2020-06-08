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
ms.openlocfilehash: 68261b165847a5c3ee29adbc4908451fb00c5443
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492263"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="95ed0-102">IMetaDataImport::EnumFieldsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="95ed0-102">IMetaDataImport::EnumFieldsWithName Method</span></span>
<span data-ttu-id="95ed0-103">Énumère les jetons FieldDef du type spécifié avec le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="95ed0-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95ed0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95ed0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="95ed0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="95ed0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="95ed0-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="95ed0-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="95ed0-107">dans Jeton du type dont les champs doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="95ed0-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="95ed0-108">dans Nom du champ qui limite la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="95ed0-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="95ed0-109">à Tableau utilisé pour stocker les jetons FieldDef.</span><span class="sxs-lookup"><span data-stu-id="95ed0-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="95ed0-110">[in] Taille maximale du tableau `rFields`.</span><span class="sxs-lookup"><span data-stu-id="95ed0-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="95ed0-111">à Nombre réel de jetons FieldDef retournés dans `rFields` .</span><span class="sxs-lookup"><span data-stu-id="95ed0-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95ed0-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="95ed0-112">Remarks</span></span>  
 <span data-ttu-id="95ed0-113">Contrairement à [IMetaDataImport :: EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` ignore tous les jetons de champ qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="95ed0-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95ed0-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="95ed0-114">Return Value</span></span>  
  
|<span data-ttu-id="95ed0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="95ed0-115">HRESULT</span></span>|<span data-ttu-id="95ed0-116">Description</span><span class="sxs-lookup"><span data-stu-id="95ed0-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="95ed0-117">`EnumFieldsWithName`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="95ed0-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="95ed0-118">Il n’y a aucun champ à énumérer.</span><span class="sxs-lookup"><span data-stu-id="95ed0-118">There are no fields to enumerate.</span></span> <span data-ttu-id="95ed0-119">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="95ed0-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="95ed0-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="95ed0-120">Requirements</span></span>  
 <span data-ttu-id="95ed0-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95ed0-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95ed0-122">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="95ed0-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="95ed0-123">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95ed0-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="95ed0-124">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95ed0-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ed0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95ed0-125">See also</span></span>

- [<span data-ttu-id="95ed0-126">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="95ed0-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="95ed0-127">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="95ed0-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
