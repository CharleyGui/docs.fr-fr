---
title: IMetaDataEmit::DefineEvent, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 6966d0ad2fefd8401b19d8e8dcf7776799a066b2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432566"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="367d5-102">IMetaDataEmit::DefineEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="367d5-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="367d5-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span><span class="sxs-lookup"><span data-stu-id="367d5-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="367d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="367d5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="367d5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="367d5-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="367d5-106">[in] The token for the target class or interface.</span><span class="sxs-lookup"><span data-stu-id="367d5-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="367d5-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="367d5-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="367d5-108">[in] The name of the event.</span><span class="sxs-lookup"><span data-stu-id="367d5-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="367d5-109">[in] Event flags.</span><span class="sxs-lookup"><span data-stu-id="367d5-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="367d5-110">[in] The token for the event class.</span><span class="sxs-lookup"><span data-stu-id="367d5-110">[in] The token for the event class.</span></span> <span data-ttu-id="367d5-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="367d5-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="367d5-112">[in] The method used to subscribe to the event, or null.</span><span class="sxs-lookup"><span data-stu-id="367d5-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="367d5-113">[in] The method used to unsubscribe to the event, or null.</span><span class="sxs-lookup"><span data-stu-id="367d5-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="367d5-114">[in] The method used (by a derived class) to raise the event.</span><span class="sxs-lookup"><span data-stu-id="367d5-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="367d5-115">[in] An array of tokens for other methods associated with the event.</span><span class="sxs-lookup"><span data-stu-id="367d5-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="367d5-116">The array is terminated with a `mdMethodDefNil` token.</span><span class="sxs-lookup"><span data-stu-id="367d5-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="367d5-117">[out] The metadata token assigned to the event.</span><span class="sxs-lookup"><span data-stu-id="367d5-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="367d5-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="367d5-118">Requirements</span></span>  
 <span data-ttu-id="367d5-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="367d5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="367d5-120">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="367d5-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="367d5-121">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="367d5-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="367d5-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="367d5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367d5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="367d5-123">See also</span></span>

- [<span data-ttu-id="367d5-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="367d5-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="367d5-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="367d5-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
