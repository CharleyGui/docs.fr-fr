---
title: IMetaDataEmit::SetCustomAttributeValue, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: c4ea325a755ed05eed378d9201068de31ca8114f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681578"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="ec108-102">IMetaDataEmit::SetCustomAttributeValue, méthode</span><span class="sxs-lookup"><span data-stu-id="ec108-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>

<span data-ttu-id="ec108-103">Définit ou met à jour la valeur d’un attribut personnalisé défini par un appel antérieur à [IMetaDataEmit ::D efinecustomattribute](imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="ec108-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec108-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec108-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec108-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec108-105">Parameters</span></span>  

 `pcv`  
 <span data-ttu-id="ec108-106">dans Jeton de l’attribut personnalisé cible.</span><span class="sxs-lookup"><span data-stu-id="ec108-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="ec108-107">dans Pointeur vers le tableau qui contient l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ec108-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="ec108-108">dans Taille, en octets, de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ec108-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec108-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec108-109">Requirements</span></span>  

 <span data-ttu-id="ec108-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec108-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec108-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ec108-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec108-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec108-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ec108-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec108-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec108-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec108-114">See also</span></span>

- [<span data-ttu-id="ec108-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="ec108-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ec108-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="ec108-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
