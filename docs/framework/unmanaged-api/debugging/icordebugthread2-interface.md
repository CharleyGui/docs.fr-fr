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
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379834"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="4139e-102">ICorDebugThread2, interface</span><span class="sxs-lookup"><span data-stu-id="4139e-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="4139e-103">Sert d’extension logique à l’interface ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="4139e-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4139e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4139e-104">Methods</span></span>  
  
|<span data-ttu-id="4139e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4139e-105">Method</span></span>|<span data-ttu-id="4139e-106">Description</span><span class="sxs-lookup"><span data-stu-id="4139e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4139e-107">GetActiveFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="4139e-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="4139e-108">Obtient un tableau d’instances de COR_ACTIVE_FUNCTION qui contiennent des données relatives aux fonctions actives dans les frames d’un thread.</span><span class="sxs-lookup"><span data-stu-id="4139e-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="4139e-109">GetConnectionID, méthode</span><span class="sxs-lookup"><span data-stu-id="4139e-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="4139e-110">Obtient un identificateur de connexion pour ce `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="4139e-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="4139e-111">GetTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="4139e-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="4139e-112">Obtient un identificateur de tâche pour ce `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="4139e-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="4139e-113">GetVolatileOSThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="4139e-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="4139e-114">Obtient l’identificateur de thread de système d’exploitation pour ce `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="4139e-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="4139e-115">InterceptCurrentException, méthode</span><span class="sxs-lookup"><span data-stu-id="4139e-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="4139e-116">Permet à un débogueur d’intercepter l’exception actuelle sur un thread.</span><span class="sxs-lookup"><span data-stu-id="4139e-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4139e-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="4139e-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4139e-118">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4139e-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4139e-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4139e-119">Requirements</span></span>  
 <span data-ttu-id="4139e-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4139e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4139e-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4139e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4139e-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4139e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4139e-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4139e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4139e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4139e-124">See also</span></span>

- [<span data-ttu-id="4139e-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4139e-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
