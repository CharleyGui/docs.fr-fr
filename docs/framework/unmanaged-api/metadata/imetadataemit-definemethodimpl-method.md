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
ms.openlocfilehash: 24a7c5bca1287e55f3eb06d63e1fed8da37eb3b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719565"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="ae0a3-102">IMetaDataEmit::DefineMethodImpl, méthode</span><span class="sxs-lookup"><span data-stu-id="ae0a3-102">IMetaDataEmit::DefineMethodImpl Method</span></span>

<span data-ttu-id="ae0a3-103">Crée une définition pour l’implémentation d’une méthode héritée d’une interface et retourne un jeton à cette définition d’implémentation de méthode.</span><span class="sxs-lookup"><span data-stu-id="ae0a3-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae0a3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae0a3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae0a3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ae0a3-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="ae0a3-106">dans `mdTypedef` Jeton de la classe d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="ae0a3-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="ae0a3-107">dans `mdMethodDef` Jeton ou `mdMemberRef` du corps du code.</span><span class="sxs-lookup"><span data-stu-id="ae0a3-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="ae0a3-108">dans `mdMethodDef` Jeton ou `mdMemberRef` de la méthode d’interface en cours d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="ae0a3-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae0a3-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ae0a3-109">Requirements</span></span>  

 <span data-ttu-id="ae0a3-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae0a3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae0a3-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ae0a3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae0a3-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ae0a3-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae0a3-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae0a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae0a3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae0a3-114">See also</span></span>

- [<span data-ttu-id="ae0a3-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ae0a3-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ae0a3-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ae0a3-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
