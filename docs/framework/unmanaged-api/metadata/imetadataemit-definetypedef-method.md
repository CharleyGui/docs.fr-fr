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
ms.openlocfilehash: 2e75b6322e40fe010e9e0a3412a99c0d3460afae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719357"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="6c905-102">IMetaDataEmit::DefineTypeDef, méthode</span><span class="sxs-lookup"><span data-stu-id="6c905-102">IMetaDataEmit::DefineTypeDef Method</span></span>

<span data-ttu-id="6c905-103">Crée une définition de type pour un type de common language runtime et obtient un jeton de métadonnées pour cette définition de type.</span><span class="sxs-lookup"><span data-stu-id="6c905-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c905-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c905-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c905-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c905-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="6c905-106">dans Nom du type en Unicode.</span><span class="sxs-lookup"><span data-stu-id="6c905-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="6c905-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="6c905-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="6c905-108">Il s’agit d’un masque de `CoreTypeAttr` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="6c905-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="6c905-109">dans Jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="6c905-109">[in] The token of the base class.</span></span> <span data-ttu-id="6c905-110">Il doit s’agir d’un `mdTypeDef` ou d’un `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="6c905-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="6c905-111">dans Tableau de jetons spécifiant les interfaces implémentées par cette classe ou cette interface.</span><span class="sxs-lookup"><span data-stu-id="6c905-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="6c905-112">à `mdTypeDef` Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="6c905-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c905-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="6c905-113">Remarks</span></span>  

 <span data-ttu-id="6c905-114">Un indicateur dans `dwTypeDefFlags` spécifie si le type en cours de création est un type de référence de système de type commun (classe ou interface) ou un type de valeur de système de type commun.</span><span class="sxs-lookup"><span data-stu-id="6c905-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="6c905-115">Selon les paramètres fournis, cette méthode, en tant qu’effet secondaire, peut également créer un `mdInterfaceImpl` enregistrement pour chaque interface héritée ou implémentée par ce type.</span><span class="sxs-lookup"><span data-stu-id="6c905-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="6c905-116">Toutefois, cette méthode ne retourne pas l’un de ces `mdInterfaceImpl` jetons.</span><span class="sxs-lookup"><span data-stu-id="6c905-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="6c905-117">Si un client souhaite ajouter ou modifier ultérieurement un `mdInterfaceImpl` jeton, il doit utiliser l' `IMetaDataImport` interface pour les énumérer.</span><span class="sxs-lookup"><span data-stu-id="6c905-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="6c905-118">Si vous souhaitez utiliser la sémantique COM de l' `[default]` interface, vous devez fournir l’interface par défaut en tant que premier élément dans `rtkImplements` ; un attribut personnalisé défini sur la classe indique que la classe a une interface par défaut (qui est toujours supposée être le premier `mdInterfaceImpl` jeton déclaré pour la classe).</span><span class="sxs-lookup"><span data-stu-id="6c905-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="6c905-119">Chaque élément du `rtkImplements` tableau contient un `mdTypeDef` jeton ou `mdTypeRef` .</span><span class="sxs-lookup"><span data-stu-id="6c905-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="6c905-120">Le dernier élément du tableau doit être `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="6c905-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c905-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c905-121">Requirements</span></span>  

 <span data-ttu-id="6c905-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c905-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c905-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6c905-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c905-124">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c905-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c905-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c905-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c905-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c905-126">See also</span></span>

- [<span data-ttu-id="6c905-127">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="6c905-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6c905-128">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="6c905-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
