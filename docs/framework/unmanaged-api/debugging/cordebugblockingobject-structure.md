---
title: CorDebugBlockingObject, structure
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273970"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="f7f84-102">CorDebugBlockingObject, structure</span><span class="sxs-lookup"><span data-stu-id="f7f84-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="f7f84-103">Définit un objet qui bloque un thread et la raison spécifique pour laquelle le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="f7f84-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7f84-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7f84-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="f7f84-105">Membres</span><span class="sxs-lookup"><span data-stu-id="f7f84-105">Members</span></span>  
  
|<span data-ttu-id="f7f84-106">Membre</span><span class="sxs-lookup"><span data-stu-id="f7f84-106">Member</span></span>|<span data-ttu-id="f7f84-107">Description</span><span class="sxs-lookup"><span data-stu-id="f7f84-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="f7f84-108">Objet sur lequel le thread se bloque.</span><span class="sxs-lookup"><span data-stu-id="f7f84-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="f7f84-109">Cet objet est valide uniquement pour la durée de l’état synchronisé actuel.</span><span class="sxs-lookup"><span data-stu-id="f7f84-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="f7f84-110">Si deux threads se bloquent sur le même objet dans le même état synchronisé, vous pouvez vous attendre à ce que la méthode [ICorDebugValue :: GetAddress](icordebugvalue-getaddress-method.md) retourne la même valeur.</span><span class="sxs-lookup"><span data-stu-id="f7f84-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="f7f84-111">Toutefois, les interfaces peuvent ou ne peuvent pas être équivalentes à un pointeur.</span><span class="sxs-lookup"><span data-stu-id="f7f84-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="f7f84-112">Nombre de millisecondes avant l’expiration du délai d’attente de l’opération de blocage, ou valeur infinie, qui indique qu’il n’expirera pas. La valeur du délai d’attente spécifie la durée totale de l’opération de blocage, et non pas la durée restante.</span><span class="sxs-lookup"><span data-stu-id="f7f84-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="f7f84-113">Raison pour laquelle le thread est bloqué sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="f7f84-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7f84-114">Notes</span><span class="sxs-lookup"><span data-stu-id="f7f84-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7f84-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f7f84-115">Requirements</span></span>  
 <span data-ttu-id="f7f84-116">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7f84-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7f84-117">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="f7f84-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="f7f84-118">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7f84-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7f84-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7f84-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7f84-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7f84-120">See also</span></span>

- [<span data-ttu-id="f7f84-121">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="f7f84-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="f7f84-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="f7f84-122">Debugging</span></span>](index.md)
