---
title: ICorDebugThread3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 7cddf860f044e8493a0fdf6023b2853ac16c5b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137500"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="916e7-102">ICorDebugThread3, interface</span><span class="sxs-lookup"><span data-stu-id="916e7-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="916e7-103">Fournit le point d’entrée pour [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) et les interfaces correspondantes.</span><span class="sxs-lookup"><span data-stu-id="916e7-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="916e7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="916e7-104">Methods</span></span>  
  
|<span data-ttu-id="916e7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="916e7-105">Method</span></span>|<span data-ttu-id="916e7-106">Description</span><span class="sxs-lookup"><span data-stu-id="916e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="916e7-107">CreateStackWalk, méthode</span><span class="sxs-lookup"><span data-stu-id="916e7-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="916e7-108">Crée un objet [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="916e7-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="916e7-109">GetActiveInternalFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="916e7-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="916e7-110">Retourne un tableau de frames internes (objets[ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) ) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="916e7-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="916e7-111">Notes</span><span class="sxs-lookup"><span data-stu-id="916e7-111">Remarks</span></span>  
 <span data-ttu-id="916e7-112">`ICorDebugThread3` est une extension logique de l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="916e7-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="916e7-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="916e7-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="916e7-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="916e7-114">Requirements</span></span>  
 <span data-ttu-id="916e7-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="916e7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="916e7-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="916e7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="916e7-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="916e7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="916e7-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="916e7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="916e7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="916e7-119">See also</span></span>

- [<span data-ttu-id="916e7-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="916e7-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="916e7-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="916e7-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
