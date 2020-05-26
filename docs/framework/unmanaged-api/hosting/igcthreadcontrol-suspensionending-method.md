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
ms.openlocfilehash: 8300daf0d39745ceda80f6c56da7e3c459a97468
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805117"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="4f9b5-102">IGCThreadControl::SuspensionEnding, méthode</span><span class="sxs-lookup"><span data-stu-id="4f9b5-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="4f9b5-103">Indique à l’hôte que le runtime reprend les threads après une garbage collection ou une autre suspension.</span><span class="sxs-lookup"><span data-stu-id="4f9b5-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f9b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f9b5-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f9b5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f9b5-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="4f9b5-106">dans Génération sur laquelle une garbage collection a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="4f9b5-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f9b5-107">Notes</span><span class="sxs-lookup"><span data-stu-id="4f9b5-107">Remarks</span></span>  
 <span data-ttu-id="4f9b5-108">Ne replanifiez pas de threads pendant le `SuspensionEnding` rappel.</span><span class="sxs-lookup"><span data-stu-id="4f9b5-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f9b5-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4f9b5-109">Requirements</span></span>  
 <span data-ttu-id="4f9b5-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f9b5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f9b5-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4f9b5-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f9b5-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4f9b5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f9b5-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f9b5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9b5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4f9b5-114">See also</span></span>

- [<span data-ttu-id="4f9b5-115">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="4f9b5-115">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
