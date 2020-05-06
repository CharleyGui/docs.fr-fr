---
title: CorDebugUserState, énumération
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d502b4098016fb14793bccd6feb641e92e3c2611
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795636"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="33bcd-102">CorDebugUserState, énumération</span><span class="sxs-lookup"><span data-stu-id="33bcd-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="33bcd-103">Indique l'état de l'utilisateur d'un thread.</span><span class="sxs-lookup"><span data-stu-id="33bcd-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33bcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33bcd-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="33bcd-105">Membres</span><span class="sxs-lookup"><span data-stu-id="33bcd-105">Members</span></span>  
  
|<span data-ttu-id="33bcd-106">Valeur</span><span class="sxs-lookup"><span data-stu-id="33bcd-106">Value</span></span>|<span data-ttu-id="33bcd-107">Description</span><span class="sxs-lookup"><span data-stu-id="33bcd-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="33bcd-108">Un arrêt du thread a été demandé.</span><span class="sxs-lookup"><span data-stu-id="33bcd-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="33bcd-109">Une suspension du thread a été demandée.</span><span class="sxs-lookup"><span data-stu-id="33bcd-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="33bcd-110">Le thread s’exécute en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="33bcd-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="33bcd-111">Le thread n’a pas commencé à s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="33bcd-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="33bcd-112">Le thread a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="33bcd-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="33bcd-113">Le thread attend qu’un autre thread termine une tâche.</span><span class="sxs-lookup"><span data-stu-id="33bcd-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="33bcd-114">Le thread a été suspendu.</span><span class="sxs-lookup"><span data-stu-id="33bcd-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="33bcd-115">Le thread se trouve à un point non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="33bcd-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="33bcd-116">Autrement dit, le thread est à un point d’exécution où il peut bloquer garbage collection.</span><span class="sxs-lookup"><span data-stu-id="33bcd-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="33bcd-117">Les événements de débogage peuvent être distribués à partir de points non sécurisés, mais l’interruption d’un thread à un point non sécurisé entraîne très probablement un blocage jusqu’à la reprise du thread.</span><span class="sxs-lookup"><span data-stu-id="33bcd-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="33bcd-118">Les points sécurisés et non sécurisés sont déterminés par l’implémentation juste-à-temps (JIT, Just-in-Time) et garbage collection.</span><span class="sxs-lookup"><span data-stu-id="33bcd-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="33bcd-119">Le thread provient du pool de threads.</span><span class="sxs-lookup"><span data-stu-id="33bcd-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33bcd-120">Notes </span><span class="sxs-lookup"><span data-stu-id="33bcd-120">Remarks</span></span>  
 <span data-ttu-id="33bcd-121">L’état utilisateur d’un thread est l’état que le thread a lorsque le débogueur l’examine.</span><span class="sxs-lookup"><span data-stu-id="33bcd-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="33bcd-122">Un thread peut avoir une combinaison d’États utilisateur.</span><span class="sxs-lookup"><span data-stu-id="33bcd-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="33bcd-123">Utilisez la méthode [ICorDebugThread :: GetUserState,](icordebugthread-getuserstate-method.md) pour récupérer l’état utilisateur d’un thread.</span><span class="sxs-lookup"><span data-stu-id="33bcd-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33bcd-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="33bcd-124">Requirements</span></span>  
 <span data-ttu-id="33bcd-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33bcd-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33bcd-126">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33bcd-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33bcd-127">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33bcd-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33bcd-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33bcd-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33bcd-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33bcd-129">See also</span></span>

- [<span data-ttu-id="33bcd-130">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="33bcd-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
