---
title: ICorDebugManagedCallback2::MDANotification, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
ms.openlocfilehash: 09a410f54ddf07c9a5f6bb7dd34f2aaf266e0734
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704576"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="c4751-102">ICorDebugManagedCallback2::MDANotification, méthode</span><span class="sxs-lookup"><span data-stu-id="c4751-102">ICorDebugManagedCallback2::MDANotification Method</span></span>

<span data-ttu-id="c4751-103">Fournit une notification indiquant que l’exécution du code a rencontré un Assistant Débogage managé (MDA) dans l’application en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="c4751-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4751-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4751-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4751-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c4751-105">Parameters</span></span>  

 `pController`  
 <span data-ttu-id="c4751-106">dans Pointeur vers une interface ICorDebugController qui expose le processus ou le domaine d’application dans lequel l’Assistant Débogage managé s’est produit.</span><span class="sxs-lookup"><span data-stu-id="c4751-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="c4751-107">Un débogueur ne doit pas faire d’hypothèses indiquant si le contrôleur est un processus ou un domaine d’application, bien qu’il puisse toujours interroger l’interface pour effectuer une détermination.</span><span class="sxs-lookup"><span data-stu-id="c4751-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="c4751-108">dans Pointeur vers une interface ICorDebugThread qui expose le thread managé sur lequel l’événement de débogage s’est produit.</span><span class="sxs-lookup"><span data-stu-id="c4751-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="c4751-109">Si l’Assistant Débogage managé s’est produit sur un thread non managé, la valeur de `pThread` est null.</span><span class="sxs-lookup"><span data-stu-id="c4751-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="c4751-110">Vous devez récupérer l’ID de thread du système d’exploitation à partir de l’objet MDA lui-même.</span><span class="sxs-lookup"><span data-stu-id="c4751-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="c4751-111">dans Pointeur vers une interface [ICorDebugMDA](icordebugmda-interface.md) qui expose les informations de l’Assistant Débogage managé.</span><span class="sxs-lookup"><span data-stu-id="c4751-111">[in] A pointer to an [ICorDebugMDA](icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4751-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="c4751-112">Remarks</span></span>  

 <span data-ttu-id="c4751-113">Un Assistant Débogage managé est un avertissement heuristique et ne nécessite aucune action explicite du débogueur, à l’exception de l’appel de [ICorDebugController :: continue](icordebugcontroller-continue-method.md) pour reprendre l’exécution de l’application en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="c4751-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="c4751-114">Le common language runtime (CLR) peut déterminer les MDA déclenchés et les données qui se trouvent dans un MDA donné à tout moment.</span><span class="sxs-lookup"><span data-stu-id="c4751-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="c4751-115">Par conséquent, les débogueurs ne doivent pas générer de fonctionnalités nécessitant des modèles d’Assistant Débogage managé spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c4751-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="c4751-116">Les MDA peuvent être mis en file d’attente et déclenchés peu après que l’Assistant Débogage managé a été rencontré.</span><span class="sxs-lookup"><span data-stu-id="c4751-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="c4751-117">Cela peut se produire si le runtime doit attendre qu’il atteigne un point de sécurité pour déclencher l’Assistant Débogage managé, au lieu de déclencher l’Assistant Débogage managé lorsqu’il le rencontre.</span><span class="sxs-lookup"><span data-stu-id="c4751-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="c4751-118">Cela signifie également que le runtime peut déclencher plusieurs MDA dans un ensemble unique de rappels mis en file d’attente (semblable à une opération d’événement d’attachement).</span><span class="sxs-lookup"><span data-stu-id="c4751-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="c4751-119">Un débogueur doit libérer la référence à une `ICorDebugMDA` instance immédiatement après avoir retourné le `MDANotification` rappel, pour permettre au CLR de recycler la mémoire consommée par un MDA.</span><span class="sxs-lookup"><span data-stu-id="c4751-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="c4751-120">La libération de l’instance peut améliorer les performances si de nombreux MDA sont déclenchés.</span><span class="sxs-lookup"><span data-stu-id="c4751-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4751-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c4751-121">Requirements</span></span>  

 <span data-ttu-id="c4751-122">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4751-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4751-123">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4751-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4751-124">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4751-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4751-125">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4751-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4751-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4751-126">See also</span></span>

- [<span data-ttu-id="c4751-127">Diagnostic d'erreurs avec les Assistants de débogage managés</span><span class="sxs-lookup"><span data-stu-id="c4751-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c4751-128">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="c4751-128">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="c4751-129">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="c4751-129">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
