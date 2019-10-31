---
title: ICLROnEventManager, interface
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140841"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="1ed30-102">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="1ed30-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="1ed30-103">Fournit des méthodes qui permettent à l’hôte d’inscrire et d’annuler l’enregistrement des rappels pour les événements common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1ed30-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ed30-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1ed30-104">Methods</span></span>  
  
|<span data-ttu-id="1ed30-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1ed30-105">Method</span></span>|<span data-ttu-id="1ed30-106">Description</span><span class="sxs-lookup"><span data-stu-id="1ed30-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ed30-107">RegisterActionOnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="1ed30-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="1ed30-108">Inscrit un pointeur de rappel pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ed30-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="1ed30-109">UnregisterActionOnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="1ed30-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="1ed30-110">Annule l’inscription d’un pointeur de rappel précédemment inscrit pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="1ed30-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ed30-111">Notes</span><span class="sxs-lookup"><span data-stu-id="1ed30-111">Remarks</span></span>  
 <span data-ttu-id="1ed30-112">Pour inscrire et désinscrire des rappels d’événements, l’hôte obtient une référence à `ICLROnEventManager` en appelant la méthode [ICLRControl :: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1ed30-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ed30-113">Les événements décrits par [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.</span><span class="sxs-lookup"><span data-stu-id="1ed30-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ed30-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="1ed30-114">Requirements</span></span>  
 <span data-ttu-id="1ed30-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ed30-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed30-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1ed30-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1ed30-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1ed30-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1ed30-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ed30-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed30-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ed30-119">See also</span></span>

- [<span data-ttu-id="1ed30-120">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="1ed30-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="1ed30-121">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="1ed30-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="1ed30-122">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="1ed30-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="1ed30-123">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="1ed30-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
