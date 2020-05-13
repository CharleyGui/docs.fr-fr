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
ms.openlocfilehash: 63e3f166c4cbf17f4892dccf770343bfbf6e0284
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209745"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="d364f-102">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="d364f-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="d364f-103">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="d364f-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d364f-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d364f-104">Methods</span></span>  
  
|<span data-ttu-id="d364f-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="d364f-105">Method</span></span>|<span data-ttu-id="d364f-106">Description</span><span class="sxs-lookup"><span data-stu-id="d364f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d364f-107">CustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="d364f-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="d364f-108">Indique qu’une notification du débogueur personnalisé activé a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="d364f-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d364f-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d364f-109">Remarks</span></span>  
 <span data-ttu-id="d364f-110">Cette interface est une extension logique des interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) et [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d364f-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d364f-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="d364f-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d364f-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d364f-112">Requirements</span></span>  
 <span data-ttu-id="d364f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d364f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d364f-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d364f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d364f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d364f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d364f-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d364f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d364f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d364f-117">See also</span></span>

- [<span data-ttu-id="d364f-118">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="d364f-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="d364f-119">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="d364f-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d364f-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="d364f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d364f-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="d364f-121">Debugging</span></span>](index.md)
