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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba35cd678d88389854ca2e866020ea3a9364c923
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777665"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="16306-102">IMetaDataEmit::DefineEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="16306-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="16306-103">Crée une définition pour un événement avec la signature de métadonnées spécifiée et obtient un jeton pour cette définition de l’événement.</span><span class="sxs-lookup"><span data-stu-id="16306-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16306-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16306-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="16306-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16306-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="16306-106">[in] Le jeton pour la classe cible ou l’interface.</span><span class="sxs-lookup"><span data-stu-id="16306-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="16306-107">Il s’agit soit un `mdTypeDef` ou `mdTypeDefNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="16306-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="16306-108">[in] Le nom de l’événement.</span><span class="sxs-lookup"><span data-stu-id="16306-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="16306-109">[in] Indicateurs d’événement.</span><span class="sxs-lookup"><span data-stu-id="16306-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="16306-110">[in] Le jeton pour la classe d’événements.</span><span class="sxs-lookup"><span data-stu-id="16306-110">[in] The token for the event class.</span></span> <span data-ttu-id="16306-111">Il s’agit d’un `mdTypeDef`, un `mdTypeRef`, ou un `mdTokenNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="16306-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="16306-112">[in] La méthode utilisée pour s’abonner à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="16306-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="16306-113">[in] La méthode utilisée pour annuler l’abonnement à l’événement, ou null.</span><span class="sxs-lookup"><span data-stu-id="16306-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="16306-114">[in] La méthode utilisée (par une classe dérivée) pour déclencher l’événement.</span><span class="sxs-lookup"><span data-stu-id="16306-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="16306-115">[in] Un tableau de jetons pour les autres méthodes associées à l’événement.</span><span class="sxs-lookup"><span data-stu-id="16306-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="16306-116">Le tableau se termine par un `mdMethodDefNil` jeton.</span><span class="sxs-lookup"><span data-stu-id="16306-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="16306-117">[out] Le jeton de métadonnées assigné à l’événement.</span><span class="sxs-lookup"><span data-stu-id="16306-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16306-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="16306-118">Requirements</span></span>  
 <span data-ttu-id="16306-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16306-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16306-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16306-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16306-121">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16306-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16306-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16306-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16306-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16306-123">See also</span></span>

- [<span data-ttu-id="16306-124">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="16306-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="16306-125">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="16306-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
