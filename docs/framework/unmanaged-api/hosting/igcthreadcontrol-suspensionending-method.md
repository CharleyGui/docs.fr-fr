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
ms.openlocfilehash: 4638672b1d64a9ea07618212cc514d00996470eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721671"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="0e98f-102">IGCThreadControl::SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="0e98f-102">IGCThreadControl::SuspensionEnding Method</span></span>

<span data-ttu-id="0e98f-103">Indique à l’hôte que le runtime reprend les threads après une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="0e98f-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e98f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e98f-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e98f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0e98f-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="0e98f-106">dans Génération sur laquelle une garbage collection a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="0e98f-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e98f-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="0e98f-107">Remarks</span></span>  

 <span data-ttu-id="0e98f-108">Ne replanifiez pas de threads pendant le `SuspensionEnding` rappel.</span><span class="sxs-lookup"><span data-stu-id="0e98f-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e98f-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0e98f-109">Requirements</span></span>  

 <span data-ttu-id="0e98f-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e98f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e98f-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e98f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e98f-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e98f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e98f-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e98f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e98f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e98f-114">See also</span></span>

- [<span data-ttu-id="0e98f-115">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="0e98f-115">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
