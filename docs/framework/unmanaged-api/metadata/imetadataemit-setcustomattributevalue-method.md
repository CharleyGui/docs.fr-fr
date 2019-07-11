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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a1f248cf800e9c2bf17d7849e449287cfc493f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737216"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="6dfe2-102">IMetaDataEmit::SetCustomAttributeValue, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfe2-102">IMetaDataEmit::SetCustomAttributeValue Method</span></span>
<span data-ttu-id="6dfe2-103">Définit ou met à jour la valeur d’un attribut personnalisé défini par un appel antérieur à [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span><span class="sxs-lookup"><span data-stu-id="6dfe2-103">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfe2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dfe2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (   
    [in]  mdCustomAttribute       pcv,   
    [in]  void const              *pCustomAttribute,    
    [in]  ULONG                   cbCustomAttribute   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dfe2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6dfe2-105">Parameters</span></span>  
 `pcv`  
 <span data-ttu-id="6dfe2-106">[in] Le jeton de l’attribut personnalisé cible.</span><span class="sxs-lookup"><span data-stu-id="6dfe2-106">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="6dfe2-107">[in] Un pointeur vers le tableau qui contient l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6dfe2-107">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="6dfe2-108">[in] La taille, en octets, de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6dfe2-108">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfe2-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6dfe2-109">Requirements</span></span>  
 <span data-ttu-id="6dfe2-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dfe2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dfe2-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6dfe2-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6dfe2-112">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6dfe2-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6dfe2-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dfe2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfe2-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfe2-114">See also</span></span>

- [<span data-ttu-id="6dfe2-115">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="6dfe2-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6dfe2-116">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="6dfe2-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
