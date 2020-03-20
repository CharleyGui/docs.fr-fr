---
title: IMetaDataImport2::EnumMethodSpecs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177172"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="9077b-102">IMetaDataImport2::EnumMethodSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="9077b-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="9077b-103">Obtient un enumérateur pour un tableau de jetons MethodSpec associés au jeton MethodDef ou MemberRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="9077b-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9077b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9077b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="9077b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9077b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9077b-106">[dans, dehors] Un pointeur à l’enumérateur pour `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="9077b-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="9077b-107">[dans] Le jeton MemberRef ou MethodDef qui représente la méthode dont les jetons MethodSpec doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="9077b-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="9077b-108">Si la `tk` valeur est de 0 (zéro), tous les jetons MethodSpec dans la portée seront énumérés.</span><span class="sxs-lookup"><span data-stu-id="9077b-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="9077b-109">[out] La gamme de jetons MethodSpec à énumérer.</span><span class="sxs-lookup"><span data-stu-id="9077b-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9077b-110">[dans] Le nombre maximum demandé de jetons à placer dans `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="9077b-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="9077b-111">[out] Le nombre retourné de jetons placés en `rMethodSpecs`.</span><span class="sxs-lookup"><span data-stu-id="9077b-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9077b-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9077b-112">Return Value</span></span>  
  
|<span data-ttu-id="9077b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9077b-113">HRESULT</span></span>|<span data-ttu-id="9077b-114">Description</span><span class="sxs-lookup"><span data-stu-id="9077b-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9077b-115">`EnumMethodSpecs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9077b-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9077b-116">`phEnum`n’a pas d’éléments membres.</span><span class="sxs-lookup"><span data-stu-id="9077b-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="9077b-117">Dans ce `pcMethodSpecs` cas, est réglé à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="9077b-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9077b-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9077b-118">Requirements</span></span>  
 <span data-ttu-id="9077b-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9077b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9077b-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="9077b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9077b-121">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9077b-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9077b-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9077b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9077b-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9077b-123">See also</span></span>

- [<span data-ttu-id="9077b-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="9077b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="9077b-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9077b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
