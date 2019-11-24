---
title: IMetaDataEmit::DeleteClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
ms.openlocfilehash: 00f2aa3364b8b707d4100f8d2574ff3765d106da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450169"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="3f072-102">IMetaDataEmit::DeleteClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="3f072-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="3f072-103">Destroys the class layout metadata signature for the type represented by the specified token.</span><span class="sxs-lookup"><span data-stu-id="3f072-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f072-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f072-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f072-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f072-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3f072-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span><span class="sxs-lookup"><span data-stu-id="3f072-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f072-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="3f072-107">Requirements</span></span>  
 <span data-ttu-id="3f072-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f072-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f072-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f072-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f072-110">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f072-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f072-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f072-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f072-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f072-112">See also</span></span>

- [<span data-ttu-id="3f072-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3f072-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f072-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="3f072-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
