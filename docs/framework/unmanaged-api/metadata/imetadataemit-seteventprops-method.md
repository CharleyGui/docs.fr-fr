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
ms.openlocfilehash: 720133e64c02aa09c9ff7e43a20630b0d55c1acf
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008753"
---
# <a name="imetadataemitseteventprops-method"></a><span data-ttu-id="8b5d6-102">IMetaDataEmit::SetEventProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8b5d6-102">IMetaDataEmit::SetEventProps Method</span></span>
<span data-ttu-id="8b5d6-103">Définit ou met à jour la fonctionnalité spécifiée d’un événement défini par un appel antérieur à [IMetaDataEmit ::D efineevent](imetadataemit-defineevent-method.md).</span><span class="sxs-lookup"><span data-stu-id="8b5d6-103">Sets or updates the specified feature of an event defined by a prior call to [IMetaDataEmit::DefineEvent](imetadataemit-defineevent-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b5d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b5d6-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8b5d6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8b5d6-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="8b5d6-106">dans Jeton d’événement.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-106">[in] The event token.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="8b5d6-107">dans Indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-107">[in] Event flags.</span></span> <span data-ttu-id="8b5d6-108">Il s’agit d’un masque de `CorEventAttr` valeur de valeurs.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-108">This is a bitmask of `CorEventAttr` values.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="8b5d6-109">dans Jeton de la classe d’événements.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-109">[in] The token for the event class.</span></span> <span data-ttu-id="8b5d6-110">Il s’agit soit d’un jeton, soit d’un `mdTypeDef` `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="8b5d6-111">dans Méthode utilisée pour s’abonner à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-111">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="8b5d6-112">dans Méthode utilisée pour annuler l’abonnement à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-112">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="8b5d6-113">dans Méthode utilisée (par une classe dérivée) pour déclencher l’événement.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-113">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="8b5d6-114">dans Tableau de jetons pour d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="8b5d6-114">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="8b5d6-115">Le dernier élément du tableau doit être `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="8b5d6-115">The last element of the array must be `mdMethodDefNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b5d6-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="8b5d6-116">Requirements</span></span>  
 <span data-ttu-id="8b5d6-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b5d6-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b5d6-118">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8b5d6-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8b5d6-119">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8b5d6-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b5d6-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b5d6-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b5d6-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b5d6-121">See also</span></span>

- [<span data-ttu-id="8b5d6-122">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8b5d6-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8b5d6-123">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="8b5d6-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
