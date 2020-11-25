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
ms.openlocfilehash: e04f5be6d2612b26bf7d71807753d170e6a5a7a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723296"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="207eb-102">ICorDebugManagedCallback3, interface</span><span class="sxs-lookup"><span data-stu-id="207eb-102">ICorDebugManagedCallback3 Interface</span></span>

<span data-ttu-id="207eb-103">Fournit une méthode de rappel indiquant qu'une notification de débogueur personnalisée active a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="207eb-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="207eb-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="207eb-104">Methods</span></span>  
  
|<span data-ttu-id="207eb-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="207eb-105">Method</span></span>|<span data-ttu-id="207eb-106">Description</span><span class="sxs-lookup"><span data-stu-id="207eb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="207eb-107">CustomNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="207eb-107">CustomNotification Method</span></span>](icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="207eb-108">Indique qu’une notification du débogueur personnalisé activé a été déclenchée.</span><span class="sxs-lookup"><span data-stu-id="207eb-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="207eb-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="207eb-109">Remarks</span></span>  

 <span data-ttu-id="207eb-110">Cette interface est une extension logique des interfaces [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) et [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="207eb-110">This interface is a logical extension of the [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="207eb-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="207eb-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="207eb-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="207eb-112">Requirements</span></span>  

 <span data-ttu-id="207eb-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="207eb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="207eb-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="207eb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="207eb-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="207eb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="207eb-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="207eb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="207eb-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="207eb-117">See also</span></span>

- [<span data-ttu-id="207eb-118">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="207eb-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="207eb-119">ICorDebugManagedCallback2, interface</span><span class="sxs-lookup"><span data-stu-id="207eb-119">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="207eb-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="207eb-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="207eb-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="207eb-121">Debugging</span></span>](index.md)
