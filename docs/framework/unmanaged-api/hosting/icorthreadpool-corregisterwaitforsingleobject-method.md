---
title: ICorThreadpool::CorRegisterWaitForSingleObject, méthode
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorRegisterWaitForSingleObject
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegisterWaitForSingleObject
helpviewer_keywords:
- ICorThreadpool::CorRegisterWaitForSingleObject method [.NET Framework hosting]
- CorRegisterWaitForSingleObject method [.NET Framework hosting]
ms.assetid: cade1feb-71d2-43ed-85ca-7b2e9da12994
topic_type:
- apiref
ms.openlocfilehash: 9f555d3119ede5eabe61467aa81d35aa5c354751
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727846"
---
# <a name="icorthreadpoolcorregisterwaitforsingleobject-method"></a><span data-ttu-id="a892c-102">ICorThreadpool::CorRegisterWaitForSingleObject, méthode</span><span class="sxs-lookup"><span data-stu-id="a892c-102">ICorThreadpool::CorRegisterWaitForSingleObject Method</span></span>

<span data-ttu-id="a892c-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a892c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a892c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a892c-104">Syntax</span></span>  
  
```cpp  
HRESULT CorRegisterWaitForSingleObject (  
    [in]  HANDLE*             phNewWaitObject,  
    [in]  HANDLE              hWaitObject,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Context,  
    [in]  ULONG               timeout,  
    [in]  BOOL                executeOnlyOnce,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a892c-105">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a892c-105">Requirements</span></span>  

 <span data-ttu-id="a892c-106">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a892c-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a892c-107">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a892c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a892c-108">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a892c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a892c-109">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a892c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a892c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a892c-110">See also</span></span>

- [<span data-ttu-id="a892c-111">ICorThreadpool, interface</span><span class="sxs-lookup"><span data-stu-id="a892c-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
