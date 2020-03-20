---
title: IMetaDataImport::FindMemberRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMemberRef
helpviewer_keywords:
- IMetaDataImport::FindMemberRef method [.NET Framework metadata]
- FindMemberRef method [.NET Framework metadata]
ms.assetid: 1ccda329-d752-4d89-abe8-511af3c3f4c9
topic_type:
- apiref
ms.openlocfilehash: d8b8bfd0e70e75c702f32555c10f433a1ff4ae10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175419"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="750b4-102">IMetaDataImport::FindMemberRef, méthode</span><span class="sxs-lookup"><span data-stu-id="750b4-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="750b4-103">Obtient un pointeur vers le jeton MemberRef pour la <xref:System.Type> référence du membre qui est inclus par le spécifié et qui a le nom spécifié et la signature des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="750b4-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="750b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="750b4-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="750b4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="750b4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="750b4-106">[dans] Le jeton TypeRef pour la classe ou l’interface qui entoure la référence du membre à la recherche.</span><span class="sxs-lookup"><span data-stu-id="750b4-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="750b4-107">Si cette `mdTokenNil`valeur est, la recherche est faite pour une variable globale ou une référence fonction globale.</span><span class="sxs-lookup"><span data-stu-id="750b4-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="750b4-108">[dans] Le nom de la référence du membre à la recherche.</span><span class="sxs-lookup"><span data-stu-id="750b4-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="750b4-109">[dans] Un pointeur à la signature binaire métadonnées de la référence du membre.</span><span class="sxs-lookup"><span data-stu-id="750b4-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="750b4-110">[dans] La taille dans `pvSigBlob`les octets de .</span><span class="sxs-lookup"><span data-stu-id="750b4-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="750b4-111">[out] Un pointeur pour le jeton De MemberRef correspondant.</span><span class="sxs-lookup"><span data-stu-id="750b4-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="750b4-112">Notes </span><span class="sxs-lookup"><span data-stu-id="750b4-112">Remarks</span></span>  
 <span data-ttu-id="750b4-113">Vous spécifiez le membre`td`en utilisant`szName`sa classe ou son`pvSigBlob`interface d’enceinte ( ), son nom ( ), et en option sa signature ().</span><span class="sxs-lookup"><span data-stu-id="750b4-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="750b4-114">La signature `FindMemberRef` transmise doit avoir été générée dans la portée actuelle, parce que les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="750b4-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="750b4-115">Une signature peut intégrer un jeton qui identifie la classe d’enceinte ou le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="750b4-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="750b4-116">Le jeton est un index dans le tableau local TypeDef.</span><span class="sxs-lookup"><span data-stu-id="750b4-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="750b4-117">Vous ne pouvez pas construire une signature en temps d’exécution `FindMemberRef`en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée à .</span><span class="sxs-lookup"><span data-stu-id="750b4-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="750b4-118">`FindMemberRef`ne trouve que les références des membres qui ont été définies directement dans la classe ou l’interface; il ne trouve pas de références de membres héritées.</span><span class="sxs-lookup"><span data-stu-id="750b4-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="750b4-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="750b4-119">Requirements</span></span>  
 <span data-ttu-id="750b4-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="750b4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="750b4-121">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="750b4-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="750b4-122">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="750b4-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="750b4-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="750b4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750b4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="750b4-124">See also</span></span>

- [<span data-ttu-id="750b4-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="750b4-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="750b4-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="750b4-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
