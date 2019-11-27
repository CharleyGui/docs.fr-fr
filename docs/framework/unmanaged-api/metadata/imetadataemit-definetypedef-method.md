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
ms.openlocfilehash: 031996813718a074eebab62ff54a2de52b898c22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450216"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="0e5cc-102">IMetaDataEmit::DefineTypeDef, méthode</span><span class="sxs-lookup"><span data-stu-id="0e5cc-102">IMetaDataEmit::DefineTypeDef Method</span></span>
<span data-ttu-id="0e5cc-103">Crée une définition de type pour un type de common language runtime et obtient un jeton de métadonnées pour cette définition de type.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e5cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e5cc-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (   
    [in]  LPCWSTR     szTypeDef,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e5cc-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e5cc-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="0e5cc-106">dans Nom du type en Unicode.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="0e5cc-107">[in] attributs `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="0e5cc-108">Il s’agit d’un masque de ré`CoreTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="0e5cc-109">dans Jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-109">[in] The token of the base class.</span></span> <span data-ttu-id="0e5cc-110">Il doit s’agir d’un `mdTypeDef` ou d’un jeton `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="0e5cc-111">dans Tableau de jetons spécifiant les interfaces implémentées par cette classe ou cette interface.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0e5cc-112">à Jeton `mdTypeDef` assigné.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e5cc-113">Notes</span><span class="sxs-lookup"><span data-stu-id="0e5cc-113">Remarks</span></span>  
 <span data-ttu-id="0e5cc-114">Un indicateur dans `dwTypeDefFlags` spécifie si le type en cours de création est un type de référence de système de type commun (classe ou interface) ou un type de valeur de système de type commun.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="0e5cc-115">Selon les paramètres fournis, cette méthode, en tant qu’effet secondaire, peut également créer un enregistrement `mdInterfaceImpl` pour chaque interface héritée ou implémentée par ce type.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="0e5cc-116">Toutefois, cette méthode ne retourne pas l’un de ces `mdInterfaceImpl` jetons.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="0e5cc-117">Si un client souhaite ajouter ou modifier ultérieurement un jeton `mdInterfaceImpl`, il doit utiliser l’interface `IMetaDataImport` pour les énumérer.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="0e5cc-118">Si vous souhaitez utiliser la sémantique COM de l’interface `[default]`, vous devez fournir l’interface par défaut en tant que premier élément de `rtkImplements`; un ensemble d’attributs personnalisés sur la classe indique que la classe a une interface par défaut (qui est toujours supposée être la première `mdInterfaceImpl` jeton déclaré pour la classe).</span><span class="sxs-lookup"><span data-stu-id="0e5cc-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="0e5cc-119">Chaque élément du tableau `rtkImplements` contient un jeton `mdTypeDef` ou `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="0e5cc-120">Le dernier élément du tableau doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="0e5cc-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e5cc-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e5cc-121">Requirements</span></span>  
 <span data-ttu-id="0e5cc-122">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e5cc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e5cc-123">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0e5cc-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e5cc-124">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0e5cc-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e5cc-125">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e5cc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5cc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e5cc-126">See also</span></span>

- [<span data-ttu-id="0e5cc-127">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="0e5cc-127">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="0e5cc-128">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="0e5cc-128">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
