---
title: IMetaDataImport::EnumTypeRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f6af4c1d6eb9c305358573b06da164e2344ff46e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774623"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="c1237-102">IMetaDataImport::EnumTypeRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="c1237-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="c1237-103">Énumère les jetons TypeRef définis dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="c1237-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1237-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1237-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1237-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c1237-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="c1237-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c1237-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="c1237-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="c1237-108">[out] Tableau utilisé pour stocker les jetons TypeRef.</span><span class="sxs-lookup"><span data-stu-id="c1237-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c1237-109">[in] Taille maximale du tableau `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="c1237-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="c1237-110">[out] Un pointeur vers le nombre de jetons TypeRef retournés dans `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="c1237-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1237-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c1237-111">Return Value</span></span>  
  
|<span data-ttu-id="c1237-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1237-112">HRESULT</span></span>|<span data-ttu-id="c1237-113">Description</span><span class="sxs-lookup"><span data-stu-id="c1237-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c1237-114">`EnumTypeRefs` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="c1237-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c1237-115">Il n’existe pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="c1237-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c1237-116">Dans ce cas, `pcTypeRefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="c1237-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1237-117">Notes</span><span class="sxs-lookup"><span data-stu-id="c1237-117">Remarks</span></span>  
 <span data-ttu-id="c1237-118">Un jeton TypeRef représente une référence à un type.</span><span class="sxs-lookup"><span data-stu-id="c1237-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1237-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1237-119">Requirements</span></span>  
 <span data-ttu-id="c1237-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1237-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1237-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c1237-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1237-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1237-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1237-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1237-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1237-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1237-124">See also</span></span>

- [<span data-ttu-id="c1237-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="c1237-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c1237-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="c1237-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
