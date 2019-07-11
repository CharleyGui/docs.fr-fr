---
title: IMetaDataImport::EnumMethodImpls, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8be30e8c3b6bc7c03ede5f897f176e04153003b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781967"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="4c8c6-102">IMetaDataImport::EnumMethodImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="4c8c6-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="4c8c6-103">Énumère les jetons MethodBody et MethodDeclaration représentant les méthodes du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c8c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c8c6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c8c6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c8c6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="4c8c6-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="4c8c6-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="4c8c6-108">[in] Jeton TypeDef représentant le type dont les implémentations de méthode à énumérer.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="4c8c6-109">[out] Le tableau pour stocker les jetons MethodBody.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="4c8c6-110">[out] Le tableau pour stocker les jetons MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4c8c6-111">[in] La taille maximale de la `rMethodBody` et `rMethodDecl` tableaux.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="4c8c6-112">[in] Le nombre réel de méthodes retournées dans `rMethodBody` et `rMethodDecl`.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4c8c6-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4c8c6-113">Return Value</span></span>  
  
|<span data-ttu-id="4c8c6-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4c8c6-114">HRESULT</span></span>|<span data-ttu-id="4c8c6-115">Description</span><span class="sxs-lookup"><span data-stu-id="4c8c6-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="4c8c6-116">`EnumMethodImpls` retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="4c8c6-117">Il n’existe aucun jeton de méthode à énumérer.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="4c8c6-118">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="4c8c6-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c8c6-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4c8c6-119">Requirements</span></span>  
 <span data-ttu-id="4c8c6-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c8c6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c8c6-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4c8c6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4c8c6-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4c8c6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c8c6-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c8c6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8c6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c8c6-124">See also</span></span>

- [<span data-ttu-id="4c8c6-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4c8c6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4c8c6-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="4c8c6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
