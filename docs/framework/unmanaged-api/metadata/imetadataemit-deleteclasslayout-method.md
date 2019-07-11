---
title: IMetaDataEmit::DeleteClassLayout, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteClassLayout
helpviewer_keywords:
- DeleteClassLayout method [.NET Framework metadata]
- IMetaDataEmit::DeleteClassLayout method [.NET Framework metadata]
ms.assetid: 65a4ad49-fa49-4b36-8ed1-76dd6a185ab4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84de8e3c688a23198762fca5219d317fabb69c1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777455"
---
# <a name="imetadataemitdeleteclasslayout-method"></a><span data-ttu-id="8a79e-102">IMetaDataEmit::DeleteClassLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="8a79e-102">IMetaDataEmit::DeleteClassLayout Method</span></span>
<span data-ttu-id="8a79e-103">Détruit la signature de métadonnées de disposition de classe pour le type représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="8a79e-103">Destroys the class layout metadata signature for the type represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a79e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a79e-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteClassLayout (  
    [in]  mdTypeDef   td  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a79e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a79e-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8a79e-106">[in] Un `mdTypeDef` jeton de métadonnées qui représente le type pour lequel la disposition de classe sera supprimée.</span><span class="sxs-lookup"><span data-stu-id="8a79e-106">[in] An `mdTypeDef` metadata token that represents the type for which the class layout will be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a79e-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a79e-107">Requirements</span></span>  
 <span data-ttu-id="8a79e-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a79e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a79e-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="8a79e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a79e-110">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8a79e-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a79e-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a79e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a79e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a79e-112">See also</span></span>

- [<span data-ttu-id="8a79e-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="8a79e-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8a79e-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="8a79e-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
