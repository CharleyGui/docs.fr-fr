---
title: ICorDebugManagedCallback3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 8da04b0c620404e0dad8227c7a627f75507389a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128025"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="86f31-102">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="86f31-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="86f31-103">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="86f31-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="86f31-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="86f31-104">Methods</span></span>  
  
|<span data-ttu-id="86f31-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="86f31-105">Method</span></span>|<span data-ttu-id="86f31-106">Description</span><span class="sxs-lookup"><span data-stu-id="86f31-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="86f31-107">CustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="86f31-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="86f31-108">Indique qu’une notification du débogueur personnalisé activé a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="86f31-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86f31-109">Notes</span><span class="sxs-lookup"><span data-stu-id="86f31-109">Remarks</span></span>  
 <span data-ttu-id="86f31-110">Cette interface est une extension logique des interfaces [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) et [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="86f31-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86f31-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="86f31-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f31-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="86f31-112">Requirements</span></span>  
 <span data-ttu-id="86f31-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f31-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f31-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86f31-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86f31-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86f31-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86f31-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f31-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f31-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f31-117">See also</span></span>

- [<span data-ttu-id="86f31-118">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="86f31-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="86f31-119">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="86f31-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="86f31-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="86f31-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="86f31-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="86f31-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
