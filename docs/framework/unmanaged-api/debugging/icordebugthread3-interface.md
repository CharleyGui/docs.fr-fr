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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378704"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="9e4e0-102">ICorDebugThread3, interface</span><span class="sxs-lookup"><span data-stu-id="9e4e0-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="9e4e0-103">Fournit le point d’entrée pour [ICorDebugStackWalk](icordebugstackwalk-interface.md) et les interfaces correspondantes.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e4e0-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9e4e0-104">Methods</span></span>  
  
|<span data-ttu-id="9e4e0-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9e4e0-105">Method</span></span>|<span data-ttu-id="9e4e0-106">Description</span><span class="sxs-lookup"><span data-stu-id="9e4e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e4e0-107">CreateStackWalk, méthode</span><span class="sxs-lookup"><span data-stu-id="9e4e0-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="9e4e0-108">Crée un objet [ICorDebugStackWalk](icordebugstackwalk-interface.md) pour le thread dont vous souhaitez dérouler la pile.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="9e4e0-109">GetActiveInternalFrames, méthode</span><span class="sxs-lookup"><span data-stu-id="9e4e0-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="9e4e0-110">Retourne un tableau de frames internes (objets[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) ) sur la pile.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e4e0-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="9e4e0-111">Remarks</span></span>  
 <span data-ttu-id="9e4e0-112">`ICorDebugThread3`est une extension logique de l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e4e0-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="9e4e0-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e4e0-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9e4e0-114">Requirements</span></span>  
 <span data-ttu-id="9e4e0-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e4e0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e4e0-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e4e0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e4e0-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e4e0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e4e0-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e4e0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4e0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e4e0-119">See also</span></span>

- [<span data-ttu-id="9e4e0-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9e4e0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9e4e0-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="9e4e0-121">Debugging</span></span>](index.md)
