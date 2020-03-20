---
title: IMetaDataImport::ResetEnum Method
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 3dd82588cf2dbf92fdda66fd7674c17ddc8b7306
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177186"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="ba952-102">IMetaDataImport::ResetEnum Method</span><span class="sxs-lookup"><span data-stu-id="ba952-102">IMetaDataImport::ResetEnum Method</span></span>
<span data-ttu-id="ba952-103">Réinitialise l'énumérateur spécifié à la position spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ba952-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba952-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba952-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba952-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba952-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ba952-106">[dans] L’enumérateur à réinitialiser.</span><span class="sxs-lookup"><span data-stu-id="ba952-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="ba952-107">[dans] La nouvelle position à laquelle placer l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="ba952-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba952-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ba952-108">Requirements</span></span>  
 <span data-ttu-id="ba952-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba952-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba952-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ba952-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ba952-111">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ba952-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ba952-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba952-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba952-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba952-113">See also</span></span>

- [<span data-ttu-id="ba952-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ba952-114">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ba952-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ba952-115">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
