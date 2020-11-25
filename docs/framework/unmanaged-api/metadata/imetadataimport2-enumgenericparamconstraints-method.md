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
ms.openlocfilehash: 27c3ec349cf6c83f6783e252e6c5af5e99fa4b37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702834"
---
# <a name="imetadataimport2enumgenericparamconstraints-method"></a><span data-ttu-id="9162d-102">IMetaDataImport2::EnumGenericParamConstraints, méthode</span><span class="sxs-lookup"><span data-stu-id="9162d-102">IMetaDataImport2::EnumGenericParamConstraints Method</span></span>

<span data-ttu-id="9162d-103">Obtient un énumérateur pour un tableau de contraintes de paramètres génériques associées au paramètre générique représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="9162d-103">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9162d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9162d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumGenericParamConstraints (  
    [in, out] HCORENUM                *phEnum,  
    [in]  mdGenericParam              tk,  
    [out] mdGenericParamConstraint    rGenericParamConstraints[],  
    [in]  ULONG                       cMax,  
    [out] ULONG                       *pcGenericParamConstraints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9162d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9162d-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="9162d-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="9162d-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="9162d-107">dans   Jeton qui représente le paramètre générique dont les contraintes doivent être énumérées.</span><span class="sxs-lookup"><span data-stu-id="9162d-107">[in]   A token that represents the generic parameter whose constraints are to be enumerated.</span></span>  
  
 `rGenericParamConstraints`  
 <span data-ttu-id="9162d-108">à Tableau de contraintes de paramètres génériques à énumérer.</span><span class="sxs-lookup"><span data-stu-id="9162d-108">[out] The array of generic parameter constraints to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9162d-109">dans   Nombre maximal de jetons demandés à placer dans `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="9162d-109">[in]   The requested maximum number of tokens to place in `rGenericParamConstraints`.</span></span>  
  
 `pcGenericParamConstraints`  
 <span data-ttu-id="9162d-110">à Pointeur vers le nombre de jetons placés dans `rGenericParamConstraints` .</span><span class="sxs-lookup"><span data-stu-id="9162d-110">[out] A pointer to the number of tokens placed in `rGenericParamConstraints`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9162d-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9162d-111">Return Value</span></span>  
  
|<span data-ttu-id="9162d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9162d-112">HRESULT</span></span>|<span data-ttu-id="9162d-113">Description</span><span class="sxs-lookup"><span data-stu-id="9162d-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9162d-114">`EnumGenericParameterConstraints` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9162d-114">`EnumGenericParameterConstraints` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9162d-115">`phEnum` n’a aucun élément membre.</span><span class="sxs-lookup"><span data-stu-id="9162d-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="9162d-116">Dans ce cas, `pcGenericParameterConstraints` a la valeur 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="9162d-116">In this case, `pcGenericParameterConstraints` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9162d-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9162d-117">Requirements</span></span>  

 <span data-ttu-id="9162d-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9162d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9162d-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9162d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9162d-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9162d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9162d-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9162d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9162d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9162d-122">See also</span></span>

- [<span data-ttu-id="9162d-123">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="9162d-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="9162d-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9162d-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
