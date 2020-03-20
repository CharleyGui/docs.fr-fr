---
title: IMetaDataEmit::SetEventProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetEventProps
helpviewer_keywords:
- IMetaDataEmit::SetEventProps method [.NET Framework metadata]
- SetEventProps method [.NET Framework metadata]
ms.assetid: 3b039e50-63ec-4730-99ff-2327408de477
topic_type:
- apiref
ms.openlocfilehash: f664e694303691fb1132150037dcbcdb5549539a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177526"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="2539e-102">IMetaDataEmit::SetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="2539e-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="2539e-103">Définit ou met à jour la fonction spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="2539e-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2539e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2539e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventProps (  
    [in]  mdEvent     ev,
    [in]  DWORD       dwEventFlags,
    [in]  mdToken     tkEventType,
    [in]  mdMethodDef mdAddOn,
    [in]  mdMethodDef mdRemoveOn,
    [in]  mdMethodDef mdFire,
    [in]  mdMethodDef rmdOtherMethods[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2539e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2539e-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="2539e-106">[dans] Le jeton de l’événement.</span><span class="sxs-lookup"><span data-stu-id="2539e-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="2539e-107">[dans] Drapeaux de l’événement.</span><span class="sxs-lookup"><span data-stu-id="2539e-107">[in] Event flags.</span></span> <span data-ttu-id="2539e-108">C’est un peu `CorEventAttr` de valeur.</span><span class="sxs-lookup"><span data-stu-id="2539e-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="2539e-109">[dans] Le jeton pour la classe d’événement.</span><span class="sxs-lookup"><span data-stu-id="2539e-109">[in] The token for the event class.</span></span> <span data-ttu-id="2539e-110">C’est `mdTypeDef` soit `mdTypeRef` un ou un jeton.</span><span class="sxs-lookup"><span data-stu-id="2539e-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="2539e-111">[dans] La méthode utilisée pour s’abonner à l’événement, ou nulle.</span><span class="sxs-lookup"><span data-stu-id="2539e-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="2539e-112">[dans] La méthode utilisée pour se désabonner à l’événement, ou nulle.</span><span class="sxs-lookup"><span data-stu-id="2539e-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="2539e-113">[dans] La méthode utilisée (par une classe dérivée) pour élever l’événement.</span><span class="sxs-lookup"><span data-stu-id="2539e-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="2539e-114">[dans] Un éventail de jetons pour d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="2539e-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="2539e-115">Le dernier élément du `mdMethodDefNil`tableau doit être .</span><span class="sxs-lookup"><span data-stu-id="2539e-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2539e-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2539e-116">Requirements</span></span>  
 <span data-ttu-id="2539e-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2539e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2539e-118">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="2539e-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2539e-119">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2539e-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2539e-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2539e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2539e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2539e-121">See also</span></span>

- [<span data-ttu-id="2539e-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="2539e-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="2539e-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="2539e-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
