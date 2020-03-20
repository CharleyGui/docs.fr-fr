---
title: IMetaDataEmit2::SetGenericParamProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SetGenericParamProps
helpviewer_keywords:
- IMetaDataEmit2::SetGenericParamProps method [.NET Framework metadata]
- SetGenericParamProps method [.NET Framework metadata]
ms.assetid: cd93a48d-1fed-4706-bec6-a05dc3b64fbd
topic_type:
- apiref
ms.openlocfilehash: fd7f149e806727d849cdceb3ffbc5dc7392fcf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177411"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="8d4c9-102">IMetaDataEmit2::SetGenericParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8d4c9-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="8d4c9-103">Définit la valeur de la propriété pour la définition de paramètre générique référencée par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d4c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d4c9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,
    [in] DWORD            dwParamFlags,
    [in] LPCWSTR          szName,
    [in] DWORD            reserved,
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d4c9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d4c9-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="8d4c9-106">[dans] Le jeton pour la définition de paramètre générique pour laquelle définir les valeurs.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="8d4c9-107">[dans] Une valeur de l’énumération [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) qui décrit le type pour le paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d4c9-108">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-108">[in] Optional.</span></span> <span data-ttu-id="8d4c9-109">Le nom du paramètre pour lequel définir des valeurs.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="8d4c9-110">[dans] Réservé à l’extensibility future.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="8d4c9-111">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-111">[in] Optional.</span></span> <span data-ttu-id="8d4c9-112">Un éventail de contraintes de type à durée nulle.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="8d4c9-113">Les membres du `mdTypeDef` `mdTypeRef`tableau `mdTypeSpec` doivent être un jeton, ou métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8d4c9-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d4c9-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8d4c9-114">Requirements</span></span>  
 <span data-ttu-id="8d4c9-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d4c9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d4c9-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="8d4c9-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d4c9-117">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d4c9-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d4c9-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d4c9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d4c9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d4c9-119">See also</span></span>

- [<span data-ttu-id="8d4c9-120">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="8d4c9-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="8d4c9-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8d4c9-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
