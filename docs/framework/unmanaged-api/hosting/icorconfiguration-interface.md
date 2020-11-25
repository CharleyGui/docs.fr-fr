---
title: ICorConfiguration, interface
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
ms.openlocfilehash: fa8d15bc8e504a57d5cc87c170a3a5b022798add
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715782"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="93ca7-102">ICorConfiguration, interface</span><span class="sxs-lookup"><span data-stu-id="93ca7-102">ICorConfiguration Interface</span></span>

<span data-ttu-id="93ca7-103">Fournit des méthodes pour configurer le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="93ca7-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93ca7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="93ca7-104">Methods</span></span>  
  
|<span data-ttu-id="93ca7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="93ca7-105">Method</span></span>|<span data-ttu-id="93ca7-106">Description</span><span class="sxs-lookup"><span data-stu-id="93ca7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93ca7-107">AddDebuggerSpecialThread, méthode</span><span class="sxs-lookup"><span data-stu-id="93ca7-107">AddDebuggerSpecialThread Method</span></span>](icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="93ca7-108">Indique aux services de débogage qu’un thread particulier doit pouvoir continuer à s’exécuter pendant que le débogueur a une application arrêtée pendant des scénarios de débogage managés ou non managés.</span><span class="sxs-lookup"><span data-stu-id="93ca7-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="93ca7-109">SetDebuggerThreadControl, méthode</span><span class="sxs-lookup"><span data-stu-id="93ca7-109">SetDebuggerThreadControl Method</span></span>](icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="93ca7-110">Définit l’interface de rappel que les services de débogage appellera en tant que threads CLR sont bloqués et débloqués pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="93ca7-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="93ca7-111">SetGCHostControl, méthode</span><span class="sxs-lookup"><span data-stu-id="93ca7-111">SetGCHostControl Method</span></span>](icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="93ca7-112">Définit l’interface de rappel que le garbage collector doit utiliser pour demander à l’hôte de modifier les limites de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="93ca7-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="93ca7-113">SetGCThreadControl, méthode</span><span class="sxs-lookup"><span data-stu-id="93ca7-113">SetGCThreadControl Method</span></span>](icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="93ca7-114">Définit l’interface de rappel pour les threads de planification pour les tâches non-Runtime qui seraient sinon bloquées pour un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="93ca7-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93ca7-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93ca7-115">Requirements</span></span>  

 <span data-ttu-id="93ca7-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93ca7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93ca7-117">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="93ca7-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93ca7-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93ca7-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93ca7-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93ca7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93ca7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93ca7-120">See also</span></span>

- [<span data-ttu-id="93ca7-121">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="93ca7-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="93ca7-122">CorRuntimeHost, coclasse</span><span class="sxs-lookup"><span data-stu-id="93ca7-122">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
