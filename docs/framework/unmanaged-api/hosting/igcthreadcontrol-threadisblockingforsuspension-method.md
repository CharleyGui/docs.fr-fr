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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8609b32ad2dea699b5b248b2b8bb3d81ec744043
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779478"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="78d7d-102">IGCThreadControl::ThreadIsBlockingForSuspension, méthode</span><span class="sxs-lookup"><span data-stu-id="78d7d-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="78d7d-103">Avertit l’hôte que le thread qui effectue l’appel va bloquer, peut-être pour une opération garbage collection ou une suspension.</span><span class="sxs-lookup"><span data-stu-id="78d7d-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78d7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78d7d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="78d7d-105">Notes</span><span class="sxs-lookup"><span data-stu-id="78d7d-105">Remarks</span></span>  
 <span data-ttu-id="78d7d-106">L’hôte peut choisir dans le `ThreadIsBlockingForSuspension` rappel s’il faut replanifier un thread.</span><span class="sxs-lookup"><span data-stu-id="78d7d-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78d7d-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="78d7d-107">Requirements</span></span>  
 <span data-ttu-id="78d7d-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78d7d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78d7d-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="78d7d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="78d7d-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="78d7d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78d7d-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78d7d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78d7d-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78d7d-112">See also</span></span>

- [<span data-ttu-id="78d7d-113">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="78d7d-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
