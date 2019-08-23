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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4eefb7ec1e7d0d130ec64531a59d1d5bbce04963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968921"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="82d3d-102">IMetaDataImport::FindMember, méthode</span><span class="sxs-lookup"><span data-stu-id="82d3d-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="82d3d-103">Obtient un pointeur vers le jeton MemberDef pour le champ ou la méthode qui est inclus dans <xref:System.Type> le spécifié et qui a le nom et la signature de métadonnées spécifiés.</span><span class="sxs-lookup"><span data-stu-id="82d3d-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d3d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82d3d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,   
   [in]  PCCOR_SIGNATURE   pvSigBlob,   
   [in]  ULONG             cbSigBlob,   
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82d3d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82d3d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="82d3d-106">dans Jeton TypeDef pour la classe ou l’interface qui englobe le membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="82d3d-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="82d3d-107">Si cette valeur est `mdTokenNil`, la recherche est effectuée pour une variable globale ou une fonction globale.</span><span class="sxs-lookup"><span data-stu-id="82d3d-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="82d3d-108">dans Nom du membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="82d3d-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="82d3d-109">dans Pointeur vers la signature de métadonnées binaires du membre.</span><span class="sxs-lookup"><span data-stu-id="82d3d-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="82d3d-110">dans Taille en octets de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="82d3d-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="82d3d-111">à Pointeur vers le jeton MemberDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="82d3d-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82d3d-112">Notes</span><span class="sxs-lookup"><span data-stu-id="82d3d-112">Remarks</span></span>  
 <span data-ttu-id="82d3d-113">Vous spécifiez le membre à l’aide de sa classe englobante ou de son interface`szName`(`td`), son nom () et`pvSigBlob`éventuellement sa signature ().</span><span class="sxs-lookup"><span data-stu-id="82d3d-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="82d3d-114">Il peut y avoir plusieurs membres portant le même nom dans une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="82d3d-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="82d3d-115">Dans ce cas, transmettez la signature du membre pour trouver la correspondance unique.</span><span class="sxs-lookup"><span data-stu-id="82d3d-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="82d3d-116">La signature transmise `FindMember` à doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="82d3d-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="82d3d-117">Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur.</span><span class="sxs-lookup"><span data-stu-id="82d3d-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="82d3d-118">Le jeton est un index dans la table TypeDef locale.</span><span class="sxs-lookup"><span data-stu-id="82d3d-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="82d3d-119">Vous ne pouvez pas générer de signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature `FindMember`comme entrée pour l’entrée dans.</span><span class="sxs-lookup"><span data-stu-id="82d3d-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="82d3d-120">`FindMember`recherche uniquement les membres qui ont été définis directement dans la classe ou l’interface; il ne trouve pas les membres hérités.</span><span class="sxs-lookup"><span data-stu-id="82d3d-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82d3d-121">`FindMember`est une méthode d’assistance.</span><span class="sxs-lookup"><span data-stu-id="82d3d-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="82d3d-122">Il appelle [IMetaDataImport:: FindMethod,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); Si cet appel ne trouve pas de correspondance, `FindMember` appelle [IMetaDataImport:: FindField,](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="82d3d-122">It calls [IMetaDataImport::FindMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d3d-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="82d3d-123">Requirements</span></span>  
 <span data-ttu-id="82d3d-124">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82d3d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82d3d-125">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="82d3d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82d3d-126">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="82d3d-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82d3d-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82d3d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d3d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82d3d-128">See also</span></span>

- [<span data-ttu-id="82d3d-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="82d3d-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="82d3d-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="82d3d-130">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
