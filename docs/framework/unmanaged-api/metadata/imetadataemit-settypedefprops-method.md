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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: baee8566e923f9cb31868f8aa0e379ff1dfa42fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777228"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="db035-102">IMetaDataEmit::SetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="db035-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="db035-103">Définit les fonctionnalités d’un type défini par un appel antérieur à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="db035-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db035-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db035-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db035-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="db035-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="db035-106">[in] Un `mdTypeDef` jeton obtenu à partir de l’appel d’origine à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="db035-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="db035-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="db035-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="db035-108">Il s’agit d’un masque de bits de `CorTypeAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="db035-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="db035-109">[in] Le `mdToken` de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="db035-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="db035-110">Obtenu à partir d’un appel précédent à [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), ou `null`.</span><span class="sxs-lookup"><span data-stu-id="db035-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="db035-111">[in] Un tableau de jetons pour les interfaces implémentées par ce type.</span><span class="sxs-lookup"><span data-stu-id="db035-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="db035-112">Ces `mdTypeRef` jetons soient obtenus à l’aide de [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="db035-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="db035-113">Est le dernier élément du tableau doit être `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="db035-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db035-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="db035-114">Requirements</span></span>  
 <span data-ttu-id="db035-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db035-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db035-116">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="db035-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="db035-117">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="db035-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db035-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db035-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db035-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db035-119">See also</span></span>

- [<span data-ttu-id="db035-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="db035-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="db035-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="db035-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
