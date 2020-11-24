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
ms.openlocfilehash: ddd03d70656ad52fd9d577beedc60b51c7b305d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672849"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="aa203-102">CorDebugBlockingReason, énumération</span><span class="sxs-lookup"><span data-stu-id="aa203-102">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="aa203-103">Spécifie les raisons pour lesquelles un thread peut être bloqué sur un objet donné.</span><span class="sxs-lookup"><span data-stu-id="aa203-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa203-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa203-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="aa203-105">Membres</span><span class="sxs-lookup"><span data-stu-id="aa203-105">Members</span></span>  
  
|<span data-ttu-id="aa203-106">Membre</span><span class="sxs-lookup"><span data-stu-id="aa203-106">Member</span></span>|<span data-ttu-id="aa203-107">Description</span><span class="sxs-lookup"><span data-stu-id="aa203-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="aa203-108">À usage interne uniquement</span><span class="sxs-lookup"><span data-stu-id="aa203-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="aa203-109">Un thread tente d’acquérir la section critique associée au verrou du moniteur sur un objet.</span><span class="sxs-lookup"><span data-stu-id="aa203-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="aa203-110">En général, cela se produit lorsque vous appelez l’une des <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> méthodes ou.</span><span class="sxs-lookup"><span data-stu-id="aa203-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="aa203-111">Un thread attend sur l’événement associé à un verrou de moniteur pour un objet.</span><span class="sxs-lookup"><span data-stu-id="aa203-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="aa203-112">En général, cela se produit lorsque vous appelez l’une des <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` méthodes.</span><span class="sxs-lookup"><span data-stu-id="aa203-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa203-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa203-113">Remarks</span></span>  

 <span data-ttu-id="aa203-114">Quand le `BLOCKING_MONITOR_CRITICAL_SECTION` `BLOCKING_MONITOR_EVENT` membre ou est utilisé dans une structure [CorDebugBlockingObject](cordebugblockingobject-structure.md) , le `pBlockingObject` membre de la structure pointe vers une interface « ICorDebugValue » qui représente l’objet en cours d’entrée.</span><span class="sxs-lookup"><span data-stu-id="aa203-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="aa203-115">Il est également garanti d’implémenter l’interface [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="aa203-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa203-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aa203-116">Requirements</span></span>  

 <span data-ttu-id="aa203-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa203-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa203-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa203-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa203-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa203-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa203-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa203-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa203-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa203-121">See also</span></span>

- [<span data-ttu-id="aa203-122">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="aa203-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="aa203-123">Débogage</span><span class="sxs-lookup"><span data-stu-id="aa203-123">Debugging</span></span>](index.md)
