---
title: IMetaDataImport2::EnumGenericParamConstraints, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParamConstraints
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParamConstraints
helpviewer_keywords:
- EnumGenericParamConstraints method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParamConstraints method [.NET Framework metadata]
ms.assetid: 8a7d4e40-28fe-4e14-b801-4049880130e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ba9d7f8873d15a7cab2b9893feb8563dfc971b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778762"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="be524-102">IMetaDataImport2::EnumGenericParamConstraints, méthode</span><span class="sxs-lookup"><span data-stu-id="be524-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>
<span data-ttu-id="be524-103">Obtient un énumérateur pour un tableau de contraintes de paramètre générique associé au paramètre générique représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="be524-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be524-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be524-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be524-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be524-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="be524-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="be524-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="be524-107">[in]   Un jeton qui représente le paramètre générique dont les contraintes doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="be524-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="be524-108">[out] Tableau des contraintes de paramètre générique à énumérer.</span><span class="sxs-lookup"><span data-stu-id="be524-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="be524-109">[in]   Le nombre maximal demandé de jetons à placer dans `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="be524-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="be524-110">[out] Un pointeur vers le nombre de jetons placés dans `rGenericParamConstraints`.</span><span class="sxs-lookup"><span data-stu-id="be524-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be524-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="be524-111">Return Value</span></span>  
  
|<span data-ttu-id="be524-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be524-112">HRESULT</span></span>|<span data-ttu-id="be524-113">Description</span><span class="sxs-lookup"><span data-stu-id="be524-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="be524-114">`EnumGenericParameterConstraints` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="be524-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="be524-115">`phEnum` ne contient aucun élément de membre.</span><span class="sxs-lookup"><span data-stu-id="be524-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="be524-116">Dans ce cas, `pcGenericParameterConstraints` est définie sur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="be524-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be524-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be524-117">Requirements</span></span>  
 <span data-ttu-id="be524-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be524-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be524-119">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be524-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be524-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be524-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be524-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be524-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be524-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be524-122">See also</span></span>

- [<span data-ttu-id="be524-123">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="be524-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="be524-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="be524-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
