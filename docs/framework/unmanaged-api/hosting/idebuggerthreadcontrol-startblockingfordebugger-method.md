---
title: IDebuggerThreadControl::StartBlockingForDebugger, méthode
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 1e0cb52a6b9f03209256e5398415b4ec632fb5e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705502"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="3c147-102">IDebuggerThreadControl::StartBlockingForDebugger, méthode</span><span class="sxs-lookup"><span data-stu-id="3c147-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="3c147-103">Avertit l’hôte que les services de débogage sont sur le paragraphe duquel ils commencent à bloquer tous les threads.</span><span class="sxs-lookup"><span data-stu-id="3c147-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c147-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c147-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c147-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3c147-105">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="3c147-106">[in] Réservé pour une future utilisation.</span><span class="sxs-lookup"><span data-stu-id="3c147-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c147-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="3c147-107">Remarks</span></span>  

 <span data-ttu-id="3c147-108">La `StartBlockingForDebugger` méthode peut être appelée sur un thread d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3c147-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c147-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3c147-109">Requirements</span></span>  

 <span data-ttu-id="3c147-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c147-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c147-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3c147-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c147-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c147-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c147-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c147-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c147-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c147-114">See also</span></span>

- [<span data-ttu-id="3c147-115">IDebuggerThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="3c147-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
