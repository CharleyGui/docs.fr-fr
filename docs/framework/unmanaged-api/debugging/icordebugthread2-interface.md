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
ms.openlocfilehash: fdaad46b739721ff95b712d4b6461a793ae0a480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791431"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="507d7-102">ICorDebugThread2, interface</span><span class="sxs-lookup"><span data-stu-id="507d7-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="507d7-103">Sert d’extension logique à l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="507d7-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="507d7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="507d7-104">Methods</span></span>  
  
|<span data-ttu-id="507d7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="507d7-105">Method</span></span>|<span data-ttu-id="507d7-106">Description</span><span class="sxs-lookup"><span data-stu-id="507d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="507d7-107">GetActiveFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="507d7-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="507d7-108">Obtient un tableau d’instances de COR_ACTIVE_FUNCTION qui contiennent des données relatives aux fonctions actives dans les frames d’un thread.</span><span class="sxs-lookup"><span data-stu-id="507d7-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="507d7-109">GetConnectionID, méthode</span><span class="sxs-lookup"><span data-stu-id="507d7-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="507d7-110">Obtient un identificateur de connexion pour ce `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="507d7-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="507d7-111">GetTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="507d7-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="507d7-112">Obtient un identificateur de tâche pour ce `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="507d7-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="507d7-113">GetVolatileOSThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="507d7-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="507d7-114">Obtient l’identificateur de thread de système d’exploitation pour ce `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="507d7-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="507d7-115">InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="507d7-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="507d7-116">Permet à un débogueur d’intercepter l’exception actuelle sur un thread.</span><span class="sxs-lookup"><span data-stu-id="507d7-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="507d7-117">Notes</span><span class="sxs-lookup"><span data-stu-id="507d7-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="507d7-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="507d7-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="507d7-119">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="507d7-119">Requirements</span></span>  
 <span data-ttu-id="507d7-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="507d7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="507d7-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="507d7-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="507d7-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="507d7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="507d7-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="507d7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507d7-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="507d7-124">See also</span></span>

- [<span data-ttu-id="507d7-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="507d7-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
