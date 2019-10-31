---
title: ICorThreadpool::CorBindIoCompletionCallback, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
ms.openlocfilehash: 3073f391efd483a161d9e7bc3787a6ce180aa28c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133365"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="e7e50-102">ICorThreadpool::CorBindIoCompletionCallback, méthode</span><span class="sxs-lookup"><span data-stu-id="e7e50-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="e7e50-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="e7e50-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7e50-104">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e7e50-105">spécifications</span><span class="sxs-lookup"><span data-stu-id="e7e50-105">Requirements</span></span>  
 <span data-ttu-id="e7e50-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7e50-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7e50-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e7e50-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7e50-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e7e50-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7e50-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7e50-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7e50-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7e50-110">See also</span></span>

- [<span data-ttu-id="e7e50-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="e7e50-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
