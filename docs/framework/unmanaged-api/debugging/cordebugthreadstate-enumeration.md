---
title: CorDebugThreadState, énumération
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce252f5a4b5fbcdbbc7b70c8b1c829490f8f63e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739531"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="e11e1-102">CorDebugThreadState, énumération</span><span class="sxs-lookup"><span data-stu-id="e11e1-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="e11e1-103">Spécifie l'état d'un thread pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="e11e1-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e11e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e11e1-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="e11e1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="e11e1-105">Members</span></span>  
  
|<span data-ttu-id="e11e1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="e11e1-106">Member</span></span>|<span data-ttu-id="e11e1-107">Description</span><span class="sxs-lookup"><span data-stu-id="e11e1-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="e11e1-108">Le thread exécute librement, sauf si un événement de débogage se produit.</span><span class="sxs-lookup"><span data-stu-id="e11e1-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="e11e1-109">Le thread ne peut pas s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="e11e1-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e11e1-110">Notes</span><span class="sxs-lookup"><span data-stu-id="e11e1-110">Remarks</span></span>  
 <span data-ttu-id="e11e1-111">Le débogueur utilise la `CorDebugThreadState` énumération pour contrôler l’exécution d’un thread.</span><span class="sxs-lookup"><span data-stu-id="e11e1-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="e11e1-112">L’état d’un thread peut être défini à l’aide de la [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) ou [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e11e1-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="e11e1-113">Un rappel fourni à la [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md) permet le pompage de messages, un état interrompu est donc pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e11e1-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e11e1-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e11e1-114">Requirements</span></span>  
 <span data-ttu-id="e11e1-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e11e1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e11e1-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e11e1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e11e1-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e11e1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e11e1-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e11e1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e11e1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e11e1-119">See also</span></span>

- [<span data-ttu-id="e11e1-120">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="e11e1-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
