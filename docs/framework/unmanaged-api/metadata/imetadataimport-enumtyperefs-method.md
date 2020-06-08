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
ms.openlocfilehash: 0c7e96c50e59902cde4686f908047a86dd2b6a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503742"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="2d53f-102">IMetaDataImport::EnumTypeRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="2d53f-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="2d53f-103">Énumère les jetons TypeRef définis dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="2d53f-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d53f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d53f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d53f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d53f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2d53f-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="2d53f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2d53f-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="2d53f-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="2d53f-108">à Tableau utilisé pour stocker les jetons TypeRef.</span><span class="sxs-lookup"><span data-stu-id="2d53f-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2d53f-109">[in] Taille maximale du tableau `rTypeRefs`.</span><span class="sxs-lookup"><span data-stu-id="2d53f-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="2d53f-110">à Pointeur vers le nombre de jetons TypeRef retournés dans `rTypeRefs` .</span><span class="sxs-lookup"><span data-stu-id="2d53f-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d53f-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="2d53f-111">Return Value</span></span>  
  
|<span data-ttu-id="2d53f-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d53f-112">HRESULT</span></span>|<span data-ttu-id="2d53f-113">Description</span><span class="sxs-lookup"><span data-stu-id="2d53f-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2d53f-114">`EnumTypeRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="2d53f-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2d53f-115">Il n’y a aucun jeton à énumérer.</span><span class="sxs-lookup"><span data-stu-id="2d53f-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2d53f-116">Dans ce cas, `pcTypeRefs` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="2d53f-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d53f-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="2d53f-117">Remarks</span></span>  
 <span data-ttu-id="2d53f-118">Un jeton TypeRef représente une référence à un type.</span><span class="sxs-lookup"><span data-stu-id="2d53f-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d53f-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d53f-119">Requirements</span></span>  
 <span data-ttu-id="2d53f-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d53f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d53f-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2d53f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d53f-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2d53f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d53f-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d53f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d53f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d53f-124">See also</span></span>

- [<span data-ttu-id="2d53f-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="2d53f-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2d53f-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="2d53f-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
