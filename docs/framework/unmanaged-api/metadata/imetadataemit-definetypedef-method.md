---
title: IMetaDataEmit::DefineTypeDef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 4f1c3e823b35fcf7d5935eee111e042b2291d216
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175757"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="9c121-102">IMetaDataEmit::DefineTypeDef, méthode</span><span class="sxs-lookup"><span data-stu-id="9c121-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="9c121-103">Crée une définition de type pour un type de temps d’exécution de langue commun, et obtient un jeton de métadonnées pour cette définition de type.</span><span class="sxs-lookup"><span data-stu-id="9c121-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c121-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c121-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c121-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c121-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="9c121-106">[dans] Le nom du type dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="9c121-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="9c121-107">[dans] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="9c121-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="9c121-108">C’est un peu `CoreTypeAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="9c121-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="9c121-109">[dans] Le jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="9c121-109">[in] The token of the base class.</span></span> <span data-ttu-id="9c121-110">Il doit être `mdTypeDef` soit `mdTypeRef` un ou un jeton.</span><span class="sxs-lookup"><span data-stu-id="9c121-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="9c121-111">[dans] Une gamme de jetons spécifiant les interfaces que cette classe ou interface implémente.</span><span class="sxs-lookup"><span data-stu-id="9c121-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="9c121-112">[out] Le `mdTypeDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="9c121-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c121-113">Notes </span><span class="sxs-lookup"><span data-stu-id="9c121-113">Remarks</span></span>  
 <span data-ttu-id="9c121-114">Un indicateur `dwTypeDefFlags` précise si le type créé est un type de référence système de type courant (classe ou interface) ou un type de valeur système de type commun.</span><span class="sxs-lookup"><span data-stu-id="9c121-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="9c121-115">Selon les paramètres fournis, cette méthode, comme un effet `mdInterfaceImpl` secondaire, peut également créer un enregistrement pour chaque interface qui est héritée ou implémentée par ce type.</span><span class="sxs-lookup"><span data-stu-id="9c121-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="9c121-116">Cependant, cette méthode ne renvoie aucun de ces `mdInterfaceImpl` jetons.</span><span class="sxs-lookup"><span data-stu-id="9c121-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="9c121-117">Si un client veut ajouter `mdInterfaceImpl` ou modifier plus tard `IMetaDataImport` un jeton, il doit utiliser l’interface pour l’énumérer.</span><span class="sxs-lookup"><span data-stu-id="9c121-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="9c121-118">Si vous souhaitez utiliser la sémantique COM de l’interface, `[default]` vous `rtkImplements`devez fournir l’interface par défaut comme premier élément dans ; un attribut personnalisé défini sur la classe indiquera que la classe a `mdInterfaceImpl` une interface par défaut (qui est toujours supposé être le premier jeton déclaré pour la classe).</span><span class="sxs-lookup"><span data-stu-id="9c121-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="9c121-119">Chaque élément `rtkImplements` du tableau `mdTypeDef` `mdTypeRef` contient un ou un jeton.</span><span class="sxs-lookup"><span data-stu-id="9c121-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="9c121-120">Le dernier élément dans `mdTokenNil`le tableau doit être .</span><span class="sxs-lookup"><span data-stu-id="9c121-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c121-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9c121-121">Requirements</span></span>  
 <span data-ttu-id="9c121-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c121-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c121-123">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="9c121-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c121-124">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c121-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9c121-125">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c121-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c121-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c121-126">See also</span></span>

- [<span data-ttu-id="9c121-127">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9c121-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9c121-128">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9c121-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
