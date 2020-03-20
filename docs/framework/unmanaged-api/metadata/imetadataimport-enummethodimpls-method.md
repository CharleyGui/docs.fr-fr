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
ms.openlocfilehash: e766cec8fd84713e12c43cd1095650ed5b757bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175471"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="8e673-102">IMetaDataImport::EnumMethodImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="8e673-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="8e673-103">Énumère les jetons MethodBody et MethodDeclaration représentant les méthodes du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="8e673-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e673-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8e673-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8e673-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8e673-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8e673-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="8e673-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8e673-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8e673-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="8e673-108">[dans] Un jeton TypeDef pour le type dont les implémentations de méthode pour énumérer.</span><span class="sxs-lookup"><span data-stu-id="8e673-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="8e673-109">[out] Le tableau pour stocker les jetons MethodBody.</span><span class="sxs-lookup"><span data-stu-id="8e673-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="8e673-110">[out] Le tableau pour stocker les jetons MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="8e673-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8e673-111">[dans] La taille maximale `rMethodBody` `rMethodDecl` de la et les tableaux.</span><span class="sxs-lookup"><span data-stu-id="8e673-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8e673-112">[dans] Le nombre réel de `rMethodBody` `rMethodDecl`méthodes retournées et .</span><span class="sxs-lookup"><span data-stu-id="8e673-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e673-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="8e673-113">Return Value</span></span>  
  
|<span data-ttu-id="8e673-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e673-114">HRESULT</span></span>|<span data-ttu-id="8e673-115">Description</span><span class="sxs-lookup"><span data-stu-id="8e673-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8e673-116">`EnumMethodImpls`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8e673-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8e673-117">Il n’y a pas de jetons de méthode pour énumérer.</span><span class="sxs-lookup"><span data-stu-id="8e673-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="8e673-118">Dans ce `pcTokens` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="8e673-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8e673-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8e673-119">Requirements</span></span>  
 <span data-ttu-id="8e673-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e673-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e673-121">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="8e673-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e673-122">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e673-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e673-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e673-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e673-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e673-124">See also</span></span>

- [<span data-ttu-id="8e673-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8e673-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8e673-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8e673-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
