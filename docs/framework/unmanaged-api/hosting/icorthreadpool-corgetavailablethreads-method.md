---
title: ICorThreadpool::CorGetAvailableThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
ms.openlocfilehash: 40da8e67c705378c9e44398f6a0f519296da03e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133264"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="9f44a-102">ICorThreadpool::CorGetAvailableThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="9f44a-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="9f44a-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="9f44a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f44a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f44a-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9f44a-105">spécifications</span><span class="sxs-lookup"><span data-stu-id="9f44a-105">Requirements</span></span>  
 <span data-ttu-id="9f44a-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f44a-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f44a-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f44a-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f44a-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9f44a-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f44a-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f44a-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f44a-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f44a-110">See also</span></span>

- [<span data-ttu-id="9f44a-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="9f44a-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
