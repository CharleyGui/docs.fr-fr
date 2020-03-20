---
title: IMetaDataEmit2::DefineGenericParam, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineGenericParam
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineGenericParam
helpviewer_keywords:
- IMetaDataEmit2::DefineGenericParam method [.NET Framework metadata]
- DefineGenericParam method [.NET Framework metadata]
ms.assetid: 47b2a3b6-907d-43dc-858d-1ae7dca1316a
topic_type:
- apiref
ms.openlocfilehash: 1868d13a9dbb73dbdf64e49c395bdbff02ce89d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177455"
---
# <a name="imetadataemit2definegenericparam-method"></a><span data-ttu-id="02fb5-102">IMetaDataEmit2::DefineGenericParam, méthode</span><span class="sxs-lookup"><span data-stu-id="02fb5-102">IMetaDataEmit2::DefineGenericParam Method</span></span>
<span data-ttu-id="02fb5-103">Crée une définition pour un paramètre de type générique, et obtient un jeton à ce paramètre de type générique.</span><span class="sxs-lookup"><span data-stu-id="02fb5-103">Creates a definition for a generic type parameter, and gets a token to that generic type parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02fb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02fb5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGenericParam (
    [in]  mdToken         tk,
    [in]  ULONG           ulParamSeq,
    [in]  DWORD           dwParamFlags,
    [in]  LPCWSTR         szname,
    [in]  DWORD           reserved,
    [in]  mdToken         rtkConstraints[],
    [out] mdGenericParam  *pgp  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02fb5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02fb5-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="02fb5-106">[dans] Un `mdTypeDef` `mdMethodDef` ou un jeton qui représente la méthode ou le constructeur pour lequel définir un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="02fb5-106">[in] An `mdTypeDef` or `mdMethodDef` token that represents the method or constructor for which to define a generic parameter.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="02fb5-107">[dans] L’index du paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="02fb5-107">[in] The index of the generic parameter.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="02fb5-108">[dans] Une valeur de l’énumération [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) qui décrit le type pour le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="02fb5-108">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szname`  
 <span data-ttu-id="02fb5-109">[dans] Le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="02fb5-109">[in] The name of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="02fb5-110">[dans] Ce paramètre est réservé à l’extéabilité future.</span><span class="sxs-lookup"><span data-stu-id="02fb5-110">[in] This parameter is reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="02fb5-111">[dans] Un éventail de contraintes de type à durée nulle.</span><span class="sxs-lookup"><span data-stu-id="02fb5-111">[in] A zero-terminated array of type constraints.</span></span> <span data-ttu-id="02fb5-112">Les membres du `mdTypeDef` `mdTypeRef`tableau `mdTypeSpec` doivent être un jeton, ou métadonnées.</span><span class="sxs-lookup"><span data-stu-id="02fb5-112">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
 `pgp`  
 <span data-ttu-id="02fb5-113">[out] Un jeton qui représente le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="02fb5-113">[out] A token that represents the generic parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02fb5-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="02fb5-114">Requirements</span></span>  
 <span data-ttu-id="02fb5-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02fb5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02fb5-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="02fb5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02fb5-117">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02fb5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02fb5-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02fb5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02fb5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02fb5-119">See also</span></span>

- [<span data-ttu-id="02fb5-120">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="02fb5-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="02fb5-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="02fb5-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
