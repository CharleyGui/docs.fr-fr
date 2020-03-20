---
title: IMetaDataEmit::SetTypeDefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: e59e7695246b2c83171e77352e16464258516f8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177460"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="b5207-102">IMetaDataEmit::SetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="b5207-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="b5207-103">Définit les caractéristiques d’un type défini par un appel antérieur à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5207-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5207-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5207-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5207-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b5207-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b5207-106">[dans] Un `mdTypeDef` jeton obtenu à partir de l’appel original à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5207-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="b5207-107">[dans] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="b5207-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="b5207-108">C’est un peu `CorTypeAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="b5207-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="b5207-109">[dans] La `mdToken` classe de base.</span><span class="sxs-lookup"><span data-stu-id="b5207-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="b5207-110">Obtenu d’un appel précédent à [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="b5207-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="b5207-111">[dans] Une gamme de jetons pour les interfaces que ce type implémente.</span><span class="sxs-lookup"><span data-stu-id="b5207-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="b5207-112">Ces `mdTypeRef` jetons sont obtenus à l’aide [d’IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="b5207-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="b5207-113">Le dernier élément du tableau `mdTokenNil`est doit être .</span><span class="sxs-lookup"><span data-stu-id="b5207-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5207-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b5207-114">Requirements</span></span>  
 <span data-ttu-id="b5207-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5207-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5207-116">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b5207-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5207-117">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5207-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5207-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5207-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5207-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5207-119">See also</span></span>

- [<span data-ttu-id="b5207-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b5207-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b5207-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b5207-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
