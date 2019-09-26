---
title: CorDebugBlockingReason, énumération
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274142"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="29678-102">CorDebugBlockingReason, énumération</span><span class="sxs-lookup"><span data-stu-id="29678-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="29678-103">Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.</span><span class="sxs-lookup"><span data-stu-id="29678-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29678-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29678-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="29678-105">Membres</span><span class="sxs-lookup"><span data-stu-id="29678-105">Members</span></span>  
  
|<span data-ttu-id="29678-106">Membre</span><span class="sxs-lookup"><span data-stu-id="29678-106">Member</span></span>|<span data-ttu-id="29678-107">Description</span><span class="sxs-lookup"><span data-stu-id="29678-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="29678-108">Usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="29678-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="29678-109">Un thread tente d’acquérir la section critique associée au verrou du moniteur sur un objet.</span><span class="sxs-lookup"><span data-stu-id="29678-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="29678-110">En général, cela se produit lorsque vous appelez l' <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> une <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> des méthodes ou.</span><span class="sxs-lookup"><span data-stu-id="29678-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="29678-111">Un thread attend sur l’événement associé à un verrou de moniteur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="29678-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="29678-112">En général, cela se produit lorsque vous appelez l' <xref:System.Threading.Monitor?displayProperty=nameWithType> une des `Wait` méthodes.</span><span class="sxs-lookup"><span data-stu-id="29678-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29678-113">Notes</span><span class="sxs-lookup"><span data-stu-id="29678-113">Remarks</span></span>  
 <span data-ttu-id="29678-114">Quand le `BLOCKING_MONITOR_CRITICAL_SECTION` membre `BLOCKING_MONITOR_EVENT` ou est utilisé dans une structure [CorDebugBlockingObject](cordebugblockingobject-structure.md) , le `pBlockingObject` membre de la structure pointe vers une interface « ICorDebugValue » qui représente l’objet en cours d’entrée.</span><span class="sxs-lookup"><span data-stu-id="29678-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="29678-115">Il est également garanti d’implémenter l’interface [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="29678-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29678-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="29678-116">Requirements</span></span>  
 <span data-ttu-id="29678-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29678-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29678-118">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29678-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29678-119">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29678-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29678-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29678-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29678-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29678-121">See also</span></span>

- [<span data-ttu-id="29678-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="29678-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="29678-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="29678-123">Debugging</span></span>](index.md)
