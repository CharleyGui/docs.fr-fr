---
title: ICorDebugChain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
ms.openlocfilehash: a0285970a8a42c078aa663579e1d5998d0d1c037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724453"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="0cdb8-102">ICorDebugChain, interface</span><span class="sxs-lookup"><span data-stu-id="0cdb8-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="0cdb8-103">Représente un segment d'une pile des appels physique ou logique.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cdb8-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0cdb8-104">Methods</span></span>  
  
|<span data-ttu-id="0cdb8-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-105">Method</span></span>|<span data-ttu-id="0cdb8-106">Description</span><span class="sxs-lookup"><span data-stu-id="0cdb8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cdb8-107">EnumerateFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="0cdb8-108">Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="0cdb8-109">GetActiveFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="0cdb8-110">Obtient le frame actif (c’est-à-dire le plus récent) de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="0cdb8-111">GetCallee, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="0cdb8-112">Obtient la chaîne qui a été appelée par cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="0cdb8-113">GetCaller, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="0cdb8-114">Obtient la chaîne qui a appelé cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="0cdb8-115">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="0cdb8-116">Non implémenté.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-116">Not implemented.</span></span>|  
|[<span data-ttu-id="0cdb8-117">GetNext, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="0cdb8-118">Obtient la chaîne suivante de frames pour le thread.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="0cdb8-119">GetPrevious, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="0cdb8-120">Obtient la chaîne précédente des frames pour le thread.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="0cdb8-121">GetReason, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="0cdb8-122">Obtient la raison pour le Genesis de cette chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="0cdb8-123">GetRegisterSet, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="0cdb8-124">Obtient le Registre défini pour la partie active de cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="0cdb8-125">GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="0cdb8-126">Obtient la plage d’adresses du segment de pile pour cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="0cdb8-127">GetThread, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="0cdb8-128">Obtient le thread physique dont fait partie cette chaîne d’appel.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="0cdb8-129">IsManaged, méthode</span><span class="sxs-lookup"><span data-stu-id="0cdb8-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="0cdb8-130">Obtient une valeur qui indique si cette chaîne exécute du code managé.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cdb8-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="0cdb8-131">Remarks</span></span>  

 <span data-ttu-id="0cdb8-132">Les frames de pile dans une chaîne occupent un espace de pile contigu et partagent le même thread et le même contexte.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="0cdb8-133">Une chaîne peut représenter des chaînes de code managées ou non managées.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="0cdb8-134">Une `ICorDebugChain` instance vide représente une chaîne de code non managé.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cdb8-135">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="0cdb8-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cdb8-136">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0cdb8-136">Requirements</span></span>  

 <span data-ttu-id="0cdb8-137">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cdb8-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cdb8-138">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cdb8-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cdb8-139">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cdb8-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cdb8-140">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cdb8-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdb8-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cdb8-141">See also</span></span>

- [<span data-ttu-id="0cdb8-142">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0cdb8-142">Debugging Interfaces</span></span>](debugging-interfaces.md)
