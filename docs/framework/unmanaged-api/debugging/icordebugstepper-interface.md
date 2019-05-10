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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f1d94ffde71962c848bece808bf2d982093896a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652166"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="51429-102">ICorDebugStepper, interface</span><span class="sxs-lookup"><span data-stu-id="51429-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="51429-103">Représente dans l'exécution du code une étape qui est effectuée par un débogueur, et qui sert d'identificateur entre l'émission et l'achèvement d'une commande tout en offrant un moyen d'annuler une étape.</span><span class="sxs-lookup"><span data-stu-id="51429-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51429-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="51429-104">Methods</span></span>  
  
|<span data-ttu-id="51429-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="51429-105">Method</span></span>|<span data-ttu-id="51429-106">Description</span><span class="sxs-lookup"><span data-stu-id="51429-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51429-107">Deactivate, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="51429-108">Cela entraîne `ICorDebugStepper` pour annuler la dernière commande reçue.</span><span class="sxs-lookup"><span data-stu-id="51429-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="51429-109">IsActive, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="51429-110">Obtient une valeur qui indique si ce `ICorDebugStepper` exécute actuellement une étape.</span><span class="sxs-lookup"><span data-stu-id="51429-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="51429-111">SetInterceptMask, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="51429-112">Définit une valeur CorDebugIntercept qui spécifie les types de code sont détaillé.</span><span class="sxs-lookup"><span data-stu-id="51429-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="51429-113">SetRangeIL, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="51429-114">Définit une valeur qui indique si les appels à [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) valeurs d’argument par rapport à du code natif ou pour le code Microsoft intermediate language (MSIL) de la méthode qui est en cours a présenté.</span><span class="sxs-lookup"><span data-stu-id="51429-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="51429-115">SetUnmappedStopMask, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="51429-116">Définit une valeur CorDebugUnmappedStop qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.</span><span class="sxs-lookup"><span data-stu-id="51429-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="51429-117">Step, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="51429-118">Cela entraîne `ICorDebugStepper` à pas son thread conteneur et éventuellement, continuez le pas à pas via des fonctions appelées dans le thread.</span><span class="sxs-lookup"><span data-stu-id="51429-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="51429-119">StepOut, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="51429-120">Cela entraîne `ICorDebugStepper` à pas son thread conteneur et se termine lorsque le frame actuel retourne le contrôle au frame appelant.</span><span class="sxs-lookup"><span data-stu-id="51429-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="51429-121">StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="51429-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="51429-122">Cela entraîne `ICorDebugStepper` à pas son thread conteneur et à retourner lorsqu’il atteint le code au-delà de la dernière des plages spécifiées.</span><span class="sxs-lookup"><span data-stu-id="51429-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51429-123">Notes</span><span class="sxs-lookup"><span data-stu-id="51429-123">Remarks</span></span>  
 <span data-ttu-id="51429-124">Le `ICorDebugStepper` interface utilisé aux fins suivantes :</span><span class="sxs-lookup"><span data-stu-id="51429-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
- <span data-ttu-id="51429-125">Il agit comme un identificateur entre une commande d’étape qui est émise et la fin de cette commande.</span><span class="sxs-lookup"><span data-stu-id="51429-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
- <span data-ttu-id="51429-126">Il fournit une interface centrale pour encapsuler le pas à pas qui peut être effectuée.</span><span class="sxs-lookup"><span data-stu-id="51429-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
- <span data-ttu-id="51429-127">Elle offre un moyen prématurément annuler une opération pas à pas.</span><span class="sxs-lookup"><span data-stu-id="51429-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="51429-128">Il peut y avoir plus d’une exécution pas à pas par thread.</span><span class="sxs-lookup"><span data-stu-id="51429-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="51429-129">Par exemple, un point d’arrêt peut être atteint lors de l’exécution pas à pas sur une fonction, et l’utilisateur peut souhaiter démarrer une nouvelle opération pas à pas à l’intérieur de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="51429-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="51429-130">Il incombe au débogueur de déterminer comment gérer cette situation.</span><span class="sxs-lookup"><span data-stu-id="51429-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="51429-131">Le débogueur peut être amené à annuler l’opération pas à pas d’origine ou imbriquer les deux opérations.</span><span class="sxs-lookup"><span data-stu-id="51429-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="51429-132">Le `ICorDebugStepper` interface prend en charge les deux choix.</span><span class="sxs-lookup"><span data-stu-id="51429-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="51429-133">Une exécution pas à pas peut migrer entre des threads si le common language runtime (CLR) effectue un appel marshalé entre les threads.</span><span class="sxs-lookup"><span data-stu-id="51429-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51429-134">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="51429-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51429-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="51429-135">Requirements</span></span>  
 <span data-ttu-id="51429-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51429-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51429-137">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51429-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51429-138">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51429-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51429-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51429-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51429-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51429-140">See also</span></span>

- [<span data-ttu-id="51429-141">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="51429-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
