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
ms.openlocfilehash: e3655f77a94da25f65bada2cd4067ef53550e778
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762017"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="db6b6-102">ICorThreadpool::CorUnregisterWait, méthode</span><span class="sxs-lookup"><span data-stu-id="db6b6-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="db6b6-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="db6b6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db6b6-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="db6b6-105">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="db6b6-105">Requirements</span></span>  
 <span data-ttu-id="db6b6-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db6b6-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db6b6-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="db6b6-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="db6b6-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="db6b6-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db6b6-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db6b6-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db6b6-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db6b6-110">See also</span></span>

- [<span data-ttu-id="db6b6-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="db6b6-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
