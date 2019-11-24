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
ms.openlocfilehash: ae105a60969e819f7974735ed8f075c60ba93916
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440348"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="e8448-102">IMetaDataFilter::MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="e8448-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="e8448-103">Sets a value indicating that the specified metadata token has been processed.</span><span class="sxs-lookup"><span data-stu-id="e8448-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8448-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8448-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8448-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e8448-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="e8448-106">[in] The token to mark as processed.</span><span class="sxs-lookup"><span data-stu-id="e8448-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8448-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="e8448-107">Requirements</span></span>  
 <span data-ttu-id="e8448-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8448-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8448-109">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e8448-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e8448-110">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8448-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8448-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8448-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8448-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8448-112">See also</span></span>

- [<span data-ttu-id="e8448-113">IMetaDataFilter, interface</span><span class="sxs-lookup"><span data-stu-id="e8448-113">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
