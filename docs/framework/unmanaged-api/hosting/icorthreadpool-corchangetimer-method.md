---
title: ICorThreadpool::CorChangeTimer, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d1733b423b2c49de3c36fc5448f7f24da1b5c44
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751335"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="29748-102">ICorThreadpool::CorChangeTimer, méthode</span><span class="sxs-lookup"><span data-stu-id="29748-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="29748-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="29748-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29748-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29748-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,   
    [in]  ULONG  DueTime,   
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="29748-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="29748-105">Requirements</span></span>  
 <span data-ttu-id="29748-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29748-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29748-107">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29748-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29748-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29748-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29748-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29748-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29748-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29748-110">See also</span></span>

- [<span data-ttu-id="29748-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="29748-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
