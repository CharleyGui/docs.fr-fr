---
title: MDAInfo, structure
ms.date: 03/30/2017
api_name:
- MDAInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MDAInfo
helpviewer_keywords:
- MDAInfo structure [.NET Framework hosting]
ms.assetid: fb8c14f7-d461-43d1-8b47-adb6723b9b93
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 198141545119976cb9107bc9c09b913572e266ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781125"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="7e304-102">MDAInfo, structure</span><span class="sxs-lookup"><span data-stu-id="7e304-102">MDAInfo Structure</span></span>
<span data-ttu-id="7e304-103">Fournit des détails sur la `Event_MDAFired` événement qui déclenche la création d’un assistant débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="7e304-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e304-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e304-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="7e304-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7e304-105">Members</span></span>  
  
|<span data-ttu-id="7e304-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7e304-106">Member</span></span>|<span data-ttu-id="7e304-107">Description</span><span class="sxs-lookup"><span data-stu-id="7e304-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="7e304-108">Le titre de l’Assistant Débogage MANAGÉ actuel.</span><span class="sxs-lookup"><span data-stu-id="7e304-108">The title of the current MDA.</span></span> <span data-ttu-id="7e304-109">Le titre décrit le genre d’échec qui a déclenché le `Event_MDAFired` événement.</span><span class="sxs-lookup"><span data-stu-id="7e304-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="7e304-110">Le message de sortie fourni par l’Assistant Débogage MANAGÉ actuel.</span><span class="sxs-lookup"><span data-stu-id="7e304-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e304-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7e304-111">Remarks</span></span>  
 <span data-ttu-id="7e304-112">Les Assistants Débogage managé (MDA) sont outils de débogage qui fonctionnent conjointement avec le common language runtime (CLR) pour effectuer des tâches telles que l’identification des conditions non valides dans le moteur d’exécution ou d’immersion des informations supplémentaires sur l’état de la moteur.</span><span class="sxs-lookup"><span data-stu-id="7e304-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="7e304-113">Les MDA génèrent des messages XML sur les événements qui sont difficiles à intercepter.</span><span class="sxs-lookup"><span data-stu-id="7e304-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="7e304-114">Ils sont particulièrement utiles pour déboguer des transitions entre code managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="7e304-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="7e304-115">Le runtime entreprend les actions suivantes lorsqu’un événement qui déclenche la création d’un Assistant Débogage MANAGÉ est déclenché :</span><span class="sxs-lookup"><span data-stu-id="7e304-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="7e304-116">Si l’hôte n’a pas inscrit un [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance en appelant [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) recevoir les notifications d’un `Event_MDAFired` événement, le runtime continue avec son comportement par défaut, non hébergé.</span><span class="sxs-lookup"><span data-stu-id="7e304-116">If the host has not registered an [IActionOnCLREvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="7e304-117">Si l’hôte a inscrit un gestionnaire pour cet événement, le runtime vérifie si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="7e304-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="7e304-118">Dans le cas, le runtime arrête le débogueur.</span><span class="sxs-lookup"><span data-stu-id="7e304-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="7e304-119">Lorsque le débogueur continue, il appelle l’hôte.</span><span class="sxs-lookup"><span data-stu-id="7e304-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="7e304-120">Si aucun débogueur n’est attaché, le runtime appelle `IActionOnCLREvent::OnEvent` et passe un pointeur vers un `MDAInfo` instance en tant que le `data` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7e304-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="7e304-121">L’hôte peut choisir d’activer les MDA et d’être notifié lorsqu’un MDA est activé.</span><span class="sxs-lookup"><span data-stu-id="7e304-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="7e304-122">Cela donne la possibilité de substituer le comportement par défaut et d’abandonner le thread managé qui a déclenché l’événement, pour empêcher d’endommager l’état du processus de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="7e304-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="7e304-123">Pour plus d’informations sur l’utilisation des Assistants Débogage managé, consultez [diagnostic d’erreurs avec les Assistants Débogage managé](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="7e304-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e304-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7e304-124">Requirements</span></span>  
 <span data-ttu-id="7e304-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e304-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e304-126">**En-tête :** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="7e304-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="7e304-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7e304-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e304-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e304-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e304-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e304-129">See also</span></span>

- [<span data-ttu-id="7e304-130">Structures d’hébergement</span><span class="sxs-lookup"><span data-stu-id="7e304-130">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="7e304-131">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="7e304-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
