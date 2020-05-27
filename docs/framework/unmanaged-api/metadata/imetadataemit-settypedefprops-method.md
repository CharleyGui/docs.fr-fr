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
ms.openlocfilehash: b05527f118de059c674ea659b1a22b7895126cf4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007765"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="dc9ca-102">IMetaDataEmit::SetTypeDefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="dc9ca-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="dc9ca-103">Définit les fonctionnalités d’un type défini par un appel antérieur à [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="dc9ca-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc9ca-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc9ca-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc9ca-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="dc9ca-106">dans `mdTypeDef`Jeton obtenu à partir de l’appel d’origine vers [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="dc9ca-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="dc9ca-107">[in] `TypeDef` attributs.</span><span class="sxs-lookup"><span data-stu-id="dc9ca-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="dc9ca-108">Il s’agit d’un masque de `CorTypeAttr` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="dc9ca-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="dc9ca-109">dans `mdToken`De la classe de base.</span><span class="sxs-lookup"><span data-stu-id="dc9ca-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="dc9ca-110">Obtenu à partir d’un appel précédent à [IMetaDataEmit ::D efineimporttype](imetadataemit-defineimporttype-method.md), ou `null` .</span><span class="sxs-lookup"><span data-stu-id="dc9ca-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="dc9ca-111">dans Tableau de jetons pour les interfaces implémentées par ce type.</span><span class="sxs-lookup"><span data-stu-id="dc9ca-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="dc9ca-112">Ces `mdTypeRef` jetons sont obtenus à l’aide de [IMetaDataEmit ::D efineimporttype](imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="dc9ca-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="dc9ca-113">Le dernier élément du tableau doit être `mdTokenNil` .</span><span class="sxs-lookup"><span data-stu-id="dc9ca-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9ca-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc9ca-114">Requirements</span></span>  
 <span data-ttu-id="dc9ca-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc9ca-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc9ca-116">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="dc9ca-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc9ca-117">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dc9ca-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc9ca-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc9ca-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc9ca-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc9ca-119">See also</span></span>

- [<span data-ttu-id="dc9ca-120">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="dc9ca-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="dc9ca-121">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="dc9ca-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
