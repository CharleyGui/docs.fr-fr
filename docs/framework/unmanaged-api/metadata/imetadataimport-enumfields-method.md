---
title: IMetaDataImport::EnumFields, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
ms.openlocfilehash: 1ff2dd64dc4797bc485550c30f7204644a3adb47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492276"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="6d524-102">IMetaDataImport::EnumFields, méthode</span><span class="sxs-lookup"><span data-stu-id="6d524-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="6d524-103">Énumère les jetons FieldDef pour le type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="6d524-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d524-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d524-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFields (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   cl,
   [out]     mdFieldDef  rFields[],
   [in]      ULONG       cMax,
   [out]     ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d524-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d524-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="6d524-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="6d524-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="6d524-107">dans Jeton TypeDef de la classe dont les champs doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="6d524-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="6d524-108">à Liste des jetons FieldDef.</span><span class="sxs-lookup"><span data-stu-id="6d524-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6d524-109">[in] Taille maximale du tableau `rFields`.</span><span class="sxs-lookup"><span data-stu-id="6d524-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="6d524-110">à Nombre réel de jetons FieldDef retournés dans `rFields` .</span><span class="sxs-lookup"><span data-stu-id="6d524-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d524-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6d524-111">Return Value</span></span>  
  
|<span data-ttu-id="6d524-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6d524-112">HRESULT</span></span>|<span data-ttu-id="6d524-113">Description</span><span class="sxs-lookup"><span data-stu-id="6d524-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6d524-114">`EnumFields`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="6d524-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6d524-115">Il n’y a aucun champ à énumérer.</span><span class="sxs-lookup"><span data-stu-id="6d524-115">There are no fields to enumerate.</span></span> <span data-ttu-id="6d524-116">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="6d524-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6d524-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6d524-117">Requirements</span></span>  
 <span data-ttu-id="6d524-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d524-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d524-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6d524-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d524-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6d524-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d524-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d524-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d524-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d524-122">See also</span></span>

- [<span data-ttu-id="6d524-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6d524-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6d524-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6d524-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
