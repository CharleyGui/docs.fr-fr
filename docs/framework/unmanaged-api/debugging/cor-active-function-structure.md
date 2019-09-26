---
title: COR_ACTIVE_FUNCTION, structure
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd4acece43628b20b6bc50a539ee197e865855
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274155"
---
# <a name="cor_active_function-structure"></a><span data-ttu-id="9092d-102">COR_ACTIVE_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="9092d-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="9092d-103">Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.</span><span class="sxs-lookup"><span data-stu-id="9092d-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="9092d-104">Cette structure est utilisée par la méthode [ICorDebugThread2 :: GetActiveFunctions,](icordebugthread2-getactivefunctions-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9092d-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9092d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9092d-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="9092d-106">Membres</span><span class="sxs-lookup"><span data-stu-id="9092d-106">Members</span></span>  
  
|<span data-ttu-id="9092d-107">Membre</span><span class="sxs-lookup"><span data-stu-id="9092d-107">Member</span></span>|<span data-ttu-id="9092d-108">Description</span><span class="sxs-lookup"><span data-stu-id="9092d-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="9092d-109">Pointeur vers le propriétaire du domaine d’application `ilOffset` du champ.</span><span class="sxs-lookup"><span data-stu-id="9092d-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="9092d-110">Pointeur désignant le propriétaire du `ilOffset` module du champ.</span><span class="sxs-lookup"><span data-stu-id="9092d-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="9092d-111">Pointeur désignant le propriétaire de `ilOffset` la fonction du champ.</span><span class="sxs-lookup"><span data-stu-id="9092d-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="9092d-112">Décalage MSIL (Microsoft Intermediate Language) du frame.</span><span class="sxs-lookup"><span data-stu-id="9092d-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="9092d-113">Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="9092d-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9092d-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9092d-114">Requirements</span></span>  
 <span data-ttu-id="9092d-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9092d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9092d-116">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="9092d-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="9092d-117">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9092d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9092d-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9092d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9092d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9092d-119">See also</span></span>

- [<span data-ttu-id="9092d-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="9092d-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="9092d-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="9092d-121">Debugging</span></span>](index.md)
