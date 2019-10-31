---
title: ICorThreadpool::CorCreateTimer, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
ms.openlocfilehash: 17afd0922930bc6db122e8dc07125dcafd483cf5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133306"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="99fe3-102">ICorThreadpool::CorCreateTimer, méthode</span><span class="sxs-lookup"><span data-stu-id="99fe3-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="99fe3-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="99fe3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fe3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99fe3-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="99fe3-105">spécifications</span><span class="sxs-lookup"><span data-stu-id="99fe3-105">Requirements</span></span>  
 <span data-ttu-id="99fe3-106">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99fe3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fe3-107">**Header:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99fe3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99fe3-108">**Library:** Included as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99fe3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99fe3-109">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fe3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fe3-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99fe3-110">See also</span></span>

- [<span data-ttu-id="99fe3-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="99fe3-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
