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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2a083f46f24d6f3f24c63dd2415b85f975cfa29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912848"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="e23a2-102">ICorDebugController, interface</span><span class="sxs-lookup"><span data-stu-id="e23a2-102">ICorDebugController Interface</span></span>

<span data-ttu-id="e23a2-103">Représente une portée, un <xref:System.Diagnostics.Process> ou un <xref:System.AppDomain>, où le contexte d'exécution du code peut être contrôlé.</span><span class="sxs-lookup"><span data-stu-id="e23a2-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e23a2-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="e23a2-104">Methods</span></span>  
  
|<span data-ttu-id="e23a2-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-105">Method</span></span>|<span data-ttu-id="e23a2-106">Description</span><span class="sxs-lookup"><span data-stu-id="e23a2-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="e23a2-107">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="e23a2-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="e23a2-108">Cette méthode est obsolète.</span><span class="sxs-lookup"><span data-stu-id="e23a2-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="e23a2-109">Continue, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="e23a2-110">Reprend l’exécution des threads managés après un appel à [ICorDebugController:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="e23a2-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="e23a2-111">Detach, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="e23a2-112">Détache le débogueur du processus ou du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e23a2-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="e23a2-113">EnumerateThreads, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="e23a2-114">Obtient un énumérateur pour les threads managés actifs dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e23a2-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="e23a2-115">HasQueuedCallbacks, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="e23a2-116">Obtient une valeur qui indique si tous les rappels managés sont actuellement mis en file d’attente pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="e23a2-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="e23a2-117">IsRunning, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="e23a2-118">Obtient une valeur qui indique si les threads du processus sont en cours d’exécution librement.</span><span class="sxs-lookup"><span data-stu-id="e23a2-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="e23a2-119">SetAllThreadsDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="e23a2-120">Définit l’état de débogage de tous les threads managés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e23a2-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="e23a2-121">Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="e23a2-122">Exécute un arrêt coopératif sur tous les threads qui exécutent du code managé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e23a2-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="e23a2-123">Terminate, méthode</span><span class="sxs-lookup"><span data-stu-id="e23a2-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="e23a2-124">Termine le processus avec le code de sortie spécifié.</span><span class="sxs-lookup"><span data-stu-id="e23a2-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e23a2-125">Notes</span><span class="sxs-lookup"><span data-stu-id="e23a2-125">Remarks</span></span>  
 <span data-ttu-id="e23a2-126">Si `ICorDebugController` contrôle un processus, l’étendue comprend tous les threads du processus.</span><span class="sxs-lookup"><span data-stu-id="e23a2-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="e23a2-127">Si `ICorDebugController` contrôle un domaine d’application, l’étendue comprend uniquement les threads de ce domaine d’application particulier.</span><span class="sxs-lookup"><span data-stu-id="e23a2-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e23a2-128">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="e23a2-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e23a2-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e23a2-129">Requirements</span></span>  
 <span data-ttu-id="e23a2-130">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e23a2-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e23a2-131">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e23a2-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e23a2-132">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e23a2-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e23a2-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e23a2-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e23a2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e23a2-134">See also</span></span>

- [<span data-ttu-id="e23a2-135">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="e23a2-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
