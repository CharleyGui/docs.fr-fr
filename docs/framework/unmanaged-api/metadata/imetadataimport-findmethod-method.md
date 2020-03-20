---
title: IMetaDataImport::FindMethod, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 53b3d94e8b1e273fcbc041d25a5bf586a12735c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177253"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="d69ed-102">IMetaDataImport::FindMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="d69ed-102">IMetaDataImport::FindMethod Method</span></span>
<span data-ttu-id="d69ed-103">Obtient un pointeur vers le jeton MethodDef pour <xref:System.Type> la méthode qui est incluse par le spécifié et qui a le nom spécifié et la signature des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="d69ed-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d69ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d69ed-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d69ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d69ed-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="d69ed-106">[dans] Le `mdTypeDef` jeton pour le type (une classe ou une interface) qui entoure le membre à rechercher.</span><span class="sxs-lookup"><span data-stu-id="d69ed-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="d69ed-107">Si cette `mdTokenNil`valeur est, alors la recherche est faite pour une fonction globale.</span><span class="sxs-lookup"><span data-stu-id="d69ed-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="d69ed-108">[dans] Le nom de la méthode à rechercher.</span><span class="sxs-lookup"><span data-stu-id="d69ed-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="d69ed-109">[dans] Un pointeur à la signature de métadonnées binaires de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d69ed-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="d69ed-110">[dans] La taille dans `pvSigBlob`les octets de .</span><span class="sxs-lookup"><span data-stu-id="d69ed-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="d69ed-111">[out] Un pointeur pour le jeton MethodDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="d69ed-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d69ed-112">Notes </span><span class="sxs-lookup"><span data-stu-id="d69ed-112">Remarks</span></span>  
 <span data-ttu-id="d69ed-113">Vous spécifiez la méthode`td`en utilisant`szName`sa classe ou son`pvSigBlob`interface d’enceinte ( ), son nom ( ), et en option sa signature ().</span><span class="sxs-lookup"><span data-stu-id="d69ed-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="d69ed-114">Il peut y avoir plusieurs méthodes avec le même nom dans une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="d69ed-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="d69ed-115">Dans ce cas, passez la signature de la méthode pour trouver le match unique.</span><span class="sxs-lookup"><span data-stu-id="d69ed-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="d69ed-116">La signature `FindMethod` transmise doit avoir été générée dans la portée actuelle, parce que les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="d69ed-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="d69ed-117">Une signature peut intégrer un jeton qui identifie la classe d’enceinte ou le type de valeur.</span><span class="sxs-lookup"><span data-stu-id="d69ed-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="d69ed-118">Le jeton est un index dans le tableau local TypeDef.</span><span class="sxs-lookup"><span data-stu-id="d69ed-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="d69ed-119">Vous ne pouvez pas construire une signature en temps d’exécution en `FindMethod`dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour entrer à .</span><span class="sxs-lookup"><span data-stu-id="d69ed-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="d69ed-120">`FindMethod`ne trouve que des méthodes qui ont été définies directement dans la classe ou l’interface; il ne trouve pas de méthodes héritées.</span><span class="sxs-lookup"><span data-stu-id="d69ed-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d69ed-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d69ed-121">Requirements</span></span>  
 <span data-ttu-id="d69ed-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d69ed-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d69ed-123">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="d69ed-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d69ed-124">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d69ed-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d69ed-125">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d69ed-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69ed-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d69ed-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="d69ed-127">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d69ed-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d69ed-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d69ed-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
