---
title: ICorThreadpool::CorDeleteTimer, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
ms.openlocfilehash: 97658d5418ac3c04abd423ffff86324acf0e99c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720540"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="83f4d-102">ICorThreadpool::CorDeleteTimer, méthode</span><span class="sxs-lookup"><span data-stu-id="83f4d-102">ICorThreadpool::CorDeleteTimer Method</span></span>

<span data-ttu-id="83f4d-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="83f4d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83f4d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="83f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="83f4d-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="83f4d-105">Requirements</span></span>  

 <span data-ttu-id="83f4d-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83f4d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83f4d-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="83f4d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83f4d-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83f4d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83f4d-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83f4d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83f4d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83f4d-110">See also</span></span>

- [<span data-ttu-id="83f4d-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="83f4d-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
