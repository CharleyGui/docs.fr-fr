---
title: IActionOnCLREvent, interface
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
ms.openlocfilehash: 9277fe2c241ce4f502339de826dccd08a2ce8055
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126958"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="94554-102">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="94554-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="94554-103">Fournit la méthode [IActionOnCLREvent :: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , qui exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="94554-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94554-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="94554-104">Methods</span></span>  
  
|<span data-ttu-id="94554-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="94554-105">Method</span></span>|<span data-ttu-id="94554-106">Description</span><span class="sxs-lookup"><span data-stu-id="94554-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94554-107">OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="94554-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="94554-108">Exécute un rappel pour un événement inscrit.</span><span class="sxs-lookup"><span data-stu-id="94554-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94554-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="94554-109">Requirements</span></span>  
 <span data-ttu-id="94554-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94554-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94554-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="94554-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94554-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="94554-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94554-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94554-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94554-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94554-114">See also</span></span>

- [<span data-ttu-id="94554-115">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="94554-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="94554-116">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="94554-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="94554-117">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="94554-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="94554-118">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="94554-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
