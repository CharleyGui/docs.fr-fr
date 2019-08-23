---
title: ICorDebugStackWalk, interface
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06ce2da435df9458ca59d76fa426becbede2e619
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959674"
---
# <a name="icordebugstackwalk-interface"></a><span data-ttu-id="263a1-102">ICorDebugStackWalk, interface</span><span class="sxs-lookup"><span data-stu-id="263a1-102">ICorDebugStackWalk Interface</span></span>
<span data-ttu-id="263a1-103">Fournit des méthodes pour obtenir les méthodes managées, ou frames, sur la pile d'un thread.</span><span class="sxs-lookup"><span data-stu-id="263a1-103">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="263a1-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="263a1-104">Methods</span></span>  
  
|<span data-ttu-id="263a1-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="263a1-105">Method</span></span>|<span data-ttu-id="263a1-106">Description</span><span class="sxs-lookup"><span data-stu-id="263a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="263a1-107">GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="263a1-107">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|<span data-ttu-id="263a1-108">Retourne le contexte du frame actuel dans l' `ICorDebugStackWalk` objet.</span><span class="sxs-lookup"><span data-stu-id="263a1-108">Returns the context for the current frame in the `ICorDebugStackWalk` object.</span></span>|  
|[<span data-ttu-id="263a1-109">SetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="263a1-109">SetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|<span data-ttu-id="263a1-110">Définit le `ICorDebugStackWalk` contexte actuel de l’objet sur un contexte valide pour le thread.</span><span class="sxs-lookup"><span data-stu-id="263a1-110">Sets the `ICorDebugStackWalk` object’s current context to a valid context for the thread.</span></span>|  
|[<span data-ttu-id="263a1-111">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="263a1-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|<span data-ttu-id="263a1-112">Déplace l' `ICorDebugStackWalk` objet vers le frame suivant.</span><span class="sxs-lookup"><span data-stu-id="263a1-112">Moves the `ICorDebugStackWalk` object to the next frame.</span></span>|  
|[<span data-ttu-id="263a1-113">GetFrame, méthode</span><span class="sxs-lookup"><span data-stu-id="263a1-113">GetFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|<span data-ttu-id="263a1-114">Obtient le frame actuel dans l' `ICorDebugStackWalk` objet.</span><span class="sxs-lookup"><span data-stu-id="263a1-114">Gets the current frame in the `ICorDebugStackWalk` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="263a1-115">Notes</span><span class="sxs-lookup"><span data-stu-id="263a1-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="263a1-116">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="263a1-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263a1-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="263a1-117">Requirements</span></span>  
 <span data-ttu-id="263a1-118">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="263a1-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263a1-119">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="263a1-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="263a1-120">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="263a1-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="263a1-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263a1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263a1-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="263a1-122">See also</span></span>

- [<span data-ttu-id="263a1-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="263a1-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="263a1-124">Débogage</span><span class="sxs-lookup"><span data-stu-id="263a1-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
