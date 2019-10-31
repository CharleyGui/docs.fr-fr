---
title: EClrEvent, énumération
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131135"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="86cb6-102">EClrEvent, énumération</span><span class="sxs-lookup"><span data-stu-id="86cb6-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="86cb6-103">Décrit les événements common language runtime (CLR) pour lesquels l’hôte peut inscrire des rappels.</span><span class="sxs-lookup"><span data-stu-id="86cb6-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86cb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86cb6-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="86cb6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="86cb6-105">Members</span></span>  
  
|<span data-ttu-id="86cb6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="86cb6-106">Member</span></span>|<span data-ttu-id="86cb6-107">Description</span><span class="sxs-lookup"><span data-stu-id="86cb6-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="86cb6-108">Spécifie une erreur CLR irrécupérable.</span><span class="sxs-lookup"><span data-stu-id="86cb6-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="86cb6-109">Spécifie le déchargement d’un <xref:System.AppDomain>particulier.</span><span class="sxs-lookup"><span data-stu-id="86cb6-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="86cb6-110">Spécifie qu’un message de l’Assistant Débogage managé (MDA) a été généré.</span><span class="sxs-lookup"><span data-stu-id="86cb6-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="86cb6-111">Spécifie qu’une erreur de dépassement de capacité de la pile s’est produite.</span><span class="sxs-lookup"><span data-stu-id="86cb6-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86cb6-112">Notes</span><span class="sxs-lookup"><span data-stu-id="86cb6-112">Remarks</span></span>  
 <span data-ttu-id="86cb6-113">L’hôte peut enregistrer des rappels pour tous les types d’événements décrits par `EClrEvent` en appelant des méthodes de l’interface [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="86cb6-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="86cb6-114">L’hôte obtient un pointeur vers cette interface en appelant la méthode [ICLRControl :: GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="86cb6-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="86cb6-115">Les événements `Event_CLRDisabled` et `Event_DomainUnload` peuvent être déclenchés plusieurs fois et à partir de différents threads pour signaler un déchargement ou la désactivation du CLR.</span><span class="sxs-lookup"><span data-stu-id="86cb6-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="86cb6-116">L’événement `Event_MDAFired` déclenche la création d’une instance [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) qui contient les détails du message de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="86cb6-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="86cb6-117">Pour plus d’informations sur les MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="86cb6-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86cb6-118">spécifications</span><span class="sxs-lookup"><span data-stu-id="86cb6-118">Requirements</span></span>  
 <span data-ttu-id="86cb6-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86cb6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86cb6-120">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="86cb6-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86cb6-121">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="86cb6-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86cb6-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86cb6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86cb6-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86cb6-123">See also</span></span>

- [<span data-ttu-id="86cb6-124">IActionOnCLREvent, interface</span><span class="sxs-lookup"><span data-stu-id="86cb6-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="86cb6-125">ICLRControl, interface</span><span class="sxs-lookup"><span data-stu-id="86cb6-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="86cb6-126">Énumérations d’hébergement</span><span class="sxs-lookup"><span data-stu-id="86cb6-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
