---
title: IGCThreadControl::SuspensionEnding, méthode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134785"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="8aea8-102">IGCThreadControl::SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="8aea8-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="8aea8-103">Indique à l’hôte que le runtime reprend les threads après une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="8aea8-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aea8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8aea8-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aea8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8aea8-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="8aea8-106">dans Génération sur laquelle une garbage collection a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="8aea8-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aea8-107">Notes</span><span class="sxs-lookup"><span data-stu-id="8aea8-107">Remarks</span></span>  
 <span data-ttu-id="8aea8-108">Ne replanifiez pas de threads pendant le rappel `SuspensionEnding`.</span><span class="sxs-lookup"><span data-stu-id="8aea8-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aea8-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="8aea8-109">Requirements</span></span>  
 <span data-ttu-id="8aea8-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aea8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aea8-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8aea8-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8aea8-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8aea8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8aea8-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aea8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aea8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aea8-114">See also</span></span>

- [<span data-ttu-id="8aea8-115">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="8aea8-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
