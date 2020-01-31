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
ms.openlocfilehash: b97f29b94ed4fad6892697ca1c7ed4a20c99c03e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793266"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="d0726-102">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="d0726-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="d0726-103">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="d0726-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0726-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d0726-104">Methods</span></span>  
  
|<span data-ttu-id="d0726-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d0726-105">Method</span></span>|<span data-ttu-id="d0726-106">Description</span><span class="sxs-lookup"><span data-stu-id="d0726-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0726-107">CustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="d0726-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="d0726-108">Indique qu’une notification du débogueur personnalisé activé a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="d0726-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0726-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d0726-109">Remarks</span></span>  
 <span data-ttu-id="d0726-110">Cette interface est une extension logique des interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) et [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d0726-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0726-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d0726-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0726-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d0726-112">Requirements</span></span>  
 <span data-ttu-id="d0726-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0726-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0726-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0726-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0726-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0726-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0726-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0726-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0726-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0726-117">See also</span></span>

- [<span data-ttu-id="d0726-118">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d0726-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="d0726-119">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="d0726-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d0726-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d0726-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d0726-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="d0726-121">Debugging</span></span>](index.md)
