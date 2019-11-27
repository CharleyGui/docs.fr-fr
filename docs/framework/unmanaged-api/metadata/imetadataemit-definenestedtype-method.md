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
ms.openlocfilehash: 5d985e22ba77053127610445374b8c13ca6b97f1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431705"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="e0043-102">IMetaDataEmit::DefineNestedType, méthode</span><span class="sxs-lookup"><span data-stu-id="e0043-102">IMetaDataEmit::DefineNestedType Method</span></span>
<span data-ttu-id="e0043-103">Crée la signature de métadonnées d’une définition de type, retourne un jeton `mdTypeDef` pour ce type et spécifie que le type défini est un membre du type référencé par le paramètre `tdEncloser`.</span><span class="sxs-lookup"><span data-stu-id="e0043-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0043-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="e0043-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0043-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="e0043-106">dans Nom du type en Unicode.</span><span class="sxs-lookup"><span data-stu-id="e0043-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="e0043-107">[in] attributs `TypeDef`.</span><span class="sxs-lookup"><span data-stu-id="e0043-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="e0043-108">Il s’agit d’un masque de ré`CorTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="e0043-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="e0043-109">dans Jeton de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="e0043-109">[in] The token of the base class.</span></span> <span data-ttu-id="e0043-110">Il s’agit soit d’un `mdTypeDef`, soit d’un jeton `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="e0043-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="e0043-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="e0043-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="e0043-112">dans Tableau de jetons qui spécifient les interfaces implémentées par cette classe ou cette interface.</span><span class="sxs-lookup"><span data-stu-id="e0043-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="e0043-113">dans Jeton du type englobant.</span><span class="sxs-lookup"><span data-stu-id="e0043-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="e0043-114">Le dernier élément du tableau doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="e0043-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="e0043-115">à Jeton `mdTypeDef` assigné.</span><span class="sxs-lookup"><span data-stu-id="e0043-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0043-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0043-116">Requirements</span></span>  
 <span data-ttu-id="e0043-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0043-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0043-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e0043-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e0043-119">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e0043-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0043-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0043-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0043-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0043-121">See also</span></span>

- [<span data-ttu-id="e0043-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="e0043-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="e0043-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="e0043-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
