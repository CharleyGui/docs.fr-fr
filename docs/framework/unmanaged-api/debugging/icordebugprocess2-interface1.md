---
title: ICorDebugProcess2, interface
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2
helpviewer_keywords:
- ICorDebugProcess2 interface [.NET Framework debugging]
ms.assetid: 73332138-5fea-441f-b893-61af87d45a42
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5519714ff2b4ee67d0e59001bf5b454cdc25d648
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961081"
---
# <a name="icordebugprocess2-interface"></a><span data-ttu-id="8ada3-102">ICorDebugProcess2, interface</span><span class="sxs-lookup"><span data-stu-id="8ada3-102">ICorDebugProcess2 Interface</span></span>
<span data-ttu-id="8ada3-103">Extension logique de l’interface ICorDebugProcess, qui représente un processus exécutant du code managé.</span><span class="sxs-lookup"><span data-stu-id="8ada3-103">A logical extension of the ICorDebugProcess interface, which represents a process running managed code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ada3-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="8ada3-104">Methods</span></span>  
  
|<span data-ttu-id="8ada3-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-105">Method</span></span>|<span data-ttu-id="8ada3-106">Description</span><span class="sxs-lookup"><span data-stu-id="8ada3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ada3-107">ClearUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-107">ClearUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)|<span data-ttu-id="8ada3-108">Supprime un point d’arrêt au niveau de l’offset spécifié qui a été défini `ICorDebugProcess2::SetUnmanagedBreakpoint`par un appel antérieur à.</span><span class="sxs-lookup"><span data-stu-id="8ada3-108">Removes a breakpoint at the specified offset that was set by an earlier call to `ICorDebugProcess2::SetUnmanagedBreakpoint`.</span></span>|  
|[<span data-ttu-id="8ada3-109">GetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-109">GetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getdesiredngencompilerflags-method.md)|<span data-ttu-id="8ada3-110">Obtient les indicateurs qui doivent être définis pour le common language runtime (CLR) pour charger l’image dans le processus référencé par ce `ICorDebugProcess2`.</span><span class="sxs-lookup"><span data-stu-id="8ada3-110">Gets the flags that must be set for the common language runtime (CLR) to load the image into the process referenced by this `ICorDebugProcess2`.</span></span>|  
|[<span data-ttu-id="8ada3-111">GetReferenceValueFromGCHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-111">GetReferenceValueFromGCHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getreferencevaluefromgchandle-method.md)|<span data-ttu-id="8ada3-112">Obtient un pointeur de référence vers l’objet managé spécifié qui a un handle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="8ada3-112">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>|  
|[<span data-ttu-id="8ada3-113">GetThreadForTaskID, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-113">GetThreadForTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getthreadfortaskid-method.md)|<span data-ttu-id="8ada3-114">Obtient le thread sur lequel s’exécute la tâche avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="8ada3-114">Gets the thread upon which the task with the specified identifier is executing.</span></span>|  
|[<span data-ttu-id="8ada3-115">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-115">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-getversion-method.md)|<span data-ttu-id="8ada3-116">Obtient la version du CLR sur laquelle le processus en cours de débogage est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8ada3-116">Gets the version of the CLR upon which the process being debugged is running.</span></span>|  
|[<span data-ttu-id="8ada3-117">SetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-117">SetDesiredNGENCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)|<span data-ttu-id="8ada3-118">Définit les indicateurs requis pour que le compilateur juste-à-temps (JIT) charge une image dans le processus en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="8ada3-118">Sets the flags that are required for the just-in-time (JIT) compiler to load an image into the process being debugged.</span></span>|  
|[<span data-ttu-id="8ada3-119">SetUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="8ada3-119">SetUnmanagedBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)|<span data-ttu-id="8ada3-120">Définit un point d’arrêt non managé au niveau de l’offset d’image native spécifié.</span><span class="sxs-lookup"><span data-stu-id="8ada3-120">Sets an unmanaged breakpoint at the specified native image offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ada3-121">Notes</span><span class="sxs-lookup"><span data-stu-id="8ada3-121">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ada3-122">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="8ada3-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ada3-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8ada3-123">Requirements</span></span>  
 <span data-ttu-id="8ada3-124">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ada3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ada3-125">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8ada3-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ada3-126">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ada3-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ada3-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ada3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ada3-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ada3-128">See also</span></span>

- [<span data-ttu-id="8ada3-129">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8ada3-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
