---
title: IMetaDataEmit::DeleteFieldMarshal, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 5989c45782b4f83ecfa285cb305080320abf6a3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700546"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="7314d-102">IMetaDataEmit::DeleteFieldMarshal, méthode</span><span class="sxs-lookup"><span data-stu-id="7314d-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="7314d-103">Détruit la signature de métadonnées de marshaling PInvoke pour l’objet référencé par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="7314d-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7314d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7314d-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7314d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7314d-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="7314d-106">dans `mdFieldDef` Jeton ou `mdParamDef` qui représente le champ ou le paramètre pour lequel la signature des métadonnées de marshaling doit être supprimée.</span><span class="sxs-lookup"><span data-stu-id="7314d-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7314d-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7314d-107">Requirements</span></span>  

 <span data-ttu-id="7314d-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7314d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7314d-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7314d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7314d-110">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7314d-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7314d-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7314d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7314d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7314d-112">See also</span></span>

- [<span data-ttu-id="7314d-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7314d-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="7314d-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="7314d-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
