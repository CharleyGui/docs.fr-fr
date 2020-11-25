---
title: IGCThreadControl::SuspensionStarting, méthode
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 9d39ee79f7734f7dd099a07640ecb06f4f8dcbb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721658"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="1dd9c-102">IGCThreadControl::SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="1dd9c-102">IGCThreadControl::SuspensionStarting Method</span></span>

<span data-ttu-id="1dd9c-103">Indique à l’hôte que le runtime commence une suspension de thread pour une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="1dd9c-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dd9c-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="1dd9c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="1dd9c-105">Remarks</span></span>  

 <span data-ttu-id="1dd9c-106">Ne replanifiez pas de threads pendant le `SuspensionStarting` rappel.</span><span class="sxs-lookup"><span data-stu-id="1dd9c-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd9c-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1dd9c-107">Requirements</span></span>  

 <span data-ttu-id="1dd9c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd9c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd9c-109">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1dd9c-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dd9c-110">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1dd9c-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd9c-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd9c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd9c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1dd9c-112">See also</span></span>

- [<span data-ttu-id="1dd9c-113">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="1dd9c-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
