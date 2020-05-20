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
ms.openlocfilehash: 4e72cd8bee2cb4f35155d7b99cfe8d9cf63f463a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616071"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="f1223-102">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="f1223-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="f1223-103">Fournit la méthode [IActionOnCLREvent :: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) , qui exécute des rappels sur les événements qui ont été inscrits à l’aide d’un appel à la méthode [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f1223-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1223-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f1223-104">Methods</span></span>  
  
|<span data-ttu-id="f1223-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f1223-105">Method</span></span>|<span data-ttu-id="f1223-106">Description</span><span class="sxs-lookup"><span data-stu-id="f1223-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1223-107">OnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="f1223-107">OnEvent Method</span></span>](iactiononclrevent-onevent-method.md)|<span data-ttu-id="f1223-108">Exécute un rappel pour un événement inscrit.</span><span class="sxs-lookup"><span data-stu-id="f1223-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1223-109">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f1223-109">Requirements</span></span>  
 <span data-ttu-id="f1223-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1223-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1223-111">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f1223-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1223-112">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1223-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1223-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1223-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1223-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1223-114">See also</span></span>

- [<span data-ttu-id="f1223-115">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="f1223-115">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="f1223-116">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="f1223-116">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="f1223-117">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="f1223-117">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="f1223-118">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="f1223-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
