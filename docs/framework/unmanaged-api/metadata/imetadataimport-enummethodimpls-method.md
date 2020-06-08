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
ms.openlocfilehash: b8fabea78f85448e39fc6d31f0a7969458343877
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492005"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="8a83f-102">IMetaDataImport::EnumMethodImpls, méthode</span><span class="sxs-lookup"><span data-stu-id="8a83f-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="8a83f-103">Énumère les jetons MethodBody et MethodDeclaration représentant les méthodes du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="8a83f-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a83f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a83f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8a83f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a83f-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8a83f-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="8a83f-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="8a83f-107">Il doit s’agir d’une valeur NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="8a83f-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="8a83f-108">dans Jeton TypeDef pour le type dont les implémentations de méthode doivent être énumérées.</span><span class="sxs-lookup"><span data-stu-id="8a83f-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="8a83f-109">à Tableau pour stocker les jetons MethodBody.</span><span class="sxs-lookup"><span data-stu-id="8a83f-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="8a83f-110">à Tableau pour stocker les jetons MethodDeclaration.</span><span class="sxs-lookup"><span data-stu-id="8a83f-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8a83f-111">dans Taille maximale des `rMethodBody` `rMethodDecl` tableaux et.</span><span class="sxs-lookup"><span data-stu-id="8a83f-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="8a83f-112">dans Nombre réel de méthodes retournées dans `rMethodBody` et `rMethodDecl` .</span><span class="sxs-lookup"><span data-stu-id="8a83f-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a83f-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="8a83f-113">Return Value</span></span>  
  
|<span data-ttu-id="8a83f-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a83f-114">HRESULT</span></span>|<span data-ttu-id="8a83f-115">Description</span><span class="sxs-lookup"><span data-stu-id="8a83f-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8a83f-116">`EnumMethodImpls`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="8a83f-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8a83f-117">Il n’y a aucun jeton de méthode à énumérer.</span><span class="sxs-lookup"><span data-stu-id="8a83f-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="8a83f-118">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="8a83f-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a83f-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a83f-119">Requirements</span></span>  
 <span data-ttu-id="8a83f-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a83f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a83f-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a83f-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a83f-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8a83f-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a83f-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a83f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a83f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a83f-124">See also</span></span>

- [<span data-ttu-id="8a83f-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8a83f-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8a83f-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8a83f-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
