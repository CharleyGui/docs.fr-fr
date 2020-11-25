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
ms.openlocfilehash: 8ca4bb1fe35451f95f752a4e71f5f0b541b55e58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721775"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="c08e8-102">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="c08e8-102">IActionOnCLREvent Interface</span></span>

<span data-ttu-id="c08e8-103">Fournit la méthode [IActionOnCLREvent :: OnEvent](iactiononclrevent-onevent-method.md) , qui exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c08e8-103">Provides the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c08e8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c08e8-104">Methods</span></span>  
  
|<span data-ttu-id="c08e8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c08e8-105">Method</span></span>|<span data-ttu-id="c08e8-106">Description</span><span class="sxs-lookup"><span data-stu-id="c08e8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c08e8-107">OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="c08e8-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="c08e8-108">Exécute un rappel pour un événement inscrit.</span><span class="sxs-lookup"><span data-stu-id="c08e8-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c08e8-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c08e8-109">Requirements</span></span>  

 <span data-ttu-id="c08e8-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c08e8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c08e8-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c08e8-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c08e8-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c08e8-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c08e8-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c08e8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c08e8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c08e8-114">See also</span></span>

- [<span data-ttu-id="c08e8-115">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="c08e8-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="c08e8-116">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="c08e8-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c08e8-117">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="c08e8-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="c08e8-118">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="c08e8-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
