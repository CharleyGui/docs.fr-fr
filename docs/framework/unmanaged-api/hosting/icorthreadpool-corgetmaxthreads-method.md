---
title: ICorThreadpool::CorGetMaxThreads, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: c3de2a063030d5169c6ff69e8db72e8be3ae22a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133284"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="55be1-102">ICorThreadpool::CorGetMaxThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="55be1-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="55be1-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="55be1-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55be1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55be1-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="55be1-105">spécifications</span><span class="sxs-lookup"><span data-stu-id="55be1-105">Requirements</span></span>  
 <span data-ttu-id="55be1-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55be1-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55be1-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="55be1-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="55be1-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="55be1-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="55be1-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55be1-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55be1-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55be1-110">See also</span></span>

- [<span data-ttu-id="55be1-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="55be1-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
