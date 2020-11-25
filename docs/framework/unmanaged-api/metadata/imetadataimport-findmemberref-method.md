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
ms.openlocfilehash: 0ba25c981cc389baf06ecca0db543d48ac60317b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711401"
---
# <a name="imetadataimportfindmemberref-method"></a><span data-ttu-id="aac34-102">IMetaDataImport::FindMemberRef, méthode</span><span class="sxs-lookup"><span data-stu-id="aac34-102">IMetaDataImport::FindMemberRef Method</span></span>

<span data-ttu-id="aac34-103">Obtient un pointeur vers le jeton MemberRef pour la référence de membre qui est incluse dans le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aac34-103">Gets a pointer to the MemberRef token for the member reference that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aac34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aac34-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMemberRef (  
   [in]  mdTypeRef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMemberRef        *pmr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aac34-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aac34-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="aac34-106">dans Jeton TypeRef pour la classe ou l’interface qui englobe la référence de membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="aac34-106">[in] The TypeRef token for the class or interface that encloses the member reference to search for.</span></span> <span data-ttu-id="aac34-107">Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une variable globale ou une référence de fonction globale.</span><span class="sxs-lookup"><span data-stu-id="aac34-107">If this value is `mdTokenNil`, the lookup is done for a global variable or a global-function reference.</span></span>  
  
 `szName`  
 <span data-ttu-id="aac34-108">dans Nom de la référence de membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="aac34-108">[in] The name of the member reference to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="aac34-109">dans Pointeur vers la signature de métadonnées binaires de la référence de membre.</span><span class="sxs-lookup"><span data-stu-id="aac34-109">[in] A pointer to the binary metadata signature of the member reference.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="aac34-110">dans Taille en octets de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="aac34-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="aac34-111">à Pointeur vers le jeton MemberRef correspondant.</span><span class="sxs-lookup"><span data-stu-id="aac34-111">[out] A pointer to the matching MemberRef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aac34-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="aac34-112">Remarks</span></span>  

 <span data-ttu-id="aac34-113">Vous spécifiez le membre à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="aac34-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="aac34-114">La signature transmise à `FindMemberRef` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="aac34-114">The signature passed to `FindMemberRef` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="aac34-115">Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur.</span><span class="sxs-lookup"><span data-stu-id="aac34-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="aac34-116">Le jeton est un index dans la table TypeDef locale.</span><span class="sxs-lookup"><span data-stu-id="aac34-116">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="aac34-117">Vous ne pouvez pas générer une signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour `FindMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="aac34-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindMemberRef`.</span></span>  
  
 <span data-ttu-id="aac34-118">`FindMemberRef` recherche uniquement les références de membre qui ont été définies directement dans la classe ou l’interface ; il ne trouve pas les références de membre héritées.</span><span class="sxs-lookup"><span data-stu-id="aac34-118">`FindMemberRef` finds only member references that were defined directly in the class or interface; it does not find inherited member references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aac34-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aac34-119">Requirements</span></span>  

 <span data-ttu-id="aac34-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aac34-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aac34-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="aac34-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aac34-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aac34-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aac34-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aac34-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aac34-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aac34-124">See also</span></span>

- [<span data-ttu-id="aac34-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="aac34-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="aac34-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="aac34-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
