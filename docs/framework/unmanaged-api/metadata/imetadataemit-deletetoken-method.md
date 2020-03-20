---
title: IMetaDataEmit::DeleteToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: 3b8aed6522b1c7eb2d8916f71d8a66b367623765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177606"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="bc270-102">IMetaDataEmit::DeleteToken, méthode</span><span class="sxs-lookup"><span data-stu-id="bc270-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="bc270-103">Supprime le jeton spécifié à partir de la portée actuelle des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="bc270-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc270-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc270-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc270-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc270-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="bc270-106">[dans] Le jeton à supprimer.</span><span class="sxs-lookup"><span data-stu-id="bc270-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc270-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bc270-107">Requirements</span></span>  
 <span data-ttu-id="bc270-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc270-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc270-109">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="bc270-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc270-110">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc270-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc270-111">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc270-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc270-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc270-112">See also</span></span>

- [<span data-ttu-id="bc270-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="bc270-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="bc270-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="bc270-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
