---
title: ICorDebugHeapValue3, interface
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
ms.openlocfilehash: 5add6da1ace372ecf6e513902bbf98f5f79c6778
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210395"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="46ed9-102">ICorDebugHeapValue3, interface</span><span class="sxs-lookup"><span data-stu-id="46ed9-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="46ed9-103">Expose les propriétés du verrou du moniteur d'objets.</span><span class="sxs-lookup"><span data-stu-id="46ed9-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="46ed9-104">Cette interface étend les interfaces ICorDebugHeapValue et ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="46ed9-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46ed9-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="46ed9-105">Methods</span></span>  
  
|<span data-ttu-id="46ed9-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="46ed9-106">Method</span></span>|<span data-ttu-id="46ed9-107">Description</span><span class="sxs-lookup"><span data-stu-id="46ed9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46ed9-108">GetThreadOwningMonitorLock, méthode</span><span class="sxs-lookup"><span data-stu-id="46ed9-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="46ed9-109">Retourne le thread managé qui détient le verrou du moniteur sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="46ed9-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="46ed9-110">GetMonitorEventWaitList, méthode</span><span class="sxs-lookup"><span data-stu-id="46ed9-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="46ed9-111">Fournit une liste triée des threads mis en file d’attente sur l’événement associé à un verrou d’analyse.</span><span class="sxs-lookup"><span data-stu-id="46ed9-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46ed9-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="46ed9-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="46ed9-113">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="46ed9-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46ed9-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46ed9-114">Requirements</span></span>  
 <span data-ttu-id="46ed9-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46ed9-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46ed9-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46ed9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46ed9-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46ed9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46ed9-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46ed9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ed9-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46ed9-119">See also</span></span>

- [<span data-ttu-id="46ed9-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="46ed9-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="46ed9-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="46ed9-121">Debugging</span></span>](index.md)
