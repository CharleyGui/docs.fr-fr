---
title: ICorDebugController, interface
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
ms.openlocfilehash: d6c923f03309da3ad8092ea6119e7d850120ee2c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783803"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="d83bb-102">ICorDebugController, interface</span><span class="sxs-lookup"><span data-stu-id="d83bb-102">ICorDebugController Interface</span></span>

<span data-ttu-id="d83bb-103">Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.</span><span class="sxs-lookup"><span data-stu-id="d83bb-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d83bb-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d83bb-104">Methods</span></span>  
  
|<span data-ttu-id="d83bb-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-105">Method</span></span>|<span data-ttu-id="d83bb-106">Description</span><span class="sxs-lookup"><span data-stu-id="d83bb-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="d83bb-107">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="d83bb-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="d83bb-108">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="d83bb-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="d83bb-109">Continue, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="d83bb-110">Reprend l’exécution des threads managés après un appel à [ICorDebugController :: Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="d83bb-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="d83bb-111">Detach, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="d83bb-112">Détache le débogueur du processus ou du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="d83bb-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="d83bb-113">EnumerateThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="d83bb-114">Obtient un énumérateur pour les threads managés actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d83bb-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="d83bb-115">HasQueuedCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="d83bb-116">Obtient une valeur qui indique si tous les rappels managés sont actuellement mis en file d’attente pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="d83bb-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="d83bb-117">IsRunning, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="d83bb-118">Obtient une valeur qui indique si les threads du processus sont en cours d’exécution librement.</span><span class="sxs-lookup"><span data-stu-id="d83bb-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="d83bb-119">SetAllThreadsDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="d83bb-120">Définit l’état de débogage de tous les threads managés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d83bb-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="d83bb-121">Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="d83bb-122">Exécute un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d83bb-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="d83bb-123">Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="d83bb-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="d83bb-124">Termine le processus avec le code de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="d83bb-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d83bb-125">Notes</span><span class="sxs-lookup"><span data-stu-id="d83bb-125">Remarks</span></span>  
 <span data-ttu-id="d83bb-126">Si `ICorDebugController` contrôle un processus, l’étendue comprend tous les threads du processus.</span><span class="sxs-lookup"><span data-stu-id="d83bb-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="d83bb-127">Si `ICorDebugController` contrôle un domaine d’application, l’étendue comprend uniquement les threads de ce domaine d’application particulier.</span><span class="sxs-lookup"><span data-stu-id="d83bb-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d83bb-128">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d83bb-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d83bb-129">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d83bb-129">Requirements</span></span>  
 <span data-ttu-id="d83bb-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d83bb-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d83bb-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d83bb-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d83bb-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d83bb-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d83bb-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d83bb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83bb-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d83bb-134">See also</span></span>

- [<span data-ttu-id="d83bb-135">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d83bb-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
