---
title: IMetaDataFilter::MarkToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: c942838fb62bf86c4054761f4e7f2ef0518b3d89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701807"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="c4735-102">IMetaDataFilter::MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="c4735-102">IMetaDataFilter::MarkToken Method</span></span>

<span data-ttu-id="c4735-103">Définit une valeur indiquant que le jeton de métadonnées spécifié a été traité.</span><span class="sxs-lookup"><span data-stu-id="c4735-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4735-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4735-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4735-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4735-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="c4735-106">dans Jeton à marquer comme traité.</span><span class="sxs-lookup"><span data-stu-id="c4735-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4735-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4735-107">Requirements</span></span>  

 <span data-ttu-id="c4735-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4735-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4735-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c4735-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4735-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4735-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c4735-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4735-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4735-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4735-112">See also</span></span>

- [<span data-ttu-id="c4735-113">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="c4735-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
