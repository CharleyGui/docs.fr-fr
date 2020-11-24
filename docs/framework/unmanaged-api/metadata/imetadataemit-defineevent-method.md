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
ms.openlocfilehash: 3c03497f48b8199da545d796637e5f8a5c532362
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675683"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="32bd0-102">IMetaDataEmit::DefineEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="32bd0-102">IMetaDataEmit::DefineEvent Method</span></span>

<span data-ttu-id="32bd0-103">Crée une définition pour un événement avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition d’événement.</span><span class="sxs-lookup"><span data-stu-id="32bd0-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32bd0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="32bd0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32bd0-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="32bd0-106">dans Jeton de la classe ou de l’interface cible.</span><span class="sxs-lookup"><span data-stu-id="32bd0-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="32bd0-107">Il s’agit d' `mdTypeDef` un `mdTypeDefNil` jeton ou.</span><span class="sxs-lookup"><span data-stu-id="32bd0-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="32bd0-108">[in] Nom de l'événement.</span><span class="sxs-lookup"><span data-stu-id="32bd0-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="32bd0-109">dans Indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="32bd0-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="32bd0-110">dans Jeton de la classe d’événements.</span><span class="sxs-lookup"><span data-stu-id="32bd0-110">[in] The token for the event class.</span></span> <span data-ttu-id="32bd0-111">Il s’agit d’un `mdTypeDef` , d’un `mdTypeRef` ou d’un `mdTokenNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="32bd0-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="32bd0-112">dans Méthode utilisée pour s’abonner à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="32bd0-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="32bd0-113">dans Méthode utilisée pour annuler l’abonnement à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="32bd0-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="32bd0-114">dans Méthode utilisée (par une classe dérivée) pour déclencher l’événement.</span><span class="sxs-lookup"><span data-stu-id="32bd0-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="32bd0-115">dans Tableau de jetons pour d’autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="32bd0-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="32bd0-116">Le tableau se termine par un `mdMethodDefNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="32bd0-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="32bd0-117">à Jeton de métadonnées affecté à l’événement.</span><span class="sxs-lookup"><span data-stu-id="32bd0-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32bd0-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="32bd0-118">Requirements</span></span>  

 <span data-ttu-id="32bd0-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32bd0-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32bd0-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="32bd0-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32bd0-121">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="32bd0-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32bd0-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32bd0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32bd0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32bd0-123">See also</span></span>

- [<span data-ttu-id="32bd0-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="32bd0-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="32bd0-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="32bd0-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
