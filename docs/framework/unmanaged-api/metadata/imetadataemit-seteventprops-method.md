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
ms.openlocfilehash: 506e13ad956a01b16e36d8c71737fe0efce4c01b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450320"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="5b5ee-102">IMetaDataEmit::SetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="5b5ee-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="5b5ee-103">Définit ou met à jour la fonctionnalité spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit ::D efineevent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="5b5ee-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b5ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b5ee-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5b5ee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5b5ee-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="5b5ee-106">dans Jeton d’événement.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="5b5ee-107">dans Indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-107">[in] Event flags.</span></span> <span data-ttu-id="5b5ee-108">Il s’agit d’un masque de ré`CorEventAttr` valeurs.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="5b5ee-109">dans Jeton de la classe d’événements.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-109">[in] The token for the event class.</span></span> <span data-ttu-id="5b5ee-110">Il s’agit soit d’un `mdTypeDef`, soit d’un jeton `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="5b5ee-111">dans Méthode utilisée pour s’abonner à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="5b5ee-112">dans Méthode utilisée pour annuler l’abonnement à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="5b5ee-113">dans Méthode utilisée (par une classe dérivée) pour déclencher l’événement.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="5b5ee-114">dans Tableau de jetons pour d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="5b5ee-115">Le dernier élément du tableau doit être `mdMethodDefNil`.</span><span class="sxs-lookup"><span data-stu-id="5b5ee-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b5ee-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5b5ee-116">Requirements</span></span>  
 <span data-ttu-id="5b5ee-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b5ee-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b5ee-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5b5ee-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5b5ee-119">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5b5ee-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5b5ee-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b5ee-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b5ee-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b5ee-121">See also</span></span>

- [<span data-ttu-id="5b5ee-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="5b5ee-122">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5b5ee-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="5b5ee-123">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
