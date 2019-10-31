---
title: ICorThreadpool::CorUnregisterWait, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 431b90f8c5db5f40bf50be0b03fa315c6ea15ef7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133200"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="68c98-102">ICorThreadpool::CorUnregisterWait, méthode</span><span class="sxs-lookup"><span data-stu-id="68c98-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="68c98-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="68c98-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68c98-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="68c98-105">spécifications</span><span class="sxs-lookup"><span data-stu-id="68c98-105">Requirements</span></span>  
 <span data-ttu-id="68c98-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68c98-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c98-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="68c98-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68c98-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="68c98-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68c98-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c98-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c98-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68c98-110">See also</span></span>

- [<span data-ttu-id="68c98-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="68c98-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
