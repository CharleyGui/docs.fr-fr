---
title: ICorDebugProcess, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: ab48efccc88787f099a182627777db95304cdc3e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212072"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="59364-102">ICorDebugProcess, interface</span><span class="sxs-lookup"><span data-stu-id="59364-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="59364-103">Représente un processus qui exécute le code managé.</span><span class="sxs-lookup"><span data-stu-id="59364-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="59364-104">Cette interface est une sous-classe de ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="59364-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59364-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="59364-105">Methods</span></span>  
  
|<span data-ttu-id="59364-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="59364-106">Method</span></span>|<span data-ttu-id="59364-107">Description</span><span class="sxs-lookup"><span data-stu-id="59364-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59364-108">ClearCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-108">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="59364-109">Efface l’exception non managée actuelle sur le thread donné.</span><span class="sxs-lookup"><span data-stu-id="59364-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="59364-110">EnableLogMessages, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-110">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="59364-111">Active et désactive l’envoi des messages du journal au débogueur.</span><span class="sxs-lookup"><span data-stu-id="59364-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="59364-112">EnumerateAppDomains, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-112">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="59364-113">Énumère tous les domaines d’application dans le processus.</span><span class="sxs-lookup"><span data-stu-id="59364-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="59364-114">EnumerateObjects, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-114">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="59364-115">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="59364-115">Not implemented.</span></span>|  
|[<span data-ttu-id="59364-116">GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-116">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="59364-117">Obtient un handle pour le processus.</span><span class="sxs-lookup"><span data-stu-id="59364-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="59364-118">GetHelperThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-118">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="59364-119">Obtient l’ID de thread du système d’exploitation pour le thread d’assistance interne du débogueur.</span><span class="sxs-lookup"><span data-stu-id="59364-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="59364-120">GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-120">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="59364-121">Obtient l’ID (se) du système d’exploitation du processus.</span><span class="sxs-lookup"><span data-stu-id="59364-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="59364-122">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-122">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="59364-123">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="59364-123">Not implemented.</span></span>|  
|[<span data-ttu-id="59364-124">GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-124">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="59364-125">Obtient l’instance de ICorDebugThread qui a l’ID de thread de système d’exploitation spécifié.</span><span class="sxs-lookup"><span data-stu-id="59364-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="59364-126">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-126">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="59364-127">Obtient le contexte pour le thread donné.</span><span class="sxs-lookup"><span data-stu-id="59364-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="59364-128">IsOSSuspended, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-128">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="59364-129">Détermine si le thread a été suspendu à la suite de l’arrêt du processus par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="59364-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="59364-130">IsTransitionStub, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-130">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="59364-131">Détermine si une adresse se trouve à l’intérieur d’un stub qui entraîne une transition vers du code managé.</span><span class="sxs-lookup"><span data-stu-id="59364-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="59364-132">ModifyLogSwitch, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-132">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="59364-133">Définit le niveau de gravité du commutateur de journalisation spécifié.</span><span class="sxs-lookup"><span data-stu-id="59364-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="59364-134">ReadMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-134">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="59364-135">Lit la mémoire à partir du processus.</span><span class="sxs-lookup"><span data-stu-id="59364-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="59364-136">SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-136">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="59364-137">Définit le contexte du thread donné.</span><span class="sxs-lookup"><span data-stu-id="59364-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="59364-138">ThreadForFiberCookie, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-138">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="59364-139">Action déconseillée.</span><span class="sxs-lookup"><span data-stu-id="59364-139">Deprecated.</span></span>|  
|[<span data-ttu-id="59364-140">WriteMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="59364-140">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="59364-141">Écrit des données dans une zone de mémoire dans le processus.</span><span class="sxs-lookup"><span data-stu-id="59364-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59364-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="59364-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59364-143">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="59364-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59364-144">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59364-144">Requirements</span></span>  
 <span data-ttu-id="59364-145">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59364-145">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59364-146">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59364-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59364-147">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59364-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59364-148">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59364-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59364-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59364-149">See also</span></span>

- [<span data-ttu-id="59364-150">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="59364-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="59364-151">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="59364-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
