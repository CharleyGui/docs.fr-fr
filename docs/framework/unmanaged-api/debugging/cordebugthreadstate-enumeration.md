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
ms.openlocfilehash: 69a8aabd1d79bb9bb4248259c99124ce50677600
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789248"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="35e9b-102">CorDebugThreadState, énumération</span><span class="sxs-lookup"><span data-stu-id="35e9b-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="35e9b-103">Spécifie l'état d'un thread pour le débogage.</span><span class="sxs-lookup"><span data-stu-id="35e9b-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35e9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35e9b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="35e9b-105">Members</span><span class="sxs-lookup"><span data-stu-id="35e9b-105">Members</span></span>  
  
|<span data-ttu-id="35e9b-106">Member</span><span class="sxs-lookup"><span data-stu-id="35e9b-106">Member</span></span>|<span data-ttu-id="35e9b-107">Description</span><span class="sxs-lookup"><span data-stu-id="35e9b-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="35e9b-108">Le thread s’exécute librement, à moins qu’un événement de débogage se produise.</span><span class="sxs-lookup"><span data-stu-id="35e9b-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="35e9b-109">Le thread ne peut pas s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="35e9b-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35e9b-110">Notes</span><span class="sxs-lookup"><span data-stu-id="35e9b-110">Remarks</span></span>  
 <span data-ttu-id="35e9b-111">Le débogueur utilise l’énumération `CorDebugThreadState` pour contrôler l’exécution d’un thread.</span><span class="sxs-lookup"><span data-stu-id="35e9b-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="35e9b-112">L’état d’un thread peut être défini à l’aide de la méthode [ICorDebugThread :: SetDebugState,](icordebugthread-setdebugstate-method.md) ou [ICorDebugController :: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="35e9b-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="35e9b-113">Un rappel fourni à l' [API d’hébergement](../../../../docs/framework/unmanaged-api/hosting/index.md) active le pompage de messages, ce qui signifie qu’il n’est pas nécessaire d’interrompre l’État.</span><span class="sxs-lookup"><span data-stu-id="35e9b-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35e9b-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="35e9b-114">Requirements</span></span>  
 <span data-ttu-id="35e9b-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35e9b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35e9b-116">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35e9b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35e9b-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35e9b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35e9b-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35e9b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e9b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35e9b-119">See also</span></span>

- [<span data-ttu-id="35e9b-120">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="35e9b-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
