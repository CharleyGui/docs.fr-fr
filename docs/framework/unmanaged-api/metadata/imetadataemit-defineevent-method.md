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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175848"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="c958d-102">IMetaDataEmit::DefineEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="c958d-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="c958d-103">Crée une définition pour un événement avec la signature spécifiée de métadonnées, et obtient un jeton à cette définition d’événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c958d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c958d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c958d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c958d-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="c958d-106">[dans] Le jeton pour la classe ou l’interface cible.</span><span class="sxs-lookup"><span data-stu-id="c958d-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="c958d-107">C’est `mdTypeDef` un `mdTypeDefNil` ou un jeton.</span><span class="sxs-lookup"><span data-stu-id="c958d-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="c958d-108">[in] Nom de l'événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="c958d-109">[dans] Drapeaux de l’événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="c958d-110">[dans] Le jeton pour la classe d’événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-110">[in] The token for the event class.</span></span> <span data-ttu-id="c958d-111">Il s’agit d’un `mdTypeDef`, un `mdTypeRef`, ou un `mdTokenNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="c958d-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="c958d-112">[dans] La méthode utilisée pour s’abonner à l’événement, ou nulle.</span><span class="sxs-lookup"><span data-stu-id="c958d-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="c958d-113">[dans] La méthode utilisée pour se désabonner à l’événement, ou nulle.</span><span class="sxs-lookup"><span data-stu-id="c958d-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="c958d-114">[dans] La méthode utilisée (par une classe dérivée) pour élever l’événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="c958d-115">[dans] Un éventail de jetons pour d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="c958d-116">Le tableau est `mdMethodDefNil` terminé avec un jeton.</span><span class="sxs-lookup"><span data-stu-id="c958d-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="c958d-117">[out] Le jeton des métadonnées attribué à l’événement.</span><span class="sxs-lookup"><span data-stu-id="c958d-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c958d-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c958d-118">Requirements</span></span>  
 <span data-ttu-id="c958d-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c958d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c958d-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="c958d-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c958d-121">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c958d-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c958d-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c958d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c958d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c958d-123">See also</span></span>

- [<span data-ttu-id="c958d-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="c958d-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c958d-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="c958d-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
