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
ms.openlocfilehash: 52c35b3bd726d4c83c6745bf99940faa44ea7338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702847"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="e9fcf-102">IMetaDataImport::ResetEnum Method</span><span class="sxs-lookup"><span data-stu-id="e9fcf-102">IMetaDataImport::ResetEnum Method</span></span>

<span data-ttu-id="e9fcf-103">Réinitialise l'énumérateur spécifié à la position spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e9fcf-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9fcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9fcf-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9fcf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9fcf-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="e9fcf-106">dans Énumérateur à réinitialiser.</span><span class="sxs-lookup"><span data-stu-id="e9fcf-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="e9fcf-107">dans Nouvelle position à laquelle placer l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="e9fcf-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9fcf-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e9fcf-108">Requirements</span></span>  

 <span data-ttu-id="e9fcf-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9fcf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9fcf-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e9fcf-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e9fcf-111">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9fcf-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e9fcf-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9fcf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fcf-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9fcf-113">See also</span></span>

- [<span data-ttu-id="e9fcf-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="e9fcf-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e9fcf-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="e9fcf-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
