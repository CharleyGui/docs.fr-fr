---
title: COR_DEBUG_STEP_RANGE, structure
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
ms.openlocfilehash: cd85ba2e6a907ff9546614e02b4da5f45e74b924
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726637"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="99005-102">COR_DEBUG_STEP_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="99005-102">COR_DEBUG_STEP_RANGE Structure</span></span>

<span data-ttu-id="99005-103">Contient les informations de décalage pour une plage de code.</span><span class="sxs-lookup"><span data-stu-id="99005-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="99005-104">Cette structure est utilisée par la méthode [ICorDebugStepper :: StepRange](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="99005-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99005-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99005-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="99005-106">Membres</span><span class="sxs-lookup"><span data-stu-id="99005-106">Members</span></span>  
  
|<span data-ttu-id="99005-107">Membre</span><span class="sxs-lookup"><span data-stu-id="99005-107">Member</span></span>|<span data-ttu-id="99005-108">Description</span><span class="sxs-lookup"><span data-stu-id="99005-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="99005-109">Offset du début de la plage.</span><span class="sxs-lookup"><span data-stu-id="99005-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="99005-110">Décalage de la fin de la plage.</span><span class="sxs-lookup"><span data-stu-id="99005-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99005-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="99005-111">Requirements</span></span>  

 <span data-ttu-id="99005-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99005-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99005-113">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="99005-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="99005-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99005-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99005-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99005-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99005-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99005-116">See also</span></span>

- [<span data-ttu-id="99005-117">StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="99005-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="99005-118">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="99005-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="99005-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="99005-119">Debugging</span></span>](index.md)
