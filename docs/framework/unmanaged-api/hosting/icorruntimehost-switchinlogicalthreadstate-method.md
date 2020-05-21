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
ms.openlocfilehash: d830635b911fa5d80382e432f283c455c41af7a8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762680"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="a188e-102">ICorRuntimeHost::SwitchInLogicalThreadState, méthode</span><span class="sxs-lookup"><span data-stu-id="a188e-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="a188e-103">Cette m&#233;thode prend en charge l'infrastructure .NET Framework et n'est pas destin&#233;e &#224; &#234;tre utilis&#233;e directement &#224; partir de votre code.</span><span class="sxs-lookup"><span data-stu-id="a188e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a188e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a188e-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a188e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a188e-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="a188e-106">dans Cookie qui indique la fibre à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a188e-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a188e-107">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="a188e-107">Requirements</span></span>  
 <span data-ttu-id="a188e-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a188e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a188e-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a188e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a188e-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a188e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a188e-111">**Version de .NET Framework :** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="a188e-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a188e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a188e-112">See also</span></span>

- [<span data-ttu-id="a188e-113">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a188e-113">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
