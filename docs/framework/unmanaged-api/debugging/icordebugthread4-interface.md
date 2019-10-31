---
title: ICorDebugThread4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugThread4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4
helpviewer_keywords:
- ICorDebugThread4 interface [.NET Framework debugging]
ms.assetid: a8c7719a-322b-4133-8566-4c27218dc104
topic_type:
- apiref
ms.openlocfilehash: 8779dbc95a8bef13d45605295bd68b1d3f16851d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122434"
---
# <a name="icordebugthread4-interface"></a><span data-ttu-id="3333a-102">ICorDebugThread4, interface</span><span class="sxs-lookup"><span data-stu-id="3333a-102">ICorDebugThread4 Interface</span></span>
<span data-ttu-id="3333a-103">Fournit des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="3333a-103">Provides thread blocking information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3333a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3333a-104">Methods</span></span>  
  
|<span data-ttu-id="3333a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3333a-105">Method</span></span>|<span data-ttu-id="3333a-106">Description</span><span class="sxs-lookup"><span data-stu-id="3333a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3333a-107">GetBlockingObjects, méthode</span><span class="sxs-lookup"><span data-stu-id="3333a-107">GetBlockingObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getblockingobjects-method.md)|<span data-ttu-id="3333a-108">Fournit une énumération ordonnée des structures [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) qui fournissent des informations sur le blocage des threads.</span><span class="sxs-lookup"><span data-stu-id="3333a-108">Provides an ordered enumeration of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>|  
|[<span data-ttu-id="3333a-109">HadUnhandledException, méthode</span><span class="sxs-lookup"><span data-stu-id="3333a-109">HadUnhandledException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-hadunhandledexception-method.md)|<span data-ttu-id="3333a-110">Indique si le thread a déjà eu une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="3333a-110">Indicates whether the thread has ever had an unhandled exception.</span></span>|  
|[<span data-ttu-id="3333a-111">GetCurrentCustomDebuggerNotification, méthode</span><span class="sxs-lookup"><span data-stu-id="3333a-111">GetCurrentCustomDebuggerNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-getcurrentcustomdebuggernotification-method.md)|<span data-ttu-id="3333a-112">Obtient l’objet [ICorDebugManagedCallback3 :: CustomNotification,](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) actuel sur le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="3333a-112">Gets the current [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3333a-113">Notes</span><span class="sxs-lookup"><span data-stu-id="3333a-113">Remarks</span></span>  
 <span data-ttu-id="3333a-114">Cette interface est une extension logique des interfaces ICorDebugThread, ICorDebugThread2 et [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3333a-114">This interface is a logical extension of the ICorDebugThread, ICorDebugThread2, and [ICorDebugThread3](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3333a-115">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="3333a-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3333a-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="3333a-116">Requirements</span></span>  
 <span data-ttu-id="3333a-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3333a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3333a-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3333a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3333a-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3333a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3333a-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3333a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3333a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3333a-121">See also</span></span>

- [<span data-ttu-id="3333a-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3333a-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3333a-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="3333a-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
