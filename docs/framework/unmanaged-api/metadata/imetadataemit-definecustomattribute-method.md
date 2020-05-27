---
title: IMetaDataEmit::DefineCustomAttribute, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineCustomAttribute
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineCustomAttribute
helpviewer_keywords:
- DefineCustomAttribute method [.NET Framework metadata]
- IMetaDataEmit::DefineCustomAttribute method [.NET Framework metadata]
ms.assetid: 7dd14854-b756-4401-b167-88ca576dc8f0
topic_type:
- apiref
ms.openlocfilehash: 17757df566ba8d141e7adec00dcc1f75959d0e00
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005623"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="9741d-102">IMetaDataEmit::DefineCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="9741d-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>
<span data-ttu-id="9741d-103">Crée une définition pour un attribut personnalisé avec la signature de métadonnées spécifiée, à attacher à l’objet spécifié et obtient un jeton pour cette définition d’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9741d-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9741d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9741d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9741d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9741d-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="9741d-106">dans Jeton pour l’élément propriétaire.</span><span class="sxs-lookup"><span data-stu-id="9741d-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="9741d-107">dans Jeton qui identifie l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9741d-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="9741d-108">dans Pointeur vers l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="9741d-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="9741d-109">dans Nombre d’octets dans `pCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="9741d-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="9741d-110">à `mdCustomAttribute`Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="9741d-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9741d-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9741d-111">Requirements</span></span>  
 <span data-ttu-id="9741d-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9741d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9741d-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9741d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9741d-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9741d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9741d-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9741d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9741d-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9741d-116">See also</span></span>

- [<span data-ttu-id="9741d-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="9741d-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="9741d-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="9741d-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
