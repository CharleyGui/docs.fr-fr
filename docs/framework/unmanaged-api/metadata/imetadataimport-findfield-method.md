---
title: IMetaDataImport::FindField, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1baee71b5b8575f51eb54fbc8a037a5dddd24500
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782526"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="6d587-102">IMetaDataImport::FindField, méthode</span><span class="sxs-lookup"><span data-stu-id="6d587-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="6d587-103">Obtient un pointeur vers le FieldDef jeton pour le champ est placé par spécifié <xref:System.Type> et qui a la signature de nom et de métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6d587-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d587-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d587-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d587-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d587-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="6d587-106">[in] Le jeton TypeDef pour la classe ou interface qui encadre le champ à rechercher.</span><span class="sxs-lookup"><span data-stu-id="6d587-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="6d587-107">Si cette valeur est `mdTokenNil`, la recherche est effectuée pour une variable globale.</span><span class="sxs-lookup"><span data-stu-id="6d587-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="6d587-108">[in] Le nom du champ à rechercher.</span><span class="sxs-lookup"><span data-stu-id="6d587-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="6d587-109">[in] Pointeur vers la signature de métadonnées binaires du champ.</span><span class="sxs-lookup"><span data-stu-id="6d587-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="6d587-110">[in] La taille en octets de `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="6d587-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="6d587-111">[out] Pointeur vers le jeton FieldDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="6d587-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d587-112">Notes</span><span class="sxs-lookup"><span data-stu-id="6d587-112">Remarks</span></span>  
 <span data-ttu-id="6d587-113">Vous spécifiez le champ à l’aide de son interface ou la classe englobante (`td`), son nom (`szName`) et éventuellement sa signature (`pvSigBlob`).</span><span class="sxs-lookup"><span data-stu-id="6d587-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="6d587-114">La signature est passé à `FindField` doit avoir été générée dans la portée actuelle, car les signatures sont liées à une étendue spécifique.</span><span class="sxs-lookup"><span data-stu-id="6d587-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="6d587-115">Une signature peut incorporer un jeton qui identifie le type de valeur ou de la classe englobant.</span><span class="sxs-lookup"><span data-stu-id="6d587-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="6d587-116">(Le jeton est un index dans la table TypeDef local).</span><span class="sxs-lookup"><span data-stu-id="6d587-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="6d587-117">Vous ne pouvez pas générer une signature d’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée dans `FindField`.</span><span class="sxs-lookup"><span data-stu-id="6d587-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="6d587-118">`FindField` recherche uniquement les champs qui ont été définis directement dans la classe ou interface ; Il ne trouve pas les champs hérités.</span><span class="sxs-lookup"><span data-stu-id="6d587-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d587-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6d587-119">Requirements</span></span>  
 <span data-ttu-id="6d587-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d587-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d587-121">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6d587-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6d587-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6d587-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6d587-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d587-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d587-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d587-124">See also</span></span>

- [<span data-ttu-id="6d587-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6d587-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6d587-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6d587-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
