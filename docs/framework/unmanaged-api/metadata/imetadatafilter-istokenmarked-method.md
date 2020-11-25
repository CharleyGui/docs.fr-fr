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
ms.openlocfilehash: ce7292003872805c9390ce3d9c59b39497a83ed1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701833"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="5ba1e-102">IMetaDataFilter::IsTokenMarked, méthode</span><span class="sxs-lookup"><span data-stu-id="5ba1e-102">IMetaDataFilter::IsTokenMarked Method</span></span>

<span data-ttu-id="5ba1e-103">Obtient une valeur indiquant si le jeton de métadonnées spécifié a été marqué comme traité.</span><span class="sxs-lookup"><span data-stu-id="5ba1e-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ba1e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ba1e-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ba1e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ba1e-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="5ba1e-106">dans Jeton à examiner pour une marque de traitement.</span><span class="sxs-lookup"><span data-stu-id="5ba1e-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="5ba1e-107">à Valeur qui est `true` si `tk` a été traité ; sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="5ba1e-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ba1e-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ba1e-108">Requirements</span></span>  

 <span data-ttu-id="5ba1e-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ba1e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ba1e-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5ba1e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5ba1e-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5ba1e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ba1e-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ba1e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba1e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ba1e-113">See also</span></span>

- [<span data-ttu-id="5ba1e-114">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="5ba1e-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
