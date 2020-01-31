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
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791388"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="1efd3-102">ICorDebugThread3, interface</span><span class="sxs-lookup"><span data-stu-id="1efd3-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="1efd3-103">Fournit le point d’entrée pour [ICorDebugStackWalk](icordebugstackwalk-interface.md) et les interfaces correspondantes.</span><span class="sxs-lookup"><span data-stu-id="1efd3-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1efd3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1efd3-104">Methods</span></span>  
  
|<span data-ttu-id="1efd3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1efd3-105">Method</span></span>|<span data-ttu-id="1efd3-106">Description</span><span class="sxs-lookup"><span data-stu-id="1efd3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1efd3-107">CreateStackWalk, méthode</span><span class="sxs-lookup"><span data-stu-id="1efd3-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="1efd3-108">Crée un objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="1efd3-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="1efd3-109">GetActiveInternalFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="1efd3-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="1efd3-110">Retourne un tableau de frames internes (objets[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="1efd3-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1efd3-111">Notes</span><span class="sxs-lookup"><span data-stu-id="1efd3-111">Remarks</span></span>  
 <span data-ttu-id="1efd3-112">`ICorDebugThread3` est une extension logique de l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1efd3-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1efd3-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="1efd3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1efd3-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="1efd3-114">Requirements</span></span>  
 <span data-ttu-id="1efd3-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1efd3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1efd3-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1efd3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1efd3-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1efd3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1efd3-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1efd3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efd3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1efd3-119">See also</span></span>

- [<span data-ttu-id="1efd3-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1efd3-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1efd3-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="1efd3-121">Debugging</span></span>](index.md)
