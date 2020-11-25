---
title: ICorDebugStepper, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
ms.openlocfilehash: 8b5bbb65034e5b715532397c9ecc650da9aee912
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718291"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="9e0f0-102">ICorDebugStepper, interface</span><span class="sxs-lookup"><span data-stu-id="9e0f0-102">ICorDebugStepper Interface</span></span>

<span data-ttu-id="9e0f0-103">Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e0f0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9e0f0-104">Methods</span></span>  
  
|<span data-ttu-id="9e0f0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-105">Method</span></span>|<span data-ttu-id="9e0f0-106">Description</span><span class="sxs-lookup"><span data-stu-id="9e0f0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e0f0-107">Deactivate, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-107">Deactivate Method</span></span>](icordebugstepper-deactivate-method.md)|<span data-ttu-id="9e0f0-108">Entraîne `ICorDebugStepper` l’annulation de la dernière commande d’étape qu’il a reçue.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="9e0f0-109">IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-109">IsActive Method</span></span>](icordebugstepper-isactive-method.md)|<span data-ttu-id="9e0f0-110">Obtient une valeur qui indique si ce `ICorDebugStepper` exécute actuellement une étape.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="9e0f0-111">SetInterceptMask, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-111">SetInterceptMask Method</span></span>](icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="9e0f0-112">Définit une valeur CorDebugIntercept, qui spécifie les types de code qui sont en escalier.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="9e0f0-113">SetRangeIL, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-113">SetRangeIL Method</span></span>](icordebugstepper-setrangeil-method.md)|<span data-ttu-id="9e0f0-114">Définit une valeur qui indique si les appels à [ICorDebugStepper :: StepRange](icordebugstepper-steprange-method.md) passent des valeurs d’argument relatives au code natif ou au code MSIL (Microsoft Intermediate Language) de la méthode qui fait l’objet d’un pas à pas.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="9e0f0-115">SetUnmappedStopMask, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-115">SetUnmappedStopMask Method</span></span>](icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="9e0f0-116">Définit une valeur CorDebugUnmappedStop, qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="9e0f0-117">Step, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-117">Step Method</span></span>](icordebugstepper-step-method.md)|<span data-ttu-id="9e0f0-118">Entraîne l' `ICorDebugStepper` exécution d’une étape unique dans le thread qui le contient et, éventuellement, à la poursuite d’un pas à pas détaillé dans les fonctions appelées dans le thread.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="9e0f0-119">StepOut, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-119">StepOut Method</span></span>](icordebugstepper-stepout-method.md)|<span data-ttu-id="9e0f0-120">Provoque l' `ICorDebugStepper` exécution d’une étape unique dans le thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="9e0f0-121">StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="9e0f0-121">StepRange Method</span></span>](icordebugstepper-steprange-method.md)|<span data-ttu-id="9e0f0-122">Provoque `ICorDebugStepper` un pas à pas détaillé dans le thread conteneur et le retourne lorsqu’il atteint le code au-delà de la dernière des plages spécifiées.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e0f0-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="9e0f0-123">Remarks</span></span>  

 <span data-ttu-id="9e0f0-124">L' `ICorDebugStepper` interface remplit les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="9e0f0-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="9e0f0-125">Il agit comme un identificateur entre une commande d’étape qui est émise et l’achèvement de cette commande.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="9e0f0-126">Il fournit une interface centrale pour encapsuler toutes les exécutions pas à pas qui peuvent être effectuées.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="9e0f0-127">Il offre un moyen d’annuler prématurément une opération pas à pas.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="9e0f0-128">Il peut y avoir plusieurs exécutions pas à pas par thread.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="9e0f0-129">Par exemple, un point d’arrêt peut être atteint pendant le pas à pas principal d’une fonction, et l’utilisateur peut souhaiter démarrer une nouvelle opération pas à pas dans cette fonction.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="9e0f0-130">Il revient au débogueur de déterminer comment gérer cette situation.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="9e0f0-131">Le débogueur peut vouloir annuler l’opération pas à pas d’origine ou imbriquer les deux opérations.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="9e0f0-132">L' `ICorDebugStepper` interface prend en charge les deux options.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="9e0f0-133">Une exécution pas à pas peut migrer entre les threads si le common language runtime (CLR) effectue un appel marshalé entre les threads.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e0f0-134">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="9e0f0-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e0f0-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9e0f0-135">Requirements</span></span>  

 <span data-ttu-id="9e0f0-136">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e0f0-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e0f0-137">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e0f0-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e0f0-138">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e0f0-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e0f0-139">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e0f0-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e0f0-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e0f0-140">See also</span></span>

- [<span data-ttu-id="9e0f0-141">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9e0f0-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
