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
ms.openlocfilehash: 83dac3b9b2ac396cdef19695fcce0f7e20485a50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740391"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="d2125-102">CorDebugBlockingObject, structure</span><span class="sxs-lookup"><span data-stu-id="d2125-102">CorDebugBlockingObject Structure</span></span>
<span data-ttu-id="d2125-103">Définit un objet qui bloque un thread et la raison spécifique que le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="d2125-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2125-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2125-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="d2125-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d2125-105">Members</span></span>  
  
|<span data-ttu-id="d2125-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d2125-106">Member</span></span>|<span data-ttu-id="d2125-107">Description</span><span class="sxs-lookup"><span data-stu-id="d2125-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="d2125-108">L’objet sur lequel le thread est bloqué.</span><span class="sxs-lookup"><span data-stu-id="d2125-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="d2125-109">Cet objet est valid uniquement pour la durée de l’état synchronisé actuel.</span><span class="sxs-lookup"><span data-stu-id="d2125-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="d2125-110">Si deux threads se bloquent sur le même objet dans le même état synchronisé, vous pouvez attendre la [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) méthode pour retourner la même valeur.</span><span class="sxs-lookup"><span data-stu-id="d2125-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="d2125-111">Toutefois, les interfaces peuvent ou peut ne pas être pointeur équivalente.</span><span class="sxs-lookup"><span data-stu-id="d2125-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="d2125-112">Le nombre de millisecondes avant l’opération de blocage sera la valeur infinie, ce qui indique ce qu’elle soit aucun délai d’expiration ou expiration. La valeur de délai d’attente spécifie la longueur totale de temps pour l’opération de blocage, pas le temps restant.</span><span class="sxs-lookup"><span data-stu-id="d2125-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="d2125-113">La raison est que le thread est bloqué sur cet objet.</span><span class="sxs-lookup"><span data-stu-id="d2125-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2125-114">Notes</span><span class="sxs-lookup"><span data-stu-id="d2125-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2125-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d2125-115">Requirements</span></span>  
 <span data-ttu-id="d2125-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2125-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2125-117">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d2125-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d2125-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2125-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2125-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2125-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2125-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2125-120">See also</span></span>

- [<span data-ttu-id="d2125-121">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="d2125-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="d2125-122">Débogage</span><span class="sxs-lookup"><span data-stu-id="d2125-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
