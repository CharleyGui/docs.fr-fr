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
ms.openlocfilehash: 5ed5afbbf49b6680d00e78b6af3d45c6f0a7229d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004489"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="09fcb-102">IMetaDataEmit::DefineMethodImpl, méthode</span><span class="sxs-lookup"><span data-stu-id="09fcb-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="09fcb-103">Crée une définition pour l’implémentation d’une méthode héritée d’une interface et retourne un jeton à cette définition d’implémentation de méthode.</span><span class="sxs-lookup"><span data-stu-id="09fcb-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09fcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09fcb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09fcb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09fcb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="09fcb-106">dans `mdTypedef`Jeton de la classe d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="09fcb-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="09fcb-107">dans `mdMethodDef`Jeton ou `mdMemberRef` du corps du code.</span><span class="sxs-lookup"><span data-stu-id="09fcb-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="09fcb-108">dans `mdMethodDef`Jeton ou `mdMemberRef` de la méthode d’interface en cours d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="09fcb-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09fcb-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="09fcb-109">Requirements</span></span>  
 <span data-ttu-id="09fcb-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09fcb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09fcb-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="09fcb-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09fcb-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="09fcb-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09fcb-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09fcb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09fcb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09fcb-114">See also</span></span>

- [<span data-ttu-id="09fcb-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="09fcb-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="09fcb-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="09fcb-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
