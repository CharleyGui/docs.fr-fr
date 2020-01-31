---
title: ICorDebugManagedCallback2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793315"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="63c0c-102">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="63c0c-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="63c0c-103">Fournit des méthodes pour prendre en charge la gestion des exceptions et les Assistants Débogage managé (MDA) du débogueur.</span><span class="sxs-lookup"><span data-stu-id="63c0c-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="63c0c-104">`ICorDebugManagedCallback2` est une extension logique de l’interface [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="63c0c-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63c0c-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="63c0c-105">Methods</span></span>  
  
|<span data-ttu-id="63c0c-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-106">Method</span></span>|<span data-ttu-id="63c0c-107">Description</span><span class="sxs-lookup"><span data-stu-id="63c0c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63c0c-108">ChangeConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-108">ChangeConnection Method</span></span>](icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="63c0c-109">Notifie le débogueur que l’ensemble des tâches associées à la connexion spécifiée a changé.</span><span class="sxs-lookup"><span data-stu-id="63c0c-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="63c0c-110">CreateConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-110">CreateConnection Method</span></span>](icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="63c0c-111">Notifie le débogueur qu’une nouvelle connexion a été créée.</span><span class="sxs-lookup"><span data-stu-id="63c0c-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="63c0c-112">DestroyConnection, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-112">DestroyConnection Method</span></span>](icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="63c0c-113">Notifie le débogueur que la connexion spécifiée a été arrêtée.</span><span class="sxs-lookup"><span data-stu-id="63c0c-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="63c0c-114">Exception, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-114">Exception Method</span></span>](icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="63c0c-115">Notifie le débogueur qu’une recherche d’un gestionnaire d’exceptions a démarré.</span><span class="sxs-lookup"><span data-stu-id="63c0c-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="63c0c-116">ExceptionUnwind, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-116">ExceptionUnwind Method</span></span>](icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="63c0c-117">Fournit une notification d’État pendant le processus de déroulement de l’exception.</span><span class="sxs-lookup"><span data-stu-id="63c0c-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="63c0c-118">FunctionRemapComplete, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-118">FunctionRemapComplete Method</span></span>](icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="63c0c-119">Notifie le débogueur que l’exécution du code a basculé vers une nouvelle version d’une fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="63c0c-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="63c0c-120">FunctionRemapOpportunity, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-120">FunctionRemapOpportunity Method</span></span>](icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="63c0c-121">Notifie le débogueur que l’exécution du code a atteint un point de séquence dans une version antérieure d’une fonction modifiée.</span><span class="sxs-lookup"><span data-stu-id="63c0c-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="63c0c-122">MDANotification, méthode</span><span class="sxs-lookup"><span data-stu-id="63c0c-122">MDANotification Method</span></span>](icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="63c0c-123">Fournit une notification indiquant que l’exécution du code a rencontré un message de l’Assistant Débogage managé (MDA).</span><span class="sxs-lookup"><span data-stu-id="63c0c-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c0c-124">Notes</span><span class="sxs-lookup"><span data-stu-id="63c0c-124">Remarks</span></span>  
 <span data-ttu-id="63c0c-125">L’interface `ICorDebugManagedCallback2` étend l’interface `ICorDebugManagedCallback` pour gérer les nouveaux événements de débogage introduits dans le .NET Framework version 2,0.</span><span class="sxs-lookup"><span data-stu-id="63c0c-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="63c0c-126">Un débogueur doit implémenter `ICorDebugManagedCallback2` s’il débogue des applications .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="63c0c-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="63c0c-127">Une instance de `ICorDebugManagedCallback` ou `ICorDebugManagedCallback2` est passée en tant qu’objet de rappel à [ICorDebug :: SetManagedHandler](icordebug-setmanagedhandler-method.md).</span><span class="sxs-lookup"><span data-stu-id="63c0c-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63c0c-128">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="63c0c-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63c0c-129">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="63c0c-129">Requirements</span></span>  
 <span data-ttu-id="63c0c-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63c0c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63c0c-131">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63c0c-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63c0c-132">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63c0c-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63c0c-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63c0c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63c0c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63c0c-134">See also</span></span>

- [<span data-ttu-id="63c0c-135">Diagnostic d’erreurs avec les Assistants Débogage managé</span><span class="sxs-lookup"><span data-stu-id="63c0c-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="63c0c-136">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="63c0c-136">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="63c0c-137">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="63c0c-137">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
