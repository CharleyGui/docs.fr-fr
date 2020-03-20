---
title: IMetaDataImport::FindMember, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: dab155b82d87609b3d3f390133e6490502a43518
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177282"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="b1bbd-102">IMetaDataImport::FindMember, méthode</span><span class="sxs-lookup"><span data-stu-id="b1bbd-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="b1bbd-103">Obtient un pointeur sur le jeton MemberDef pour le <xref:System.Type> champ ou la méthode qui est inclus par le spécifié et qui a le nom spécifié et la signature des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bbd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1bbd-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1bbd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1bbd-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b1bbd-106">[dans] Le jeton TypeDef pour la classe ou l’interface qui entoure le membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="b1bbd-107">Si cette `mdTokenNil`valeur est, la recherche est faite pour une variable globale ou fonction globale.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="b1bbd-108">[dans] Le nom du membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b1bbd-109">[dans] Un pointeur à la signature binaire métadonnées du membre.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="b1bbd-110">[dans] La taille dans `pvSigBlob`les octets de .</span><span class="sxs-lookup"><span data-stu-id="b1bbd-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="b1bbd-111">[out] Un pointeur pour le jeton MemberDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1bbd-112">Notes </span><span class="sxs-lookup"><span data-stu-id="b1bbd-112">Remarks</span></span>  
 <span data-ttu-id="b1bbd-113">Vous spécifiez le membre`td`en utilisant`szName`sa classe ou son`pvSigBlob`interface d’enceinte ( ), son nom ( ), et en option sa signature ().</span><span class="sxs-lookup"><span data-stu-id="b1bbd-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="b1bbd-114">Il peut y avoir plusieurs membres avec le même nom dans une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="b1bbd-115">Dans ce cas, passez la signature du membre pour trouver le match unique.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="b1bbd-116">La signature `FindMember` transmise doit avoir été générée dans la portée actuelle, parce que les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="b1bbd-117">Une signature peut intégrer un jeton qui identifie la classe d’enceinte ou le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="b1bbd-118">Le jeton est un index dans le tableau local TypeDef.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="b1bbd-119">Vous ne pouvez pas construire une signature en temps d’exécution en `FindMember`dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour entrer à .</span><span class="sxs-lookup"><span data-stu-id="b1bbd-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="b1bbd-120">`FindMember`ne trouve que les membres qui ont été définis directement dans la classe ou l’interface; il ne trouve pas de membres hérités.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1bbd-121">`FindMember`est une méthode d’aide.</span><span class="sxs-lookup"><span data-stu-id="b1bbd-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="b1bbd-122">Il appelle [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); si cet appel ne trouve `FindMember` pas de correspondance, appelle [alors IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="b1bbd-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1bbd-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b1bbd-123">Requirements</span></span>  
 <span data-ttu-id="b1bbd-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1bbd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1bbd-125">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b1bbd-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1bbd-126">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1bbd-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1bbd-127">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1bbd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bbd-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1bbd-128">See also</span></span>

- [<span data-ttu-id="b1bbd-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b1bbd-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b1bbd-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b1bbd-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
