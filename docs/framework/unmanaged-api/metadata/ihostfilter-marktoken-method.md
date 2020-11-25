---
title: IHostFilter::MarkToken, méthode
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
ms.openlocfilehash: b4db3b115517f0a146aeab469f091008d31efc86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718226"
---
# <a name="ihostfiltermarktoken-method"></a><span data-ttu-id="f8081-102">IHostFilter::MarkToken, méthode</span><span class="sxs-lookup"><span data-stu-id="f8081-102">IHostFilter::MarkToken Method</span></span>

<span data-ttu-id="f8081-103">Indique que le jeton de métadonnées spécifié sera traité.</span><span class="sxs-lookup"><span data-stu-id="f8081-103">Indicates that the specified metadata token will be processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8081-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8081-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8081-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f8081-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="f8081-106">dans Jeton de métadonnées à traiter.</span><span class="sxs-lookup"><span data-stu-id="f8081-106">[in] The metadata token to be processed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8081-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="f8081-107">Remarks</span></span>  

 <span data-ttu-id="f8081-108">En général, vous souhaitez qu’un jeton soit traité s’il se trouve dans la portée des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f8081-108">Typically, you want a token to be processed if it is in the metadata scope.</span></span> <span data-ttu-id="f8081-109">La `MarkToken` méthode est passée au moteur de métadonnées via la méthode [IMetaDataEmit :: SetHandler](imetadataemit-sethandler-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f8081-109">The `MarkToken` method is passed to the metadata engine via the [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8081-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f8081-110">Requirements</span></span>  

 <span data-ttu-id="f8081-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8081-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8081-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f8081-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f8081-113">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8081-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f8081-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8081-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8081-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8081-115">See also</span></span>

- [<span data-ttu-id="f8081-116">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f8081-116">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="f8081-117">IHostFilter, interface</span><span class="sxs-lookup"><span data-stu-id="f8081-117">IHostFilter Interface</span></span>](ihostfilter-interface.md)
