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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d446e2b78f41d43aa70f429e23f1f4be22fd799
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782507"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="9f73d-102">IMetaDataImport::FindMemberRef, méthode</span><span class="sxs-lookup"><span data-stu-id="9f73d-102">IMetaDataImport::FindMemberRef Method</span></span>
<span data-ttu-id="9f73d-103">Obtient un pointeur vers le jeton MemberRef pour le membre de référence qui est délimitée par spécifié <xref:System.Type> et qui a la signature de nom et de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f73d-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f73d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f73d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,   
   [in]  PCCOR_SIGNATURE    pvSigBlob,   
   [in]  ULONG              cbSigBlob,   
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f73d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f73d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="9f73d-106">[in] Le jeton TypeRef pour la classe ou interface qui englobe la référence de membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="9f73d-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="9f73d-107">Si cette valeur est `mdTokenNil`, la recherche est effectuée pour une variable globale ou une référence de fonction globale.</span><span class="sxs-lookup"><span data-stu-id="9f73d-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="9f73d-108">[in] Le nom de la référence de membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="9f73d-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="9f73d-109">[in] Pointeur vers la signature de métadonnées binaires de la référence de membre.</span><span class="sxs-lookup"><span data-stu-id="9f73d-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="9f73d-110">[in] La taille en octets de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="9f73d-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="9f73d-111">[out] Pointeur vers le jeton MemberRef correspondant.</span><span class="sxs-lookup"><span data-stu-id="9f73d-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f73d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="9f73d-112">Remarks</span></span>  
 <span data-ttu-id="9f73d-113">Vous spécifiez le membre à l’aide de son interface ou la classe englobante (`td`), son nom (`szName`) et éventuellement sa signature (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="9f73d-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="9f73d-114">La signature est passé à `FindMemberRef` doit avoir été générée dans la portée actuelle, car les signatures sont liées à une étendue spécifique.</span><span class="sxs-lookup"><span data-stu-id="9f73d-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="9f73d-115">Une signature peut incorporer un jeton qui identifie le type de valeur ou de la classe englobant.</span><span class="sxs-lookup"><span data-stu-id="9f73d-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="9f73d-116">Le jeton est un index dans la table TypeDef local.</span><span class="sxs-lookup"><span data-stu-id="9f73d-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="9f73d-117">Vous ne pouvez pas générer une signature d’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée dans `FindMemberRef`.</span><span class="sxs-lookup"><span data-stu-id="9f73d-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="9f73d-118">`FindMemberRef` recherche uniquement les références de membre ont été définis directement dans la classe ou interface ; Il ne trouve pas de références de membre hérité.</span><span class="sxs-lookup"><span data-stu-id="9f73d-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f73d-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9f73d-119">Requirements</span></span>  
 <span data-ttu-id="9f73d-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f73d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f73d-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9f73d-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9f73d-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9f73d-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f73d-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f73d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f73d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f73d-124">See also</span></span>

- [<span data-ttu-id="9f73d-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9f73d-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9f73d-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="9f73d-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
