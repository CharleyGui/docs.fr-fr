---
title: IMetaDataEmit::DefineNestedType, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175809"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="ae341-102">IMetaDataEmit::DefineNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="ae341-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="ae341-103">Crée la signature des métadonnées `mdTypeDef` d’une définition de type, renvoie un jeton pour ce type, et spécifie que le type défini est un membre du type référencé par le `tdEncloser` paramètre.</span><span class="sxs-lookup"><span data-stu-id="ae341-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae341-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae341-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae341-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae341-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="ae341-106">[dans] Le nom du type dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="ae341-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="ae341-107">[dans] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="ae341-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="ae341-108">C’est un peu `CorTypeAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="ae341-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="ae341-109">[dans] Le jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="ae341-109">[in] The token of the base class.</span></span> <span data-ttu-id="ae341-110">C’est `mdTypeDef` soit `mdTypeRef` un ou un jeton.</span><span class="sxs-lookup"><span data-stu-id="ae341-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="ae341-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="ae341-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="ae341-112">[dans] Une gamme de jetons qui spécifient les interfaces que cette classe ou interface implémente.</span><span class="sxs-lookup"><span data-stu-id="ae341-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="ae341-113">[dans] Le jeton du type d’enclos.</span><span class="sxs-lookup"><span data-stu-id="ae341-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="ae341-114">Le dernier élément du `mdTokenNil`tableau doit être .</span><span class="sxs-lookup"><span data-stu-id="ae341-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="ae341-115">[out] Le `mdTypeDef` jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="ae341-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae341-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ae341-116">Requirements</span></span>  
 <span data-ttu-id="ae341-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae341-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae341-118">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ae341-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae341-119">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae341-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae341-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae341-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae341-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae341-121">See also</span></span>

- [<span data-ttu-id="ae341-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ae341-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="ae341-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ae341-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
