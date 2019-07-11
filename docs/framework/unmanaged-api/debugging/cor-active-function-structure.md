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
ms.openlocfilehash: 6875ce0e7ae4cefa9b0c8abaded0dd4535bdf838
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740828"
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="7af6c-102">COR_ACTIVE_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="7af6c-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="7af6c-103">Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.</span><span class="sxs-lookup"><span data-stu-id="7af6c-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="7af6c-104">Cette structure est utilisée par le [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="7af6c-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7af6c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7af6c-105">Syntax</span></span>  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="7af6c-106">Membres</span><span class="sxs-lookup"><span data-stu-id="7af6c-106">Members</span></span>  
  
|<span data-ttu-id="7af6c-107">Membre</span><span class="sxs-lookup"><span data-stu-id="7af6c-107">Member</span></span>|<span data-ttu-id="7af6c-108">Description</span><span class="sxs-lookup"><span data-stu-id="7af6c-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="7af6c-109">Pointeur vers le propriétaire du domaine d’application le `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="7af6c-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="7af6c-110">Pointeur vers le propriétaire du module le `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="7af6c-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="7af6c-111">Pointeur vers le propriétaire de la fonction de la `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="7af6c-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="7af6c-112">L’offset Microsoft intermediate language (MSIL), du frame.</span><span class="sxs-lookup"><span data-stu-id="7af6c-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="7af6c-113">Réservé pour une extensibilité future.</span><span class="sxs-lookup"><span data-stu-id="7af6c-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7af6c-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7af6c-114">Requirements</span></span>  
 <span data-ttu-id="7af6c-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7af6c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7af6c-116">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="7af6c-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="7af6c-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7af6c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7af6c-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7af6c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7af6c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7af6c-119">See also</span></span>

- [<span data-ttu-id="7af6c-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="7af6c-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="7af6c-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="7af6c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
