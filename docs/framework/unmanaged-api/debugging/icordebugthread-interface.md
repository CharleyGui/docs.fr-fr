---
title: ICorDebugThread, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133499"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="3c306-102">ICorDebugThread, interface</span><span class="sxs-lookup"><span data-stu-id="3c306-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="3c306-103">Représente un thread de processus.</span><span class="sxs-lookup"><span data-stu-id="3c306-103">Represents a thread in a process.</span></span> <span data-ttu-id="3c306-104">La durée de vie d'une instance `ICorDebugThread` est la même que la durée de vie du thread qu'elle représente.</span><span class="sxs-lookup"><span data-stu-id="3c306-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c306-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3c306-105">Methods</span></span>  
  
|<span data-ttu-id="3c306-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-106">Method</span></span>|<span data-ttu-id="3c306-107">Description</span><span class="sxs-lookup"><span data-stu-id="3c306-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c306-108">ClearCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="3c306-109">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="3c306-109">This method is not implemented.</span></span> <span data-ttu-id="3c306-110">Ne pas l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="3c306-110">Do not use it.</span></span>|  
|[<span data-ttu-id="3c306-111">CreateEval, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="3c306-112">Crée un objet ICorDebugEval qui fonctionne sur cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-113">CreateStepper, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="3c306-114">Crée un objet ICorDebugStepper qui permet d’effectuer un pas à pas détaillé dans le frame actif dans cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-115">EnumerateChains, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="3c306-116">Obtient un pointeur d’interface vers un énumérateur ICorDebugChainEnum qui contient toutes les chaînes de pile de cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-117">GetActiveChain, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="3c306-118">Obtient un pointeur d’interface vers l’ICorDebugChain actif sur cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-119">GetActiveFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="3c306-120">Obtient un pointeur d’interface vers le ICorDebugFrame actif sur cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-121">GetAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="3c306-122">Obtient un pointeur d’interface vers le domaine d’application dans lequel ce `ICorDebugThread` est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3c306-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="3c306-123">GetCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="3c306-124">Obtient un pointeur d’interface vers un objet ICorDebugValue qui représente une exception actuellement levée par du code managé.</span><span class="sxs-lookup"><span data-stu-id="3c306-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="3c306-125">GetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="3c306-126">Obtient une valeur CorDebugThreadState qui décrit l’état de débogage actuel de ce `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-127">GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="3c306-128">Obtient le handle actuel pour la partie active de cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-129">GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="3c306-130">Obtient l’identificateur de système d’exploitation actuel de la partie active de ce `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-131">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="3c306-132">Obtient un pointeur d’interface vers le thread common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3c306-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="3c306-133">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="3c306-134">Obtient un pointeur d’interface vers le processus dont ce `ICorDebugThread` forme un composant.</span><span class="sxs-lookup"><span data-stu-id="3c306-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="3c306-135">GetRegisterSet, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="3c306-136">Obtient un pointeur d’interface vers le jeu de registres associé à ce `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-137">GetUserState, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="3c306-138">Obtient une combinaison d’opérations de bits de valeurs CorDebugUserState, qui décrivent l’état actuel de cette `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="3c306-139">SetDebugState, méthode</span><span class="sxs-lookup"><span data-stu-id="3c306-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="3c306-140">Définit une combinaison au niveau du bit des valeurs `CorDebugThreadState` qui décrivent l’état de débogage de ce `ICorDebugThread`.</span><span class="sxs-lookup"><span data-stu-id="3c306-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c306-141">Notes</span><span class="sxs-lookup"><span data-stu-id="3c306-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c306-142">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="3c306-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c306-143">spécifications</span><span class="sxs-lookup"><span data-stu-id="3c306-143">Requirements</span></span>  
 <span data-ttu-id="3c306-144">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c306-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c306-145">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c306-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c306-146">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c306-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c306-147">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c306-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c306-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3c306-148">See also</span></span>

- [<span data-ttu-id="3c306-149">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3c306-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
