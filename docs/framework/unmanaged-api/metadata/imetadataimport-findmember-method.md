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
ms.openlocfilehash: fce4f3875fbdb110134d6b7f684eff40821f6bdd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503677"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="1e372-102">IMetaDataImport::FindMember, méthode</span><span class="sxs-lookup"><span data-stu-id="1e372-102">IMetaDataImport::FindMember Method</span></span>
<span data-ttu-id="1e372-103">Obtient un pointeur vers le jeton MemberDef pour le champ ou la méthode qui est inclus dans le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.</span><span class="sxs-lookup"><span data-stu-id="1e372-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e372-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e372-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e372-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1e372-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="1e372-106">dans Jeton TypeDef pour la classe ou l’interface qui englobe le membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1e372-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="1e372-107">Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une variable globale ou une fonction globale.</span><span class="sxs-lookup"><span data-stu-id="1e372-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="1e372-108">dans Nom du membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="1e372-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="1e372-109">dans Pointeur vers la signature de métadonnées binaires du membre.</span><span class="sxs-lookup"><span data-stu-id="1e372-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="1e372-110">dans Taille en octets de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="1e372-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="1e372-111">à Pointeur vers le jeton MemberDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="1e372-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e372-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="1e372-112">Remarks</span></span>  
 <span data-ttu-id="1e372-113">Vous spécifiez le membre à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="1e372-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="1e372-114">Il peut y avoir plusieurs membres portant le même nom dans une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="1e372-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="1e372-115">Dans ce cas, transmettez la signature du membre pour trouver la correspondance unique.</span><span class="sxs-lookup"><span data-stu-id="1e372-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="1e372-116">La signature transmise à `FindMember` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="1e372-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="1e372-117">Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur.</span><span class="sxs-lookup"><span data-stu-id="1e372-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="1e372-118">Le jeton est un index dans la table TypeDef locale.</span><span class="sxs-lookup"><span data-stu-id="1e372-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="1e372-119">Vous ne pouvez pas générer de signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour l’entrée dans `FindMember` .</span><span class="sxs-lookup"><span data-stu-id="1e372-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="1e372-120">`FindMember`recherche uniquement les membres qui ont été définis directement dans la classe ou l’interface ; il ne trouve pas les membres hérités.</span><span class="sxs-lookup"><span data-stu-id="1e372-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e372-121">`FindMember`est une méthode d’assistance.</span><span class="sxs-lookup"><span data-stu-id="1e372-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="1e372-122">Il appelle [IMetaDataImport :: FindMethod,](imetadataimport-findmethod-method.md); Si cet appel ne trouve pas de correspondance, `FindMember` appelle [IMetaDataImport :: FindField,](imetadataimport-findfield-method.md).</span><span class="sxs-lookup"><span data-stu-id="1e372-122">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e372-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1e372-123">Requirements</span></span>  
 <span data-ttu-id="1e372-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e372-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e372-125">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1e372-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e372-126">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1e372-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e372-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e372-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e372-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e372-128">See also</span></span>

- [<span data-ttu-id="1e372-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="1e372-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1e372-130">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="1e372-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
