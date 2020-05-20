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
ms.openlocfilehash: 30312e6e09535cee2968b1f9e8ac87b461c5ff40
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703516"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="7001c-102">ICLROnEventManager, interface</span><span class="sxs-lookup"><span data-stu-id="7001c-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="7001c-103">Fournit des méthodes qui permettent à l’hôte d’inscrire et d’annuler l’enregistrement des rappels pour les événements common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7001c-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7001c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7001c-104">Methods</span></span>  
  
|<span data-ttu-id="7001c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7001c-105">Method</span></span>|<span data-ttu-id="7001c-106">Description</span><span class="sxs-lookup"><span data-stu-id="7001c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7001c-107">RegisterActionOnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="7001c-107">RegisterActionOnEvent Method</span></span>](iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="7001c-108">Inscrit un pointeur de rappel pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="7001c-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="7001c-109">UnregisterActionOnEvent, méthode</span><span class="sxs-lookup"><span data-stu-id="7001c-109">UnregisterActionOnEvent Method</span></span>](iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="7001c-110">Annule l’inscription d’un pointeur de rappel précédemment inscrit pour l’événement spécifié.</span><span class="sxs-lookup"><span data-stu-id="7001c-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7001c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7001c-111">Remarks</span></span>  
 <span data-ttu-id="7001c-112">Pour inscrire et désinscrire des rappels d’événements, l’hôte obtient une référence à `ICLROnEventManager` en appelant la méthode [ICLRControl :: GetCLRManager](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7001c-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7001c-113">Les événements décrits par [EClrEvent](eclrevent-enumeration.md) peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.</span><span class="sxs-lookup"><span data-stu-id="7001c-113">The events described by [EClrEvent](eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7001c-114">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="7001c-114">Requirements</span></span>  
 <span data-ttu-id="7001c-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7001c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7001c-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7001c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7001c-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7001c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7001c-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7001c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7001c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7001c-119">See also</span></span>

- [<span data-ttu-id="7001c-120">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="7001c-120">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="7001c-121">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="7001c-121">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="7001c-122">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="7001c-122">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7001c-123">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="7001c-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
