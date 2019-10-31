---
title: IGCThreadControl::ThreadIsBlockingForSuspension, méthode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: e6534c3085b70b590c2dcc3f50cf0253bd5e6682
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134747"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="9aa9e-102">IGCThreadControl::ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="9aa9e-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="9aa9e-103">Avertit l’hôte que le thread qui effectue l’appel est sur le présent bloqué, peut-être pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="9aa9e-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aa9e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9aa9e-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="9aa9e-105">Notes</span><span class="sxs-lookup"><span data-stu-id="9aa9e-105">Remarks</span></span>  
 <span data-ttu-id="9aa9e-106">L’hôte peut choisir dans le `ThreadIsBlockingForSuspension` rappel s’il faut replanifier un thread.</span><span class="sxs-lookup"><span data-stu-id="9aa9e-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aa9e-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="9aa9e-107">Requirements</span></span>  
 <span data-ttu-id="9aa9e-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aa9e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aa9e-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9aa9e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9aa9e-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9aa9e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aa9e-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9aa9e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa9e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aa9e-112">See also</span></span>

- [<span data-ttu-id="9aa9e-113">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="9aa9e-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
