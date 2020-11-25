---
title: ICorThreadpool::CorQueueUserWorkItem, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: 42de7cd566db53e43985088851fd01fb66feabd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720496"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="a1bdb-102">ICorThreadpool::CorQueueUserWorkItem, méthode</span><span class="sxs-lookup"><span data-stu-id="a1bdb-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>

<span data-ttu-id="a1bdb-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a1bdb-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1bdb-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1bdb-104">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a1bdb-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1bdb-105">Requirements</span></span>  

 <span data-ttu-id="a1bdb-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1bdb-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1bdb-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a1bdb-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1bdb-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a1bdb-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1bdb-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1bdb-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1bdb-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1bdb-110">See also</span></span>

- [<span data-ttu-id="a1bdb-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="a1bdb-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
