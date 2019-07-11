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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0c9f104329818f47597e8735389e5e6205ca617
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777102"
---
# <a name="imetadataemit2setgenericparamprops-method"></a><span data-ttu-id="cb0f8-102">IMetaDataEmit2::SetGenericParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="cb0f8-102">IMetaDataEmit2::SetGenericParamProps Method</span></span>
<span data-ttu-id="cb0f8-103">Définit les valeurs de propriété pour la définition de paramètre générique référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-103">Sets property values for the generic parameter definition referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb0f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb0f8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGenericParamProps (  
    [in] mdGenericParam   gp,   
    [in] DWORD            dwParamFlags,   
    [in] LPCWSTR          szName,   
    [in] DWORD            reserved,   
    [in] mdToken          rtkConstraints[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb0f8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cb0f8-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="cb0f8-106">[in] Le jeton pour la définition de paramètre générique pour lequel définir des valeurs.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-106">[in] The token for the generic parameter definition for which to set values.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="cb0f8-107">[in] Une valeur de la [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) énumération qui décrit le type du paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-107">[in] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the type for the generic parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="cb0f8-108">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-108">[in] Optional.</span></span> <span data-ttu-id="cb0f8-109">Le nom du paramètre pour lequel définir des valeurs.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-109">The name of the parameter for which to set values.</span></span>  
  
 `reserved`  
 <span data-ttu-id="cb0f8-110">[in] Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-110">[in] Reserved for future extensibility.</span></span>  
  
 `rtkConstraints`  
 <span data-ttu-id="cb0f8-111">[in] Facultatif.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-111">[in] Optional.</span></span> <span data-ttu-id="cb0f8-112">Un tableau de contraintes de type se terminant par zéro.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-112">A zero-terminated array of type constraints.</span></span> <span data-ttu-id="cb0f8-113">Les membres de tableau doivent être un `mdTypeDef`, `mdTypeRef`, ou `mdTypeSpec` jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="cb0f8-113">Array members must be an `mdTypeDef`, `mdTypeRef`, or `mdTypeSpec` metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb0f8-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cb0f8-114">Requirements</span></span>  
 <span data-ttu-id="cb0f8-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb0f8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb0f8-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb0f8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb0f8-117">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb0f8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb0f8-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb0f8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb0f8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb0f8-119">See also</span></span>

- [<span data-ttu-id="cb0f8-120">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="cb0f8-120">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="cb0f8-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="cb0f8-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
