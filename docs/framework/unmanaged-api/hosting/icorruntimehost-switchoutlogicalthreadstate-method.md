---
title: ICorRuntimeHost::SwitchOutLogicalThreadState, méthode
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
ms.openlocfilehash: 8151531e470b149012b2dd4fca918c8937f13918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133338"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="2bdc0-102">ICorRuntimeHost::SwitchOutLogicalThreadState, méthode</span><span class="sxs-lookup"><span data-stu-id="2bdc0-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="2bdc0-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="2bdc0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bdc0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bdc0-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bdc0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2bdc0-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="2bdc0-106">à Cookie qui indique la fibre en cours de sortie.</span><span class="sxs-lookup"><span data-stu-id="2bdc0-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bdc0-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="2bdc0-107">Requirements</span></span>  
 <span data-ttu-id="2bdc0-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bdc0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bdc0-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2bdc0-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bdc0-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2bdc0-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bdc0-111">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="2bdc0-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bdc0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bdc0-112">See also</span></span>

- [<span data-ttu-id="2bdc0-113">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="2bdc0-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
