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
ms.openlocfilehash: 99f529a151a42cf4a9ee1f74bd3a76a5b6b1b35f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445265"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="f4f87-102">IMetaDataEmit::DefineMethodImpl, méthode</span><span class="sxs-lookup"><span data-stu-id="f4f87-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="f4f87-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span><span class="sxs-lookup"><span data-stu-id="f4f87-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4f87-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4f87-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f4f87-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="f4f87-106">[in] The `mdTypedef` token of the implementing class.</span><span class="sxs-lookup"><span data-stu-id="f4f87-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="f4f87-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span><span class="sxs-lookup"><span data-stu-id="f4f87-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="f4f87-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span><span class="sxs-lookup"><span data-stu-id="f4f87-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4f87-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="f4f87-109">Requirements</span></span>  
 <span data-ttu-id="f4f87-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4f87-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4f87-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f4f87-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f4f87-112">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4f87-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4f87-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4f87-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f87-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4f87-114">See also</span></span>

- [<span data-ttu-id="f4f87-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f4f87-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f4f87-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="f4f87-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
