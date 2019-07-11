---
title: IMetaDataEmit::DefineMethodImpl, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b64275def01d7b62f9a461de69a286769094305e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777587"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="a77f4-102">IMetaDataEmit::DefineMethodImpl, méthode</span><span class="sxs-lookup"><span data-stu-id="a77f4-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="a77f4-103">Crée une définition pour l’implémentation d’une méthode héritée d’une interface et retourne un jeton pour cette définition de l’implémentation de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a77f4-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a77f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a77f4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a77f4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a77f4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a77f4-106">[in] Le `mdTypedef` jeton de la classe d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a77f4-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="a77f4-107">[in] Le `mdMethodDef` ou `mdMemberRef` jeton du corps du code.</span><span class="sxs-lookup"><span data-stu-id="a77f4-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="a77f4-108">[in] Le `mdMethodDef` ou `mdMemberRef` jeton de la méthode d’interface en cours d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="a77f4-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a77f4-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a77f4-109">Requirements</span></span>  
 <span data-ttu-id="a77f4-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a77f4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a77f4-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a77f4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a77f4-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a77f4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a77f4-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a77f4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77f4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a77f4-114">See also</span></span>

- [<span data-ttu-id="a77f4-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a77f4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="a77f4-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a77f4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
