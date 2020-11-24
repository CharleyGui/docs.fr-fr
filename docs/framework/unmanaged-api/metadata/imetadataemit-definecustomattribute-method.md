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
ms.openlocfilehash: 096a460f9d6581ebdd00f8487af68f652524d52f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681663"
---
# <a name="imetadataemitdefinecustomattribute-method"></a><span data-ttu-id="81f67-102">IMetaDataEmit::DefineCustomAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="81f67-102">IMetaDataEmit::DefineCustomAttribute Method</span></span>

<span data-ttu-id="81f67-103">Crée une définition pour un attribut personnalisé avec la signature de métadonnées spécifiée, à attacher à l’objet spécifié et obtient un jeton pour cette définition d’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="81f67-103">Creates a definition for a custom attribute with the specified metadata signature, to be attached to the specified object, and gets a token to that custom attribute definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f67-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81f67-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineCustomAttribute (
    [in]  mdToken     tkObj,
    [in]  mdToken     tkType,
    [in]  void const  *pCustomAttribute,
    [in]  ULONG       cbCustomAttribute,
    [out] mdCustomAttribute *pcv
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81f67-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81f67-105">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="81f67-106">dans Jeton pour l’élément propriétaire.</span><span class="sxs-lookup"><span data-stu-id="81f67-106">[in] The token for the owner item.</span></span>  
  
 `tkType`  
 <span data-ttu-id="81f67-107">dans Jeton qui identifie l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="81f67-107">[in] The token that identifies the custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="81f67-108">dans Pointeur vers l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="81f67-108">[in] A pointer to the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="81f67-109">dans Nombre d’octets dans `pCustomAttribute` .</span><span class="sxs-lookup"><span data-stu-id="81f67-109">[in] The count of bytes in `pCustomAttribute`.</span></span>  
  
 `pcv`  
 <span data-ttu-id="81f67-110">à `mdCustomAttribute` Jeton assigné.</span><span class="sxs-lookup"><span data-stu-id="81f67-110">[out] The `mdCustomAttribute` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81f67-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="81f67-111">Requirements</span></span>  

 <span data-ttu-id="81f67-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81f67-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81f67-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="81f67-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81f67-114">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81f67-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81f67-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81f67-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f67-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81f67-116">See also</span></span>

- [<span data-ttu-id="81f67-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="81f67-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="81f67-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="81f67-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
