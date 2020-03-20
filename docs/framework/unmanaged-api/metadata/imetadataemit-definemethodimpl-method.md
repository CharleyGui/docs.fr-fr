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
ms.openlocfilehash: 64d76efa8c2f29fda559e5c84217b865540027ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175822"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="b6b81-102">IMetaDataEmit::DefineMethodImpl, méthode</span><span class="sxs-lookup"><span data-stu-id="b6b81-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="b6b81-103">Crée une définition pour la mise en œuvre d’une méthode héritée d’une interface, et renvoie un jeton à cette définition de la méthode de mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="b6b81-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6b81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6b81-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6b81-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b6b81-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="b6b81-106">[dans] Le `mdTypedef` jeton de la classe d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="b6b81-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="b6b81-107">[dans] Le `mdMethodDef` `mdMemberRef` ou le jeton du corps de code.</span><span class="sxs-lookup"><span data-stu-id="b6b81-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="b6b81-108">[dans] Le `mdMethodDef` `mdMemberRef` ou le jeton de la méthode d’interface en cours d’implémenté.</span><span class="sxs-lookup"><span data-stu-id="b6b81-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b81-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b6b81-109">Requirements</span></span>  
 <span data-ttu-id="b6b81-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6b81-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b81-111">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="b6b81-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6b81-112">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6b81-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6b81-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6b81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b81-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6b81-114">See also</span></span>

- [<span data-ttu-id="b6b81-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b6b81-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b6b81-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b6b81-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
