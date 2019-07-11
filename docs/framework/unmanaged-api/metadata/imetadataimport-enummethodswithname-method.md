---
title: IMetaDataImport::EnumMethodsWithName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5de55d74741e9deb33be2f9adf15a970561664b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779733"
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="d80f2-102">IMetaDataImport::EnumMethodsWithName, méthode</span><span class="sxs-lookup"><span data-stu-id="d80f2-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="d80f2-103">Énumère les méthodes portant le nom spécifié et définies par le type référencé par le jeton TypeDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="d80f2-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d80f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d80f2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d80f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d80f2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d80f2-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="d80f2-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d80f2-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d80f2-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="d80f2-108">[in] Jeton TypeDef représentant le type dont les méthodes à énumérer.</span><span class="sxs-lookup"><span data-stu-id="d80f2-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="d80f2-109">[in] Nom qui limite l’étendue de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="d80f2-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="d80f2-110">[out] Tableau utilisé pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="d80f2-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d80f2-111">[in] Taille maximale du tableau `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="d80f2-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d80f2-112">[out] Le nombre de jetons MethodDef retournés dans `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="d80f2-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d80f2-113">Notes</span><span class="sxs-lookup"><span data-stu-id="d80f2-113">Remarks</span></span>  
 <span data-ttu-id="d80f2-114">Cette méthode énumère les champs et méthodes, mais pas propriétés ou événements.</span><span class="sxs-lookup"><span data-stu-id="d80f2-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="d80f2-115">Contrairement aux [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` ignore tous les jetons de méthode qui n’ont pas le nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="d80f2-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d80f2-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d80f2-116">Return Value</span></span>  
  
|<span data-ttu-id="d80f2-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d80f2-117">HRESULT</span></span>|<span data-ttu-id="d80f2-118">Description</span><span class="sxs-lookup"><span data-stu-id="d80f2-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d80f2-119">`EnumMethodsWithName` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d80f2-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d80f2-120">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="d80f2-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="d80f2-121">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="d80f2-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d80f2-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d80f2-122">Requirements</span></span>  
 <span data-ttu-id="d80f2-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d80f2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d80f2-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d80f2-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d80f2-125">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d80f2-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d80f2-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d80f2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d80f2-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d80f2-127">See also</span></span>

- [<span data-ttu-id="d80f2-128">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d80f2-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d80f2-129">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d80f2-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
