---
title: IMetaDataImport2::EnumGenericParams, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 55709e79cd8bdb36fe1e32ee8a699fccb1b1bbc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175302"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="f81d2-102">IMetaDataImport2::EnumGenericParams, méthode</span><span class="sxs-lookup"><span data-stu-id="f81d2-102">IMetaDataImport2::EnumGenericParams Method</span></span>
<span data-ttu-id="f81d2-103">Obtient un enumérateur pour une gamme de jetons de paramètres génériques associés au jeton typeDef ou MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="f81d2-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f81d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f81d2-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f81d2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f81d2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f81d2-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="f81d2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="f81d2-107">[dans] Le jeton TypeDef ou MethodDef dont les paramètres génériques doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="f81d2-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="f81d2-108">[out] La gamme de paramètres génériques à énumérer.</span><span class="sxs-lookup"><span data-stu-id="f81d2-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f81d2-109">[dans] Le nombre maximum demandé de jetons à placer dans `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="f81d2-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="f81d2-110">[out] Le nombre retourné de jetons placés en `rGenericParams`.</span><span class="sxs-lookup"><span data-stu-id="f81d2-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f81d2-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f81d2-111">Return Value</span></span>  
  
|<span data-ttu-id="f81d2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f81d2-112">HRESULT</span></span>|<span data-ttu-id="f81d2-113">Description</span><span class="sxs-lookup"><span data-stu-id="f81d2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f81d2-114">`EnumGenericParams`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="f81d2-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f81d2-115">`phEnum`n’a pas d’éléments membres.</span><span class="sxs-lookup"><span data-stu-id="f81d2-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="f81d2-116">Dans ce `pcGenericParams` cas, est réglé à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="f81d2-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f81d2-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f81d2-117">Requirements</span></span>  
 <span data-ttu-id="f81d2-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f81d2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f81d2-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="f81d2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f81d2-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f81d2-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f81d2-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f81d2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f81d2-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f81d2-122">See also</span></span>

- [<span data-ttu-id="f81d2-123">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="f81d2-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="f81d2-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f81d2-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
