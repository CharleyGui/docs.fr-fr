---
title: IMetaDataFilter::IsTokenMarked, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
ms.openlocfilehash: 47377e892aaf2bdd96a297630c47fe52215b0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177379"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="c9d5e-102">IMetaDataFilter::IsTokenMarked, méthode</span><span class="sxs-lookup"><span data-stu-id="c9d5e-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="c9d5e-103">Obtient une valeur indiquant si le jeton spécifié des métadonnées a été marqué comme traité.</span><span class="sxs-lookup"><span data-stu-id="c9d5e-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9d5e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9d5e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9d5e-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c9d5e-106">[dans] Le jeton à examiner pour une marque de traitement.</span><span class="sxs-lookup"><span data-stu-id="c9d5e-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="c9d5e-107">[out] Une valeur `true` qui `tk` est si elle a été traitée; autrement `false`.</span><span class="sxs-lookup"><span data-stu-id="c9d5e-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9d5e-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9d5e-108">Requirements</span></span>  
 <span data-ttu-id="c9d5e-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9d5e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9d5e-110">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="c9d5e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c9d5e-111">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9d5e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c9d5e-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9d5e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d5e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9d5e-113">See also</span></span>

- [<span data-ttu-id="c9d5e-114">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="c9d5e-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
