---
title: ICorRuntimeHost::SwitchInLogicalThreadState, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
ms.openlocfilehash: b6569b5dab89a88a24cf2dfc873da9740e5af505
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133380"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="152e9-102">ICorRuntimeHost::SwitchInLogicalThreadState, méthode</span><span class="sxs-lookup"><span data-stu-id="152e9-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="152e9-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="152e9-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="152e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="152e9-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="152e9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="152e9-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="152e9-106">dans Cookie qui indique la fibre à utiliser.</span><span class="sxs-lookup"><span data-stu-id="152e9-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152e9-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="152e9-107">Requirements</span></span>  
 <span data-ttu-id="152e9-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="152e9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152e9-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="152e9-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="152e9-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="152e9-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="152e9-111">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="152e9-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152e9-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="152e9-112">See also</span></span>

- [<span data-ttu-id="152e9-113">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="152e9-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
