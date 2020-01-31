---
title: ICorDebugEnum, interface
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: cc5598f9cbec4b97bb75f83fb18ccf8742904272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783011"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="c91df-102">ICorDebugEnum, interface</span><span class="sxs-lookup"><span data-stu-id="c91df-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="c91df-103">Sert d’interface de base abstraite pour les énumérateurs utilisés par une application de débogage.</span><span class="sxs-lookup"><span data-stu-id="c91df-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c91df-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="c91df-104">Methods</span></span>  
  
|<span data-ttu-id="c91df-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="c91df-105">Method</span></span>|<span data-ttu-id="c91df-106">Description</span><span class="sxs-lookup"><span data-stu-id="c91df-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c91df-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="c91df-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="c91df-108">Crée une copie de cet objet `ICorDebugEnum`.</span><span class="sxs-lookup"><span data-stu-id="c91df-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="c91df-109">GetCount, méthode</span><span class="sxs-lookup"><span data-stu-id="c91df-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="c91df-110">Obtient le nombre d’éléments dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c91df-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="c91df-111">Reset, méthode</span><span class="sxs-lookup"><span data-stu-id="c91df-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="c91df-112">Déplace le curseur au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c91df-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="c91df-113">Skip, méthode</span><span class="sxs-lookup"><span data-stu-id="c91df-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="c91df-114">Déplace le curseur vers l’avant dans l’énumération d’après le nombre d’éléments spécifié.</span><span class="sxs-lookup"><span data-stu-id="c91df-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c91df-115">Notes</span><span class="sxs-lookup"><span data-stu-id="c91df-115">Remarks</span></span>  
 <span data-ttu-id="c91df-116">Les énumérateurs suivants dérivent de `ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="c91df-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="c91df-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="c91df-118">"ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="c91df-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="c91df-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="c91df-121">"ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="c91df-122">"ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="c91df-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="c91df-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="c91df-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="c91df-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="c91df-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="c91df-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="c91df-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="c91df-130">"ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="c91df-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="c91df-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="c91df-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="c91df-134">"ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="c91df-135">"ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="c91df-136">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="c91df-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="c91df-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="c91df-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="c91df-138">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="c91df-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c91df-139">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="c91df-139">Requirements</span></span>  
 <span data-ttu-id="c91df-140">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c91df-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c91df-141">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c91df-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c91df-142">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c91df-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c91df-143">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c91df-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c91df-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c91df-144">See also</span></span>

- [<span data-ttu-id="c91df-145">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c91df-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
