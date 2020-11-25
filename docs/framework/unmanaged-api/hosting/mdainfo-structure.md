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
ms.openlocfilehash: 8e88d90e3291d21888fae7aa162f84b6377658c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730017"
---
# <a name="mdainfo-structure"></a><span data-ttu-id="005b9-102">MDAInfo, structure</span><span class="sxs-lookup"><span data-stu-id="005b9-102">MDAInfo Structure</span></span>

<span data-ttu-id="005b9-103">Fournit des détails sur l' `Event_MDAFired` événement, qui déclenche la création d’un Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="005b9-103">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="005b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="005b9-104">Syntax</span></span>  
  
```cpp  
typedef struct _MDAInfo {  
    LPCWSTR  lpMDACaption;  
    LPCWSTR  lpMDAMessage  
} MDAInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="005b9-105">Membres</span><span class="sxs-lookup"><span data-stu-id="005b9-105">Members</span></span>  
  
|<span data-ttu-id="005b9-106">Membre</span><span class="sxs-lookup"><span data-stu-id="005b9-106">Member</span></span>|<span data-ttu-id="005b9-107">Description</span><span class="sxs-lookup"><span data-stu-id="005b9-107">Description</span></span>|  
|------------|-----------------|  
|`lpMDACaption`|<span data-ttu-id="005b9-108">Titre de l’Assistant Débogage managé actuel.</span><span class="sxs-lookup"><span data-stu-id="005b9-108">The title of the current MDA.</span></span> <span data-ttu-id="005b9-109">Le titre décrit le type d’échec qui a déclenché l' `Event_MDAFired` événement.</span><span class="sxs-lookup"><span data-stu-id="005b9-109">The title describes the kind of failure that triggered the `Event_MDAFired` event.</span></span>|  
|`lpMDAMessage`|<span data-ttu-id="005b9-110">Message de sortie fourni par l’Assistant Débogage managé actuel.</span><span class="sxs-lookup"><span data-stu-id="005b9-110">The output message provided by the current MDA.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="005b9-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="005b9-111">Remarks</span></span>  

 <span data-ttu-id="005b9-112">Les Assistants Débogage managé (MDA) sont des aides au débogage qui fonctionnent conjointement avec le common language runtime (CLR) pour effectuer des tâches telles que l’identification de conditions non valides dans le moteur d’exécution du runtime ou le vidage d’informations supplémentaires sur l’état du moteur.</span><span class="sxs-lookup"><span data-stu-id="005b9-112">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to perform tasks such as identifying invalid conditions in the runtime execution engine or dumping additional information about the state of the engine.</span></span> <span data-ttu-id="005b9-113">Les MDA génèrent des messages XML sur les événements qui, sinon, sont difficiles à intercepter.</span><span class="sxs-lookup"><span data-stu-id="005b9-113">MDAs generate XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="005b9-114">Ils sont particulièrement utiles pour déboguer des transitions entre du code managé et du code non managé.</span><span class="sxs-lookup"><span data-stu-id="005b9-114">They are especially useful for debugging transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="005b9-115">Le Runtime effectue les étapes suivantes lorsqu’un événement qui déclenche la création d’un Assistant Débogage managé est déclenché :</span><span class="sxs-lookup"><span data-stu-id="005b9-115">The runtime takes the following steps when an event that triggers the creation of an MDA is fired:</span></span>  
  
- <span data-ttu-id="005b9-116">Si l’hôte n’a pas inscrit une instance [IActionOnCLREvent](iactiononclrevent-interface.md) en appelant [ICLROnEventManager :: RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) pour être averti d’un `Event_MDAFired` événement, le runtime continue avec son comportement par défaut, non hébergé.</span><span class="sxs-lookup"><span data-stu-id="005b9-116">If the host has not registered an [IActionOnCLREvent](iactiononclrevent-interface.md) instance by calling [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) to be notified of an `Event_MDAFired` event, the runtime proceeds with its default, non-hosted behavior.</span></span>  
  
- <span data-ttu-id="005b9-117">Si l’hôte a inscrit un gestionnaire pour cet événement, le runtime vérifie si un débogueur est attaché au processus.</span><span class="sxs-lookup"><span data-stu-id="005b9-117">If the host has registered a handler for this event, the runtime checks to see whether a debugger is attached to the process.</span></span> <span data-ttu-id="005b9-118">Si c’est le cas, le runtime s’arrête dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="005b9-118">If it is, the runtime breaks into the debugger.</span></span> <span data-ttu-id="005b9-119">Quand le débogueur continue, il appelle l’hôte.</span><span class="sxs-lookup"><span data-stu-id="005b9-119">When the debugger continues, it calls into the host.</span></span> <span data-ttu-id="005b9-120">Si aucun débogueur n’est attaché, le runtime appelle `IActionOnCLREvent::OnEvent` et passe un pointeur vers une `MDAInfo` instance en tant que `data` paramètre.</span><span class="sxs-lookup"><span data-stu-id="005b9-120">If no debugger is attached, the runtime calls `IActionOnCLREvent::OnEvent` and passes a pointer to an `MDAInfo` instance as the `data` parameter.</span></span>  
  
 <span data-ttu-id="005b9-121">L’hôte peut choisir d’activer les MDA et de recevoir une notification lorsqu’un Assistant Débogage managé est activé.</span><span class="sxs-lookup"><span data-stu-id="005b9-121">The host can choose to activate MDAs and to be notified when an MDA is activated.</span></span> <span data-ttu-id="005b9-122">Cela donne à l’hôte la possibilité de substituer le comportement par défaut et d’abandonner le thread managé qui a déclenché l’événement, afin de l’empêcher de corrompre l’état du processus.</span><span class="sxs-lookup"><span data-stu-id="005b9-122">This gives the host an opportunity to override default behavior and to abort the managed thread that raised the event, to prevent it from corrupting the process state.</span></span> <span data-ttu-id="005b9-123">Pour plus d’informations sur l’utilisation des MDA, consultez [diagnostic des erreurs avec les Assistants Débogage managé](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="005b9-123">For more information about using MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="005b9-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="005b9-124">Requirements</span></span>  

 <span data-ttu-id="005b9-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="005b9-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="005b9-126">**En-tête :** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="005b9-126">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="005b9-127">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="005b9-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="005b9-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="005b9-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="005b9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="005b9-129">See also</span></span>

- [<span data-ttu-id="005b9-130">Structures d'hébergement</span><span class="sxs-lookup"><span data-stu-id="005b9-130">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="005b9-131">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="005b9-131">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
