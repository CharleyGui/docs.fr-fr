---
title: ICorDebugThread2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: 49d0015e9d8390a47aae7ce497dd431dfe743c36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138679"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="b0484-102">ICorDebugThread2, interface</span><span class="sxs-lookup"><span data-stu-id="b0484-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="b0484-103">Sert d’extension logique à l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b0484-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0484-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="b0484-104">Methods</span></span>  
  
|<span data-ttu-id="b0484-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="b0484-105">Method</span></span>|<span data-ttu-id="b0484-106">Description</span><span class="sxs-lookup"><span data-stu-id="b0484-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0484-107">GetActiveFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="b0484-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="b0484-108">Obtient un tableau d’instances COR_ACTIVE_FUNCTION qui contiennent les données relatives aux fonctions actives dans les frames d’un thread.</span><span class="sxs-lookup"><span data-stu-id="b0484-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="b0484-109">GetConnectionID, méthode</span><span class="sxs-lookup"><span data-stu-id="b0484-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="b0484-110">Obtient un identificateur de connexion pour ce `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="b0484-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="b0484-111">GetTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="b0484-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="b0484-112">Obtient un identificateur de tâche pour ce `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="b0484-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="b0484-113">GetVolatileOSThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="b0484-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="b0484-114">Obtient l’identificateur de thread de système d’exploitation pour ce `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="b0484-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="b0484-115">InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="b0484-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="b0484-116">Permet à un débogueur d’intercepter l’exception actuelle sur un thread.</span><span class="sxs-lookup"><span data-stu-id="b0484-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0484-117">Notes</span><span class="sxs-lookup"><span data-stu-id="b0484-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0484-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="b0484-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0484-119">spécifications</span><span class="sxs-lookup"><span data-stu-id="b0484-119">Requirements</span></span>  
 <span data-ttu-id="b0484-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0484-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0484-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0484-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0484-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0484-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0484-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0484-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0484-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0484-124">See also</span></span>

- [<span data-ttu-id="b0484-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="b0484-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
