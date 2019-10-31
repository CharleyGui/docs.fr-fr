---
title: ICorDebugAppDomain, interface
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 9abcb765357a0f305ae5acae77a4a13b07a003a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134688"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="4a100-102">ICorDebugAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="4a100-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="4a100-103">Fournit des méthodes pour le débogage de domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="4a100-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="4a100-104">This interface is a subclass of ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="4a100-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a100-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4a100-105">Methods</span></span>  
  
|<span data-ttu-id="4a100-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-106">Method</span></span>|<span data-ttu-id="4a100-107">Description</span><span class="sxs-lookup"><span data-stu-id="4a100-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a100-108">Attach, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="4a100-109">Attaches the debugger to the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="4a100-110">EnumerateAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="4a100-111">Gets an enumerator for the assemblies in the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="4a100-112">EnumerateBreakpoints, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="4a100-113">Gets an enumerator for all active breakpoints in the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="4a100-114">EnumerateSteppers, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="4a100-115">Gets an enumerator for all active steppers in the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="4a100-116">GetID, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="4a100-117">Gets the unique ID of the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="4a100-118">GetModuleFromMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="4a100-119">Gets the ICorDebugModule object with the given metadata interface.</span><span class="sxs-lookup"><span data-stu-id="4a100-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="4a100-120">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="4a100-121">Gets the name of the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="4a100-122">GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="4a100-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="4a100-124">GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="4a100-125">Gets the process containing the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="4a100-126">IsAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="4a100-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="4a100-127">Determines whether the debugger is attached to the application domain.</span><span class="sxs-lookup"><span data-stu-id="4a100-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a100-128">Notes</span><span class="sxs-lookup"><span data-stu-id="4a100-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a100-129">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="4a100-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a100-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="4a100-130">Requirements</span></span>  
 <span data-ttu-id="4a100-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a100-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a100-132">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a100-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a100-133">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a100-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a100-134">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a100-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a100-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a100-135">See also</span></span>

- [<span data-ttu-id="4a100-136">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4a100-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
