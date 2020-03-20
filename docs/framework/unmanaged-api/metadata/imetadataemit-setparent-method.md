---
title: IMetaDataEmit::SetParent, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: 7389e9233fd946cdb2c810bec01cfbfffc8b707d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175601"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="4951a-102">IMetaDataEmit::SetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="4951a-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="4951a-103">Établit que le membre spécifié, tel que défini par un appel antérieur à [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), est un membre du type spécifié, tel que défini par un appel préalable à [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="4951a-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4951a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4951a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4951a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4951a-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="4951a-106">[dans] Le `mdMemberRef` jeton pour recevoir un nouveau parent.</span><span class="sxs-lookup"><span data-stu-id="4951a-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="4951a-107">[dans] Le `mdToken` pour le nouveau parent.</span><span class="sxs-lookup"><span data-stu-id="4951a-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4951a-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4951a-108">Requirements</span></span>  
 <span data-ttu-id="4951a-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4951a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4951a-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="4951a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4951a-111">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4951a-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4951a-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4951a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4951a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4951a-113">See also</span></span>

- [<span data-ttu-id="4951a-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4951a-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4951a-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="4951a-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
