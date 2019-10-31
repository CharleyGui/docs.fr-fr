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
ms.openlocfilehash: 206e4fb232f4786a76525d24aa379b25d6d2f71d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099348"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="ec59b-102">COR_DEBUG_STEP_RANGE, structure</span><span class="sxs-lookup"><span data-stu-id="ec59b-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="ec59b-103">Contient les informations de décalage pour une plage de code.</span><span class="sxs-lookup"><span data-stu-id="ec59b-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="ec59b-104">Cette structure est utilisée par la méthode [ICorDebugStepper :: StepRange](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ec59b-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec59b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec59b-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="ec59b-106">Membres</span><span class="sxs-lookup"><span data-stu-id="ec59b-106">Members</span></span>  
  
|<span data-ttu-id="ec59b-107">Membre</span><span class="sxs-lookup"><span data-stu-id="ec59b-107">Member</span></span>|<span data-ttu-id="ec59b-108">Description</span><span class="sxs-lookup"><span data-stu-id="ec59b-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="ec59b-109">Offset du début de la plage.</span><span class="sxs-lookup"><span data-stu-id="ec59b-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="ec59b-110">Décalage de la fin de la plage.</span><span class="sxs-lookup"><span data-stu-id="ec59b-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec59b-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="ec59b-111">Requirements</span></span>  
 <span data-ttu-id="ec59b-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec59b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec59b-113">**En-tête :** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="ec59b-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="ec59b-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec59b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec59b-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec59b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec59b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec59b-116">See also</span></span>

- [<span data-ttu-id="ec59b-117">StepRange, méthode</span><span class="sxs-lookup"><span data-stu-id="ec59b-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="ec59b-118">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="ec59b-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ec59b-119">Débogage</span><span class="sxs-lookup"><span data-stu-id="ec59b-119">Debugging</span></span>](index.md)
