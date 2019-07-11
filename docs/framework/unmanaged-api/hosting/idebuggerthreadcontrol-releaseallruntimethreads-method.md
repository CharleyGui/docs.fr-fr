---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads, méthode
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09895294c4678cdb1dd033076cfb42853aa06b2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780505"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="0247f-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="0247f-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="0247f-103">Avertit l’hôte que les services de débogage sont sur le point de mise en production de tous les threads qui sont bloqués.</span><span class="sxs-lookup"><span data-stu-id="0247f-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0247f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0247f-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="0247f-105">Notes</span><span class="sxs-lookup"><span data-stu-id="0247f-105">Remarks</span></span>  
 <span data-ttu-id="0247f-106">Le `ReleaseAllRuntimeThreads` méthode ne sera jamais appelée sur un thread d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0247f-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="0247f-107">Si l’hôte a un thread du runtime bloqué, il doit le libérer maintenant.</span><span class="sxs-lookup"><span data-stu-id="0247f-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0247f-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0247f-108">Requirements</span></span>  
 <span data-ttu-id="0247f-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0247f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0247f-110">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0247f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0247f-111">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0247f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0247f-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0247f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0247f-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0247f-113">See also</span></span>

- [<span data-ttu-id="0247f-114">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="0247f-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
