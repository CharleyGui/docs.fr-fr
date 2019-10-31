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
ms.openlocfilehash: bc488e55bf64468eb62e2dc6eaedca62ebde3310
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098985"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="bb2cc-102">CorDebugBlockingReason, énumération</span><span class="sxs-lookup"><span data-stu-id="bb2cc-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="bb2cc-103">Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb2cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb2cc-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="bb2cc-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bb2cc-105">Members</span></span>  
  
|<span data-ttu-id="bb2cc-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bb2cc-106">Member</span></span>|<span data-ttu-id="bb2cc-107">Description</span><span class="sxs-lookup"><span data-stu-id="bb2cc-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="bb2cc-108">Usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="bb2cc-109">Un thread tente d’acquérir la section critique associée au verrou du moniteur sur un objet.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="bb2cc-110">En général, cela se produit lorsque vous appelez l’une des méthodes <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ou <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="bb2cc-111">Un thread attend sur l’événement associé à un verrou de moniteur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="bb2cc-112">En général, cela se produit lorsque vous appelez l’une des méthodes <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait`.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb2cc-113">Notes</span><span class="sxs-lookup"><span data-stu-id="bb2cc-113">Remarks</span></span>  
 <span data-ttu-id="bb2cc-114">Quand le membre `BLOCKING_MONITOR_CRITICAL_SECTION` ou `BLOCKING_MONITOR_EVENT` est utilisé dans une structure [CorDebugBlockingObject](cordebugblockingobject-structure.md) , le membre `pBlockingObject` de la structure pointe vers une interface « ICorDebugValue » qui représente l’objet en cours d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bb2cc-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="bb2cc-115">Il est également garanti d’implémenter l’interface [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="bb2cc-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb2cc-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="bb2cc-116">Requirements</span></span>  
 <span data-ttu-id="bb2cc-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb2cc-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb2cc-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb2cc-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb2cc-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb2cc-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb2cc-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb2cc-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb2cc-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb2cc-121">See also</span></span>

- [<span data-ttu-id="bb2cc-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="bb2cc-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="bb2cc-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="bb2cc-123">Debugging</span></span>](index.md)
